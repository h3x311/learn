# Design

> 记录一些平时看到的可以改进的design tips,另方面我认为前端的设计分为process data-> state management --> how to render,并且我看来数据处理和render是最困难的部分

如果是在一个组件里有自定义的数据,可以把数据放在parent里, 然后通过props传递给child,这样结构更好