# iOS 截屏代码（并保存到相册）


```Object-C
+ (UIImage *)clipView:(UIView *)view
{
    ///截屏 （view 为需要截屏的view）
    UIGraphicsBeginImageContext(view.frame.size); //当前的view
    [view.layer renderInContext:UIGraphicsGetCurrentContext()];
    UIImage *viewImage = UIGraphicsGetImageFromCurrentImageContext();
    UIGraphicsEndImageContext();
    ///保存到相册
    UIImageWriteToSavedPhotosAlbum(viewImage,nil,nil,nil);

    return viewImage;
}
```
