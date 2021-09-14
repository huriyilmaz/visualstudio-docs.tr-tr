---
title: Komut satırı verilerinden katman etkileşim verileri | Microsoft Docs
description: Bir veya daha fazla veritabanıyla iletişim kuran çok katmanlı uygulamalar için zaman uyumlu çağrılar için yürütme süresi bilgileri için katman etkileşim profili oluşturma kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f185cf57e118c923d8fbdfda6caa30a23059b9d2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634398"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Komut satırından katman etkileşim verileri ekleme

Katman etkileşimi profili oluşturma, bir veya daha fazla veritabanıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde zaman uyumlu çağrıların yürütme süreleri hakkında [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] ek bilgi sağlar.

**Windows 8 ve Windows Server 2012**

Masaüstü uygulamaları ve Windows 8 katman etkileşim verilerini Windows Server 2012 için ölçüm ölçüm yöntemini kullansanız gerekir. UWP uygulamaları üzerinde katman etkileşim verileri toplama desteklenmiyor.

**Visual Studio sürümleri**

Katman etkileşim profili oluşturma, herhangi bir sürüm kullanılarak Visual Studio. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise.

**Uzak makinede İPUCU verileri toplama**

Uzak makinede katman etkileşim verileri toplamak için **\_ vs_profiler**.exedosyasını bir Visual Studio makinesinin _\<Platform>_ **\_** _\<Language>_ **** _%VSInstallDir%_**\Team Tools\Performance Tools\Setups** klasöründen uzak bilgisayara kopyalamanız ve yüklemeniz gerekir. Uzaktan Hata Ayıklama indirme paketinde profil [oluşturma araçlarını kullanılamaz.](../debugger/remote-debugging.md)

**İpucu raporları**

Katman etkileşim verileri yalnızca Visual Studio Enterprise. [VSPerfReport](../profiling/vsperfreport.md) aracılığıyla dosya tabanlı katman etkileşim raporları kullanılamaz.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>VSPerfCmd ile katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı, komut satırı aracında kullanılabilen tüm işlevlere erişmenizi Profil Oluşturma Araçları. VSPerfCmd kullanılarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için **vsPerfCLREnv** yardımcı programını kullanarak katman etkileşim verilerini sağlayan ortam değişkenlerini ayarp kaldırmanız gerekir. Belirttiğiniz seçenekler ve veri toplamak için gereken yordamlar, profil oluşturma sırasında kullandığınız uygulamanın türüne bağlıdır.

## <a name="profile-stand-alone-applications"></a>Tek başına uygulamaların profilini oluşturma

SqlServer veritabanına zaman uyumlu çağrılar yapan bir Windows masaüstü uygulaması gibi başka bir işlem tarafından çalıştır olmayan bir uygulamaya katman etkileşim verileri eklemek için, ortam değişkenlerini ayarlamak için [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **VSPerfClrEnv /InteractionOn** seçeneğini ve bunları kaldırmak için **VSPerfClrEnv /InteractionOff** seçeneğini kullanın.

Aşağıdaki örnekte, Windows yöntemi kullanılarak bir masaüstü uygulamasının profili ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-desktop-application-example"></a>Bir masaüstü Windows profili oluşturma örneği

1. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. **Başlat'a** tıklayın, Tüm **Programlar'ın üzerine gelin** ve ardından Donatılar'ın **üzerine gelin.** Komut **İstemi'ne sağ tıklayın** ve ardından Yönetici Olarak **Çalıştır'a tıklayın.**

2. .NET profil oluşturmayı ve TIP ortam değişkenlerini başlatma. Aşağıdaki komutları yazın:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Profilleyiciyi başlatma. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. Uygulamayı VSPerfCmd ile başlatma. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Profil oluşturma verilerini toplamak için uygulamayı alıştırma yapın ve ardından uygulamayı normal şekilde kapatın.

6. TIP ortam değişkenlerini temizleme. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /off
    ```

Daha fazla bilgi için [bkz. Tek başına uygulamaların profilini oluşturma.](../profiling/command-line-profiling-of-stand-alone-applications.md)

## <a name="profile-services"></a>Profil hizmetleri

Uygulamalar dahil olmak üzere hizmetlerin profilini oluşturmak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **VSPerfClrEnv /GlobalInteractionOn** seçeneğini kullanarak ortam değişkenlerini ayarlayın ve **VSPerfClrEnv /GlobalInteractionOff** seçeneğini kullanarak bunları kaldırın.

Web uygulamaları da dahil olmak üzere hizmet profili oluşturma işlemi için genellikle profil [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] oluşturmayı etkinleştirmek için bilgisayarı yeniden başlatmanız gerekir.

Aşağıdaki örnekte, Windows yöntemi kullanılarak bir hizmet profili ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-service-example"></a>Bir Windows profili oluşturma örneği

1. Gerekirse hizmeti yükleyin.

2. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. **Başlat'a** tıklayın, Tüm **Programlar'ın üzerine gelin** ve ardından Donatılar'ın **üzerine gelin.** Komut **İstemi'ne sağ tıklayın** ve ardından Yönetici Olarak **Çalıştır'a tıklayın.**

3. .NET profil oluşturma ortam değişkenlerini başlatma. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. TIP ortam değişkenlerini başlatma. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

6. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın.

7. Profilleyiciyi başlatma. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. Gerekirse hizmeti başlatabilirsiniz.

9. Profiler'i hizmete ekleme. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Hizmeti alıştırma yapın ve profil oluşturma verilerini toplayın.

11. Profil oluşturmayı durdurun. Aşağıdaki komutu yazın:

     `vsperfcmd /detach`

12. .NET ve TIP profil oluşturma ortam değişkenlerini temizleme. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Temizilen ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

Daha fazla bilgi için aşağıdaki konulardan birine bakın:

[Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Profil hizmetleri](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı, Web uygulamalarının profilini kolayca [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] oluşturmanizi sağlar. **VSPerfCmd** komut satırı aracıyla karşılaştırıldığında, seçenekler azaltıldı, ortam değişkeni ayarlanmaz ve bilgisayarı yeniden başlatma gerekli değildir. VSPerfASPNETCmd'nin bu özellikleri, katman etkileşim verilerini toplamayı son derece kolaylaştırır.

VSPerfASPNETCmd kullanarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için komut satırına **/TIP** seçeneğini ekleyin. Örneğin, bir Web uygulaması için ölçümleme yöntemini kullanarak katman etkileşim verilerini [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] toplamak için aşağıdaki komut satırı kullanın:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

VSPerfASPNETCmd hakkında daha fazla bilgi için bkz. [VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)ile hızlı web sitesi profili oluşturma.
