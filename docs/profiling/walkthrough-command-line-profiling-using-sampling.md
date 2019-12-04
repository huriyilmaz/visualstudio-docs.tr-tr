---
title: 'İzlenecek yol: örnekleme kullanarak komut satırı profili oluşturma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 09272c8cf2dff02d3be024b9c3eeab8b51f56df7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777978"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>İzlenecek yol: örnekleme kullanarak komut satırı profili oluşturma

Bu izlenecek yol, performans sorunlarını belirlemek için komut satırı araçları ve örnekleme kullanarak bir uygulamanın profilini oluşturmayı gösterir.

Bu kılavuzda, komut satırı araçlarını kullanarak yönetilen bir uygulamanın profilini oluşturmaya ve uygulamadaki performans sorunlarını yalıtmak ve tanımlamak için örnekleme kullanmayı öğreneceksiniz.

Bu kılavuzda, aşağıdaki adımları izleyeceğinizi göreceksiniz:

- Komut satırı araçlarını ve örneklemesi kullanarak bir uygulama profili oluşturma.
- Performans sorunlarını bulmak ve gidermek için örneklenmiş profil oluşturma sonuçlarını çözümleyin.

## <a name="prerequisites"></a>Prerequisites

- [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)] ara anlama
- Komut satırı araçlarıyla çalışmanın ara anlama
- [PeopleTrax örneğinin](performance-explorer.md) bir kopyası
- Profil oluşturma tarafından sağlanan bilgilerle çalışmak için, hata ayıklama sembol bilgilerinin kullanılabilir olması en iyisidir.

## <a name="command-line-profiling-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak komut satırı profili oluşturma

Örnekleme, belirli bir işlemin etkin işlevi belirlemede düzenli aralıklarla yokladığı profil oluşturma yöntemidir. Elde edilen veriler, işlemin örneklendiği sırada işlevin çağrı yığınının en üstünde ne sıklıkta olduğunu gösteren bir sayı sağlar.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>PeopleTrax uygulamasını örnekleme yöntemini kullanarak profili eklemek için

1. PeopleTrax örnek uygulamasını yükleyip uygulamanın yayın sürümünü oluşturun.

2. Bir komut istemi penceresi açın ve Profil Oluşturma Araçları dizinini yerel yol ortam değişkenine ekleyin.

3. Çalışma dizinini PeopleTrax ikililerini içeren dizin olarak değiştirin.

4. Uygun ortam değişkenlerini ayarlamak için aşağıdaki komutu yazın:

    ```cmd
    VSPerfCLREnv /sampleon
    ```

5. Profil oluşturucuyu denetleyen komut satırı aracı olan *VSPerfCmd. exe*' yi çalıştırarak profil oluşturmayı başlatın. Aşağıdaki komut, örnekleme modunda uygulamayı ve profil oluşturucuyu başlatır:

    ```cmd
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe
    ```

     Profil Oluşturucu işlemi başlar ve *PeopleTrax. exe* işlemine ekler. Profil Oluşturucu işlemi, toplanan profil oluşturma verilerini rapor dosyasına yazmaya başlar.

6. **Kişi al**seçeneğine tıklayın.

7. **ExportData**öğesine tıklayın.

     Not Defteri açılır ve **PeopleTrax**adresinden dışarıya aktarılmış verileri içeren yeni bir dosya görüntüler.

8. Not defteri 'ni kapatın ve sonra **PeopleTrax** uygulamasını kapatın.

9. Profil oluşturucuyu kapatın. Şu komutu yazın:

    ```cmd
    VSPerfCmd /shutdown
    ```

10. Ortam değişkenlerini sıfırlamak için aşağıdaki komutu kullanın:

    ```cmd
    VSPerfCLREnv /sampleoff
    ```

11. Profil oluşturma verileri içinde depolanır. *VSP* dosyası aşağıdaki yöntemlerden birini kullanarak sonuçları çözümleyin:

    - Öğesini açın. Visual Studio IDE 'de *VSP* dosyası.

         veya

    - Virgülle ayrılmış bir değer (. *CSV*) dosyasını kullanarak *VSPerfReport. exe*komut satırı aracını kullanın. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE dışında kullanılmak üzere raporlar oluşturmak için aşağıdaki komutu kullanın:

        ```cmd
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all
        ```

## <a name="see-also"></a>Ayrıca bkz.


[VSPerfCmd](../profiling/vsperfcmd.md)
[komut satırından](../profiling/using-the-profiling-tools-from-the-command-line.md) [performans oturumuna genel bakış](../profiling/performance-session-overview.md)
profili [örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)
[Performans raporu görünümleri](../profiling/performance-report-views.md)
