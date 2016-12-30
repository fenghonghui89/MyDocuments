

XML解析

NSXML（SAX，IOS默认）

TBXML（DOM，不能写文档）
TBXML中有支持ARC的开关，在xxx-Prefix.pch文件中添加宏定义打开ARC支持：#define ARC_ENABLED
TBXML需要添加系统库libz.dylib

************************************************************************************************************************************************
************************************************************************************************************************************************

Json解析

NextiveJson/SBJson 第三方，不支持ARC
NSJSONSerialization 支持ARC

************************************************************************************************************************************************
************************************************************************************************************************************************

HTTP请求

GET/POST与同步/异步无关
GET：可以用NSURLRequest、NSMutableURLRequest（NSURLRequest的子类）
POST：只能用NSMutableURLRequest（setHTTPMethod方法只有该类才有）
同步会导致界面阻塞，异步不会


Foundation下的HTTP请求

1.GET可以用NSURLRequest、NSMutableURLRequest（NSURLRequest的子类）
2.POST只能用NSMutableURLRequest（setHTTPMethod方法只有该类才有）

同步请求：
NSData* data = [NSURLConnection sendSynchronousRequest:requestGET returningResponse:nil error:nil];

异步请求：（需要遵循协议）
1.<NSURLConnectionDelegate,NSURLConnectionDataDelegate>
2.NSURLConnection* conn = [[NSURLConnection alloc] initWithRequest:request delegate:self];

可设置缓存策略和超时时间的构造方法
NSMutableURLRequest *test = [[NSMutableURLRequest alloc] initWithURL:urlGET cachePolicy:NSURLRequestUseProtocolCachePolicy timeoutInterval:5.0];

网络等待指示器
[UIApplication sharedApplication].networkActivityIndicatorVisible = NO;






第三方ASIHTTPRequest的HTTP请求

不支持arc
所需框架：cfnetwork/systemconfiguration/mobilecoreservices/coregraphics/libz.dylib
只要有网络请求就会有网络等待指示器，无需设置

同步get/异步get-ASIHTTPRequest、ASIFormDataRequest都可以
同步post/异步post-只能用ASIFormDataRequest，可以用框架提供的协议、自定义协议、或者框架提供的代码块

请求队列
用ASINetworkQueue，需要自定义协议

上传数据
用ASIFormDataRequest

************************************************************************************************************************************************
************************************************************************************************************************************************

webview加载https网站，info-plist无需额外设置
需要安装证书，具体方法是webview加载证书的url，然后会提示自动安装证书
然后如果需要连接vpn 就打开vpn 然后就可以打开了
