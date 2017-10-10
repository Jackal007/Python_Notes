## Configurations

### requests.defaults

This module provides the Requests configuration defaults.

| base\_headers | 默认HTTP头. |
| :--- | :--- |
| verbose | Stream to write request logging to. |
| max\_redirects | 重定向的最多次数 |
| keep\_alive | Reuse HTTP Connections? |
| max\_retries | 连接失败后重试的次数 |
| danger\_mode | 如果设置成True，出现错误会立即报告 |
| safe\_mode | 如果设置成True，Requests 会捕获所有异常 |
| pool\_maxsize | Http连接池大小的最大值 |
| pool\_connections | 可使用的激活HTTP连接池的数量 |



