 branching model 和 rebase

![image-20220330195646270](https://tva1.sinaimg.cn/large/e6c9d24egy1h0styiwr09j20s808s3yu.jpg)

![image-20220330195707972](https://tva1.sinaimg.cn/large/e6c9d24egy1h0styyj1slj20sg0bt0td.jpg)

```
1. git check out feature
// add f2 in feature branch
2. git add .
   git commit -m "f2"
3. git master // git to master branch
```

Now we are in master and m3 as latest commit

```
git merge feature // commits all you feature commit, not only lastest one
```

![image-20220330200627126](https://tva1.sinaimg.cn/large/e6c9d24egy1h0su8d677ej20mq0cnt9d.jpg)

```
git merge --squash feature // smmarize all the changes in the feature branch and make it last commit and merge this last commit to master branch
```



![image-20220330202733377](https://tva1.sinaimg.cn/large/e6c9d24egy1h0suubzuigj20qk0jsmyc.jpg)

![image-20220330202813480](https://tva1.sinaimg.cn/large/e6c9d24egy1h0suv0pfu4j20q60m2gn7.jpg)

```
// in feature branch
git rebase master // add master changed commit in feature brach after m2, this time master doesn't have any change
```

Note:

1.   git will check last commit in master and brach have in common, there was m2 commit
2.   git will check what change after m2 commit in feature branch
3.   git will check what change after m2 commit in master branch
4.   then add those commit after m2 in feature feature, which changed in feature branch will be more forward, now the feature not base on m2 but base on m3