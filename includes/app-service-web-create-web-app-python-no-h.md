Cloud Shell で [az webapp create](/cli/azure/webapp?view=azure-cli-latest#az_webapp_create) コマンドを使って、`myAppServicePlan` App Service プランに Web アプリを作成します。 

次の例では、`<app_name>` をグローバルに一意のアプリ名に置き換えてください (有効な文字は `a-z`、`0-9`、`-`)。 ランタイムは `python|3.4` に設定されています。 サポートされているすべてのランタイムを確認するには、[az webapp list-runtimes](/cli/azure/webapp?view=azure-cli-latest#az_webapp_list_runtimes) を実行します。 

```azurecli-interactive
az webapp create --resource-group myResourceGroup --plan myAppServicePlan --name <app_name> --runtime "python|3.4" --deployment-local-git
```

Web アプリが作成されると、Azure CLI によって次の例のような出力が表示されます。

```json
Local git is configured with url of 'https://<username>@<app_name>.scm.azurewebsites.net/<app_name>.git'
{
  "availabilityState": "Normal",
  "clientAffinityEnabled": true,
  "clientCertEnabled": false,
  "cloningInfo": null,
  "containerSize": 0,
  "dailyMemoryTimeQuota": 0,
  "defaultHostName": "<app_name>.azurewebsites.net",
  "deploymentLocalGitUrl": "https://<username>@<app_name>.scm.azurewebsites.net/<app_name>.git",
  "enabled": true,
  < JSON data removed for brevity. >
}
```

Git デプロイが有効な、空の新しい Web アプリが作成されました。

> [!NOTE]
> Git リモートの URL は `deploymentLocalGitUrl` プロパティに `https://<username>@<app_name>.scm.azurewebsites.net/<app_name>.git` 形式で出力されます。 この URL は後で必要になるので保存しておいてください。
>
