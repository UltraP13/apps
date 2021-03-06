---

copyright:
  years: 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# 從您自己的程式碼儲存庫建立應用程式
{: #code-repo}

您可以使用現有的應用程式儲存庫，在 {{site.data.keyword.cloud}} 中建立應用程式。只需在建立應用程式期間提供儲存庫的 Web 鏈結、繼續新增資源，然後將 DevOps 工具鏈連接至應用程式以進行部署。
{: shortdesc}

## 開始之前
{: #prereqs}

請確定已備妥下列必要條件：

 * 安裝 [{{site.data.keyword.dev_cli_long}} 指令行介面 (CLI)](/docs/cli/index.html)。
 * 參閱[構成良好應用程式的要點？](/docs/apps/best-practice.html)，以取得建立應用程式的最佳作法。
 * 您必須具有來自下列任何提供者的 Git 原始碼儲存庫：GitHub、GitHub Enterprise、Git Lab、BitBucket 或 Rational。

## 步驟 1. 使用現有的儲存庫建立應用程式
{: #create}

若要建立應用程式並將其與原始檔儲存庫連接，請完成下列步驟：

1. 從[儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}){: new_window}，按一下**應用程式**磚中的**建立應用程式**。
2. 為應用程式命名，然後選取資源群組。
3. 選取**自帶程式碼**，並提供 Git 儲存庫的 URL。您的應用程式及 Docker 映像檔必須位於相同的儲存庫中。
4. 按一下**建立**。

即會顯示**應用程式詳細資料**頁面。從這裡，您可以：
* [新增資源](/docs/apps/reqnsi.html)（選用）。
* 按一下**連接至 DevOps 工具鏈**，將應用程式連接至 DevOps 工具鏈。如果您還沒有工具鏈，則會開啟**連接 DevOps 工具鏈**頁面。按一下**建立 DevOps 工具鏈**。此時，[DevOps 儀表板](https://{DomainName}/devops/)中的[建立工具鏈](https://{DomainName}/devops/create)頁面會在瀏覽器的新標籤中開啟。在該標籤中建立並配置工具鏈之後，您必須回到應用程式中的**連接工具鏈**頁面，然後重新整理頁面。如需相關資訊，請參閱[將應用程式連接至新的工具鏈](#create_toolchain)。
* 按一下**檢視儲存庫**來檢視您的儲存庫。
* 按一下**應用程式詳細資料**頁面上的任何相關鏈結，進一步瞭解工具鏈或應用程式建立體驗。

## 步驟 2. 將應用程式連接至 DevOps 工具鏈
{: #connect_toolchain}

建立應用程式、工具鏈與儲存庫之間的鏈結，是邁向組織產品資產的一步。它也有助於用 DevOps 工作流程、執行中的應用程式實例，以及跨所有部署目標的相依服務，聚集您原始碼儲存庫的視圖。如需相關資訊，請參閱[將應用程式連接至新的工具鏈](/docs/services/ContinuousDelivery/toolchains_working.html)。

您可以使用 {{site.data.keyword.cloud_notm}} 主控台或 CLI，將應用程式連接至 DevOps 工具鏈。 

### 使用主控台

  1. 按一下**連接至 DevOps 工具鏈**，將應用程式連接至 DevOps 工具鏈。 
  
    如果您沒有現有的工具鏈，請按一下**建立 DevOps 工具鏈**。 
    
  2. 在建立並配置工具鏈之後，請回到應用程式中的「連接工具鏈」頁面，然後重新整理頁面。 

### 使用 CLI

您可以使用 `ibmcloud dev enable` 指令，來產生「DevOps 工具鏈」範本，然後您可以將其移入儲存庫，作為「DevOps 工具鏈」要建立什麼的指示集。 

  1. 從「應用程式服務」視窗，按一下**下載程式碼**或**複製儲存庫**，以在本端使用程式碼。
  2. 請執行下列指令：
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

如需相關資訊，請參閱[使用 CLI 建立及部署應用程式](/docs/apps/create-deploy-cli.html#developing)。

## 步驟 3. 部署應用程式
{: #deploy_app}

將 DevOps 工具鏈附加至應用程式之後，請完成下列步驟以將其部署至 {{site.data.keyword.cloud_notm}}： 

1. 從「應用程式詳細資料」頁面中，按一下**部署至雲端**。
2. 選取部署方法。 

    * [部署至 Kubernetes 叢集](/docs/apps/tutorials/tutorial_byoc_kube.html)。建立主機（稱為工作者節點）的叢集，以部署及管理高可用性的應用程式容器。您可以建立叢集或部署至現有的叢集。
    * 使用 Cloud Foundry 進行部署，如此便不需要管理基礎的基礎架構。
    * 部署至[虛擬伺服器實例](/docs/apps/vsi-deploy.html)。


