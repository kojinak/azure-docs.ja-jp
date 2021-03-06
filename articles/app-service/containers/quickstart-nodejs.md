---
title: "Azure App Service on Linux での Node.js の作成 | Microsoft Docs"
description: "Azure App Service on Linux で、初めての Node.js の Hello World を数分でデプロイします。"
services: app-service\web
documentationcenter: 
author: cephalin
manager: syntaxc4
editor: 
ms.assetid: 582bb3c2-164b-42f5-b081-95bfcb7a502a
ms.service: app-service-web
ms.workload: web
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: quickstart
ms.date: 05/05/2017
ms.author: cephalin
ms.custom: mvc
ms.openlocfilehash: 3f75a49c697898ee52bcec68e520f103061752a8
ms.sourcegitcommit: 3fca41d1c978d4b9165666bb2a9a1fe2a13aabb6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="create-a-nodejs-web-app-in-azure-app-service-on-linux"></a>Azure App Service on Linux での Node.js Web アプリの作成

> [!NOTE]
> この記事では、Linux 上の App Service にアプリをデプロイします。 _Windows_ 上の App Service にデプロイするには、「[Azure で Node.js Web アプリを作成する](../app-service-web-get-started-nodejs.md)」を参照してください。
>

[App Service on Linux](app-service-linux-intro.md) は、Linux オペレーティング システムを使用する、高度にスケーラブルな自己適用型の Web ホスティング サービスを提供します。 このクイックスタートでは、組み込みイメージを使用して App Service on Linux に Node.js アプリをデプロイする方法を示します。 [Azure CLI](https://docs.microsoft.com/cli/azure/get-started-with-azure-cli) を使用して、組み込みイメージを使用する Web アプリを作成し、Git を使用してその Web アプリに Node.js のコードをデプロイします。

![Azure で実行されるサンプル アプリ](media/quickstart-nodejs/hello-world-in-browser.png)

以下の手順は、Mac、Windows、または Linux コンピューターを使用して実行できます。

## <a name="prerequisites"></a>前提条件

このクイック スタートを完了するには、以下が必要です。

* <a href="https://git-scm.com/" target="_blank">Git をインストールする</a>
* <a href="https://nodejs.org/" target="_blank">Node.js および NPM をインストールする</a>

[!INCLUDE [quickstarts-free-trial-note](../../../includes/quickstarts-free-trial-note.md)]

## <a name="download-the-sample"></a>サンプルのダウンロード

コンピューターのターミナル ウィンドウで、次のコマンドを実行して、サンプル アプリのリポジトリをローカル コンピューターに複製します。

```bash
git clone https://github.com/Azure-Samples/nodejs-docs-hello-world
```

このクイック スタートでは、ターミナル ウィンドウを使ってすべてのコマンドを実行します。

サンプル コードが含まれているディレクトリに移動します。

```bash
cd nodejs-docs-hello-world
```

## <a name="run-the-app-locally"></a>アプリをローカルで実行する

ターミナル ウィンドウを開き、`npm start` スクリプトを使って組み込みの Node.js の HTTP サーバーを起動して、ローカルでアプリケーションを実行します。

```bash
npm start
```

Web ブラウザーを開き、`http://localhost:1337` のサンプル アプリに移動します。

ページに表示されているサンプル アプリの **Hello World** メッセージが表示されます。

![ローカルで実行されるサンプル アプリ](media/quickstart-nodejs/localhost-hello-world-in-browser.png)

ターミナル ウィンドウで **Ctrl + C** キーを押して、Web サーバーを終了します。

[!INCLUDE [cloud-shell-try-it.md](../../../includes/cloud-shell-try-it.md)]

[!INCLUDE [Configure deployment user](../../../includes/configure-deployment-user.md)]

[!INCLUDE [Create resource group](../../../includes/app-service-web-create-resource-group.md)]

[!INCLUDE [Create app service plan](../../../includes/app-service-web-create-app-service-plan-linux.md)]

## <a name="create-a-web-app"></a>Web アプリを作成する

[!INCLUDE [Create web app](../../../includes/app-service-web-create-web-app-nodejs-no-h.md)]

新しく作成された Web アプリに移動します。 _&lt;app_name>_ は、Web アプリの名前に置き換えます。

```bash
http://<app name>.azurewebsites.net
```

![空の Web アプリ ページ](media/quickstart-nodejs/app-service-web-service-created.png)

[!INCLUDE [Push to Azure](../../../includes/app-service-web-git-push-to-azure.md)]

```bash
Counting objects: 23, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (21/21), done.
Writing objects: 100% (23/23), 3.71 KiB | 0 bytes/s, done.
Total 23 (delta 8), reused 7 (delta 1)
remote: Updating branch 'master'.
remote: Updating submodules.
remote: Preparing deployment for commit id 'bf114df591'.
remote: Generating deployment script.
remote: Generating deployment script for node.js Web Site
remote: Generated deployment script files
remote: Running deployment command...
remote: Handling node.js deployment.
remote: Kudu sync from: '/home/site/repository' to: '/home/site/wwwroot'
remote: Copying file: '.gitignore'
remote: Copying file: 'LICENSE'
remote: Copying file: 'README.md'
remote: Copying file: 'index.js'
remote: Copying file: 'package.json'
remote: Copying file: 'process.json'
remote: Deleting file: 'hostingstart.html'
remote: Ignoring: .git
remote: Using start-up script index.js from package.json.
remote: Node.js versions available on the platform are: 4.4.7, 4.5.0, 6.2.2, 6.6.0, 6.9.1.
remote: Selected node.js version 6.9.1. Use package.json file to choose a different version.
remote: Selected npm version 3.10.8
remote: Finished successfully.
remote: Running post deployment command(s)...
remote: Deployment successful.
To https://<app_name>.scm.azurewebsites.net:443/<app_name>.git
 * [new branch]      master -> master
```

## <a name="browse-to-the-app"></a>アプリの参照

Web ブラウザーを使用して、デプロイされたアプリケーションを参照します。

```bash
http://<app_name>.azurewebsites.net
```

Node.js のサンプル コードが、組み込みイメージを使用する Web アプリで実行されています。

![Azure で実行されるサンプル アプリ](media/quickstart-nodejs/hello-world-in-browser.png)

**お疲れさまでした。** App Service on Linux に初めての Node.js アプリをデプロイしました。

## <a name="update-and-redeploy-the-code"></a>コードを更新して再デプロイする

ローカル ディレクトリで、Node.js アプリ内の `index.js` ファイルを開き、`response.end` の呼び出し内のテキストを少し変更します。

```nodejs
response.end("Hello Azure!");
```

Git で変更をコミットしてから、コード変更を Azure にプッシュします。

```bash
git commit -am "updated output"
git push azure master
```

デプロイが完了したら、「**アプリの参照**」の手順で開いた元のブラウザー ウィンドウに切り替えて、更新をクリックします。

![Azure で実行される更新済みのサンプル アプリ](media/quickstart-nodejs/hello-azure-in-browser.png)

## <a name="manage-your-new-azure-web-app"></a>新しい Azure Web アプリを管理する

<a href="https://portal.azure.com" target="_blank">Azure Portal</a> に移動し、作成した Web アプリを管理します。

左側のメニューで **[App Services]** をクリックした後、Azure Web アプリの名前をクリックします。

![Azure Web アプリへのポータル ナビゲーション](./media/quickstart-nodejs/nodejs-docs-hello-world-app-service-list.png)

Web アプリの [概要] ページを確認します。 ここでは、参照、停止、開始、再開、削除のような基本的な管理タスクを行うことができます。 

![Azure Portal の [App Service] ページ](media/quickstart-nodejs/nodejs-docs-hello-world-app-service-detail.png)

左側のメニューは、アプリを構成するためのさまざまなページを示しています。 

[!INCLUDE [cli-samples-clean-up](../../../includes/cli-samples-clean-up.md)]

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [Node.js と MongoDB](tutorial-nodejs-mongodb-app.md)
