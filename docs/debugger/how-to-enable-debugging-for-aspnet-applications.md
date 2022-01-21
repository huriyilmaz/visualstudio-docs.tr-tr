---
title: ASP.NET uygulamaları için hata ayıklamayı etkinleştirme | Microsoft Docs
description: Visual Studio ASP.NET ve ASP.NET Core uygulamalarda hata ayıklamayı etkinleştirmeyi öğrenin. işlemi bir IIS Express sunucuda veya yerel bir ııs sunucusunda çalıştırabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 01/14/2022
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
ms.openlocfilehash: bc76e94a7769b52fabc8075ee27ec0dd667983c5
ms.sourcegitcommit: 7746657b87b22a7684e79e508af598b02dfe24b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "137609670"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Visual Studio'da ASP.NET veya ASP.NET Core uygulamalarının hatalarını ayıklama

Visual Studio 'de ASP.NET ve ASP.NET Core uygulamalarda hata ayıklaması yapabilirsiniz. işlem, ASP.NET ve ASP.NET Core arasında ve IIS Express ya da yerel bir ııs sunucusunda çalıştırıp çalıştırıetmeksizin farklılık gösterir.

>[!NOTE]
>Aşağıdaki adımlar ve ayarlar yalnızca yerel bir sunucudaki uygulamalarda hata ayıklama için geçerlidir. Uzak IIS sunucusundaki uygulamalarda hata ayıklama Işlemi, **işlemek Için İliştir** kullanır ve bu ayarları yoksayar. ııs 'deki uygulamalar ASP.NET uzaktan hata ayıklama hakkında daha fazla bilgi ve yönergeler için bkz. uzaktan [hata ayıklama ASP.NET bir ııs bilgisayarında](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) veya uzaktan [hata ayıklama ASP.NET Core uzak bir ııs bilgisayarında](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

yerleşik IIS Express sunucusu Visual Studio dahildir. IIS Express, ASP.NET ve ASP.NET Core projelerine yönelik varsayılan hata ayıklama sunucusudur ve önceden yapılandırılmıştır. Hata ayıklamanın en kolay yolu, ilk hata ayıklama ve test için idealdir.

::: moniker range=">=vs-2022"
ASP.NET Core için, Kestrel web sunucusunda da hata ayıklaması yapabilirsiniz.
::: moniker-end

ayrıca, uygulamayı çalıştıracak şekilde yapılandırılmış yerel bir ııs sunucusunda (sürüm 8,0 veya üzeri) bir ASP.NET veya ASP.NET Core uygulamasında hata ayıklaması yapabilirsiniz. Yerel IIS 'de hata ayıklamak için aşağıdaki gereksinimleri karşılamanız gerekir:

<a name="iis"></a>
- yüklü değilse, **ASP.NET ve web geliştirme iş yükünü** yükleme. (Visual Studio Yükleyicisi yeniden çalıştırın, **değiştir**' i seçin ve bu iş yükünü ekleyin.)

   ::: moniker range="vs-2017"
   Visual Studio 2017 ' de, **geliştirme zamanı ııs destek** bileşeni ' ne bakın. İş yükünü eklediğinizde seçildiğinden emin olun.
   ::: moniker-end
- Visual Studio'yu yönetici olarak çalıştırın.
- ASP.NET ve/veya ASP.NET Core uygun sürümleri ile ııs 'yi yükleyip doğru şekilde yapılandırın. ASP.NET Core ile ııs kullanma hakkında daha fazla bilgi için bkz. [ııs ile Windows konak ASP.NET Core](/aspnet/core/host-and-deploy/iis/index). ASP.NET için bkz. [ınstall ııs and ASP.NET Modules](/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules).
- Uygulamanın IIS 'de hata olmadan çalıştığından emin olun.

## <a name="debug-aspnet-apps"></a>ASP.NET uygulamalarda hata ayıkla

IIS Express varsayılandır ve önceden yapılandırılmıştır. Yerel IIS 'de hata ayıklaması yapıyorsanız, [yerel IIS hata ayıklama gereksinimlerini](#iis)karşıladığınızdan emin olun.

1. Visual Studio **Çözüm Gezgini** ASP.NET projesi seçin ve **özellikler** simgesine tıklayın ya da **Alt** + **enter** tuşuna basın veya sağ tıklayıp **özellikler**' i seçin.

1. **Web** sekmesini seçin.

1. **Özellikler** bölmesinde, **sunucular** altında,
   - IIS Express için, açılan listeden **IIS Express** seçin.
   - Yerel IIS için
     1. Açılan listeden **yerel IIS** ' yi seçin.
     1. uygulamayı henüz ııs 'de ayarlamadıysanız, **Project URL** alanının yanında **sanal dizin oluştur**' u seçin.

1. **Hata ayıklayıcıları** altında **ASP.net**' yi seçin.

   ![ASP.NET hata ayıklayıcı ayarları](media/dbg-aspnet-enable-debugging2.png "ASP.NET ayıklayıcı ayarlarını değiştirme")

1.   >  Değişiklikleri kaydetmek için dosya **Seçili öğeleri kaydet** ' i (veya **CTRL** + **'leri** tuşlarına basın) seçin.

1. Uygulamada hata ayıklamak için, projenizde, bazı koddaki kesme noktaları ayarlayın. Visual Studio araç çubuğunda, yapılandırmanın **hata ayıkla** olarak ayarlandığından ve istediğiniz tarayıcının öykünücü alanında **IIS Express ( \<Browser name> )** veya **yerel ııs ( \<Browser name> )** içinde göründüğünden emin olun.

1. hata ayıklamayı başlatmak için, araç çubuğunda **IIS Express ( \<Browser name> )** veya **yerel ııs ( \<Browser name> )** seçeneğini belirleyin, **hata ayıkla** menüsünden **hata ayıklamayı başlat** ' ı seçin veya **F5** tuşuna basın. Hata ayıklayıcı kesme noktalarında duraklatılır. Hata ayıklayıcı kesme noktalarına ulaşamıyorum, bkz. [hata ayıklama sorun giderme](#troubleshoot-debugging).

::: moniker range=">=vs-2022"
## <a name="debug-aspnet-core-apps"></a>ASP.NET Core uygulamalarda hata ayıkla

IIS Express varsayılandır ve önceden yapılandırılmıştır. IIS Express yerine yerel ııs 'de hata ayıklaması yapıyorsanız, [yerel ııs hata ayıklama gereksinimlerini](#iis)karşıladığınızdan emin olun. Kestrel Web sunucusu için yapılandırılan proje adına dayalı varsayılan bir profil de mevcuttur.

1. Visual Studio **Çözüm Gezgini** ASP.NET Core projesi seçin ve **özellikler** simgesine tıklayın ya da **Alt** + **enter** tuşuna basın veya sağ tıklayıp **özellikler**' i seçin.

1. **Hata Ayıkla** sekmesini seçin ve bağlantıyı tıklayarak **hata ayıklama başlatma profilleri kullanıcı arabirimini** açın.

   Gösterilen kullanıcı arabirimi, projenin *launchsettings. JSON* dosyasındaki ayarlara karşılık gelir. Bu dosya hakkında daha fazla bilgi için, [ASP.NET Core çoklu ortamları kullanma](/aspnet/core/fundamentals/environments)konusundaki geliştirme ve launchsettings. JSON bölümüne bakın.

1. Hata ayıklama için yapılandırılacak profili seçin.

   - IIS Express için, açılan listeden **IIS Express** seçin.
   - Kestrel için, projeden sonra adlı profili seçin.
   - Yerel IIS için **Yeni** ' yi seçin ve yenı bir IIS profili oluşturun.

1. **Başlatma tarayıcısının** seçili olduğundan emin olun.

1. **URL**, **Uygulama URL**'SI ve **uygulama SSL URL 'sinin** doğru olduğundan emin olun.

   **URL** , .NET veya .NET Core için ana bilgisayar URL 'sinin konumunu belirtir. projeden sonra adlı bir profil için (yani, *launchsettings. json* içindeki commandName özelliği *Project*), Kestrel sunucusu belirtilen bağlantı noktasını dinler. Bir IIS profili için bu, genellikle **Uygulama URL 'siyle** aynı değerdir. Daha fazla bilgi için, [projeyi yapılandırma](/aspnet/core/host-and-deploy/iis/development-time-iis-support#configure-the-project)altındaki IIS başlatma profili bölümüne bakın.

   Uygulama **URL** 'si ve uygulama **SSL URL 'si** uygulama URL 'leri belirtin. Projeden sonra adlı bir profil için bu özellik, genellikle ve Kestrel sunucu URL 'Lerini belirtir https://localhost:5001 http://localhost:5000 . IIS Express için, **uygulama SSL URL 'si** genellikle olur http://localhost:44334 .

1. **Ortam değişkenleri** altında **ASPNETCORE_ENVIRONMENT** bir **geliştirme** değeriyle bulunduğundan emin olun. Aksi takdirde, değişkeni ekleyin.

   ![ASP.NET Core hata ayıklayıcı ayarları](../debugger/media/vs-2022/dbg-asp-dotnet-enable-debugging-3.png "ASP.NET Core hata ayıklayıcısı ayarlarını değiştirme")

   Ortam değişkenleri hakkında daha fazla bilgi için bkz. [ortamlar](/aspnet/core/fundamentals/environments#environments-1).

1. Uygulamada hata ayıklamak için, projenizde, bazı koddaki kesme noktaları ayarlayın. Visual Studio araç çubuğunda, yapılandırmanın **hata ayıkla** olarak ayarlandığından emin olun.

1. hata ayıklamayı başlatmak için, araç çubuğunda, IIS Express gibi profil adını seçin veya **\<project profile name>**  **\<IIS profile name>** araç çubuğunda hata **ayıkla** menüsünden **hata ayıklamayı başlat** ' ı seçin veya **F5** tuşuna basın. Hata ayıklayıcı kesme noktalarında duraklatılır. Hata ayıklayıcı kesme noktalarına ulaşamıyorum, bkz. [hata ayıklama sorun giderme](#troubleshoot-debugging).
::: moniker-end

::: moniker range="<=vs-2019"
## <a name="debug-aspnet-core-apps"></a>ASP.NET Core uygulamalarda hata ayıkla

IIS Express varsayılandır ve önceden yapılandırılmıştır. Yerel IIS 'de hata ayıklaması yapıyorsanız, [yerel IIS hata ayıklama gereksinimlerini](#iis)karşıladığınızdan emin olun.

1. Visual Studio **Çözüm Gezgini** ASP.NET Core projesi seçin ve **özellikler** simgesine tıklayın ya da **Alt** + **enter** tuşuna basın veya sağ tıklayıp **özellikler**' i seçin.

1. **Hata Ayıkla** sekmesini seçin.

1. **Özellikler** bölmesinde, **profil**' ın yanında,
   - IIS Express için, açılan listeden **IIS Express** seçin.
   - Yerel IIS için, açılan listeden uygulama adını seçin veya **Yeni**' yi seçin, yeni bir profil adı oluşturun ve **Tamam**' ı seçin.

1. **başlat**' ın yanındaki açılan listeden **IIS Express** veya **ııs** ' yi seçin.

1. **Başlatma tarayıcısının** seçili olduğundan emin olun.

1. **Ortam değişkenleri** altında **ASPNETCORE_ENVIRONMENT** bir **geliştirme** değeriyle bulunduğundan emin olun. Aksi takdirde **Ekle** ' yi seçin ve ekleyin.

   ![ASP.NET Core hata ayıklayıcı ayarları](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core hata ayıklayıcısı ayarlarını değiştirme")

1.  > Değişiklikleri kaydetmek için **Seçili öğeleri kaydet** veya **CTRL** + **S** dosyalarını kullanın.

1. Uygulamada hata ayıklamak için, projenizde, bazı koddaki kesme noktaları ayarlayın. Visual Studio araç çubuğunda, yapılandırmanın **hata ayıklama** olarak ayarlandığından ve **IIS Express** ya da yeni ııs profili adının öykünücü alanında göründüğünden emin olun.

1. hata ayıklamayı başlatmak için **IIS Express** ' yi seçin veya **\<IIS profile name>** araç çubuğunda hata **ayıkla** menüsünden **hata ayıklamayı başlat** ' ı seçin veya **F5** tuşuna basın. Hata ayıklayıcı kesme noktalarında duraklatılır. Hata ayıklayıcı kesme noktalarına ulaşamıyorum, bkz. [hata ayıklama sorun giderme](#troubleshoot-debugging).
::: moniker-end

## <a name="troubleshoot-debugging"></a>Hata ayıklama sorunlarını giderme

Yerel IIS hata ayıklaması kesme noktasına ilerleyememesi durumunda sorun gidermek için aşağıdaki adımları izleyin.

1. Web uygulamasını IIS 'den başlatın ve düzgün çalıştığından emin olun. Web uygulamasını çalışır durumda bırakın.

2. Visual Studio, **hata ayıkla > işleme ekle** ' yi seçin veya **Ctrl** + **Alt** + **P** tuşlarına basın ve ASP.NET ya da ASP.NET Core işlemine bağlanın (genellikle **w3wp.exe** veya **dotnet.exe**). daha fazla bilgi için bkz. [işleme iliştirme](attach-to-running-processes-with-the-visual-studio-debugger.md) ve [ASP.NET işlemin adını bulma](how-to-find-the-name-of-the-aspnet-process.md).

**Hata ayıklama** başlatma hata ayıklaması veya F5 kullanarak, **İşleme İliştir**' i kullanarak bağlanıp kesme noktasına ulaşırsanız  >   , proje özelliklerinde bir ayar büyük olasılıkla yanlış olur. Bir HOSTS dosyası kullanıyorsanız, bunun da doğru yapılandırıldığından emin olun.

## <a name="configure-debugging-in-the-webconfig-file"></a>web.config dosyasında hata ayıklamayı yapılandırma

ASP.NET projelerinde *varsayılanweb.config,* hata ayıklama ayarları da dahil olmak üzere hem uygulama yapılandırması hem de başlatma bilgilerini içeren bir dosya vardır. Hata *web.config* hata ayıklama için doğru yapılandırıldığından emin olun. Önceki **bölümlerde** yer alan Özellikler ayarları, *web.config* dosyaları güncelleştirmektedir ancak bunları el ile de yapılandırabilirsiniz.

> [!NOTE]
> ASP.NET Core başlangıçta uygulama *dosyalarına sahipweb.config,* ancak uygulama yapılandırması ve başlatma bilgileri için *appsettings.json* ve *launchSettings.json* dosyalarını kullanın. Uygulama dağıtılarak proje içinde *web.config* bir dosya veya dosya oluşturur, ancak genellikle hata ayıklama bilgileri içermez.

> [!TIP]
> Dağıtım işleminiz,web.config *ayarlarını* güncelleştireblir, bu nedenle hata ayıklamayıweb.confighata *ayıklama* için yapılandırıldığından emin olun.

**Hata ayıklama için bir *web.config* el ile yapılandırmak için:**

1. Bu Visual Studio, ASP.NET projesinin *web.config* açın.

2. *Web.config* bir XML dosyası olduğu için etiketlerle işaretlenmiş iç içe geçmiş bölümler içerir. `configuration/system.web/compilation` bölümünü bulun. (Öğe `compilation` yoksa oluşturun.)

3. öğesinde `debug` özniteliğinin olarak `compilation` ayarlanmış olduğundan emin `true` olun. (Öğe `compilation` bir öznitelik `debug` içeriyorsa, ekleyin ve olarak `true` ayarlayın.)

   Varsayılan yapılandırma sunucusu yerine yerel IIS IIS Express, öğesinde öznitelik değerinin IIS sunucusundaki çerçeveyle eşle `targetFramework` `compilation` eş olduğundan emin olun.

   Dosyanın `compilation`web.config aşağıdaki örnekteki gibi olması gerekir:

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

Web sitesi çeşitli sanal dizinler ve alt dizinler içerebilir ve *her* web.configdosya içerebilir. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamaları, YAPıLANDıRMA ayarlarını *URLweb.config* üst düzeylerde yer alan dosyalardan devralınabilir. Hiyerarşik dosya *web.config* ayarları, hiyerarşide [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] altlarında yer alan tüm uygulamalar için geçerlidir. Hiyerarşinin alt köşesindeki *birweb.config* yapılandırmayı ayarlama, daha yüksek dosyada ayarları geçersiz kılar.

Örneğin, www.microsoft.com/aaa/web.config'de belirtirseniz, aaa klasöründeki veya `debug="true"` <em></em> *aaa'nın* herhangi  bir alt klasöründeki herhangi bir uygulama bu ayarı devralır, ancak bu uygulamalardan biri ayarı kendiweb.config *dosyasıyla geçersiz kılar.*

## <a name="publish-in-debug-mode-using-the-file-system"></a>Dosya sistemini kullanarak hata ayıklama modunda yayımlama

IIS'de uygulama yayımlamanın farklı yolları vardır. Bu adımlar, dosya sistemini kullanarak bir hata ayıklama Yayımlama profili oluşturma ve dağıtmayı gösterir. Bunu yapmak için yönetici olarak Visual Studio çalıştırmanız gerekir.

> [!IMPORTANT]
> Kodunuzu değiştirir veya yeniden oluşturmanız gerekirse, yeniden yayımlamak için bu adımları tekrarlamanız gerekir.

1. Bu Visual Studio projeye sağ tıklayın ve Yayımla'yı **seçin.**

3. **IIS, FTP vb. öğesini seçin ve** Yayımla'ya **tıklayın.**

    ![Visual Studio'da Yayımlama hedefi seçin iletişim kutusunun ekran Visual Studio. IIS, FTP ve Web Dağıtımı seçilidir ve Yayımla düğmesi vurgulanır.](media/dbg-aspnet-local-iis.png)

4. **CustomProfile iletişim kutusundaki** Publish method **(Yayımlama yöntemi) için File** system **(Dosya sistemi) öğesini seçin.**

5. Hedef **konum için Gözat**( ... ) öğesini **seçin.** 

   - Bu ASP.NET Yerel **IIS'yi** seçin, uygulama için oluşturduğunuz web sitesini seçin ve ardından Aç'ı **seçin.**

     ![IIS'ASP.NET yayımlama](media/dbg-aspnet-local-iis1.png "IIS'ASP.NET yayımlama")

   - Bu ASP.NET Core Dosya **Sistemi'ne tıklayın,** uygulama için ayar istediğiniz klasörü seçin ve ardından Aç'ı **seçin.**

1. **İleri**’yi seçin.

1. **Yapılandırma'nın** **altında, açılan listeden Hata** Ayıkla'ya seçin.

1. **Kaydet**’i seçin.

1. Yayımla **iletişim** kutusunda **CustomProfile** (veya yeni oluşturduğunuz profilin adı) göründüğünden ve **LastUsedBuildConfiguration** öğesinin Hata Ayıkla olarak ayarlanmış olduğundan **emin olun.**

1. **Yayımla**’yı seçin.

    ![CustomProfile uygulamasının seçili olduğu, Yayımla düğmesinin vurgulanmış olduğu ve LastBuildConfiguration öğesinin Hata Ayıkla olarak ayarlanmış olduğu Yayımla iletişim kutusunun ekran görüntüsü.](media/dbg-aspnet-local-iis-select-site.png)

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
