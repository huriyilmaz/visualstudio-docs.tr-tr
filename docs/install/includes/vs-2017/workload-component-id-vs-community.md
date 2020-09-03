---
title: Visual Studio Community 2017 iş yükü ve bileşen kimlikleri
titleSuffix: ''
description: Komut satırını kullanarak Visual Studio 'Yu yüklemek veya bir VSıX bildiriminde bağımlılık olarak belirtmek için iş yükü ve bileşen kimliklerini kullanma
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 2/12/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 83a1daa65642d720bd5f2420ee634688cf4be2c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76159580"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-community-2017"></a>Visual Studio çekirdek Düzenleyicisi (Visual Studio Community 2017 ile birlikte)

**Kimliği:** Microsoft. VisualStudio. Workload. CoreEditor

**Açıklama:** Sözdizimi kullanan kod düzenlemesi, kaynak kodu denetimi ve iş öğesi yönetimi de dahil olmak üzere Visual Studio Core kabuğu deneyimi.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. VisualStudio. Component. CoreEditor | Visual Studio temel Düzenleyicisi | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. Startpagedenemeler. cpp | C++ kullanıcıları için Visual Studio başlangıç sayfası | 15.0.27128.1 | İsteğe Bağlı

## <a name="azure-development"></a>Azure geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Azure

**Açıklama:** Bulut uygulamaları geliştirmeye, kaynak oluşturmaya ve Docker desteği dahil kapsayıcılar oluşturmaya yönelik Azure SDK 'Ları, araçları ve projeleri.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 15.0.26720.2 | Gerekli
Component. Microsoft. VisualStudio. Web. AzureFunctions | Microsoft Azure Web Işleri araçları | 15.7.27617.1 | Gerekli
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 15.8.27705.0 | Gerekli
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | Gerekli
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft. Component. NetFX. Core. Runtime | .NET Core çalışma zamanı | 15.0.26208.0 | Gerekli
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. net. Core. Component. SDK. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. NetCore. ComponentGroup. DevelopmentTools. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. NetCore. ComponentGroup. Web. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Azure yazma araçları | 15.9.28307.421 | Gerekli
Microsoft. VisualStudio. Component. Azure. Clientlıbs | .NET için Azure kitaplıkları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. Azure. COMPUTE. öykünücü | Azure Işlem öykünücüsü | 15.9.28307.421 | Gerekli
Microsoft. VisualStudio. Component. Azure. Storage. öykünücü | Azure Storage Öykünücüsü | 15.9.28125.51 | Gerekli
Microsoft. VisualStudio. Component. CloudExplorer | Cloud Explorer | 15.9.28230.55 | Gerekli
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 15.8.27906.1 | Gerekli
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Kapsayıcı geliştirme araçları-derleme araçları | 15.7.27617.1 | Gerekli
Microsoft. VisualStudio. Component. FSharp | F # dil desteği | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. FSharp. WebTemplates | Web projeleri için F # dil desteği | 15.9.28307.421 | Gerekli
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server komut satırı yardımcı programları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. DataSources | SQL Server destek için veri kaynakları | 15.0.26621.2 | Gerekli
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Gerekli
Microsoft. VisualStudio. Component. SQL. NCLI | SQL Server Native Client | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 15.9.28107.0 | Gerekli
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Gerekli
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. Web | ASP.NET ve Web geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. ComponentGroup. Azure. Önkoşullar | Azure geliştirme önkoşulları | 15.9.28107.0 | Gerekli
Microsoft. VisualStudio. ComponentGroup. AzureFunctions | Microsoft Azure Web Işleri araçları | 15.7.27617.1 | Gerekli
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve Web geliştirme araçları önkoşulları | 15.9.28219.51 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Gerekli
Microsoft. Component. Azure. DataLake. Tools | Azure Data Lake ve Stream Analytics araçları | 15.9.28107.0 | Önerilen
Microsoft.Net. Component. 4.5.1. TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.6. TargetingPack | .NET Framework 4,6 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. ComponentGroup. TargetingPacks. Common | .NET Framework 4 – 4,6 geliştirme araçları | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. AspNet45 | Gelişmiş ASP.NET özellikleri | 15.7.27625.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. MobileAppsSdk | Azure Mobile Apps SDK 'Sı | 15.7.27625.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. ResourceManager. Tools | Azure Resource Manager çekirdek araçları | 15.9.28107.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. ServiceFabric. Tools | Service Fabric Araçları | 15.8.27825.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. Waverton | Azure Cloud Services çekirdek araçları | 15.9.28107.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. Waverton. BuildTools | Azure Cloud Services derleme araçları | 15.7.27617.1 | Önerilen
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. ComponentGroup. Azure. CloudServices | Azure Cloud Services araçları | 15.0.26504.0 | Önerilen
Microsoft. VisualStudio. ComponentGroup. Azure. ResourceManager. Tools | Azure Resource Manager araçları | 15.0.27005.2 | Önerilen
Microsoft. net. Component. 4.6.2. SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.6.2. TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7.1. SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.1. TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7.2. SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 15.8.27825.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7. SDK | .NET Framework 4,7 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7. TargetingPack | .NET Framework 4,7 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.6.2. DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.1. DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.2. DeveloperTools | .NET Framework 4.7.2 geliştirme araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7. DeveloperTools | .NET Framework 4,7 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK | .NET Core 2,0 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK. 1x | .NET Core 1,0-1,1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. NetCore. 1x. ComponentGroup. Web | Web için .NET Core 1,0-1,1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. NetCore. ComponentGroup. DevelopmentTools | .NET Core 2,0 geliştirme araçları | 15.8.27729.1 | İsteğe Bağlı
Microsoft. NetCore. ComponentGroup. Web | .NET Core 2,0 geliştirme araçları | 15.7.27625.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. Storage. AzCopy | Azure depolama AzCopy | 15.0.26906.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. WCF. Tooling | Windows Communication Foundation | 15.8.27924.0 | İsteğe Bağlı

## <a name="data-storage-and-processing"></a>Veri depolama ve işleme

**Kimliği:** Microsoft. VisualStudio. Workload. Data

**Açıklama:** SQL Server, Azure Data Lake veya Hadoop ile veri çözümlerini bağlayın, geliştirin ve test edin.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 15.0.26720.2 | Önerilen
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 15.8.27705.0 | Önerilen
Component. Redgate. SQLSearch. Vsextenma | Redgate SQL Araması | 3.1.7.2062 | Önerilen
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | Önerilen
Microsoft. Component. Azure. DataLake. Tools | Azure Data Lake ve Stream Analytics araçları | 15.9.28107.0 | Önerilen
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | Önerilen
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Önerilen
Microsoft.Net. Component. 4.5.1. TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.6. TargetingPack | .NET Framework 4,6 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Önerilen
Microsoft.Net. ComponentGroup. TargetingPacks. Common | .NET Framework 4 – 4,6 geliştirme araçları | 15.6.27406.0 | Önerilen
Microsoft. net. Core. Component. SDK. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Azure yazma araçları | 15.9.28307.421 | Önerilen
Microsoft. VisualStudio. Component. Azure. Clientlıbs | .NET için Azure kitaplıkları | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. COMPUTE. öykünücü | Azure Işlem öykünücüsü | 15.9.28307.421 | Önerilen
Microsoft. VisualStudio. Component. Azure. Storage. öykünücü | Azure Storage Öykünücüsü | 15.9.28125.51 | Önerilen
Microsoft. VisualStudio. Component. Azure. Waverton | Azure Cloud Services çekirdek araçları | 15.9.28107.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. Waverton. BuildTools | Azure Cloud Services derleme araçları | 15.7.27617.1 | Önerilen
Microsoft. VisualStudio. Component. CloudExplorer | Cloud Explorer | 15.9.28230.55 | Önerilen
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | Önerilen
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 15.8.27906.1 | Önerilen
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Kapsayıcı geliştirme araçları-derleme araçları | 15.7.27617.1 | Önerilen
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Önerilen
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Önerilen
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server komut satırı yardımcı programları | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. SQL. DataSources | SQL Server destek için veri kaynakları | 15.0.26621.2 | Önerilen
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Önerilen
Microsoft. VisualStudio. Component. SQL. NCLI | SQL Server Native Client | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 15.9.28107.0 | Önerilen
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Önerilen
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. Web | ASP.NET ve Web geliştirme araçları | 15.8.27825.0 | Önerilen
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve Web geliştirme araçları önkoşulları | 15.9.28219.51 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Önerilen
Microsoft. VisualStudio. Component. FSharp. Desktop | F # masaüstü dil desteği | 15.8.27825.0 | İsteğe Bağlı

## <a name="data-science-and-analytical-applications"></a>Veri bilimi ve analitik uygulamalar

**Kimliği:** Microsoft. VisualStudio. Workload. DataScience

**Açıklama:** Python, R ve F # dahil veri bilimi uygulamaları oluşturmak için Diller ve araçlar.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Anaconda3. x64 | Anaconda3 64-bit (5.2.0) | 5.2.0 | Önerilen
Microsoft. Component. tanımlama bilgisi Ecuttertools | Cookiecutter şablonu desteği | 15.0.26621.2 | Önerilen
Microsoft. Component. PythonTools | Python dil desteği | 15.0.26823.1 | Önerilen
Microsoft. Component. PythonTools. Web | Python web desteği | 15.9.28107.0 | Önerilen
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | Önerilen
Microsoft. VisualStudio. Component. FSharp. Desktop | F # masaüstü dil desteği | 15.8.27825.0 | Önerilen
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Önerilen
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Önerilen
Microsoft. VisualStudio. Component. R. Open | Microsoft R Client (3.3.2) | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. RHost | R geliştirme araçları için çalışma zamanı desteği | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. Component. RTools | R dil desteği | 15.0.26919.1 | Önerilen
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Önerilen
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Önerilen
Component. Anaconda2. x64 | Anaconda2 64-bit (5.2.0) | 5.2.0 | İsteğe Bağlı
Component. Anaconda2. x86 | Anaconda2 32-bit (5.2.0) | 5.2.0 | İsteğe Bağlı
Component. Anaconda3. x86 | Anaconda3 32-bit (5.2.0) | 5.2.0 | İsteğe Bağlı
Microsoft. Component. VC. Runtime. UıCRTSDK | Windows Evrensel CRT SDK | 15.6.27309.0 | İsteğe Bağlı
Microsoft. ComponentGroup. PythonTools. NativeDevelopment | Python yerel geliştirme araçları | 15.9.28307.102 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics. Tools | DirectX için grafik hata ayıklayıcı ve GPU Profiler | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics. Win81 | Grafik araçları Windows 8.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. 140 | Masaüstü için VC + + 2015,3 v 14.00 (v140) araç takımı | 15.7.27617.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Coreıde | Visual Studio C++ temel özellikleri | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. DiagnosticTools | C++ profil oluşturma araçları | 15.0.26823.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 sürüm 15,9 v 14.16 en son v141 araçları | 15.9.28230.55 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK | Windows Universal C çalışma zamanı | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | İsteğe Bağlı

## <a name="net-desktop-development"></a>.NET masaüstü geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. ManagedDesktop

**Açıklama:** C#, Visual Basic ve F # kullanarak WPF, Windows Forms ve konsol uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Önkoşullar | .NET masaüstü geliştirme araçları | 15.7.27625.0 | Gerekli
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Gerekli
Microsoft. ComponentGroup. Blend | Visual Studio için Blend | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.5.1. TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.6. TargetingPack | .NET Framework 4,6 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. ComponentGroup. TargetingPacks. Common | .NET Framework 4 – 4,6 geliştirme araçları | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. Debugger. Adaıntime | Tam zamanında hata ayıklayıcı | 15.0.27005.2 | Önerilen
Microsoft. VisualStudio. Component. EntityFramework | Entity Framework 6 araçları | 15.6.27406.0 | Önerilen
Component. Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | İsteğe Bağlı
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 15.0.26720.2 | İsteğe Bağlı
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 15.8.27705.0 | İsteğe Bağlı
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | İsteğe Bağlı
Microsoft. net. Component. 4.6.2. SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.6.2. TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7.1. SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.1. TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7.2. SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 15.8.27825.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7. SDK | .NET Framework 4,7 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7. TargetingPack | .NET Framework 4,7 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.6.2. DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.1. DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.2. DeveloperTools | .NET Framework 4.7.2 geliştirme araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7. DeveloperTools | .NET Framework 4,7 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK | .NET Core 2,0 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK. 1x | .NET Core 1,0-1,1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | İsteğe Bağlı
Microsoft. NetCore. ComponentGroup. DevelopmentTools | .NET Core 2,0 geliştirme araçları | 15.8.27729.1 | İsteğe Bağlı
Microsoft. NetCore. ComponentGroup. DevelopmentTools. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | İsteğe Bağlı
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 15.8.27906.1 | İsteğe Bağlı
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Kapsayıcı geliştirme araçları-derleme araçları | 15.7.27617.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. FSharp | F # dil desteği | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. FSharp. Desktop | F # masaüstü dil desteği | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | İsteğe Bağlı
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server komut satırı yardımcı programları | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. DataSources | SQL Server destek için veri kaynakları | 15.0.26621.2 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. NCLI | SQL Server Native Client | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 15.9.28107.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | İsteğe Bağlı
Microsoft. VisualStudio. Component. WCF. Tooling | Windows Communication Foundation | 15.8.27924.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Web | ASP.NET ve Web geliştirme araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve Web geliştirme araçları önkoşulları | 15.9.28219.51 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | İsteğe Bağlı

## <a name="game-development-with-unity"></a>Unity ile oyun geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. ManagedGame

**Açıklama:** Güçlü platformlar arası bir geliştirme ortamı olan Unity ile 2B ve 3B Oyunlar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Net. Component. 3.5. DeveloperTools | .NET Framework 3,5 geliştirme araçları | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.7.1. TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. Unity | Unity için Visual Studio Araçları | 15.7.27617.1 | Gerekli
Component. UnityEngine. x64 | Unity 2018,3 64-bit düzenleyici | 15.9.28307.271 | Önerilen
Component. UnityEngine. x86 | Unity 5,6 32-bit düzenleyici | 15.6.27406.0 | Önerilen

## <a name="linux-development-with-c"></a>C++ ile Linux geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. NativeCrossPlat

**Açıklama:** Linux ortamında çalışan uygulamalar oluşturun ve hatalarını ayıklayın.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. MDD. Linux | Linux'ta Geliştirme için Visual C++ | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. VC. Coreıde | Visual Studio C++ temel özellikleri | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. Windows10SDK | Windows Universal C çalışma zamanı | 15.6.27406.0 | Gerekli
Component. Linux. CMake | CMake ve Linux için Visual C++ araçları | 15.9.28307.102 | Önerilen
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 sürüm 15,9 v 14.16 en son v141 araçları | 15.9.28230.55 | Önerilen
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Önerilen
Component. MDD. Linux. GCC. ARM | Katıştırılmış ve IoT geliştirme | 15.6.27309.0 | İsteğe Bağlı

## <a name="desktop-development-with-c"></a>C++ ile masaüstü geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. NativeDesktop

**Açıklama:** Microsoft C++ araç takımı, ATL veya MFC kullanarak Windows Masaüstü uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. VC. Coreıde | Visual Studio C++ temel özellikleri | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. VC. Redist. 14. Latest | Visual C++ 2017 yeniden dağıtılabilir güncelleştirmesi | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. ComponentGroup. NativeDesktop. Core | Visual C++ çekirdek masaüstü özellikleri | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. Debugger. Adaıntime | Tam zamanında hata ayıklayıcı | 15.0.27005.2 | Önerilen
Microsoft. VisualStudio. Component. Graphics. Tools | DirectX için grafik hata ayıklayıcı ve GPU Profiler | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. Graphics. Win81 | Grafik araçları Windows 8.1 SDK | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Önerilen
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. VC. ATL | X86 ve x64 için Visual C++ ATL | 15.7.27625.0 | Önerilen
Microsoft. VisualStudio. Component. VC. CMake. Project | CMake için Visual C++ araçları | 15.9.28307.102 | Önerilen
Microsoft. VisualStudio. Component. VC. DiagnosticTools | C++ profil oluşturma araçları | 15.0.26823.1 | Önerilen
Microsoft. VisualStudio. Component. VC. TestAdapterForBoostTest | Boost. test için test bağdaştırıcısı | 15.8.27906.1 | Önerilen
Microsoft. VisualStudio. Component. VC. TestAdapterForGoogleTest | Google Test için Test Bağdaştırıcısı | 15.8.27906.1 | Önerilen
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 sürüm 15,9 v 14.16 en son v141 araçları | 15.9.28230.55 | Önerilen
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Önerilen
Component. IncrediBuild | IncrediBuild-derleme hızlandırma | 15.7.27617.1 | İsteğe Bağlı
Component. IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | İsteğe Bağlı
Microsoft. Component. VC. Runtime. UıCRTSDK | Windows Evrensel CRT SDK | 15.6.27309.0 | İsteğe Bağlı
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. 140 | Masaüstü için VC + + 2015,3 v 14.00 (v140) araç takımı | 15.7.27617.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. ATLMFC | X86 ve x64 için Visual C++ MFC | 15.7.27625.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. CLı. support | C++/CLı desteği | 15.6.27309.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Modules. x86. x64 | Standart kitaplık modülleri (deneysel) | 15.6.27309.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 15063. Desktop | Masaüstü C++ [x86 ve x64] için Windows 10 SDK (10.0.15063.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP | UWP için Windows 10 SDK (10.0.15063.0): C#, VB, JS | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP. Native | UWP için Windows 10 SDK (10.0.15063.0): C++ | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. Desktop | Masaüstü C++ [x86 ve x64] için Windows 10 SDK (10.0.16299.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. Desktop. ARM | Masaüstü C++ [ARM ve ARM64] için Windows 10 SDK (10.0.16299.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. UWP | UWP için Windows 10 SDK (10.0.16299.0): C#, VB, JS | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. UWP. Native | UWP için Windows 10 SDK (10.0.16299.0): C++ | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. WinXP | C++ için Windows XP desteği | 15.8.27924.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. NativeDesktop. Win81 | Windows 8.1 SDK ve UCRT SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. NativeDesktop. WinXP | C++ için Windows XP desteği | 15.8.27705.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Windows10SDK. 15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | İsteğe Bağlı

## <a name="game-development-with-c"></a>C++ ile oyun geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. NativeGame

**Açıklama:** DirectX, Unreal veya Cocos2d tarafından desteklenen profesyonel oyunlar oluşturmak için C++ ' ın tam gücünü kullanın.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. VC. Coreıde | Visual Studio C++ temel özellikleri | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. VC. Redist. 14. Latest | Visual C++ 2017 yeniden dağıtılabilir güncelleştirmesi | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 sürüm 15,9 v 14.16 en son v141 araçları | 15.9.28230.55 | Gerekli
Microsoft. VisualStudio. Component. Windows10SDK | Windows Universal C çalışma zamanı | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. Graphics. Tools | DirectX için grafik hata ayıklayıcı ve GPU Profiler | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. Graphics. Win81 | Grafik araçları Windows 8.1 SDK | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. VC. DiagnosticTools | C++ profil oluşturma araçları | 15.0.26823.1 | Önerilen
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Önerilen
Component. Android. NDK. R12B | Android NDK (R12B) | 12.1.10 | İsteğe Bağlı
Component. Android. SDK23. Private | Android SDK kurulumu (API düzeyi 23) (JavaScript/C++ ile mobil geliştirme için yerel yükleme) | 15.9.28016.0 | İsteğe Bağlı
Component. ant | Apache Ant (1.9.3) | 1.9.3.8 | İsteğe Bağlı
Bileşen. Cocos | Cocos | 15.0.26906.1 | İsteğe Bağlı
Component. IncrediBuild | IncrediBuild-derleme hızlandırma | 15.7.27617.1 | İsteğe Bağlı
Component. IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | İsteğe Bağlı
Component. MDD. Android | C++ Android geliştirme araçları | 15.0.26606.0 | İsteğe Bağlı
Component. OpenJDK | Microsoft dağıtımı OpenJDK | 15.9.28125.51 | İsteğe Bağlı
Component. Unreal | Unreal Engine yükleyicisi | 15.8.27729.1 | İsteğe Bağlı
Component. Unreal. Android | Unreal Engine için Visual Studio Android desteği | 15.9.28307.341 | İsteğe Bağlı
Microsoft. Component. VC. Runtime. UıCRTSDK | Windows Evrensel CRT SDK | 15.6.27309.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.5.1. TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.6. TargetingPack | .NET Framework 4,6 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. TargetingPacks. Common | .NET Framework 4 – 4,6 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. NuGet. BuildTools | NuGet hedefleri ve derleme görevleri | 15.9.28016.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 15063. Desktop | Masaüstü C++ [x86 ve x64] için Windows 10 SDK (10.0.15063.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP | UWP için Windows 10 SDK (10.0.15063.0): C#, VB, JS | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP. Native | UWP için Windows 10 SDK (10.0.15063.0): C++ | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. Desktop | Masaüstü C++ [x86 ve x64] için Windows 10 SDK (10.0.16299.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. Desktop. ARM | Masaüstü C++ [ARM ve ARM64] için Windows 10 SDK (10.0.16299.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. UWP | UWP için Windows 10 SDK (10.0.16299.0): C#, VB, JS | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. UWP. Native | UWP için Windows 10 SDK (10.0.16299.0): C++ | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. NativeDesktop. Win81 | Windows 8.1 SDK ve UCRT SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Windows10SDK. 15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | İsteğe Bağlı

## <a name="mobile-development-with-c"></a>C++ ile mobil geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. NativeMobile

**Açıklama:** C++ kullanarak iOS, Android veya Windows için platformlar arası uygulamalar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Android. SDK19. Private | Android SDK kurulumu (API Düzey 19) (JavaScript/C++ ile mobil geliştirme için yerel yükleme) | 15.9.28107.0 | Gerekli
Component. Android. SDK21. Private | Android SDK kurulumu (API Düzey 21) (JavaScript/C++ ile mobil geliştirme için yerel yükleme) | 15.9.28016.0 | Gerekli
Component. Android. SDK22. Private | Android SDK kurulumu (API düzeyi 22) (JavaScript/C++ ile mobil geliştirme için yerel yükleme) | 15.9.28016.0 | Gerekli
Component. Android. SDK23. Private | Android SDK kurulumu (API düzeyi 23) (JavaScript/C++ ile mobil geliştirme için yerel yükleme) | 15.9.28016.0 | Gerekli
Component. Android. SDK25. Private | Android SDK kurulumu (API düzeyi 25) (JavaScript/C++ ile mobil geliştirme için yerel yükleme) | 15.9.28016.0 | Gerekli
Component. OpenJDK | Microsoft dağıtımı OpenJDK | 15.9.28125.51 | Gerekli
Microsoft. VisualStudio. Component. VC. Coreıde | Visual Studio C++ temel özellikleri | 15.6.27406.0 | Gerekli
Component. Android. NDK. R15C | Android NDK (R15C) | 15.2.1 | Önerilen
Component. ant | Apache Ant (1.9.3) | 1.9.3.8 | Önerilen
Component. MDD. Android | C++ Android geliştirme araçları | 15.0.26606.0 | Önerilen
Component. Android. NDK. R12B | Android NDK (R12B) | 12.1.10 | İsteğe Bağlı
Component. Android. NDK. R12B_3264 | Android NDK (R12B) (32 bit) | 12.1.11 | İsteğe Bağlı
Component. Android. NDK. R13B | Android NDK (R13B) | 13.1.7 | İsteğe Bağlı
Component. Android. NDK. R13B_3264 | Android NDK (R13B) (32 bit) | 13.1.8 | İsteğe Bağlı
Component. Android. NDK. R15C_3264 | Android NDK (R15C) (32 bit) | 15.2.1 | İsteğe Bağlı
Component. Google. Android. öykünücü. API23. Private | Google Android Emulator (API düzeyi 23) (yerel yüklemesi) | 15.6.27413.0 | İsteğe Bağlı
Component. HAXM. Private | Intel Hardware Accelerated Execution Manager (HAXM) (yerel yüklemesi) | 15.9.28307.421 | İsteğe Bağlı
Component. IncrediBuild | IncrediBuild-derleme hızlandırma | 15.7.27617.1 | İsteğe Bağlı
Component. IncredibuildMenu | IncrediBuildMenu | 1.5.0.2 | İsteğe Bağlı
Component. MDD. IOS | C++ iOS geliştirme araçları | 15.0.26621.2 | İsteğe Bağlı

## <a name="net-core-cross-platform-development"></a>.NET Core platformlar arası geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. NetCoreTools

**Açıklama:** .NET Core, ASP.NET Core, HTML/JavaScript ve Docker desteği dahil kapsayıcılar kullanarak platformlar arası uygulamalar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 15.0.26720.2 | Gerekli
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 15.8.27705.0 | Gerekli
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | Gerekli
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. net. Core. Component. SDK. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. NetCore. ComponentGroup. DevelopmentTools. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. NetCore. ComponentGroup. Web. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 15.8.27906.1 | Gerekli
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Kapsayıcı geliştirme araçları-derleme araçları | 15.7.27617.1 | Gerekli
Microsoft. VisualStudio. Component. FSharp | F # dil desteği | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. FSharp. WebTemplates | Web projeleri için F # dil desteği | 15.9.28307.421 | Gerekli
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server komut satırı yardımcı programları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. DataSources | SQL Server destek için veri kaynakları | 15.0.26621.2 | Gerekli
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Gerekli
Microsoft. VisualStudio. Component. SQL. NCLI | SQL Server Native Client | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 15.9.28107.0 | Gerekli
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Gerekli
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve Web geliştirme araçları önkoşulları | 15.9.28219.51 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Gerekli
Component. Microsoft. VisualStudio. Web. AzureFunctions | Microsoft Azure Web Işleri araçları | 15.7.27617.1 | Önerilen
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 15.8.27825.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Azure yazma araçları | 15.9.28307.421 | Önerilen
Microsoft. VisualStudio. Component. Azure. Clientlıbs | .NET için Azure kitaplıkları | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. COMPUTE. öykünücü | Azure Işlem öykünücüsü | 15.9.28307.421 | Önerilen
Microsoft. VisualStudio. Component. Azure. Storage. öykünücü | Azure Storage Öykünücüsü | 15.9.28125.51 | Önerilen
Microsoft. VisualStudio. Component. CloudExplorer | Cloud Explorer | 15.9.28230.55 | Önerilen
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. Component. Web | ASP.NET ve Web geliştirme araçları | 15.8.27825.0 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. ComponentGroup. AzureFunctions | Microsoft Azure Web Işleri araçları | 15.7.27617.1 | Önerilen
Microsoft. VisualStudio. ComponentGroup. Web. CloudTools | Web geliştirme için bulut araçları | 15.8.27729.1 | Önerilen
Microsoft. net. Core. Component. SDK | .NET Core 2,0 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK. 1x | .NET Core 1,0-1,1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. NetCore. 1x. ComponentGroup. Web | Web için .NET Core 1,0-1,1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. NetCore. ComponentGroup. DevelopmentTools | .NET Core 2,0 geliştirme araçları | 15.8.27729.1 | İsteğe Bağlı
Microsoft. NetCore. ComponentGroup. Web | .NET Core 2,0 geliştirme araçları | 15.7.27625.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. ıısdevelopment | Geliştirme zamanı IIS desteği | 15.9.28219.51 | İsteğe Bağlı

## <a name="mobile-development-with-net"></a>.NET ile mobil geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. NETbir Splat

**Açıklama:** Xamarin kullanarak iOS, Android veya Windows için platformlar arası uygulamalar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Xamarin | Xamarin | 15.8.27906.1 | Gerekli
Component. Xamarin. Remotedsimülatör | Xamarin uzaktan simülatör | 15.6.27323.2 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. net. Core. Component. SDK | .NET Core 2,0 geliştirme araçları | 15.6.27406.0 | Gerekli
Microsoft. NetCore. ComponentGroup. DevelopmentTools | .NET Core 2,0 geliştirme araçları | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. FSharp | F # dil desteği | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. Merq | Ortak Xamarin iç araçları | 15.8.27924.0 | Gerekli
Microsoft. VisualStudio. Component. MonoDebugger | Mono hata ayıklayıcısı | 15.0.26720.2 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions. TemplateEngine | ASP.NET şablon oluşturma altyapısı | 15.8.27729.1 | Gerekli
Component. Android. SDK27 | Android SDK kurulumu (API düzeyi 27) | 15.9.28016.0 | Önerilen
Component. Google. Android. öykünücü. API27 | Google Android Emulator (API düzeyi 27) | 15.9.28307.421 | Önerilen
Component. HAXM | Intel Hardware Accelerated Execution Manager (HAXM) (genel yüklemesi) | 15.9.28307.421 | Önerilen
Component. OpenJDK | Microsoft dağıtımı OpenJDK | 15.9.28125.51 | Önerilen
Component. Xamarin. Inspector | Xamarin Workbooks | 15.0.26606.0 | İsteğe Bağlı
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | İsteğe Bağlı
Microsoft. Component. NetFX. Native | .NET Yerel | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 15.8.27729.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics | Görüntü ve 3B model düzenleyicileri | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. UWP. Xamarin | Xamarin için Evrensel Windows Platformu araçları | 15.9.28307.102 | İsteğe Bağlı

## <a name="aspnet-and-web-development"></a>ASP.NET ve web geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. NetWeb

**Açıklama:** ASP.NET, ASP.NET Core, HTML/JavaScript ve Docker desteği dahil kapsayıcılar kullanarak Web uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 15.0.26720.2 | Gerekli
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 15.8.27705.0 | Gerekli
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | Gerekli
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. net. Core. Component. SDK. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. NetCore. ComponentGroup. DevelopmentTools. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. NetCore. ComponentGroup. Web. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 15.8.27906.1 | Gerekli
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Kapsayıcı geliştirme araçları-derleme araçları | 15.7.27617.1 | Gerekli
Microsoft. VisualStudio. Component. FSharp | F # dil desteği | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. FSharp. WebTemplates | Web projeleri için F # dil desteği | 15.9.28307.421 | Gerekli
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server komut satırı yardımcı programları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. DataSources | SQL Server destek için veri kaynakları | 15.0.26621.2 | Gerekli
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Gerekli
Microsoft. VisualStudio. Component. SQL. NCLI | SQL Server Native Client | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 15.9.28107.0 | Gerekli
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Gerekli
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. Web | ASP.NET ve Web geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve Web geliştirme araçları önkoşulları | 15.9.28219.51 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Gerekli
Component. Microsoft. VisualStudio. Web. AzureFunctions | Microsoft Azure Web Işleri araçları | 15.7.27617.1 | Önerilen
Microsoft.Net. Component. 4.5.1. TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4.6. TargetingPack | .NET Framework 4,6 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 hedefleme paketi | 15.6.27406.0 | Önerilen
Microsoft.Net. ComponentGroup. TargetingPacks. Common | .NET Framework 4 – 4,6 geliştirme araçları | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 15.8.27825.0 | Önerilen
Microsoft. VisualStudio. Component. AspNet45 | Gelişmiş ASP.NET özellikleri | 15.7.27625.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Azure yazma araçları | 15.9.28307.421 | Önerilen
Microsoft. VisualStudio. Component. Azure. Clientlıbs | .NET için Azure kitaplıkları | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. Azure. COMPUTE. öykünücü | Azure Işlem öykünücüsü | 15.9.28307.421 | Önerilen
Microsoft. VisualStudio. Component. Azure. Storage. öykünücü | Azure Storage Öykünücüsü | 15.9.28125.51 | Önerilen
Microsoft. VisualStudio. Component. CloudExplorer | Cloud Explorer | 15.9.28230.55 | Önerilen
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. Component. EntityFramework | Entity Framework 6 araçları | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. WCF. Tooling | Windows Communication Foundation | 15.8.27924.0 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. ComponentGroup. AzureFunctions | Microsoft Azure Web Işleri araçları | 15.7.27617.1 | Önerilen
Microsoft. VisualStudio. ComponentGroup. Web. CloudTools | Web geliştirme için bulut araçları | 15.8.27729.1 | Önerilen
Microsoft. net. Component. 4.6.2. SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.6.2. TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7.1. SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.1. TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7.2. SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 15.8.27825.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7. SDK | .NET Framework 4,7 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7. TargetingPack | .NET Framework 4,7 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.6.2. DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.1. DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.2. DeveloperTools | .NET Framework 4.7.2 geliştirme araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7. DeveloperTools | .NET Framework 4,7 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK | .NET Core 2,0 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK. 1x | .NET Core 1,0-1,1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. NetCore. 1x. ComponentGroup. Web | Web için .NET Core 1,0-1,1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. NetCore. ComponentGroup. DevelopmentTools | .NET Core 2,0 geliştirme araçları | 15.8.27729.1 | İsteğe Bağlı
Microsoft. NetCore. ComponentGroup. Web | .NET Core 2,0 geliştirme araçları | 15.7.27625.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. ıısdevelopment | Geliştirme zamanı IIS desteği | 15.9.28219.51 | İsteğe Bağlı
Microsoft. VisualStudio. Web. Mvc4. ComponentGroup | ASP.NET MVC 4 | 15.6.27406.0 | İsteğe Bağlı

## <a name="nodejs-development"></a>Node.js geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Node

**Açıklama:** Zaman uyumsuz olay temelli bir JavaScript çalışma zamanı olan Node.js kullanarak ölçeklenebilir ağ uygulamaları oluşturun. 

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Gerekli
Microsoft. VisualStudio. Component. Node. Build | MSBuild desteğini Node.js | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. Node. Tools | Node.js geliştirme desteği | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
Microsoft. VisualStudio. Component. TestTools. Core | Test araçları temel özellikleri | 15.7.27520.0 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Coreıde | Visual Studio C++ temel özellikleri | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 sürüm 15,9 v 14.16 en son v141 araçları | 15.9.28230.55 | İsteğe Bağlı

## <a name="officesharepoint-development"></a>Office/SharePoint geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Office

**Açıklama:** C#, VB ve JavaScript kullanarak Office ve SharePoint eklentileri, SharePoint çözümleri ve VSTO eklentileri oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 15.0.26720.2 | Gerekli
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 15.8.27705.0 | Gerekli
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | Gerekli
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. net. Core. Component. SDK. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 15.8.27906.1 | Gerekli
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Kapsayıcı geliştirme araçları-derleme araçları | 15.7.27617.1 | Gerekli
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Önkoşullar | .NET masaüstü geliştirme araçları | 15.7.27625.0 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. SharePoint. Tools | Visual Studio için Office Geliştirici Araçları | 15.8.27924.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server komut satırı yardımcı programları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. DataSources | SQL Server destek için veri kaynakları | 15.0.26621.2 | Gerekli
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Gerekli
Microsoft. VisualStudio. Component. SQL. NCLI | SQL Server Native Client | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 15.9.28107.0 | Gerekli
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Gerekli
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. WCF. Tooling | Windows Communication Foundation | 15.8.27924.0 | Gerekli
Microsoft. VisualStudio. Component. Web | ASP.NET ve Web geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. Workflow | Windows Workflow Foundation | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve Web geliştirme araçları önkoşulları | 15.9.28219.51 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. TeamOffice | Office için Visual Studio Araçları (VSTO) | 15.7.27625.0 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 15.8.27729.1 | Önerilen
Microsoft. net. Component. 4.6.2. SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.6.2. TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7.1. SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.1. TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7.2. SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 15.8.27825.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7. SDK | .NET Framework 4,7 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.7. TargetingPack | .NET Framework 4,7 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.6.2. DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.1. DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.2. DeveloperTools | .NET Framework 4.7.2 geliştirme araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7. DeveloperTools | .NET Framework 4,7 geliştirme araçları | 15.6.27406.0 | İsteğe Bağlı

## <a name="python-development"></a>Python geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Python

**Açıklama:** Python için düzen, hata ayıklama, etkileşimli geliştirme ve kaynak denetimi.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. Component. PythonTools | Python dil desteği | 15.0.26823.1 | Gerekli
Component. CPython3. x64 | Python 3 64-bit (3.6.6) | 3.6.6 | Önerilen
Microsoft. Component. tanımlama bilgisi Ecuttertools | Cookiecutter şablonu desteği | 15.0.26621.2 | Önerilen
Microsoft. Component. PythonTools. Web | Python web desteği | 15.9.28107.0 | Önerilen
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | Önerilen
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Önerilen
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Önerilen
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Önerilen
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Önerilen
Component. Anaconda2. x64 | Anaconda2 64-bit (5.2.0) | 5.2.0 | İsteğe Bağlı
Component. Anaconda2. x86 | Anaconda2 32-bit (5.2.0) | 5.2.0 | İsteğe Bağlı
Component. Anaconda3. x64 | Anaconda3 64-bit (5.2.0) | 5.2.0 | İsteğe Bağlı
Component. Anaconda3. x86 | Anaconda3 32-bit (5.2.0) | 5.2.0 | İsteğe Bağlı
Component. CPython2. x64 | Python 2 64-bit (2.7.14) | 2.7.14 | İsteğe Bağlı
Component. CPython2. x86 | Python 2 32-bit (2.7.14) | 2.7.14 | İsteğe Bağlı
Component. CPython3. x86 | Python 3 32-bit (3.6.6) | 3.6.6 | İsteğe Bağlı
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 15.0.26720.2 | İsteğe Bağlı
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 15.8.27705.0 | İsteğe Bağlı
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | İsteğe Bağlı
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | İsteğe Bağlı
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | İsteğe Bağlı
Microsoft. Component. NetFX. Native | .NET Yerel | 15.0.26208.0 | İsteğe Bağlı
Microsoft. Component. PythonTools. UWP | Python IoT desteği | 15.0.26606.0 | İsteğe Bağlı
Microsoft. Component. VC. Runtime. UıCRTSDK | Windows Evrensel CRT SDK | 15.6.27309.0 | İsteğe Bağlı
Microsoft. ComponentGroup. PythonTools. NativeDevelopment | Python yerel geliştirme araçları | 15.9.28307.102 | İsteğe Bağlı
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Azure yazma araçları | 15.9.28307.421 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. Clientlıbs | .NET için Azure kitaplıkları | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. COMPUTE. öykünücü | Azure Işlem öykünücüsü | 15.9.28307.421 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. Storage. öykünücü | Azure Storage Öykünücüsü | 15.9.28125.51 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. Waverton | Azure Cloud Services çekirdek araçları | 15.9.28107.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. Waverton. BuildTools | Azure Cloud Services derleme araçları | 15.7.27617.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. ClassDesigner | Sınıf Tasarımcısı | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 15.8.27729.1 | İsteğe Bağlı
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 15.8.27906.1 | İsteğe Bağlı
Microsoft.VisualStudio.Component.DockerTools. BuildTools | Kapsayıcı geliştirme araçları-derleme araçları | 15.7.27617.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics | Görüntü ve 3B model düzenleyicileri | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics. Tools | DirectX için grafik hata ayıklayıcı ve GPU Profiler | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics. Win81 | Grafik araçları Windows 8.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 15.8.27729.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. CMDUtils | SQL Server komut satırı yardımcı programları | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. DataSources | SQL Server destek için veri kaynakları | 15.0.26621.2 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. NCLI | SQL Server Native Client | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 15.9.28107.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. 140 | Masaüstü için VC + + 2015,3 v 14.00 (v140) araç takımı | 15.7.27617.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Coreıde | Visual Studio C++ temel özellikleri | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. DiagnosticTools | C++ profil oluşturma araçları | 15.0.26823.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 sürüm 15,9 v 14.16 en son v141 araçları | 15.9.28230.55 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Web | ASP.NET ve Web geliştirme araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK | Windows Universal C çalışma zamanı | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve Web geliştirme araçları önkoşulları | 15.9.28219.51 | İsteğe Bağlı

## <a name="universal-windows-platform-development"></a>Evrensel Windows Platformu geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Universal

**Açıklama:** C#, VB, JavaScript veya isteğe bağlı olarak C++ ile Evrensel Windows Platformu uygulamalar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | Gerekli
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | Gerekli
Microsoft. Component. NetFX. Native | .NET Yerel | 15.0.26208.0 | Gerekli
Microsoft. ComponentGroup. Blend | Visual Studio için Blend | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft. net. Core. Component. SDK. 2.1 | .NET Core 2,1 geliştirme araçları | 15.8.27924.0 | Gerekli
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. Graphics | Görüntü ve 3B model düzenleyicileri | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Gerekli
Microsoft. VisualStudio. Component. UWP. support | Evrensel Windows Platformu araçları | 15.9.28119.51 | Gerekli
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | Gerekli
Microsoft. VisualStudio. ComponentGroup. UWP. Cordova | Cordova için Evrensel Windows Platformu araçları | 15.9.28307.102 | Gerekli
Microsoft. VisualStudio. ComponentGroup. UWP. NetCoreAndStandard | .NET Native ve .NET Standard | 15.8.27906.1 | Gerekli
Microsoft. VisualStudio. ComponentGroup. UWP. Xamarin | Xamarin için Evrensel Windows Platformu araçları | 15.9.28307.102 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Gerekli
Microsoft. Component. VC. Runtime. OSSupport | UWP için Visual C++ çalışma zamanı | 15.6.27406.0 | İsteğe Bağlı
Microsoft. net. Component. 4.7.2. SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics. Tools | DirectX için grafik hata ayıklayıcı ve GPU Profiler | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics. Win81 | Grafik araçları Windows 8.1 SDK | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Phone. öykünücü. 15254 | Windows 10 Mobile öykünücüsü (Fall Creators Update) | 15.0.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. UWP. VC. ARM64 | ARM64 için C++ Evrensel Windows Platformu araçları | 15.0.28125.51 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Coreıde | Visual Studio C++ temel özellikleri | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. ARM | ARM için Visual C++ derleyiciler ve kitaplıklar | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. ARM64 | ARM64 için derleyiciler ve kitaplıklar Visual C++ | 15.9.28230.55 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 sürüm 15,9 v 14.16 en son v141 araçları | 15.9.28230.55 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 15063. Desktop | Masaüstü C++ [x86 ve x64] için Windows 10 SDK (10.0.15063.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP | UWP için Windows 10 SDK (10.0.15063.0): C#, VB, JS | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 15063. UWP. Native | UWP için Windows 10 SDK (10.0.15063.0): C++ | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. Desktop | Masaüstü C++ [x86 ve x64] için Windows 10 SDK (10.0.16299.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. Desktop. ARM | Masaüstü C++ [ARM ve ARM64] için Windows 10 SDK (10.0.16299.0) | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. UWP | UWP için Windows 10 SDK (10.0.16299.0): C#, VB, JS | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299. UWP. Native | UWP için Windows 10 SDK (10.0.16299.0): C++ | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 15.9.28307.102 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. ıpoıb Verusb | USB cihaz bağlantısı | 15.9.28307.102 | İsteğe Bağlı
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ Evrensel Windows Platformu araçları | 15.9.28307.102 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Windows10SDK. 15063 | Windows 10 SDK (10.0.15063.0) | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 15.8.27825.0 | İsteğe Bağlı

## <a name="visual-studio-extension-development"></a>Visual Studio uzantısı geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. VisualStudioExtension

**Açıklama:** Visual Studio için yeni komutlar, kod Çözümleyicileri ve araç pencereleri dahil eklentiler ve uzantılar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6. TargetingPack | .NET Framework 4,6 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
Microsoft. VisualStudio. Component. PortableLibrary | .NET taşınabilir kitaplık hedefleme paketi | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. static. Analysis. Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft. VisualStudio. Component. VSSDK | Visual Studio SDK | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. ComponentGroup. VisualStudioExtension. Önkoşullar | Visual Studio uzantısı geliştirme önkoşulları | 15.7.27625.0 | Gerekli
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 15.8.27729.1 | Önerilen
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 15.0.26208.0 | Önerilen
Component. Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | İsteğe Bağlı
Microsoft. Component. CodeAnalysis. SDK | .NET Compiler Platform SDK’sı | 15.0.27729.1 | İsteğe Bağlı
Microsoft. Component. VC. Runtime. OSSupport | UWP için Visual C++ çalışma zamanı | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. ClassDesigner | Sınıf Tasarımcısı | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. DslTools | Modelleme SDK 'Sı | 15.0.27005.2 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. ATL | X86 ve x64 için Visual C++ ATL | 15.7.27625.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. ATLMFC | X86 ve x64 için Visual C++ MFC | 15.7.27625.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Coreıde | Visual Studio C++ temel özellikleri | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | VC + + 2017 sürüm 15,9 v 14.16 en son v141 araçları | 15.9.28230.55 | İsteğe Bağlı

## <a name="mobile-development-with-javascript"></a>JavaScript ile mobil geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Webbir Splat

**Açıklama:** Apache Cordova için Araçlar kullanarak Android, iOS ve UWP uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Cordovaaraç takımı. 6.3.1 | Cordova 6.3.1 araç takımı | 15.7.27625.0 | Gerekli
Component. WebSocket | WebSocket4Net | 15.0.26606.0 | Gerekli
Microsoft. VisualStudio. Component. Cordova | JavaScript temel özellikleriyle mobil geliştirme | 15.0.26606.0 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. ProjectSystem | JavaScript ProjectSystem ve Shared Tooling | 15.0.26606.0 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 15.9.28125.51 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 2.3 | TypeScript 2,3 SDK | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 3.1 | TypeScript 3,1 SDK | 15.0.28218.60 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 15.8.27825.0 | Gerekli
Component. Android. SDK23. Private | Android SDK kurulumu (API düzeyi 23) (JavaScript/C++ ile mobil geliştirme için yerel yükleme) | 15.9.28016.0 | İsteğe Bağlı
Component. Google. Android. öykünücü. API23. Private | Google Android Emulator (API düzeyi 23) (yerel yüklemesi) | 15.6.27413.0 | İsteğe Bağlı
Component. HAXM. Private | Intel Hardware Accelerated Execution Manager (HAXM) (yerel yüklemesi) | 15.9.28307.421 | İsteğe Bağlı
Component. OpenJDK | Microsoft dağıtımı OpenJDK | 15.9.28125.51 | İsteğe Bağlı
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | İsteğe Bağlı
Microsoft. Component. NetFX. Native | .NET Yerel | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 15.8.27825.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 15.8.27729.1 | İsteğe Bağlı
Microsoft. VisualStudio. Component. git | Windows için Git | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics | Görüntü ve 3B model düzenleyicileri | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Phone. öykünücü. 15254 | Windows 10 Mobile öykünücüsü (Fall Creators Update) | 15.0.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 15.9.28307.102 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. UWP. Cordova | Cordova için Evrensel Windows Platformu araçları | 15.9.28307.102 | İsteğe Bağlı

## <a name="unaffiliated-components"></a>Bağlantılı olmayan bileşenler

Bunlar herhangi bir iş yüküne dahil olmayan, ancak tek bir bileşen olarak seçilebilir olan bileşenlerdir.

Bileşen KIMLIĞI | Name | Sürüm
--- | --- | ---
Component. Android. öykünücü | Android için Visual Studio Öykünücüsü | 15.6.27413.0
Component. Android. NDK. R11C | Android NDK (R11C) | 11.3.14
Component. Android. NDK. R11C_3264 | Android NDK (R11C) (32 bit) | 11.3.16
Component. Android. SDK23 | Android SDK kurulumu (API düzeyi 23) (Genel yükleme) | 15.9.28107.0
Component. Android. SDK25 | Android SDK kurulumu (API düzeyi 25) | 15.9.28107.0
Component. GitHub. VisualStudio | Visual Studio için GitHub Uzantısı | 2.5.2.2500
Component. Google. Android. öykünücü. API23. v2 | Google Android Emulator (API düzeyi 23) (genel yüklemesi) | 15.6.27413.0
Component. Google. Android. öykünücü. API25 | Google Android Emulator (API düzeyi 25) | 15.7.27604.0
Microsoft. Component. Blend. SDK. WPF | .NET için Visual Studio için Blend SDK | 15.6.27406.0
Microsoft. Component. HelpViewer | Yardım Görüntüleyicisi | 15.9.28307.421
Microsoft. VisualStudio. Component. DependencyValidation. Community | Bağımlılık doğrulaması | 15.0.26208.0
Microsoft. VisualStudio. Component. GraphDocument | DGML Düzenleyicisi | 15.0.27005.2
Microsoft. VisualStudio. Component. LinqToSql | LINQ to SQL araçları | 15.6.27406.0
Microsoft. VisualStudio. Component. Phone. öykünücü | Windows 10 Mobile öykünücüsü (yıldönümü sürümü) | 15.6.27406.0
Microsoft. VisualStudio. Component. Phone. öykünücü. 15063 | Windows 10 Mobile öykünücüsü (Creators Update) | 15.6.27406.0
Microsoft. VisualStudio. Component. Runtime. Node. x 86.6.4.0 | Node.js v 6.4.0 (x86) tabanlı bileşenler için çalışma zamanı | 15.7.27617.1
Microsoft. VisualStudio. Component. Runtime. Node. x 86.7.4.0 | Node.js v 7.4.0 (x86) tabanlı bileşenler için çalışma zamanı | 15.7.27617.1
Microsoft. VisualStudio. Component. TypeScript. 2.0 | TypeScript 2,0 SDK | 15.8.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.1 | TypeScript 2,1 SDK | 15.8.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.2 | TypeScript 2,2 SDK | 15.8.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.5 | TypeScript 2,5 SDK | 15.6.27406.0
Microsoft. VisualStudio. Component. TypeScript. 2.6 | TypeScript 2,6 SDK | 15.0.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.7 | TypeScript 2,7 SDK | 15.0.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.8 | TypeScript 2,8 SDK | 15.0.27729.1
Microsoft. VisualStudio. Component. TypeScript. 2.9 | TypeScript 2,9 SDK | 15.0.27924.0
Microsoft. VisualStudio. Component. TypeScript. 3.0 | TypeScript 3,0 SDK | 15.0.27924.0
Microsoft. VisualStudio. Component. VC. ATL. ARM | ARM için Visual C++ ATL | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. ATL. ARM. Spectre | Spectre azaltmaları ile ARM için ATL Visual C++ | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. ATL. ARM64 | ARM64 için ATL Visual C++ | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. ATL. ARM64. Spectre | Spectre azaltmaları ile ARM64 için ATL Visual C++ | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. ATL. Spectre | Spectre azaltmaları ile ATL (x86/x64) Visual C++ | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. ATLMFC. Spectre | Spectre azaltmaları ile x86/x64 için Visual C++ MFC | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. ClangC2 | Clang/C2 (deneysel) | 15.7.27520.0
Microsoft. VisualStudio. Component. VC. MFC. ARM | ARM için MFC Visual C++ | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. MFC. ARM. Spectre | Spectre azaltmaları ile ARM için MFC Visual C++ | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. MFC. ARM64 | ARM64 için MFC Visual C++ | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. MFC. ARM64. Spectre | Spectre azaltmaları ile ARM64 için MFC desteği Visual C++ | 15.7.27625.0
Microsoft. VisualStudio. Component. VC. çalışma zamanları. ARM. Spectre | VC + + 2017 sürüm 15,9 v 14.16 libs for Spectre (ARM) | 15.9.28230.55
Microsoft. VisualStudio. Component. VC. çalışma zamanları. ARM64. Spectre | VC + + 2017 sürüm 15,9 v 14.16 libs for Spectre (ARM64) | 15.9.28230.55
Microsoft. VisualStudio. Component. VC. çalışma zamanları. x86. x64. Spectre | VC + + 2017 sürüm 15,9 v 14.16 libs for Spectre (x86 ve x64) | 15.9.28230.55
Microsoft. VisualStudio. Component. VC. Tools. 14.11 | VC + + 2017 sürüm 15,4 v 14.11 araç takımı | 15.0.27924.0
Microsoft. VisualStudio. Component. VC. Tools. 14.12 | VC + + 2017 sürüm 15,5 v 14.12 araç takımı | 15.0.27924.0
Microsoft. VisualStudio. Component. VC. Tools. 14.13 | VC + + 2017 sürüm 15,6 v 14.13 araç takımı | 15.0.27924.0
Microsoft. VisualStudio. Component. VC. Tools. 14.14 | VC + + 2017 sürüm 15,7 v 14.14 araç takımı | 15.0.27924.0
Microsoft. VisualStudio. Component. VC. Tools. 14.15 Spectre | VC + + 2017 sürüm 15,8 v 14.15 Spectre araç takımı | 15.0.28230.55
