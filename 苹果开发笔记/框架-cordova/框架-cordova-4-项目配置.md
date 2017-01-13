


# 打开其他页面

- 1.如果需要打开其他html文件，新建一个文件夹，把其他html文件放入到文件夹里面，添加到工程当中（注意选择Create folder references），然后调用cordova webview的时候添加如下代码指定

```
viewController.wwwFolderName = @"www”;//指定网页文件夹
viewController.startPage = @"my.html”;//指定网页文件夹的html文件
```

- 2.如果需要打开特定首页，而不是默认的项目内index.html，在config.xml里面做如下修改：

```
<content src="http://www.baidu.com" /> //默认为index.html
<access origin="*" />
<allow-navigation href="*" /> //允许全部http及https网站
<allow-navigation href="http://*/*" />
<allow-navigation href="https://*/*" />
```
或者做如下修改
```
- (void)viewDidLoad
{
  self.startPage = @"http://www.baidu.com";
  [super viewDidLoad];
  
  // Do any additional setup after loading the view from its nib.
}
在config.xml添加<allow-navigation href="*" />
```

- 3.如果是https网站，额外要在AppDelegate.m添加如下代码:

```
@implementation NSURLRequest(DataController)
+ (BOOL)allowsAnyHTTPSCertificateForHost:(NSString *)host
{
    return YES;
}
@end
```
