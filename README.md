This article can help some iOS Developer build a nice architecture.

From now on,I will introduct how to do it.

First of all,I think respect some rules is very important.In my respective,I like do that.

@property (nonamatic, strong) UIButton *button;
.......

#pragma mark - life cycle
- (void)viewDidLoad;
- (void)viewWillAppear;
.....

#pragma mark - UITableViewDelegate
methods
....

#pragma mark - CustomDelegate
methods
....

#pragma mark - event response(like UITapGesture,Target....)
methods
.....

#pragma mark - private methods
methods
.....

#pragma mark - getters and setters
-(UIButton *)button;
.....

