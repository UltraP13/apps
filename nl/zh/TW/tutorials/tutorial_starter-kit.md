---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 使用入門範本套件建立應用程式
{: #create_starterkit}

您可以使用入門範本套件，快速讓您的應用程式啟動，並準備它以便未來進行開發。選擇入門範本套件和程式設計語言、建立應用程式，然後設定 DevOps 工具鏈，以自動部署應用程式。您也可以下載程式碼以便立即進行檢驗。
{: shortdesc}

您可以從一群精選的入門範本套件建立應用程式，這其中包括空白的入門範本套件（如果您想要自己自訂建置選項的話）。無論哪一種方法，都會自動建立 DevOps 工具鏈來部署應用程式。您也可以下載程式碼以便立即進行檢驗。

入門範本套件有許多種類，其中包括：
* [Watson ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/watson/dashboard){:new_window}
* [Apple ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appledevelopment/dashboard){:new_window}
* [行動 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/mobile/dashboard){:new_window}
* [Web 應用程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appservice/dashboard){:new_window}
* [安全 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/security/dashboard){:new_window}
* [財務 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/finance/dashboard){:new_window}

## 步驟 1. 建立應用程式
{: #create-app}

1. 從 [{{site.data.keyword.cloud}} 儀表板](https://{DomainName})中，按一下**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > **Web 應用程式**。

2. 按一下**從 Web 開始**區段中的**開始使用**。

3. 選取您選擇的入門範本套件、閱讀詳細資料，然後按一下**建立**。
    
    若要查看入門範本套件中所包含的內容，請展開[應用程式服務入門範本套件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appservice/starter-kits){:new_window} 儀表板上的磚。「建立應用程式」入門範本套件選項可以用來作為空白的入門範本應用程式，並可進一步自訂以符合您的需求。
    {: tip}

4. 為您的應用程式命名、選取語言，然後按一下**建立**。
    
    很棒的開始！您剛剛建立了應用程式。

若要檢查您的程式碼，請按一下應用程式詳細資料頁面上的**下載程式碼**。請檢查所下載壓縮檔中的 `README.md` 檔，以找出您是否需要採取更多動作，以讓入門範本應用程式啟動並執行。
{: tip}

如需相關資訊，請參閱[使用入門範本套件來建立基本 Web 應用程式](/docs/apps/tutorials/tutorial_web.html)。

## 步驟 2. 新增資源
{: #add-services}

您可以新增資源，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。針對本指導教學，請新增工作區以便管理您的資料。

1. 從應用程式服務視窗，按一下**新增資源**。
2. 選取您要的服務類型。例如，選取**資料** > **下一步** > **Cloudant** > **下一步**。
3. 選取定價方案。有免費選項，您可以用於本指導教學。
4. 按一下**建立**。

## 步驟 3. 部署至 {{site.data.keyword.cloud_notm}}
{: #deploy}

按一下「應用程式詳細資料」頁面上的**部署至雲端**、選取部署方法（例如 Kubernetes 叢集或 Cloud Foundry 應用程式），然後按一下**建立**。{{site.data.keyword.cloud_notm}} 會自動建立開放式工具鏈，此工具鏈會完整地具備 Git 儲存庫及持續交付管線。請開啟新工具鏈的管線元件，以開始起始的建置並部署處理程序，以便您可以在數分鐘內看到您的新應用程式。

若要使用指令行來部署應用程式，請使用 `ibmcloud dev deploy`。如需相關資訊，請參閱[使用 CLI 建立及部署應用程式](/docs/apps/create-deploy-cli.html)。
