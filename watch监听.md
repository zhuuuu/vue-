## 监听
```
watch:{
    name(newVal){
        console.log(newVal)
    }
}
watch 监听每次修改变化的新值
watch 方法默认写的就是handler,vue会去处理这个逻辑,最终编译出来其实就是这个handler

```
## handler方法和immediate属性
```
上述watch的特点是,最初绑定时不会执行,等name改变时才执行监听计算.
若想要一开始就让它最初绑定时就执行,需修改watch写法
watch:{
    name:{
        handler(newVal){
            console.log(newVal)
        },
        immediate:true
    }
}

```
## deep属性(是否深度监听)
```
obj:{
    a:123
}
watch:{
    obj:{
        handler(newVal){
            console.log(newVal,'obj.a')
        },
        immediate:true,
        deep:true
    }
}
监听器会一层层的往下遍历,给对象的所有属性都加上这个监听器,但是这样性能开销就会非常大，修改obj里面任何一个属性都会触发监听器里的 handler。

可以使用字符串形式监听.
watch:{
    'obj.a':{
        handler(newVal){
            console.log(newVal)
        },
        immediate:true
    }
}
Vue会一层一层解析下去，直到遇到属性a，然后才给a设置监听函数
```