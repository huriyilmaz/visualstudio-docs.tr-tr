---
title: Project Ayarlar C# hata ayıklama yapılandırması için | Microsoft Docs
description: Proje özellik sayfalarının Hata Ayıkla sekmesini ve Derleme sekmesini kullanarak Visual Studio C# hata ayıklama yapılandırması için proje ayarlarını nasıl değiştiryebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 0c6bbbe67de734fec2e90f33195732b7e69da40b71727602cbfbaf0d76b554c6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121310978"
---
# <a name="project-settings-for--c-debug-configurations"></a>C# hata ayıklama yapılandırması proje ayarları

Proje özellik sayfalarının Hata Ayıkla sekmesinde ve Derleme [sekmesinde](#debug-tab) C# proje [hata](#build-tab) ayıklama ayarlarını değiştirebilirsiniz.

Özellik sayfalarını açmak için, Çözüm Gezgini'de projeyi seçin ve  ardından Özellikler simgesini seçin veya projeye sağ tıklar ve Özellikler'i **seçin.** 

Daha fazla bilgi için [bkz. Hata ayıklama ve sürüm yapılandırmaları.](how-to-set-debug-and-release-configurations.md)

>[!IMPORTANT]
>Bu ayarlar .NET Core, ASP.NET veya UWP uygulamaları için geçerli değildir. UWP uygulamaları için hata ayıklama ayarlarını yapılandırmak için [bkz. UWP uygulaması için hata ayıklama oturumu başlatma.](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="debug-tab"></a>Hata ayıklama sekmesi

|Ayar|Açıklama|
|-------------------------------------| - |
| **Yapılandırma** | Uygulamanın inşası için modu ayarlar. Açılan **listeden Etkin (Hata Ayıkla)**, **Hata** **Ayıkla,** Serbest **Bırak** veya Tüm Yapılandırmalar'ı seçin. |
| **Başlatma eylemi** | Hata ayıklama yapılandırmasında **Başlat'ı** seçerek eylemi belirtir.<br />- **Başlangıç projesi** varsayılandır ve hata ayıklama için başlangıç projesini başlatıyor. Daha fazla bilgi için [bkz. Başlangıç projesini seçme.](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100))<br />- **Dış programı başlat** bir projenin parçası olan bir uygulamayı başlatır ve bu uygulamaya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] iliştirer. Daha fazla bilgi için [bkz. Hata ayıklayıcısı ile çalışan işlemlere ekleme.](attach-to-running-processes-with-the-visual-studio-debugger.md)<br />- **URL ile tarayıcıyı başlat,** bir web uygulamasında hata ayıklamaya olanak sağlar. |
| **Başlatma seçenekleri**  >  **Komut satırı bağımsız değişkenleri** | Hata ayıklaması yapılan uygulama için komut satırı bağımsız değişkenlerini belirtir. Komut adı, Dış programı başlat içinde belirtilen **uygulama adıdır.** |
| **Başlatma seçenekleri**  >  **Çalışma dizini** | Hata ayıklama yapılan uygulamanın çalışma dizinini belirtir. C# içinde çalışma dizini varsayılan olarak *\bin\debug* dizinidir.
| **Başlatma seçenekleri**  >  **Uzak makineyi kullanma**|Uzaktan hata ayıklama için bu seçeneği belirleyin ve uzaktan hata ayıklama hedefinin adını veya [msvsmon sunucu adını girin.](../debugger/remote-debugging.md) <br />Uzak makinede uygulamanın konumu, Derleme **sekmesindeki Çıkış** Yolu özelliği **tarafından** belirtilir. Konum, uzak makinede paylaşılabilir bir dizin olmalıdır.
| **Hata ayıklayıcı altyapısı**  >  **Unmanaged code debugging'i etkinleştirme** | Yönetilen uygulamanın yerel (yönetilemeyen) Win32 koduna yapılan çağrılarda hata ayıklar. |
| **Hata ayıklayıcı altyapısı**  >  **Hata SQL Server etkinleştirme** | Veritabanı nesnelerini SQL Server hataları ayıklar. |

## <a name="build-tab"></a>Derleme sekmesi

|Ayar|Açıklama|
|-------------|-----------------|
|**Genel**  >  **Koşullu derleme sembolleri**|Seçilirse DEBUG ve TRACE sabitlerini tanımlayın.<br /><br /> Bu sabitler, Hata Ayıklama sınıfının ve Trace [sınıfının koşullu](/dotnet/api/system.diagnostics.debug) [derlemeye olanak sağlar.](/dotnet/api/system.diagnostics.trace) Bu sabitler tanımlandığı için Hata Ayıklama ve İzleme sınıfı yöntemleri Çıktı penceresine [çıkış oluşturur.](../ide/reference/output-window.md) Bu sabitler olmadan Hata Ayıklama ve İzleme sınıfı yöntemleri derlanmaz ve hiçbir çıkış oluşturulmaz.<br /><br />Genellikle, DEBUG derlemenin Hata Ayıklama sürümünde tanımlanır ve Yayın sürümünde tanımlanmamıştır. TRACE hem Hata Ayıklama hem de Yayın sürümlerinde tanımlanır.|
|**Genel**  >  **Kodu iyileştirme**|Hata yalnızca iyileştirilmiş kodda görüntülendiğinden, Hata ayıklama derlemeleri için bu ayarın seçimini kaldırın. İyileştirilmiş kodun hata ayıklaması daha zordur çünkü yönergeler kaynak kodda doğrudan deyimlere karşılık gelir.|
|**Çıkış**  >  **Çıkış yolu**|Hata ayıklama için *genellikle bin\Debug* olarak ayarlanır.|
|**Gelişmiş** düğmesi|Gelişmiş hata ayıklama seçenekleri hakkında bilgi için [bkz. Gelişmiş derleme ayarları iletişim kutusu (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Sembol (*.pdb*) dosyalarının taşınabilir biçimi. .NET Core uygulamaları için son platformlar arası bir biçimdir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)