### 路径

| 路径         | 含义                                              | 事例                    |
| ------------ | ------------------------------------------------- | ----------------------- |
| 绝对路径     | 以根目录做起点，描述路径的方式，路径以/开头       | `cd /` `cd /src/test`   |
| 相对路径     | 以当前目录做起点，描述路径的方式，路径不需以/开头 | `cd test` `cd src/test` |
| 特殊路径`.`  | 当前路径                                          | `cd .` `cd ./test`      |
| 特殊路径`..` | 上一级目录                                        | `cd ../test`            |
| 特殊路径`~`  | 用户的 HOME 目录                                  | `cd ~` `cd ~/test`      |

### 通配符

符号* 表示通配符，即匹配任意内容（包含空），示例：
| 事例 | 含义 |
|---|---|
| test* | 匹配任何以 test 开头的内容 |
| *test | 匹配任何以 test 结尾的内容 |
| *test\* | 匹配任何包含 test 的内容 |

### 管道符

管道符：| 它的含义是：将管道符左边命令的结果，作为右边命令的输入

```bash
ls  | grep test
```

### 重定向符

重定向符号有两个`>`和`>>`
| 符号 | 内容 | 事例|
|---|---|---|
| ">" | 将左侧命令的结果，覆盖写入到符号右侧指定的文件中 | `echo "rewrite content" > test.txt`
| `>>`|将左侧命令的结果，追加写入到符号右侧指定的文件中| `echo "append content" >> test.txt`

### 文件 API

| 指令                                                        | 事例                                                                 | 内容                                                       | 其他说明                                                                                      |
| ----------------------------------------------------------- | -------------------------------------------------------------------- | ---------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| ls [-a -l -h] [path]                                        | `ls -a` `ls -lh`                                                     | 列出目录下的内容                                           | -a 表示所有，-l 表示以列表展示更多内容，-h 表示以易于阅读的形式列出文件大小                   |
| cd [path]                                                   | `cd` `cd ../` `cd /home`                                             | 进入某个目录                                               | 不写参数`cd`表示进入用户 home 目录                                                            |
| pwd                                                         | `pwd`                                                                | 查看当前工作目录                                           |
| mkdir [-p] path                                             | `mkdir test` `mkdir -p src/components/test`                          | 创建文件夹                                                 | -p 选项可选，表示自动创建不存在的父目录，适用于创建连续多层级的目录                           |
| touch path                                                  | `touch a.js`                                                         | 创建文件                                                   |
| cat path                                                    | `cat a.js`                                                           | 查看文件内容                                               |
| more path                                                   | `more a.js`                                                          | 查看文件内容（部分）                                       | 通过空格翻页,按 q 退出查看                                                                    |
| cp [-r] path1 path2                                         | `cp a.js b.js` `cp -r src src1`                                      | 复制路径                                                   | -r 选项可选，用于复制文件夹使用，表示递归                                                     |
| mv path1 path2                                              | `mv src public/src` `mv a.js b.js`                                   | 移动文件或文件夹                                           | 如果目标不存在，则进行改名                                                                    |
| rm [-r -f] path1 path2 path3                                | `rm -rf /test` `rm -f test.js`                                       | 删除文件或文件夹                                           |
| which command                                               | `which mkdir` `which node`                                           | 查找命令的程序文件存放在哪里                               |
| find path -name "被查找的文件名" find path -size +\|-n[kMG] | `find ./ -name "index.html"` `find ./ -size 1M` `find ./ -size -20k` | 查找符合规则的文件                                         | +、- 表示大于和小于,n 表示大小数字,kMG 表示大小单位，k(小写字母)表示 kb，M 表示 MB，G 表示 GB |
| grep [-n] keyword path                                      | `grep hello text.txt` `grep -n hello text.txt` `ls -l                | grep index.\*`                                             | 从文件或者输入端口（前一个命令返回值）中通过关键字过滤文件行                                  | -n 表示是否显示行数 |
| wc [-c -m -l -w] path                                       | `wc -l test.js` `wc -c test.js`                                      | 从文件或者输入端口（前一个命令返回值）中获取文件的统计信息 | -c bytes 数量，-m 字符数量，-l 行数，-w 单词数量                                              |
| echo content                                                | `echo "test content"`                                                | 输出指定内容                                               | 被飘号"`"包围的内容，会被作为命令执行,因为可能有空格或\等特殊符号，建议使用双引号包围         |
| tail [-f -num] path                                         | `tail -f -5 test.txt` `tail -5 test.txt`                             | 查看文件尾部内容                                           | -f 表示跟踪文件更改 -num 表示查看尾部多少行。                                                 |
