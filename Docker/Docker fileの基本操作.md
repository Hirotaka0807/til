# 目標  
  Dockerfileの働きと、基本的な文法を知る。
  
  ## Dockerfileとは  
  Docker imageの設計図。
  コンテナがどのような働きをするのかを記載したテキストファイル。
  
  ## Dockerfileの基本設計  
  ```
  # Docker imageのベースとなるDocker imageを指定する。
  # Ubuntu, AlpineなどOSを指定することが多い。
  FROM ubuntu:latest
  
  # RUNでほしい機能を網羅していく。
  RUN apt-get update -o Acquire::ForceIPv4=true && apt-get install -y \
  curl \
  cvs \
  nginx
  
  # 起動したときのデフォルトコマンドをCMDで指定。
  CMD ["bin/bash]
  
  ```
  ### その他注意点
  - -o Acquire::ForceIPv4=trueを指定することで、IPv6を参照してupdateに時間がかかることを防ぐ。  
  - -yオプションで選択肢をすべてyesで答えるようにする。  
