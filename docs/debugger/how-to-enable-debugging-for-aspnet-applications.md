---
title: ASP.NET uygulamaları için hata ayıklamayı | Microsoft Docs
description: ASP.NET ve ASP.NET Core uygulamaları için hata ayıklamayı etkinleştirmeyi Visual Studio. Bu işlemi bir IIS Express veya yerel IIS sunucusunda çalıştırabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: f452ed79ce12e7f5e8e265bbb46a3a011bb10328
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146949"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio'da ASP.NET veya ASP.NET Core uygulamalarının hatalarını ayıklama

Uygulamalarınız için hata ASP.NET ve ASP.NET Core hataları Visual Studio. bu işlem, ASP.NET ASP.NET Core ve yerel bir IIS sunucusunda IIS Express çalıştırmanız arasında farklılık gösterir.

>[!NOTE]
>Aşağıdaki adımlar ve ayarlar yalnızca yerel sunucuda hata ayıklama uygulamaları için geçerlidir. Uzak IIS sunucusundaki uygulamalarda hata ayıklama işlemi İşleme **Ekle'yi kullanır** ve bu ayarları yoksayar. IIS'de uygulamalarda uzaktan hata ayıklama ASP.NET daha fazla bilgi ve yönergeler için bkz. IIS [bilgisayarda uzaktan](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ASP.NET hata ayıklama veya uzak IIS ASP.NET Core uzaktan hata [ayıklama.](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)

Yerleşik IIS Express sunucusu, sunucuya Visual Studio. IIS Express, ASP.NET ve ASP.NET Core için varsayılan hata ayıklama sunucusudur ve önceden yapılandırılmıştır. Bu, hata ayıklamanın en kolay yolu ve ilk hata ayıklama ve test için idealdir.

Ayrıca, uygulamayı çalıştırmak ASP.NET ASP.NET Core bir IIS sunucusunda (sürüm 8.0 veya daha yüksek) bir uygulamanın hata ayıklaması da sebilirsiniz. Yerel IIS'de hata ayıklamak için aşağıdaki gereksinimleri karşılamanız gerekir:

<a name="iis"></a>
- Yüklü değilse, web geliştirme iş **ASP.NET yükleyin.** (Çalışma Visual Studio Yükleyicisi değiştir'i **seçin** ve bu iş yükünü ekleyin.)

   ::: moniker range="vs-2017"
   2017 Visual Studio de Geliştirme zamanı **IIS destek bileşenini** bulun. İş yükünü eklerken seçildiğinden emin olun.
   ::: moniker-end
- Visual Studio'yu yönetici olarak çalıştırın.
- IIS'yi uygulama ve/veya sanal ağların uygun ASP.NET ve/veya ASP.NET Core. IIS'yi ASP.NET Core kullanma hakkında daha fazla bilgi için [bkz. IIS ile ASP.NET Core Windows ana bilgisayar adı.](/aspnet/core/host-and-deploy/iis/index) Daha ASP.NET için [bkz. IIS ve ASP.NET Yükleme.](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules)
- Uygulamanın IIS üzerinde hatasız şekilde çalıştırıla olduğundan emin olun.

## <a name="debug-aspnet-apps"></a>Uygulamalarda ASP.NET ayıklama

IIS Express varsayılandır ve önceden yapılandırılmıştır. Yerel IIS'de hata ayıklarken, yerel IIS hata ayıklama [gereksinimlerini karşılarken emin olun.](#iis)

1. ASP.NET'Visual Studio **Çözüm Gezgini** simgesine tıklayın veya **Alt**  Enter tuşuna basın ya da özellikler'e sağ + tıklar ve **öğesini seçin.**

1. Web **sekmesini** seçin.

1. Özellikler **bölmesinde,** Sunucular **altında**,
   - Daha IIS Express açılan **listeden IIS Express'yi** seçin.
   - Yerel IIS için,
     1. Açılan **listeden Yerel IIS'yi** seçin.
     1. Uygulamayı **IIS Project henüz** **ayarlamadıysanız,** Sanal Dizin Oluştur url'sinin yanındaki öğesini seçin.

1. Hata **Ayıklayıcılar altında,** öğesini **ASP.NET.**

   ![ASP.NET ayıklayıcı ayarlarını değiştirme](media/dbg-aspnet-enable-debugging2.png "ASP.NET ayıklayıcı ayarlarını değiştirme")

1. Değişiklikleri **kaydetmek**  >  **için Seçilen Öğeleri Dosya** Kaydet'i seçin **(veya Ctrl** + **S** tuşlarına basın).

1. Uygulamada hata ayıklamak için projesinde bazı kodlarda kesme noktaları ayarlayın. Uygulama Visual Studio, yapılandırmanın Hata Ayıkla olarak ayarlendiğinden ve istediğiniz tarayıcının öykünücü alanında **IIS Express \<Browser name> ( )** veya Yerel IIS ( ) **\<Browser name> içinde** göründüğünden emin olun.

1. Hata ayıklamayı başlatmak için araç **çubuğundan IIS Express \<Browser name> ( )** veya  Yerel IIS (  **\<Browser name> )** öğesini seçin, Hata Ayıklama menüsünden Hata Ayıklamayı Başlat'ı seçin veya **F5 tuşuna basın.** Hata ayıklayıcısı kesme noktalarında duraklatılır. Hata ayıklayıcısı kesme noktalarına isabet edeee, [bkz. Hata ayıklama sorunlarını giderme.](#troubleshoot-debugging)

## <a name="debug-aspnet-core-apps"></a>Uygulamalarda ASP.NET Core ayıklama

IIS Express varsayılandır ve önceden yapılandırılmıştır. Yerel IIS'de hata ayıklarken, yerel IIS hata ayıklama [gereksinimlerini karşılarken emin olun.](#iis)

1. ASP.NET Core projesinde Visual Studio **Çözüm Gezgini** simgesine tıklayın veya **Alt**  Enter tuşuna basın veya sağ tıklar ve + Özellikler'i **seçin.**

1. Hata **Ayıkla sekmesini** seçin.

1. Özellikler **bölmesinde,** **Profil'in** yanındaki ,
   - Daha IIS Express açılan **listeden IIS Express'yi** seçin.
   - Yerel IIS için, açılan listeden uygulama adını seçin veya Yeni'yi **seçin,** yeni bir profil adı oluşturun ve Tamam'ı **seçin.**

1. **Başlat'ın** yanındaki açılan **listeden IIS Express** **VEYA IIS'yi** seçin.

1. Tarayıcıyı **başlat'ın seçili** olduğundan emin olun.

1. Ortam **değişkenleri altında,** geliştirme **ASPNETCORE_ENVIRONMENT** değerinin mevcut olduğundan emin **olun.** Yoksa **Ekle'yi seçin** ve ekleyin.

   ![ASP.NET Core hata ayıklayıcısı ayarlarını değiştirme](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core hata ayıklayıcısı ayarlarını değiştirme")

1. Değişiklikleri **kaydetmek**  >  **için Seçilen Öğeleri Dosya** Kaydet veya **Ctrl** + **S** tuşlarını kullanın.

1. Uygulamada hata ayıklamak için projesinde bazı kodlarda kesme noktaları ayarlayın. Visual Studio araç çubuğunda yapılandırmanın Hata Ayıkla olarak ayarlanmış olduğundan ve öykünücü **alanında IIS Express** veya yeni IIS profili adının göründüğünden emin olun.

1. Hata ayıklamayı başlatmak için, **hata IIS Express** seçin veya araç çubuğunda Hata Ayıklama menüsünden Hata Ayıklamayı Başlat'ı seçin **\<IIS profile name>** veya   **F5 tuşuna basın.** Hata ayıklayıcısı kesme noktalarında duraklatılır. Hata ayıklayıcısı kesme noktalarına isabet edeee, [bkz. Hata ayıklama sorunlarını giderme.](#troubleshoot-debugging)

## <a name="troubleshoot-debugging"></a>Hata ayıklama sorunlarını giderme

Yerel IIS hata ayıklaması kesme noktasıyla birlikte ilerleyene kadar ilerleyene kadar sorun gidermek için aşağıdaki adımları izleyin.

1. Web uygulamasını IIS'den başlatarak doğru şekilde çalıştırıla olduğundan emin olun. Web uygulamasını açık bırakın.

2. Bu Visual Studio Hata Ayıkla **>** İşleme Ekle'yi seçin veya **Ctrl** Alt P tuşlarına basın ve ASP.NET veya ASP.NET Core işleme +  + bağlanın (genellikle **w3wp.exeveya** **dotnet.exe).** Daha fazla bilgi için [bkz. İşleme](attach-to-running-processes-with-the-visual-studio-debugger.md) Ekleme ve İşlem [ASP.NET adı bulma.](how-to-find-the-name-of-the-aspnet-process.md)

İşleme Ekle'yi kullanarak bağlantı kurup kesme noktalarına isabet ediyorsanız, ancak Hata AyıklamaYı Başlatma Hata Ayıklama veya F5 kullanarak isabet alamasanız, proje özelliklerinde büyük olasılıkla  >   yanlış bir ayar vardır.  HOSTS dosyası kullanıyorsanız, dosyanın da doğru yapılandırıldığından emin olun.

## <a name="configure-debugging-in-the-webconfig-file"></a>web.config dosyasında hata ayıklamayı yapılandırma

ASP.NET projelerinde *varsayılanweb.config,* hata ayıklama ayarları da dahil olmak üzere uygulama yapılandırması ve başlatma bilgilerini içeren bir dosya vardır. Hata *web.config* hata ayıklama için doğru yapılandırıldığından emin olun. Önceki **bölümlerde** yer alan Özellikler ayarları, *web.config* dosyaları güncelleştirmektedir ancak bunları el ile de yapılandırabilirsiniz.

> [!NOTE]
> ASP.NET Core başlangıçta bir dosya *web.config,* ancak uygulama *yapılandırmasıappsettings.js* başlatma  bilgileri içinlaunchSettings.jsve dosyalarda veri yükleme kullanın. Uygulama dağıtılarak proje içinde *web.config* bir dosya veya dosya oluşturur, ancak genellikle hata ayıklama bilgileri içermez.

> [!TIP]
> Dağıtım işleminiz,web.config *ayarlarını* güncelleştirebilirsiniz, bu nedenle hata ayıklamayı denmeden önce hata ayıklama *web.config* yapılandırıldığından emin olun.

**Hata ayıklama için bir *web.config* el ile yapılandırmak için:**

1. Bu Visual Studio, ASP.NET projesinin *web.config* açın.

2. *Web.config* bir XML dosyası olduğu için etiketlerle işaretlenmiş iç içe geçmiş bölümler içerir. `configuration/system.web/compilation` bölümünü bulun. (Öğe `compilation` yoksa oluşturun.)

3. öğesinde `debug` özniteliğinin olarak `compilation` ayarlanmış olduğundan emin `true` olun. (Öğe `compilation` bir öznitelik `debug` içeriyorsa, ekleyin ve olarak `true` ayarlayın.)

   Varsayılan yapılandırma sunucusu yerine yerel IIS IIS Express, öğesinde öznitelik değerinin IIS sunucusundaki çerçeveyle eşle `targetFramework` `compilation` eş olduğundan emin olun.

   dosyanın `compilation`web.config aşağıdaki örnekteki gibi olması gerekir:

   > [!NOTE]
   > Bu örnek, kısmi bir *web.config* dosyasıdır. ve öğelerinde genellikle ek XML `configuration` bölümleri vardır ve öğesi diğer öznitelik ve öğeleri de `system.web` `compilation` içerebilir.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dosyalarda yapılan değişiklikleri otomatik *web.config* ve yeni yapılandırma ayarlarını uygular. Değişikliklerin etkili olması için bilgisayarı veya IIS sunucusunu yeniden başlatmanız gerek yoktur.

Web sitesi çeşitli sanal dizinler ve alt dizinler içerebilir ve her biri *web.config* birden fazla dosya içerebilir. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamaları, YAPıLANDıRMA ayarlarını *URLweb.config* üst düzeylerde yer alan dosyalardan devralınabilir. Hiyerarşik dosya *web.config* ayarları, hiyerarşide [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] altlarında yer alan tüm uygulamalar için geçerlidir. Hiyerarşinin alt köşesindeki *birweb.config* yapılandırmayı ayarlama, daha yüksek dosyada ayarları geçersiz kılar.

Örneğin, www.microsoft.com/aaa/web.config'de belirtirseniz, aaa klasöründeki veya `debug="true"` <em></em> *aaa'nın* herhangi  bir alt klasöründeki herhangi bir uygulama bu ayarı devralır, ancak bu uygulamalardan biri ayarı kendiweb.config *dosyasıyla geçersiz kılar.*

## <a name="publish-in-debug-mode-using-the-file-system"></a>Dosya sistemini kullanarak hata ayıklama modunda yayımlama

IIS'de uygulama yayımlamanın farklı yolları vardır. Bu adımlar, dosya sistemini kullanarak bir hata ayıklama Yayımlama profili oluşturma ve dağıtmayı gösterir. Bunu yapmak için yönetici olarak Visual Studio çalıştırmanız gerekir.

> [!IMPORTANT]
> Kodunuzu değiştirir veya yeniden oluşturmanız gerekirse, yeniden yayımlamak için bu adımları tekrarlamanız gerekir.

1. Bu Visual Studio projeye sağ tıklayın ve Yayımla'yı **seçin.**

3. **IIS, FTP vb. seçin ve** Yayımla'ya **tıklayın.**

    ![Bir yayımlama hedefi seçin iletişim kutusunun ekran görüntüsü Visual Studio. IIS, FTP ve Web Dağıtımı seçilidir ve Yayımla düğmesi vurgulanır.](media/dbg-aspnet-local-iis.png)

4. **CustomProfile iletişim kutusundaki** Publish method **(Yayımlama yöntemi) için File** system **(Dosya sistemi) öğesini seçin.**

5. Hedef **konum için Gözat**( ... ) öğesini **seçin.** 

   - Bu ASP.NET Yerel **IIS'yi** seçin, uygulama için oluşturduğunuz web sitesini seçin ve ardından Aç'ı **seçin.**

     ![IIS'ASP.NET yayımlama](media/dbg-aspnet-local-iis1.png "IIS'ASP.NET yayımlama")

   - Bu ASP.NET Core Dosya **Sistemi'ne** tıklayın, uygulama için ayar istediğiniz klasörü seçin ve ardından Aç'ı **seçin.**

1. **İleri**’yi seçin.

1. **Yapılandırma'nın** **altında, açılan listeden Hata** Ayıkla'ya seçin.

1. **Kaydet**’i seçin.

1. Yayımla **iletişim** kutusunda **CustomProfile** (veya yeni oluşturduğunuz profilin adı) göründüğünden ve **LastUsedBuildConfiguration** öğesinin Hata Ayıkla olarak ayarlanmış olduğundan **emin olun.**

1. **Yayımla**’yı seçin.

    ![Yayımla iletişim kutusunun ekran görüntüsü, CustomProfile uygulaması seçili, Yayımla düğmesi vurgulanmış ve LastBuildConfiguration Hata Ayıkla olarak ayarlanmış.](media/dbg-aspnet-local-iis-select-site.png)

> [!IMPORTANT]
> Hata ayıklama modu, uygulama performansını önemli ölçüde azaltır. En iyi performans için, üretimweb.configdağıtım veya performans ölçümleri yürüterek yayın `debug="false"` derlemesini belirtin. 

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET hata ayıklama: sistem gereksinimleri](aspnet-debugging-system-requirements.md)
- [Nasıl yapılır: Bir kullanıcı hesabı altında çalışan işlemini çalıştırma](how-to-run-the-worker-process-under-a-user-account.md)
- [Nasıl yapılır: ASP.NET işleminin adını bulma](how-to-find-the-name-of-the-aspnet-process.md)
- [Dağıtılan web uygulamalarında hata ayıklama](debugging-deployed-web-applications.md)
- [Adım adım kılavuz: Web formunda hata ayıklama](walkthrough-debugging-a-web-form.md)
- [Nasıl ASP.NET: ASP.NET ayıklama](how-to-debug-aspnet-exceptions.md)
- [Web uygulamalarında hata ayıklama: Hatalar ve sorun giderme](debugging-web-applications-errors-and-troubleshooting.md)
