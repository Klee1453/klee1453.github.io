---
title: 在 Makefile 中，通过重定向输出字面的 $()
date: 2024-03-01 20:50:31
tags: 
- makefile
- linux

---

（GNU Make 4.3）

需要在 Makefile 中生成另一个 Makefile，遇到的问题是无法重定向输出字面的 $()，代码如下：

```makefile
bitstream-w:
	mkdir -p $(DIR_PROJECT)
	cd $(DIR_PROJECT); cp $(DIR_TCL)/vivado.tcl .
	cd $(DIR_PROJECT); cp -r $(DIR_SRC) src
	cd $(DIR_PROJECT); cp -r $(DIR_SYN) syn
	echo "DIR_SRC ?= src" > $(DIR_PROJECT)/temp
	echo "DIR_SYN ?= syn" >> $(DIR_PROJECT)/temp
	echo "export DIR_SRC, DIR_SYN" >> $(DIR_PROJECT)/temp
	echo "bitstream:" >> $(DIR_PROJECT)/temp
	echo "	$(VIVADO_SETUP) && set DIR_SRC=$$(DIR_SRC)&&set DIR_SYN=$$(DIR_SYN) && \
	    vivado -mode batch -nojournal -source vivado.tcl -tclargs -top-module $(TOP_MODULE) -board $(BOARD)" >> $(DIR_PROJECT)/temp
	mv $(DIR_PROJECT)/temp $(DIR_PROJECT)/Makefile
```

问题出在最后一个 echo 的重定向上。

此时 `make bitstream-w` 在屏幕上的输出为：

```bash
$ make bitstream-w
mkdir -p ...
cd ...; cp ... .
cd ...; cp -r ... src
cd ...; cp -r ... syn
echo "DIR_SRC ?= src" > ...
echo "DIR_SYN ?= syn" >> ...
echo "export DIR_SRC, DIR_SYN" >> ...
echo "bitstream:" >> ...
echo "  call ...\Xilinx\Vivado\2017.4\settings64.bat && set DIR_SRC=$(DIR_SRC)&&set DIR_SYN=$(DIR_SYN) && \
        vivado -mode batch -nojournal -source vivado.tcl -tclargs -top-module top  -board ..." >> .../temp
/bin/sh: 1: DIR_SRC: not found
/bin/sh: 1: DIR_SYN: not found
mv .../temp .../Makefile
```

然而在重定向输出时，最后一个 echo 中的 `$(DIR_SRC)` 与 `$(DIR_SYN)` 会被尝试替换为变量实际的值，而非预期的字面量 `$(DIR_SRC)` 与 `$(DIR_SYN)`。

如果在 Makefile 中改用 `$$$$(DIR_SRC)`， `make bitstream-w` 在屏幕上的输出为：

```bash
$ make bitstream-w
...
echo "  call ...\Xilinx\Vivado\2017.4\settings64.bat && set DIR_SRC=$$(DIR_SRC)&&set DIR_SYN=$$(DIR_SYN) && \
        vivado -mode batch -nojournal -source vivado.tcl -tclargs -top-module top  -board ..." >> .../temp
mv .../temp .../Makefile
```

在重定向输出时，最后一个 echo 中的 `$$(DIR_SRC)` 与 `$$(DIR_SYN)` 中的 `$$` 会被替换为 shell 进程的 PID，与在 shell 中运行 `echo $$` 效果等同，
也不能够在生成的 Makefile 文件中获得预期的字面量 `$(DIR_SRC)` 与 `$(DIR_SYN)`。

使用诸如下式的管道和 `tee` 也不能解决这个问题。

```bash
$ echo "Hello, World!" | tee file1.txt file2.txt > /dev/null
```

解决方案是**使用单引号 `''` 而非双引号 `""`**，原因是 make 不会尝试解析命令行，因此 make 对 `"$name"` 和 `"$name"` 的处理是一样的；
在这两种情况下，`$name` 都将被替换为 Makefile 中变量 `$(name)` 的值。在这两种情况下，shell 都不会看到 `$`。

如果要在 Makefile 的命令中插入字面量 `$`，则需要写入 `$$`。

然而 shell 对单引号 `''`与双引号 `""` 的处理是不同的：

- `echo '$a'` 将显示字面量 `$a` 。
- `echo "$a"` 会回显环境变量 `a` 的值。

因此，需要同时考虑 make 的扩展规则和 shell 的扩展规则，make 的扩展规则使得在这里的 `$` 应该被替换为 `$$`，
而 shell 扩展规则则要求命令行参数包含在单引号中。

参见：<https://stackoverflow.com/questions/22825640/simple-echo-in-makefile-escape-issue>