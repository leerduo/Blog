title: MessageHandler
date: 2016-01-16 17:36:03
tags:
- Handler
- Message
- Thread safe
- recycle
- project

---

这个组件是一个简单小巧的Handler转发，主要是为了对外提供绑定目标Handler对象的所有消息的`暂停`、`恢复`、`废弃`、`取消所有队列中的消息`，用于整个完全解耦消息队列的全局性有效管理。

> [ENGLISH](https://github.com/Jacksgong/MessageHandler/blob/master/README.md)

---

> 随着RxJava的普及，逐渐有一些文章出来，提出了EventPool/Handler这些抛事件的架构已死或不建议使用的说法，而无非就是不易于调试，不够灵活。

> 个人觉得确实很多事务用RxJava可以解决。但是就解耦，全局的大架构，还是这类抛事件的更易于阅读代码更加干净，甚至更易于全局性控制。
如picasso，业务非常的复杂，因此内部使用了Handler抛事件的方式来促使事务流的运作。

<!-- more -->

## 简述所解决问题

系统提供的Handler用于解决跨线程抛消息，复杂的事务流固然方便，但是缺少全局性的控制，如暂停，恢复等，故有了这个基于`android.os.Handler`进行上层封装转发实现全局控制功能的组件。

## Demo

![][demo_gif]

## 在项目中引用

```
dependencies {
    compile 'cn.dreamtobe.messagehandler:messagehandler:0.0.9'
}
```


## 使用场景

如demo中的，需要全局暂停、恢复、清理、干掉整个消息队列，比如有复杂交错的消息传递逻辑需要全局性控制，这个`MessageHandler`将会有奇效。

## 使用

> 所有方法都是线程安全

| 方法名 | 功能 |
| --- | --- |
| pause(void) | 暂停所有消息(所有delay的事件在这个时刻冻结)，暂停期间有任何消息也一并冻结
| resume(void) | 恢复所有消息(根据冻结时刻的事件，解冻delay的时间，重新发送消息)
| cancelAllMessage(void) | 清理所有已经在队列中等待触发的消息
| killSelf(void) | 废弃当前Handler，不再接受任何消息处理


> 以下接口与Handler中提供的功能相同

| 方法名 | 功能 |
| --- | --- |
| sendEmptyMessage(what) | 同`Handler#sendEmptyMessage`
| sendEmptyMessageDelayed(what, delayMillis) | 同`Handler#sendEmptyMessageDelayed`
| sendMessage(msg) | 同`Handler#sendMessage`
| sendMessageDelayed(msg, delayMillis) | 同`Handler#sendMessageDelayed`
| sendMessageAtTime(msg, uptimeMillis) | 同`Handler#sendMessageAtTime`
| sendMessageAtFrontOfQueue(msg) | 同`Handler#sendMessageAtFrontOfQueue`
| post(runnable) | 同`Hanler#post`
| postDelayed(runnable, delayMillis) | 同`Hanler#postDelayed`
| removeMessages(what) | 同`Handler#removeMessages`
| removeCallbacks(runnable) | 同`Handler#removeCallbacks`
| obtainMessage(void):Message | 同`Handler#obtainMessage`

## LICENSE

```
Copyright (c) 2016 Jacksgong(blog.dreamtobe.cn).

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

## Open Source

[Jacksgong/MessageHandler](https://github.com/Jacksgong/MessageHandler)

[license_2_svg]: https://img.shields.io/hexpm/l/plug.svg
[bintray_svg]: https://api.bintray.com/packages/jacksgong/maven/MessageHandler/images/download.svg
[bintray_url]: https://bintray.com/jacksgong/maven/MessageHandler/_latestVersion
[demo_gif]: https://github.com/Jacksgong/MessageHandler/raw/master/art/demo.gif
