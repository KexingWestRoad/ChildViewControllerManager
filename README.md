# ChildViewControllerManager
我们在做很多滚动页面的容器的时候经常会在一个VC中添加另外几个VC的子View [self.view addSubViews:vc.view].
接下来[self addChildViewController:vc]
此时树形的视图层级都是View.
那么各自的VC的生命周期是谁来管理的呢？
其实就是VC在管理被添加到它上面的子VC.

1.didMoveToParentViewController
2.willMoveToParentViewController
3.removeFromParentViewController
这三个方法在切换VC中的显示View。

我们都知道一个VC自己的生命周期是从loadview->viewDidLoad->viewWillAppear->viewWillDisappear->viewDidDisappear
那么子VC也是遵循这个规则。

￼￼2017-07-21 18:16:57.164 ChildViewControllerManager[20340:2594368] FirstViewController :loadView
2017-07-21 18:16:57.164 ChildViewControllerManager[20340:2594368] FirstViewController :viewDidLoad
2017-07-21 18:16:57.165 ChildViewControllerManager[20340:2594368] FirstViewController :viewWillAppear
2017-07-21 18:17:20.133 ChildViewControllerManager[20340:2594368] SecondViewController :loadView
2017-07-21 18:17:20.133 ChildViewControllerManager[20340:2594368] SecondViewController :viewDidLoad
2017-07-21 18:17:20.134 ChildViewControllerManager[20340:2594368] FirstViewController :viewWillDisappear
2017-07-21 18:17:20.134 ChildViewControllerManager[20340:2594368] SecondViewController :viewWillAppear
2017-07-21 18:17:20.537 ChildViewControllerManager[20340:2594368] FirstViewController :viewDidDisappear
