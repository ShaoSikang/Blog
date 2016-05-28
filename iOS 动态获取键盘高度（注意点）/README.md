# iOS动态获取键盘高度（注意点）

添加通知

```h
- (void)addNotification
{
    [[NSNotificationCenter defaultCenter] addObserver:self
                                             selector:@selector(keyboardWillShown:)
                                                 name:UIKeyboardWillShowNotification object:nil];
    [[NSNotificationCenter defaultCenter] addObserver:self
                                             selector:@selector(keyboardWillBeHidden:)
                                                 name:UIKeyboardWillHideNotification object:nil];
}
```


方法实现

```h
}#pragma mark - KeyBroad Notification
- (void)keyboardWillShown:(NSNotification*)aNotification
{
    NSDictionary* info = [aNotification userInfo];
    CGFloat KBHeight = [[info objectForKey:UIKeyboardFrameEndUserInfoKey] CGRectValue].size.height;
    NSLog(@"KBHeight:%f", KBHeight);

    self.chatBottomViewBottom.constant = - 200 + KBHeight;
    [UIView animateWithDuration:0.3 animations:^{

        [self.view layoutIfNeeded];
    }];
```


注意点

```h
 UIKeyboardFrameEndUserInfoKey 为键盘修改后的高度
// UIKeyboardFrameBeginUserInfoKey 为键盘修改前的高度，在切换键盘的时候可能得出不正确的高度
```
