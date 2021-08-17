---
title: Visual Studio Enterprise 2019 iş yükü ve bileşen kimlikleri
titleSuffix: ''
description: komut satırını kullanarak veya bir vsıx bildiriminde bağımlılık olarak belirtmek için Visual Studio yüklemek için iş yükü ve bileşen kimliklerini kullanın
keywords: ''
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.date: 08/10/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 2ce98655c9ff3dee97ddb444fd5bb4adafb67c6b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077912"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Visual Studio çekirdek düzenleyicisi (Visual Studio Enterprise 2019 ile birlikte)

**Kimliği:** Microsoft. VisualStudio. Workload. CoreEditor

**Açıklama:** sözdizimi kullanan kod düzenlemesi, kaynak kodu denetimi ve iş öğesi yönetimi de dahil olmak üzere Visual Studio çekirdek kabuğu deneyimi.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. VisualStudio. Component. CoreEditor | Visual Studio core düzenleyicisi | 16.1.28811.260 | Gerekli
Microsoft. VisualStudio. Component. Startpagedenemeler. cpp | Visual Studio C++ kullanıcıları için başlangıç sayfası | 16.0.28315.86 | İsteğe Bağlı

## <a name="azure-development"></a>Azure geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Azure

**Açıklama:** Bulut uygulamaları geliştirmeye ve .NET ve .NET Framework kullanarak kaynak oluşturmaya yönelik Azure SDK 'Ları, araçları ve projeleri. Ayrıca, Docker desteği dahil olmak üzere uygulamanızı kapsayıcıya yönelik araçlar içerir.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 16.10.31205.252 | Gerekli
Component. Microsoft. VisualStudio. Web. AzureFunctions | Azure Web Işleri araçları | 16.10.31205.252 | Gerekli
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 16.10.31205.180 | Gerekli
Component. Microsoft. WebTools. BrowserLink. WebLivePreview | Web canlı önizleme | 0.7.22.39845 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft. ComponentGroup. ClickOnce. Yayınlamanız | ClickOnce .NET için yayımlama  | 16.11.31603.221 | Gerekli
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 16.11.31605.320 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | Gerekli
Microsoft. net. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft. NetCore. Component. DevelopmentTools | .NET geliştirme araçları | 16.10.31303.231 | Gerekli
Microsoft. NetCore. Component. Runtime. 3.1 | .NET Core 3,1 çalışma zamanı (LTS) | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 çalışma zamanı | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. SDK | .NET SDK | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. Web | .NET geliştirme araçları | 16.10.31303.231 | Gerekli
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Azure yazma araçları | 16.0.28625.61 | Gerekli
Microsoft. VisualStudio. Component. Azure. Clientlıbs | .NET için Azure kitaplıkları | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.Azure.Compute. Emulator | Azure İşlem Emulator | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.Component.Azure. Depolama. Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | Gerekli
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.FSharp | F# dil desteği | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web projeleri için F# dili desteği | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılaması | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | Gerekli
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Yönetilen Masaüstü İş Yükü Çekirdeği | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.Component.MSODBC. SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | Gerekli
Microsoft.VisualStudio.Component. NuGet | NuGet paketi yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.Component. SQL. ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component. SQL. Clr | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component. SQL. Datasources | Veri kaynağı desteği SQL Server kaynakları | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component. SQL. LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component. SQL. Ssdt | SQL Server Veri Araçları | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüşümü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.TypeScript.4.3 | TypeScript 4.3 SDK | 16.0.31506.151 | Gerekli
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Azure geliştirme önkoşulları | 16.10.31303.231 | Gerekli
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure Web İşleri Araçları | 16.10.31205.180 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları önkoşulları | 16.10.31205.180 | Gerekli
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Gerekli
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake ve Stream Analytics Araçları | 16.10.31205.252 | Önerilen
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 geliştirme araçları | 16.0.28516.191 | Önerilen
Microsoft.VisualStudio.Component.AspNet45 | Gelişmiş ASP.NET özellikleri | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Kubernetes için Visual Studio Araçları | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.Azure.Powershell | Azure PowerShell | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager temel araçlar | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric Araçları | 16.4.29313.120 | Önerilen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services temel araçlar | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services araçları oluşturma | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Anlık Görüntü Hata Ayıklayıcı | 16.5.29813.82 | Önerilen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Zaman Yolculuğu Hata Ayıklayıcısı | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services araçları | 16.10.31205.180 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager araçları | 16.0.28528.71 | Önerilen
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 hedefleme paketi | 16.4.29313.120 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 geliştirme araçları | 16.4.29318.151 | İsteğe Bağlı
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 Çalışma Zamanı (LTS) | 16.11.31603.221 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Azure. Depolama. AzCopy | Azure Depolama AzCopy | 16.0.28517.75 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | İsteğe Bağlı

## <a name="data-storage-and-processing"></a>Veri depolama ve işleme

**Kimlik:** Microsoft.VisualStudio.Workload.Data

**Açıklama:** Bağlan, Azure Data Lake veya Hadoop ile veri SQL Server, geliştirme ve test edin.

### <a name="components-included-by-this-workload"></a>Bu iş yüküne dahil edilen bileşenler

Bileşen Kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Dil Hizmetleri | 16.10.31205.252 | Önerilen
Component.Microsoft.Web.LibraryManager | Kitaplık Yöneticisi | 16.10.31205.180 | Önerilen
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Önerilen
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake ve Stream Analytics Araçları | 16.10.31205.252 | Önerilen
Microsoft.Component. MSBuild | MSBuild | 16.5.29515.121 | Önerilen
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | Önerilen
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Önerilen
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Önerilen
Microsoft.Net. ComponentGroup. TargetingPacks. Common | .NET Framework 4 – 4,6 geliştirme araçları | 16.0.28516.191 | Önerilen
Microsoft. NetCore. Component. Runtime. 3.1 | .NET Core 3,1 çalışma zamanı (LTS) | 16.11.31603.221 | Önerilen
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 çalışma zamanı | 16.11.31603.221 | Önerilen
Microsoft. NetCore. Component. SDK | .NET SDK | 16.11.31603.221 | Önerilen
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Azure yazma araçları | 16.0.28625.61 | Önerilen
Microsoft. VisualStudio. Component. Azure. Clientlıbs | .NET için Azure kitaplıkları | 16.0.28315.86 | Önerilen
Microsoft. VisualStudio. Component. Azure. COMPUTE. Emulator | Azure Işlem Emulator | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. Azure. Depolama. Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | Önerilen
Microsoft. VisualStudio. Component. Azure. Waverton | Azure Cloud Services çekirdek araçları | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. Azure. Waverton. BuildTools | Azure Cloud Services derleme araçları | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. CloudExplorer | Cloud Explorer | 16.0.28625.61 | Önerilen
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Önerilen
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | Önerilen
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | Önerilen
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 16.4.29318.151 | Önerilen
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ODBC sürücüsü | 16.0.28625.61 | Önerilen
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server Komut satırı yardımcı programları | 16.0.28707.177 | Önerilen
Microsoft. VisualStudio. Component. NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic roslyn derleyicileri | 16.0.28714.129 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Önerilen
Microsoft. VisualStudio. Component. SQL. Kaynağı | SQL Server destek için veri kaynakları | 16.0.28315.86 | Önerilen
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 localdb | 16.0.28625.61 | Önerilen
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 16.3.29207.166 | Önerilen
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 16.0.28625.61 | Önerilen
Microsoft. VisualStudio. Component. TypeScript. 4.3 | TypeScript 4,3 SDK | 16.0.31506.151 | Önerilen
Microsoft. VisualStudio. Component. Web | ASP.NET ve web geliştirme araçları | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve web geliştirme araçları önkoşulları | 16.10.31205.180 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Önerilen
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft. VisualStudio. Component. FSharp. Desktop | F # masaüstü dil desteği | 16.0.28315.86 | İsteğe Bağlı

## <a name="data-science-and-analytical-applications"></a>Veri bilimi ve analitik uygulamalar

**Kimliği:** Microsoft. VisualStudio. Workload. DataScience

**Açıklama:** Python ve F # dahil olmak üzere veri bilimi uygulamaları oluşturmak için Diller ve araçlar.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. Component. PythonTools | Python dil desteği | 16.11.31314.313 | Önerilen
Microsoft. Component. PythonTools. Minicondax64 | Python miniconda (destek dışı) | 16.11.31314.313 | Önerilen
Microsoft. Component. PythonTools. Web | Python web desteği | 16.10.31205.252 | Önerilen
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Önerilen
Microsoft. VisualStudio. Component. FSharp. Desktop | F # masaüstü dil desteği | 16.0.28315.86 | Önerilen
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | Önerilen
Microsoft. VisualStudio. Component. NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic roslyn derleyicileri | 16.0.28714.129 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. TypeScript. 4.3 | TypeScript 4,3 SDK | 16.0.31506.151 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Önerilen
Microsoft. ComponentGroup. PythonTools. NativeDevelopment | Python yerel geliştirme araçları | 16.10.31205.180 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics. Tools | DirectX için grafik hata ayıklayıcı ve GPU Profiler | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Coreıde | C++ temel özellikleri | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. DiagnosticTools | C++ profil oluşturma araçları | 16.5.29515.121 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC v142-VS 2019 C++ x64/x86 derleme araçları (en son) | 16.11.31317.239 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK | Windows Evrensel C çalışma zamanı | 16.4.29409.204 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | İsteğe Bağlı

## <a name="net-desktop-development"></a>.NET masaüstü geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. ManagedDesktop

**Açıklama:** .net ve .NET Framework ile C#, Visual Basic ve F # kullanarak WPF, Windows Forms ve konsol uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | Gerekli
Microsoft. net. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft. NetCore. Component. Runtime. 3.1 | .NET Core 3,1 çalışma zamanı (LTS) | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 çalışma zamanı | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. SDK | .NET SDK | 16.11.31603.221 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 16.4.29318.151 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Önkoşullar | .NET masaüstü geliştirme araçları | 16.10.31205.180 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 16.0.28625.61 | Gerekli
Component. Microsoft. VisualStudio. Livespaylaşımı | Live Share | 1.0.4438 | Önerilen
Microsoft. ComponentGroup. Blend | Visual Studio için Blend | 16.0.28315.86 | Önerilen
Microsoft. ComponentGroup. ClickOnce. Yayınlamanız | ClickOnce .NET için yayımlama  | 16.11.31603.221 | Önerilen
Microsoft.Net. Component. 4.5.1. TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net. Component. 4.6. TargetingPack | .NET Framework 4,6 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net. ComponentGroup. TargetingPacks. Common | .NET Framework 4 – 4,6 geliştirme araçları | 16.0.28516.191 | Önerilen
Microsoft. NetCore. Component. DevelopmentTools | .NET geliştirme araçları | 16.10.31303.231 | Önerilen
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Önerilen
Microsoft. VisualStudio. Component. Debugger. Adaıntime | Tam zamanında hata ayıklayıcı | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. DotNetModelBuilder | ML.NET Model Builder (önizleme) | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. EntityFramework | Entity Framework 6 araçları | 16.0.28315.86 | Önerilen
Microsoft. VisualStudio. Component. FSharp | F # dil desteği | 16.0.28315.86 | Önerilen
Microsoft. VisualStudio. Component. ıntellicode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft. VisualStudio. Component. IntelliTrace. ön uç | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | Önerilen
Microsoft. VisualStudio. Component. LiveUnitTesting | Live Unit Testing | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Önerilen
Microsoft. VisualStudio. Component. TypeScript. 4.3 | TypeScript 4,3 SDK | 16.0.31506.151 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Önerilen
Component. Dotfuscator | PreEmptive Protection - Dotfuscator | 16.10.31205.252 | İsteğe Bağlı
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 16.10.31205.252 | İsteğe Bağlı
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 16.10.31205.180 | İsteğe Bağlı
Component. Microsoft. WebTools. BrowserLink. WebLivePreview | Web canlı önizleme | 0.7.22.39845 | İsteğe Bağlı
Microsoft.Net. Component. 4.6.2. TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 hedefleme paketi | 16.4.29313.120 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 geliştirme araçları | 16.4.29318.151 | İsteğe Bağlı
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 Çalışma Zamanı (LTS) | 16.11.31603.221 | İsteğe Bağlı
Microsoft.VisualStudio.Component.ClassDesigner | Sınıf Tasarımcısı | 16.0.28528.71 | İsteğe Bağlı
Microsoft.VisualStudio.Component.CodeClone | Kod Kopyalama | 16.4.29409.204 | İsteğe Bağlı
Microsoft.VisualStudio.Component.CodeMap | Kod Haritası | 16.0.28625.61 | İsteğe Bağlı
Microsoft.VisualStudio.Component.DependencyValidation. Enterprise | Canlı Bağımlılık Doğrulaması | 16.0.28625.61 | İsteğe Bağlı
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | İsteğe Bağlı
Microsoft.VisualStudio.Component.FSharp.Desktop | F# masaüstü dili desteği | 16.0.28315.86 | İsteğe Bağlı
Microsoft.VisualStudio.Component.GraphDocument | DGML düzenleyicisi | 16.0.28625.61 | İsteğe Bağlı
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | İsteğe Bağlı
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılaması | 16.0.28517.75 | İsteğe Bağlı
Microsoft.VisualStudio.Component.MSODBC. SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | İsteğe Bağlı
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | İsteğe Bağlı
Microsoft.VisualStudio.Component.PortableLibrary | .NET Taşınabilir Kitaplığı hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.VisualStudio.Component. SQL. ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | İsteğe Bağlı
Microsoft.VisualStudio.Component. SQL. Datasources | Veri kaynağı desteği SQL Server kaynakları | 16.0.28315.86 | İsteğe Bağlı
Microsoft.VisualStudio.Component. SQL. LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | İsteğe Bağlı
Microsoft.VisualStudio.Component. SQL. Ssdt | SQL Server Veri Araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.10.31205.252 | İsteğe Bağlı
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Mimari ve analiz araçları | 16.5.29514.35 | İsteğe Bağlı
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | MSIX Paketleme Araçları | 16.10.31205.180 | İsteğe Bağlı
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları önkoşulları | 16.10.31205.180 | İsteğe Bağlı

## <a name="game-development-with-unity"></a>Unity ile oyun geliştirme

**Kimlik:** Microsoft.VisualStudio.Workload.ManagedGame

**Açıklama:** Güçlü bir platformlar arası geliştirme ortamı olan Unity ile 2D ve 3D oyunlar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yüküne dahil edilen bileşenler

Bileşen Kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 geliştirme araçları | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.Component. NuGet | NuGet paketi yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.Component.Unity | Unity için Visual Studio Araçları | 16.0.28315.86 | Gerekli
Component.UnityEngine.x64 | Unity Hub | 16.10.31205.252 | Önerilen
Component.UnityEngine.x86 | Unity 5.6 32 bit Düzenleyici | 16.1.28811.260 | Önerilen

## <a name="linux-development-with-c"></a>C++ ile Linux geliştirme

**Kimlik:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Açıklama:** Linux ortamında çalışan uygulamalar oluşturma ve hata ayıklama.

### <a name="components-included-by-this-workload"></a>Bu iş yüküne dahil edilen bileşenler

Bileşen Kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.MDD.Linux | Linux Geliştirme için C++ | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.10.31205.252 | Gerekli
Component.Linux.CMake | Linux için C++ CMake araçları | 16.2.29003.222 | Önerilen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Önerilen
Component.MDD.Linux. GCC.arm | Embedded ve IoT geliştirme araçları | 16.5.29515.121 | İsteğe Bağlı

## <a name="desktop-development-with-c"></a>C++ ile masaüstü geliştirme

**Kimlik:** Microsoft.VisualStudio.Workload.NativeDesktop

**Açıklama:** MSVC, Clang, CMake veya Windows gibi tercih Windows için modern C++ uygulamaları MSBuild.

### <a name="components-included-by-this-workload"></a>Bu iş yüküne dahil edilen bileşenler

Bileşen Kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Component. MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.ClassDesigner | Sınıf Tasarımcısı | 16.0.28528.71 | Gerekli
Microsoft.VisualStudio.Component.CodeMap | Kod Haritası | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.GraphDocument | DGML düzenleyicisi | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component. SQL. LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüşümü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 Yeniden Dağıtılabilir Güncelleştirmesi | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | C++ için mimari araçları | 16.0.28621.142 | Gerekli
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++ temel masaüstü özellikleri | 16.2.29012.281 | Gerekli
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4438 | Önerilen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Tam Zamanında hata ayıklayıcısı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX için grafik hata ayıklayıcısı ve GPU profilleyicisi | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | Önerilen
Microsoft.VisualStudio.Component. NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Önerilen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.TypeScript.4.3 | TypeScript 4.3 SDK | 16.0.31506.151 | Önerilen
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.VC.ATL | En son v142 derleme araçları için C++ ATL (x86 & x64) | 16.4.29313.120 | Önerilen
Microsoft.VisualStudio.Component.VC.CMake. Project | Windows için C++ CMake araçları | 16.3.29103.31 | Önerilen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ profil oluşturma araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Boost. test için test bağdaştırıcısı | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. Component. VC. TestAdapterForGoogleTest | Google Test için Test Bağdaştırıcısı | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC v142-VS 2019 C++ x64/x86 derleme araçları (en son) | 16.11.31317.239 | Önerilen
Microsoft. VisualStudio. Component. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Önerilen
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions. CMake | JSON düzenleyicisi | 16.10.31205.180 | Önerilen
Component. IncrediBuild | IncrediBuild-derleme hızlandırma | 16.10.31205.252 | İsteğe Bağlı
Component. IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | İsteğe Bağlı
Microsoft. Component. VC. Runtime. UıCRTSDK | Windows Evrensel CRT SDK | 16.0.28625.61 | İsteğe Bağlı
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft. net. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | İsteğe Bağlı
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 16.0.28517.75 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. 140 | MSVC v140-VS 2015 C++ derleme araçları (v 14.00) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. ATLMFC | En son v142 derleme araçları için C++ MFC (x86 & x64) | 16.4.29313.120 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. CLı. support | V142 derleme araçları için C++/CLı desteği (en son) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. LLVM. Clang | Windows için C++ clang derleyicisi (12.0.0) | 16.11.31603.221 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. LLVM. Clangaraç takımı | C++ Clang-CL for v142 derleme araçları (x64/x86) | 16.3.29207.166 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Modules. x86. x64 | V142 derleme araçları için C++ modülleri (x64/x86 – deneysel) | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. ARM64 | MSVC v142-VS 2019 C++ ARM64 derleme araçları (en son) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. v141. x86. x64 | MSVC v141-VS 2017 C++ x64/x86 derleme araçları (v 14.16) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. NativeDesktop. LLVM. Clang | Windows için C++ clang araçları (12.0.0-x64/x86) | 16.11.31603.221 | İsteğe Bağlı

## <a name="game-development-with-c"></a>C++ ile oyun geliştirme

**Kimlik:** Microsoft.VisualStudio.Workload.NativeGame

**Açıklama:** DirectX, Unreal veya Cocos2d tarafından desteklenen profesyonel oyunlar oluşturmak için C++'ın tüm gücünü kullanın.

### <a name="components-included-by-this-workload"></a>Bu iş yüküne dahil edilen bileşenler

Bileşen Kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 Yeniden Dağıtılabilir Güncelleştirmesi | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (En son) | 16.11.31317.239 | Gerekli
Microsoft.VisualStudio.Component.Windows10SDK | Windows Evrensel C Çalışma Zamanı | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX için grafik hata ayıklayıcısı ve GPU profilleyicisi | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ profil oluşturma araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Önerilen
Component.Android.NDK.R16B | Android NDK (R16B) | 16.11.31603.221 | İsteğe Bağlı
Component.Android.SDK25.Private | Android SDK kurulumu (API düzeyi 25) (C++ ile mobil geliştirme için yerel yükleme) | 16.0.28625.61 | İsteğe Bağlı
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | İsteğe Bağlı
Component.Cocos | Cocos | 16.0.28315.86 | İsteğe Bağlı
Component.Incredibuild | Incredibuild - Derleme Hızlandırma | 16.10.31205.252 | İsteğe Bağlı
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | İsteğe Bağlı
Component.MDD.Android | C++ Android geliştirme araçları | 16.0.28517.75 | İsteğe Bağlı
Component.OpenJDK | OpenJDK (Microsoft dağıtımı) | 16.10.31303.311 | İsteğe Bağlı
Component.Unreal | Unreal Engine yükleyicisi | 16.1.28810.153 | İsteğe Bağlı
Component.Unreal.Android | Unreal altyapısı için Android IDE desteği | 16.1.28810.153 | İsteğe Bağlı
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 16.11.31605.320 | İsteğe Bağlı
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 hedefleme paketi | 16.11.31605.320 | İsteğe Bağlı
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | İsteğe Bağlı
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.11.31605.320 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 geliştirme araçları | 16.0.28516.191 | İsteğe Bağlı
Microsoft.VisualStudio.Component. NuGet. BuildTools | NuGet ve derleme görevleri oluşturma | 16.1.28829.92 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.10.31205.252 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | İsteğe Bağlı

## <a name="mobile-development-with-c"></a>C++ ile mobil geliştirme

**Kimlik:** Microsoft.VisualStudio.Workload.NativeMobile

**Açıklama:** C++ kullanarak iOS, Android veya Windows platformlar arası uygulamalar derleme.

### <a name="components-included-by-this-workload"></a>Bu iş yüküne dahil edilen bileşenler

Bileşen Kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.Android.SDK25.Private | Android SDK kurulumu (API düzeyi 25) (C++ ile mobil geliştirme için yerel yükleme) | 16.0.28625.61 | Gerekli
Component.OpenJDK | OpenJDK (Microsoft dağıtımı) | 16.10.31303.311 | Gerekli
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.10.31205.252 | Gerekli
Component.Android.NDK.R16B | Android NDK (R16B) | 16.11.31603.221 | Önerilen
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Önerilen
Component.MDD.Android | C++ Android geliştirme araçları | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.11.31603.221 | Önerilen
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (32bit) | 16.11.31603.221 | İsteğe Bağlı
Component.Google.Android. Emulator. API25. Özel | Google Android Emulator (API Düzeyi 25) (yerel yükleme) | 16.1.28810.153 | İsteğe Bağlı
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (yerel yükleme) | 16.0.28528.71 | İsteğe Bağlı
Component.Incredibuild | Incredibuild - Derleme Hızlandırma | 16.10.31205.252 | İsteğe Bağlı
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | İsteğe Bağlı
Component.MDD.IOS | C++ iOS geliştirme araçları | 16.0.28517.75 | İsteğe Bağlı

## <a name="net-cross-platform-development"></a>.NET platformlar arası geliştirme

**Kimlik:** Microsoft.VisualStudio.Workload.NetCoreTools

**Açıklama:** Docker desteği de dahil olmak üzere .NET, ASP.NET Core, HTML/JavaScript ve Kapsayıcılar kullanarak platformlar arası uygulamalar derleme.

### <a name="components-included-by-this-workload"></a>Bu iş yüküne dahil edilen bileşenler

Bileşen Kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Razor Dil Hizmetleri | 16.10.31205.252 | Gerekli
Component.Microsoft.Web.LibraryManager | Kitaplık Yöneticisi | 16.10.31205.180 | Gerekli
Component.Microsoft.WebTools.BrowserLink.WebLivePreview | Web Live Preview | 0.7.22.39845 | Gerekli
Microsoft.Component. MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.ComponentGroup. ClickOnce. Yayımlamak | ClickOnce .NET için yayımlama  | 16.11.31603.221 | Gerekli
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 hedefleme paketi | 16.11.31605.320 | Gerekli
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | Gerekli
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft.NetCore.Component.DevelopmentTools | .NET geliştirme araçları | 16.10.31303.231 | Gerekli
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 Çalışma Zamanı (LTS) | 16.11.31603.221 | Gerekli
Microsoft.NetCore.Component.Runtime.5.0 | .NET 5.0 Çalışma Zamanı | 16.11.31603.221 | Gerekli
Microsoft.NetCore.Component.SDK | .NET SDK | 16.11.31603.221 | Gerekli
Microsoft.NetCore.Component.Web | .NET geliştirme araçları | 16.10.31303.231 | Gerekli
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.FSharp | F# dil desteği | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web projeleri için F# dili desteği | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılaması | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | Gerekli
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Yönetilen Masaüstü İş Yükü Çekirdeği | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.Component.MSODBC. SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | Gerekli
Microsoft.VisualStudio.Component. NuGet | NuGet paketi yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.Component. SQL. ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component. SQL. Clr | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component. SQL. Datasources | Veri kaynağı desteği SQL Server kaynakları | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component. SQL. LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component. SQL. Ssdt | SQL Server Veri Araçları | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüşümü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.TypeScript.4.3 | TypeScript 4.3 SDK | 16.0.31506.151 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları önkoşulları | 16.10.31205.180 | Gerekli
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Gerekli
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4438 | Önerilen
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure Web İşleri Araçları | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.AppInsights.Tools | Geliştirici Analizi araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Yazma Araçları | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET için Azure kitaplıkları | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.Azure.Compute. Emulator | Azure İşlem Emulator | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.Azure. Depolama. Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | Önerilen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Tam Zamanında hata ayıklayıcısı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Anlık Görüntü Hata Ayıklayıcı | 16.5.29813.82 | Önerilen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Zaman Yolculuğu Hata Ayıklayıcısı | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.DotNetModelBuilder | ML.NET Model Builder (Önizleme) | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.WslDebugging | WSL ile .NET Hata Ayıklama | 16.11.31603.221 | Önerilen
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Azure Web İşleri Araçları | 16.10.31205.180 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Web geliştirme için bulut araçları | 16.10.31205.180 | Önerilen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 Çalışma Zamanı (LTS) | 16.11.31603.221 | İsteğe Bağlı
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Geliştirme zamanı IIS desteği | 16.10.31205.180 | İsteğe Bağlı
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | MSIX Paketleme Araçları | 16.10.31205.180 | İsteğe Bağlı

## <a name="mobile-development-with-net"></a>.NET ile mobil geliştirme

**Kimlik:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Açıklama:** Xamarin kullanarak iOS, Android veya Windows platformlar arası uygulamalar derleme.

### <a name="components-included-by-this-workload"></a>Bu iş yüküne dahil edilen bileşenler

Bileşen Kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (Microsoft dağıtımı) | 16.10.31303.311 | Gerekli
Component.Xamarin | Xamarin | 16.10.31205.252 | Gerekli
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.10.31205.252 | Gerekli
Microsoft.Component. MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.ComponentGroup. ClickOnce. Yayımlamak | ClickOnce .NET için yayımlama  | 16.11.31603.221 | Gerekli
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | Gerekli
Microsoft. net. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft. NetCore. Component. DevelopmentTools | .NET geliştirme araçları | 16.10.31303.231 | Gerekli
Microsoft. NetCore. Component. Runtime. 3.1 | .NET Core 3,1 çalışma zamanı (LTS) | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 çalışma zamanı | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. SDK | .NET SDK | 16.11.31603.221 | Gerekli
Microsoft. VisualStudio. Component. FSharp | F # dil desteği | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. Component. Merq | Ortak Xamarin iç araçları | 16.2.29012.281 | Gerekli
Microsoft. VisualStudio. Component. MonoDebugger | Mono hata ayıklayıcısı | 16.0.28517.75 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions. TemplateEngine | ASP.NET şablon oluşturma altyapısı | 16.10.31205.180 | Gerekli
Component. Android. SDK30 | Android SDK kurulumu (API düzeyi 30) | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. ıntellicode | IntelliCode | 16.11.31603.221 | Önerilen

## <a name="aspnet-and-web-development"></a>ASP.NET ve web geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. NetWeb

**Açıklama:** ASP.NET Core, ASP.NET, HTML/JavaScript ve docker desteği dahil kapsayıcılar kullanarak web uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 16.10.31205.252 | Gerekli
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 16.10.31205.180 | Gerekli
Component. Microsoft. WebTools. BrowserLink. WebLivePreview | Web canlı önizleme | 0.7.22.39845 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft. ComponentGroup. ClickOnce. Yayınlamanız | ClickOnce .NET için yayımlama  | 16.11.31603.221 | Gerekli
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 16.11.31605.320 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | Gerekli
Microsoft. net. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft. NetCore. Component. DevelopmentTools | .NET geliştirme araçları | 16.10.31303.231 | Gerekli
Microsoft. NetCore. Component. Runtime. 3.1 | .NET Core 3,1 çalışma zamanı (LTS) | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 çalışma zamanı | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. SDK | .NET SDK | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. Web | .NET geliştirme araçları | 16.10.31303.231 | Gerekli
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Gerekli
Microsoft. VisualStudio. Component. FSharp | F # dil desteği | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. Component. FSharp. WebTemplates | Web projeleri için F # dil desteği | 16.3.29207.166 | Gerekli
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 16.0.28517.75 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 16.4.29318.151 | Gerekli
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ODBC sürücüsü | 16.0.28625.61 | Gerekli
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server Komut satırı yardımcı programları | 16.0.28707.177 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Gerekli
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. Component. SQL. Kaynağı | Veri kaynağı desteği SQL Server kaynakları | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component. SQL. LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component. SQL. Ssdt | SQL Server Veri Araçları | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüşümü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.TypeScript.4.3 | TypeScript 4.3 SDK | 16.0.31506.151 | Gerekli
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları önkoşulları | 16.10.31205.180 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Web.Client | ASP.NET ve web geliştirme araçları | 16.10.31205.180 | Gerekli
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Gerekli
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.4438 | Önerilen
Component.Microsoft.VisualStudio.Web.AzureFunctions | Azure Web İşleri Araçları | 16.10.31205.252 | Önerilen
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.11.31605.320 | Önerilen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 geliştirme araçları | 16.0.28516.191 | Önerilen
Microsoft.VisualStudio.Component.AppInsights.Tools | Geliştirici Analizi araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.AspNet45 | Gelişmiş ASP.NET özellikleri | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Yazma Araçları | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET için Azure kitaplıkları | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.Azure.Compute. Emulator | Azure İşlem Emulator | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.Azure. Depolama. Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | Önerilen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Tam Zamanında hata ayıklayıcısı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Anlık Görüntü Hata Ayıklayıcı | 16.5.29813.82 | Önerilen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Zaman Yolculuğu Hata Ayıklayıcısı | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. EntityFramework | Entity Framework 6 araçları | 16.0.28315.86 | Önerilen
Microsoft. VisualStudio. Component. ıntellicode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft. VisualStudio. Component. IntelliTrace. ön uç | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft. VisualStudio. Component. LiveUnitTesting | Live Unit Testing | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. Component. WslDebugging | WSL ile .NET hata ayıklaması | 16.11.31603.221 | Önerilen
Microsoft. VisualStudio. ComponentGroup. AzureFunctions | Azure Web Işleri araçları | 16.10.31205.180 | Önerilen
Microsoft. VisualStudio. ComponentGroup. Web. CloudTools | Web geliştirme için bulut araçları | 16.10.31205.180 | Önerilen
Microsoft.Net. Component. 4.6.2. TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.1. TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.Net. Component. 4.7. TargetingPack | .NET Framework 4,7 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.Net. Component. 4.8. TargetingPack | .NET Framework 4,8 hedefleme paketi | 16.4.29313.120 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.6.1. DeveloperTools | .NET Framework 4.6.1 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.6.2. DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.1. DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7. DeveloperTools | .NET Framework 4,7 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.8. DeveloperTools | .NET Framework 4,8 geliştirme araçları | 16.4.29318.151 | İsteğe Bağlı
Microsoft. net. Core. Component. SDK. 2.1 | .NET Core 2,1 çalışma zamanı (LTS) | 16.11.31603.221 | İsteğe Bağlı
Microsoft. VisualStudio. Component. ClassDesigner | Sınıf Tasarımcısı | 16.0.28528.71 | İsteğe Bağlı
Microsoft. VisualStudio. Component. CodeClone | Kod kopyası | 16.4.29409.204 | İsteğe Bağlı
Microsoft. VisualStudio. Component. CodeMap | Kod Haritası | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. DependencyValidation. Enterprise | Canlı bağımlılık doğrulaması | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. GraphDocument | DGML Düzenleyicisi | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. TestTools. WebLoadTest | Web performansı ve yük testi araçları | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. WCF. Tooling | Windows Communication Foundation | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Addiwebprojecttemplates | Ek proje şablonları (önceki sürümler) | 16.10.31205.180 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. mimari Turetools. Managed | Mimari ve analiz araçları | 16.5.29514.35 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. ıısdevelopment | Geliştirme zamanı IIS desteği | 16.10.31205.180 | İsteğe Bağlı

## <a name="nodejs-development"></a>Node.js geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Node

**Açıklama:** Zaman uyumsuz olay temelli bir JavaScript çalışma zamanı olan Node.js kullanarak ölçeklenebilir ağ uygulamaları oluşturun. 

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 16.0.28517.75 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | Gerekli
Microsoft. VisualStudio. Component. Node. Tools | Node.js geliştirme araçları | 16.5.29515.121 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 4.3 | TypeScript 4,3 SDK | 16.0.31506.151 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Gerekli
Component. Microsoft. VisualStudio. Livespaylaşımı | Live Share | 1.0.4438 | Önerilen
Microsoft. VisualStudio. Component. Debugger. Adaıntime | Tam zamanında hata ayıklayıcı | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. Component. ıntellicode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic roslyn derleyicileri | 16.0.28714.129 | Önerilen
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 16.5.29515.121 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Coreıde | C++ temel özellikleri | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC v142-VS 2019 C++ x64/x86 derleme araçları (en son) | 16.11.31317.239 | İsteğe Bağlı

## <a name="officesharepoint-development"></a>Office/SharePoint geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Office

**Açıklama:** C#, VB ve JavaScript kullanarak Office ve SharePoint eklentiler, SharePoint çözümleri ve VSTO eklentileri oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 16.10.31205.252 | Gerekli
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 16.10.31205.180 | Gerekli
Component. Microsoft. WebTools. BrowserLink. WebLivePreview | Web canlı önizleme | 0.7.22.39845 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 16.11.31605.320 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | Gerekli
Microsoft. net. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 hedefleme paketi | 16.11.31605.320 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft. NetCore. Component. Runtime. 3.1 | .NET Core 3,1 çalışma zamanı (LTS) | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 çalışma zamanı | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. SDK | .NET SDK | 16.11.31603.221 | Gerekli
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 16.5.29515.121 | Gerekli
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Gerekli
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 16.0.28517.75 | Gerekli
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 16.4.29318.151 | Gerekli
Microsoft. VisualStudio. Component. ManagedDesktop. Önkoşullar | .NET masaüstü geliştirme araçları | 16.10.31205.180 | Gerekli
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ODBC sürücüsü | 16.0.28625.61 | Gerekli
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server Komut satırı yardımcı programları | 16.0.28707.177 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Gerekli
Microsoft. VisualStudio. Component. SharePoint. Tools | Visual Studio için Office Geliştirici Araçları | 16.4.29409.204 | Gerekli
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. Component. SQL. Kaynağı | SQL Server destek için veri kaynakları | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 localdb | 16.0.28625.61 | Gerekli
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 16.3.29207.166 | Gerekli
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 16.0.28625.61 | Gerekli
Microsoft. VisualStudio. Component. TypeScript. 4.3 | TypeScript 4,3 SDK | 16.0.31506.151 | Gerekli
Microsoft. VisualStudio. Component. WCF. Tooling | Windows Communication Foundation | 16.0.28625.61 | Gerekli
Microsoft. VisualStudio. Component. Web | ASP.NET ve web geliştirme araçları | 16.10.31205.252 | Gerekli
Microsoft. VisualStudio. Component. Workflow | Windows Workflow Foundation | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve web geliştirme araçları önkoşulları | 16.10.31205.180 | Gerekli
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | Gerekli
Microsoft. VisualStudio. Component. ıntellicode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft. VisualStudio. Component. TeamOffice | Office için Visual Studio Araçları (VSTO) | 16.4.29409.204 | Önerilen
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.Net. Component. 4.6.2. TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.1. TargetingPack | .NET Framework 4.7.1 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.Net. Component. 4.7. TargetingPack | .NET Framework 4,7 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft.Net. Component. 4.8. TargetingPack | .NET Framework 4,8 hedefleme paketi | 16.4.29313.120 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.6.1. DeveloperTools | .NET Framework 4.6.1 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.6.2. DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7.1. DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.7. DeveloperTools | .NET Framework 4,7 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. 4.8. DeveloperTools | .NET Framework 4,8 geliştirme araçları | 16.4.29318.151 | İsteğe Bağlı
Microsoft. VisualStudio. Component. IntelliTrace. ön uç | IntelliTrace | 16.5.29515.121 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. SharePoint. WıF | Windows Identity Foundation 3.5 | 16.0.28621.142 | İsteğe Bağlı

## <a name="python-development"></a>Python geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Python

**Açıklama:** Python için düzen, hata ayıklama, etkileşimli geliştirme ve kaynak denetimi.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. Component. PythonTools | Python dil desteği | 16.11.31314.313 | Gerekli
Component. CPython3. x64 | Python 3 64-bit (3.7.8) | 3.7.8 | Önerilen
Component. CPython2. x64 | Python 2 64-bit (2.7.18) (destek dışı) | 2.7.18.2 | İsteğe Bağlı
Component. CPython2. x86 | Python 2 32-bit (2.7.18) (destek dışı) | 2.7.18.2 | İsteğe Bağlı
Component. CPython3. x86 | Python 3 32-bit (3.7.8) | 3.7.8 | İsteğe Bağlı
Component. Microsoft. VisualStudio. Livespaylaşımı | Live Share | 1.0.4438 | İsteğe Bağlı
Component. Microsoft. VisualStudio. Çzorexgeri | Razor dil Hizmetleri | 16.10.31205.252 | İsteğe Bağlı
Component. Microsoft. Web. LibraryManager | Kitaplık Yöneticisi | 16.10.31205.180 | İsteğe Bağlı
Component. Microsoft. WebTools. BrowserLink. WebLivePreview | Web canlı önizleme | 0.7.22.39845 | İsteğe Bağlı
Microsoft. Component. IronPython | IronPython (destek dışı) | 16.10.31303.231 | İsteğe Bağlı
Microsoft. Component. MSBuild | MSBuild | 16.5.29515.121 | İsteğe Bağlı
Microsoft. Component. PythonTools. Minicondax64 | Python miniconda (destek dışı) | 16.11.31314.313 | İsteğe Bağlı
Microsoft. Component. PythonTools. Web | Python web desteği | 16.10.31205.252 | İsteğe Bağlı
Microsoft. ComponentGroup. PythonTools. NativeDevelopment | Python yerel geliştirme araçları | 16.10.31205.180 | İsteğe Bağlı
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | İsteğe Bağlı
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 16.11.31605.320 | İsteğe Bağlı
Microsoft.Net. Component. 4.7.2. TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | İsteğe Bağlı
Microsoft. net. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | İsteğe Bağlı
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft. NetCore. Component. Runtime. 3.1 | .NET Core 3,1 çalışma zamanı (LTS) | 16.11.31603.221 | İsteğe Bağlı
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 çalışma zamanı | 16.11.31603.221 | İsteğe Bağlı
Microsoft. NetCore. Component. SDK | .NET SDK | 16.11.31603.221 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. AuthoringTools | Azure yazma araçları | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. Clientlıbs | .NET için Azure kitaplıkları | 16.0.28315.86 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. COMPUTE. Emulator | Azure Işlem Emulator | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. Depolama. Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. Waverton | Azure Cloud Services çekirdek araçları | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Azure. Waverton. BuildTools | Azure Cloud Services derleme araçları | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Debugger. Adaıntime | Tam zamanında hata ayıklayıcı | 16.0.28517.75 | İsteğe Bağlı
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics. Tools | DirectX için grafik hata ayıklayıcı ve GPU Profiler | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. IISExpress | IIS Express  | 16.0.28315.86 | İsteğe Bağlı
Microsoft. VisualStudio. Component. JavaScript. Diagnostics | JavaScript tanılama | 16.0.28517.75 | İsteğe Bağlı
Microsoft. VisualStudio. Component. JavaScript. TypeScript | JavaScript ve TypeScript dil desteği | 16.11.31404.150 | İsteğe Bağlı
Microsoft. VisualStudio. Component. ManagedDesktop. Core | Yönetilen masaüstü Iş yükü çekirdeği | 16.4.29318.151 | İsteğe Bağlı
Microsoft. VisualStudio. Component. MSODBC. SQL | SQL Server ODBC sürücüsü | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. MSSQL. CMDLnUtils | SQL Server Komut satırı yardımcı programları | 16.0.28707.177 | İsteğe Bağlı
Microsoft. VisualStudio. Component. NuGet | NuGet paket yöneticisi | 16.1.28829.92 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic roslyn derleyicileri | 16.0.28714.129 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. Kaynağı | SQL Server destek için veri kaynakları | 16.0.28315.86 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 localdb | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. SSDT | SQL Server Veri Araçları | 16.3.29207.166 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Textşablon oluşturma | Metin şablonu dönüşümü | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. TypeScript. 4.3 | TypeScript 4,3 SDK | 16.0.31506.151 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Coreıde | C++ temel özellikleri | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. DiagnosticTools | C++ profil oluşturma araçları | 16.5.29515.121 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC v142-VS 2019 C++ x64/x86 derleme araçları (en son) | 16.11.31317.239 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Web | ASP.NET ve web geliştirme araçları | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. WebDeploy | Web Dağıtımı | 16.0.28517.75 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK | Windows Evrensel C çalışma zamanı | 16.4.29409.204 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. Web | ASP.NET ve web geliştirme araçları önkoşulları | 16.10.31205.180 | İsteğe Bağlı
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions | ASP.NET ve web geliştirme | 16.10.31205.180 | İsteğe Bağlı

## <a name="universal-windows-platform-development"></a>Evrensel Windows Platformu geliştirme

**Kimliği:** Microsoft. VisualStudio. Workload. Universal

**Açıklama:** C#, VB veya isteğe bağlı C++ ile Evrensel Windows Platformu uygulamalar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. Component. NetFX. Native | .NET Yerel | 16.5.29515.121 | Gerekli
Microsoft. ComponentGroup. Blend | Visual Studio için Blend | 16.0.28315.86 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 16.11.31605.320 | Gerekli
Microsoft. NetCore. Component. Runtime. 3.1 | .NET Core 3,1 çalışma zamanı (LTS) | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. Runtime. 5.0 | .NET 5,0 çalışma zamanı | 16.11.31603.221 | Gerekli
Microsoft. NetCore. Component. SDK | .NET SDK | 16.11.31603.221 | Gerekli
Microsoft. VisualStudio. Component. Appınsights. Tools | Geliştirici analiz araçları | 16.5.29515.121 | Gerekli
Microsoft. VisualStudio. Component. DiagnosticTools | .NET profil oluşturma araçları | 16.10.31205.252 | Gerekli
Microsoft. VisualStudio. Component. Graphics | Görüntü ve 3B model düzenleyicileri | 16.10.31205.252 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. derleyicisi | C# ve Visual Basic roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft. VisualStudio. Component. Roslyn. LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Gerekli
Microsoft. VisualStudio. Component. SQL. CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft. VisualStudio. Component. Windows10SDK. 19041 | Windows 10 SDK (10.0.19041.0) | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.ComponentGroup.MSIX. paketleme | MSIX paketleme araçları | 16.10.31205.180 | Gerekli
Microsoft. VisualStudio. ComponentGroup. UWP. NetCoreAndStandard | .NET Native ve .NET Standard | 16.3.29102.218 | Gerekli
Microsoft. VisualStudio. ComponentGroup. UWP. support | Evrensel Windows Platformu araçları | 16.10.31205.180 | Gerekli
Microsoft. VisualStudio. ComponentGroup. UWP. Xamarin | Xamarin için Evrensel Windows Platformu araçları | 16.10.31205.180 | Gerekli
Microsoft. VisualStudio. Component. ıntellicode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft. VisualStudio. Component. IntelliTrace. ön uç | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft. net. Component. 4.8. SDK | .NET Framework 4,8 SDK | 16.4.29313.120 | İsteğe Bağlı
Microsoft. VisualStudio. Component. ClassDesigner | Sınıf Tasarımcısı | 16.0.28528.71 | İsteğe Bağlı
Microsoft. VisualStudio. Component. CodeClone | Kod kopyası | 16.4.29409.204 | İsteğe Bağlı
Microsoft. VisualStudio. Component. CodeMap | Kod Haritası | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. DependencyValidation. Enterprise | Canlı bağımlılık doğrulaması | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. GraphDocument | DGML Düzenleyicisi | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. Graphics. Tools | DirectX için grafik hata ayıklayıcı ve GPU Profiler | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. SQL. LocalDB. Runtime | SQL Server Express 2016 localdb | 16.0.28625.61 | İsteğe Bağlı
Microsoft. VisualStudio. Component. UWP. VC. ARM64 | v142 derleme araçları için C++ Evrensel Windows Platformu desteği (ARM64) | 16.3.29207.166 | İsteğe Bağlı
Microsoft. VisualStudio. Component. UWP. VC. ARM64EC | v142 derleme araçları için C++ Evrensel Windows Platformu desteği (ARM64EC – deneysel) | 16.10.31303.231 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Coreıde | C++ temel özellikleri | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. ARM | MSVC v142-VS 2019 C++ ARM derleme araçları (en son) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. ARM64 | MSVC v142-VS 2019 C++ ARM64 derleme araçları (en son) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. ARM64EC | MSVC v142-VS 2019 C++ ARM64EC derleme araçları (en son – deneysel) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. Tools. x86. x64 | MSVC v142-VS 2019 C++ x64/x86 derleme araçları (en son) | 16.11.31317.239 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. v141. ARM | MSVC v141-VS 2017 C++ ARM derleme araçları (v 14.16) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. v141. ARM64 | MSVC v141-VS 2017 C++ ARM64 derleme araçları (v 14.16) | 16.10.31205.252 | İsteğe Bağlı
Microsoft. VisualStudio. Component. VC. v141. x86. x64 | MSVC v141 - VS 2017 C++ x64/x86 derleme araçları (v14.16) | 16.10.31205.252 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.10.31205.252 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.10.31205.252 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | İsteğe Bağlı
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | USB Cihaz Bağlantısı | 16.10.31205.252 | İsteğe Bağlı
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Mimari ve analiz araçları | 16.5.29514.35 | İsteğe Bağlı
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ (v142) Universal Windows Platform araçları | 16.10.31205.180 | İsteğe Bağlı
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | C++ (v141) Universal Windows Platform araçları | 16.1.28810.153 | İsteğe Bağlı

## <a name="visual-studio-extension-development"></a>Visual Studio uzantısı geliştirme

**Kimlik:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Açıklama:** Yeni komutlar, kod çözümleyicileri ve araç Visual Studio için eklentiler ve uzantılar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yüküne dahil edilen bileşenler

Bileşen Kimliği | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Component. MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 hedefleme paketi | 16.10.31205.252 | Gerekli
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component. NuGet | NuGet paketi yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.10.31205.252 | Gerekli
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio geliştirme önkoşulları | 16.10.31205.180 | Gerekli
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.10.31205.252 | Önerilen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 16.11.31603.221 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüşümü | 16.0.28625.61 | Önerilen
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK’sı | 16.2.29003.222 | İsteğe Bağlı
Microsoft.VisualStudio.Component.AppInsights.Tools | Geliştirici Analizi araçları | 16.5.29515.121 | İsteğe Bağlı
Microsoft.VisualStudio.Component.DslTools | Modelleme SDK'sı | 16.0.28315.86 | İsteğe Bağlı

## <a name="unaffiliated-components"></a>Bağlı olmayan bileşenler

Bunlar herhangi bir iş yüküne dahil değildir, ancak tek bir bileşen olarak seçilebilir.

Bileşen Kimliği | Name | Sürüm
--- | --- | ---
Bileşen. GitHub. VisualStudio | GitHub uzantısını Visual Studio | 2.5.9.5485
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Microsoft.Component. ClickOnce | ClickOnce Yayımlama | 16.11.31603.221
Microsoft.Component.HelpViewer | Yardım Görüntüleyicisi | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2 Çalışma Zamanı (destek dışında) | 16.11.31603.221
Microsoft.Net.Core.Component.SDK.3.0 | .NET Core 3.0 Çalışma Zamanı (destek dışında) | 16.11.31603.221
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Geliştirme Araçları ve .NET Core 2.1 | 16.10.31205.252
Microsoft.NetCore.ComponentGroup.Web.2.1 | Web Geliştirme Araçları ve .NET Core 2.1 | 16.10.31205.252
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Azure DevOps Office Tümleştirmesi | 16.0.28625.61
Microsoft.VisualStudio.Component.Git | Windows için Git | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL araçları | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Kodlanmış UI testi | 16.0.28327.66
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ ARM64 derleme araçları (v14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | v142 derleme araçları için C++ v14.20 ATL (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | v142 derleme araçları (ARM) için C++ v14.20 ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.20 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | v142 derleme araçları için C++ v14.20 ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.20 ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.20 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | v142 derleme araçları için C++/CLI desteği (14.20) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.20.MFC | v142 derleme araçları için C++ v14.20 MFC (x86 & x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | v142 derleme araçları (ARM) için C++ v14.20 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.20 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | v142 derleme araçları için C++ v14.20 MFC (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.20 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.20 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.20) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.21) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 - VS 2019 C++ ARM64 derleme araçları (v14.21) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | v142 derleme araçları için C++ v14.21 ATL (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | v142 derleme araçları (ARM) için C++ v14.21 ATL | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.21 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | v142 derleme araçları için C++ v14.21 ATL (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.21 ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.21 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | v142 derleme araçları için C++/CLI desteği (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | v142 derleme araçları için C++ v14.21 MFC (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | v142 derleme araçları (ARM) için C++ v14.21 MFC | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.21 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | v142 derleme araçları için C++ v14.21 MFC (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.21 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.21 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.21) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 - VS 2019 C++ ARM64 derleme araçları (v14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | v142 derleme araçları için C++ v14.22 ATL (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | v142 derleme araçları (ARM) için C++ v14.22 ATL | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.22 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | v142 derleme araçları için C++ v14.22 ATL (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.22 ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.22 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | v142 derleme araçları için C++/CLI desteği (14.22) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.22.MFC | v142 derleme araçları için C++ v14.22 MFC (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | v142 derleme araçları (ARM) için C++ v14.22 MFC | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.22 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | v142 derleme araçları için C++ v14.22 MFC (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.22 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.22 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.22) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC v142 - VS 2019 C++ ARM64 derleme araçları (v14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | v142 derleme araçları için C++ v14.23 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | v142 derleme araçları (ARM) için C++ v14.23 ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.23 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | v142 derleme araçları için C++ v14.23 ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.23 ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.23 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | v142 derleme araçları için C++/CLI desteği (14.23) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.23.MFC | v142 derleme araçları için C++ v14.23 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | v142 derleme araçları (ARM) için C++ v14.23 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.23 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | v142 derleme araçları için C++ v14.23 MFC (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.23 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.23 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.23) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.24) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.24) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. ARM64 | MSVC v142-VS 2019 C++ ARM64 derleme araçları (v 14.24) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. ARM64. Spectre | MSVC v142-VS 2019 C++ ARM64 Spectre-azaltılan lıbs (v 14.24) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. ATL | V142 derleme araçları için C++ v 14.24 ATL (x86 & x64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. ATL. ARM | V142 derleme araçları için C++ v 14.24 ATL (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. ATL. ARM. Spectre | Spectre azaltmaları (ARM) ile v142 derleme araçları için C++ v 14.24 ATL | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. ATL. ARM64 | V142 derleme araçları için C++ v 14.24 ATL (ARM64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. ATL. ARM64. Spectre | Spectre azaltmaları ile v142 derleme araçları için C++ v 14.24 ATL (ARM64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. ATL. Spectre | Spectre azaltmaları ile v142 derleme araçları için C++ v 14.24 ATL (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. CLı. support | V142 derleme araçları için C++/CLı desteği (14,24) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. MFC | V142 derleme araçları için C++ v 14.24 MFC (x86 & x64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM | V142 derleme araçları için C++ v 14.24 MFC (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM. Spectre | Spectre azaltmaları (ARM) ile v142 derleme araçları için C++ v 14.24 MFC | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM64 | V142 derleme araçları için C++ v 14.24 MFC (ARM64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.24. MFC. ARM64. Spectre | Spectre azaltmaları ile v142 derleme araçları için C++ v 14.24 MFC (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. MFC. Spectre | Spectre azaltmaları ile v142 derleme araçları için C++ v 14.24 MFC (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.24. x86. x64 | MSVC v142-VS 2019 C++ x64/x86 derleme araçları (v 14.24) | 16.11.31317.239
Microsoft. VisualStudio. Component. VC. 14.24. x86. x64. Spectre | MSVC v142-VS 2019 C++ x64/x86 Spectre-azaltıllıbs (v 14.24) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. 14.25. ARM | MSVC v142-VS 2019 C++ ARM derleme araçları (v 14.25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ARM. Spectre | MSVC v142-VS 2019 C++ ARM Spectre-azaltılan lıbs (v 14.25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ARM64 | MSVC v142-VS 2019 C++ ARM64 derleme araçları (v 14.25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ARM64. Spectre | MSVC v142-VS 2019 C++ ARM64 Spectre-azaltılan lıbs (v 14.25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL | V142 derleme araçları için C++ v 14.25 ATL (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM | V142 derleme araçları için C++ v 14.25 ATL (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM. Spectre | Spectre azaltmaları (ARM) ile v142 derleme araçları için C++ v 14.25 ATL | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM64 | V142 derleme araçları için C++ v 14.25 ATL (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. ARM64. Spectre | Spectre azaltmaları ile v142 derleme araçları için C++ v 14.25 ATL (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. ATL. Spectre | Spectre azaltmaları ile v142 derleme araçları için C++ v 14.25 ATL (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. CLı. support | V142 derleme araçları için C++/CLı desteği (14,25) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. MFC | V142 derleme araçları için C++ v 14.25 MFC (x86 & x64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. MFC. ARM | V142 derleme araçları için C++ v 14.25 MFC (ARM) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. MFC. ARM. Spectre | Spectre azaltmaları (ARM) ile v142 derleme araçları için C++ v 14.25 MFC | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. MFC. ARM64 | V142 derleme araçları için C++ v 14.25 MFC (ARM64) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. 14.25. MFC. ARM64. Spectre | Spectre azaltmaları ile v142 derleme araçları için C++ v 14.25 MFC (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.MFC.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.25 MFC (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.25.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.25) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.25.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.25) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ARM64 | MSVC v142 - VS 2019 C++ ARM64 derleme araçları (v14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL | v142 derleme araçları için C++ v14.26 ATL (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM | v142 derleme araçları (ARM) için C++ v14.26 ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.26 ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64 | v142 derleme araçları için C++ v14.26 ATL (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.26 ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.ATL.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.26 ATL (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.CLI.Support | v142 derleme araçları için C++/CLI desteği (14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC | v142 derleme araçları için C++ v14.26 MFC (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM | v142 derleme araçları (ARM) için C++ v14.26 MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.26 MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64 | v142 derleme araçları için C++ v14.26 MFC (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.26 MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.MFC.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.26 MFC (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.26.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.26) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.26.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.26) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM64 | MSVC v142 - VS 2019 C++ ARM64 derleme araçları (v14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL | v142 derleme araçları için C++ v14.27 ATL (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM | v142 derleme araçları (ARM) için C++ v14.27 ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.27 ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM64 | v142 derleme araçları için C++ v14.27 ATL (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.27 ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.ATL.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.27 ATL (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.CLI.Support | v142 derleme araçları için C++/CLI desteği (14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC | v142 derleme araçları için C++ v14.27 MFC (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM | v142 derleme araçları (ARM) için C++ v14.27 MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM.Spectre | Spectre Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.27 MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64 | v142 derleme araçları için C++ v14.27 MFC (ARM64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.27 MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.MFC.Spectre | Spectre Azaltmaları ile v142 derleme araçları için C++ v14.27 MFC (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.27.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.27) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.27.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.27) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM64 | MSVC v142 - VS 2019 C++ ARM64 derleme araçları (v14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL | v142 derleme araçları için C++ v14.28 (16.9) ATL (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM | v142 derleme araçları (ARM) için C++ v14.28 (16.9) ATL | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM.Spectre | Spectre Risk Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.28 (16.9) ATL | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM64 | v142 derleme araçları (ARM64) için C++ v14.28 (16.9) ATL | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.28 (16.9) ATL | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.ATL.Spectre | Spectre Risk Azaltmaları ile v142 derleme araçları için C++ v14.28 (16.9) ATL (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.CLI.Support | v142 derleme araçları için C++/CLI desteği (14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC | v142 derleme araçları için C++ v14.28 (16.9) MFC (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM | v142 derleme araçları (ARM) için C++ v14.28 (16.9) MFC | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM.Spectre | Spectre Risk Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.28 (16.9) MFC | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM64 | v142 derleme araçları (ARM64) için C++ v14.28 (16.9) MFC | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.28 (16.9) MFC | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.MFC.Spectre | Spectre Risk Azaltmaları ile v142 derleme araçları için C++ v14.28 (16.9) MFC (x86 & x64) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.16.9.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.28-16.9) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.28.16.9.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.28-16.9) | 16.10.31303.231
Microsoft.VisualStudio.Component.VC.14.28.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ARM64 | MSVC v142 - VS 2019 C++ ARM64 derleme araçları (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL | v142 derleme araçları için C++ v14.28 (16.8) ATL (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM | v142 derleme araçları (ARM) için C++ v14.28 (16.8) ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM.Spectre | Spectre Risk Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.28 (16.8) ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM64 | v142 derleme araçları (ARM64) için C++ v14.28 (16.8) ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.28 (16.8) ATL | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.ATL.Spectre | Spectre Risk Azaltmaları ile v142 derleme araçları için C++ v14.28 (16.8) ATL (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.CLI.Support | v142 derleme araçları için C++/CLI desteği (14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC | v142 derleme araçları için C++ v14.28 (16.8) MFC (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM | v142 derleme araçları (ARM) için C++ v14.28 (16.8) MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM.Spectre | Spectre Risk Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.28 (16.8) MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM64 | v142 derleme araçları (ARM64) için C++ v14.28 (16.8) MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.28 (16.8) MFC | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.MFC.Spectre | Spectre Risk Azaltmaları ile v142 derleme araçları için C++ v14.28 (16.8) MFC (x86 & x64) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.28.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.28-16.8) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.28.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.28-16.8) | 16.10.31205.252
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM | MSVC v142 - VS 2019 C++ ARM derleme araçları (v14.29-16.10) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre-mitigated libs (v14.29-16.10) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM64 | MSVC v142 - VS 2019 C++ ARM64 derleme araçları (v14.29-16.10) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre-mitigated libs (v14.29-16.10) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL | v142 derleme araçları için C++ v14.29 (16.10) ATL (x86 & x64) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.ARM | v142 derleme araçları (ARM) için C++ v14.29 (16.10) ATL | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.ARM.Spectre | Spectre Risk Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.29 (16.10) ATL | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.ARM64 | v142 derleme araçları (ARM64) için C++ v14.29 (16.10) ATL | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.29 (16.10) ATL | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.ATL.Spectre | Spectre Risk Azaltmaları ile v142 derleme araçları için C++ v14.29 (16.10) ATL (x86 & x64) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.CLI.Support | v142 derleme araçları için C++/CLI desteği (14.29-16.10) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC | v142 derleme araçları için C++ v14.29 (16.10) MFC (x86 & x64) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM | v142 derleme araçları (ARM) için C++ v14.29 (16.10) MFC | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM.Spectre | Spectre Risk Azaltmaları (ARM) ile v142 derleme araçları için C++ v14.29 (16.10) MFC | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM64 | v142 derleme araçları (ARM64) için C++ v14.29 (16.10) MFC | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.ARM64.Spectre | Spectre Risk Azaltmaları (ARM64) ile v142 derleme araçları için C++ v14.29 (16.10) MFC | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.MFC.Spectre | Spectre Risk Azaltmaları ile v142 derleme araçları için C++ v14.29 (16.10) MFC (x86 & x64) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.14.29.16.10.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 derleme araçları (v14.29-16.10) | 16.11.31317.239
Microsoft.VisualStudio.Component.VC.14.29.16.10.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre-mitigated libs (v14.29-16.10) | 16.11.31314.313
Microsoft.VisualStudio.Component.VC.ATL.ARM | En son v142 derleme araçları (ARM) için C++ ATL | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Spectre Risk Azaltmaları (ARM) ile en son v142 derleme araçları için C++ ATL | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. ATL. ARM64 | En son v142 derleme araçları için C++ ATL (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. ATL. ARM64. Spectre | Spectre azaltmaları ile en son v142 derleme araçları için C++ ATL (ARM64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. ATL. ARM64EC | En son v142 derleme araçları için C++ ATL (ARM64EC-deneysel) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. ATL. ARM64EC. Spectre | Spectre azaltmaları ile en son v142 derleme araçları için C++ ATL (ARM64EC-deneysel) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. ATL. Spectre | Spectre azaltmaları ile en son v142 derleme araçları için C++ ATL (x86 & x64) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. ATLMFC. Spectre | Spectre azaltmaları ile en son v142 derleme araçları için C++ MFC (x86 & x64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. MFC. ARM | En son v142 derleme araçları (ARM) için C++ MFC | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. MFC. ARM. Spectre | Spectre azaltmaları (ARM) ile en son v142 derleme araçları için C++ MFC | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. MFC. ARM64 | En son v142 derleme araçları için C++ MFC (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. MFC. ARM64. Spectre | Spectre azaltmaları ile en son v142 derleme araçları için C++ MFC (ARM64) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. MFC. ARM64EC | En son v142 derleme araçları için C++ MFC (ARM64EC-deneysel) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. MFC. ARM64EC. Spectre | Spectre azaltmaları ile en son v142 derleme araçları için C++ MFC (ARM64EC-deneysel) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. Redist. MSM | C++ 2019 yeniden dağıtılabilir MSMs | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. çalışma zamanları. ARM. Spectre | MSVC v142-VS 2019 C++ ARM Spectre-azaltılan lıbs (en son) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. çalışma zamanları. ARM64. Spectre | MSVC v142-VS 2019 C++ ARM64 Spectre-azaltılan lıbs (en son) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. çalışma zamanları. ARM64EC. Spectre | MSVC v142-VS 2019 C++ ARM64EC Spectre-azaltılan lıbs (en son-deneysel) | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. çalışma zamanları. x86. x64. Spectre | MSVC v142-VS 2019 C++ x64/x86 Spectre-azaltıllıbs (en son)  | 16.10.31205.252
Microsoft. VisualStudio. Component. VC. v141. ARM. Spectre | MSVC v141-VS 2017 C++ ARM Spectre-azaltılan lıbs (v 14.16) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. v141. ARM64. Spectre | MSVC v141-VS 2017 C++ ARM64 Spectre-azaltılan lıbs (v 14.16) | 16.5.29515.121
Microsoft. VisualStudio. Component. VC. v141. ATL | V141 derleme araçları için C++ ATL (x86 & x64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. ATL. ARM | V141 derleme araçları (ARM) için C++ ATL | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. ATL. ARM. Spectre | Spectre azaltmaları ile v141 derleme araçları için C++ ATL (ARM) | 16.5.29721.120
Microsoft. VisualStudio. Component. VC. v141. ATL. ARM64 | V141 derleme araçları için C++ ATL (ARM64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. ATL. ARM64. Spectre | Spectre azaltmaları ile v141 derleme araçları için C++ ATL (ARM64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. ATL. Spectre | Spectre azaltmaları ile v141 derleme araçları için C++ ATL (x86 & x64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. CLı. support | V141 derleme araçları için C++/CLı desteği (14,16) | 16.3.29207.166
Microsoft. VisualStudio. Component. VC. v141. MFC | V141 derleme araçları için C++ MFC (x86 & x64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. MFC. ARM | V141 derleme araçları (ARM) için C++ MFC | 16.2.28915.88
Microsoft. VisualStudio. Component. VC. v141. MFC. ARM. Spectre | Spectre azaltmaları (ARM) ile v141 derleme araçları için C++ MFC | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. MFC. ARM64 | V141 derleme araçları için C++ MFC (ARM64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. MFC. ARM64. Spectre | Spectre azaltmaları ile v141 derleme araçları için C++ MFC (ARM64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. MFC. Spectre | Spectre azaltmaları ile v141 derleme araçları için C++ MFC (x86 & x64) | 16.0.28625.61
Microsoft. VisualStudio. Component. VC. v141. x86. x64. Spectre | MSVC v141-VS 2017 C++ x64/x86 Spectre-azaltıllıbs (v 14.16) | 16.5.29515.121
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 16.0.28707.177
Microsoft. VisualStudio. Component. Windows10SDK. 20348 | Windows 10 SDK (10.0.20348.0) | 16.11.31603.221
Microsoft. VisualStudio. Component. WinXP | VS 2017 (v141) araçları için C++ Windows XP desteği [kullanım dışı] | 16.10.31205.252
Microsoft. VisualStudio. Web. Mvc4. ComponentGroup | ASP.NET MVC 4 | 16.10.31205.180
