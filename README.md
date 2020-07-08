# CDSTool
Cleanup Dual State

## Cleanup Dual State ツールを実行するユーザーは Windows 10 端末のローカル管理者権限を持っていない場合の手順
***
1. Azure ポータルなどで Azure AD Registered のデバイスのオーナーのユーザーで、対象デバイスにログオンします。
2. 本サイトから CDS.zip ファイルを対象の端末にダウンロードし、展開します。

3. RS4_NonAdminUsers フォルダの cleanup.cmd の以下の内容を編集し、保存します。

runas /noprofile /user:<ドメイン管理者ユーザー名> "dsregcmd /leave"

の　"<ドメイン管理者ユーザー名>" にはドメインの管理者権限を持つユーザーのユーザー名を入力します。

例 : 

runas /noprofile /user:contoso\administrator "dsregcmd /leave"


3. 端末にログオンしているユーザーの権限でコマンドプロンプトを起動し、cleanup.cmd を実行します。
実行中に手順 2 で入力したドメインの管理者権限のパスワードを要求されますので、入力します。

4. cleanup.cmd の実行が完了すると、ユーザーが自動的にログオンされます。
5. Azure ポータルから Dual State となっている Azure AD Registered と Hybrid Azure AD joined のデバイスが両方が消えたことを確認します。
6. ユーザーで再度端末にログオンし、デバイスが Hybrid Azure AD Join になっていることを確認します。
7. 一旦ユーザーをログオフし、再度ログオンし、WHfB をプロビジョニングします。


## Cleanup Dual State ツールを実行するユーザーは Windows 10 端末のローカル管理者権限を持っている場合の手順
***

1. Azure ポータルなどで Azure AD Registered のデバイスのオーナーのユーザーで、対象デバイスにログオンします。
2. CDS.zip ファイルを対象の端末に展開します。
3. 管理者権限でコマンドプロンプトを起動し、展開した ZIP ファイルの RS4_AdminUsers フォルダの cleanup.cmd を実行します。
4. cleanup.cmd の実行が完了すると、ユーザーが自動的にログオンされます。
5. Azure ポータルから Dual State となっている Azure AD Registered と Hybrid Azure AD joined のデバイスが両方が消えたことを確認します。
6. ユーザーで再度端末にログオンし、デバイスが Hybrid Azure AD Join になっていることを確認します。
7. 一旦ユーザーをログオフし、再度ログオンし、WHfB をプロビジョニングします。