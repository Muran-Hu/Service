# Service
Service 详解

## Service 是一个专门在后台执行长时间操作的类，它并不与用户产生 UI 交互。它提供了两种启动方式。

#### 1. started
###### 其它组件调用 startService() 启动一个 Service。一旦启动，Service 将一直运行在后台，即使启动这个 Service 的组件已经被销毁。通常一个被 start 的 Service 会在后台执行单独的操作，也并不需要给启动它的组件返回结果。只有当 Service 自己调用 stopSelf() 或者其它组件调用 stopService() 才会终止。

#### 2. bind
###### 其它组件可以调用 bindService() 来绑定一个 Service。这种方式会让 Service 和启动它的组件绑定在一起，当启动它的组件销毁的时候，Service 也会自动进行 unBind 操作。同一个 Service 可以被多个组件绑定，只有所有绑定它的组件都进行了 unBind 操作，这个 Service 才会被销毁。

## 注意：
#### 将 android:exported 属性设为 false，表示不允许其他应用程序启动本应用的组件，即便是显式 Intent 也不行（even when using an explicit intent）。这可以防止其他应用程序启动您的 Service 组件。

## 附：Service 生命周期
![示例图片](https://github.com/Muran-Hu/Service/blob/master/service_lifecircle.png)
