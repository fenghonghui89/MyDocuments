


## Introduction to Appium 介绍
```
Appium Design
```
WebDriver (aka “Selenium WebDriver”) specifies a client-server protocol (known as the JSON Wire Protocol).
Given this client-server architecture, a client written in any language can be used to send the appropriate HTTP requests to the server.
Appium使用WebDriver的json wire协议，来驱动Apple系统的UIAutomation库、Android系统的UIAutomator框架。

Instead we have extended the protocol with extra API methods useful for mobile automation.
appium扩展了Selenium WebDriver JSON Wire Protocol



## Appium
```
Why Appium?
```
You can write tests with your favorite dev tools using any WebDriver-compatible language such as Java, Objective-C, JavaScript with Node.js (in promise, callback or generator flavors), PHP, Python, Ruby, C#, Clojure, or Perl with the Selenium WebDriver API and language-specific client libraries.
Appium支持Selenium WebDriver支持的所有语言，如Java、Object-C、JavaScript、PHP、Python、Ruby、C#、Clojure，或者Perl语言，更可以使用Selenium WebDriver的Api

You can use any testing framework.

```
Requirements 环境要求
```
Make sure you have not installed Node or Appium with sudo
不能sudo安装node and appium

appium-doctor检测环境配置是否正确
$ npm install -g appium-doctor
$ appium-doctor --ios/android

You also need to download the Appium client for your language so you can write tests
项目要安装appium client库

```
Quick Start 安装运行
```
$ npm install -g appium
$ appium
或者官网下载桌面应用

安装的时候，提示如下并卡住
sqlite3@3.1.8 install /Users/hanyfeng/.nvm/versions/node/v6.10.0/lib/node_modules/sqlite3
node-pre-gyp install --fallback-to-build
则可以先npm安装 node-pre-gyp sqlite3 两个库
安装sqlite3也会卡住，不用理会直接ctrl+z停止，然后安装appium
npm安装可能比较慢，要耐心等
cnpm安装可能会卡在某个下载依赖包





```
Writing Tests for Appium
```
The main guide for getting started writing and running tests is the running tests doc, which includes explanations for iOS, Android, and Android older devices.

If you're interested in testing on physical hardware, you might be interested in our real devices guide.

(Note: If you're automating iOS 10+, be sure to check out our XCUITest Migration Guide since Apple's automation support has changed significantly since iOS 10, with corresponding changes in Appium).

Essentially, we support a subset of the Selenium WebDriver JSON Wire Protocol, and extend it so that you can specify mobile-targeted desired capabilities to run your test through Appium.

You find elements by using a subset of WebDriver's element-finding strategies.
We also have several extensions to the JSON Wire Protocol for automating mobile gestures like tap, flick, and swipe.

You can also automate web views in hybrid apps!


```
How It Works
```
Appium drives various native automation frameworks and provides an API based on Selenium's WebDriver JSON wire protocol.

For new iOS versions (9.3 and up), Appium drives Apple's XCUITest library. Our support for XCUITest utilizes Facebook's WebDriverAgent project.

For older iOS versions (9.3 and below), Appium drives Apple's UIAutomation library, using a strategy which is based on Dan Cuellar's work on iOS Auto.
















# 未看
ANDROID
RUNNING IOS TESTS ON OS X USING JENKINS
Deploying an iOS app to a real device
