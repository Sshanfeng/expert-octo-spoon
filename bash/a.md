### cat
- 创建文件并写入内容
```bash
cat > f.txt << EOF
Hi
Nice to meet you
Where are you come from
EOF
```
- 追加 >>f.txt
- 合并文件
- 当文件名是 `-` 时表示标准输入
- `cat -s` 压缩空行
- `-n` 加行号
- `-b` 空行不加行号
- `-E` 显示结尾为 $
- `-T` 显示tab 为`^I`
- `-v` 显示不可见字符
- 
### grep

### col 去除控制字符
`col -x`将tab替换为空格
### whatis
### which
### whereis
### nl

### tac 反向输出每行
### rev 逐字符反向输出
### pv 显示进度
realpath 显示绝对路径
pager = less
seq 输出序列

grep 
egrep = grep -E
fgrep = grep -F

find 可以接受正则表达式，如果接受正则表达式，则匹配的是全路径
find 
`-o` 或      `-a`与      `!`非
`-print`
`-exec command {} \`
`-prune` 当文件是目录时，不进入此目录搜索，但此目录在搜索结果没



linux shell 的正则表达式，特殊符号要`\`转义，
特殊符号有
`.`
`?`
`+`
`{`  `}`
`[`  `]`
`(`  `)`
`*`
`\`

shell 通配符有

###

### 输入重定向
`<f.txt command` 等价于
`command < f.txt`
0是标准输入，1输出，2错误

2>&1 标准错误重定向到标准输出
2>1 标准错误重定向到文件1


### 
命令后加&表示后台执行

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM0MDcyMTM2OF19
-->