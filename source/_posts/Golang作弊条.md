---
title: Golang作弊条
date: 2019-09-03 16:06:54
tags:
cat: golang
description: 好记性不如烂笔头。这篇文章是记录一些我常用的Golang的命令和非常容易忘记的。开发的时候速查之用。
---

## 占位符
### 普通占位符
```golang
type People struct {
    Age int 
    Name string 
}

func main (){
    age := 18
    name := "javelin"    
    people := People {
        Age : age,
        Name : name,
    }
}    
```
占位符 | 说明 | 举例 | 输出 
---|---|------|---
%v |相应指的默认格式|fmt.Printf("%v", people)|{18 javelin}
%+v|打印结构体时,会添加字段名|fmt.Printf("%+v", people)|{Age:18 Name:javelin}
%#v|相应值的Go 语言语法|fmt.Printf("%+v", people)|main.People{Age:18, Name:"javelin"}
%%|字面上的百分号|fmt.Printf("%%")|%

### 整数占位符
占位符 | 说明 | 举例 | 输出 
---|---|------|---
%b|二进制数|fmt.Println("%b", 18)|10010
%c|Unicode码点所表示的字符|fmt.Println("%c", 0x45DF)|䗟
%d|十进制表示|fmt.Println("%d", 0x45DF)|1788
%o|八进制表示|fmt.Println("%o", 16)|20
%x|十六进制表示,字母为小写|fmt.Println("%x", x)|b
%X|十六进制表示,字母为大写|fmt.Println("%x", X)|B
%U|Unicode格式：U+1234，等同于 “U+%04X”|fmt.Printf(“%U”, 0x4E2D)|U+4E2D
### 浮点数和字节切片
占位符 | 说明 | 举例 | 输出 
---|---|------|---
%s|输出字符串表示（string类型或[]byte)|fmt.Println("%s", "golang")|golang
%q|双引号围绕的字符串, 由go安全的转义(转义出来带双引号)|fmt.Println("%q", "golang")|"golang"
%x|十六进制，小写字母，每字节两个字符|fmt.Println("%x", "golang")|676f6c616e67
%X|十六进制，大写字母，每字节两个字符|fmt.Println("%x", "golang")|676F6C616E67

### 指针
占位符 | 说明 | 举例 | 输出 
---|---|------|---
%p|十六进制,前缀Ox| fmt.Printf("%p", &people)|0xc000052400








