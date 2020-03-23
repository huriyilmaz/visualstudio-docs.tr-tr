---
title: Visual Studio Enterprise 2019 iş yükü ve bileşen ilikleri
titleSuffix: ''
description: Komut satırını kullanarak Visual Studio'yu yüklemek veya VSIX bildiriminde bağımlılık olarak belirtmek için iş yükünü ve bileşen bilgisayarlarını kullanın
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 5844e30a9ca1f73026ed86f45dd8eb3d8842594f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437650"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-enterprise-2019"></a>Visual Studio çekirdek editörü (Visual Studio Enterprise 2019 ile birlikte)

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.CoreEditor

**Açıklama:** Sözdizime duyarlı kod düzenleme, kaynak kodu denetimi ve iş öğesi yönetimi de dahil olmak üzere Visual Studio çekirdek kabuk deneyimi.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio çekirdek editörü | 16.1.28811.260 | Gerekli
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | C++ Kullanıcıları için Visual Studio Başlangıç Sayfası | 16.0.28315.86 | İsteğe bağlı

## <a name="azure-development"></a>Azure geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.Azure

**Açıklama:** .NET Core ve .NET Framework'u kullanarak bulut uygulamaları geliştirmek ve kaynak oluşturmak için Azure SDK'ları, araçları ve projeleri. Docker desteği de dahil olmak üzere uygulamanızı kapsayıcıhale getirmek için araçlar da içerir.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jilet Dil Hizmetleri | 16.0.28714.129 | Gerekli
Component.Microsoft.VisualStudio.Web.Azure Fonksiyonları | Azure Webİşler Araçları | 16.0.28714.129 | Gerekli
Component.Microsoft.Web.LibraryManager | Kitaplık Yöneticisi | 16.0.28315.86 | Gerekli
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft.NetCore.Component.DevelopmentTools | .NET Çekirdek geliştirme araçları | 16.5.29721.120 | Gerekli
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Çalışma Süresi | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.Web | .NET Çekirdek geliştirme araçları | 16.5.29721.120 | Gerekli
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Yazma Araçları | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET için azure kitaplıkları | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure İşlem Emülatör | 16.1.28810.153 | Gerekli
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | Gerekli
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.FSharp | F# dil desteği | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web projeleri için F# dil desteği | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.IISExpress | IIS Ekspresi  | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılama | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.5.29721.120 | Gerekli
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Yönetilen Masaüstü İş Yükü Çekirdeği | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | Gerekli
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server desteği için veri kaynakları | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Veri Araçları | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Gerekli
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Azure.Ön Koşullar | Azure geliştirme ön koşulları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Azure İşlevler | Azure Webİşler Araçları | 16.0.28621.142 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları ön koşulları | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | Gerekli
Microsoft.Component.Azure.DataLake.Tools | Azure Veri Gölü ve Akış Analizi Araçları | 16.5.29721.120 | Önerilen
Microsoft.Net.Component.4.5.1.Hedefleme Paketi | .NET Framework 4.5.1 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.6.Hedefleme Paketi | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 geliştirme araçları | 16.0.28516.191 | Önerilen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 LTS Çalışma Süresi | 16.5.29905.7 | Önerilen
Microsoft.VisualStudio.Component.AspNet45 | Gelişmiş ASP.NET özellikleri | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Kubernetes için Visual Studio Araçları | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Azure.Powershell | Azure PowerShell | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Kaynak Yöneticisi temel araçları | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric Araçları | 16.4.29313.120 | Önerilen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Bulut Hizmetleri temel araçları | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Bulut Hizmetleri oluşturma araçları | 16.3.29207.166 | Önerilen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Anlık Görüntü Hata Ayıklayıcı | 16.5.29813.82 | Önerilen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Zaman Yolculuğu Hata Ayıklama | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Bulut Hizmetleri araçları | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Kaynak Yöneticisi araçları | 16.0.28528.71 | Önerilen
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.1.Hedefleme Paketi | .NET Framework 4.7.1 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.Hedefleme Paketi | .NET Framework 4.7 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.8.Hedefleme Paketi | .NET Framework 4.8 hedefleme paketi | 16.4.29313.120 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 geliştirme araçları | 16.4.29318.151 | İsteğe bağlı
Microsoft.VisualStudio.Component.Azure.Depolama.AzCopy | Azure Depolama Azcopy | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | İsteğe bağlı

## <a name="data-storage-and-processing"></a>Veri depolama ve işleme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.Data

**Açıklama:** SQL Server, Azure Veri Gölü veya Hadoop ile veri çözümlerini bağlayın, geliştirin ve test edin.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jilet Dil Hizmetleri | 16.0.28714.129 | Önerilen
Component.Microsoft.Web.LibraryManager | Kitaplık Yöneticisi | 16.0.28315.86 | Önerilen
Microsoft.Component.Azure.DataLake.Tools | Azure Veri Gölü ve Akış Analizi Araçları | 16.5.29721.120 | Önerilen
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Önerilen
Microsoft.Net.Component.4.5.1.Hedefleme Paketi | .NET Framework 4.5.1 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.6.Hedefleme Paketi | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | Önerilen
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Önerilen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 geliştirme araçları | 16.0.28516.191 | Önerilen
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Çalışma Süresi | 16.5.29905.7 | Önerilen
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Önerilen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Yazma Araçları | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET için azure kitaplıkları | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure İşlem Emülatör | 16.1.28810.153 | Önerilen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | Önerilen
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Bulut Hizmetleri temel araçları | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Bulut Hizmetleri oluşturma araçları | 16.3.29207.166 | Önerilen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.IISExpress | IIS Ekspresi  | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılama | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.5.29721.120 | Önerilen
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Yönetilen Masaüstü İş Yükü Çekirdeği | 16.4.29318.151 | Önerilen
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | Önerilen
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Önerilen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Önerilen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server desteği için veri kaynakları | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Veri Araçları | 16.3.29207.166 | Önerilen
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Önerilen
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları ön koşulları | 16.4.29318.151 | Önerilen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | Önerilen
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.FSharp.Desktop | F# masaüstü dil desteği | 16.0.28315.86 | İsteğe bağlı

## <a name="data-science-and-analytical-applications"></a>Veri bilimi ve analitik uygulamalar

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.DataScience

**Açıklama:** Python ve F# dahil olmak üzere veri bilimi uygulamaları oluşturmak için diller ve araçlar.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Component.PythonTools | Python dil desteği | 16.5.29515.121 | Önerilen
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | Önerilen
Microsoft.Component.PythonTools.Web | Python web desteği | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.FSharp.Desktop | F# masaüstü dil desteği | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.5.29721.120 | Önerilen
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Önerilen
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Önerilen
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Önerilen
Microsoft.VisualStudio.Component.WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | Önerilen
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python yerel geliştirme araçları | 16.2.29020.229 | İsteğe bağlı
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX için grafik hata ayıklayıcı ve GPU profil oluşturucu | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ profil oluşturma araçları | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.25) | 16.5.29721.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Çalışma Zamanı | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | İsteğe bağlı

## <a name="net-desktop-development"></a>.NET masaüstü geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Açıklama:** .NET Core ve .NET Framework ile C#, Visual Basic ve F# kullanarak WPF, Windows Formları ve konsol uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Çalışma Süresi | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Yönetilen Masaüstü İş Yükü Çekirdeği | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.Component.ManagedDesktop.Ön Koşullar | .NET masaüstü geliştirme araçları | 16.5.29514.35 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | Gerekli
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Önerilen
Microsoft.ComponentGroup.Blend | Visual Studio için Blend | 16.0.28315.86 | Önerilen
Microsoft.Net.Component.4.5.1.Hedefleme Paketi | .NET Framework 4.5.1 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.6.Hedefleme Paketi | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 geliştirme araçları | 16.0.28516.191 | Önerilen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 LTS Çalışma Süresi | 16.5.29905.7 | Önerilen
Microsoft.NetCore.Component.DevelopmentTools | .NET Çekirdek geliştirme araçları | 16.5.29721.120 | Önerilen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Tam Zamanında hata ayıklama | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.EntityFramework | Varlık Çerçevesi 6 araçları | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.FSharp | F# dil desteği | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Önerilen
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Önerilen
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | İsteğe bağlı
Component.Microsoft.VisualStudio.RazorExtension | Jilet Dil Hizmetleri | 16.0.28714.129 | İsteğe bağlı
Component.Microsoft.Web.LibraryManager | Kitaplık Yöneticisi | 16.0.28315.86 | İsteğe bağlı
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.1.Hedefleme Paketi | .NET Framework 4.7.1 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.Hedefleme Paketi | .NET Framework 4.7 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.8.Hedefleme Paketi | .NET Framework 4.8 hedefleme paketi | 16.4.29313.120 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 geliştirme araçları | 16.4.29318.151 | İsteğe bağlı
Microsoft.VisualStudio.Component.ClassDesigner | Sınıf Tasarımcısı | 16.0.28528.71 | İsteğe bağlı
Microsoft.VisualStudio.Component.CodeClone | Kod Klon | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.CodeMap | Kod Haritası | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Canlı Bağımlılık Doğrulama | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.FSharp.Desktop | F# masaüstü dil desteği | 16.0.28315.86 | İsteğe bağlı
Microsoft.VisualStudio.Component.GraphDocument | DGML editörü | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.IISExpress | IIS Ekspresi  | 16.0.28315.86 | İsteğe bağlı
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılama | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.5.29721.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | İsteğe bağlı
Microsoft.VisualStudio.Component.PortableLibrary | .NET Taşınabilir Kütüphane hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server desteği için veri kaynakları | 16.0.28315.86 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Veri Araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | İsteğe bağlı
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Mimarlık ve analiz araçları | 16.5.29514.35 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | MSIX Paketleme Araçları | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları ön koşulları | 16.4.29318.151 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | İsteğe bağlı

## <a name="game-development-with-unity"></a>Unity ile oyun geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.ManagedGame

**Açıklama:** Güçlü bir platform ötesi geliştirme ortamı olan Unity ile 2D ve 3D oyunlar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 geliştirme araçları | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.1.Hedefleme Paketi | .NET Framework 4.7.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.Unity | Unity için Visual Studio Araçları | 16.0.28315.86 | Gerekli
Component.UnityEngine.x64 | Unity 2019.2 64-bit Editör | 16.5.29515.121 | Önerilen
Component.UnityEngine.x86 | Unity 5.6 32-bit Editör | 16.1.28811.260 | Önerilen

## <a name="linux-development-with-c"></a>C++ ile Linux geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Açıklama:** Linux ortamında çalışan uygulamalar oluşturun ve hata ayıklayın.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Bileşen.MDD.Linux | Linux Geliştirme için C++ | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.0.28625.61 | Gerekli
Component.Linux.CMake | Linux için C++ CMake araçları | 16.2.29003.222 | Önerilen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | Önerilen
Bileşen.MDD.Linux.GCC.arm | Gömülü ve IoT geliştirme araçları | 16.5.29515.121 | İsteğe bağlı

## <a name="desktop-development-with-c"></a>C++ ile masaüstü geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.NativeDesktop

**Açıklama:** MSVC, Clang, CMake veya MSBuild gibi seçtiğiniz araçları kullanarak Windows için modern C++ uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.ClassDesigner | Sınıf Tasarımcısı | 16.0.28528.71 | Gerekli
Microsoft.VisualStudio.Component.CodeMap | Kod Haritası | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.GraphDocument | DGML editörü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.VC.Redist.14.Son | C++ 2019 Yeniden Dağıtılabilir Güncelleştirme | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | C++ için mimari araçlar | 16.0.28621.142 | Gerekli
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++ çekirdek masaüstü özellikleri | 16.2.29012.281 | Gerekli
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Önerilen
Microsoft.VisualStudio.Component.Debugger.JustInTime | Tam Zamanında hata ayıklama | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX için grafik hata ayıklayıcı ve GPU profil oluşturucu | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Önerilen
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer (Deneysel) | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.VC.ATL | En son v142 yapı araçları için C++ ATL (x86 & x64) | 16.4.29313.120 | Önerilen
Microsoft.VisualStudio.Component.VC.CMake.Project | C++ CWindows için araçlar yapın | 16.3.29103.31 | Önerilen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ profil oluşturma araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Boost.Test için Test Adaptörü | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Google Test için Test Adaptörü | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.25) | 16.5.29721.120 | Önerilen
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Önerilen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.CMake | JSON düzenleyicisi | 16.3.29207.166 | Önerilen
Component.Incredibuild | IncrediBuild - Yapı İvme | 16.5.29721.120 | İsteğe bağlı
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | İsteğe bağlı
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | İsteğe bağlı
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılama | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ yapı araçları (v14.00) | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.ATLMFC | En son v142 oluşturma araçları için C++ MFC (x86 & x64) | 16.4.29313.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.CLI.Support | V142 yapı araçları için C++/CLI desteği (14,25) | 16.5.29721.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Windows için C++ Clang Derleyicisi (9.0.0) | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | V142 yapı araçları için C++ Clang-cl (x64/x86) | 16.3.29207.166 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | V142 yapı araçları için C++ Modülleri (x64/x86 – deneysel) | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 yapı araçları (v14.16) | 16.1.28829.92 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | Windows için C++ Clang araçları (9.0.0 - x64/x86) | 16.5.29514.35 | İsteğe bağlı

## <a name="game-development-with-c"></a>C++ ile oyun geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.NativeGame

**Açıklama:** DirectX, Unreal veya Cocos2d tarafından desteklenen profesyonel oyunlar oluşturmak için C++'ın tüm gücünü kullanın.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.VC.Redist.14.Son | C++ 2019 Yeniden Dağıtılabilir Güncelleştirme | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.25) | 16.5.29721.120 | Gerekli
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Çalışma Zamanı | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX için grafik hata ayıklayıcı ve GPU profil oluşturucu | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer (Deneysel) | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ profil oluşturma araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Önerilen
Bileşen.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | İsteğe bağlı
Component.Android.SDK25.Private | Android SDK kurulumu (API level 25) (C++ile Mobil geliştirme için yerel yükleme) | 16.0.28625.61 | İsteğe bağlı
Component.Ant | Apaçi Karınca (1.9.3) | 1.9.3.8 | İsteğe bağlı
Bileşen.Cocos | Cocos | 16.0.28315.86 | İsteğe bağlı
Component.Incredibuild | IncrediBuild - Yapı İvme | 16.5.29721.120 | İsteğe bağlı
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | İsteğe bağlı
Bileşen.MDD.Android | C++ Android geliştirme araçları | 16.0.28517.75 | İsteğe bağlı
Bileşen.OpenJDK | OpenJDK (Microsoft dağıtımı) | 16.1.28811.260 | İsteğe bağlı
Component.Unreal | Unreal Motor yükleyici | 16.1.28810.153 | İsteğe bağlı
Component.Unreal.Android | Unreal motoru için Android IDE desteği | 16.1.28810.153 | İsteğe bağlı
Microsoft.Net.Component.4.5.1.Hedefleme Paketi | .NET Framework 4.5.1 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.6.Hedefleme Paketi | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | İsteğe bağlı
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 geliştirme araçları | 16.0.28516.191 | İsteğe bağlı
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet hedefleri ve oluşturma görevleri | 16.1.28829.92 | İsteğe bağlı
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | İsteğe bağlı
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | İsteğe bağlı

## <a name="mobile-development-with-c"></a>C++ ile mobil geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.NativeMobile

**Açıklama:** C++'ı kullanarak iOS, Android veya Windows için çapraz platform uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.Android.SDK25.Private | Android SDK kurulumu (API level 25) (C++ile Mobil geliştirme için yerel yükleme) | 16.0.28625.61 | Gerekli
Bileşen.OpenJDK | OpenJDK (Microsoft dağıtımı) | 16.1.28811.260 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.0.28625.61 | Gerekli
Bileşen.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | Önerilen
Component.Ant | Apaçi Karınca (1.9.3) | 1.9.3.8 | Önerilen
Bileşen.MDD.Android | C++ Android geliştirme araçları | 16.0.28517.75 | Önerilen
Bileşen.Android.NDK.R16B_3264 | Android NDK (R16B) (32bit) | 16.5.29916.74 | İsteğe bağlı
Component.Google.Android.Emulator.API25.Private | Google Android Emülatörü (API Level 25) (yerel yükleme) | 16.1.28810.153 | İsteğe bağlı
Component.HAXM.Private | Intel Donanım Hızlandırılmış Yürütme Yöneticisi (HAXM) (yerel yükleme) | 16.0.28528.71 | İsteğe bağlı
Component.Incredibuild | IncrediBuild - Yapı İvme | 16.5.29721.120 | İsteğe bağlı
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | İsteğe bağlı
Bileşen.MDD.IOS | C++ iOS geliştirme araçları | 16.0.28517.75 | İsteğe bağlı

## <a name="net-core-cross-platform-development"></a>.NET Core çoklu platform geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.NetCoreTools

**Açıklama:** .NET Core, ASP.NET Core, HTML/JavaScript ve Docker desteği de dahil olmak üzere Kapsayıcılar'ı kullanarak çapraz platform uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jilet Dil Hizmetleri | 16.0.28714.129 | Gerekli
Component.Microsoft.Web.LibraryManager | Kitaplık Yöneticisi | 16.0.28315.86 | Gerekli
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft.NetCore.Component.DevelopmentTools | .NET Çekirdek geliştirme araçları | 16.5.29721.120 | Gerekli
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Çalışma Süresi | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.Web | .NET Çekirdek geliştirme araçları | 16.5.29721.120 | Gerekli
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.FSharp | F# dil desteği | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web projeleri için F# dil desteği | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.IISExpress | IIS Ekspresi  | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılama | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.5.29721.120 | Gerekli
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Yönetilen Masaüstü İş Yükü Çekirdeği | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | Gerekli
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server desteği için veri kaynakları | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Veri Araçları | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları ön koşulları | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | Gerekli
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Önerilen
Component.Microsoft.VisualStudio.Web.Azure Fonksiyonları | Azure Webİşler Araçları | 16.0.28714.129 | Önerilen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 LTS Çalışma Süresi | 16.5.29905.7 | Önerilen
Microsoft.VisualStudio.Component.AppInsights.Tools | Geliştirici Analitik araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Yazma Araçları | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET için azure kitaplıkları | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure İşlem Emülatör | 16.1.28810.153 | Önerilen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | Önerilen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Anlık Görüntü Hata Ayıklayıcı | 16.5.29813.82 | Önerilen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Zaman Yolculuğu Hata Ayıklama | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Önerilen
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Azure İşlevler | Azure Webİşler Araçları | 16.0.28621.142 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Web geliştirme için bulut araçları | 16.2.29003.222 | Önerilen
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Geliştirme süresi IIS desteği | 16.0.28315.86 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | MSIX Paketleme Araçları | 16.4.29409.204 | İsteğe bağlı

## <a name="mobile-development-with-net"></a>.NET ile mobil geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Açıklama:** Xamarin kullanarak iOS, Android veya Windows için çapraz platform uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Bileşen.OpenJDK | OpenJDK (Microsoft dağıtımı) | 16.1.28811.260 | Gerekli
Bileşen.Xamarin | Xamarin | 16.5.29721.120 | Gerekli
Component.Xamarin.RemotedSimulator | Xamarin Uzaktan Simülatörü | 16.0.28315.86 | Gerekli
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft.NetCore.Component.DevelopmentTools | .NET Çekirdek geliştirme araçları | 16.5.29721.120 | Gerekli
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Çalışma Süresi | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Gerekli
Microsoft.VisualStudio.Component.FSharp | F# dil desteği | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.Merq | Ortak Xamarin iç araçları | 16.2.29012.281 | Gerekli
Microsoft.VisualStudio.Component.MonoDebugger | Mono hata ayıklama | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | ASP.NET cazip motor | 16.0.28315.86 | Gerekli
Bileşen.Android.SDK28 | Android SDK kurulumu (API seviye 28) | 16.2.29003.222 | Önerilen

## <a name="aspnet-and-web-development"></a>ASP.NET ve web geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.NetWeb

**Açıklama:** Docker desteği de dahil olmak üzere ASP.NET Core, ASP.NET, HTML/JavaScript ve Konteynerler'i kullanarak web uygulamaları oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jilet Dil Hizmetleri | 16.0.28714.129 | Gerekli
Component.Microsoft.Web.LibraryManager | Kitaplık Yöneticisi | 16.0.28315.86 | Gerekli
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft.NetCore.Component.DevelopmentTools | .NET Çekirdek geliştirme araçları | 16.5.29721.120 | Gerekli
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Çalışma Süresi | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.Web | .NET Çekirdek geliştirme araçları | 16.5.29721.120 | Gerekli
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.FSharp | F# dil desteği | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Web projeleri için F# dil desteği | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.IISExpress | IIS Ekspresi  | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılama | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.5.29721.120 | Gerekli
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Yönetilen Masaüstü İş Yükü Çekirdeği | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | Gerekli
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server desteği için veri kaynakları | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Veri Araçları | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Gerekli
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları ön koşulları | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | Gerekli
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Önerilen
Component.Microsoft.VisualStudio.Web.Azure Fonksiyonları | Azure Webİşler Araçları | 16.0.28714.129 | Önerilen
Microsoft.Net.Component.4.5.1.Hedefleme Paketi | .NET Framework 4.5.1 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.6.Hedefleme Paketi | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.0.28517.75 | Önerilen
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 geliştirme araçları | 16.0.28516.191 | Önerilen
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 LTS Çalışma Süresi | 16.5.29905.7 | Önerilen
Microsoft.VisualStudio.Component.AppInsights.Tools | Geliştirici Analitik araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.AspNet45 | Gelişmiş ASP.NET özellikleri | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Yazma Araçları | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET için azure kitaplıkları | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure İşlem Emülatör | 16.1.28810.153 | Önerilen
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | Önerilen
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Önerilen
Microsoft.VisualStudio.Component.Debugger.Snapshot | Anlık Görüntü Hata Ayıklayıcı | 16.5.29813.82 | Önerilen
Microsoft.VisualStudio.Component.Debugger.TimeTravel | Zaman Yolculuğu Hata Ayıklama | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.EntityFramework | Varlık Çerçevesi 6 araçları | 16.0.28315.86 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 16.1.28811.260 | Önerilen
Microsoft.VisualStudio.Component.WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Azure İşlevler | Azure Webİşler Araçları | 16.0.28621.142 | Önerilen
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Web geliştirme için bulut araçları | 16.2.29003.222 | Önerilen
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.1.Hedefleme Paketi | .NET Framework 4.7.1 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.Hedefleme Paketi | .NET Framework 4.7 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.8.Hedefleme Paketi | .NET Framework 4.8 hedefleme paketi | 16.4.29313.120 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 geliştirme araçları | 16.4.29318.151 | İsteğe bağlı
Microsoft.VisualStudio.Component.ClassDesigner | Sınıf Tasarımcısı | 16.0.28528.71 | İsteğe bağlı
Microsoft.VisualStudio.Component.CodeClone | Kod Klon | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.CodeMap | Kod Haritası | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Canlı Bağımlılık Doğrulama | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.GraphDocument | DGML editörü | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.TestTools.WebLoadTest | Web performansı ve yük test araçları | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Ek proje şablonları (önceki sürümler) | 16.0.28621.142 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Mimarlık ve analiz araçları | 16.5.29514.35 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Geliştirme süresi IIS desteği | 16.0.28315.86 | İsteğe bağlı

## <a name="nodejs-development"></a>Düğüm.js geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.Node

**Açıklama:** Asynchronous event-driven JavaScript çalışma süresi olan Node.js kullanarak ölçeklenebilir ağ uygulamaları oluşturun. 

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılama | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.5.29721.120 | Gerekli
Microsoft.VisualStudio.Component.Node.Tools | Düğüm.js geliştirme araçları | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Gerekli
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | Gerekli
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Önerilen
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Önerilen
Microsoft.VisualStudio.Component.WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.AppInsights.Tools | Geliştirici Analitik araçları | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.25) | 16.5.29721.120 | İsteğe bağlı

## <a name="officesharepoint-development"></a>Office/SharePoint geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.Office

**Açıklama:** C#, VB ve JavaScript kullanarak Office ve SharePoint eklentileri, SharePoint çözümleri ve VSTO eklentileri oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Jilet Dil Hizmetleri | 16.0.28714.129 | Gerekli
Component.Microsoft.Web.LibraryManager | Kitaplık Yöneticisi | 16.0.28315.86 | Gerekli
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Çalışma Süresi | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Gerekli
Microsoft.VisualStudio.Component.AppInsights.Tools | Geliştirici Analitik araçları | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.IISExpress | IIS Ekspresi  | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılama | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.5.29721.120 | Gerekli
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Yönetilen Masaüstü İş Yükü Çekirdeği | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.Component.ManagedDesktop.Ön Koşullar | .NET masaüstü geliştirme araçları | 16.5.29514.35 | Gerekli
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | Gerekli
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.Sharepoint.Tools | Visual Studio için Office Geliştirici Araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server desteği için veri kaynakları | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Veri Araçları | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Gerekli
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Gerekli
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.İş Akışı | Windows Workflow Foundation | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları ön koşulları | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | Gerekli
Microsoft.VisualStudio.Component.TeamOffice | Ofis için Görsel Stüdyo Araçları (VSTO) | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.1.Hedefleme Paketi | .NET Framework 4.7.1 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.Hedefleme Paketi | .NET Framework 4.7 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.8.Hedefleme Paketi | .NET Framework 4.8 hedefleme paketi | 16.4.29313.120 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 geliştirme araçları | 16.4.29318.151 | İsteğe bağlı
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | İsteğe bağlı

## <a name="python-development"></a>Python geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.Python

**Açıklama:** Python için düzenleme, hata ayıklama, etkileşimli geliştirme ve kaynak denetimi.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Component.PythonTools | Python dil desteği | 16.5.29515.121 | Gerekli
Bileşen.CPython3.x64 | Python 3 64-bit (3.7.5) | 3.7.5 | Önerilen
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Önerilen
Microsoft.Component.PythonTools.Minicondax64 | Python miniconda | 16.2.29003.222 | Önerilen
Microsoft.Component.PythonTools.Web | Python web desteği | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 16.4.29409.204 | Önerilen
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript ve TypeScript dil desteği | 16.5.29721.120 | Önerilen
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Önerilen
Microsoft.VisualStudio.Component.WebDeploy | Web Dağıtımı | 16.0.28517.75 | Önerilen
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET ve web geliştirme | 16.0.28621.142 | Önerilen
Bileşen.CPython2.x64 | Python 2 64-bit (2.7.16) | 2.7.16 | İsteğe bağlı
Bileşen.CPython2.x86 | Python 2 32-bit (2.7.16) | 2.7.16 | İsteğe bağlı
Bileşen.CPython3.x86 | Python 3 32-bit (3.7.5) | 3.7.5 | İsteğe bağlı
Component.Microsoft.VisualStudio.RazorExtension | Jilet Dil Hizmetleri | 16.0.28714.129 | İsteğe bağlı
Component.Microsoft.Web.LibraryManager | Kitaplık Yöneticisi | 16.0.28315.86 | İsteğe bağlı
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | İsteğe bağlı
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python yerel geliştirme araçları | 16.2.29020.229 | İsteğe bağlı
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | İsteğe bağlı
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | İsteğe bağlı
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Çalışma Süresi | 16.5.29905.7 | İsteğe bağlı
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | İsteğe bağlı
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Yazma Araçları | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET için azure kitaplıkları | 16.0.28315.86 | İsteğe bağlı
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure İşlem Emülatör | 16.1.28810.153 | İsteğe bağlı
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage Öykünücüsü | 16.4.29313.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Bulut Hizmetleri temel araçları | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Bulut Hizmetleri oluşturma araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.VisualStudio.Component.DockerTools | Kapsayıcı geliştirme araçları | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX için grafik hata ayıklayıcı ve GPU profil oluşturucu | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.IISExpress | IIS Ekspresi  | 16.0.28315.86 | İsteğe bağlı
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript tanılama | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Yönetilen Masaüstü İş Yükü Çekirdeği | 16.4.29318.151 | İsteğe bağlı
Microsoft.VisualStudio.Component.MSODBC.SQL | SQL Server ODBC Sürücüsü | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Komut Satırı Yardımcı Programları | 16.0.28707.177 | İsteğe bağlı
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | İsteğe bağlı
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | İsteğe bağlı
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL çalışma zamanı | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server desteği için veri kaynakları | 16.0.28315.86 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Veri Araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ profil oluşturma araçları | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.25) | 16.5.29721.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.Web | ASP.NET ve web geliştirme araçları | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Çalışma Zamanı | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.Web | ASP.NET ve web geliştirme araçları ön koşulları | 16.4.29318.151 | İsteğe bağlı

## <a name="universal-windows-platform-development"></a>Evrensel Windows Platformu geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.Universal

**Açıklama:** C#, VB veya isteğe bağlı C++ içeren Evrensel Windows Platformu için uygulamalar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Yerel | 16.5.29515.121 | Gerekli
Microsoft.ComponentGroup.Blend | Visual Studio için Blend | 16.0.28315.86 | Gerekli
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS Çalışma Süresi | 16.5.29905.7 | Gerekli
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Gerekli
Microsoft.VisualStudio.Component.AppInsights.Tools | Geliştirici Analitik araçları | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.Graphics | Resim ve 3B model editörleri | 16.0.28517.75 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server için CLR veri türleri | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | MSIX Paketleme Araçları | 16.4.29409.204 | Gerekli
Microsoft.visualstudio.componentgroup.uWP.netcoreandstandard | .NET Yerli ve .NET Standardı | 16.3.29102.218 | Gerekli
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Evrensel Windows Platformu araçları | 16.4.29409.204 | Gerekli
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Xamarin için Evrensel Windows Platformu araçları | 16.5.29514.35 | Gerekli
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | İsteğe bağlı
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.ClassDesigner | Sınıf Tasarımcısı | 16.0.28528.71 | İsteğe bağlı
Microsoft.VisualStudio.Component.CodeClone | Kod Klon | 16.4.29409.204 | İsteğe bağlı
Microsoft.VisualStudio.Component.CodeMap | Kod Haritası | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Canlı Bağımlılık Doğrulama | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.GraphDocument | DGML editörü | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX için grafik hata ayıklayıcı ve GPU profil oluşturucu | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | V142 yapı araçları için C++ Evrensel Windows Platformu desteği (ARM64) | 16.3.29207.166 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.CoreIde | C++ temel özellikleri | 16.0.28625.61 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Redist.14.Son | C++ 2019 Yeniden Dağıtılabilir Güncelleştirme | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 - VS 2019 C++ ARM yapı araçları (v14.25) | 16.5.29721.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 - VS 2019 C++ ARM64 yapı araçları (v14.25) | 16.5.29721.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.25) | 16.5.29721.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ ARM yapı araçları (v14.16) | 16.2.29003.222 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ ARM64 yapı araçları (v14.16) | 16.1.28829.92 | İsteğe bağlı
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ x64/x86 yapı araçları (v14.16) | 16.1.28829.92 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 Önizleme SDK (10.0.19041.0) | 16.5.29721.120 | İsteğe bağlı
Microsoft.VisualStudio.Component.Windows10SDK.ipoverUsb | USB Aygıt Bağlantısı | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Mimarlık ve analiz araçları | 16.5.29514.35 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | C++ için mimari araçlar | 16.0.28621.142 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | C++ çekirdek masaüstü özellikleri | 16.2.29012.281 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ (v142) Evrensel Windows Platformu araçları | 16.3.29207.166 | İsteğe bağlı
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | C++ (v141) Evrensel Windows Platformu araçları | 16.1.28810.153 | İsteğe bağlı

## <a name="visual-studio-extension-development"></a>Visual Studio uzantısı geliştirme

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.visualStudioExtension

**Açıklama:** Visual Studio için yeni komutlar, kod çözümleyicileri ve araç pencereleri dahil olmak üzere eklentiler ve uzantılar oluşturun.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Gerekli
Microsoft.Net.Component.4.6.Hedefleme Paketi | .NET Framework 4.6 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.7.2.Hedefleme Paketi | .NET Framework 4.7.2 hedefleme paketi | 16.0.28517.75 | Gerekli
Microsoft.Net.Component.4.8.SDK | .NET Çerçeve 4.8 SDK | 16.4.29313.120 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.7.2 geliştirme araçları | 16.3.29207.166 | Gerekli
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Gerekli
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 16.1.28829.92 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 16.0.28714.129 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 16.5.29515.121 | Gerekli
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Gerekli
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Ön Koşullar | Visual Studio uzantı geliştirme ön koşulları | 16.4.29318.151 | Gerekli
Microsoft.VisualStudio.Component.DiagnosticTools | .NET profil oluşturma araçları | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | 16.5.29515.121 | Önerilen
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 16.0.28625.61 | Önerilen
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK’sı | 16.2.29003.222 | İsteğe bağlı
Microsoft.VisualStudio.Component.AppInsights.Tools | Geliştirici Analitik araçları | 16.5.29515.121 | İsteğe bağlı
Microsoft.VisualStudio.Component.DslTools | Modelleme SDK | 16.0.28315.86 | İsteğe bağlı

## <a name="unaffiliated-components"></a>Bağlı olmayan bileşenler

Bunlar, iş yüküne dahil olmayan, ancak tek bir bileşen olarak seçilebilen bileşenlerdir.

Bileşen Kimliği | Adı | Sürüm
--- | --- | ---
Component.GitHub.VisualStudio | Visual Studio için GitHub uzantısı | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | ClickOnce Yayıncılık | 16.4.29409.204
Microsoft.Component.HelpViewer | Yardım Görüntüleyici | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | .NET Çerçeve 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Çerçeve 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Çerçeve 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Çerçeve 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Çerçeve 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2 Çalışma Zamanı (EOL) | 16.5.29813.82
Microsoft.Net.Core.Component.SDK.3.0 | .NET Core 3.0 Çalışma Süresi (EOL) | 16.5.29905.7
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Geliştirme Araçları artı .NET Core 2.1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Web Geliştirme Araçları artı .NET Core 2.1 | 16.3.29207.166
Microsoft.VisualStudio.Component.AzureDevops.OfficeIntegration | Azure Devops Ofis Tümleştirmesi | 16.0.28625.61
Microsoft.VisualStudio.Component.Debugger.VSOnline | Visual Studio Online Ortamlar için Debugger | 16.5.29813.82
Microsoft.VisualStudio.Component.Git | Windows için Git | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL araçları | 16.0.28625.61
Microsoft.VisualStudio.Component.TestTools.CodedUITest | Kodlanmış UI testi | 16.0.28327.66
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ ARM yapı araçları (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre azaltıcı libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ ARM64 yapı araçları (v14.20) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre azaltıcı libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | V142 yapı araçları için C++ v14,20 ATL (x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | V142 yapı araçları için C++ v14.20 ATL (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.20 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | V142 yapı araçları için C++ v14.20 ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | C++ v14.20 Spectre Azaltma lı v142 yapı araçları için ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | C++ v14.20 Spectre Azaltma lı v142 yapı araçları için ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | V142 yapı araçları için C++/CLI desteği (14,20) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.20.MFC | V142 yapı araçları için C++ v14.20 MFC (x86 & x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | V142 yapı araçları için C++ v14.20 MFC (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.20 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | V142 yapı araçları için C++ v14.20 MFC (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | Spectre Azaltma (ARM64) ile v142 yapı araçları için C++ v14.20 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | C++ v14.20 MFC, Spectre Azaltma lı v142 yapı araçları için (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre azaltılmış libs (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 - VS 2019 C++ ARM yapı araçları (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre azaltıcı libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 - VS 2019 C++ ARM64 yapı araçları (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre azaltıcı libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | V142 yapı araçları için C++ v14.21 ATL (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | V142 yapı araçları için C++ v14.21 ATL (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.21 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | V142 yapı araçları için C++ v14.21 ATL (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | Spectre Azaltma (ARM64) ile v142 yapı araçları için C++ v14.21 ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | Spectre Azaltma lı v142 yapı araçları için C++ v14.21 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | V142 yapı araçları için C++/CLI desteği (14,21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | V142 yapı araçları için C++ v14.21 MFC (x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | V142 yapı araçları için C++ v14.21 MFC (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.21 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | V142 yapı araçları için C++ v14.21 MFC (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | Spectre Azaltma (ARM64) ile v142 yapı araçları için C++ v14.21 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | C++ v14.21 MFC, Spectre Azaltma lı v142 yapı araçları için (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre azaltılmış libs (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC v142 - VS 2019 C++ ARM yapı araçları (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre azaltıcı libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 - VS 2019 C++ ARM64 yapı araçları (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre azaltıcı libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | V142 yapı araçları için C++ v14.22 ATL (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | V142 yapı araçları için C++ v14.22 ATL (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.22 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | V142 yapı araçları için C++ v14.22 ATL (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | C++ v14.22 Spectre Azaltma lı v142 yapı araçları için ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | C++ v14.22 Spectre Azaltma lı v142 yapı araçları için ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | V142 yapı araçları için C++/CLI desteği (14,22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC | V142 yapı araçları için C++ v14.22 MFC (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | V142 yapı araçları için C++ v14.22 MFC (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.22 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | V142 yapı araçları için C++ v14.22 MFC (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | Spectre Azaltma (ARM64) ile v142 yapı araçları için C++ v14.22 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | Spectre Azaltma lı v142 yapı araçları için C++ v14.22 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre azaltılmış libs (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 - VS 2019 C++ ARM yapı araçları (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre azaltıcı libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC v142 - VS 2019 C++ ARM64 yapı araçları (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre azaltıcı libs (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | V142 yapı araçları için C++ v14.23 ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | V142 yapı araçları için C++ v14.23 ATL (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.23 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | V142 yapı araçları için C++ v14.23 ATL (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | Spectre Azaltma (ARM64) ile v142 yapı araçları için C++ v14.23 ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | C++ v14.23 Spectre Azaltma lı v142 yapı araçları için ATL (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | V142 yapı araçları için C++/CLI desteği (14,23) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.23.MFC | V142 yapı araçları için C++ v14.23 MFC (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | V142 yapı araçları için C++ v14.23 MFC (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.23 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | V142 yapı araçları için C++ v14.23 MFC (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | Spectre Azaltma (ARM64) ile v142 yapı araçları için C++ v14.23 MFC | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | C++ v14.23 MFC, Spectre Azaltma lı v142 yapı araçları için (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre azaltılmış libs (v14,23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC v142 - VS 2019 C++ ARM yapı araçları (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre azaltıcı libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64 | MSVC v142 - VS 2019 C++ ARM64 yapı araçları (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre azaltıcı libs (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | V142 yapı araçları için C++ v14,24 ATL (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | V142 yapı araçları için C++ v14.24 ATL (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.24 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | V142 yapı araçları için C++ v14.24 ATL (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | Spectre Azaltma (ARM64) ile v142 yapı araçları için C++ v14.24 ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | Spectre Azaltma lı v142 yapı araçları için C++ v14.24 ATL (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | V142 yapı araçları için C++/CLI desteği (14,24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC | V142 yapı araçları için C++ v14.24 MFC (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM | V142 yapı araçları için C++ v14.24 MFC (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM.Spectre | Spectre Azaltma (ARM) ile v142 yapı araçları için C++ v14.24 MFC | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64 | V142 yapı araçları için C++ v14.24 MFC (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64.Spectre | Spectre Azaltma (ARM64) ile v142 yapı araçları için C++ v14.24 MFC | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.Spectre | C++ v14.24 MFC, Spectre Azaltma lı v142 yapı araçları için (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 yapı araçları (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre azaltılmış libs (v14,24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM | En son v142 yapı araçları için C++ ATL (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Spectre Azaltma (ARM) ile en son v142 yapı araçları için C++ ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | En son v142 yapı araçları için C++ ATL (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Spectre Azaltma (ARM64) ile en son v142 yapı araçları için C++ ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Spectre Azaltma (x86 & x64) ile en son v142 yapı araçları için C++ ATL | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Spectre Azaltma (x86 & x64) ile en son v142 oluşturma araçları için C++ MFC | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | En son v142 yapı araçları için C++ MFC (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Spectre Azaltma (ARM) ile en son v142 yapı araçları için C++ MFC | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | En son v142 yapı araçları için C++ MFC (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Spectre Azaltma (ARM64) ile en son v142 yapı araçları için C++ MFC | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++ 2019 Yeniden Dağıtılabilir MSMs | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre azaltıcı libs (v14.25) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre azaltıcı libs (v14.25) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre azaltılmış libs (v14.25)  | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 - VS 2017 C++ ARM Spectre azaltıcı libs (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 - VS 2017 C++ ARM64 Spectre azaltıcı libs (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | V141 yapı araçları için C++ ATL (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | V141 yapı araçları için C++ ATL (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | Spectre Azaltma (ARM) ile v141 yapı araçları için C++ ATL | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | V141 yapı araçları için C++ ATL (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | Spectre Azaltma (ARM64) ile v141 yapı araçları için C++ ATL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | Spectre Azaltma (x86 & x64) ile v141 yapı araçları için C++ ATL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | V141 yapı araçları için C++/CLI desteği (14,16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | V141 yapı araçları için C++ MFC (x86 & x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | V141 yapı araçları için C++ MFC (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | Spectre Azaltma (ARM) ile v141 oluşturma araçları için C++ MFC | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | V141 yapı araçları için C++ MFC (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | Spectre Azaltma (ARM64) ile v141 yapı araçları için C++ MFC | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | Spectre Azaltma (x86 & x64) ile v141 oluşturma araçları için C++ MFC | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 - VS 2017 C++ x64/x86 Spectre azaltılmış libs (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Veri kaynakları ve hizmet referansları | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | VS 2017 (v141) araçları için C++ Windows XP Desteği [Amortismana Uğradı] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
