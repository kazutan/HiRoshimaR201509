データハンドリング再入門
========================================================
author: kazutan
date: 2015/9/19
width: 1280
height: 800

## HiRoshima.R #5
![icon](pics/user.png)

自己紹介
===
### 所属
比治山大学短期大学部

### Twitter
@kazutan

### Web
http://kz-md.net/  
http://blog.kz-md.net/

***

![ビールのみてぇ](pics/icon_tw4.png)


今回の内容
===
## Rのポイントはデータハンドリング
- データの読み込みは`read.*`
- 分析の実行は、その分析の関数
- では、データの加工は?
  - 変数を取り出して…
  - 変数を新しく算出して…
  - 条件にあるレコードを抽出して…
  - 集計して…
  - 縦型と横型を切り替えて…
  - 複数のデータセットを結合して…
  
これらをdplyr + tidyrを活用してやってみます




デモ(1)
===
## こんな感じになります


```r
iris %>% 
  dplyr::select(starts_with("sepal"),Species) %>% 
  dplyr::group_by(Species) %>% 
  dplyr::summarize_each(funs(mean)) %>% 
  dplyr::arrange(Sepal.Width) 
```

```
Source: local data frame [3 x 3]

     Species Sepal.Length Sepal.Width
      (fctr)        (dbl)       (dbl)
1 versicolor        5.936       2.770
2  virginica        6.588       2.974
3     setosa        5.006       3.428
```

デモ(1)の内容
===
## こういうことをやってます


```r
iris %>% 
  dplyr::select(starts_with("sepal"),Species) %>% 
  dplyr::group_by(Species) %>% 
  dplyr::summarize_each(funs(mean)) %>% 
  dplyr::arrange(Sepal.Width) 
```

```
irisデータを…
  "sepal"で始まる変数と"Species"を取り出して…
  "Species"の値でグループ化して…
  各列に対して"平均"で要約して…
  "Sepal.Width"の昇順でソート
```

デモ(2)
===
## もひとつ


```r
iris %>% 
  dplyr::select(-Species) %>% 
  tidyr::gather(key = var_name, value = value) %>% 
  head
```

```
      var_name value
1 Sepal.Length   5.1
2 Sepal.Length   4.9
3 Sepal.Length   4.7
4 Sepal.Length   4.6
5 Sepal.Length   5.0
6 Sepal.Length   5.4
```


デモ(2)の内容
===
## こういうことをやってます

```r
iris %>% 
  dplyr::select(-Species) %>% 
  tidyr::gather(key = var_name, value = value) %>% 
  head
```

```
irisデータを…
  "Species"以外の変数を取り出して…
  4つの変数を縦型のデータに整形して…
  上6つのデータを表示
```



本日の内容
===
## dplyrパッケージ

## tidyrパッケージ




