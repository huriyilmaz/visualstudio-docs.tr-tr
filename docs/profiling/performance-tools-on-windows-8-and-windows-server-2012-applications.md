---
title: WS 2012 Windows 8 & performans araçları
description: Performans araçlarının veri toplama Windows 8 Windows Server 2012 önemli değişiklikler Visual Studio gelişmiş güvenlik özelliklerinin nasıl gerekli olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/19/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8725d077b4baa90a3350d4e866cb06e432282773
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107101"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Windows 8 ve Windows Server 2012 uygulamalarında performans araçları

Gelişmiş güvenlik özellikleri Windows 8 Windows Server 2012 performans araçlarının bu platformlarda veri toplama Visual Studio önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Bu konu başlığında, Windows 8 ve Windows Server 2012 açıklanmıştır.

> [!NOTE]
> Windows'nin (Windows 7, Windows Server 2008 R2) desteklenen diğer sürümleri için performans araçları değişmemiştir.

## <a name="collect-data-on-uwp-apps-from-the-visual-studio-ide"></a>IDE'den UWP uygulamaları Visual Studio toplama

JavaScript ve HTML 5 ile yazılmış bir UWP uygulamasının profilini 0'a 0'larsanız, JavaScript kodu için ölçüm verilerini toplar. Visual C++, Visual C# veya Visual Basic yazılmış bir UWP uygulamasının veya bileşeninin profilini 0,000'den fazla yerel ve yönetilen kod için toplar. Uygulamanın profilini yerel olarak veya uzak bir makinede kullanabilirsiniz.

Bu profil oluşturma özellikleri ve seçenekleri, UWP uygulamalarının profilini oluşturmada desteklenmiyor:

- Örnekleme yöntemini kullanarak JavaScript uygulamalarının profilini oluşturma.
- Ölçümleme yöntemini kullanarak yönetilen ve yerel kodun profilini oluşturma.
- Eşzamanlılık profili oluşturma
- .NET bellek profili oluşturma
- Katman etkileşimi profili oluşturma (TIP)
- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.
- Performans ve Windows sayaç verilerini toplama veya ek komut satırı seçenekleri belirtme gibi ölçümleme seçenekleri.

UWP uygulamalarının profilini oluşturma hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Yerel makinede UWP uygulamaları çalıştırma](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)
- [Uzak makinede UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md)
- [Profil oluşturma araçlarına ilk bakış](profiling-feature-tour.md)
- [JavaScript belleği](../profiling/javascript-memory.md)
- [Yerel Visual C++ UWP uygulamalarındaki Visual Basic, Visual C# ve Visual Basic kodunun profilini oluşturma](/previous-versions/hh696631(v=vs.140))
- [Uzak Visual C++ UWP uygulamalarındaki Visual Basic, Visual C# ve Visual Basic kodunun profilini oluşturma](/previous-versions/hh972878(v=vs.140))
- [UWP uygulamalarındaki Visual C++, Visual C# ve Visual Basic için performans verilerini analiz etme](/previous-versions/hh780914(v=vs.140))

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a>Windows 8 masaüstünde veya Windows Server 2012 IDE'den Visual Studio verileri toplama

Profil oluşturma yöntemi kullanılarak profil oluşturma, Windows 8.

Katman etkileşimi profili oluşturma (TIP), örnekleme yöntemi kullanılarak desteklenmiyor.

## <a name="collect-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a>IDE'den örnekleme kullanarak Windows 8 masaüstünde veya Windows Server 2012 üzerinde çalışan Visual Studio toplama

Bu profil oluşturma özellikleri ve seçenekleri, örnekleme yöntemini kullanarak Windows 8 uygulamaları veya Windows Server 2012 profil oluşturma özelliği için destek değildir:

- Katman etkileşimi profili oluşturma (TIP). İPUCU verilerini toplama, ölçümleme kullanılarak de desteklene.

- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.

## <a name="profile-from-the-command-line"></a>Komut satırı profili

Profil oluşturma verilerini Windows 8 ve Windows Server 2012 cihazları üzerinde toplamak için iki komut satırı aracı kullanırsınız. Bu araçlar arasında yüklemesi Visual Studio:

|Araç adı|Açıklama|
|---------------|-----------------|
|[VSPerf](../profiling/vsperf.md)|UWP uygulamalarından profil oluşturma verilerini toplar ve masaüstü uygulamalarından ve Windows 8 uygulamalardan örnek profil Windows Server 2012 toplar.|
|[VSPerfCmd](../profiling/vsperfcmd.md)|Windows 8 masaüstü veya Windows Server 2012 üzerinde çalışan uygulamalardan ölçümlü araç, eşzamanlılık ve katman etkileşim profili oluşturma verilerini Windows Server 2012. Uygulamanın önceki sürümlerinden profil oluşturma verisi Windows.|

Her iki araç da yerel Visual Studio için bir uygulamayla birlikte yüklenir.

Yüklü yüklü Visual Studio cihazlarda uygulamaların profilini oluşturmak için, aşağıdakilerden birini yapın:

- MSDN web sitesinden Visual Studio için Uzak Araçlar parçası olarak [indirin.](https://visualstudio.microsoft.com/#downloads+d-additional-software)

- Tek başına profil oluşturma araçları yükleme programını kopyalayıp bilgisayarınızdan Visual Studio çalıştırın. Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) Uzak bilgisayarın işletim sistemi (x86/x64) için kurulum programını seçin.

> [!NOTE]
> İPUCU profili oluşturma verilerini toplamak için, uzak bilgisayara tek başına profil Visual Studio makinenizi yüklemeniz gerekir.

Bu profil oluşturma özellikleri ve seçenekleri, komut Windows 8 ve Windows Server 2012 profil oluşturma özelliğinde desteklanmaz:

- [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md)Windows Server 2012 Windows 8 örnekleme modunu kullanarak web uygulamalarından ve web uygulamalarından veri toplama.

- Veri kaynağı kullanarak örnekleme VsPerfCmd.exe.

- Örnekleme olayı ve zamanlama aralığını ayarlama veya ek performans sayacı verileri toplama gibi örnekleme seçenekleri.

## <a name="collect-tier-interaction-tip-data"></a>Katman etkileşimi (TIP) verilerini toplama

Katman etkileşimi profili oluşturma, veritabanlarıyla iletişim kuran çok katmanlı uygulamaların işlevlerinin yürütme süreleri hakkında ek bilgi sağlar ve ADO.NET sağlar. Veriler yalnızca zaman uyumlu işlev çağrıları için toplanır.

**Visual Studio sürümleri**

Katman etkileşimi profil oluşturma verileri, herhangi bir sürüm kullanılarak Visual Studio. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise.

**Windows 8 ve Windows Server 2012**

1. Windows 8 masaüstünde veya Windows Server 2012 çalışan uygulamalardan katman etkileşim verilerini toplamak için, ölçüm yöntemini kullansanız gerekir.

2. UWP uygulamaları için katman etkileşim verileri toplayabilirsiniz.

3. Katman etkileşim verilerini tüm profil oluşturma yöntemlerine diğer desteklenen sürümlerde dahil Windows.

**Performans Sihirbazı ve Performans Gezgini**

Katman etkileşim veri toplama seçeneğini profil oluşturma çalıştırması kaynağından bir Performans Gezgini. Ayrıca projeyi, yürütülebilir dosyayı veya web sitesini de uygulamanın Hedef düğümüne Performans Gezgini. Bkz. [Katman etkileşim verilerini toplama.](../profiling/collecting-tier-interaction-data.md)

**Uzak makinede TIP verileri toplama**

Uzak makinede katman etkileşim verileri toplamak için, vs **\_ profiler \_**.exedosyasını bir Visual Studio makinesinin _\<Platform>_ **\_** _\<Language>_ **** *%VSInstallDir%\Team Tools\Performance Tools\Setups* klasöründen uzak bilgisayara kopyalamanız ve yüklemeniz gerekir. Uzaktan Hata Ayıklama indirme paketinde profil [oluşturma araçlarını kullanılamaz.](../debugger/remote-debugging.md)

Profil oluşturma verilerini [toplamak için VSPerfCmd](../profiling/vsperfcmd.md) veya [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) kullanabilirsiniz.

**İpucu raporları**

Katman etkileşim verileri yalnızca Visual Studio Enterprise. [VSPerfReport](../profiling/vsperfreport.md) aracılığıyla dosya tabanlı katman etkileşim raporları kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

[Performans Gezgini](../profiling/performance-explorer.md) 
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Komut satırı profili](../profiling/using-the-profiling-tools-from-the-command-line.md)