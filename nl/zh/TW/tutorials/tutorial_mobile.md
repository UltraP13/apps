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
{:tip: .tip}

# 使用入門範本套件來建立行動應用程式
{: #tutorial}

{{site.data.keyword.cloud}} 提供行動入門範本套件以協助您快速建立行動應用程式。請從「應用程式服務入門範本套件」選擇語言、架構及工具，以開始使用預先配置的自訂應用程式。在本指導教學中，您可以了解如何安裝所需的工具、在本端建置並執行應用程式，然後將它部署至雲端。
{: shortdesc}

## 步驟 1. 安裝工具
{: #install-tools}

安裝 [{{site.data.keyword.dev_cli_short}}](/docs/cli/index.html)。

Docker 會安裝為開發人員工具的一部分。Docker 必須在執行中，建置指令才能運作。您必須建立 Docker 帳戶、執行 Docker 應用程式，然後登入。

## 步驟 2. 使用 {{site.data.keyword.dev_console}} 建立應用程式
{: #create-devex}

1. 在 {{site.data.keyword.Bluemix}} 中建立 {{site.data.keyword.dev_console}} 應用程式。
2. 從 {{site.data.keyword.dev_console}} 的[入門範本套件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appservice/starter-kits/) 頁面，根據您要的特性選取入門範本套件。例如，若為 Watson 語言應用程式，請選取 **Swift Kitura**。
3. 輸入應用程式名稱。針對本指導教學，請使用 `WatsonApp`。
4. 選取語言平台。針對本指導教學，請使用 `Swift`。
5. 選取語言及架構。部分入門範本套件可能只提供一種語言。
6. 選取定價方案。有免費選項，您可以用於本指導教學。
7. 按一下**建立**。

## 步驟 3. 新增資源（選用）
{: #add-services}

您可以新增資源，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。針對本指導教學，請新增工作區以便管理您的資料。

1. 從應用程式服務視窗，按一下**新增資源**。
2. 選取您要的服務類型。例如，選取**資料** > **下一步** > **Cloudant** > **下一步**。
3. 選取定價方案。有免費選項，您可以用於本指導教學。
4. 按一下**建立**。

## 步驟 4. 建立 DevOps 工具鏈
{: #add-toolchain}

啟用工具鏈會為您的應用程式建立一個以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們針對您所選部署平台（Kubernetes 或 Cloud Foundry）經過自訂。

已針對部分應用程式啟用持續交付。您可以啟用持續交付，以透過 Delivery Pipeline 及 GitHub 自動建置、測試及部署。

1. 從應用程式服務視窗，按一下**部署至雲端**。
2. 選取部署方法。根據您所選方法的指示設定部署方法。

    * 部署至 Kubernetes 叢集。建立主機（稱為工作者節點）的叢集，以部署及管理高可用性的應用程式容器。您可以建立叢集或部署至現有的叢集。

    * 使用 Cloud Foundry 進行部署，如此便不需要管理基礎的基礎架構。

## 步驟 5. 在本端建置及執行應用程式
{: #build-run}

在前一個步驟中將應用程式部署至雲端時，已經建立了工具鏈。工具鏈會為您的應用程式建立 Git 儲存庫，您可以在該處找到程式碼。請遵循下列步驟來存取您的儲存庫。您可以在本端建置應用程式以進行測試，然後才將它推送至雲端。

1. 從應用程式服務視窗，按一下**下載程式碼**或**複製儲存庫**，以在本端使用程式碼。
2. 將應用程式匯入至整合開發環境。
3. 修改程式碼。
4. 新增個人存取記號來設定 [Git 鑑別](/docs/services/ContinuousDelivery/git_working.html#git_authentication)。
5. 登入 {{site.data.keyword.Bluemix}} 指令行介面。如果您的組織使用聯合登入，請使用 `-sso` 選項。

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 設定您的組織及空間目標。

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  取得認證。

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. 確定 Docker 在執行中，然後在本端開發容器中從目錄建置應用程式。

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. 在本端開發容器中執行應用程式。

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10.  使用瀏覽器開啟 `http://localhost:3000`。您的埠號可能會根據選擇的運行環境而不同。

### 在 Xcode 中執行 Swift 應用程式
{: #run_swift}

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以檢閱配置應用程式的步驟。
2. 開啟您的終端機並導覽至應用程式資料夾，然後執行下列指令：
    1. 如果您需要設定 CocoaPods 儲存庫，請執行 `pod setup`。
    2. 如果您需要更新現有的 Pod，請執行 `pod update`。
    3. 執行 `pod install` 來安裝應用程式的 Pod。
3. 開啟您的 `<appname>.xcworkspace` Xcode 工作區。
4. 執行應用程式。

### 在 Xcode 中執行 Cordova 應用程式
{: #run_cordova_xcode}

如果您選擇使用 Cordova 作為您的實作語言，請遵循這些指示。

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。
2. 在 Xcode 中開啟 `platforms/ios` 應用程式。
3. 執行應用程式。

### 在 Android Studio 中執行 Cordova 應用程式
{: #run_cordova_studio}

如果您選擇使用 Cordova 作為行動應用程式的平台，請使用本小節。

1. 解壓縮 `BasicProject-Cordova.zip` 檔案。
2. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。
3. 在 Android Studio 中開啟 `platforms/android` 應用程式。
4. 執行應用程式。

### 在 Android Studio 中執行 Android 應用程式
{: #run_android}

如果您選擇使用 Android 作為行動應用程式的平台，請使用本小節。

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。
2. 在 Android Studio 中開啟 `BasicProject-Android` 應用程式。
3. 執行應用程式。

## 步驟 6. 部署應用程式
{: #deploy}

### 使用工具鏈進行部署

您有數種方式可以將應用程式部署至 {{site.data.keyword.cloud_notm}}，但 DevOps 工具鏈是部署正式作業應用程式的最佳方法。使用 DevOps 工具鏈，您可以輕鬆地自動部署到許多環境，並快速新增監視、記載和警示服務，以協助您在應用程式成長時進行管理。

使用適當配置的工具鏈，會自動開始建置、部署的循環，並且全都合併到您儲存庫的主要分支。從 {{site.data.keyword.cloud_notm}} 開發人員儀表板建立的所有工具鏈，都會針對自動部署進行配置。


您也可以從 DevOps 工具鏈手動部署應用程式：

1. 從「應用程式詳細資料」視窗，按一下**檢視工具鏈**。

2. 按一下 **Delivery Pipeline**，您可以在其中啟動建置、管理部署，以及檢視日誌和歷程。

### 使用 {{site.data.keyword.dev_cli_short}} 進行部署

若要將應用程式部署至 Cloud Foundry，請輸入下列指令：

```
ibmcloud dev deploy
```
{: pre}

若要將應用程式部署至 Kubernetes 叢集，請輸入下列指令：

```
ibmcloud dev deploy --target <container>
```
{: pre}

## 步驟 7. 驗證應用程式在執行中
{: #verify}

部署應用程式之後，DevOps 管線或指令行會將您指向應用程式的 URL，例如 `abc-devhost.mybluemix.net`。請在瀏覽器中移至該 URL。
