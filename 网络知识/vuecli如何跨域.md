## vuecli内部集成了 webpack-dev-server , 而webpack-dev-server 集成了一个本地的express
跨域配置参数配置方式1
``` javascript
{
    module.exports = {
        ...
        ...
        devServer = {
            headers : {
                "Access-Allow-Origin" : "*"
            }
        }
    }
}
```
跨域配置参数配置2 
[参考链接：express如何设置返回的headers](https://expressjs.com/en/4x/api.html#res.set)
``` javascript
{
    module.exports = {
        ...
        ...
        devServer : {
            before: app => {
                app.all('*', function (req, res, next) {
                    res.set('Access-Control-Allow-Origin', '*')
                    next();
                });
            },
        }
    }
}
```