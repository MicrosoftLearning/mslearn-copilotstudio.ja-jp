---
lab:
  title: Microsoft Teams にコパイロットをデプロイする
  module: Create a copilot with Microsoft Copilot Studio and Dataverse for Teams
---

# Microsoft Teams にコパイロットをデプロイする

## シナリオ

このラボでは、次のことを行います。

- コパイロット アクションを作成する

## 学習する内容

- コパイロットを Microsoft Teams にデプロイする方法

## ラボ手順の概要

- 公開
- Microsoft Teams にコパイロットをデプロイする
  
## 前提条件

- **ラボ: Microsoft Copilot Studio で生成 AI を使用する**を完了している必要があります

## 詳細な手順

## 演習 1 - コパイロットを公開する

### タスク 1.1 - 最新のコンテンツを公開する

1. Microsoft Copilot Studio ポータル `https://copilotstudio.microsoft.com` に移動し、適切な環境にあることを確認します。

1. 左側のナビゲーション ウィンドウから **[Copilot]** を選択します。

1. 前のラボで作成したコパイロットを選択します。

1. **[Publish]** を選択し、もう一度 **[Publish]** を選択します。

   ![発行ダイアログのスクリーンショット。](../media/copilot-publish.png)

   > **注:** 公開には数分かかる場合があります。

## 演習 2 - チャネル

コパイロットを公開すると、Teams のユーザーが自分のコパイロットを使用できるようになります。 こうすることで、ユーザー、ユーザーのチームメイト、より広範な組織がユーザーのコパイロットとやり取りできます。

### タスク 2.1 - Microsoft Teams チャンネル

1. Microsoft Copilot Studio で Copilot を開いた状態で、**[Channels]** タブを選択します。

    ![[Channels] タブのスクリーンショット。](../media/channels.png)

1. **Microsoft Teams** タイルを選択します。

    ![[Teams] ダイアログのスクリーンショット。](../media/teams-enable.png)

1. **Teams を有効にする**を選択します。

    ![Team チャネル ダイアログのスクリーンショット。](../media/teams-channel.png)

1. **利用可能オプション**を選択します。

    ![Teams チャネルの可用性オプションのスクリーンショット。](../media/teams-availability-options.png)

1. **[Copy link]** を選択します。

1. **チームメイトと共有ユーザーに表示する**を選択します。

1. ユーザーを選択します。

1. ウィンドウの左上隅にある戻る矢印ボタンを選択します。

1. **[共有]** を選択します。

### タスク 2.2 - Microsoft Teams

1. 別のタブで、Microsoft Teams `https://teams.microsoft.com` に移動します。

1. プロンプトが表示されたら、Teams にサインインします。

1. 左側のナビゲーションで、**[Teams]** を選択します。

1. **[General]** チャネルを持つ **Contoso** という名前のチームが表示されます。

1. 新しいタブを開き、前のタスクでコピーした URL リンクに移動します。

1. **"This site is trying to open Microsoft Teams"** ダイアログ ボックスで **[Cancel]** を選択します。

1. **[代わりに Web アプリを使用]** を選択します。

1. **[追加]** を選択します。

    !["Add the app to Teams" ダイアログのスクリーンショット。](../media/teams-add-app.png)

1. Copilot をテストする

    ![Copilot in Teams のスクリーンショット。](../media/teams-copilot.png)
