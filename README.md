# YZViewController
快速定位iOS线上App崩溃在哪个控制器里面，需要和后台配合使用

1.
下载本项目并添加手动添加到项目里

2.
新建所有的页面都继承于YZViewController

3.
在AppDelegate的didFinishLaunchingWithOptions方法里面写下如下代码：

if ([[[NSUserDefaults standardUserDefaults] valueForKey:@"BUG"] isKindOfClass:[NSDictionary class]]) {
        NSLog(@"%@",[[NSUserDefaults standardUserDefaults] valueForKey:@"BUG"]);
        [[NSUserDefaults standardUserDefaults] removeObjectForKey:@"BUG"];
    }
    
打印的字典内容即为崩溃的信息，与网上不同的是，这个可以直接显示在哪个控制器崩溃的，百分百准确，而且还可以手动把崩溃的用户其他信息给传送到后台，使BUG更容易重现和解决（前提是你的控制器必须继承YZViewController）