---
lab:
  title: エンティティの使用
  module: Work with entities and variables in Microsoft Copilot Studio
---

# エンティティの使用

## シナリオ

このラボでは、次のことを行います。

- エンティティの作成と使用

## 学習する内容

- エンティティを作成および使用してコパイロットを改善する方法

## ラボ手順の概要

- エンティティを作成する
- ノードでエンティティを使用する
  
## 前提条件

- **ラボ: ノードの管理**を完了している必要があります

## 詳細な手順

## 演習 1 - エンティティを作成する

Microsoft Copilot Studio では、エンティティを使用してユーザーの意図を理解します。 よく使用される情報用に、事前構築済みのエンティティが多数含まれています。 特定の目的に合わせて、カスタム エンティティを作成できます。

### タスク 1.1 - 事前構築済みのエンティティを表示する

1. Microsoft Copilot Studio ポータル `https://copilotstudio.microsoft.com` に移動し、適切な環境にあることを確認します。

1. 左側のナビゲーション ウィンドウから **[Copilot]** を選択します。

1. 前のラボで作成した **[Real Estate Booking Service]** を選択します。

1. 画面の右上にある **[Settings]** を選択します。

1. **[Entities]** タブを選択します。

    ![[Entities] タブのスクリーンショット。](../media/system-entities.png)

### タスク 1.2 - プロパティ型エンティティを作成する

1. **[+ Add an entity]** を選択し、**[+ New entity]** を選択します。

    ![新しいエンティティのメソッドを選択している場面を示すスクリーンショット。](../media/add-an-entity.png)

1. **[Closed list]** タイルを選択します。

1. **[Name]** フィールドに「**`Property Type`**」と入力します。

1. **[Enter item]** フィールドに「**`Apartment`**」と入力し、**[Add]** を選択します。

1. **[Enter item]** フィールドに「**`Condominium`**」と入力し、**[Add]** を選択します。

1. **[Enter item]** フィールドに「**`Duplex`**」と入力し、**[Add]** を選択します。

1. **[Enter item]** フィールドに「**`House`**」と入力し、**[Add]** を選択します。

1. **Apartment** の **[+ Synonyms]** を選択し、「**`Flat`**」と入力して **[+]** アイコンを選択し、**[Done]** を選択します。

1. **Condominium** の **[+ Synonyms]** を選択し、「**`Townhouse`**」と入力して **[+]** アイコンを選択し、**[Done]** を選択します。

1. **House** の **[+ Synonyms]** を選択し、「**`Single-family home`**」と入力して **[+]** アイコンを選択し、**[Done]** を選択します。

    ![新しいエンティティのスクリーンショット。](../media/add-list-entity.png)

1. **[保存]** を選択します。

1. **[閉じる]** を選択します。

### タスク 1.3 - ベッドルーム エンティティの数を作成する

1. **[+ Add an entity]** を選択し、**[+ New entity]** を選択します。

1. **[Regular expression (Regex)]** タイルを選択します。

1. **[Name]** フィールドに「**`Number of Bedrooms`**」と入力します。

1. **[Pattern]** フィールドに「**`[1-5]`**」と入力します。

1. **[保存]** を選択します。

1. **[閉じる]** を選択します。

## 演習 2 - エンティティを使用してコパイロットを改善する

会話フローでエンティティを使用して、コパイロットを改善します。

### タスク 2.1 - エンティティを使用する

1. 右上にある **[X]** アイコンを選択して [Settings] を閉じ、コパイロットに戻ります。

1. **[Topics]** タブを選択します。

1. **[不動産の内見を予約する]** トピックを選択します。

1. **[Condition]** ノードとプロパティ **[Question]** ノードの間の **[+]** アイコンを選択し、**[Ask a question]** を選択します。

1. **"Enter a message"** フィールドに、次のテキストを入力します。

    `What type of property do you want to see?`

1. **[Identify]** には、**[Property Type]** を選択します。

1. **[Select options for user]** を選択し、4 つの値すべてに対して **[Display]** オプションをオンにします。

1. **[Save user response as]** で変数を選択し、**[Variable name]** に「**`PropertyType`**」を入力します。

    ![新しいエンティティのスクリーンショット。](../media/question-node-entity.png)

1. 新しい **[Question]** ノードの下にある **[+]** アイコンを選択し、**[Ask a question]** を選択します。

1. **"Enter a message"** フィールドに、次のテキストを入力します。

    `How many bedrooms do you need?`

1. **[Identify]** には、**[Number of Bedrooms]** を選択します。

1. **[Save user response as]** で変数を選択し、**[Variable name]** に「**`NumberofBedrooms`**」を入力します。

1. **[保存]** を選択します。
