


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
        TestProjectWithOC copy



$ xcodebuild -configuration Debug -project TestProjectWithOC.xcodeproj -target TestProjectWithOCOhter clean build
$ xcodebuild -configuration Debug -project TestProjectWithOC.xcodeproj -target TestProjectWithOCOhter -showBuildSettings

$ xcodebuild -showsdks
$ xcodebuild -list
