# 这是Introduction



Gitbook访问链接：https://sunyd1006.gitbook.io/forbook/



# 写什么呢

还不知道，先把这个配置好，就可以写书了







## 写书步骤

1. 创建github
2. 在gitbook界面配置
3. 抄一些常见的配置就好了



## Gitbook插件



http://jartto.wang/2020/02/02/about-gitbook/



写入基本配置：

```
{
    "title": "Jartto-GitBook-Demo",
    "description": "Jartto-GitBook-Demo",
    "author": "sphard",
    "language": "zh-hans",
    "root": ".",

    "plugins": [
        "donate",
        "github-buttons@2.1.0",
        "edit-link"
    ],

    "pluginsConfig": {
        "donate": {
            "wechat": "http://jartto.wang/images/wechatpay.jpg",
            "alipay": "http://jartto.wang/images/alipay.jpg",
            "title": "",
            "button": "打赏",
            "alipayText": "支付宝打赏",
            "wechatText": "微信打赏"
        },
        "github-buttons": {
            "repo": "jartto/gitbook",
            "types": [
                "star"
            ],
            "size": "small"
        },
        "edit-link": {
            "base": "https://github.com/jartto/gitbook/master",
            "label": "Edit This Page"
        }
    }
}
```



插件安装通用命令：

```
npm install gitbook-plugin-[插件名]
```



例如：我们要安装 `flexible-alerts` 信息框插件：

```
npm install gitbook-plugin-flexible-alerts
```



效果如下：
![信息框插件](https://raw.githubusercontent.com/chenfengyanyu/my-web-accumulation/master/images/gitbook/plugin.png)



还有很多可用插件，具体如下：

1. 信息框(`flexible-alerts`)
2. 阅读统计（`pageview-count`）
3. 侧边栏宽度可调节（`splitter`）
4. 页脚版权（`page-copyright`）
5. 打赏功能（`donate`）
6. 分享当前页面（`sharing-plus`）
7. 修改标题栏图标（`custom-favicon`）
8. 复选框（`todo`）
9. 显示图片名称（`image-captions`）
10. 目录折叠（`toggle-chapters`）
11. 分章节展示（`multipart`）
12. 插入 `Logo`（`insert-logo`）
13. `Google` 分析（`ga`）
14. 返回顶部（`back-to-top-button`）
15. 代码添加行号和复制按钮（`code`）
16. 高级搜索，支持中文（`search-pro`）
17. 添加 `Github` 图标（`github`）
    …

需要注意的是：
`GitBook` 默认带有 `5` 个插件：

- `highlight`
- `search`
- `sharing`
- `fontsettings`
- `livereload`

如果要去除自带的插件，可以在插件名称前面加 `-`，例如：

```
"plugins":[
    "-search"
]
```



小技巧：`NPM` 中搜索关键字 [`GitBook-Plugin`](https://www.npmjs.com/search?q=gitbook-plugin)，发现更多插件。

