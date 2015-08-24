This article can help some iOS Developer build a nice architecture.

From now on,I will introduct how to do it.

First of all,I think respect some rules is very important.In my respective,I like do that.

@property (nonamatic, strong) UIButton *button;
.......

pragma mark - life cycle
- (void)viewDidLoad;
- (void)viewWillAppear;
.....

pragma mark - UITableViewDelegate
methods
....

pragma mark - CustomDelegate
methods
....

pragma mark - event response(like UITapGesture,Target....)
methods
.....

pragma mark - private methods
methods
.....

pragma mark - getters and setters
-(UIButton *)button;
.....

And then,it is very controversial wheather use fat Model + skinny Controller or skinny Model + fat Controller.
I think former is better,but when you using that,please concern some aspects:
1,The Model should be reused,reused,reused....(important thing must say three time).
2,The weak logic is written in Model.

For example,we create a custom UITableViewCell,and we @class xxxModel and declare a @property in CustomCell.h,and import xxxModel.h in CustomCell.m(implement file),and then We should set the cell normal state,it is necessary for us.we can make advantage of setter method to take some weak login achieve in setter of Model.that can decline Controller logic,and we can reuse the Cell.

Ok,next....
what is a good architecture?
MVC,MVVM....and so on. Actually,all of the architectures transform from MVC,it only change in structure.We do that just wanna decline press in ViewController.So I have a architecture design,for reference only;
We can design a data download layer,and we import Model in it,we can take the layer to do some weak logic.For example:

    XXXRequest.h
    @interface XXXStatus:NSObject
    - (void)XXXXRequest;
    - (NSString *)XXXXRequestStatus;
    - (NSInteger)numberOfData;
    - (XXXModel *)getXXXXModelAtIndex:(NSInteger)index;
    @interface XXXRequest:BaseRequest
    - (id)initWithDic:(NSDictionary *)dic;
    - (NSDictionary *)parameter;
    - (NSString *)URLStr;
    
And the architecture benefit is we can achieve our data in method,and We don't deal many logic in ViewController,We just do two things
1,We make a Object that class of XXXRequest;
2,We transfer method in XXXRequest;
    
and there is some thing impotant to say,we'd better setting AutoLayout in ViewDidLayoutSubView,and in ViewDidLoad,We just addSubViews is enough.https://github.com/SnapKit/Masonry.git is a good tool that can let you get rid of NSAutoLayout,it use the relation of superView and subView layout,and you will give up CGRect.

NSNotification should be stated in ViewDidAppear,and remove in ViewWillDisAppear.
