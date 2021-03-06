# 按键模拟指令

基于Socket-command的指令包。  
可以通过一行指令来执行连续的按键输入。  

------

按键模拟指令Key为`press`

例如在客户端输入:

```shell
press alt tab
```

即可模拟切换应用的按键。  
目前支持108键的所有按键模拟，类似于回车这类按键请用`enter`这种写于按键上的英文标识代替。

------

支持字符连输模式，默认关键词为`LINE`

例如在客户端输入：

```shell
press line ping 127.0.0.1
```

服务端即会使用`ping 127.0.0.1`。  
字符连输模式支持以下字符：
* 大写、小写字母
* 数字及其上方符号`!@#$%^&*()`
* 其他常用符号<code>`~-_=+[{]}\|;:'".>,</? </code>
* 空格

__注意__：
1. 这里的输入方式都是模拟按键，所以请注意输入法与默认大小写。
2. 当服务端开启大写时，输入`A`会输出`a`，因为大写字母使用的是`SHIFT + A`方式输入
3. 当服务端当前为中文输入法时，输入`nihaoya1`则会输入`你好鸭`

------

配置说明：

```json
{
  "interval" : 20,
  "max" : 20,
  "lineLink": "LINE"
}
```

| 参数名称     | 参数类型        | 参数说明                                 |
|----------|-------------|--------------------------------------|
| interval | 数字          | 每个按键的间隔时间（毫秒）                        |
| max      | 数字          | 单次指令最大的按键执行数量                        |
| lineLink | 字符串（不区分大小写） | 字符连输指令（例如“press line ping 127.0.0.1” |