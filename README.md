> **This repository is optimized for Japanese.**

# Generative AI Use Cases JP

Generative AI（生成系 AI）は、ビジネスの変革に革新的な可能性をもたらします。このリポジトリでは、Generative AI を活用したビジネスユースケースをデモンストレーションしています。

![sc_lp.png](/imgs/sc_lp.png)

動画でデプロイ手順とデモンストレーションをご覧いただけます。以下のサムネイルをクリックして再生してください。なおデプロイ手順につきましては、詳細な手順を後述しております。

| **デプロイ手順**                                                                                             | **デモンストレーション**                                                                             |
|--------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| [![デプロイ手順](https://img.youtube.com/vi/9sMA17OKP1k/0.jpg)](https://www.youtube.com/watch?v=9sMA17OKP1k) | [![デモ](https://img.youtube.com/vi/rkKZZSuVZUU/0.jpg)](https://www.youtube.com/watch?v=rkKZZSuVZUU) |

> - 2023年8月現在、Amazon Bedrock はプレビュー版であるため、このリポジトリの実装には含まれていません。OpenAI を LLM としてサポートしていますので、そちらをご利用いただけます。Amazon Bedrock が GA になり次第、対応いたします。
> - OpenAI を LLM として利用する場合は、別途利用料金がかかります。OpenAI 利用に関する情報は、事前に [OpenAI](https://platform.openai.com/) で確認してください。

## Why Generative AI on AWS?

[AWS Summit New York City 2023 の Keynote](https://www.youtube.com/watch?v=1PkABWCJINM&t=1652s) で、**データこそが差別化要因である**というメッセージが強調されました。Generative AI が普及した世界では、差別化の要因となるのは蓄積されたデータそのものであるということです。AWS は多岐にわたるデータの様式・蓄積・検索に対応したサービスを提供しており、強力なデータ基盤と Amazon Bedrock の Fine-tuning とを組み合わせることで、高品質な Generative AI を構築することができます。

## 機能一覧

> :white_check_mark: ... 実装されている、:construction: ... まだ実装されていない

- :white_check_mark: OpenAI を LLM として利用
- :construction: Amazon Bedrock を LLM として利用
- :construction: Amazon Bedrock Fine-tuning 用のデータ収集
- :construction: Amazon Bedrock Fine-tuning の実行

## ユースケース一覧

> ビジネスユースケースは随時追加予定です。ご要望があれば [Issue](https://github.com/aws-samples/generative-ai-use-cases-jp/issues) に起票をお願いいたします。

#### チャット

LLM とチャット形式で対話することができます。LLM と直接対話するプラットフォームが存在するおかげで、細かいユースケースや新しいユースケースに迅速に対応することができます。また、プロンプトエンジニアリングの検証用環境としても有効です。

<details>
  <summary>動作の様子 (スクリーンショット)</summary>
  <img src="/imgs/sc_chat.png"/>
</details>

#### 要約

LLM は、大量の文章を要約するタスクを得意としています。ただ要約するだけでなく、文章をコンテキストとして与えた上で、必要な情報を対話形式で引き出すこともできます。例えば、契約書を読み込ませて「XXX の条件は？」「YYY の金額は？」といった情報を取得することが可能です。

<details>
  <summary>動作の様子 (スクリーンショット)</summary>
  <img src="/imgs/sc_summary.png"/>
</details>

#### メール作成

ビジネスメールの作成を日常的に行う人々は、形式的な挨拶や敬語の繰り返しではなく、メールの内容に集中したいと考えているでしょう。LLM を使用することで、そのような冗長なタスクを極力減らし、ルーチンワークにかかる時間を大幅に削減することが可能です。さらに、単に補完するだけでなく、誤字脱字の防止という効果も期待できます。

<details>
  <summary>動作の様子 (スクリーンショット)</summary>
  <img src="/imgs/sc_mail.png"/>
</details>

#### 情報抽出

文章を LLM に読み込ませることで、必要な情報を抽出できます。LLM は文章を的確に理解し、文体に気を使うことなく情報を抽出することが可能です。

<details>
  <summary>動作の様子 (スクリーンショット)</summary>
  <img src="/imgs/sc_extract.png"/>
</details>

#### CS 業務効率化

人々が手動で処理する必要のある多数の問い合わせに対しても、LLM の活用が可能です。例えば、お客様からの問い合わせに対して「OK」や「無理です」といった単純な返答から、「承知いたしました。直ちに対応いたします。」や「申し訳ございません。お客様のプランではその機能の有効化はできません。」などの表現への変換が可能です。お客様からの問い合わせ内容をコンテキストとすることで、適切な文章へと変換することができます。さらに、Fine-tuning することで、「OK」や「無理です」といった返答を打つ必要がなくなる可能性もあります。

<details>
  <summary>動作の様子 (スクリーンショット)</summary>
  <img src="/imgs/sc_cs.png"/>
</details>

> 現在、このリポジトリでは Fine-tuning はサポートされていません。
> Amazon Bedrock 及びその Fine-tuning 機能のリリースが完了次第、対応を予定しています。

## アーキテクチャ

このサンプルでは、フロントエンドは React を用いて実装し、静的ファイルは CloudFront + S3 によって配信されています。バックエンドには API Gateway + Lambda、認証には Congito を使用しています。また、LLM は OpenAI または Amazon Bedrock (現在は未実装) を使用します。今後、会話履歴機能や Fine-tuning 機能の追加が予定されています。

![arch.png](/imgs/arch.png)

## デプロイ

> **OpenAI を LLM として使用する場合は、あらかじめ [OpenAI の API キーを取得](https://platform.openai.com/account/api-keys)してください。**

[AWS Cloud Development Kit](https://aws.amazon.com/jp/cdk/)（以降 CDK）を利用してデプロイします。最初に、npm パッケージをインストールしてください。なお、全てのコマンドはルートディレクトリで実行してください。

```bash
npm ci
```

OpenAIを使用する場合は以下のように、Secret Manager で API Key を保存します。(現状は LLM として OpenAI のみがサポートされているため、必須の手順です。)

```bash
aws secretsmanager create-secret --name openai-secret --secret-string <Open AI の API キー>
```

上記のコマンド実行後、作成した Secret の ARN がレスポンスとして返ってくるため、[cdk.json](packages/cdk/cdk.json) の context の `openAiApiKeySecretArn` を受け取った値に変更します。

CDK を利用したことがない場合、初回のみ [Bootstrap](https://docs.aws.amazon.com/ja_jp/cdk/v2/guide/bootstrapping.html) 作業が必要です。すでに Bootstrap された環境では以下のコマンドは不要です。

```bash
npx -w packages/cdk cdk bootstrap
```

最後に、以下のコマンドでデプロイします。

```bash
npm run cdk:deploy
```

cdk.json にコミットせず、以下のようにコマンドライン引数で OpenAI API Key を渡すこともできます。

```bash
npm run cdk:deploy -- -c openAiApiKeySecretArn=<Secret ARN>
```

## ローカル環境構築手順

開発者用にローカル環境を構築する手順を説明します。なお、ローカル環境を構築する場合も、前述した AWS へのデプロイは完了している必要があります。

デプロイ完了時に表示される Outputs から API の Endpoint (Output key = APIApiEndpoint...)、Cognito User Pool ID (Output key = AuthUserPoolId...)、Cognito User Pool Client ID (Output Key = AuthUserPoolClientId...) 、Cognito Identity Pool ID (Output Key = AuthIdPoolId...)、レスポンスストリーミングの Lambda 関数の ARN (Output Key = APIPredictStreamFunctionArn...) を取得します。
デプロイ時の出力が消えている場合、[CloudFormation](https://console.aws.amazon.com/cloudformation/home) の GenerativeAiUseCasesStack をクリックして Outputs タブから確認できます。
それらの値を以下のように環境変数に設定してください。

```bash
export VITE_APP_API_ENDPOINT=<API Endpoint>
export VITE_APP_USER_POOL_ID=<Cognito User Pool ID>
export VITE_APP_USER_POOL_CLIENT_ID=<Cognito User Pool Client ID>
export VITE_APP_IDENTITY_POOL_ID=<Cognito Identity Pool ID>
export VITE_APP_PREDICT_STREAM_FUNCTION_ARN=<Function ARN>
export VITE_APP_REGION=<デプロイしたリージョン>
```

具体例は以下です。

```bash
export VITE_APP_API_ENDPOINT=https://xxxxxxxxxx.execute-api.ap-northeast-1.amazonaws.com/api/
export VITE_APP_USER_POOL_ID=ap-northeast-1_xxxxxxxxx
export VITE_APP_USER_POOL_CLIENT_ID=abcdefghijklmnopqrstuvwxyz
export VITE_APP_IDENTITY_POOL_ID=ap-northeast-1:xxxxxxxx-xxxx-xxxx-xxxxxxxxxxxxxxxxx
export VITE_APP_PREDICT_STREAM_FUNCTION_ARN=arn:aws:lambda:ap-northeast-1:000000000000:function:FunctionName
export VITE_APP_REGION=ap-northeast-1
```

続いて以下のコマンドを実行します。

```bash
npm run web:dev
```

正常に実行されれば http://localhost:5173 で起動しますので、ブラウザからアクセスしてみてください。

### Pull Request を出す場合

バグ修正や機能改善などの Pull Request は歓迎しております。コミットする前に、lint ツールを実行してください。

```bash
npm run lint
```

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
