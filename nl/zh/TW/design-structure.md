---

copyright:

  years: 2018
lastupdated: "2018-10-26"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 設計 IBM Cloud Foundry Enterprise Environment 的結構
{: #bpimplementation}

您可以實作開發人員及測試人員可與其他團隊成員分工合作的環境，而不實作傳統且嚴格定義的開發、測試及正式作業方法。如果您設計要開發及交付應用程式的方式，請建立空間來達成該方法。您可以考慮從空間層次向上設計 {{site.data.keyword.cfee_full}} (CFEE)，而不要從組織層次向下設計環境。

請考量您計劃開發及部署之應用程式的規模和範圍。Cloud Foundry 空間可以用來作為一個以上緊密連接或定義之應用程式的開發環境。例如，除了開發空間之外，您還可以建立空間來進行單元測試、效能測試及整合測試。您也可以為建置、編譯打包和正式作業定義空間。您建立的每一個空間都可以與相同組織內的不同團隊成員共用。

如果您的員工在不同的業務領域工作，而且其活動未重疊，則請建立個別的 Cloud Foundry 組織。如果有兩個獨立群組，則為每個群組建立一個組織，可以為交付和管理團隊成員和資源定義明確的界限。您可以定義 API，以在組織之間進行通訊。

您可以建立 Cloud Foundry 組織，以符合您要的工作方式，而不是符合公司內的結構。一般而言，公司組織可能會變更，但應用程式的開發及維護仍會照常繼續。請針對應用程式生命期限設計 {{site.data.keyword.cfee_full}} 實例，而不是根據您的公司組織結構。

反覆地開發及部署可能會導致應用程式快速擴充。您的交付程序設計必須能夠快速並輕鬆地擴增。您要以快速部署速率進行持續開發。在相同的 CFEE 組織中具有開發及正式作業空間，可讓您存取相同的資源。管理單一組織內的不同空間可減少管理工作負載。如果開發、測試和作業人員在相同的 CFEE 組織內工作，就可以輕鬆地分工合作。

實作命名標準，以清楚識別組織和空間用途。例如，您可以包含雲端類型、地理區域、使用類型（如開發、測試、正式作業）、應用程式名稱，以及版本或修訂號碼。如此就可以輕鬆地識別組織和空間的管理及存取用途。  

空間數可能會因為反覆開發而快速倍增。您可以在組織內定義所需的空間數。如果您計劃定義許多空間，則可以建立應用程式來協助管理空間。當空間數超過 60 個時，建議您考慮再定義另一個組織。

請某位人員來建立及管理組織、定義空間，以及授與團隊成員存取權。組織管理員失能時，可以授與第二個人員相同的存取權來維護環境。  

識別需要存取每個空間及組織的所有人員。決定他們的角色。團隊成員的工作角色會決定他們的權限。例如，資深開發人員需要權限來檢視及更新整個 {{site.data.keyword.cfee_full}} 開發環境。不過，資淺開發人員則會受限於他們可檢視及更新的內容。
