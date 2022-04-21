## 定制协议

通过 `Lua API` 我们可以非常容易的定制自己的网络通讯协议。

## 入口文件

每个 lua 入口文件都必须包含这些方法：`init`、`on_connect`、`protocol_input`、`on_close`、`protocol_input`、`protocol_decode`、`protocol_encode`、`on_message`

## Lua API

`mix` 全局模块方法

|  方法   | 描述  |
|  ----  | ----  |
| mix.queue.new(name, size)  |  |
| n, err = mix.queue.push(name, data)  |  |
| s, err = mix.json_encode(data)  |  |
| tb, err = mix.json_decode(str)  |  |
| s = mix.base64_encode(data)  |  |
| s, err = mix.base64_decode(str)  |  |
| s, err = mix.php_pack(format, args+)  |  |
| tb, err = mix.php_unpack(format, data)  |  |
| tb = mix.str_split(str, sep)  |  |
| s = mix.bytes_tostring(bytes_table)  |  |
| s = mix.md5(data)  |  |
| s = mix.md5_bin(data)  |  |
| s = mix.sha1(data)  |  |
| s = mix.sha1_bin(data)  |  |
| b = mix.log(mix.INFO, msg)  | mix.DEBUG,mix.INFO,mix.WARN,mix.ERROR |

`mix.conn` 对象方法

|  方法   | 描述  |
|  ----  | ----  |
| n = conn:client_id()  |  |
| s = conn:remote_addr()  |  |
| tb = conn:context()  |  |
| any = conn:context_value("key")  |  |
| any = conn:wait_context_value("user_id")  |  |
| conn:set_context({ user_id = 10000 })  | 可远程执行 |
| conn:set_context_value("user_id", 10000)  | 可远程执行 |
| err = conn:subscribe("channel1", "channel2")  | 可远程执行 |
| err = conn:unsubscribe("channel1", "channel2")  | 可远程执行 |
| err = conn:send(data)  |  |
| err = conn:close()  |  |
| conn:clear_buffer()  |  |

`mix.buffer` 对象方法

| 方法                       | 描述  |
|--------------------------| ----  |
| s = buf:tostring()       |  |
| s, err = buf:read(2) |  |
| n = buf:position()   |  |
| n = buf:length()     |  |