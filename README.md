4.6.0 + Xcode 14 + CMake 3.22.2 无法编译，大概率是 CMake 的问题，
找不到 Compiler ，以后有时间再处理

## Golfer Modification
### How to build

Please refer to https://docs.opencv.org/master/d5/da3/tutorial_ios_install.html

1. prepare root folder 

```
mkdir -p gf-opencv
```

2. git clone the codes

```
git clone https://github.com/SkyroadJP/opencv.git opencv
git clone git clone https://github.com/opencv/opencv_contrib.git opencv_contrib
```

3. confirm the versions

```
Currently it is 4.5.2
```

4. build the binaries separately

```
# for simulator
python opencv/platforms/ios/build_framework.py simulator --contrib opencv_contrib --iphonesimulator_archs arm64,x86_64 --build_only_specified_archs

# for ios
python opencv/platforms/ios/build_framework.py ios --contrib opencv_contrib --iphoneos_archs arm64 --build_only_specified_archs
```

5. Create xcframework
```
xcodebuild -create-xcframework -framework ios/opencv2.framework -framework simulator/opencv2.framework -output final/opencv2.xcframework
```

### How to deploy

    - build the framework
    - zip it with name "opencv2.xcframework.zip"
    - in github, create a release, with a proper tag, such as r4.5.2 (r is a necessary prefix)
    - upload zip and get the zip URL
    - modify the podspec file with tag name

```
pod repo push skyroadjp gf-opencv.podspec --use-libraries --allow-warnings --skip-tests --sources=https://github.com/SkyroadJP/Cocoapods-Specs.git,https://github.com/CocoaPods/Specs.git

```

### pod install notes
因为opencv里面有swift模块，通过pod安装时，Xcode不能有效开启swift编译全家桶。
因此需要在 宿主项目中，手动添加一个 dummy.swift，用于开启全家桶


## OpenCV: Open Source Computer Vision Library

### Resources

* Homepage: <https://opencv.org>
  * Courses: <https://opencv.org/courses>
* Docs: <https://docs.opencv.org/4.x/>
* Q&A forum: <https://forum.opencv.org>
  * previous forum (read only): <http://answers.opencv.org>
* Issue tracking: <https://github.com/opencv/opencv/issues>
* Additional OpenCV functionality: <https://github.com/opencv/opencv_contrib> 


### Contributing

Please read the [contribution guidelines](https://github.com/opencv/opencv/wiki/How_to_contribute) before starting work on a pull request.

#### Summary of the guidelines:

* One pull request per issue;
* Choose the right base branch;
* Include tests and documentation;
* Clean up "oops" commits before submitting;
* Follow the [coding style guide](https://github.com/opencv/opencv/wiki/Coding_Style_Guide).
