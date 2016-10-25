
# Foundation
## NSArray
注意数组不能插入nil对象，但数组为nil时可以读取，但创建数组后如果未有元素不能读取，否则会崩

## NSUserDefault
用userdefault可以保存自定义对象，自定义对象要遵守NSCoding协议，对象归档为NSData再用userdefault保存，反过来亦然



# UIKit
## UITableView
如果有100个数据源 reloaddata就会请求100次cell高度的callback


# runtime
参考以下
http://www.jianshu.com/p/58c985408b75
http://www.cocoachina.com/ios/20141018/9960.html
