# AFNetWorking里的UIKit+AFNetWorking 清除缓存的方法

有用AFNetWorking里的AFNetWorking里的UIKit+AFNetWorking，我共享一个清除图片缓存的方法。


方法申明
```Object-C
//邵思康 清除缓存 清除所有缓存
+ (void)clearCache;
//清除url对应的缓存
+ (void)clearCacheWithURL:(NSURL *)url;
```

方法体
```Object-C
//邵思康 清除缓存 清除所有缓存
+ (void)clearCache {
    AFImageCache *cache = (AFImageCache *)[UIImageView sharedImageCache];
    [cache removeAllObjects];
    return;
}

//清除url对应的缓存
+ (void)clearCacheWithURL:(NSURL *)url
{
    NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:url];
    [request addValue:@"image/*" forHTTPHeaderField:@"Accept"];

    AFImageCache *cache = (AFImageCache *)[UIImageView sharedImageCache];
    [cache removeObjectForKey:[[request URL] absoluteString]];
}
```
