---
title: 'Nasıl yapılır: bir Web sitesi için performans verilerini toplama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3307b5372852d6f3e269264a02fa2c90cb1acd22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787035"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Nasıl yapılır: bir Web sitesi için performans verilerini toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Web uygulaması için performans verilerini toplamak üzere **performans sihirbazını** kullanabilirsiniz [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . İçinde açık olan bir Web uygulamasını profilin profilini oluşturabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] yerel bilgisayarınızda bulunan ve IDE 'de açık olmayan bir Web sitesi profili oluşturabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> **Performans Sihirbazı** , toplanan profil oluşturma verilerine katman ETKILEŞIMI (tıp) verileri, JScript performans verileri veya her ikisini birden eklemenizi sağlar. Ipucu seçeneği, sunucu tarafı süreçlerinden veri toplar. JScript profil oluşturma, yerel veya uzak Web sitesinde çalışan betiklerden veri toplar. Çoğu durumda seçeneklerden yalnızca birini seçmeniz gerekir.  
  
 Yöneticinin kullanılabilir hale getirdiğine yönelik kullanıcı erişim Izinleri ayarlarına bağlı olarak, tek bir Kullanıcı, ASP.NET işlemini barındıran bilgisayarda bir profil oluşturucu oturumu oluşturmak için güvenlik iznine sahip olabilir veya olmayabilir. Aşağıdaki örneklerde kullanıcılar arasındaki olası farklılıklar gösterilmektedir:  
  
- Yönetici, sürücüyü ve hizmeti başlatmaya ayarladıktan sonra bazı kullanıcılar Gelişmiş profil oluşturma özelliklerine erişebilir.  
  
- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişimi sağlayabilir.  
  
- Bazı kullanıcılar, diğer tüm kullanıcılara profil oluşturma izni vermem.  
  
  Daha fazla bilgi için bkz. [profil oluşturma ve Windows Vista güvenliği](../profiling/profiling-and-windows-vista-security.md) ve [VSPerfCmd](../profiling/vsperfcmd.md)içindeki yönetici seçenekleri.  
  
### <a name="to-profile-a-web-site-project"></a>Bir Web sitesi projesi profili oluşturma  
  
1. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Web projesini veya içinde açın [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] .  
  
2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı tıklatın.  
  
3. Sihirbazın ilk sayfasında bir profil oluşturma yöntemi seçin ve ardından **İleri**' ye tıklayın. Profil oluşturma yöntemleri hakkında daha fazla bilgi için bkz. [performans toplama yöntemlerini anlama](../profiling/understanding-performance-collection-methods.md). Eşzamanlılık görselleştiricisi profil oluşturma yönteminin Web uygulamaları için kullanılabilir olmadığına unutmayın.  
  
4. **Profil oluşturmak Için hangi uygulamayı hedeflemek istiyorsunuz?** açılan listede, geçerli projenin seçili olduğundan emin olun ve ardından **İleri**' ye tıklayın.  
  
5. Sihirbazın üçüncü sayfasında, katman etkileşimi profil oluşturma (tıp) verilerini, Web sayfalarında çalışan JavaScript 'ten verileri veya her ikisini de eklemeyi seçebilirsiniz.  
  
    - Katman etkileşimini toplamak için **katman etkileşim profilini etkinleştir** onay kutusunu seçin.  
  
    - Web sayfalarında çalışan JavaScript 'ten veri toplamak için, **profil JavaScript** onay kutusunu seçin.  
  
6. **İleri**’ye tıklayın.  
  
7. Sihirbazın dördüncü sayfasında **son**' a tıklayın.  
  
8. Uygulama için bir performans oturumu oluşturulur [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ve Web sitesi tarayıcıda başlatılır. Profili eklemek istediğiniz işlevleri yapın ve ardından tarayıcıyı kapatın.  
  
     Profil Oluşturucu veri dosyasını oluşturur ve ana penceredeki verilerin özet görünümünü görüntüler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Visual Studio 'da bir proje açmadan bir Web sitesi profili oluşturma  
  
1. Veya öğesini açın [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] .  
  
2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı tıklatın.  
  
3. Sihirbazın ilk sayfasında bir profil oluşturma yöntemi seçin ve ardından **İleri**' ye tıklayın. Daha fazla bilgi için bkz. [performans toplama yöntemlerini anlama](../profiling/understanding-performance-collection-methods.md).  
  
4. Sihirbazın ikinci sayfasında, **profil a ASP.NET veya JavaScript uygulaması** seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.  
  
5. Sihirbazın üçüncü sayfasında **Web uygulamanızı HANGI URL veya yolda çalıştıracağınızı** , uygulama GIRIŞ sayfasına URL girin ve ardından **İleri**' ye tıklayın.  
  
   - Sunucu (IIS) tabanlı bir Web sitesi için gibi bir URL yazın **http://localhost/MySite/default.aspx** . Bunun nedeni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , Sitem 'in uygulama kökündeki yerel bilgisayardaki uygulamanın profili oluşturulabilir ve oturumu başlatmak Için Internet Explorer 'da bu sitede varsayılan. aspx sayfası başlatılır.  
  
   - Dosya tabanlı bir Web sitesi için, File///**c:\WebSites\MySite\default.aspx**gibi bir yol yazın. Bu, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] C:\websites\sitem konumundaki uygulamanın profili oluşturulabilir ve http://localhost:nnnn/MySite/default.aspx oturumu başlatmak Için Internet Explorer 'da sayfanın başlatılmasına neden olur.  
  
   - JavaScript verilerini toplamak istediğiniz dış sitelerde URL 'yi yazın, örneğin, http: \/ /www.contoso.com.  
  
     Daha fazla bilgi için, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] hedef ikilinin özellik sayfalarını görüntüleyin.  
  
6. Sihirbazın üçüncü sayfasında, katman etkileşimi profil oluşturma (tıp) verilerini, Web sayfalarında çalışan JavaScript 'ten verileri veya her ikisini de eklemeyi seçebilirsiniz.  
  
   - Katman etkileşimini toplamak için **katman etkileşim profilini etkinleştir** onay kutusunu seçin.  
  
   - Web sayfalarında çalışan JavaScript 'ten veri toplamak için, **profil JavaScript** onay kutusunu seçin.  
  
7. **İleri**’ye tıklayın.  
  
8. Sihirbazın dördüncü sayfasında **son**' a tıklayın.  
  
9. ASP.NET uygulaması için bir performans oturumu oluşturulur ve Web sitesi tarayıcıda başlatılır. Profili eklemek istediğiniz işlevleri yapın ve ardından tarayıcıyı kapatın.  
  
     Profil Oluşturucu veri dosyasını oluşturur ve ana penceredeki verilerin özet görünümünü görüntüler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tahmin](../profiling/overviews-performance-tools.md)   
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [Izleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)   
 [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)
