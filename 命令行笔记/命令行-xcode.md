

# 例子
$ pwd
/Users/hanyfeng/SourceTree/OSC_Test/TestProjectWithOC
$ ls
TestProjectWithOC           TestProjectWithOC.xcodeproj build
$ xcodebuild -list
Information about project "TestProjectWithOC":
    Targets:
        TestProjectWithOC
        TestProjectWithOCOhter

    Build Configurations:
        Debug
        Release

    If no build configuration is specified and -scheme is not passed then "Release" is used.

    Schemes:
        TestProjectWithOC
        TestProjectWithOCOther




# build action
一般有build,analyze,archive,test,install,clean 默认是build可不写
个别可组合使用，例如clean build
clean默认clean Release


# 用法
例子:
$ xcodebuild -configuration Debug -project TestProjectWithOC.xcodeproj -target TestProjectWithOCOther clean
$ xcodebuild -configuration Debug -project TestProjectWithOC.xcodeproj -target TestProjectWithOCOther clean build -showBuildSettings
$ xcodebuild -workspace TestWorkspaceWithOC.xcworkspace/ -scheme TestProjectWithOC

参数:
-workspace TestWorkspaceWithOC.xcworkspace/
-scheme TestProjectWithOC
-configuration Debug | Release
-project TestProjectWithOC.xcodeproj/
-target TestProjectWithOCOther
-showBuildSettings

注意:
xcodebuild: error: You cannot specify both a scheme and targets
xcodebuild: error: If you specify a workspace then you must also specify a scheme.  Use -list to see the schemes in this workspace.


# 查看
$ xcodebuild -showsdks
$ xcodebuild -list
$ xcodebuild -usage
$ xcodebuild -version -sdk




# 相关工具
## xcpretty输出美化工具
安装:gem install xcpretty
使用:xcodebuild ... | xcpretty

## xcbuild
facebook开源的兼容Xcode的编译工具，它能使编译更快快速，更友好的编译过程日志
https://github.com/facebook/xcbuild
