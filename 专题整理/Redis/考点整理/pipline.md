# pipeline

## 使用pipeline的好处

- pipeline和Linux管道类似
- Redis基于请求/响应模型，单个请求处理需要一一应答
- pipeline批量执行指令，节省多次IO往返的时间
- 有顺序依赖的指令建议分批发送
