---
title: Windows 8 & Windows Server 2012 uygulamalarında performans araçları
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 03c5897f4cbf06ad7c9dc7541a032f5b86e45d4c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038614"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Windows 8 ve Windows Server 2012 uygulamalarında performans araçları

Windows 8 ve Windows Server 2012 ' den başlayan gelişmiş güvenlik özellikleri, Visual Studio performans araçları 'nın bu platformlarda veri toplama biçiminde önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bu konuda, Windows 8 ve Windows Server 2012 platformlarından itibaren performans araçları için değişiklikler açıklanmaktadır.

> [!NOTE]
> Desteklenen diğer Windows sürümleri (Windows 7, Windows Server 2008 R2) için performans araçları değişmemiştir.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Visual Studio IDE 'den UWP uygulamalarında veri toplama

JavaScript ve HTML 5 ' te yazılmış bir UWP uygulamasını profilin içinde, JavaScript kodu için izleme verileri toplayabilirsiniz. Visual C++, Visual C# veya Visual Basic yazılmış bir UWP uygulamasını veya bileşenini profil oluştururken, yerel ve yönetilen kod için örnekleme verisi toplamanız gerekir. Uygulamanızı yerel olarak veya uzak bir makinede profil oluşturabilirsiniz.

UWP uygulamalarının profili oluşturulurken Bu profil oluşturma özellikleri ve seçenekleri desteklenmez:

- Örnekleme yöntemi kullanılarak JavaScript uygulamalarının profilini oluşturma.
- İzleme yöntemi kullanılarak yönetilen ve yerel kod profili oluşturuluyor.
- Eşzamanlılık profili oluşturma
- .NET bellek profili oluşturma
- Katman etkileşimi profili oluşturma (tıp)
- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.
- Performans ve Windows sayaç verilerini toplama ya da ek komut satırı seçeneklerini belirtme gibi izleme seçenekleri.

UWP uygulamalarının profilini oluşturma hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Yerel makinede UWP uygulamaları çalıştırma](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)
- [Uzak makinede UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Profil oluşturma araçlarına ilk bakış](profiling-feature-tour.md)
- [JavaScript belleği](../profiling/javascript-memory.md)
- [Yerel bir makinedeki UWP uygulamalarında profil Visual C++, Visual C# ve Visual Basic kodu](/previous-versions/hh696631(v=vs.140))
- [Uzak cihazdaki UWP uygulamalarında profil Visual C++, Visual C# ve Visual Basic kodu](/previous-versions/hh972878(v=vs.140))
- [UWP uygulamalarında Visual C++, Visual C# ve Visual Basic kodu için performans verilerini çözümleme](/previous-versions/hh780914(v=vs.140))

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Visual Studio IDE 'den Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalar üzerinde veri toplama

İzleme yöntemini kullanarak profil oluşturma, Windows 8 için değişmemiştir.

Katman etkileşimi profili oluşturma (tıp), örnekleme yöntemi kullanılarak desteklenmez.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Visual Studio IDE 'de örnekleme kullanarak Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalarda veri toplayın

Bu profil oluşturma özellikleri ve seçenekleri, örnekleme yöntemi kullanılarak Windows 8 masaüstü uygulamalarının veya Windows Server 2012 uygulamalarının profili oluşturulurken desteklenmez:

- Katman etkileşimi profili oluşturma (tıp). Tıp verilerinin toplanması, izleme kullanılarak desteklenir.

- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.

## <a name="profile-from-the-command-line"></a>Komut satırından profil

Visual Studio yüklemesi olmayan aygıtlar da dahil olmak üzere Windows 8 ve Windows Server 2012 cihazlarında profil oluşturma verilerini toplamak için iki komut satırı aracını kullanın:

|Araç adı|Description|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|UWP uygulamalarından profil oluşturma verilerini toplar ve Windows 8 Masaüstü uygulamalarından ve Windows Server 2012 uygulamalarından örnek profil oluşturma verilerini toplar.|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalardan izleme, eşzamanlılık ve katman etkileşimi profil oluşturma verilerini toplar. Önceki Windows sürümlerinden tüm profil oluşturma verisi türlerini toplar.|

Her iki araç da yerel bilgisayarda kullanılmak üzere Visual Studio ile birlikte yüklenir.

Visual Studio yüklü olmayan cihazlarda uygulama profili eklemek için aşağıdakilerden birini yapın:

- Araçları [MSDN Web sitesinden](https://visualstudio.microsoft.com/#downloads+d-additional-software)Visual Studio için uzak Araçlar bir parçası olarak indirin.

- Visual Studio bilgisayarınızdan tek başına profil oluşturucu araçları yükleme programını kopyalayın ve çalıştırın. Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Uzak bilgisayarın işletim sistemi (x86/x64) için Kurulum programını seçin.

> [!NOTE]
> Tıp profil oluşturma verilerini toplamak için, Visual Studio makinenizden tek başına profil oluşturucuyu uzak bilgisayara yüklemelisiniz.

Bu profil oluşturma özellikleri ve seçenekleri, Windows 8 ve Windows Server 2012 uygulamalarının komut satırından profil oluşturma sırasında desteklenmez:

- [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md)ile örnekleme modunu kullanarak Windows 8 ve windows Server 2012 Web uygulamalarından veri toplama.

- VsPerfCmd.exe kullanarak örnekleme verileri toplama.

- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.

## <a name="collect-tier-interaction-tip-data"></a>Katman etkileşimi (tıp) verilerini topla

Katman etkileşimi profili oluşturma, ADO.NET Hizmetleri aracılığıyla veritabanlarıyla iletişim kuran çok katmanlı uygulamalar işlevlerinin yürütme zamanları hakkında ek bilgiler sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.

**Visual Studio sürümleri**

Katman etkileşimi profil oluşturma verileri, herhangi bir Visual Studio sürümü kullanılarak toplanabilir. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise görüntülenebilir.

**Windows 8 ve Windows Server 2012**

1. Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalardan katman etkileşim verileri toplamak için, izleme yöntemini kullanmanız gerekir.

2. UWP uygulamaları için katman etkileşimi verilerini toplayamazsınız.

3. Katman etkileşim verilerini, desteklenen diğer Windows sürümündeki tüm profil oluşturma yöntemlerine dahil edebilirsiniz.

**Performans Sihirbazı ve Performans Gezgini**

Katman etkileşim verileri toplama seçeneğini Performans Gezgini bir profil oluşturma çalıştırmasına eklemeniz gerekir. Ayrıca, Performans Gezgini hedef düğümüne proje, çalıştırılabilir veya Web sitesini de eklemeniz gerekir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md).

**Uzak makinede Ipucu verileri toplama**

Uzak bir makinedeki katman etkileşimi verilerini toplamak için, **vs \_ Profiler \_ ** _\<Platform>_ **\_** _\<Language>_ **. exe** dosyasını bir Visual Studio makinesinin *%VSInstallDir%\Team Tools\Performance tools\kurulumları* klasöründen uzak bilgisayara kopyalamanız ve kurmanız gerekir. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) indirme paketindeki profil oluşturma araçlarını kullanamazsınız.

Profil oluşturma verilerini toplamak için [VSPerfCmd](../profiling/vsperfcmd.md) veya [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) kullanabilirsiniz.

**Ipucu raporları**

Katman etkileşim verileri yalnızca Visual Studio Enterprise ' de görüntülenebilir. [VSPerfReport](../profiling/vsperfreport.md) aracılığıyla dosya tabanlı katman etkileşimi raporları kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

[Performans Gezgini](../profiling/performance-explorer.md) 
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)