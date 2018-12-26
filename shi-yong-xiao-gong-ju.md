# 实用小工具

> 作为这个坑的 第一个开篇的文章，这里就做个简单轻松的入门了

这里主要是整理一些工具的功能，简单且实用且常用，這篇就从简单的开始了。

---

## LS

第一个命令不用惊讶，这里是对前面的知识进行拾遗，所以从简单的开始巩固

parameter：

| paramater | word | desc |
| :--- | :--- | :--- |
| -l | list |  |
| -i | inode | 显示存储的inode号 |
| -t | time | 修改时间正序 |
| -r | time reverse | 修改时间倒序 |

---

## WC

`wordcount` 这个看名字就清楚，是用于单词统计的一个工具。

| parameter | desc |
| :--- | :--- |
| -c | 文件字节数 |
| -m | 文件字符数 |
| -l | 文件行数 |

wc 是支持流输入的，这里意味着可以实用管道符号对输入和输出进行连接。

```
cat x.txt | wc -c 
cat x.txt | wc -l
```

---

## ECHO

用于打印的命令：

| parameter | desc |
| :--- | :--- |
| -n | 不加换行符 |
| -e | 解析转义符号 |

echo 常见的是 和重定向符号同时使用。

```
echo -n 'hello world'
echo -e 'hello\n world'
```

---

## PRINTF

C like 的一个命令，实现格式化的打印和输出

`printf format [arguments]` 其基本格式这样。

支持的占位符：

- %.1s
- %% 	百分号 和 py 类似
- \n \r \t

---

## CAT

查看命令（连接文件以及标准输出打印）

| paramater | desc       |
| --------- | ---------- |
| -A        | 全部内容   |
| **-b**    | 显示非空行 |
| **-n**    | 显示行号   |

---

### TAC/REV

行倒序打印，可以用来对数据进行倒序

```shell
cat -bn a.txt | tac
```

字符倒序打印：

```shell
echo '123' | rev
```



---

## CP

常用的文件拷贝工具，这里整理其使用细节：

| parameter | desc                                 |
| --------- | ------------------------------------ |
| **-b**    | 目标文件存在则**创建文件备份后覆盖** |
| -r        | recursion                            |
| -p        | privilege 保留原有的文件权限         |
| -f        | 强制进行文件复制及覆盖               |

`-b` 参数普适用于 文件的操作工具中，mv 同样可以使用用于覆盖备份

---

## MKDIR

创建目录：

```shell
mkdir -p /a/a/a/	# 递归创建目录
# 创建多级目录：
mkdir /opt/test/abc
# 创建多个目录：
mkdir {install,tmp}
# 创建连续目录：
mkdir {a..c}
```

---

## RENAME

用于批量的对文件进行重命名，对文件名中的相同字段进行匹配

```shell
# 把文件夹中的所有的匹配项进行重新的命名
rename .htm .html *.htm
# 将foo1-foo9替换为foo01-foo09：
rename foo foo0 foo?
```



## NAME操作

## dirname

显示文件父文件夹

```shell
dirname [dir]
```

## basename

打印路径的最末级目录

```shell
basename [dir]
```

## DU

**disk usage**, 用于列出文件的磁盘使用

| parameter | desc                   |
| --------- | ---------------------- |
| -b        | 单位以bytes来显示      |
| -c        | 显示总大小             |
| -h        | 自动的显示为易读的格式 |
| -k/-m     | 以 KB，MB 为单位       |
| -s        | 仅显示当前的总大小     |

---

## CUT

对每行数据进行处理，支持流输入。

| parameter | desc                                                |
| --------- | --------------------------------------------------- |
| -b        | 选中单个字符                                        |
| -c        | 选中n个字符                                         |
| -d        | 选择分隔符                                          |
| -f        | 指定显示选中字段， 在进行分组之后的，对字段进行选择 |

cut在对于单行字符串的处理用处很大，下面是使用示例（丢了一个小时的进度很sad，所以直接copy）

```shell
#打印b字符：
echo "abc" |cut -b "2"
b
#截取abc字符：
#echo "abcdef" |cut -c 1-3
abc
#已冒号分隔，显示第二个字段：
echo "a:b:c" |cut -d: -f2
b
```

---

## SEQ / SHUF / SORT /UNIQ

- `seq`	用于生成有序序列

- `shuf`	用于生成乱序序列，支持流输入

- `sort`	用于数据排序	，支持流输入

- `uniq`	用于去掉相邻重复行，所以一般是进行排序之后再使用

```shell
seq 3
seq -f '123%02g' 10
seq 10 | shuf
seq 10 | shuf | sort
python -c "print '500\n' * 50" | uniq
```

---

## TEE

读取标准输入写到标准输出 ，支持流操作

```shell
echo 123 | tee 
echo 123 | tee -a a.out
```

---

## NL

linenumber 	区别于符号链接，用于文件的行号显示

