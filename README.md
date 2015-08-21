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

And then,it is very controversial wheather use fat Model + skinny Controller or skinny Model + fat Controller.
I think former is better,but when you using that,please concern some aspects:
1,The Model should be reused,reused,reused....(important thing must say three time).
2,The weak logic is written in Model.

For example,we create a custom UITableViewCell,and we @class xxxModel and declare a @property in CustomCell.h,and import xxxModel.h in CustomCell.m(implement file),and then We should set the cell normal state,it is necessary for us.we can make advantage of setter method to take some weak login achieve in setter of Model.that can decline Controller logic,and we can reuse the Cell.

