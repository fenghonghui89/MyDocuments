模态视图专用属性-(iphone/ipad)modalTransitionStyle跳转动画类型/(ipad)modalPresentationStyle样式类型
￼



UIPopoverController
ipad下才有效
创建时类似navi，要包含一个vc

dismissPopoverAnimated:不会触发协议方法，协议方法只有点击屏幕才会调用
作为UIPopoverController的vc，不能自己dismiss自己，只能作为主界面的属性，在主界面调用dismiss，如下
[self.flipsidePopoverController dismissPopoverAnimated:YES];//self为主界面
或者关系紧密，则如下
[self.mainVC.flipsidePopoverController dismissPopoverAnimated:YES];//self为子界面
如果设置主界面为子界面代理，因为delegate是id，无法点出flipsidePopoverController属性，则不能调用后面的方法
[self.delegate.flipsidePopoverController dismissPopoverAnimated:YES];



UISplitViewController
ipad下才有效
协议方法，会在ipad转为竖屏，masterview将要隐藏时和ipad转为横屏，masterview将要显示时调用
detailview vc会在UISplitViewController对象被创建时就会创建

self.splitViewController.viewControllers
splitViewController是uiview的属性
viewControllers只有两个元素，第一个是MasterView的根视图控制器（占用固定320像素），第二个是Detailview的根视图控制器（如果vc被navi包含，则为navi，如果没有，则是vc），masterview的vc在master-detail模板中被UIPopoverController包含，用于协议方法中赋值和置nil，方便隐藏主视图和防止多次实例化






master-detail模板：设备为iphone时，相当于tablview+navi push；当设备为ipad时，相当于SplitViewController+navi+popover+tableview
utility模板：设备为iphone时，相当于view+navi push；当设备为ipad时，相当于navi+popover+view
