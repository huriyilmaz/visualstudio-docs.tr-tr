---
title: Komut satırından katman etkileşim verileri ekleme | Microsoft Docs
description: Bir veya daha fazla veritabanıyla iletişim kuran çok katmanlı uygulamalarda, zaman uyumlu çağrılar için yürütme zaman bilgileri için katman etkileşim profili oluşturma kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9070e515fd59f7b29427f20322ef6cb1a01afaee
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901328"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Komut satırından katman etkileşim verileri ekleme

Katman etkileşimi profili oluşturma, [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] bir veya daha fazla veritabanı ile iletişim kuran çok katmanlı uygulamaların işlevlerinde zaman uyumlu çağrıların yürütme zamanları hakkında ek bilgiler sağlar.

**Windows 8 ve Windows Server 2012**

Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamalarında katman etkileşim verilerini toplamak için, izleme yöntemini kullanmanız gerekir. UWP uygulamalarında katman etkileşimi verilerinin toplanması desteklenmez.

**Visual Studio sürümleri**

Katman etkileşimi profili oluşturma, herhangi bir Visual Studio sürümü kullanılarak toplanabilir. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise görüntülenebilir.

**Uzak makinede Ipucu verileri toplama**

Uzak bir makinedeki katman etkileşimi verilerini toplamak için, **\_ vs_profiler** _\<Platform>_ **\_** _\<Language>_ **. exe** dosyasını bir Visual Studio makinesinin _% VSInstallDir%_**\Team Tools\Performance tools\kurulumları** klasöründen uzak bilgisayara kopyalamanız ve kurmanız gerekir. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) indirme paketindeki profil oluşturma araçlarını kullanamazsınız.

**Ipucu raporları**

Katman etkileşim verileri yalnızca Visual Studio Enterprise ' de görüntülenebilir. [VSPerfReport](../profiling/vsperfreport.md) aracılığıyla dosya tabanlı katman etkileşimi raporları kullanılamaz.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>VSPerfCmd ile katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı, Profil Oluşturma Araçları bulunan tüm işlevselliğe erişmenize olanak tanır. VSPerfCmd kullanılarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için, **VSPerfCLREnv** yardımcı programını kullanarak katman etkileşim verileri sağlayan ortam değişkenlerini ayarlayıp kaldırmanız gerekir. Belirttiğiniz seçenekler ve veri toplamak için gereken yordamlar, profil oluşturduğunuz uygulamanın türüne bağlıdır.

## <a name="profile-stand-alone-applications"></a>Tek başına uygulamalar profili

Bir SQLServer veritabanına zaman uyumlu çağrılar yapan bir Windows masaüstü uygulaması gibi başka bir işlem tarafından çalıştırılmayan bir uygulamaya katman etkileşim verileri eklemek için [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] , ortam değişkenlerini ayarlamak Için **VSPerfCLREnv/InteractionOn** seçeneğini ve bunları kaldırmak Için **VSPerfCLREnv/InteractionOff** seçeneğini kullanın.

Aşağıdaki örnekte, bir Windows masaüstü uygulaması, izleme yöntemi kullanılarak profili oluşturulur ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-desktop-application-example"></a>Bir Windows masaüstü uygulaması örneği profili oluşturma

1. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin ve **Donatılar**' ın üzerine gelin. **Komut istemi**' ne sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.

2. .NET profil oluşturma ve tıp ortam değişkenlerini başlatın. Aşağıdaki komutları yazın:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Profil oluşturucuyu başlatın. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. Uygulamayı VSPerfCmd ile başlatın. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Profil oluşturma verilerini toplamak için uygulamayı alıştırma yapın ve uygulamayı düzenli olarak kapatın.

6. Tıp ortam değişkenlerini temizleyin. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /off
    ```

Daha fazla bilgi için bkz. [tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md).

## <a name="profile-services"></a>Profil hizmetleri

Uygulamalar dahil olmak üzere Hizmetleri profili eklemek için, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ortam değişkenlerini ayarlamak Için **VSPerfCLREnv/GlobalInteractionOn** seçeneğini ve bunları kaldırmak Için **VSPerfCLREnv/GlobalInteractionOff** seçeneğini kullanın.

Web uygulamaları dahil olmak üzere profil oluştururken [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] genellikle, profil oluşturmayı etkinleştirmek için bilgisayarı yeniden başlatmanız gerekir.

Aşağıdaki örnekte, bir Windows hizmeti, izleme yöntemi kullanılarak profili oluşturulur ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-service-example"></a>Windows hizmeti örneği profili oluşturma

1. Gerekirse, hizmeti yükler.

2. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin ve **Donatılar**' ın üzerine gelin. **Komut istemi**' ne sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.

3. .NET profil oluşturma ortamı değişkenlerini başlatın. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. Tıp ortam değişkenlerini başlatın. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

6. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın.

7. Profil oluşturucuyu başlatın. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. Gerekirse, hizmeti başlatın.

9. Profil oluşturucuyu hizmete ekleyin. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Hizmeti alıştırma yapın ve profil oluşturma verilerini toplayın.

11. Profil oluşturucuyu durdurun. Aşağıdaki komutu yazın:

     `vsperfcmd /detach`

12. .NET ve tıp profil oluşturma ortam değişkenlerini temizleyin. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Temizlenmiş ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

Daha fazla bilgi için aşağıdaki konulardan birine bakın:

[ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Profil hizmetleri](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı, Web uygulamalarını kolayca profillemenize olanak sağlar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . **VSPerfCmd** komut satırı aracıyla karşılaştırıldığında, seçenekler azalır, hiçbir ortam değişkeni ayarlanamaz ve bilgisayarın yeniden başlatılması gerekli değildir. VSPerfASPNETCmd 'nin bu özellikleri, katman etkileşimi verilerinin toplanmasını çok daha kolay hale getirir.

VSPerfASPNETCmd kullanılarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için, **/tip** seçeneğini komut satırına ekleyin. Örneğin, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] izleme yöntemini kullanarak bir Web uygulaması için katman etkileşimi verilerini toplamak üzere aşağıdaki komut satırını kullanın:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

VSPerfASPNETCmd hakkında daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
