---
title: 'Nasıl Kullanılır: Bir Web Sitesi için Performans Verileri Toplama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8b5cacba328c48b682fe9069d8ab4a9ee21635db
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302905"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Nasıl kullanılır: Bir web sitesi için performans verileri toplama

Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması için performans verileri toplamak için **Performans Sihirbazı'nı** kullanabilirsiniz. Visual Studio'da açık olan bir web uygulamasının profilini [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çıkarabilirsiniz veya yerel bilgisayarınızda bulunan ve Visual Studio IDE'de açık olmayan bir Web sitesinin profilini çıkarabilirsiniz.

> [!NOTE]
> **Performans Sihirbazı,** toplanan profil oluşturma verilerine katman etkileşimi (TIP) verileri, JScript performans verileri veya her ikisini de eklemenize olanak tanır. TIP seçeneği, sunucu tarafındaki işlemlerden veri toplar. JScript profil oluşturma yerel veya uzak bir Web sitesinde çalışan komut dosyaları veri toplar. Çoğu durumda, seçeneklerden yalnızca birini seçmeniz gerekir.

 Bir yöneticinin kullanıma sunmuş kullanıcı erişim izinleri ayarlarına bağlı olarak, tek bir kullanıcı nın bilgisayarda ASP.NET işlemini barındıran bir profil oluşturabilecek bir profiloluşturucu oturumu oluşturmak için güvenlik izni olabilir veya olmayabilir. Aşağıdaki örnekler, kullanıcılar arasındaki olası farklılıkları göstermektedir:

- Yönetici sürücüyü ve hizmeti başlatmaya ayarladığında bazı kullanıcılar gelişmiş profil oluşturma özelliklerine erişebilir.

- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişebilir.

- Bazı kullanıcılar diğer tüm kullanıcılara profil oluşturma erişimini reddedebilir.

  Daha fazla bilgi için, [VSPerfCmd'deki](../profiling/vsperfcmd.md) [Profil oluşturma ve Windows Vista güvenliği ve](../profiling/profiling-and-windows-vista-security.md) ADMIN seçeneklerine bakın.

## <a name="to-profile-a-web-site-project"></a>Bir web sitesi projesinin profilini çıkarmak için

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web projesini Visual Studio'da açın.

2. **Çözümle** menüsünde **Performans Profilcisi'ni**seçin, **Performans Gezgini'ni**seçin ve ardından **Başlat'ı**seçin.

3. Sihirbazın ilk sayfasında bir profil oluşturma yöntemini seçin ve sonra **İleri'yi**tıklatın. Profil oluşturma yöntemleri hakkında daha fazla bilgi için [bkz.](../profiling/understanding-performance-collection-methods.md) Eşzamanlı görselleştirici profil oluşturma yönteminin web uygulamaları için kullanılamadığını unutmayın.

4. Profil **oluşturma için hangi uygulamayı hedeflemek istiyorsunuz?** açılan listede, geçerli projenin seçildiğinden emin olun ve sonra **İleri'yi**tıklatın.

5. Sihirbazın üçüncü sayfasında, katman etkileşimi profil oluşturma (TIP) verileri, web sayfalarında çalışan JavaScript verileri veya her ikisi de eklemeyi seçebilirsiniz.

    - Katman etkileşimi toplamak için **Katman Etkileşimi Profil Oluşturmayı Etkinleştir** onay kutusunu seçin.

    - Web sayfalarında çalışan JavaScript'ten veri toplamak için **Profile JavaScript** onay kutusunu seçin.

6. **İleri**'ye tıklayın.

7. Sihirbazın dördüncü sayfasında **Finish'i**tıklatın.

8. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Uygulama için bir performans oturumu oluşturulur ve web sitesi tarayıcıda başlatılır. Profilini çıkarmak istediğiniz işlevselliği kullanın ve ardından tarayıcıyı kapatın.

     Profil oluşturucu veri dosyasını oluşturur ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ana penceredeki verilerin Özet görünümünü görüntüler.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Visual Studio'da proje açmadan bir web sitesinin profilini çıkarmak için

1. Visual Studio'yu açın.

2. **Çözümle** menüsünde **Performans Profilcisi'ni**seçin, **Performans Gezgini'ni**seçin ve ardından **Başlat'ı**seçin.

3. Sihirbazın ilk sayfasında bir profil oluşturma yöntemini seçin ve sonra **İleri'yi**tıklatın. Daha fazla bilgi için [bkz.](../profiling/understanding-performance-collection-methods.md)

4. Sihirbazın ikinci sayfasında, Profil **ASP.NET veya JavaScript uygulama** seçeneğini seçin ve sonra **İleri'yi**tıklatın.

5. Sihirbazın üçüncü sayfasında **web uygulama kutunuzu hangi URL veya Yol çalıştırır,** URL'yi uygulama giriş sayfasına girin ve **ardından İleri'yi**tıklatın.

   - Sunucu (IIS) tabanlı bir Web sitesi için, ** < `http://localhost/MySite/default.aspx` **'. Bu, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] MySite'nin uygulama kökündeki yerel bilgisayardaki uygulamanın profilinin ve bu sitedeki varsayılan.aspx sayfasının oturumu başlatmak için Internet Explorer'da başlatılmasına neden olur.

   - Dosya tabanlı bir Web sitesi için, dosya/**c:\WebSites\MySite\default.aspx**gibi bir yol yazın. Bu, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] c:\webSites\MySite adresinde bulunan uygulamanın profilinin `http://localhost:nnnn/MySite/default.aspx` ve oturumu başlatmak için Internet Explorer'da başlatılacak sayfanın başlatılmasına neden olur.

   - JavaScript verilerini toplamak istediğiniz harici siteler için, örneğin `http://www.contoso.com`URL'yi yazın.

     Daha fazla bilgi için, hedef [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ikili için özellik sayfalarını görüntüleyin.

6. Sihirbazın üçüncü sayfasında, katman etkileşimi profil oluşturma (TIP) verileri, web sayfalarında çalışan JavaScript verileri veya her ikisi de eklemeyi seçebilirsiniz.

    - Katman etkileşimi toplamak için **Katman Etkileşimi Profil Oluşturmayı Etkinleştir** onay kutusunu seçin.

    - Web sayfalarında çalışan JavaScript'ten veri toplamak için **Profile JavaScript** onay kutusunu seçin.

7. **İleri**'ye tıklayın.

8. Sihirbazın dördüncü sayfasında **Finish'i**tıklatın.

9. ASP.NET uygulaması için bir performans oturumu oluşturulur ve web sitesi tarayıcıda başlatılır. Profilini çıkarmak istediğiniz işlevselliği kullanın ve ardından tarayıcıyı kapatın.

     Profil oluşturucu veri dosyasını oluşturur ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ana penceredeki verilerin Özet görünümünü görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

[Genel BakışPerformans](../profiling/overviews-performance-tools.md)
[oturumlarını](../profiling/configuring-performance-sessions.md)
yapılandırma[Enstrümantasyon veri değerlerini](../profiling/understanding-instrumentation-data-values.md)
anlama Örnekleme veri değerlerini[anlama](../profiling/understanding-sampling-data-values.md)
