---
title: VSPerf | Microsoft Docs
description: Cihazda yüklü değilken vsPerf komut satırı aracını kullanarak komut Visual Studio UWP uygulamalarının profilini oluşturma hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c690567092f5cd7532e4430dab8d05812e8a4ad08480e62241fd26c76e715b9c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410014"
---
# <a name="vsperf"></a>VSPerf
**VsPerf komut satırı** aracını kullanarak:

1. Cihaza yüklü değilken komut Visual Studio UWP uygulamalarının profilini oluşturun.

2. Profil Windows 8 profil oluşturma Windows Server 2012 kullanarak masaüstü uygulamaları ve uygulama profili oluşturma.

   Profil oluşturma seçenekleriniz hakkında daha fazla bilgi için bkz. Windows 8 [ve Windows Server 2012.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="uwp-apps-only"></a>Yalnızca UWP uygulamaları
 Bu seçenekler yalnızca UWP uygulamaları için geçerlidir.

|Seçenek|Açıklama|
|-|-|
|**/app:{AppName}**|Profilleyiciyi başlatır ve belirtilen uygulamanın Başlat menüsü.<br /><br /> Yüklü `vsperf /listapps` uygulamaların uygulama Adını ve PackageFullName'i görüntülemek için çalıştırın.|
|**/package:{PackageFullName}**|Profilleyiciyi başlatır ve belirtilen uygulamanın Başlat menüsü.<br /><br /> Yüklü `vsperf /listapps` uygulamaların uygulama Adını ve PackageFullName'i görüntülemek için çalıştırın.|
|**/js**|JavaScript uygulamalarının profilini oluşturma için gereklidir.<br /><br /> JavaScript uygulamalardan performans verileri toplama.<br /><br /> Yalnızca /package veya /attach ile kullanın.|
|**/noclr**|İsteğe bağlı. CLR verilerini toplamayın.<br /><br /> Yalnızca /package veya /attach ile kullanın.<br /><br /> İyileştirme, hiçbir yönetilen simge çözümlemezse.|
|**/listapps**|Yüklü uygulama adlarını ve PackageFullNames adlarını listele.|

## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamaları
 Bu seçenekler UWP uygulamaları üzerinde çalışmaz.

|Seçenek|Açıklama|
|-|-|
|**/launch:{Executable}**|Belirtilen yürütülebilir dosyanın profilini başlatır ve profil oluşturmaya başlar.|
|**/args:{ExecutableArguments}**|/launch hedefini geçecek komut satırı **bağımsız değişkenlerini** belirtir.|
|**/console**|**/launch hedefini** yeni bir komut penceresinde çalıştırır.|

## <a name="all-applications"></a>Tüm uygulamalar
 Bu seçenek tüm uygulama Windows 8 veya Windows Server 2012 geçerlidir.

|Seçenek|Açıklama|
|-|-|
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Belirtilen işlemlerden veri toplar.<br /><br /> Çalışan uygulamaların işlem kimliğini (PID) ve işlem adlarını görüntülemek için Görev Yöneticisi'ni kullanın.|
|**/file:{ReportName}**|İsteğe bağlı. Çıktı dosyasını belirtir (var olan dosyanın üzerine yazma).<br /><br /> Yalnızca /package veya /attach ile kullanın.|
|**/pause**|Veri toplamayı duraklatma.|
|**/resume**|Veri toplamayı sürdürme.|
|**/stop**|Veri toplamayı durdurun ve hedef işlemleri sonlandırin.|
|**/detach**|Veri toplamayı durdurun, ancak hedef işlemlerin çalışmaya devamsına izin verme.|
|**/status**|Profil oluşturma durumunu göster.|

## <a name="see-also"></a>Ayrıca bkz.
- [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
- [Komut satırı profili](../profiling/using-the-profiling-tools-from-the-command-line.md)
