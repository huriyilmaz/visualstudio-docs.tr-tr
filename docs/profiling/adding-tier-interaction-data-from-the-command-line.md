---
title: Komut satırından katman etkileşim verileri ekleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 20b8438243382b28cccb510894d1674aa5872946
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779876"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Komut satırından katman etkileşim verileri ekleme

Katman etkileşimi profili oluşturma, bir veya daha fazla veritabanıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde zaman uyumlu [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] çağrılarının yürütme zamanları hakkında ek bilgiler sağlar.

**Windows 8 ve Windows Server 2012**

Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamalarında katman etkileşim verilerini toplamak için, izleme yöntemini kullanmanız gerekir. UWP uygulamalarında katman etkileşimi verilerinin toplanması desteklenmez.

**Visual Studio sürümleri**

Katman etkileşimi profili oluşturma, herhangi bir Visual Studio sürümü kullanılarak toplanabilir. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise görüntülenebilir.

**Uzak makinede Ipucu verileri toplama**

Uzak bir makinedeki katman etkileşimi verilerini toplamak için, bir Visual Studio makinesinin _% VSInstallDir%_ **\Team Tools\performance tools\kurulumları** klasöründeki **vs_profiler\_** _\<platform >_ **\_** _\<Language >_ **. exe** dosyasını uzak bilgisayara kopyalamanız ve kurmanız gerekir. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) indirme paketindeki profil oluşturma araçlarını kullanamazsınız.

**Ipucu raporları**

Katman etkileşim verileri yalnızca Visual Studio Enterprise ' de görüntülenebilir. [VSPerfReport](../profiling/vsperfreport.md) aracılığıyla dosya tabanlı katman etkileşimi raporları kullanılamaz.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>VSPerfCmd ile katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı, Profil Oluşturma Araçları bulunan tüm işlevselliğe erişmenize olanak tanır. VSPerfCmd kullanılarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için, **VSPerfCLREnv** yardımcı programını kullanarak katman etkileşim verileri sağlayan ortam değişkenlerini ayarlayıp kaldırmanız gerekir. Belirttiğiniz seçenekler ve veri toplamak için gereken yordamlar, profil oluşturduğunuz uygulamanın türüne bağlıdır.

## <a name="profile-stand-alone-applications"></a>Tek başına uygulamalar profili

Bir SQLServer veritabanına çağrı [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] çağrısı yapan bir Windows masaüstü uygulaması gibi başka bir işlem tarafından çalıştırılmayan bir uygulamaya katman etkileşim verileri eklemek için, ortam değişkenlerini ayarlamak için **VSPerfCLREnv/InteractionOn** seçeneğini ve bunları kaldırmak Için **VSPerfCLREnv/InteractionOff** seçeneğini kullanın.

Aşağıdaki örnekte, bir Windows masaüstü uygulaması, izleme yöntemi kullanılarak profili oluşturulur ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-desktop-application-example"></a>Bir Windows masaüstü uygulaması örneği profili oluşturma

1. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin ve **Donatılar**' ın üzerine gelin. **Komut istemi**' ne sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.

2. .NET profil oluşturma ve tıp ortam değişkenlerini başlatın. Aşağıdaki komutları yazın:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Profil oluşturucuyu başlatın. Şu komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. Uygulamayı VSPerfCmd ile başlatın. Şu komutu yazın:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Profil oluşturma verilerini toplamak için uygulamayı alıştırma yapın ve uygulamayı düzenli olarak kapatın.

6. Tıp ortam değişkenlerini temizleyin. Şu komutu yazın:

    ```cmd
    vsperfclrenv /off
    ```

Daha fazla bilgi için bkz. [tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Profil hizmetleri

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamalar dahil olmak üzere Hizmetleri profil kurmak için, ortam değişkenlerini ayarlamak için **VSPerfCLREnv/GlobalInteractionOn** seçeneğini ve bunları kaldırmak Için **VSPerfCLREnv/GlobalInteractionOff** seçeneğini kullanın.

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamaları dahil olmak üzere profil oluştururken genellikle, profil oluşturmayı etkinleştirmek için bilgisayarı yeniden başlatmanız gerekir.

Aşağıdaki örnekte, bir Windows hizmeti, izleme yöntemi kullanılarak profili oluşturulur ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-service-example"></a>Windows hizmeti örneği profili oluşturma

1. Gerekirse, hizmeti yükler.

2. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin ve **Donatılar**' ın üzerine gelin. **Komut istemi**' ne sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.

3. .NET profil oluşturma ortamı değişkenlerini başlatın. Şu komutu yazın:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Tıp ortam değişkenlerini başlatın. Şu komutu yazın:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

6. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın.

7. Profil oluşturucuyu başlatın. Şu komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. Gerekirse, hizmeti başlatın.

9. Profil oluşturucuyu hizmete ekleyin. Şu komutu yazın:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Hizmeti alıştırma yapın ve profil oluşturma verilerini toplayın.

11. Profil oluşturucuyu durdurun. Şu komutu yazın:

     `vsperfcmd /detach`

12. .NET ve tıp profil oluşturma ortam değişkenlerini temizleyin. Şu komutu yazın:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Temizlenmiş ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

Daha fazla bilgi için aşağıdaki konulardan birine bakın:

[ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Profil hizmetleri](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamalarını kolayca profilinize olanak sağlar. **VSPerfCmd** komut satırı aracıyla karşılaştırıldığında, seçenekler azalır, hiçbir ortam değişkeni ayarlanamaz ve bilgisayarın yeniden başlatılması gerekli değildir. VSPerfASPNETCmd 'nin bu özellikleri, katman etkileşimi verilerinin toplanmasını çok daha kolay hale getirir.

VSPerfASPNETCmd kullanılarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için, **/tip** seçeneğini komut satırına ekleyin. Örneğin, izleme yöntemini kullanarak bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasına ait katman etkileşim verilerini toplamak için aşağıdaki komut satırını kullanın:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

VSPerfASPNETCmd hakkında daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
