1、1维前缀和:通过O(n)预处理pre数组，之后可以在O(1)内查找一段连续区间的和。
```
for(int i=1;i<=n;i++)
    pre[i]=pre[i-1]+a[i];//一维前缀和
//查找[l,r]的和
    ans=pre[r]-pre[l-1];
```
2维前缀和:
```
    for(int i=1;i<=n;i++)
    {
        for(int j=1;j<=m;j++)
        {
            pre[i][j]=pre[i-1][j]+pre[i][j-1]-pre[i-1][j-1]+a[i][j];
        }
    }

    //查找一块区间的值
    ans=pre[r][d]-pre[l][d]-pre[r][u]+pre[l][u];
```

2、1维差分,通过O(n)预处理diff数组，之后可以在O(1)内对一段区间内的值进行修改。
```
for(int i=1;i<=n;i++)
    diff[i]=a[i]-a[i-1];

diff[l]++,diff[r+1]--;//将[l,r]区间内的值+1
for(int i=1;i<=n;i++)
    a[i]=diff[i]+a[i-1];//还原a数组
```
