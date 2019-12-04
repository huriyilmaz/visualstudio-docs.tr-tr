---
title: 'Nasıl yapılır: bir Web sitesi için performans verilerini toplama | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779044"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Nasıl yapılır: bir Web sitesi için performans verilerini toplama

Bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması için performans verilerini toplamak üzere **performans sihirbazını** kullanabilirsiniz. Visual Studio 'da açık olan bir Web uygulaması profilini oluşturabilir veya yerel bilgisayarınızda bulunan ve Visual Studio IDE 'de açık olmayan bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web sitesinin profilini oluşturabilirsiniz.

> [!NOTE]
> **Performans Sihirbazı** , toplanan profil oluşturma verilerine katman ETKILEŞIMI (tıp) verileri, JScript performans verileri veya her ikisini birden eklemenizi sağlar. Ipucu seçeneği, sunucu tarafı süreçlerinden veri toplar. JScript profil oluşturma, yerel veya uzak Web sitesinde çalışan betiklerden veri toplar. Çoğu durumda seçeneklerden yalnızca birini seçmeniz gerekir.

 Yöneticinin kullanılabilir hale getirdiğine yönelik kullanıcı erişim Izinleri ayarlarına bağlı olarak, tek bir Kullanıcı, ASP.NET işlemini barındıran bilgisayarda bir profil oluşturucu oturumu oluşturmak için güvenlik iznine sahip olabilir veya olmayabilir. Aşağıdaki örneklerde kullanıcılar arasındaki olası farklılıklar gösterilmektedir:

- Yönetici, sürücüyü ve hizmeti başlatmaya ayarladıktan sonra bazı kullanıcılar Gelişmiş profil oluşturma özelliklerine erişebilir.

- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişimi sağlayabilir.

- Bazı kullanıcılar, diğer tüm kullanıcılar için profil oluşturmaya erişimi reddedebilirler.

  Daha fazla bilgi için bkz. [profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md) ve [VSPerfCmd](../profiling/vsperfcmd.md)içindeki yönetici seçenekleri.

## <a name="to-profile-a-web-site-project"></a>Bir Web sitesi projesi profili oluşturma

1. Visual Studio 'da [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web projesi ' ni açın.

2. **Çözümle** menüsünde, **performans profili Oluşturucu**' yı seçin, **Performans Gezgini**' yi seçin ve ardından **Başlat**' ı seçin.

3. Sihirbazın ilk sayfasında bir profil oluşturma yöntemi seçin ve ardından **İleri**' ye tıklayın. Profil oluşturma yöntemleri hakkında daha fazla bilgi için bkz. [performans toplama yöntemlerini anlama](../profiling/understanding-performance-collection-methods.md). Eşzamanlılık görselleştiricisi profil oluşturma yönteminin Web uygulamaları için kullanılabilir olmadığına unutmayın.

4. **Profil oluşturmak Için hangi uygulamayı hedeflemek istiyorsunuz?** açılan listede, geçerli projenin seçili olduğundan emin olun ve ardından **İleri**' ye tıklayın.

5. Sihirbazın üçüncü sayfasında, katman etkileşimi profil oluşturma (tıp) verilerini, Web sayfalarında çalışan JavaScript 'ten verileri veya her ikisini de eklemeyi seçebilirsiniz.

    - Katman etkileşimini toplamak için **katman etkileşim profilini etkinleştir** onay kutusunu seçin.

    - Web sayfalarında çalışan JavaScript 'ten veri toplamak için, **profil JavaScript** onay kutusunu seçin.

6. **İleri**'ye tıklayın.

7. Sihirbazın dördüncü sayfasında **son**' a tıklayın.

8. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulaması için bir performans oturumu oluşturulur ve Web sitesi tarayıcıda başlatılır. Profili eklemek istediğiniz işlevleri yapın ve ardından tarayıcıyı kapatın.

     Profil Oluşturucu veri dosyasını oluşturur ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ana penceresindeki verilerin özet görünümünü görüntüler.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Visual Studio 'da bir proje açmadan bir Web sitesi profili oluşturma

1. Visual Studio'yu açın.

2. **Çözümle** menüsünde, **performans profili Oluşturucu**' yı seçin, **Performans Gezgini**' yi seçin ve ardından **Başlat**' ı seçin.

3. Sihirbazın ilk sayfasında bir profil oluşturma yöntemi seçin ve ardından **İleri**' ye tıklayın. Daha fazla bilgi için bkz. [performans toplama yöntemlerini anlama](../profiling/understanding-performance-collection-methods.md).

4. Sihirbazın ikinci sayfasında, **profil a ASP.NET veya JavaScript uygulaması** seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.

5. Sihirbazın üçüncü sayfasında **Web uygulamanızı HANGI URL veya yolda çalıştıracağınızı** , uygulama GIRIŞ sayfasına URL girin ve ardından **İleri**' ye tıklayın.

   - Sunucu (IIS) tabanlı bir Web sitesi için **<`http://localhost/MySite/default.aspx`>** gıbı bir URL yazın. Bunun nedeni, Sitem 'in uygulama kökündeki yerel bilgisayardaki [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasının profili oluşturulabilir ve oturumu başlatmak için Internet Explorer 'da varsayılan. aspx sayfası başlatılır.

   - Dosya tabanlı bir Web sitesi için, File///**c:\WebSites\MySite\default.aspx**gibi bir yol yazın. Bu, C:\websites\sitem konumundaki [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasının profili oluşturulabilir ve oturumu başlatmak için Internet Explorer 'da `http://localhost:nnnn/MySite/default.aspx` sayfanın başlatılmasına neden olur.

   - JavaScript verilerini toplamak istediğiniz dış sitelerde URL 'yi yazın, örneğin `http://www.contoso.com`.

     Daha fazla bilgi için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hedef ikilisinin özellik sayfalarını görüntüleyin.

6. Sihirbazın üçüncü sayfasında, katman etkileşimi profil oluşturma (tıp) verilerini, Web sayfalarında çalışan JavaScript 'ten verileri veya her ikisini de eklemeyi seçebilirsiniz.

    - Katman etkileşimini toplamak için **katman etkileşim profilini etkinleştir** onay kutusunu seçin.

    - Web sayfalarında çalışan JavaScript 'ten veri toplamak için, **profil JavaScript** onay kutusunu seçin.

7. **İleri**'ye tıklayın.

8. Sihirbazın dördüncü sayfasında **son**' a tıklayın.

9. ASP.NET uygulaması için bir performans oturumu oluşturulur ve Web sitesi tarayıcıda başlatılır. Profili eklemek istediğiniz işlevleri yapın ve ardından tarayıcıyı kapatın.

     Profil Oluşturucu veri dosyasını oluşturur ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ana penceresindeki verilerin özet görünümünü görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

[Genel bakış](../profiling/overviews-performance-tools.md)
[performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
[izleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)
[örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)
