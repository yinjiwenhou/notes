# react 

## react 

## redux

## react-redux
1. 定义App组件（antd && styled-components)
2. 组件要使用redux提供的Provider标签包裹App组件，并提供store属性；
   此时需要获取store，store需要使用redux提供的createStore函数定义，接受一个reduce参数；
   reduce是一个纯函数，其入参分别是store和action，store不可变，action是一个包含的操作意图和数据的对象；
   App组件中需要使用recat-redux提供的connect函数连接store；
   connect入参提供两个映射函数，分别是mapStateToProps和mapDispatchToProsp；
   组件中都将使用this.props访问store中的数据，和发送action的形式更新store中的数据；
## react-router-dom

## immutable.js

## styled-component

## axios
