# Ansible WireGuard セットアップ

このAnsibleプレイブックは、WireGuard VPNのセットアップを自動化します。

## 要件

*   コントロールノードにAnsibleがインストールされていること。
*   ターゲットホストにSSHでアクセス可能であり、Pythonがインストールされていること。

## 使い方

1.  **インベントリの更新:** `inventory.ini` を編集して、ターゲットホストをリストアップします。
2.  **Pythonのブートストラップ (必要な場合):** ターゲットホストにPythonがインストールされていない場合は、ブートストラッププレイブックを実行します:
    ```bash
    ansible-playbook -i inventory.ini bootstrap_python.yaml --ask-become-pass
    ```
3.  **WireGuardのインストール:** メインプレイブックを実行して、WireGuardをインストールおよび設定します:
    ```bash
    ansible-playbook -i inventory.ini install_wireguard.yaml --ask-become-pass
    ```

## ファイル構成

*   `inventory.ini`: Ansibleのターゲットホストを定義します。
*   `bootstrap_python.yaml`: ターゲットホストにPythonをインストールするためのプレイブック（通常、Ansibleモジュールに必要です）。
*   `install_wireguard.yaml`: WireGuardをインストールおよび設定するためのメインプレイブック。
*   `.gitignore`: Gitが無視すべき、意図的に追跡しないファイルを指定します。