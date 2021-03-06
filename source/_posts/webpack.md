---
title: webpack
---
## 打包字体图标和图片的方式(参考：https://github.com/webpack-contrib/file-loader)
    
    使用之前要安装url-loader、file-loader

```bash
{
    test: /\.(woff|woff2|ttf|eot|svg)(\?]?.*)?$/,
    use: [
        {
            loader: "file-loader",
            options: {
                name: "assets/fonts/[name]-[hash].[ext]",
                publicPath: './'
            }
        }
    ]
},

/*
* 这种打包字体的方式会直接以hash的方式重命名
* */
{
    test: /\.(woff|woff2|ttf|eot|svg)(\?]?.*)?$/,
    loader: 'file-loader?publicPath=./&outputPath=assets/fonts/'
},
/*
* 下面的方式可用
* */
{
    test: /\.(woff|woff2|ttf|eot|svg)(\?]?.*)?$/,
    loader: 'file-loader',
    options: {
        name: "assets/fonts/[name]-[hash].[ext]",
        publicPath: './'
    }
},
/*
*也可以把file-loader改成url-loader转成base64编码，但是会扩大内存
*
**/
{
    test: /\.(woff|woff2|ttf|eot|svg)(\?]?.*)?$/,
    use: [
        {
            loader: "url-loader",　　　//如果用file-loader会查询不到资源
            options: {
                name: "assets/fonts/[name]-[hash].[ext]"
            }
        },
    ]
},
{
    test: /\.(jpg|jepg|png|gif)(\?]?.*)?$/,
    use: [
        {
            loader: "file-loader",
            options: {
                name: "assets/imgs/[name]-[hash].[ext]"
            }
        }
    ]
｝
```







