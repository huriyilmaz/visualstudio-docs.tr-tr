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
ms.workload:
- aspnet
ms.openlocfilehash: 1fd620a0c7f4860421b6f8b1a15c0b708c1ba860
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729266"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio'da ASP.NET veya ASP.NET Core uygulamalarının hatalarını ayıklama

ASP.NET ve ASP.NET Core Visual Studio. İşlem, ASP.NET ASP.NET Core ile IIS Express veya yerel bir IIS sunucusunda çalıştırmanız arasında farklılık gösterir.

>[!NOTE]
>Aşağıdaki adımlar ve ayarlar yalnızca yerel sunucuda hata ayıklama uygulamaları için geçerlidir. Uzak IIS sunucusundaki uygulamalarda hata ayıklama işlemi İşleme **Ekle'yi kullanır** ve bu ayarları yoksayar. IIS'de uygulamalarda uzaktan hata ayıklama ASP.NET daha fazla bilgi ve yönergeler için bkz. IIS bilgisayarda uzaktan hata ayıklama [ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) veya uzak IIS bilgisayarında Uzaktan hata ayıklama [ASP.NET Core.](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)

Yerleşik IIS Express sunucusu, Visual Studio. IIS Express, ASP.NET ve ASP.NET Core projeleri için varsayılan hata ayıklama sunucusudur ve önceden yapılandırılmıştır. Bu, hata ayıklamanın en kolay yolu ve ilk hata ayıklama ve test için idealdir.

Ayrıca, uygulamayı çalıştırmak için yapılandırılmış ASP.NET veya ASP.NET Core uygulamasında (sürüm 8.0 veya üst sürümü) bir ASP.NET Core uygulamasında da hata ayıkabilirsiniz. Yerel IIS'de hata ayıklamak için aşağıdaki gereksinimleri karşılamanız gerekir:

<a name="iis"></a>
- Yüklü değilse, uygulama ve **web ASP.NET yükleyin.** (Çalışma Visual Studio Yükleyicisi **değiştir'i seçin** ve bu iş yükünü ekleyin.)

   ::: moniker range="vs-2017"
   2017 Visual Studio de Geliştirme zamanı **IIS destek bileşenini** bulun. İş yükünü eklerken seçildiğinden emin olun.
   ::: moniker-end
- Visual Studio'yu yönetici olarak çalıştırın.
- IIS'yi ASP.NET ve/veya ASP.NET Core'un uygun ASP.NET yükleyin. IIS'yi ASP.NET Core ile kullanma hakkında daha fazla bilgi için bkz. [IIS ile Windows'ASP.NET Çekirdeği'ni barındırma.](/aspnet/core/host-and-deploy/iis/index) Daha ASP.NET için [bkz. IIS ve ASP.NET Yükleme.](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules)
- Uygulamanın IIS 'de hata olmadan çalıştığından emin olun.

## <a name="debug-aspnet-apps"></a>ASP.NET uygulamalarında hata ayıklama

IIS Express varsayılandır ve önceden yapılandırılmıştır. Yerel IIS 'de hata ayıklaması yapıyorsanız, [yerel IIS hata ayıklama gereksinimlerini](#iis)karşıladığınızdan emin olun.

1. Visual Studio 'da ASP.NET projesini seçin **Çözüm Gezgini** ve **Özellikler** simgesine tıklayın veya **alt** + **ENTER** tuşuna basın ya da sağ tıklayıp **Özellikler**' i seçin.

1. **Web** sekmesini seçin.

1. **Özellikler** bölmesinde, **sunucular** altında,
   - IIS Express için, açılan listeden **IIS Express** seçin.
   - Yerel IIS için
     1. Açılan listeden **yerel IIS** ' yi seçin.
     1. Uygulamayı henüz IIS 'de ayarlamadıysanız, **proje URL 'si** alanının yanında, **sanal dizin oluştur**' u seçin.

1. **Hata ayıklayıcılar** altında **ASP.net**' yi seçin.

   ![ASP.NET hata ayıklayıcısı ayarları](media/dbg-aspnet-enable-debugging2.png "ASP.NET hata ayıklayıcısı ayarları")

1.   >  Değişiklikleri kaydetmek için dosya **Seçili öğeleri kaydet** ' i (veya **CTRL** + **'leri** tuşlarına basın) seçin.

1. Uygulamada hata ayıklamak için, projenizde, bazı koddaki kesme noktaları ayarlayın. Visual Studio araç çubuğunda, yapılandırmanın **hata ayıklama** olarak ayarlandığından ve istediğiniz tarayıcının öykünücü alanında **IIS Express ( \<Browser name> )** veya **yerel IIS ( \<Browser name> )** içinde göründüğünden emin olun.

1. Hata ayıklamayı başlatmak için, araç çubuğunda **IIS Express ( \<Browser name> )** veya **yerel IIS ( \<Browser name> )** seçeneğini belirleyin, **Hata Ayıkla** menüsünden **hata ayıklamayı Başlat** ' ı seçin veya **F5** tuşuna basın. Hata ayıklayıcı kesme noktalarında duraklatılır. Hata ayıklayıcı kesme noktalarına ulaşamıyorum, bkz. [hata ayıklama sorun giderme](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>ASP.NET Core uygulamalarda hata ayıkla

IIS Express varsayılandır ve önceden yapılandırılmıştır. Yerel IIS'de hata ayıklarken, yerel IIS hata ayıklama [gereksinimlerini karşılarken emin olun.](#iis)

1. Visual Studio Çözüm Gezgini'daki ASP.NET Core projesini  seçin ve Özellikler simgesine tıklayın veya **Alt**  Enter tuşuna basın veya sağ + tıklar ve Özellikler'i **seçin.**

1. Hata **Ayıkla sekmesini** seçin.

1. Özellikler **bölmesinde,** **Profil'in** yanındaki ,
   - Daha IIS Express açılan **listeden IIS Express'yi** seçin.
   - Yerel IIS için, açılan listeden uygulama adını seçin veya Yeni'yi **seçin,** yeni bir profil adı oluşturun ve Tamam'ı **seçin.**

1. **Başlat'ın** yanındaki açılan **listeden IIS Express** **VEYA IIS'yi** seçin.

1. Tarayıcıyı **başlat'ın seçili** olduğundan emin olun.

1. Ortam **değişkenleri altında,** geliştirme **ASPNETCORE_ENVIRONMENT** değerinin mevcut olduğundan emin **olun.** Yoksa **Ekle'yi seçin** ve ekleyin.

   ![ASP.NET Çekirdek hata ayıklayıcısı ayarları](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core hata ayıklayıcı ayarları")

1. Değişiklikleri **kaydetmek**  >  **için Seçilen Öğeleri Dosya** Kaydet veya **Ctrl** + **S** tuşlarını kullanın.

1. Uygulamada hata ayıklamak için projesinde bazı kodlarda kesme noktaları ayarlayın. Uygulama Visual Studio, yapılandırmanın Hata Ayıkla olarak ayarlanmış olduğundan ve öykünücü **alanında IIS Express** veya yeni IIS profili adının göründüğünden emin olun.

1. Hata ayıklamayı başlatmak için hata **ayıklamayı IIS Express** araç çubuğundan Hata Ayıklamayı Başlat'ı seçin veya **\<IIS profile name>** **F5 tuşuna basın.**   Hata ayıklayıcısı kesme noktalarında duraklatılır. Hata ayıklayıcısı kesme noktalarına isabet edeee, bkz. [Hata ayıklama sorunlarını giderme.](#troubleshoot-debugging)

## <a name="troubleshoot-debugging"></a>Hata ayıklama sorunlarını giderme

Yerel IIS hata ayıklaması kesme noktasıyla birlikte ilerleyene kadar ilerleyene kadar sorun gidermek için aşağıdaki adımları izleyin.

1. Web uygulamasını IIS 'den başlatın ve düzgün çalıştığından emin olun. Web uygulamasını çalışır durumda bırakın.

2. Visual Studio 'da, **işleme eklemek > hata ayıkla** ' yı seçin veya **CTRL** + **alt** + **P** tuşlarına basın ve ASP.NET veya ASP.NET Core işlemine bağlanın (genellikle **w3wp.exe** veya **dotnet.exe**). Daha fazla bilgi için bkz. [Işleme iliştirme](attach-to-running-processes-with-the-visual-studio-debugger.md) ve [ASP.NET işleminin adını bulma](how-to-find-the-name-of-the-aspnet-process.md).

**Hata ayıklama** başlatma hata ayıklaması veya F5 kullanarak, **İşleme İliştir**' i kullanarak bağlanıp kesme noktasına ulaşırsanız  >   , proje özelliklerinde bir ayar büyük olasılıkla yanlış olur. Bir HOSTS dosyası kullanıyorsanız, bunun da doğru yapılandırıldığından emin olun.

## <a name="configure-debugging-in-the-webconfig-file"></a>web.config dosyasında hata ayıklamayı yapılandırma

ASP.NET projelerinde, hata ayıklama ayarları dahil olmak üzere uygulama yapılandırma ve başlatma bilgilerini içeren *web.config* dosyaları varsayılan olarak bulunur. *web.config* dosyaların hata ayıklama için doğru şekilde yapılandırılması gerekir. Önceki bölümlerdeki **Özellikler** ayarları *web.config* dosyalarını güncelleştirir, ancak bunları el ile de yapılandırabilirsiniz.

> [!NOTE]
> ASP.NET Core projelerin başlangıçta *web.config* dosyaları yoktur, ancak uygulama yapılandırması ve başlatma bilgileri için dosyalar üzerinde *appsettings.js* ve *launchSettings.js* kullanın. Uygulamanın dağıtımı, projede bir *web.config* dosyası veya dosya oluşturur, ancak genellikle hata ayıklama bilgilerini içermez.

> [!TIP]
> Dağıtım işleminiz *web.config* ayarlarını güncelleştirebilir, bu nedenle hata ayıklamayı denemeden önce *web.config* hata ayıklama için yapılandırıldığından emin olun.

**Hata ayıklama için bir *web.config* dosyasını el ile yapılandırmak için:**

1. Visual Studio 'da ASP.NET projesinin *web.config* dosyasını açın.

2. *Web.config* bir XML dosyasıdır, bu nedenle Etiketler tarafından işaretlenen iç içe yerleştirilmiş bölümler içerir. `configuration/system.web/compilation` bölümünü bulun. ( `compilation` Öğe yoksa, oluşturun.)

3. `debug` `compilation` Öğesindeki özniteliğin olarak ayarlandığından emin olun `true` . ( `compilation` Öğe bir `debug` öznitelik içermiyorsa, onu ekleyin ve olarak ayarlayın `true` .)

   Varsayılan yapılandırma sunucusu yerine yerel IIS IIS Express, öğesinde öznitelik değerinin IIS sunucusundaki `targetFramework` `compilation` çerçeveyle eşle eş olduğundan emin olun.

   dosyanın `compilation`web.config aşağıdaki örnekteki gibi olması gerekir:

   > [!NOTE]
   > Bu örnek, kısmi bir *web.config* dosyasıdır. genellikle ve öğelerinde ek XML `configuration` bölümleri vardır ve öğesi diğer öznitelik ve öğeleri de `system.web` `compilation` içerebilir.

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

Web sitesi çeşitli sanal dizinler ve alt dizinler içerebilir ve her biri *web.config* birden fazla dosya içerebilir. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamaları, YAPıLANDıRMA ayarlarını *URLweb.config* üst düzeylerde yer alan dosyalardan devralınabilir. Hiyerarşik dosya *web.config* ayarları, hiyerarşide [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] altlarında yer alan tüm uygulamalar için geçerlidir. Hiyerarşinin altlarında yer alan *web.config* bir dosyada farklı bir yapılandırmanın ayar olması, daha yüksek dosyada ayarları geçersiz kılar.

Örneğin, www.microsoft.com/aaa/web.config'de belirtirseniz, aaa klasöründeki veya `debug="true"` <em></em> *aaa'nın* herhangi  bir alt klasöründeki herhangi bir uygulama bu ayarı devralır, ancak bu uygulamalardan biri ayarı kendiweb.config *dosyasıyla geçersiz* kılar.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Dosya sistemini kullanarak hata ayıklama modunda yayımlama

IIS'de uygulama yayımlamanın farklı yolları vardır. Bu adımlar, dosya sistemini kullanarak bir hata ayıklama Yayımlama profili oluşturma ve dağıtmayı gösterir. Bunu yapmak için yönetici olarak Visual Studio çalıştırmanız gerekir.

> [!IMPORTANT]
> Kodunuzu değiştirir veya yeniden oluşturmanız gerekirse, yeniden yayımlamak için bu adımları tekrarlamanız gerekir.

1. Bu Visual Studio projeye sağ tıklayın ve Yayımla'yı **seçin.**

3. **IIS, FTP vb. seçin ve** Yayımla'ya **tıklayın.**

    ![Bir yayımlama hedefi seçin iletişim kutusunun ekran görüntüsü Visual Studio. IIS, FTP ve Web Dağıtımı seçilidir ve Yayımla düğmesi vurgulanır.](media/dbg-aspnet-local-iis.png)

4. **Customprofile** iletişim kutusunda, **Yayımla yöntemi** için **dosya sistemi**' ni seçin.

5. **Hedef konum** için, (**...**) **düğmesini** seçin.

   - ASP.NET için **yerel IIS**' yi seçin, uygulama için oluşturduğunuz Web sitesini seçin ve sonra **Aç**' ı seçin.

     ![ASP.NET 'de IIS 'ye yayımlama](media/dbg-aspnet-local-iis1.png "ASP.NET 'i IIS 'ye yayımlama")

   - ASP.NET Core için **dosya sistemi**' ni seçin, uygulama için ayarladığınız klasörü seçin ve **Aç**' ı seçin.

1. **İleri**’yi seçin.

1. **Yapılandırma** altında, açılan listeden **Hata Ayıkla** ' yı seçin.

1. **Kaydet**’i seçin.

1. **Yayımla** Iletişim kutusunda **customprofile** (veya yeni oluşturduğunuz profilin adı) göründüğünden emin olun ve **Lastusedbuildconfiguration** **hata ayıklama** olarak ayarlanmıştır.

1. **Yayımla**’yı seçin.

    ![Yayımla iletişim kutusunun, CustomProfile uygulaması seçiliyken, Yayımla düğmesi vurgulanmış ve LastBuildConfiguration, hata ayıklama olarak ayarlanan ekran görüntüsü.](media/dbg-aspnet-local-iis-select-site.png)

> [!IMPORTANT]
> Hata ayıklama modu uygulamanızın performansını önemli ölçüde azaltır. En iyi performansı elde etmek için `debug="false"` *web.config* ayarlayın ve bir üretim uygulaması dağıtırken veya performans ölçümleri yaparken bir yayın derlemesi belirleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET hata ayıklama: sistem gereksinimleri](aspnet-debugging-system-requirements.md)
- [Nasıl yapılır: Bir kullanıcı hesabı altında çalışan işlemini çalıştırma](how-to-run-the-worker-process-under-a-user-account.md)
- [Nasıl yapılır: ASP.NET işleminin adını bulma](how-to-find-the-name-of-the-aspnet-process.md)
- [Dağıtılmış Web uygulamalarında hata ayıklama](debugging-deployed-web-applications.md)
- [İzlenecek yol: Web formunda hata ayıklama](walkthrough-debugging-a-web-form.md)
- [Nasıl yapılır: hata ayıklama ASP.NET özel durumları](how-to-debug-aspnet-exceptions.md)
- [Web uygulamalarında hata ayıklama: hatalar ve sorun giderme](debugging-web-applications-errors-and-troubleshooting.md)
