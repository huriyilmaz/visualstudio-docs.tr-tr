---
title: Komut satırından katman etkileşim verileri ekleme | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779876"
---
# <a name="add-tier-interaction-data-from-the-command-line"></a>Komut satırından katman etkileşim verileri ekleme

Katman etkileşimi profil oluşturma, bir veya daha [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] fazla veritabanıyla iletişim sağlayan çok katmanlı uygulamaların işlevlerinde eşzamanlı çağrıların yürütme süreleri hakkında ek bilgiler sağlar.

**Windows 8 ve Windows Server 2012**

Windows 8 masaüstü uygulamalarında ve Windows Server 2012 uygulamalarında katman etkileşim verileri toplamak için enstrümantasyon yöntemini kullanmanız gerekir. UWP uygulamalarında katman etkileşim verilerinin toplanması desteklenmez.

**Visual Studio sürümleri**

Seviye etkileşimi profiloluşturma Visual Studio herhangi bir sürümü kullanılarak toplanabilir. Ancak, katman etkileşimprofilleme verileri yalnızca Visual Studio Enterprise'da görüntülenebilir.

**Uzak bir makinede İpucu verileri toplama**

Uzak bir makinede katman etkileşim verilerini toplamak **\_için, vs_profiler**_\<Platformu>_ **\_** _ \<Dil>_ **.exe** dosyasını _%VSInstallDir%_**\Team Tools\Performance Tools\Setups** klasöründen uzak bilgisayara kopyalamanız ve yüklemeniz gerekir. [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md) indirme paketinde profil oluşturma araçlarını kullanamazsınız.

**TIP raporları**

Katman etkileşim verileri yalnızca Visual Studio Enterprise'da görüntülenebilir. [VSPerfReport](../profiling/vsperfreport.md) aracılığıyla dosya tabanlı katman etkileşim raporları kullanılamaz.

## <a name="add-tier-interaction-data-with-vsperfcmd"></a>VSPerfCmd ile katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı, Profil Oluşturma Araçları'nda bulunan tüm işlevselliklere erişmenizi sağlar. VSPerfCmd kullanarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için, katman etkileşim verilerini sağlayan ortam değişkenlerini ayarlamak ve kaldırmak için **VSPerfCLREnv** yardımcı programını kullanmanız gerekir. Belirttiğiniz seçenekler ve veri toplamak için gereken yordamlar profil oluşturma yaptığınız uygulamatürüne bağlıdır.

## <a name="profile-stand-alone-applications"></a>Profil tek başına uygulamalar

SQLServer veritabanına eşzamanlı [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] arama lar yapan bir Windows masaüstü uygulaması gibi başka bir işlem tarafından çalıştırılan bir uygulamaya katman etkileşim verileri eklemek için, ortam değişkenlerini ayarlamak için **VSPerfClrEnv /InteractionOn** seçeneğini ve bunları kaldırmak için **VSPerfClrEnv /InteractionOff** seçeneğini kullanın.

Aşağıdaki örnekte, bir Windows masaüstü uygulaması enstrümantasyon yöntemi kullanılarak profillenir ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-desktop-application-example"></a>Profil windows masaüstü uygulaması örneği

1. Yönetici ayrıcalıkları içeren bir komut istemi penceresi açın. **Başlat'ı**tıklatın, **Tüm Programlar'ı**işaret edin ve ardından **Aksesuarlar'ı işaret edin.** **Komut İstemi'ni**sağ tıklatın ve ardından **Yönetici Olarak Çalıştır'ı**tıklatın.

2. .NET profil oluşturma ve TIP ortamı değişkenlerini başlatma. Aşağıdaki komutları yazın:

    ```cmd
    vsperfclrenv /traceon
    vsperfclrenv /interactionon
    ```

3. Profilciyi çalıştırın. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:Desktop_tip.vsp
    ```

4. VSPerfCmd ile uygulamayı başlatın. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /launch:DesktopApp.exe
    ```

5. Profil oluşturma verilerini toplamak için uygulamayı egzersiz yapın ve uygulamayı düzenli olarak kapatın.

6. TIP ortamı değişkenlerini temizleyin. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /off
    ```

Daha fazla bilgi için [profil tek başına uygulamalara](../profiling/command-line-profiling-of-stand-alone-applications.md)bakın.

## <a name="profile-services"></a>Profil hizmetleri

Uygulamalar da dahil [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] olmak üzere profil hizmetleri için, ortam değişkenlerini ayarlamak için **VSPerfClrEnv /GlobalInteractionOn** seçeneğini ve bunları kaldırmak için **VSPerfClrEnv /GlobalInteractionOff** seçeneğini kullanın.

Web uygulamaları da [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dahil olmak üzere hizmetlerin profilini çıkarırken, profil oluşturmayı etkinleştirmek için genellikle bilgisayarı yeniden başlatmanız gerekir.

Aşağıdaki örnekte, bir Windows hizmeti enstrümantasyon yöntemi kullanılarak profillenir ve katman etkileşim verileri toplanır.

### <a name="profile-a-windows-service-example"></a>Profil bir Windows hizmeti örneği

1. Gerekirse hizmeti yükleyin.

2. Yönetici ayrıcalıkları içeren bir komut istemi penceresi açın. **Başlat'ı**tıklatın, **Tüm Programlar'ı**işaret edin ve ardından **Aksesuarlar'ı işaret edin.** **Komut İstemi'ni**sağ tıklatın ve ardından **Yönetici Olarak Çalıştır'ı**tıklatın.

3. .NET profil oluşturma ortamı değişkenlerini başlangıç olarak gün,. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /globaltraceon
    ```

4. TIP ortamı değişkenlerini başlangıç olarak ver. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /globalinteractionon
    ```

5. Ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

6. Yönetici ayrıcalıkları içeren bir komut istemi penceresi açın.

7. Profilciyi çalıştırın. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession
    ```

8. Gerekirse hizmeti başlatın.

9. ProfiloluşturcIyi servise takın. Aşağıdaki komutu yazın:

    ```cmd
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession
    ```

10. Hizmeti çalıştırın ve profil oluşturma verilerini toplayın.

11. Profilciyi durdur. Aşağıdaki komutu yazın:

     `vsperfcmd /detach`

12. .NET ve TIP profil oluşturma ortamı değişkenlerini temizleyin. Aşağıdaki komutu yazın:

    ```cmd
    vsperfclrenv /globaloff
    ```

13. Temizlenen ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.

Daha fazla bilgi için aşağıdaki konulardan birine bakın:

[Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)

[Profil hizmetleri](../profiling/command-line-profiling-of-services.md)

## <a name="add-tier-interaction-data-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile katman etkileşim verileri ekleme

VSPerfASPNETCmd komut satırı aracı, Web uygulamalarının kolayca profilini [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çıkarabilmenizi sağlar. **VSPerfCmd** komut satırı aracıyla karşılaştırıldığında seçenekler azalır, ortam değişkenlerinin ayarlanması gerekmez ve bilgisayarın yeniden başlatılması gerekmez. VSPerfASPNETCmd'nin bu özellikleri, katman etkileşim verilerinin toplanmasını son derece kolaylaştırır.

VSPerfASPNETCmd kullanılarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için komut satırına **/TIP** seçeneğini ekleyin. Örneğin, enstrümantasyon yöntemini kullanarak bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması için katman etkileşim verileri toplamak için aşağıdaki komut satırını kullanın:

```cmd
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp
```

VSPerfASPNETCmd hakkında daha fazla bilgi için, [VSPerfASPNETCmd ile Hızlı web sitesi profilleme](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)bakın.
