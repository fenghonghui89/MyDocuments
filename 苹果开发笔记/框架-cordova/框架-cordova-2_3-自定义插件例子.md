


## 例子

### 自定义插件1

- 插件.m

```
- (void)echo:(CDVInvokedUrlCommand*)command
{
  CDVPluginResult* pluginResult = nil;
  NSString* echo = [command.arguments objectAtIndex:0];
  
  if ([echo isEqualToString:@"echo"]) {
    NSLog(@"一样");
    pluginResult = [CDVPluginResult resultWithStatus:CDVCommandStatus_OK messageAsString:echo];
  }else{
    NSLog(@"不一样");
    pluginResult = [CDVPluginResult resultWithStatus:CDVCommandStatus_ERROR messageAsString:@"错的"];
  }
  
  [self.commandDelegate runInBackground:^{
    [self.commandDelegate sendPluginResult:pluginResult callbackId:command.callbackId];
  }];
}
```

- 插件js：（成功回调，失败回调，类名，方法名，参数）

```
window.echo = function(str, scallback,fcallback) {
               cordova.exec(scallback, fcallback, "Echo", "echo", [str]);
               };
```
注：cordova.define为添加插件后cordova自动加上的

- 网页调用

```
function onSuccess(message) {
      alert("success:"+message);
    }
    
function onFail(message) {
      alert("fail:"+message);
    }

function echoTest(){
      window.echo(
                  "echomeabc",
                  onSuccess,
                  onFail
                  );
    }
```

### 自定义插件2

- 插件js

```
var exec = require('cordova/exec');
               
module.exports = {
gcappFunction: function(success,fail) {
 exec(success, fail, "Gcapp", "version",[]);
 }  
};

```

- 网页调用

```
function onSuccess(message) {
      alert("success:"+message);
    }
    
function onFail(message) {
      alert("fail:"+message);
    }

function gcappTest(){
var gcappModel = {
        showF: function(success,fail{gcapp.gcappFunction(success,fail);}
      };//gcapp为cordova_plugins.js里面对应插件的clobbers
gcappModel.showF(onSuccess,onFail);
      
    }

```

## 自定义插件3

- 插件.m

```
- (void)more:(CDVInvokedUrlCommand*)command
{
  CGFloat option1 = [[command argumentAtIndex:0] integerValue];
  NSString *option2 = [command argumentAtIndex:1];
  NSLog(@"more:%f %@",option1,option2);
  
  CDVPluginResult* result = [CDVPluginResult resultWithStatus:CDVCommandStatus_ERROR messageAsString:@"more"];
  
  [self.commandDelegate runInBackground:^{
    [self.commandDelegate sendPluginResult:result callbackId:command.callbackId];
  }];
}
```

- 插件js

```
var exec = require('cordova/exec');
               var argscheck = require('cordova/argscheck');
               var echoModel = {};
               
               echoModel.echoFunction = function(str,success,fail) {
               exec(success, fail, "Echo", "echo",[str]);
               }
               
               echoModel.versionFunction = function(success,fail, options) {
               exec(success, fail, "Echo", "version",[]);
               }
               
               echoModel.moreFunction = function(success,fail,options){
               argscheck.checkArgs('fFO', 'echoModel.moreFunction', arguments);
               options = options || {};
               var getValue = argscheck.getValue;
               var op1 = getValue(options.option1,40);
               var op2 = getValue(options.option2,"abc");
               var args = [op1,op2];
               exec(success, fail, "Echo", "more",args);
               }

               module.exports = echoModel;

```

- 网页调用

```
function echoTest(){
     
      var gcappModel = {
        showF: function(str,success,fail){Echo.echoFunction(str,success,fail);}
      };
      gcappModel.showF("echo",onSuccess,onFail);
    }
    

function echoTest1(){
      var gcappModel = {
        showF: function(success,fail,options){Echo.versionFunction(success,fail,options);}
      };//注意参数名，网页调用和插件js的要一致
      gcappModel.showF(onSuccess,onFail,’yeah');
      
    }

function echoTest2(){
      var gcappModel = {
        showF: function(success,fail,options){Echo.moreFunction(success,fail,options);}
      };
      gcappModel.showF(onSuccess,onFail,{option1:1,option2:"23"});
    }

```
