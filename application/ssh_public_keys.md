# ssh公開鍵の登録・追加・変更手順


セキュリテイ強化のため、スーパーコンピュータシステムへのログイン利用者は、ssh公開鍵の登録をお願い致します。


## ssh公開鍵の登録手順概略

ssh公開鍵の登録手順の概略は以下のとおりです。

1. ユーザ端末におけるssh公開鍵及び秘密鍵の生成
  - Mac/Linux/Windows WSL2環境の場合
  - Windows TeraTermの場合
  - Windows Puttyの場合
2. 遺伝研スパコンへの公開鍵の設置
  - 直接入力フォーム
  - ファイルのアップロードフォーム
3. 遺伝研スパコンへのssh接続確認（ログイン）


スーパーコンピュータシステム上の~/.ssh/authorized_keysへ追加登録をしております。
訂正が必要な場合は、ご自身で上記ファイルを訂正して下さい。
ログインが出来なくなったなど、問題が発生した場合には、から問い合わせ下さい。


## ssh公開鍵及び秘密鍵の生成 : Mac/Linux/Windows WSL2環境の場合


（１）ユーザ端末におけるペア鍵の生成

　利用するクライアントにＯｐｅnSSHがインストールされていることを確認して下さい。インストールされていない場合、先にインストールをお願いします。

　Mac／Linuxで鍵を生成するには、ssh-keygenコマンドを使用します。

$ ssh-keygen -t rsa -b 2048                                                      (1)
Generating public/private rsa key pair.
Enter file in which to save the key (/home/temp/.ssh/id_rsa):                    (2)
Enter passphrase (empty for no passphrase):                                      (3)
Enter same passphrase again:                                                     (4)
Your identification has been saved in /home/temp/.ssh/id_rsa.
Your public key has been saved in /home/temp/.ssh/id_rsa.pub.
The key fingerprint is:
e5:23:f0:fc:b7:60:70:80:79:91:f2:f1:6d:a8:ae:90 temp@host

   (1)RSAバージョン２で、２０４８ビットの鍵を生成する。

   (2)鍵ペアの保存先：変更する場合のみここでパスを指定する。変更しない場合は、Ｅｎｔerのみ入力する。

   (3)パスフレーズの入力する。

   (4)パスフレーズの再入力する。

 

（２）遺伝研ゲートウェイノードへの公開鍵の設置

$ ls ~/.ssh
id_rsa  id_rsa.pub
$ cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAznOdmkDHzjDpsNIhkl2VNjUXBlC3QePKDAzmu3FDCMgBYUDyiXAXLf85q25cylVq66gLUP63nlFJz4/SLO13w2Qf3Gyyj7ADJJZR3sD+Sf8vdlt2hShAT0kkKBmToBqv2Pqx2SfzRVedlyCE4YFieUVmZUkz95dxwSUklGXmQSvigkqCG86r0NlxCSMjYitDGWAyGMu37cvBYzH0+C2uthtbqTd1VYHfjtvewySSZsvbVVnjLme0Ah2cAyifVaSN4uslDBqkN62b3vaijoXPy9ieUzSP0/dgBhKN/m7yhnM/1s+foJnRI3wfDdqXPw3yOqPC/9EXrjnmdpEmpgMJTw== temp@host
$ 

 鍵ペアの保存先を確認すると、id_rsa,id_rsa.pubの２つのファイルが作成されています。

 id_rsa.pubが公開鍵になりますので、ファイルの内容をコピー、直接入力フォームにペーストすることで、公開鍵の登録が出来ます。

もしくは、ファイルのアップロードフォームでid_rsa.pubをアップロードして下さい。

　・ 直接入力フォーム

sshdirectjpg
 

画面下部（赤枠）部分に上記でコピーした鍵をペーストする。ベースト後、画面下部の公開鍵ボタンを押して登録を行う。

 

　・ ファイルのアップロードフォーム

sshupload

画面下部（赤枠）の【選択】を押し、ファイル選択画面寄り、アップロードするファイルを選択後、画面下部（赤枠）の【公開鍵登録】ボタンを押して登録を行う。

 

（３）遺伝研ゲートウェイノードへのＳＳＨ接続確認

 sshコマントにてスーパーコンピュータシステムに接続します。

$ ssh （アカウント名）@gw.ddbj.nig.ac.jp
Enter passphrase for key '/home/（アカウント名）/.ssh/id_rsa':
Last login: Fri Sep 19 13:28:19 2014 from gw.ddbj.nig.ac.jp
---------------------------------------------------------------------
Thank you for using supercomputer system.
This node is in use for login service only. Please use 'qlogin'.
---------------------------------------------------------------------
[（アカウント名）@gw ~]$

　パスフレーズの入力依頼が表示されたら鍵生成に指定したパスフレーズを入力します。

　認証後、スーパーコンピュータシステムへのログインが完了します。

  秘密鍵の格納場所が^/.ssh/id_rsa以外の場合はｓｓｈコマンドのパラメタ、-i 秘密鍵ＰＡTHを用いることも可能です。




---






 
ユーザ端末毎の移行手順

ユーザー端末の種類及び、使用ソフトウェアに応じて、下記移行手順を参照して下さい。

なお、使用端末が複数存在する場合は、端末毎に移行作業を行って下さい。

・Windows（Putty）

・Windows（TeraTerm）

・Mac／Linux

 
Windows（Putty）  topへ移動

（１）ユーザ端末におけるペア鍵の生成

　Putty で鍵を生成するには、Putty 本体に付属しているputtyegen.exeを起動します。

　 putty1

  鍵の種類をSSH-2 ＲＳＡ，ビット数（Ｂ）を２０４８として【生成】ボタンを押下して、鍵を生成します。

 

   putty2

  指示に従い、空白部分でマウスを動かして下さい。数十秒後、鍵が生成されます。

 

   putty3

 　鍵のパスフレーズを入力後、【秘密鍵の保存】（id_rsaファイルの保存）ボタンを押下して、id_rsaを作成します。

 

   putty4

画面上部（赤枠）部分が公開鍵となりますので、すべてを選択後，コピーし，直接入力フォームにペーストすることで、公開鍵の登録が出来ます。 

　・ 直接入力フォーム

sshdirectjpg
 

画面下部（赤枠）部分に上記でコピーした鍵をペーストする。ベースト後、画面下部の公開鍵ボタンを押して登録を行う。

 

（３）遺伝研ゲートウェイノードへのＳＳＨ接続確認

 ※公開出来ない箇所については、画面上＊＊＊＊＊＊で消していますので、ご了承下さい。

・　Windows（Putty）で接続する

　putty c1

  【セッション】ページを開き、ホスト名：gw.ddbj.nig.ac.jp  ポート：２２を設定する。

  putty c2

   【接続】ー【認証】ページを開き、「keyboard-interactive認証を試みる（ＳＳH－２）（Ｉ）」をチェックする。

　鍵生成時(puttygen)に作成したプライベートキーを選択する。

  putty c3

　次回から、設定を不要にするため、セッション一覧に名前を入力後、【保存】ボタンを押下して、設定内容を保存する。

　次回起動時は、一覧より、対象セッションを選択後、【読込】ボタンを押下すると、設定が読み込まれる。 

  putty c4

　設定が完了したら、【開く】ボタンを押下して、スーパーコンピュータシステムに接続する。

  putty c5

　スーパーコンピュータシステムにログインするユーザＩＤを入力する。

  putty c6

  鍵生成時(puttygen)に指定したパスフレーズを入力する。

  putty c7

 スーパーコンピュータシステムへのログインが完了します。

 

 
Windows（TeraTerm）   topへ移動

（１）ユーザ端末におけるペア鍵の生成

　TeraTerm で鍵を生成するには、TeraTermを起動します。

　teraterm1

　,【設定】ー【ＳＳＨ鍵生成】にて鍵の生成を行います。

 

　teraterm2

  鍵の種類をＲＳＡ，ビット数（Ｂ）を２０４８として【生成】ボタンを押下して、鍵を生成します。

 

  teraterm3

  鍵のパスフレーズを入力後、【公開鍵の保存】(id_rsa.pubファイルの保存）、【秘密鍵の保存】（id_rsaファイルの保存）ボタンを押下して、id_rsa,id_rsa.pubを作成します。

 

（２）遺伝研ゲートウェイノードへの公開鍵の設置

 作成したid_rsa.pubをファイルのアップロードフォームでアップロードして下さい。

　・ ファイルのアップロードフォーム

sshupload

画面下部（赤枠）の【選択】を押し、ファイル選択画面寄り、アップロードするファイルを選択後、画面下部（赤枠）の【公開鍵登録】ボタンを押して登録を行う。

（３）遺伝研ゲートウェイノードへのＳＳＨ接続確認

TeraTermを起動します。

  teraterm c1

　ホスト名：gw.ddbj.nig.ac.jp  ポート：２２、サービス：SSH,サービスバージョンSSH2を設定し、【ＯＫ】ボタンを押下する。

  teraterm c2

   スーパーコンピュータシステムにログインするユーザＩＤ、鍵生成時に指定したパスフレーズを入力する。

　「ＲＡＳ／ＩＳＡ鍵を使う」を選択し、作成した秘密鍵を選択し、【ＯＫ】ボタンを押下する。

  teraterm c3

  スーパーコンピュータシステムへのログインが完了します。

 

 
Mac／Linux   topへ移動


 
