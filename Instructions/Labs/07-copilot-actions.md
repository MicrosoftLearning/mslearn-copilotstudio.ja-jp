---
lab:
  title: コパイロット アクションを作成する
  module: Enhance Microsoft Copilot Studio copilots
---

# コパイロット アクションを作成する

## シナリオ

このラボでは、次のことを行います。

- コパイロット アクションを作成する

## 学習する内容

- Power Automate を追加して使用し Microsoft Dataverse のデータにアクセスする方法

## ラボ手順の概要

- Power Automate クラウド フローを作成して、Copilot アクションを使用して Dataverse データを取得する
- Power Automate クラウド フローを作成して、Copilot アクションを使用して Dataverse データを作成する
  
## 前提条件

- **ラボ: エンティティの使用**を完了している必要があります

## 詳細な手順

## 演習 1 - Copilot アクションを作成してDataverse からデータを取得する

Microsoft Copilot Studio は、Power Automate クラウド フローを使用して Microsoft Dataverse のデータにアクセスできます。

### タスク 1.1 - Power Automate フローを作成してプロパティを取得する

1. Microsoft Copilot Studio ポータル `https://copilotstudio.microsoft.com` に移動し、適切な環境にあることを確認します。

1. 左側のナビゲーション ウィンドウから **[Copilot]** を選択します。

1. 前のラボで作成した **[Real Estate Booking Service]** を選択します。

1. **[Actions](アクション)** タブを選択します。

1. **[+ アクションの追加]** を選択します。

    ![アクションを追加するステップ 1 のスクリーンショット。](../media/add-action-step-1.png)

1. **[フロー]** フィルターを選択してから、**[デスクトップ用 Power Automate でフローを実行する]** を選択します。

1. プロンプトが表示されたら Power Automate にサインインします。

    ![トリガーと応答の手順を含む Power Automate フローのスクリーンショット。](../media/create-flow-step1.png)

1. 画面の左上にある **[Copilot からフローを実行する]** を選択し、フロー名として「`Get Property`」と入力します。

1. **[Copilot からフローを実行する]** トリガーステップを選択し、**[+ 入力の追加]** を選択します。

1. **[テキスト]** を選択します。

1. **[入力]** に「`Bedrooms`」を入力し、**[入力してください]** に「`Number of Bedrooms`」を入力します。

    ![フローのトリガー プロパティのスクリーンショット。](../media/create-flow-step2.png)

1. フロー内の 2 つのステップの間の [**+**] アイコンを選択し、 **[アクションの追加]** を選択します。

1. **[検索]** フィールドに「`Dataverse`」と入力し、**Microsoft Dataverse** コネクタの **[詳細情報]** を選択します。

    ![[フローのコネクタを検索する] のスクリーンショット。](../media/create-flow-step3.png)

1. **[行の一覧表示]** アクションを選択します。

1. 認証を求められたら、**[OAuth]** を選択し、**[サインイン]** を選択します。

    > **注:** 「**OAuth 接続の作成に失敗しました**」というエラーが表示された場合は、ブラウザーでポップアップを許可する必要があります。

    ![OAuth エラーのスクリーンショット。](../media/failed-oauth-popup.png)

    ![Edge でポップアップを許可するスクリーンショット。](../media/failed-oauth-popup-2.png)

1. テーブル名に **[不動産物件]** テーブルを選択します。

1. **[行のフィルター選択]** フィールドに「`contoso_bedrooms eq `」と入力します (**eq** の後にスペースを入れます)。

1. **[行のフィルター選択]** フィールドを選択したまま、右側にある **[Lightning]** アイコンを選択し、**[Bedrooms]** パラメーターを選択します。

    ![「行の一覧表示アクションを設定する」のスクリーンショット。](../media/create-flow-step4.png)

1. Power Automate のメイン ウィンドウで、**[Respond to Copilot]** アクションを選択し、**[+ Add an output]** を選択します。

1. **[テキスト]** を選択します。

1. **[名前を入力する]** に「`PropertyId`」を入力する

1. **[応答する値を入力する]** フィールドを選択し、**[fx (式を挿入する)]** を選択します。

1. 一番上のフィールドに、次の式を入力します。

    ```
    first(outputs('List_rows')?['body/value'])['contoso_realestatepropertyid']
    ```

    ![「応答アクションを設定する」のスクリーンショット。](../media/create-flow-step5.png)

1. **[追加]** を選択します。

1. **+ 出力を追加** を選択します。

1. **[テキスト]** を選択します。

1. **[名前を入力する]** に「`PropertyName`」を入力します。

1. **[応答する値を入力する]** フィールドを選択し、**[fx (式を挿入する)]** を選択します。

1. 次の式を入力します。

    ```
    first(outputs('List_rows')?['body/value'])['contoso_propertyname']
    ```

1. **[追加]** を選択します。

1. **[Copilot に対して応答]** ウィンドウで **[設定]** タブを選択します。

1. **[非同期応答]** が **オフ** に設定されていることを確認します。

    ![[応答アクションの設定] のスクリーンショット。](../media/create-flow-step6.png)

1. ページの右上の近くにある **[保存]** を選択します。

1. 保存が完了するまで待ってから、[Power Automate] タブを閉じます。

### タスク 1.2 - Copilot アクションを追加してプロパティを取得する

1. [Copilot Studio] ダイアログ ボックスから **[更新]** を選択して、新しいフローを表示します。

1. **[プロパティを取得する]** フローを選択します。

    ![[フロー アクションを追加する] の手順 1 のスクリーンショット。](../media/add-action-flow-step-1.png)

1. [**次へ**] を選択します。

1. [**次へ**] を選択します。

1. **[完了]** を選択します。

### タスク 1.3 - [プロパティを取得する] Copilot アクションをトピックに追加する

1. **[Topics]** タブを選択します。

1. **[不動産の内見を予約する]** トピックを選択します。

1. **[How many bedrooms do you need question?]** ノードの下にある **[+]** アイコンを選択し、**[Call an action]** を選択してから **[Get Property]** フローを選択します。

    ![[フロー アクションを追加する] の手順 2 のスクリーンショット。](../media/add-action-flow-step-2.png)

1. **Bedrooms** 入力パラメーターの **NumberofBedrooms** 変数を選択します。

    ![[フロー アクションを追加する] の手順 3 のスクリーンショット。](../media/add-action-flow-step-3.png)

1. **[どのプロパティを表示しますか?]** ノードで **3 つのドット**を選択し、**[削除]** を選択します。

1. **[Action]** ノードの下にある **[+]** アイコンを選択し、**[Send a message]** を選択します。

1. **[メッセージの入力]** フィールドで「`Property `」と入力します (その後にスペースを付けます)。

1. 同じノードで、 **[{X} (変数の挿入)]** アイコンを選択し、 **PropertyName** 変数を選択します。

    ![[フロー アクションを追加する] の手順 4 のスクリーンショット。](../media/add-action-flow-step-4.png)

1. **[保存]** を選択します。

## 演習 2 - Copilot アクションを作成して Dataverse でデータを作成する

Microsoft Copilot Studio では、Power Automate クラウド フローを使用して Microsoft Dataverse 内のデータを保存できます。

### タスク 2.1 - Power Automate フローを作成して予約を行う

1. **Real Estate Booking Service** の **[アクション]** タブを選択します。

1. **[+ アクションの追加]** を選択します。

1. 下にスクロールし、**[新しいフローの作成]** を選択します。

1. 画面の左上にある **[Copilot からフローを実行する]** を選択しフロー名として「`Create Booking Request`」と入力します。

1. **[Copilot からフローを実行する]** トリガーステップを選択し、**[+ 入力の追加]** を選択します。

1. **[テキスト]** を選択します。

1. **[入力]** に「`PropertyId`」を入力し、**[入力してください]** に「`Property`」を入力します。

1. **+ 入力の追加**を選択します。

1. **[テキスト]** を選択します。

1. **[入力]** に「`ViewerName`」を入力し、**[入力してください]** に「`Viewer Name`」を入力します。

1. **+ 入力の追加**を選択します。

1. **[テキスト]** を選択します。

1. **[入力]** に「`ViewerEmail`」を入力し、**[入力してください]** に「`Viewer Email`」を入力します。

    ![「フロー・パラメーター・アクションを設定する」のスクリーンショット。](../media/create-flow2-step1.png)

1. フロー内の 2 つのステップの間の [**+**] アイコンを選択し、 **[アクションの追加]** を選択します。

1. **[検索]** フィールドに「`Dataverse`」と入力し、**Microsoft Dataverse** コネクタの **[詳細情報]** を選択します。

1. **[新しい行を追加する]** アクションを追加します。

1. テーブル名として **[予約要求]** を選択します。

1. **[予約名]** フィールドに「`Copilot booking`」と入力します。

1. **詳細パラメーター**で**すべて表示**を選択します。

1. **プロパティ (不動産プロパティ)** フィールドに「`contoso_bookingrequests()`」と入力し、かっこ内にカーソルを移動し、**[Lightning]** アイコンを選択してから、**PropertyId** パラメーターを選択します。

1. **[ビューアー メール]** フィールドを選択し、**[Lightning]** アイコンを選択してから、**ViewerEmail** パラメーターを選択します。

1. **"Viewer Name"** フィールドを選択し、**[Lightning]** アイコンを選択してから、**[ViewerName]** パラメーターを選択します。

    ![フローの行の追加アクションの構成のスクリーンショット。](../media/create-flow2-step2.png)

1. **[Respond to Copilot]** アクション選択します。

1. **[Settings](設定)** タブを選択します。

1. **[非同期応答]** が **オフ** に設定されていることを確認します。

1. ウィンドウの右上にある **[Save]** を選択します。

1. 保存が完了するまで待ってから、[Power Automate] タブを閉じます。

### タスク 2.2 - 予約要求を作成する Copilot アクションを追加する

1. [Copilot Studio] ダイアログ ボックスから **[更新]** を選択して、新しいフローを表示します。

1. **[Create Booking Request]** フローを選択します。

1. [**次へ**] を選択します。

1. [**次へ**] を選択します。

1. **[完了]** を選択します。

### タスク 2.3 - Create Booking Request Copilot アクションをトピックに追加する

1. **[Topics]** タブを選択します。

1. **[不動産の内見を予約する]** トピックを選択します。

1. **[What date and time do you want to see the property?]** ノードの下にある **[+]** アイコンを選択し、**[Call an action]** を選択してから **[Create Booking Request]** フローを選択します。

1. **PropertyId**入力パラメーターに、**[PropertyId]** 変数を選択します。

1. **ViewerName**入力パラメーターに、**[Name]** 変数を選択します。

1. **ViewerEmail**入力パラメーターに、**[EmailAddress]** 変数を選択します。

1. 新しい **[Action]** ノードの下にある **[+]** アイコンを選択し、**[Topic management]** を選択し、**[Go to another topic]** を選択して、**[End of Conversation]** を選択します。

1. **[保存]** を選択します。

1. **[Publish]** を選択し、もう一度 **[Publish]** を選択します。

## 演習 3 - Copilot アクションをテストする

### タスク 3.1 - 予約要求を行う

1. 閉じている場合は、画面の右上にある **[Test]** ボタンを選択して、テスト パネルを開きます。

1. 画面の右上にあるテスト パネルの上部にある **3 つのドット**を選択します。

    ![テスト パネル オプションのスクリーンショット。](../media/test-pane-options.png)

1. 有効になっていない場合は、 **[Track between topics]** を有効にします。

1. テスト パネルの上部にある **[Start a new conversation]** アイコンを選択します。

1. **Conversation Start** メッセージが表示されたら、コパイロットによって会話が開始されます。 応答に、先に作成したトピックのトリガー フレーズを入力します。

    `I want to book a real estate showing`

1. 次の情報を入力してください。

    ```
    Name: <Your name>
    Email address: <Your email address>
    ```

1. 情報を入力すると、入力した情報がアダプティブ カードに表示され、詳細が正しいかどうかを確認します。 **[はい]** を選択します。

1. プロパティ プロンプトの種類に、**[House]** を選択します。

1. ベッドルーム数のプロンプトに、「`3`」と入力します。

    ![情報が入力されたテスト ウィンドウのスクリーンショット。](../media/test-pane-action-results.png)

1. **"What date and time do you want to see the property?"** プロンプトに、「`Tomorrow 2:00 PM`」と入力します。

1. **"Did that answer your question?"** プロンプトに対して、**[Yes]** を選択します。

1. 任意の評価を選択します。

1. **"Can I help with anything else?"** プロンプトに対して、**[No]** を選択します。

### タスク 3.2 - 予約要求を確認する

1. まだ開いていない場合は、新しいタブで `https://make.powerapps.com` に移動します。

1. 適切な環境にいることを確認します。

1. モデル駆動型アプリ **Real Estate Property Management** で **[Play]** を選択します。

1. 左側のナビゲーションで **[Booking Requests]** を選択します。

    ![予約要求データを示す Maker ポータルのスクリーンショット。](../media/booking-request-row.png)
