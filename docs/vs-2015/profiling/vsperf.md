---
title: VSPerf | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8042b228a481dc3d720d8b422963db41abbddcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533841"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VSPerf** komut satırı aracını kullanarak şunları yapın:  
  
1. Cihaza Visual Studio yüklü olmadığında, komut satırından Windows Mağazası uygulamalarını profile.  
  
2. Örnekleme profili oluşturma yöntemini kullanarak Windows 8 masaüstü uygulamalarını ve Windows Server 2012 uygulamalarını profili oluşturma.  
  
   Profil oluşturma seçenekleriniz hakkında daha fazla bilgi için bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda  
 Bu konu, komut satırı aracı ile kullanabileceğiniz seçenekleri açıklar `vsperf.exe` . Konusu aşağıdaki bölümleri içerir:  
  
 [Yalnızca Windows Mağazası uygulamaları](#BKMK_windows_store_apps_only)  
  
 [Yalnızca Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamaları](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Tüm uygulamalar](#BKMK_All_applications)  
  
## <a name="windows-store-apps-only"></a><a name="BKMK_windows_store_apps_only"></a> Yalnızca Windows Mağazası uygulamaları  
 Bu seçenekler yalnızca Windows Mağazası uygulamaları için geçerlidir.  
  
|Seçenek|Açıklama|  
|-|-|  
|**/App: {AppName}**|Profil oluşturucuyu başlatır ve başlangıç menüsünden belirtilen uygulamanın başlatılmasını bekler.<br /><br /> `vsperf /listapps`Yüklenen uygulamaların uygulama adını ve PackageFullName 'ni görüntülemek için öğesini çalıştırın.|  
|**/Package: {PackageFullName}**|Profil oluşturucuyu başlatır ve başlangıç menüsünden belirtilen uygulamanın başlatılmasını bekler.<br /><br /> `vsperf /listapps`Yüklenen uygulamaların uygulama adını ve PackageFullName 'ni görüntülemek için öğesini çalıştırın.|  
|**/JS**|JavaScript uygulamalarının profilini oluşturmak için gereklidir.<br /><br /> JavaScript uygulamalarından performans verileri toplayın.<br /><br /> Yalnızca/Package veya/attachile kullanın.|  
|**/noclr**|İsteğe bağlı. CLR verileri toplama.<br /><br /> Yalnızca/Package veya/attachile kullanın.<br /><br /> İyileştirme, yönetilen semboller çözümlenmez.|  
|**/listapps**|Yüklü uygulama adlarını ve PackageFullNames listesini listeleyin.|  
  
## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a><a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a> Yalnızca Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamaları  
 Bu seçenekler Windows Mağazası uygulamaları üzerinde çalışmaz.  
  
|Seçenek|Açıklama|  
|-|-|  
|**/Launch: {executable}**|Başlatılır ve belirtilen yürütülebilir dosyanın profilini oluşturmaya başlar.|  
|**/args: {ExecutableArguments}**|**/Launch** hedefini geçirmek için komut satırı bağımsız değişkenlerini belirtir.|  
|**/Console**|Yeni bir komut penceresinde **/Launch** hedefini çalıştırır.|  
  
## <a name="all-applications"></a><a name="BKMK_All_applications"></a> Tüm uygulamalar  
 Bu seçenek, herhangi bir Windows 8 veya Windows Server 2012 uygulaması için geçerlidir.  
  
|Seçenek|Açıklama|  
|-|-|  
|**/Attach: {PID&#124;ProcessName} [, PID&#124;ProcessName]...**|Belirtilen işlemlerden verileri toplar.<br /><br /> Çalışan uygulamaların işlem kimliğini (PID) ve işlem adlarını görüntülemek için Görev Yöneticisi 'ni kullanın.|  
|**/File: {ReportName}**|İsteğe bağlı. Çıkış dosyasını belirtir (varolan dosyanın üzerine yazar).<br /><br /> Yalnızca/Package veya/attachile kullanın.|  
|**/Pause**|Veri toplamayı duraklatın.|  
|**/Resume sistemde**|Veri toplamayı sürdürür.|  
|**/Stop**|Veri toplamayı durdurun ve hedef süreçlerini sonlandırın.|  
|**/Detach**|Veri toplamayı durdurun, ancak hedef işlemlerin çalışmaya devam etmesine izin verin.|  
|**/Status**|Profil Oluşturucu durumunu göster.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows 8 ve Windows Server 2012 uygulamalarındaki performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)
