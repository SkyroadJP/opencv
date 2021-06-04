## Golfer Modification
### How to build

Please refer to https://docs.opencv.org/master/d5/da3/tutorial_ios_install.html

```
python opencv/platforms/ios/build_framework.py ios --contrib opencv_contrib --iphoneos_archs arm64 --iphonesimulator_archs x86_64 arm64
```

### How to deploy
    - build the framework
    - zip it with name "opencv2.framework.zip"
    - in github, create a release, with a proper tag, such as r4.5.2 (r is a necessary prefix)
    - upload zip and get the zip URL
    - modify the podspec file with tag name
```
pod repo push skyroad gf-opencv.podspec --use-libraries --allow-warnings --skip-tests --sources=https://github.com/SkyroadJP/Cocoapods-Specs.git,https://github.com/CocoaPods/Specs.git

```


## OpenCV: Open Source Computer Vision Library

### Resources

* Homepage: <https://opencv.org>
  * Courses: <https://opencv.org/courses>
* Docs: <https://docs.opencv.org/master/>
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
