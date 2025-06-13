---
lab:
  title: トピックの管理
  module: Manage topics in Microsoft Copilot Studio
---

# トピックの管理

## シナリオ

この演習では、次のことを行います。

- 既存のトピックを管理する
- 自然言語を使用してトピックを作成および編集する
- トリガー フレーズを使用してトピックを手動で作成する

この演習の所要時間は約 **30** 分です。

## 学習する内容

- エージェント トピックを構成する方法

## ラボ手順の概要

- トピックを無効にする
- 自然言語でトピックを新規作成および編集する
- 新しいトピックを作成しトリガー フレーズを追加する
  
## 前提条件

- **ラボ: 最初のエージェントを構築する**を完了している必要があります

## 詳細な手順

## 演習 1 - トピックを削除する

この演習では、エージェント内のトピックを削除します。

### タスク 1.1 - トピックを無効にする

1. Microsoft Copilot Studio ポータル `https://copilotstudio.microsoft.com` に移動し、適切な環境にあることを確認します。

1. 画面の右上にある **[Test]** ボタンを選択して、パネルが開いている場合はテスト パネルを閉じます。

1. 左側のナビゲーション ウィンドウから **[エージェント]** を選択します。

    ![Copilot Studio ポータルでのエージェント。](../media/copilot-studio-copilots.png)

1. 前のラボで作成したエージェントを選択します。

1. **[Topics]** タブを選択します。

    ![Copilot Studio ポータルの [Topics] タブ。](../media/topics-tab.png)

1. **[Start Over]** トピックの **[Enabled]** を **[Off]** に切り替えます。

    ![Copilot Studio ポータルでトピックが削除され無効になった様子。](../media/topics-removed.png)

## 演習 2 - 自然言語でトピックを作成する

この演習では、エージェントにトピックを作成し、トリガー フレーズを追加します。

### タスク 2.1 - コパイロットを使用してトピックを追加する

1. **[+ Add a topic]** を選択し、**[Create from description with Copilot]** を選択します。 新しいウィンドウが開きます。

    ![Copilot でトピックを作成します。](../media/topic-create-from-description-2.png)

    ![Copilot でトピックを作成します。](../media/topic-create-with-copilot.png)

1. **[Name your topic]** テキスト ボックスに「**`Customer Details`**」と入力します。

1. **[Create a topic to...]** テキスト ボックスに「**`Ask the customer for their name and email address.`**」と入力します。

1. **[Create]** を選択します。

1. **[Save]** を選択します。

### タスク 2.2 - 自然言語でノードを更新する

1. **[Customer Details]** ペインの右側に **[Edit with CoPilot]** ペインが表示されない場合は、作成キャンバスの上部にある**コパイロット** アイコンを選択します。

    ![[Copilot で編集] アイコンのスクリーンショット。](../media/edit-with-copilot.png)

1. 2 番目の **[Question]** ノードである **[What is your email address?]** を選択します。

    ![[Copilot で編集] アイコンのスクリーンショット。](../media/copilot-email-address-node.png)

1. **Copilot で編集**パネルで、**何の操作を実行しますか?** フィールドに、次のテキストを入力します。

    `Change "What is your email address?" to say thank you to the Name variable from the previous node and then proceed to ask the email address question.`

1. **[更新]** を選択します。

    ![プロンプトを含む [Copilot で編集] パネルのスクリーンショット。](../media/edit-with-copilot-panel.png)

    ![Name 変数を含むように更新されたメッセージのスクリーンショット。](../media/message-updated-name-variable.png)

    > **注**: メッセージは、先ほどのノードの *Name* 変数を含むように更新されるはずです。上記のスクリーンショットのようになります。 [コパイロットで編集する] で質問ノードが正しく更新されなかった場合は、[元に戻す] を選択し、別のプロンプトでもう一度試します。

1. **[保存]** を選択します。

### タスク 2.3 – 自然言語でノードを追加する

既存のノードを更新する他に、Copilotを 使用して新しいノードを追加できます。

1. ノードの周りにある空き領域を選択して、ノードが選択されていないことを確認します。

1. **Copilot で編集**パネルで、**何の操作を実行しますか?** フィールドに、次のテキストを入力します。

    `Summarize the information collected in an adaptive card`

1. **[更新]** を選択します。

1. トピックの末尾に、アダプティブ カードを含むメッセージ ノードが追加されます。

    ![アダプティブ カードを含むメッセージ ノードのスクリーンショット。](../media/message-node-adaptive-card.png)

1. アダプティブ カードの **[Media]** ボックスを選択します。 画面の右側にアダプティブ カードのプロパティが表示されます。

    ![アダプティブ カードのプロパティのスクリーンショット。](../media/adaptive-card-properties.png)

   アダプティブ カードの式は、上記のようになります。 このようになっていない場合は、以下の式を貼り付けることができます。

    ```json
    {
    type: "AdaptiveCard", 
        body: 
        [
            {
                type: "TextBlock",
                size: "Medium",
                weight: "Bolder",
                text: "Summary"    
            },
            {
                type: "FactSet",
                facts: 
                [
                    {
                        title: "Full Name",
                        value: Text(Topic.Name)
                    },
                    {
                        title: "Email Address",
                        value: Text(Topic.EmailAddress)
                    }
                ]
            },
            {
                type: "TextBlock",
                text: "Thank you for providing the information."
            }
        ]
    }
    ```

1. アダプティブ カードのプロパティを開くと **[Edit with Copilot]** パネルが閉じるため、**[Copilot]** アイコンを選択してもう一度開く必要があります。

1. ノードの周りにある空き領域を選択して、ノードが選択されていないことを確認します。

1. **何の操作を実行しますか?** フィールドに、次のテキストを入力します。

    `Add a new multiple choice question to prompt the user if the details are correct with two options Yes or No`

1. **[更新]** を選択します。

1. トピックの末尾に、ユーザーが選択できるオプションを含む新しい質問ノードが追加されます。

    ![はい/いいえのオプションを含む新しい質問ノードのスクリーンショット。](../media/new-question-node.png)

1. **[保存]** を選択します。

### タスク 2.4 - トピックをテストする

1. 画面の右上にある **[Test]** ボタンを選択して、テスト パネルが閉じている場合は開きます。

1. テスト パネルの上部にある **[Start a new conversation]** アイコンを選択します。

1. **[Ask a question or describe what you need]** テキスト ボックスに、「**`Customer information`**」と入力します。

1. 名前とメール アドレスを入力します。

1. **[はい]** を選択します。

## 演習 3 - トピックを手動で作成する

トリガー フレーズを追加してトピックを手動で作成できます

### タスク 3.1 - 空白からトピックを作成する

1. **Real Estate Booking Service** の上部バーにある **[Topics]** タブを選択します。

1. **[+ Add a topic]** を選択し、**[From blank]** を選択します。

1. **[Details]** アイコンを選択して、"Topic details" ダイアログを開きます。

    !["Topic details" ダイアログのスクリーンショット。 ](../media/topic-details.png)

1. **"Name"** フィールドに、次のテキストを入力します。

    `Book a Real Estate Showing`

1. **"Display Name"** フィールドに、次のテキストを入力します。

    `Book`

1. **"Description"** フィールドに、次のテキストを入力します。

    `Select the property and requested date and create a booking request`

1. **[保存]** を選択します。

### タスク 3.2 - トリガー フレーズを追加する

1. **[トリガー]** の **[フレーズ]** で **[編集]** を選択します。

    ![トピック トリガー フレーズのウィンドウのスクリーンショット。](../media/topic-trigger-phrases.png)

1. **[Add Phrases]** に「`I want to book a real estate showing`」と入力し、**[+]** アイコンを選択します。

1. **[Add Phrases]** に「`Schedule a real estate showing`」と入力し、**[+]** アイコンを選択します。

1. **[Add Phrases]** に「`Arrange the viewing for a real estate property`」と入力し、**[+]** アイコンを選択します。

1. **[Add Phrases]** に「`Set up an appointment to view a house`」と入力し、**[+]** アイコンを選択します。

1. **[Add Phrases]** に「`Plan a property viewing`」と入力し、**[+]** アイコンを選択します。

1. **[保存]** を選択します。
