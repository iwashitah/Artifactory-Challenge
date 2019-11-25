# Jenkins ArtifactoryプラグインでGradleを利用した**Artifactory Challenge**

## 1. Artifactory Pro版のトライアル申請方法
**Artifactory Challenge**では[オンプレミスまたはクラウド版のフリートライアル](https://jfrog.com/ja/artifactory/free-trial/)を利用可能です。  
オンプレミス版のライセンスの取得方法はWebinarの[JFROG ARTIFACTORY PROのご紹介](https://www.youtube.com/watch?v=M8K6mGC3f6M)の13分13秒〜14分50秒をご確認下さい。

## 2. Artifactoryのインストール方法
Webinarの[JFROG ARTIFACTORY PROのご紹介](https://www.youtube.com/watch?v=M8K6mGC3f6M)または
wikiの[Artifactoryマニュアル](https://www.jfrog.com/confluence/display/RTF/Installing+Artifactory)をご確認下さい。

## 3. Artifactoryのリポジトリ作成方法
[Welcome, admin]→[Quick Setup]をクリックします。
![Artifactory](https://user-images.githubusercontent.com/17076819/69491633-0f90dc80-0edb-11ea-97ba-918c9631ce99.png)

[Create Repositories]パネルで[Maven]→[Create
]をクリックすればバーチャルリポジトリとして[libs-snapshot]と[libs-release]、ローカルリポジトリとして[libs-snapshot-local]と[libs-release-local]が自動的に作成されます。  
**Artifactory Challenge**では[libs-snapshot-local]にビルドします。
![Artifactory](https://user-images.githubusercontent.com/17076819/69491634-0f90dc80-0edb-11ea-8cfd-bc98deda6968.png)

## 4. Jenkinsのインストール方法
Dockerを利用する場合は[jenkinsの2.0-alphaをDockerで試してみよう！](https://qiita.com/letusfly85/items/78306e038a083d449196)がスクリーンショットもあり、分かり易く記述されています。
尚、タグの[2.0-alpha-3]は削除して、以下の通り[latest]をご利用下さい。
```
docker pull jenkinsci/jenkins:2.0-alpha-3
                  ↓
docker pull jenkinsci/jenkins
```

## 5. Jenkinsの設定方法
- #### Artifactoryプラグインのインストール  
  - [プラグインマネージャー]から[Artifactory]を選択し、[再起動せずにインストール]します。
  ![Jenkins](https://user-images.githubusercontent.com/17076819/69491637-10297300-0edb-11ea-991c-44d760c8d756.png)
- #### Gradleの追加
  - [Global Tool Configuration]から[Gradle]の*name*を[gradle]とし、[自動インストール]をチェックして保存します。
  ![Jenkins](https://user-images.githubusercontent.com/17076819/69491638-10297300-0edb-11ea-8a43-9c6abaef0078.png)
- #### Artifactoryの設定
  - [設定]から[Artifactory]を以下の通り設定します。尚、*Password*は[password]です。
  ![Jenkins](https://user-images.githubusercontent.com/17076819/69491639-10c20980-0edb-11ea-8c57-128a2a4b7c07.png)

## 6. Jenkinsパイプラインジョブの作成とビルド方法
- #### 新規パイプラインジョブの作成
  - [Enter an item name]にジョブ名を入力後、[パイプライン]を選択して[OK]をクリックします。
  ![JenkinsJob](https://user-images.githubusercontent.com/17076819/69506071-495ff280-0f70-11ea-987a-e1ae5144dc55.png)
- #### ビルドのパラメータ化
  - 以下の通りにパラメータを設定します。
  ![JenkinsJob](https://user-images.githubusercontent.com/17076819/69506072-495ff280-0f70-11ea-95fb-81c0e3f81421.png)
- #### パイプライン
  - 以下の通りにパラメータを設定します。リポジトリは弊社のサンプルGradleビルドを利用します。
  ![JenkinsJob](https://user-images.githubusercontent.com/17076819/69506073-49f88900-0f70-11ea-8121-d008193fc7a7.png)
- #### ビルド
  - [パラメータ付ビルド]をクリックし、[ビルド]ボタンで実行します。
  ![JenkinsJob](https://user-images.githubusercontent.com/17076819/69506074-49f88900-0f70-11ea-9228-da9c3ce8574d.png)

## 7. Artifactoryでスクリーンショットの取得
Artifactory UIでビルドによって作成されたアーティファクト（Artifact Repository Browserページ）と依存関係（Build Browserページ→Build Name→Build ID）の以下のスクリーンショットをお送り下さい。
![Artifactory](https://user-images.githubusercontent.com/17076819/69509429-6d293580-0f7c-11ea-911c-2e0c9dcd0d2e.png)
![Artifactory](https://user-images.githubusercontent.com/17076819/69509433-6e5a6280-0f7c-11ea-9465-86f09198d1d9.png)

**Artifactory Challenge**に関してのご質問がございましたら、件名に[Artifactory Challengeについて]と記述して、mailto:iwashitah@jfrog.comにお問合せ下さい。
