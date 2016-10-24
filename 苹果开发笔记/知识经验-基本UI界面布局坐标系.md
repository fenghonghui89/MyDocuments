

# Autoresizing（局限性：所有的自动布局坐标全部都是参照父视图）
是什么？
		一个旧版的自动布局技术
		操作非常简单、api也很简单
		但是功能有局限性
		现在依然生效
干什么？
		帮助你管理子view的布局
		当父view的大小改变时
		它会帮你把所有的子view找到合适的位置和大小
		（会自动计算每一个子view合理的frame并赋值）
怎么用？
		外框负责约束子view和父view边界的间距
		内框负责约束子view自己的宽高是否缩放
		横向：左边距、宽、右边距
		纵向：上边距、高、下边距
		尽力让横向和纵向各有一个是可变的，其它都不可变
布局代码与autoresizing混合使用
		autoresizing只是帮你进行部分的布局
		如果有些特殊的布局效果它做不到
		你就可以在
		vc -> viewDidLayoutSubviews消息内补充实现自定义的高级的布局效果
		V -> layoutSubviews [super layoutSubviews]下面补充实现自定义的高级的布局效果
局限性
		所有的自动布局全部都是参照父视图

************************************************************************************************************************************************
************************************************************************************************************************************************

# autolayout

注意：
			尽量不要在代码中给个任何view直接设置frame

什么时候用？
			用于展示信息，控件比较多，没有使用transform（注意：transform与autolayout会有些冲突）

代码方式（不用深究）
	万能公式
			view1.attr1 = view2.attr2 * multiplier + constant
			类似于y = kx + b

			button.frame.origin.x = 10;
			button.left = 10;
			button.left = 0 + 10;
			button.left = self.view.left + 10;
			button.left = self.view.left * 1 + 10;

			button.frame.origin.x = self.view.bounds.size.width - 10 - button.frame.size.width;
			button.frame.origin.x + button.frame.size.width = self.view.bounds.size.width - 10 ;
			button.right = self.view.width - 10;
			button.right = self.view.width * 1 + (-10);

			button.frame.size.width = 60;
			button.width = 60;
			button.width = 0 + 60;
			button.width = nil.nil * 0 + 60;

			button1.frame.size.width = button2.frame.size.width;
			button1.width = button2.width;
			button1.width = button2.width * 1 + 0;
			[Demo8]
		注意：1.要关闭把Autoresizing翻译成Autolayout 2.addSubview必须写在约束之前			

	VFL
			1)	什么是？
				Visual Format Language 可视化有格式语言
			2)	基本步骤
				1)	构建控件 修改控件 把控件加入到视图
				2)	关掉 Autoresizing 到 autolayout 的自动翻译
				3)	创建约束（可以在帮助文档查询“Visual Format Syntax”参考）
				4)	把约束加到视图上

折叠
xib的需要折叠的view的高度约束拖线到文件，动态修改该约束的contant值，多余的约束属性拖线要删除

界面已经显示，运行时数据改变了，需要从新布局——[self setNeedsLayout]
************************************************************************************************************************************************
************************************************************************************************************************************************


视图生命周期
vc viewDidLoad
|
vc VIewWillAppear
vc viewWillLayoutSUbview（旋屏时会再次调用）
view layoutSubviews
vc viewDidLayoutSubview（旋屏时会再次调用）
vc viewDidAppear
|
vc viewWillDisappear
vc viewDidDisappear

旋屏时
bounds 会根据方向改变
frame 不会改变，依然是按照Portrait
[[UIScreen mainScreen] bounds]                       不会改变依然是按照Portrait
[[UIApplication sharedApplication] keyWindow].bounds 不会改变依然是按照Portrait
[[UIApplication sharedApplication] keyWindow].frame 不会改变依然是按照Portrait

隐藏掉statusbar后，frame旋转不会变

获取旋屏方向
UIInterfaceOrientation interfaceOrientation = (UIInterfaceOrientation)[[UIApplication sharedApplication] statusBarOrientation];
下面两者不一样
UIDeviceOrientationLandscapeLeft
UIInterfaceOrientationLandscapeLeft
UIDeviceOrientation      是机器硬件的当前旋转方向   这个你只能取值 不能设置
UIInterfaceOrientation   是你程序界面的当前旋转方向   这个可以设置

键盘显示的情况下旋屏：收起键盘-旋转-打开键盘
//添加旋屏通知后要手动调用一次旋屏触发事件，否则页面刚出现时不会坐标不会调整


************************************************************************************************************************************************
************************************************************************************************************************************************


storyboard下cell正向传值
方法1：
1.cell连线到指定页面，设置segue ID
2.tvc中做如下设置：（注：如果这时用方法2，会报动画重复警告，造成传值错误）
```
-(void)prepareForSegue:(UIStoryboardSegue *)segue sender:(id)sender
{
    if ([segue.identifier isEqualToString:@"changeNote"]) {
        HFChangeNoteViewController *changeNoteViewController = segue.destinationViewController;
        changeNoteViewController.noteDataIndex = [self.tableView indexPathForSelectedRow].row;
    }
}

方法2：
如果页面中已经有按钮做segue跳转到被推出页面，而点击cell后也需要跳转到该页面，但功能不一样，则cell不用连线，tvc中做如下设置：
-(void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath
{
    NSNumber *sender = [NSNumber numberWithInt:indexPath.row];
    [self performSegueWithIdentifier:@"changeNote" sender:sender];
}
-(void)prepareForSegue:(UIStoryboardSegue *)segue sender:(id)sender
{
    if ([segue.identifier isEqualToString:@"changeNote"]) {
        HFChangeNoteViewController *changeNoteViewController = segue.destinationViewController;
        if ([sender isKindOfClass:[NSNumber class]]) {
            long index = [sender longValue];
            changeNoteViewController.noteDataIndex = index;
        }
    }
}
```


storyboard-segue-点击cell跳转：连线不要用cell连线到下一个页面，最好是tableview连线到下一个界面
 NSInteger index=[[self.tableView indexPathForCell:sender]row];

************************************************************************************************************************************************
************************************************************************************************************************************************

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


 ************************************************************************************************************************************************
 ************************************************************************************************************************************************

 不加navi、加navi（透明/不透明）
 2015-11-20 02:40:58.463 testtab[2776:87110] 1l {{0, 0}, {375, 667}} {{0, 64}, {320, 435}}
 2015-11-20 02:40:58.464 testtab[2776:87110] 1w {{0, 0}, {375, 667}} {{0, 64}, {320, 435}}
 2015-11-20 02:40:58.469 testtab[2776:87110] 1wl {{0, 0}, {375, 554}} {{0, 64}, {320, 435}}
 2015-11-20 02:40:58.469 testtab[2776:87110] 1dl {{0, 0}, {375, 554}} {{0, 20}, {375, 534}}
 2015-11-20 02:40:58.972 testtab[2776:87110] 1d {{0, 64}, {375, 554}} {{0, 20}, {375, 534}}
 2015-11-20 02:40:58.973 testtab[2776:87110] 1wl {{0, 64}, {375, 554}} {{0, 20}, {375, 534}}
 2015-11-20 02:40:58.973 testtab[2776:87110] 1dl {{0, 64}, {375, 554}} {{0, 20}, {375, 534}}
 注：
 self.view的bounds在viewWillLayoutSubviews开始获取才是正确的值
 self.view的frame在viewDidApperar开始获取才是正确的值

 subview的bounds在viewDidLayoutSubviews开始获取才是正确的值
 subview的frame在viewDidLayoutSubviews开始获取才是正确的值

 ios6
 screen.bounds.size:320 480
 vc.view.bounds.size:320 460（会减去20stateBar）（透明或不透明都一样）
 naviH:44
 vc.view原点相对screen位置：透明(0,0)，不透明(0,naviH)

 ios7
 screen.bounds.size::320 480
 vc.view.bounds.size:320 480 （透明或不透明都一样）
 naviH:44
 vc.view原点相对screen位置：透明(0,0)，不透明(0,naviH+stateH)

 ios8
 screen.bounds.size::320 480
 vc.view.bounds.size:320 480 （透明或不透明都一样）
 naviH:44
 vc.view原点相对screen位置：透明(0,0)，不透明(0,naviH+ stateH)

 ************************************************************************************************************************************************
 ************************************************************************************************************************************************

 # 状态栏
 ## 使statusbar不透明（代码方式，sb方式未解决）
 - 1.用navi包住rootvc
 - 2.rootvc设置navi隐藏

 ```
  [self.navigationController setNavigationBarHidden:YES animated:NO];
 ```
 - 3.这样操作后，新建webview，frame(0 0 screenw screenh),加载页面后,效果就出来了

 判断某UI控件自身是否还存在 不是用if(!self)，而应该用if(!self.superView)
