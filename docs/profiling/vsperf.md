---
title: VSPerf | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 051c983920ddc80909d721e569c5efb5ecd33a7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779941"
---
# <a name="vsperf"></a>VSPerf
**VsPerf** komut satırı aracını kullanarak:

1. Visual Studio aygıta yüklenmediğinde komut satırındaki Profil UWP uygulamaları.

2. Profil profil oluşturma yöntemini kullanarak Profil Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamaları.

   Profil oluşturma seçenekleriniz hakkında daha fazla bilgi için [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

## <a name="uwp-apps-only"></a>Yalnızca UWP uygulamaları
 Bu seçenekler yalnızca UWP uygulamaları için geçerlidir.

|||
|-|-|
|**/app:{AppName}**|Profil oluşturucuyu başlatır ve belirtilen uygulamanın Başlat menüsünden başlatılmasını bekler.<br /><br /> Yüklü `vsperf /listapps` uygulamaların uygulama Adı ve PackageFullName'sini görüntülemek için çalıştırın.|
|**/paket:{PackageFullName}**|Profil oluşturucuyu başlatır ve belirtilen uygulamanın Başlat menüsünden başlatılmasını bekler.<br /><br /> Yüklü `vsperf /listapps` uygulamaların uygulama Adı ve PackageFullName'sini görüntülemek için çalıştırın.|
|**/js**|JavaScript uygulamalarının profilini çıkarmak için gereklidir.<br /><br /> JavaScript uygulamalarından performans verileri toplayın.<br /><br /> Yalnızca /paket veya /ekle ile kullanın.|
|**/noclr**|İsteğe bağlı. CLR verileri toplamayın.<br /><br /> Yalnızca /paket veya /ekle ile kullanın.<br /><br /> Optimizasyon, yönetilen semboller çözülecek.|
|**/listapps**|Yüklü uygulama Adlarını ve PaketFullAdlarını listele.|

## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Yalnızca Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamaları
 Bu seçenekler UWP uygulamalarında çalışmaz.

|||
|-|-|
|**/launch:{Çalıştırılabilir}**|Belirtilen yürütülebilir dosyanın profilini çıkarmaya başlar ve başlar.|
|**/args:{ExecutableArguments}**|**/başlat hedefini** geçmek için komut satırı bağımsız değişkenlerini belirtir.|
|**/konsol**|**/başlat** hedefini yeni bir komut penceresinde çalıştırın.|

## <a name="all-applications"></a>Tüm uygulamalar
 Bu seçenek herhangi bir Windows 8 veya Windows Server 2012 uygulaması için geçerlidir.

|||
|-|-|
|**/ekle:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Belirtilen işlemlerden veri toplar.<br /><br /> İşlem kimliğini (PID) ve çalışan uygulamaların işletim adlarını görüntülemek için Görev Yöneticisi'ni kullanın.|
|**/dosya:{ReportName}**|İsteğe bağlı. Çıktı dosyasını belirtir (varolan dosyanın üzerine yazar).<br /><br /> Yalnızca /paket veya /ekle ile kullanın.|
|**/duraklatma**|Veri toplamayı duraklatın.|
|**/özgeçmiş**|Veri toplamaya devam edin.|
|**/stop**|Veri toplamayı durdurun ve hedef işlemleri sonlandırın.|
|**/ayırma**|Veri toplamayı durdurun, ancak hedef işlemlerin çalışmaya devam etmesine izin verin.|
|**/durum**|Profil oluşturucu durumunu göster.|

## <a name="see-also"></a>Ayrıca bkz.
- [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
- [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
