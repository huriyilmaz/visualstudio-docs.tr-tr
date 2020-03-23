---
title: Visual Studio Desktop Express iş yükü ve bileşen t.c.
titleSuffix: ''
description: Komut satırını kullanarak Visual Studio'yu yüklemek veya VSIX bildiriminde bağımlılık olarak belirtmek için iş yükünü ve bileşen bilgisayarlarını kullanın
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
ms.openlocfilehash: 3db18da6e09b3206d81f5600d54700f912a411e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113915"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Visual Studio Desktop Express bileşen dizini

Bu sayfadaki tablolar, komut satırını kullanarak Visual Studio'yu yüklemek için kullanabileceğiniz veya VSIX bildiriminde bağımlılık olarak belirtebileceğiniz künyeleri listelediğinizde. Visual Studio'ya güncellemeler yayınlarken ek bileşenler ekleyeceğiz.

Ayrıca sayfa hakkında aşağıdaki leri unutmayın:

* Her iş yükünün kendi bölümü vardır ve ardından iş yükü kimliği ve iş yükü için kullanılabilir bileşenlerin bir tablosu vardır.
* Varsayılan olarak, iş yükünü yüklediğinizde **Gerekli** bileşenler yüklenir.
* İsterseniz, **Önerilen** ve **İsteğe Bağlı** bileşenleri de yükleyebilirsiniz.
* Ayrıca, herhangi bir iş yüküne bağlı olmayan ek bileşenleri listeleyen bir bölüm ekledik.

VSIX bildiriminizde bağımlılıkları ayarladığınızda, yalnızca Bileşen kimliklerini belirtmeniz gerekir. Minimum bileşen bağımlılıklarımızı belirlemek için bu sayfadaki tabloları kullanın. Bazı senaryolarda, bu iş yükünden yalnızca bir bileşen belirttiğiniz anlamına gelebilir. Diğer senaryolarda, tek bir iş yükünden birden çok bileşen veya birden çok iş yükünden birden çok bileşen belirtmeniz anlamına gelebilir. Daha fazla bilgi için Visual [Studio 2017 sayfasına Nasıl Taşınır: Genişletilebilirlik Projelerini Geçirin](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) sayfasına bakın.

Bu tbm'lerin nasıl kullanılacağı hakkında daha fazla bilgi için [Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) sayfasını yüklemek için Komut Satırı Parametrelerini Kullanın sayfasına bakın. Ayrıca, diğer ürünler için iş yükü ve bileşen idelerinin listesi için [Visual Studio 2017 İş Yükü ve Bileşen II'leri](workload-and-component-ids.md) sayfasına bakın.

## <a name="express-for-windows-desktop"></a>Windows Masaüstü için Express

**Kimlik Numarası:** Microsoft.VisualStudio.Workload.WDExpress

**Açıklama:** Sözdizime duyarlı kod düzenleme, kaynak kodu denetimi ve iş öğesi yönetimi yle WPF, WinForms ve Win32 gibi yerel ve yönetilen uygulamalar oluşturun. C#, Visual Basic ve Visual C++ desteği içerir.

### <a name="components-included-by-this-workload"></a>Bu iş yükü tarafından dahil edilen bileşenler

Bileşen Kimliği | Adı | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce Yayıncılık | 15.8.27825.0 | Gerekli
Microsoft.Component.HelpViewer | Yardım Görüntüleyici | 15.6.27323.2 | Gerekli
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Gerekli
Microsoft.Component.VC.Runtime.OSSupport | UWP için Visual C++ çalışma zamanı | 15.6.27406.0 | Gerekli
Microsoft.Net.Component.4.5.1.Hedefleme Paketi | .NET Framework 4.5.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net.Component.4.5.Hedefleme Paketi | .NET Framework 4.5 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net.Component.4.6.1.SDK | .NET Çerçeve 4.6.1 SDK | 15.6.27406.0 | Gerekli
Microsoft.Net.Component.4.6.1.Hedefleme Paketi | .NET Framework 4.6.1 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net.Component.4.6.Hedefleme Paketi | .NET Framework 4.6 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 hedefleme paketi | 15.6.27406.0 | Gerekli
Microsoft.Net.ComponentGroup.DevelopmentÖn Koşullar | .NET Framework 4.6.1 geliştirme araçları | 15.8.27825.0 | Gerekli
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 geliştirme araçları | 15.6.27406.0 | Gerekli
Microsoft.VisualStudio.Component.Common.Azure.Tools | Bağlantı ve yayımlama araçları | 15.9.28107.0 | Gerekli
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio çekirdek editörü | 15.8.27729.1 | Gerekli
Microsoft.VisualStudio.Component.EntityFramework | Varlık Çerçevesi 6 araçları | 15.6.27406.0 | Gerekli
Microsoft.VisualStudio.Component.NuGet | NuGet paket yöneticisi | 15.9.28016.0 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# ve Visual Basic Roslyn derleyicileri | 15.6.27309.0 | Gerekli
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# ve Visual Basic | 15.8.27729.1 | Gerekli
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL çalışma zamanı | 15.6.27406.0 | Gerekli
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server için CLR veri türleri | 15.0.26208.0 | Gerekli
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Komut Satırı Yardımcı Programları | 15.0.26208.0 | Gerekli
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server desteği için veri kaynakları | 15.0.26621.2 | Gerekli
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | Gerekli
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Gerekli
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Veri Araçları | 15.9.28107.0 | Gerekli
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Statik analiz araçları | 15.0.26208.0 | Gerekli
Microsoft.VisualStudio.Component.TextTemplating | Metin Şablonu Dönüştürme | 15.0.26208.0 | Gerekli
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI desteği | 15.6.27309.0 | Gerekli
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM için Visual C++ derleyicileri ve kütüphaneleri | 15.8.27825.0 | Gerekli
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | ARM64 için Visual C++ derleyicileri ve kütüphaneleri | 15.9.28230.55 | Gerekli
Microsoft.VisualStudio.Component.VisualStudioData | Veri kaynakları ve hizmet referansları | 15.6.27406.0 | Gerekli
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Gerekli
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Gerekli

## <a name="unaffiliated-components"></a>Bağlı olmayan bileşenler

Bunlar, iş yüküne dahil olmayan, ancak tek bir bileşen olarak seçilebilen bileşenlerdir.

Bileşen Kimliği | Adı | Sürüm
--- | --- | ---
yok | yok | yok

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Visual Studio'yı yüklemek için komut satırı parametrelerini kullanma](use-command-line-parameters-to-install-visual-studio.md)
  * [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Visual Studio'nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
