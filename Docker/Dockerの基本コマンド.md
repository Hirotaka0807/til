# 目標
  Dockerのpullから編集、pushまでの流れと使うコードを簡単に整理する。  
## Dockerhubからのpull
```
$docker login 
$docker pull <image> 
```

## コンテナ作成
```
$docker run -it <image> bash
```

## コンテナから出る
```
$exit
```

## docker内のコンテナを参照
```
$docker ps -a
```

## dockerのコンテナを再起動
```
$docker restart 
```

## 既存コンテナを実行
```
$docker exec -it <container> bash
```

## コンテナからimageをコミット
```
$docker commit <container> <image>
```

## imageの名前を、hub上のリポジトリに合わせて変更
```
$docker tag <source> <target>
```

## imageをpush
```
$docker push <image>
```

## imageの削除
```
$docker rmi <image>
```
