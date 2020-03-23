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
ms.openlocfilehash: 3938e7dc1b3ec33c8a4cf74b6957067bbdfd6185
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778433"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Windows 8 ve Windows Server 2012 uygulamalarında performans araçları

Windows 8 ve Windows Server 2012'de başlayan gelişmiş güvenlik özellikleri, Visual Studio performans araçlarının bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. Bu konu, Windows 8 ve Windows Server 2012 platformlarında başlayan performans araçları değişikliklerini açıklar.

> [!NOTE]
> Windows'un diğer desteklenen sürümleri (Windows 7, Windows Server 2008 R2) için performans araçları değişmedi.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>Visual Studio IDE'den UWP uygulamaları hakkında veri toplama

JavaScript ve HTML 5 ile yazılmış bir UWP uygulamasının profilini aldığınızda, JavaScript kodu için enstrümantasyon verileri toplarsınız. Visual C++, Visual C#veya Visual Basic'te yazılmış bir UWP uygulamasının veya bileşeninin profilini çıkardığınız zaman, yerel ve yönetilen kod için örnekleme verileri toplarsınız. Uygulamanızın profilini yerel olarak veya uzak bir makinede oluşturabilirsiniz.

UWP uygulamaları nın profilini çıkarırken bu profil oluşturma özellikleri ve seçenekleri desteklenmez:

- Örnekleme yöntemini kullanarak JavaScript uygulamalarını profilleme.
- Enstrümantasyon yöntemini kullanarak yönetilen ve yerel kod oluşturma.
- Eşzamanlılık profiloluşturma
- .NET bellek profilleme
- Katman etkileşimi profiloluşturma (TIP)
- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.
- Performans ve windows sayacı verilerini toplama veya ek komut satırı seçenekleri belirtme gibi enstrümantasyon seçenekleri.

UWP uygulamalarının profil oluşturma hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Yerel makinede UWP uygulamaları çalıştırma](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)
- [Uzak makinede UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Profil oluşturma araçlarına ilk bakış](profiling-feature-tour.md)
- [JavaScript bellek](../profiling/javascript-memory.md)
- [Yerel bir makinedeki UWP uygulamalarında Profil Görsel C++, Visual C#ve Visual Basic kodu](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)
- [Uzak bir cihazdaki UWP uygulamalarında Profil Visual C++, Visual C#ve Visual Basic kodu](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)
- [UWP uygulamalarında Visual C++, Visual C#ve Visual Basic kodları için performans verilerini analiz edin](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Visual Studio IDE'den Windows 8 masaüstünde veya Windows Server 2012'de çalışan uygulamalar hakkında veri toplama

Enstrümantasyon yöntemini kullanarak profil oluşturma Windows 8 için değişmedi.

Katman etkileşimi profiloluşturma (TIP) örnekleme yöntemi kullanılarak desteklenmez.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>Visual Studio IDE'den örnekleme kullanarak Windows 8 masaüstünde veya Windows Server 2012'de çalışan uygulamalar hakkında veri toplama

Bu profil oluşturma özellikleri ve seçenekleri, örnekleme yöntemini kullanarak Windows 8 masaüstü uygulamaları veya Windows Server 2012 uygulamaları profil leme yaparken desteklenmez:

- Katman etkileşimi profiloluşturma (TIP). TIP verilerinin toplanması enstrümantasyon kullanılarak desteklenir.

- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.

## <a name="profile-from-the-command-line"></a>Komut satırından profil

Visual Studio yüklemesi olmayan aygıtlar da dahil olmak üzere, Windows 8 ve Windows Server 2012 aygıtlarında profil oluşturma verileri toplamak için iki komut satırı aracı kullanırsınız:

|Araç adı|Açıklama|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|UWP uygulamalarından profil oluşturma verileri toplar ve Windows 8 masaüstü uygulamalarından ve Windows Server 2012 uygulamalarından örnek profil oluşturma verileri toplar...|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Windows 8 masaüstü veya Windows Server 2012'de çalışan uygulamalardan enstrümantasyon, eşzamanlılık ve katman etkileşimi profil oluşturma verileri toplar. Windows'un önceki sürümlerinden tüm profil oluşturma verilerini toplar.|

Her iki araç da yerel bilgisayarda kullanılmak üzere Visual Studio ile yüklenir.

Visual Studio yüklü olmayan aygıtlarda profil uygulamaları için aşağıdakilerden birini yapın:

- [Araçları MSDN web sitesinden](https://visualstudio.microsoft.com/#downloads+d-additional-software)Visual Studio için Uzak Araçlar'ın bir parçası olarak indirin.

- Visual Studio bilgisayarınızdan tek başına profil oluşturma araçları yükleme programını kopyalayın ve çalıştırın. Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz. Uzak bilgisayarın işletim sistemi (x86/x64) için kurulum programını seçin.

> [!NOTE]
> TIP profil oluşturma verilerini toplamak için, Visual Studio makinenizdeki tek başına profil oluşturucuyu uzak bilgisayara yüklemeniz gerekir.

Bu profil oluşturma özellikleri ve seçenekleri, komut satırından Windows 8 ve Windows Server 2012 uygulamaları profilleme de desteklenmez:

- [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md)ile örnekleme modunu kullanarak Windows 8 ve Windows Server 2012 web uygulamalarından veri toplama.

- VsPerfCmd.exe kullanarak örnekleme verileri toplama.

- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.

## <a name="collect-tier-interaction-tip-data"></a>Katman etkileşimi (TIP) verilerini toplama

Katman etkileşimi profil oluşturma, veritabanlarıyla ADO.NET hizmetler aracılığıyla iletişim sağlayan çok katmanlı uygulamaların işlevlerinin yürütme süreleri hakkında ek bilgiler sağlar. Veriler yalnızca eşzamanlı işlev çağrıları için toplanır.

**Visual Studio sürümleri**

Katman etkileşimprofilleme verileri Visual Studio'nun herhangi bir sürümü kullanılarak toplanabilir. Ancak, katman etkileşimprofilleme verileri yalnızca Visual Studio Enterprise'da görüntülenebilir.

**Windows 8 ve Windows Server 2012**

1. Windows 8 masaüstü veya Windows Server 2012'de çalışan uygulamalardan katman etkileşim verileri toplamak için enstrümantasyon yöntemini kullanmanız gerekir.

2. UWP uygulamaları için katman etkileşim verileri toplayamazsınız.

3. Windows'un desteklenen diğer sürümündeki tüm profil oluşturma yöntemlerine katman etkileşim verilerini ekleyebilirsiniz.

**Performans Sihirbazı ve Performans Gezgini**

Performans Gezgini'nden bir profil oluşturma çalışmasına katman etkileşim veri toplama seçeneğini eklemeniz gerekir. Ayrıca, projeyi, çalıştırılabilir veya web sitesini Performans Gezgini'nin Hedef düğümüne eklemeniz gerekir. Bkz. [Katman etkileşim verilerini topla.](../profiling/collecting-tier-interaction-data.md)

**Uzak bir makinede İpucu verilerini toplama**

Uzak bir makinede katman etkileşim verilerini toplamak için, bir Visual Studio makinesinin *%VSInstallDir%\Team Tools\Performance Tools\Setups* klasöründen vs **\_** **\_profiler\_**_\<Platformu>_ _ \<Language>_ **.exe** dosyasını kopyalamanız ve yüklemeniz gerekir. [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md) indirme paketinde profil oluşturma araçlarını kullanamazsınız.

Profil oluşturma verilerini toplamak için [VSPerfCmd](../profiling/vsperfcmd.md) veya [VSPerfASPNetCmd'yi](../profiling/vsperfaspnetcmd.md) kullanabilirsiniz.

**TIP raporları**

Katman etkileşim verileri yalnızca Visual Studio Enterprise'da görüntülenebilir. [VSPerfReport](../profiling/vsperfreport.md) aracılığıyla dosya tabanlı katman etkileşim raporları kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

[Performans Gezgini](../profiling/performance-explorer.md)
[Performans oturumlarını](../profiling/configuring-performance-sessions.md)
yapılandırma[Komut satırından profil](../profiling/using-the-profiling-tools-from-the-command-line.md)
