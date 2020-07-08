# CDSTool
Cleanup Dual State

### Cleanup Dual State ツールを実行するユーザーは Windows 10 端末のローカル管理者権限を持っていない場合の手順
***
1. Azure ポータルなどで Azure AD Registered のデバイスのオーナーのユーザーで、対象デバイスにログオンします。

2. 本サイトから CDS.zip ファイルを対象の端末にダウンロードし、展開します。

3. 展開された CleanupWithoutAdmin.cmd をテキスト エディタで開き、以下の内容を編集し、保存します。

    ```
    runas /noprofile /user:<ドメイン管理者ユーザー名> "dsregcmd /leave"

    の　"<ドメイン管理者ユーザー名>" にはドメインの管理者権限を持つユーザーのユーザー名を入力します。

    例 : 

    runas /noprofile /user:contoso\administrator "dsregcmd /leave"
    ```

4. ログオンユーザーの権限でコマンド プロンプトを起動し、展開した ZIP ファイルのフォルダへ移動します。

5. CleanupWithoutAdmin.cmd を実行し、実行中に手順 3 で入力したドメインの管理者権限のパスワードを以下のように要求されますので、入力します。

    ```
    xxxxx\xxxxx のパスワードを入力してください:
    ```

6. 以下のメッセージが表示されましたら、何かのキーを押して、ユーザーをログオフします。

    ```
    All done and have to log off
    続行するには何かキーを押してください . . .
    ```

7. Azure ポータルから Dual State となっている Azure AD Registered と Hybrid Azure AD joined のデバイスが両方が消えたことを確認します。


### Cleanup Dual State ツールを実行するユーザーは Windows 10 端末のローカル管理者権限を持っている場合の手順
***

1. Azure ポータルなどで Azure AD Registered のデバイスのオーナーのユーザーで、対象デバイスにログオンします。

2. 本サイトから CDS.zip ファイルを対象の端末にダウンロードし、展開します。

3. 管理者権限でコマンドプロンプトを起動し、展開した ZIP ファイルのフォルダへ移動します。

4. CleanupWithAdmin.cmd を実行します。

5. 以下のメッセージが表示されましたら、何かのキーを押して、ユーザーをログオフします。

    ```
    All done and have to log off
    続行するには何かキーを押してください . . .
    ```

6. Azure ポータルから Dual State となっている Azure AD Registered と Hybrid Azure AD joined のデバイスが両方が消えたことを確認します。