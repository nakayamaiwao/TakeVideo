# TakeVideo
An iOS project that takes video with customized User Interfaces and water mark and compression 

## Effect Picture
![TakeVideo Effect Photo 1](https://github.com/VictorZhang2014/TakeVideo/blob/master/images/TakeVideo_EffectPicture_11.png "TakeVideo")
![TakeVideo Effect Photo 2](https://github.com/VictorZhang2014/TakeVideo/blob/master/images/TakeVideo_EffectPicture_22.png "TakeVideo")
![TakeVideo Effect Photo 2](https://github.com/VictorZhang2014/TakeVideo/blob/master/images/TakeVideo_EffectPicture_33.png "TakeVideo")

## Let's get started
There're three ways to call. I'm going to show you on how do you call it.

#### First way
Importing this header file
```
#import "ZRMediaCaptureController.h"
```

Then calling the code as shown below. This way is using the default User Interface which means that has done by System
```
    ZRMediaCaptureController *manager = [[ZRMediaCaptureController alloc] init];
    [manager setVideoCaptureType:ZRMediaCaptureTypeDefault completion:^(int statusCode, NSString *errorMessage, NSURL *videoURL, NSTimeInterval videoInterval) {
        NSLog(@"视频地址：%@", videoURL.absoluteString);
        
        if (errorMessage.length) {
            NSLog(@"拍摄视频失败 %@", errorMessage);
        } else {
            [self previewVideo:videoURL interval:videoInterval];
        }
    }];
    [self presentViewController:manager animated:YES completion:nil];
```


#### Second way
Importing this header file
```
#import "ZRMediaCaptureController.h"
```

Then calling the code as shown below. The only difference is `CaptureType`. This way is customized User Interface, and the tailored UI is popular at present, most of apps are using this way.
```
    ZRMediaCaptureController *manager = [[ZRMediaCaptureController alloc] init];
    [manager setVideoCaptureType:ZRMediaCaptureTypeCustomizedUI completion:^(int statusCode, NSString *errorMessage, NSURL *videoURL, NSTimeInterval videoInterval) {
        NSLog(@"视频地址：%@", videoURL.absoluteString);
        
        if (errorMessage.length) {
            NSLog(@"拍摄视频失败 %@", errorMessage);
        } else {
            [self previewVideo:videoURL interval:videoInterval];
        }
    }];
    [self presentViewController:manager animated:YES completion:nil];
```


#### Second way
Importing this header file
```
#import "ZRVideoCaptureViewController.h"
```

Then calling the code as shown below. This is third way to call. The tailored UI(User Interface) that are fitted for the most of apps that is prevalent on WeChat, Snapchat, Instagram, etc. If you want to get deeply tailored UI, you can add some views in this way. 
```
    ZRVideoCaptureViewController * videoCapture = [[ZRVideoCaptureViewController alloc] init];
    [videoCapture setCaptureCompletion:^(int statusCode, NSString *errorMessage, NSURL *videoURL, NSTimeInterval videoInterval) {
        NSLog(@"视频地址：%@", videoURL.absoluteString);
        
        if (errorMessage.length) {
            NSLog(@"拍摄视频失败 %@", errorMessage);
        } else {
            [self previewVideo:videoURL interval:videoInterval];
        }
    }];
    [self presentViewController:videoCapture animated:YES completion:nil];
```

