# 目標  
Windows10PCにLinux環境（Ubuntu）を導入し、Ubuntu上でDockerが動作するようにする。

# 手順1: VirtualBoxのインストール
Sourse:https://sukkiri.jp/technologies/virtualizers/virtualbox/virtualbox-win_install.html  
上記手順に従えば、エラーなしでインストールできた。  

# 手順2: Ubuntuのインストール
Sourse:https://qiita.com/pyon_kiti_jp/items/0be8ac17439abf418e48
こちらも難なく。

# 手順3: Dockerのインストール
Sourse:https://qiita.com/HirMtsd/items/11d7fbab6dff5599c54b  

いくつかの手順でエラーが発生。  

  ## エラー1: apt installが動作しない。  
  ```
  $ sudo apt install curl
  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
  E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?  
  ```
  実行を中断したり、メモリ不足でループしたりしたことでlockファイルが作られ、aptがロックされてた。  
  ### 解決策
  ```
  $ sudo rm /var/lib/apt/lists/lock
  $ sudo rm /var/cache/apt/archives/lock
  $ sudo rm /var/lib/dpkg/lock
  $ sudo dpkg --configure -a
  ```
  関係がありそうなlockフォルダを全部削除、一応再構成。  
  sourse:https://it-baron.com/hack/could-not-get-lock/  
  
  ## エラー2: リポジトリの追加がバージョンに合ってない。
  ```
  sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
  ```
  stableの前に、バージョンに合った文言（バージョン名）が必要な模様。  
  今回は、Ubuntu16.04（古くない？）なので、xenial.  
  その他手順は以下ソース。
  
  sourse:https://unix.stackexchange.com/questions/363048/unable-to-locate-package-docker-ce-on-a-64bit-ubuntu  

# 追加資料
  - 本格的開発環境前に再インストール。参考資料:https://qiita.com/ys22_/items/ff3ed3f79c8a1df3731c
残りは手順通り進んだ。  
お疲れさまでした。  
