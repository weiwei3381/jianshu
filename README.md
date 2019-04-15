# 利用react开发简书项目实战

## 项目前期工作

### 创建项目

利用npm安装脚手架工具`create-react-app`, 然后使用`create-react-app jianshu`快速创建简书开发环境.  
创建完毕之后, 在github上建立空白项目, 然后使用下面命令进行初次提交:

```bash
# 初始化git
git init
# 将远程仓库git@github.com:weiwei3381/jianshu.git的别名设为origin
git remote add origin git@github.com:weiwei3381/jianshu.git
# 将master分支推送到远程仓库origin上, 并利用-u指定为默认远程主机, 以后只需要git push就可以默认推送到该位置
git push -u origin master 
```

### css样式管理
提交之后, 精简项目内容, 值得注意的是, 在`index.js`中引入的css文件, 可以直接在下级组件`App.js`中使用. 更深一步, 只要在一个组件中引入css样式, 则在全局项目中都生效, 但是这样会造成css样式之间产生**耦合**, 不利于样式管理. 可以使用第三方模块`styled-components`管理css样式, 安装方法为:  
`npm install --save styled-components@3.3.2`  
需要注意的是, styled-component的v4版本修改了很多api, 例如移除了`injectGlobal`方法, 本项目采用v3版本, 使用`styled-components`管理样式的示例代码如下:

```javascript
import  {injectGlobal}  from 'styled-components';

injectGlobal`
  body {
    margin: 0;
    padding: 0;
    background: green;
  }
  `
```

### 统一浏览器默认样式

使用[reset.css](https://meyerweb.com/eric/tools/css/reset/)可以统一不同浏览器内核的样式, 典型的例如body的间距在不同浏览器的默认值是不一样的, 为此, 通过`reset.css`可以将所有的默认实现进行统一.