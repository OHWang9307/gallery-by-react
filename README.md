<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
<style>
img{
width:200px;
height:200px;
}
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote {
    margin: 0;
    padding: 0;
}
body {
    font-family: "Helvetica Neue", Helvetica, "Hiragino Sans GB", Arial, sans-serif;
    font-size: 13px;
    line-height: 18px;
    color: #737373;
    background-color: white;
    margin: 10px 13px 10px 13px;
}
table {
    margin: 10px 0 15px 0;
    border-collapse: collapse;
}
td,th { 
    border: 1px solid #ddd;
    padding: 3px 10px;
}
th {
    padding: 5px 10px;  
}

a {
    color: #0069d6;
}
a:hover {
    color: #0050a3;
    text-decoration: none;
}
a img {
    border: none;
}
p {
    margin-bottom: 9px;
}
h1,
h2,
h3,
h4,
h5,
h6 {
    color: #404040;
    line-height: 36px;
}
h1 {
    margin-bottom: 18px;
    font-size: 30px;
}
h2 {
    font-size: 24px;
}
h3 {
    font-size: 18px;
}
h4 {
    font-size: 16px;
}
h5 {
    font-size: 14px;
}
h6 {
    font-size: 13px;
}
hr {
    margin: 0 0 19px;
    border: 0;
    border-bottom: 1px solid #ccc;
}
blockquote {
    padding: 13px 13px 21px 15px;
    margin-bottom: 18px;
    font-family:georgia,serif;
    font-style: italic;
}
blockquote:before {
    content:"\201C";
    font-size:40px;
    margin-left:-10px;
    font-family:georgia,serif;
    color:#eee;
}
blockquote p {
    font-size: 14px;
    font-weight: 300;
    line-height: 18px;
    margin-bottom: 0;
    font-style: italic;
}
code, pre {
    font-family: Monaco, Andale Mono, Courier New, monospace;
}
code {
    background-color: #fee9cc;
    color: rgba(0, 0, 0, 0.75);
    padding: 1px 3px;
    font-size: 12px;
    -webkit-border-radius: 3px;
    -moz-border-radius: 3px;
    border-radius: 3px;
}
pre {
    display: block;
    padding: 14px;
    margin: 0 0 18px;
    line-height: 16px;
    font-size: 11px;
    border: 1px solid #d9d9d9;
    white-space: pre-wrap;
    word-wrap: break-word;
}
pre code {
    background-color: #fff;
    color:#737373;
    font-size: 11px;
    padding: 0;
}
sup {
    font-size: 0.83em;
    vertical-align: super;
    line-height: 0;
}
* {
    -webkit-print-color-adjust: exact;
}
@media screen and (min-width: 914px) {
    body {
        width: 854px;
        margin:10px auto;
    }
}
@media print {
    body,code,pre code,h1,h2,h3,h4,h5,h6 {
        color: black;
    }
    table, pre {
        page-break-inside: avoid;
    }
}
</style>
# gallery-by-react
## a photo gallery project based on react

基于ReactJS构架的图片画廊应用-仿造慕课网课程编写

因为课程是老版本，和最新版本有很多不同，改动了一些东西，自己也进了不少了坑，多少次有想死的感觉，想放弃，又于心不忍，还好一步一步填完了所有的坑，最终实现了想要达到的效果

```
git clone https://github.com/cllgeek/gallery-by-react
npm i
npm start
```

完事会自动打开http://localhost:8000/webpack-dev-server/可看效果

如果你想先睹为快，也可通过 https://cllgeek.github.io/gallery-by-react/ 查看效果

当然，学一门新技术可能会遇到很多问题，尤其是最新版本和教程已经有很不同之处，这需要有足够的耐心，一步一步去解决它。

<!--more-->

## 项目搭建

尤其是刚开始项目搭建的时候就会遇到很多问题，比如：

`yo react-webapack projectName`之后不会出现很教程里面类似的目录，这时候，不要方，试想一下，版本的迭代更新之后，肯定是向着越来越简单的方向走的，比如没有Gruntfile.js，没有关系，很多都已经迁移到webpack.config.js和cfg/defaults.js下了

还有一点是刚开始的时候把post-css选为yes,因为后面用到的autoprefixer-loader is deprecated，具体可看

 https://github.com/passy/autoprefixer-loader

## 命令

启动命令改了：`npm start`

build命令也改了：`npm run dist`

可参考官网

https://github.com/react-webpack-generators/generator-react-webpack

`npm ls -g --depth=1 2>/dev/null | grep generator- `

这个命令运行之后 可查看generator的各个版本

## .eslintrc文件

.eslintrc文件里面可以加一些代码检查：

比如我加了强制分号结尾

```
"semi": [2, "always"],//语句强制分号结尾
```

具体可查看[eslint](http://eslint.org/)，我发现了一篇文章也不错[01-Eslint静态代码检查](http://www.jianshu.com/p/1682b91756b1)

## css get到的

scrollWidth：对象的实际内容的宽度，不包边线宽度，会随对象中内容超过可视区后而变大。 

clientWidth：对象内容的可视区的宽度，不包滚动条等边线，会随对象显示大小的变化而改变。 

offsetWidth：对象整体的实际宽度，包滚动条等边线，会随对象显示大小的变化而改变。

## 其他要注意的地方

* 关于调试react,可以下个chrome的插件很方便 React Developer Tools 真的超级方便,不会用的联系我哈
* webpack的注意点:如果不加json-loader的话,main.js中获取json要这样写require('json!../data/imageDatas.json')
* 使用ReactDOM.findDOMNode注意要导入react-dom 还有和this.refs的区别
* 还有就是如果要把项目推送到gh-pages的话,注意把src目录下index.html中的/assets/app.js/和cgf/default.js中的publicPath改为相对路径

```
//少了个斜杠
singeImageData.imageUrl = require('../images/'+singeImageData.fileName);
```

```
//因为' is-inverse'没加空格
imgFigureClassName += this.props.arrange.isInverse ? ' is-inverse' : '';
```

切不可大意，不过遇到问题，慢慢解决就好，代码不会犯错，只有人会犯错
```css
img{
width:200px;
height:200px;
}
```
## 最后
有问题可以联系我![image](https://cllgeek.github.io/uploads/weixin.gif)
[materliu](https://github.com/materliu)是个非常好的带有文艺气息的高水平的程序员，已经路转粉了。
