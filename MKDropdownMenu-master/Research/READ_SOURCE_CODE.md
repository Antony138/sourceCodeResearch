在进行SolarBeacon的时候，需要用到一个下拉菜单：根据类型，选择搜索不同类型的beacon。

试用了很多，感觉都不太友好或好看（包括GitHub上start最多的项目——搜索*DropdownMenu*），后来发现[maxkonovalov/MKDropdownMenu](https://github.com/maxkonovalov/MKDropdownMenu)很容易用，也满足需求。遂用之。



# About Protocol

[Working with Protocols](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/WorkingwithProtocols/WorkingwithProtocols.html)中写道：

> it's improtant to be able to define a set of behavior that is expected of an object in a given situation.

所以，官方说法，protocol是用来定义类/对象的行为的？

普通的类，「接口/interface」中定义了方法和属性。而一个协议，则是用于给非指定的所有类，定义方法和属性。

procotol还定义了消息传递的约定。

> Protocols Define Messaging Contracts

Check that Optional Methods Are Implemented at Runtime

在实现「Optional Method」的时候，还要先检查是否已经实现了这个方法。

```objective-c
NSString *thisSegmentTitle;
if ([self.dataSource respondsToSelector:@selector(titleForSegmentAtIndex:)]) {
        thisSegmentTitle = [self.dataSource titleForSegmentAtIndex:index];
}
```

`NS_ASSUME_NONNULL_BEGIN`和`NS_ASSUME_NONNULL_END`的作用:在这两个宏之间的代码，所有指针对象都被假定为nonnull，所以只需要显式声明nullable就可以了（对应Swift中的Option类型）