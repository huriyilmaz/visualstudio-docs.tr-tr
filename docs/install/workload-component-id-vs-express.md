---
title: Visual Studio Desktop Express iş yükü ve bileşen kimlikleri
titleSuffix: ''
description: Komut satırını kullanarak Visual Studio 'Yu yüklemek veya bir VSıX bildiriminde bağımlılık olarak belirtmek için iş yükü ve bileşen kimliklerini kullanma
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: 1e24f90f24921bee9a6132ccc047c0b9da37fc90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81276298"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Visual Studio Desktop Express bileşen dizini

Bu sayfadaki tablolarda, komut satırını kullanarak Visual Studio 'Yu yüklemek için kullanabileceğiniz veya bir VSıX bildiriminde bağımlılık olarak belirtebileceğiniz kimlikler listelenmektedir. Visual Studio 'Da güncelleştirmeler yayınlıyoruz, ek bileşenler ekleyeceğiz.

Ayrıca, sayfa hakkında aşağıdakilere de göz önünde bulabilirsiniz:

* Her iş yükü kendi bölümüne sahiptir ve iş yükü KIMLIĞI ve iş yükü için kullanılabilir bileşenlerin bir tablosu gelir.
* Varsayılan olarak, **gerekli** bileşenler iş yükünü yüklediğinizde yüklenir.
* Seçeneğini belirlerseniz, **Önerilen** ve **isteğe bağlı** bileşenleri de yükleyebilirsiniz.
* Ayrıca, herhangi bir iş yükü ile bağlantılı olmayan ek bileşenleri listeleyen bir bölüm ekledik.

VSıX bildiriminizde bağımlılıklar ayarladığınızda, yalnızca bileşen kimliklerini belirtmeniz gerekir. En düşük bileşen bağımlılıklarımızı öğrenmek için bu sayfadaki tabloları kullanın. Bazı senaryolarda bu, bir iş yüküyle yalnızca bir bileşen belirttiğinizde anlamına gelebilir. Diğer senaryolarda, tek bir iş yüküyle birden çok bileşeni veya birden çok iş yükünün birden çok bileşenini belirtmeniz anlamına gelebilir. Daha fazla bilgi için bkz. [nasıl yapılır: genişletilebilirlik projelerini Visual Studio 'Ya geçirme 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) sayfası.

Bu kimlikleri kullanma hakkında daha fazla bilgi için bkz. [Visual Studio 2017 sayfasını yüklemek Için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md) . Ayrıca, diğer ürünlerin iş yükü ve bileşen kimliklerinin bir listesi için bkz. [Visual Studio 2017 Iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası.

## <a name="express-for-windows-desktop"></a>Windows Masaüstü için Express

**Kimliği:** Microsoft. VisualStudio. Workload. WDExpress

**Açıklama:** Sözdizimi kullanan kod düzenlemesi, kaynak kodu denetimi ve iş öğesi yönetimi ile WPF, WinForms ve Win32 gibi yerel ve yönetilen uygulamalar oluşturun. C#, Visual Basic ve Visual C++ desteğini içerir.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. Component. ClickOnce | ClickOnce yayımlama | 15.8.27825.0 | Gerekli
Microsoft. Component. HelpViewer | Yardım Görüntüleyicisi | 15.6.27323.2 | Gerekli
Microsoft. Component. MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft. Component. VC. Runtime. OSSupport | UWP için Visual C++ çalışma zamanı | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.5.1. TargetingPack | .NET Framework 4.5.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.5.2. TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.5. TargetingPack | .NET Framework 4,5 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft. net. Component. 4.6.1. SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6.1. TargetingPack | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4.6. TargetingPack | .NET Framework 4,6 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. Component. 4. TargetingPack | .NET Framework 4 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net. ComponentGroup. Developmentönkoşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft.Net. ComponentGroup. TargetingPacks. Common | .NET Framework 4 – 4,6 geliştirme araçları | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. Common. Azure. Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | Gerekli
Microsoft. VisualStudio. Component. CoreEditor | Visual Studio temel Düzenleyicisi | 15.8.27729.1 | Gerekli
Microsoft. VisualStudio. Component. EntityFramework | Entity Framework 6 araçları | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. NuGet | NuGet Paket Yöneticisi | 15.9.28016.0 | Gerekli
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
Microsoft. VisualStudio. Component. VC. CLı. support | C++/CLı desteği | 15.6.27309.0 | Gerekli
Microsoft. VisualStudio. Component. VC. Tools. ARM | ARM için Visual C++ derleyiciler ve kitaplıklar | 15.8.27825.0 | Gerekli
Microsoft. VisualStudio. Component. VC. Tools. ARM64 | ARM64 için derleyiciler ve kitaplıklar Visual C++ | 15.9.28230.55 | Gerekli
Microsoft. VisualStudio. Component. VisualStudioData | Veri kaynakları ve hizmet başvuruları | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. Windows10SDK. 14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. Windows10SDK. 17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Gerekli

## <a name="unaffiliated-components"></a>Bağlantılı olmayan bileşenler

Bunlar herhangi bir iş yüküne dahil olmayan, ancak tek bir bileşen olarak seçilebilir olan bileşenlerdir.

Bileşen KIMLIĞI | Name | Sürüm
--- | --- | ---
yok | yok | yok

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
  * [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
