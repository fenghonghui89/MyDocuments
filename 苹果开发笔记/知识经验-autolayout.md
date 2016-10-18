day14
{AM1}
一、	布局
	1.	V - View布局子View
		layoutSubviews
		1)	干什么？
			给view对象一个机会去布局子view
		2)	什么时候被调用
			VC的大小尺寸改变的时候
			先调用      	VC -> viewWillLayoutSubviews
			在调用	V -> layoutSubviews
			最后调用	VC -> viewDidLayoutSubviews
		[Demo1]

		补充：界面已经显示，运行时数据改变了，需要从新布局——[self setNeedsLayout]

二、	Autoresizing（局限性：所有的自动布局坐标全部都是参照父视图）
	1.	是什么？
		一个旧版的自动布局技术
		操作非常简单、api也很简单
		但是功能有局限性
		现在依然生效

	2.	干什么？
		帮助你管理子view的布局
		当父view的大小改变时
		它会帮你把所有的子view找到合适的位置和大小
		（会自动计算每一个子view合理的frame并赋值）

	3.	怎么用？
		外框负责约束子view和父view边界的间距
		内框负责约束子view自己的宽高是否缩放

		[Demo2]

		横向：左边距、宽、右边距
		纵向：上边距、高、下边距

		尽力让横向和纵向各有一个是可变的，其它都不可变
		[G01]

		[Demo3]

	4.	布局代码与autoresizing混合使用
		autoresizing只是帮你进行部分的布局
		如果有些特殊的布局效果它做不到
		你就可以在
		vc -> viewDidLayoutSubviews
			 消息内补充实现自定义的高级的布局效果
		V -> layoutSubviews
			[super layoutSubviews]
			下面补充实现自定义的高级的布局效果

	5.	局限性
		所有的自动布局全部都是参照父视图
		{PM1}
	6.	代码方式
		1)	时机
			针对在运行时代码添加的子view设置布局管理
		2)	步骤
			1>	先给出一个在当前父view下的正确的位置
			2>	再设置autoresizingMask（指明在变化时，坐标如何改变）

			[Demo4]
		3)	| 位运算

			1 << 0	1	0000 0001
			1 << 1	2	0000 0010
			1 << 2	4	0000 0100
			1 << 3	8	0000 1000
			1 << 4	16	0001 0000

			a			0001 0000
			b			0010 0000
			c			0000 0010	|或运算
			-------------------------
			r			0011 0010

			f			0000 0010	&且运算
			-------------------------
						0000 0010

三、	Autolayout
	1.	什么是？
		是新版的自动布局技术
		6.0版本之后支持
		功能超级强大
		但是：操作比较复杂*
			Xcode 4 autolayout 设置 超级变态
			Xcode 5 autolayout 设置 还好

	2.	基本原理
		是通过约束的方式描述界面内视图应该保持的位置/大小
		约束可以跟父view 甚至可以跟其它任何view

	3.	第一个autolayout
		[Demo5]

	4.	两大原则
		颜色
			蓝色	对	符合autolayout的两大原则
			橙色	错	不符合autolayout的两大原则
		原则
			描述清晰
			互不冲突

	5.	描述
		1>	各种对齐约束

		2>	各种间距约束

		3>	最佳大小
			UIButton
			UILabel
			UIStepper

		4>	直接指定大小

		5>	参考其它控件

	练习
		1.	一个UIImageView在屏幕的右上角
			宽高都是60，距离屏幕上右各10间距
			一个UITextView距离屏幕上左下各10间距
			UIImageView UITextView横向10间距
			[Demo6]

		2.	让两个按钮在屏幕的上方
			左按钮距离屏幕左上各10间距
			右按钮距离屏幕右上各10间距
			两个按钮宽度一致，两个按钮横向间距保持10
			[Demo7]

			4:20公布答案

	6.	Xcode 4 中的变态版Autolayout
		紫色	系统自动补齐的约束
		蓝色	自己增加的约束

		1)	拖新控件到界面上的时候，系统会自动“帮助”你增加约束以满足两大原则
		2)	手动添加的蓝色约束 会使部分冲突的紫色系统约束“自动”消失
		3)	当你删除蓝色约束的时候， 系统会再重新“帮助”你增加紫色约束
		4)	紫色的约束无法删除
		5)	当你有多个控件，系统必然会增加N条紫色的约束
		6)	系统增加约束的时候，“智能”添加
		7)	当你添加蓝色约束，系统会“更智能”的帮助添加蓝色的约束

	{PM3}
	7.	深入
		基本：
			约束是描述当父view的大小改变时，控件应该如何修改自己的大小/位置
			真正在干的事情，就是通过各种约束计算出每一个子view的frame并赋值

		注意：
			尽量不要在代码中给个任何view直接设置frame

		什么时候用？
			用于展示信息，控件比较多，没有使用transform（注意：transform与autolayout会有些冲突）

	8.	代码方式（不用深究）
		1.	万能公式
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

		2.	VFL
			1)	什么是？
				Visual Format Language 可视化有格式语言
			2)	基本步骤
				1)	构建控件 修改控件 把控件加入到视图
				2)	关掉 Autoresizing 到 autolayout 的自动翻译
				3)	创建约束（可以在帮助文档查询“Visual Format Syntax”参考）
				4)	把约束加到视图上
				[Demo9]

		3.	常见的运行时错误
			1>	违反描述清晰
				控制台会看到下面这个单词
				ambigious
			2>	违反互不冲突
				控制台会看到下面这些单词
				unable to .... statisfy .....




ß
设置某个控件的保持宽高比，宽=父视图的0.5
https://segmentfault.com/q/1010000002428070
控件拖线到父视图 选择 equal width 检查器修改比例
然后控件的al设置里面aspect ratio和width打钩
	
