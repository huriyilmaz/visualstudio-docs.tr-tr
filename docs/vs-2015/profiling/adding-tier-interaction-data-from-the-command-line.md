---
title: Komut satırından katman etkileşim verileri ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 369c5b75780e9d557dedbde60b5b584c8b3345b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705843"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Komut satırından katman etkileşim verileri ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Katman etkileşimi profili oluşturma, [!INCLUDE[vstecado](../includes/vstecado-md.md)] bir veya daha fazla veritabanı ile iletişim kuran çok katmanlı uygulamaların işlevlerinde zaman uyumlu çağrıların yürütme zamanları hakkında ek bilgiler sağlar.  
  
 **Windows 8 ve Windows Server 2012**  
  
 Windows 8 masaüstü uygulamaları ve Windows Server 2012 uygulamalarında katman etkileşim verilerini toplamak için, izleme yöntemini kullanmanız gerekir. Windows Mağazası uygulamalarında katman etkileşimi verilerinin toplanması desteklenmez.  
  
 **Visual Studio sürümleri**  
  
 Katman etkileşimi profili oluşturma,, veya kullanılarak toplanabilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] . Ancak, katman etkileşimi profil oluşturma verileri yalnızca ve ' de [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] görüntülenebilir [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
  
 **Uzak makinede Ipucu verileri toplama**  
  
 Uzak bir makinedeki katman etkileşimi verilerini toplamak için, **vs \_ Profiler \_ ** _\<Platform>_ **\_** _\<Language>_ **. exe** dosyasını bir Visual Studio makinesinin _% VSInstallDir%_**\Team Tools\Performance tools\kurulumları** klasöründen uzak bilgisayara kopyalamanız ve kurmanız gerekir. [Visual Studio uzak Araçlar](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) indirme paketindeki profil oluşturma araçlarını kullanamazsınız.  
  
 **Ipucu raporları**  
  
 Katman etkileşim verileri yalnızca IDE 'de görüntülenebilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] . [VSPerfReport](../profiling/vsperfreport.md) aracılığıyla dosya tabanlı katman etkileşimi raporları kullanılamaz.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>VSPerfCmd ile katman etkileşim verileri ekleme  
 VSPerfASPNETCmd komut satırı aracı, Profil Oluşturma Araçları bulunan tüm işlevselliğe erişmenize olanak tanır. VSPerfCmd kullanılarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için, **VSPerfCLREnv** yardımcı programını kullanarak katman etkileşim verileri sağlayan ortam değişkenlerini ayarlayıp kaldırmanız gerekir. Belirttiğiniz seçenekler ve veri toplamak için gereken yordamlar, profil oluşturduğunuz uygulamanın türüne bağlıdır.  
  
### <a name="profiling-stand-alone-applications"></a>Tek başına uygulamaların profilini oluşturma  
 Bir SQLServer veritabanına zaman uyumlu çağrılar yapan bir Windows masaüstü uygulaması gibi başka bir işlem tarafından çalıştırılmayan bir uygulamaya katman etkileşim verileri eklemek için [!INCLUDE[vstecado](../includes/vstecado-md.md)] , ortam değişkenlerini ayarlamak Için **VSPerfCLREnv/InteractionOn** seçeneğini ve bunları kaldırmak Için **VSPerfCLREnv/InteractionOff** seçeneğini kullanın.  
  
 Aşağıdaki örnekte, bir Windows masaüstü uygulaması, izleme yöntemi kullanılarak profili oluşturulur ve katman etkileşim verileri toplanır.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Windows masaüstü uygulaması örneği profili oluşturma  
  
1. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin ve **Donatılar**' ın üzerine gelin. **Komut istemi**' ne sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.  
  
2. .NET profil oluşturma ve tıp ortam değişkenlerini başlatın. Aşağıdaki komutları yazın:  
  
   ```  
   vsperfclrenv /traceon  
   vsperfclrenv /interactionon  
   ```  
  
3. Profil oluşturucuyu başlatın. Aşağıdaki komutu yazın:  
  
   ```  
   vsperfcmd /start:trace /output:Desktop_tip.vsp   
   ```  
  
4. Uygulamayı VSPerfCmd ile başlatın. Aşağıdaki komutu yazın:  
  
   ```  
   vsperfcmd /launch:DesktopApp.exe  
   ```  
  
5. Profil oluşturma verilerini toplamak için uygulamayı alıştırma yapın ve uygulamayı düzenli olarak kapatın.  
  
6. Tıp ortam değişkenlerini temizleyin. Aşağıdaki komutu yazın:  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   Daha fazla bilgi için bkz. [tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Profil oluşturma hizmetleri  
 Uygulamalar dahil olmak üzere Hizmetleri profili eklemek için, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ortam değişkenlerini ayarlamak Için **VSPerfCLREnv/GlobalInteractionOn** seçeneğini ve bunları kaldırmak Için **VSPerfCLREnv/GlobalInteractionOff** seçeneğini kullanın.  
  
 Web uygulamaları dahil olmak üzere profil oluştururken [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] genellikle, profil oluşturmayı etkinleştirmek için bilgisayarı yeniden başlatmanız gerekir.  
  
 Aşağıdaki örnekte, bir Windows hizmeti, işaretleme yöntemi kullanılarak profili oluşturulur ve katman etkileşim verileri toplanır.  
  
##### <a name="profiling-a-windows-service-example"></a>Windows hizmeti örneği profili oluşturma  
  
1. Gerekirse, hizmeti yükler.  
  
2. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın. **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin ve **Donatılar**' ın üzerine gelin. **Komut istemi**' ne sağ tıklayın ve ardından **yönetici olarak çalıştır**' a tıklayın.  
  
3. .NET profil oluşturma ortamı değişkenlerini başlatın. Aşağıdaki komutu yazın:  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. Tıp ortam değişkenlerini başlatın. Aşağıdaki komutu yazın  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. Ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.  
  
6. Yönetici ayrıcalıklarıyla bir komut istemi penceresi açın.  
  
7. Profil oluşturucuyu başlatın. Aşağıdaki komutu yazın:  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. Gerekirse, hizmeti başlatın.  
  
9. Profil oluşturucuyu hizmete ekleyin. Aşağıdaki komutu yazın:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Hizmeti alıştırma yapın ve profil oluşturma verilerini toplayın.  
  
11. Profil oluşturucuyu durdurun. Aşağıdaki komutu yazın:  
  
     `vsperfcmd /detach`  
  
12. .NET ve tıp profil oluşturma ortam değişkenlerini temizleyin. Aşağıdaki komutu yazın:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Temizlenmiş ortam değişkenlerini kaydetmek için bilgisayarı yeniden başlatın.  
  
    Daha fazla bilgi için aşağıdaki konulardan birine bakın:  
  
    [ASP.NET Web Uygulamalarında Profil Oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd ile katman etkileşim verileri ekleme  
 VSPerfASPNETCmd komut satırı aracı, Web uygulamalarını kolayca profillemenize olanak sağlar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . **VSPerfCmd** komut satırı aracıyla karşılaştırıldığında, seçenekler azalır, hiçbir ortam değişkeni ayarlanamaz ve bilgisayarın yeniden başlatılması gerekli değildir. VSPerfASPNETCmd 'nin bu özellikleri, katman etkileşimi verilerinin toplanmasını çok daha kolay hale getirir.  
  
 VSPerfASPNETCmd kullanılarak toplanan profil oluşturma verilerine katman etkileşimi eklemek için, **/tip** seçeneğini komut satırına ekleyin. Örneğin, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] izleme yöntemini kullanarak bir Web uygulaması için katman etkileşimi verilerini toplamak üzere aşağıdaki komut satırını kullanın:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 VSPerfASPNETCmd hakkında daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).
