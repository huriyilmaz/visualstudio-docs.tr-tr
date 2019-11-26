---
title: Windows 8 ve Windows Server 2012 uygulamalarında performans araçları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c65561f9a9a2ca287232b7a61bb0e07ca07a769d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299655"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Windows 8 ve Windows Server 2012 Uygulamalarında Performans Araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio performans araçları 'nın bu platformlarda veri toplama biçiminde önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bu konuda, Windows 8 ve Windows Server 2012 platformlarındaki performans araçları için değişiklikler açıklanmaktadır.  
  
> [!NOTE]
> Desteklenen diğer Windows sürümleri (Windows 7, Windows Server 2008 R2) için performans araçları değişmemiştir.  
  
## <a name="BKMK_In_this_topic"></a>Bu konuda  
 [Visual Studio IDE 'den Windows Mağazası uygulamaları üzerinde veri toplama](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Visual Studio IDE 'den Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalarda veri toplama](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
- [Visual Studio IDE 'de örnekleme kullanarak Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalarda veri toplama](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
  [Komut satırından profil oluşturma](#BKMK_Profiling_from_the_command_line)  
  
  [Katman etkileşimi (tıp) verilerini toplama](#BKMK_Collecting_tier_interaction__TIP__data)  
  
## <a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a>Visual Studio IDE 'den Windows Mağazası uygulamaları üzerinde veri toplama  
 JavaScript ve HTML 5 ' te yazılmış bir Windows Mağazası uygulamasını profilin içinde, JavaScript kodu için izleme verileri toplayabilirsiniz. Visual C++, visual C#veya Visual Basic yazılmış bir Windows Mağazası uygulamasını veya bileşenini profil oluştururken, yerel ve yönetilen kod için örnekleme verisi toplamanız gerekir. Uygulamanızı yerel olarak veya uzak bir makinede profil oluşturabilirsiniz.  
  
 Windows Mağazası uygulamalarının profili oluşturulurken Bu profil oluşturma özellikleri ve seçenekleri desteklenmez:  
  
- Örnekleme yöntemi kullanılarak JavaScript uygulamalarının profilini oluşturma.  
  
- İzleme yöntemi kullanılarak yönetilen ve yerel kod profili oluşturuluyor.  
  
- Eşzamanlılık profili oluşturma  
  
- .NET bellek profili oluşturma  
  
- Katman etkileşimi profili oluşturma (tıp)  
  
- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.  
  
- Performans ve Windows sayaç verilerini toplama ya da ek komut satırı seçeneklerini belirtme gibi izleme seçenekleri.  
  
  Windows Mağazası uygulamalarının profilini oluşturma hakkında daha fazla bilgi için, Windows Geliştirme Merkezi 'nde aşağıdaki konulara bakın:  
  
  [Yerel makinede Microsoft Store uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
  [Uzak makinede Microsoft Store uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
  [Uygulama performansını çözümle](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
- [JavaScript Işlev zamanlaması](https://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
- [Uzak cihazda JavaScript Işlev zamanlaması](https://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
- [JavaScript Işlev zamanlaması verilerini çözümle](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
- [Yerel makinedeki C++Windows Mağazası C#uygulamalarında görsel, görsel ve Visual Basic kodu profili oluşturma](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
- [Uzak bir C++cihazdaki Windows C#Mağazası uygulamalarında görsel, görsel ve Visual Basic kodu profili oluşturma](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
- [Windows Mağazası uygulamalarında Visual C++, visual C#ve Visual Basic Code için performans verilerini çözümleme](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
  [Bu konuda](#BKMK_In_this_topic)  
  
## <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a>Visual Studio IDE 'den Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalarda veri toplama  
 İzleme yöntemini kullanarak profil oluşturma, Windows 8 için değişmemiştir.  
  
 Katman etkileşimi profili oluşturma (tıp), örnekleme yöntemi kullanılarak desteklenmez.  
  
### <a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a>Visual Studio IDE 'de örnekleme kullanarak Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalarda veri toplama  
 Bu profil oluşturma özellikleri ve seçenekleri, örnekleme yöntemi kullanılarak Windows 8 masaüstü uygulamalarının veya Windows Server 2012 uygulamalarının profili oluşturulurken desteklenmez:  
  
- Katman etkileşimi profili oluşturma (tıp). Tıp verilerinin toplanması, izleme kullanılarak desteklenir.  
  
- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.  
  
## <a name="BKMK_Profiling_from_the_command_line"></a>Komut satırından profil oluşturma  
 Visual Studio yüklemesi olmayan aygıtlar da dahil olmak üzere Windows 8 ve Windows Server 2012 cihazlarında profil oluşturma verilerini toplamak için iki komut satırı aracını kullanın:  
  
|Araç adı|Açıklama|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Windows Mağazası uygulamalarından profil oluşturma verilerini toplar ve Windows 8 Masaüstü uygulamalarından ve Windows Server 2012 uygulamalarından örnek profil oluşturma verilerini toplar.|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalardan izleme, eşzamanlılık ve katman etkileşimi profil oluşturma verilerini toplar. Önceki Windows sürümlerinden tüm profil oluşturma verisi türlerini toplar.|  
  
 Her iki araç da yerel bilgisayarda kullanılmak üzere Visual Studio ile birlikte yüklenir.  
  
 Visual Studio yüklü olmayan cihazlarda uygulama profili eklemek için aşağıdakilerden birini yapın:  
  
- Araçları [MSDN Web sitesinden](https://go.microsoft.com/fwlink/?LinkID=219549)Visual Studio için uzak Araçlar bir parçası olarak indirin.  
  
- Visual Studio bilgisayarınızdan tek başına profil oluşturucu araçları yükleme programını kopyalayın ve çalıştırın. Yükleme programları *% VSInstallDir%* **\Team Tools\performance tools\kurulumları** klasöründedir. Uzak bilgisayarın işletim sistemi (x86/x64) için Kurulum programını seçin.  
  
> [!NOTE]
> Tıp profil oluşturma verilerini toplamak için, Visual Studio makinenizden tek başına profil oluşturucuyu uzak bilgisayara yüklemelisiniz.  
  
 Bu profil oluşturma özellikleri ve seçenekleri, Windows 8 ve Windows Server 2012 uygulamalarının komut satırından profil oluşturma sırasında desteklenmez:  
  
- [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md)ile örnekleme modunu kullanarak Windows 8 ve windows Server 2012 Web uygulamalarından veri toplama.  
  
- VsPerfCmd. exe kullanarak örnekleme verilerini toplama.  
  
- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.  
  
## <a name="BKMK_Collecting_tier_interaction__TIP__data"></a>Katman etkileşimi (tıp) verilerini toplama  
 Katman etkileşimi profili oluşturma, ADO.NET Hizmetleri aracılığıyla veritabanlarıyla iletişim kuran çok katmanlı uygulamalar işlevlerinin yürütme zamanları hakkında ek bilgiler sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.  
  
 **Visual Studio sürümleri**  
  
 Katman etkileşimi profil oluşturma verileri [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]veya [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]kullanılarak toplanabilir. Ancak, katman etkileşimi profil oluşturma verileri yalnızca [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] ve [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]' de görüntülenebilir.  
  
 **Windows 8 ve Windows Server 2012**  
  
1. Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalardan katman etkileşim verileri toplamak için, izleme yöntemini kullanmanız gerekir.  
  
2. Windows Mağazası uygulamaları için katman etkileşimi verilerini toplayamazsınız.  
  
3. Katman etkileşim verilerini, desteklenen diğer Windows sürümündeki tüm profil oluşturma yöntemlerine dahil edebilirsiniz.  
  
   **Performans Sihirbazı ve Performans Gezgini**  
  
   Katman etkileşim verileri toplama seçeneğini Performans Gezgini bir profil oluşturma çalıştırmasına eklemeniz gerekir. Ayrıca, Performans Gezgini hedef düğümüne proje, çalıştırılabilir veya Web sitesini de eklemeniz gerekir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md).  
  
   **Uzak makinede Ipucu verileri toplama**  
  
   Uzak bir makinedeki katman etkileşimi verilerini toplamak için, bir Visual Studio makinesinin _% VSInstallDir%_ **\Team Tools\performance tools\kurulumları** klasöründeki **vs\_profiler\_** _\<platform >_ **\_** _\<Language >_ **. exe** dosyasını uzak bilgisayara kopyalamanız ve onu kurmanız gerekir. [Visual Studio uzak Araçlar](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) indirme paketindeki profil oluşturma araçlarını kullanamazsınız.  
  
   Profil oluşturma verilerini toplamak için [VSPerfCmd](../profiling/vsperfcmd.md) veya [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) kullanabilirsiniz.  
  
   **Ipucu raporları**  
  
   Katman etkileşim verileri yalnızca [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] veya [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] IDE 'de görüntülenebilir. [VSPerfReport](../profiling/vsperfreport.md) aracılığıyla dosya tabanlı katman etkileşimi raporları kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)   
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Komut Satırından Profil Oluşturma](../profiling/using-the-profiling-tools-from-the-command-line.md)
