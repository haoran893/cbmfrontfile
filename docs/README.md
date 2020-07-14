# 香港中旅系统管理(前端文档)

> 项目基于[React](https://react.docschina.org/)^16.8.6，默认所有代码采用 Hooks 形式进行开发，如无必要不要使用基于 Class 的形式写组件，所有的 react 组件相关代码最好以 jsx 结尾方便查看。

项目是在 [Ant Design Pro](https://pro.ant.design).的基础上进行搭建，默认的 UI 框架[Ant Design](https://ant.design/docs/react/introduce-cn),数据管理[Redux 的封装 DVA](https://dvajs.com/guide/)，具体使用详情可以去相关官网查看

>关于 hooks 的最佳实践，建议在写代码前精读一下文章

[写 React Hooks 前必读](https://juejin.im/post/5e6ccbf86fb9a07cb52bddf1)  
[React Hooks 官方文档以及相关 FAQ](https://react.docschina.org/docs/hooks-intro.html)  
[React Hooks 详解](https://juejin.im/post/5dbbdbd5f265da4d4b5fe57d)

## 环境以及包管理工具

Install `node_modules`:

```
yarn
```

```
npm install
```

## 包管理工具

> 推荐使用[yarn](https://yarn.bootcss.com/)作为包管理工具，下面是一些常用 yarn 命令，其余可去官网查看。

> 安装项目的全部依赖

yarn  
yarn install

>添加依赖包

yarn add [package]  
yarn add [package]@[version]  
yarn add [package]@[tag]

> 将依赖项添加到不同依赖项类别中

> 分别添加到 devDependencies、peerDependencies 和 optionalDependencies 类别中：

yarn add [package] --dev  
yarn add [package] --peer  
yarn add [package] --optional

## 项目环境

使用 cross-env 做为环境管理，目前暂定项目分为 3 个环境，使用

```
REACT_APP_ENV
```

变量名可在项目中代码中拿到当前环境。

```
cross-env REACT_APP_ENV=dev
```

```
cross-env REACT_APP_ENV=pre
```

```
cross-env REACT_APP_ENV=test
```

## Provided Scripts

所有的脚本命令都在 `package.json`. 可以在里面添加或是修改响应的脚本命令：

### 常用的脚本命令

以 mock 数据的形式 run 项目---dev 环境

```
yarn start
```

以拉取服务端数据的形式 run 项目---dev 环境

```
yarn dev
```

## 项目依赖的第三方库(只挑选一些重点的写在这其他的自行了解)

> (https://www.npmjs.com/package/react-cookie) cookie 使用 [UmiJS，antpro 也是基于 umi 进行搭建的，相关文档非常重要](https://umijs.org/zh-CN)  
[Umi Hooks，各种 hooks 的封装非常好用，强烈推荐，项目中很多地方都用到了](https://hooks.umijs.org/zh-CN)  
[DVA ,  基于 redux，redux-saga 的数据流的简化封装](https://dvajs.com/) [Redux-Saga，redux 数据异步解决方案，各种操作符需要熟悉](https://redux-saga-in-chinese.js.org/) [number-precision，项目中数据计算时使用，防止精读丢失](https://github.com/nefe/number-precision)

## 项目结构

> config

所有配置相关的都在这个文件夹下的 config.js 中，[routes.js 中配置所有路由相关的文件](https://pro.ant.design/docs/router-and-nav-cn)。proxy.js 中配置了不同环境对应的服务端地址。

> mock

存放 mock 相关数据的文件夹，[mock.js 的使用自行查看文档](http://mockjs.com/)，参照现有的 mock 文件进行编写，文件命名跟着模块走方便查找。

> src/components

存放项目所有的公共组件，不管是否带有业务只要被不同也面所使用的组件都要放这里。

> src/pages

存放所有的页面，会对应路由配置，单个页面使用的组件直接写在对应的文件夹内，可参考现有的的页面进行管理。

> src/layouts

存放所有的布局组件

> src/models

存放所有业务逻辑以及异步处理

> src/services

存放所有接口 url,供顯影的 models 調用


# 常用组件
## 基础组件
> 基础组件的代码写在/src/components


### 页面头部组件
> 路径 '@ant-design/pro-layout'
```
<PageHeaderWrapper>
</PageHeaderWrapper>

```

### 表单组件
>  路径 'src/components/FormItemComp'

```
里面封装了基本的表单控件
使用onchange 把里面的东西抛出来

```

### 权限组件

## 业务组件
> 路径 /src/components/BussinessComponents

### 评论框
> 路径 /src/components/BussinessComponents/CommentModal 

```
  <CommentModal
        showModal={showComment} // 是否显示
        onCancel={onCancel}     // 取消时间
        operaId={operaId}       // 评论id
        history={props.history} // history跳转
        compType={'1'}          // 公司类型
        dispatch={dispatch}    // dispatch
      />
```

### 根据组织机构选择员工
> 路径 /src/components/BussinessComponents/CommentModal 

```
  <StaffSelect 
    record={record}  // 用于回显
    change={handleChangeSpr}  // 抛出的id组合
    index={index}  // 第几行 
    type={type}    // 类型
  />

```

