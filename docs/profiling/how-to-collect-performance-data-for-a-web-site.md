---
title: Bir Web Sitesi Sunucusu için Performans Verileri | Microsoft
description: Bir web uygulamasının performans verilerini toplamak için Performans Sihirbazı'nı ASP.NET öğrenin. Uygulama yerel bilgisayarınızda çalışır ve yerel bilgisayarınızda Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 88a705ad675c5d546e884460b1b105bba18c77ac
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131462"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Nasıl kullanılır: Bir web sitesi için performans verileri toplama

Bir web uygulamasının **performans verilerini toplamak** için Performans Sihirbazı'nı [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kullanabilirsiniz. Visual Studio'de açık bir web uygulamasının profilini Visual Studio yerel bilgisayarınızda bulunan ve IDE'de açık olan bir Web sitesi [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Visual Studio.

> [!NOTE]
> Performans **Sihirbazı,** toplanan profil oluşturma verilerine katman etkileşimi (TIP) JScript veya her ikisini birden eklemenize olanak sağlar. İPUCU seçeneği, sunucu tarafı işlemlerden veri toplar. Profil JScript, yerel veya uzak bir Web sitesinde çalışan betiklerden veri toplar. Çoğu durumda seçeneklerden yalnızca birini seçmeniz gerekir.

 Bir yöneticinin kullanılabilir duruma yaptığı Kullanıcı Erişim İzinleri ayarlarına bağlı olarak, tek bir kullanıcı, profil oluşturma işlemini barındıran bilgisayarda bir profil oluşturma güvenlik iznine ASP.NET sahip olabilir. Aşağıdaki örnekler kullanıcılar arasındaki olası farkları göstermektedir:

- Yönetici, sürücüyü ve hizmeti başlatıyorken bazı kullanıcılar gelişmiş profil oluşturma özelliklerine erişebilirsiniz.

- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişimine sahip olabilir.

- Bazı kullanıcılar diğer tüm kullanıcılar için profil oluşturma erişimini reddeder.

  Daha fazla bilgi için [bkz.](../profiling/profiling-and-windows-vista-security.md) [VSPerfCmd'de](../profiling/vsperfcmd.md)Profil oluşturma ve Windows Vista güvenliği ve YÖNETİCI seçenekleri.

## <a name="to-profile-a-web-site-project"></a>Bir web sitesi projesinin profilini oluşturmak için

1. Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projesini Visual Studio.

2. Çözümle **menüsünde** **Performans Profili Oluşturucu'Performans Gezgini** **ve** ardından Başlat'ı **seçin.**

3. Sihirbazın ilk sayfasında bir profil oluşturma yöntemi seçin ve ardından Sonraki'ye **tıklayın.** Profil oluşturma yöntemleri hakkında daha fazla bilgi için [bkz. Performans toplama yöntemlerini anlama.](../profiling/understanding-performance-collection-methods.md) Eşzamanlılık görselleştiricisi profil oluşturma yönteminin web uygulamaları için kullanılabilir olmadığını unutmayın.

4. Profil **oluşturma için hangi uygulamayı** hedeflemek istediğiniz? açılan listesinde geçerli projenin seçili olduğundan emin olun ve ardından Sonraki 'ye **tıklayın.**

5. Sihirbazın üçüncü sayfasında katman etkileşim profili oluşturma (TIP) verileri, web sayfalarında çalışan JavaScript verileri veya her ikisi de eklemeyi seçebilirsiniz.

    - Katman etkileşimini toplamak için Katman Etkileşimi **Profili Oluşturmayı Etkinleştir onay** kutusunu seçin.

    - Web sayfalarında çalışan JavaScript'den veri toplamak için Profil **JavaScript onay** kutusunu seçin.

6. **İleri**’ye tıklayın.

7. Sihirbazın dördüncü sayfasında Son'a **tıklayın.**

8. Uygulama için bir performans [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] oturumu oluşturulur ve web sitesi tarayıcıda açılır. Profil oluşturmak istediğiniz işlevselliği kullanın ve ardından tarayıcıyı kapatın.

     Profil oluşturan veri dosyası oluşturulur ve ana pencerede verilerin Özet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] görünümü görüntülenir.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Web sitesinde proje açmadan bir web sitesi profili Visual Studio

1. Visual Studio'yu açın.

2. Çözümle **menüsünde** **Performans Profili Oluşturucu'Performans Gezgini** **ve** ardından Başlat'ı **seçin.**

3. Sihirbazın ilk sayfasında bir profil oluşturma yöntemi seçin ve ardından Sonraki'ye **tıklayın.** Daha fazla bilgi için [bkz. Performans Toplama Yöntemlerini Anlama.](../profiling/understanding-performance-collection-methods.md)

4. Sihirbazın ikinci sayfasında Profil oluşturma veya **JavaScript** ASP.NET seçeneğini belirleyin ve ardından Sonraki 'ye **tıklayın.**

5. Sihirbazın **üçüncü sayfasındaki Web** uygulaması hangi URL veya Yol çalıştıracak kutusuna uygulama giriş sayfasının URL'sini girin ve ardından Sonraki 'ye **tıklayın.**

   - Sunucu (IIS) tabanlı bir Web sitesi için gibi bir URL **<`http://localhost/MySite/default.aspx`>** yazın. Bu, mySite uygulama kökünde yerel bilgisayarda uygulamanın profilinin ve o sitenin default.aspx sayfasının oturumu başlatmak için Internet Explorer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] başlamasını sağlar.

   - Dosya tabanlı bir Web sitesi için file///**c:\WebSites\MySite\default.aspx** gibi bir yol yazın. Bu, c:\webSites\MySite konumunda bulunan uygulamanın profilinin ve oturumu başlatmak için Internet Explorer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] `http://localhost:nnnn/MySite/default.aspx` sayfasında başlatılamaya neden olur.

   - JavaScript verilerini toplamak istediğiniz dış siteler için URL'yi yazın, örneğin `http://www.contoso.com` .

     Daha fazla bilgi için, hedef ikili için özellik [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sayfalarını görüntüleme.

6. Sihirbazın üçüncü sayfasında katman etkileşim profili oluşturma (TIP) verileri, web sayfalarında çalışan JavaScript verileri veya her ikisi de eklemeyi seçebilirsiniz.

    - Katman etkileşimini toplamak için Katman Etkileşimi **Profili Oluşturmayı Etkinleştir onay** kutusunu seçin.

    - Web sayfalarında çalışan JavaScript'den veri toplamak için Profil **JavaScript onay** kutusunu seçin.

7. **İleri**’ye tıklayın.

8. Sihirbazın dördüncü sayfasında Son'a **tıklayın.**

9. ASP.NET uygulaması için bir performans oturumu oluşturulur ve web sitesi tarayıcıda açılır. Profil oluşturmak istediğiniz işlevselliği kullanın ve ardından tarayıcıyı kapatın.

     Profil oluşturan veri dosyası oluşturulur ve ana pencerede verilerin Özet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] görünümü görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

[Genel Bakışlar](../profiling/overviews-performance-tools.md) 
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Ölçüm ölçüm verisi değerlerini anlama](../profiling/understanding-instrumentation-data-values.md) 
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)
