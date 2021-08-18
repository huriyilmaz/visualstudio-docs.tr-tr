---
title: Komut ClickOnce Komut Satırı Uygulamalarından Uygulama | Microsoft Docs
description: Otomatikleştirilmiş bir Visual Studio kullanarak derlemeyi yeniden oluşturma izni veren komut satırı projeleri oluşturma hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 6bb7d455bf85ef9ba1776956330ac217b73cd2dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160913"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Komut satırından ClickOnce uygulamalarını derleme

[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]'de, tümleşik geliştirme ortamında (IDE) oluşturulmuş olsalar bile komut satırıyla projeler derlemek için. Aslında, ile oluşturulan bir projeyi yalnızca yüklü [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] olan başka bir bilgisayarda .NET Framework. Bu sayede bir derlemeyi merkezi bir derleme laboratuvarında veya projenin kendisini oluşturma kapsamının ötesindeki gelişmiş betik tekniklerini kullanarak otomatik bir işlem kullanarak yeniden oluşturabilirsiniz.

## <a name="use-msbuild-to-reproduce-net-framework-clickonce-application-deployments"></a>Uygulama MSBuild oluşturmak için .NET Framework ClickOnce kullanma

 Komut satırına msbuild /target:publish komutunu çağırsanız, MSBuild sisteme projeyi derlemesini ve yayımlama klasöründe bir uygulama [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] oluşturmalarını söyler. Bu, IDE'de **Yayımla komutunu** seçmeye eşdeğerdir.

 Bu komut *msbuild.exe* komut istemi ortamındaki yolda bulunan Visual Studio yürütür.

 "Hedef", komutun nasıl iş MSBuild için kullanılan bir göstergedir. Anahtar hedefler "derleme" hedefi ve "yayımla" hedefidir. Derleme hedefi, IDE'de Derleme komutunu seçmeye (veya F5'e basarak) eşdeğerdir. Yalnızca projenizi oluşturmak için yazarak bunu `msbuild` başarabilirsiniz. Derleme hedefi, tarafından oluşturulan tüm projeler için varsayılan hedef olduğundan bu komut [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] çalışır. Başka bir ifadeyle derleme hedefini açıkça belirtmeniz gerekmez. Bu nedenle, `msbuild` yazma işlemi yazmakla `msbuild /target:build` aynıdır.

 komutu, `/target:publish` MSBuild hedefini çağırmalarını söyler. Yayımlama hedefi, derleme hedefine bağlıdır. Bu, yayımlama işlemi derleme işlemi üst kümesi olduğu anlamına gelir. Örneğin, C# veya C# kaynak Visual Basic bir değişiklik yaptıysanız, ilgili derleme yayımlama işlemi tarafından otomatik olarak yeniden oluşturulur.

 Bildiriminizi oluşturmak için Mage.exe komut satırı aracını kullanarak tam dağıtım oluşturma hakkında bilgi için bkz. Adım adım: Bir uygulama için ClickOnce [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [dağıtma.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>MSBuild ile temel ClickOnce uygulama oluşturma ve MSBuild

### <a name="to-create-and-publish-a-clickonce-project"></a>Bir proje oluşturmak ve ClickOnce için

1. Yeni Visual Studio ve yeni bir proje oluşturun.

    Masaüstü **Uygulaması Windows şablonunu** seçin ve projeye adını `CmdLineDemo` girin.

1. Derleme **menüsünde** Yayımla **komutuna** tıklayın.

    Bu adım, projenin bir uygulama dağıtımı üretmek için düzgün şekilde [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yapılandırılması sağlar.

    Yayımlama Sihirbazı görüntülenir.

1. Yayımlama Sihirbazı'nda Son'a **tıklayın.**

    Visual Studio,Publish.htmadlı varsayılan Web *sayfasınıPublish.htm.*

1. Projenizi kaydedin ve depolandığı klasör konumunu not edin.

   Yukarıdaki adımlar, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ilk kez yayımlanan bir proje oluşturun. Artık derlemeyi IDE'nin dışında yeniden üretin.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Derlemeyi komut satırıyla yeniden oluşturmak için

1. 'den [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] çıkın.

2. Başlat menüsünden Windows **Programlar'a** **tıklayın,** ardından Microsoft Visual Studio **ve** ardından **Visual Studio Araçları'** Visual Studio **İstemi'ne tıklayın.** Bunun geçerli kullanıcının kök klasöründe bir komut istemi açması gerekir.

3. Komut **Visual Studio'de,** geçerli dizini yukarıda yeni inşa edilen projenin konumuyla değiştirir. Örneğin, `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.

4. "Proje oluşturmak ve yayımlamak için" içinde üretilen mevcut [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dosyaları kaldırmak için `rmdir /s publish` yazın.

    Bu adım isteğe bağlıdır, ancak yeni dosyaların komut satırı derlemesi tarafından üretilmalarını sağlar.

5. `msbuild /target:publish` yazın.

   Yukarıdaki adımlar, projenizin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Yayımla adlı alt klasörüne tam bir uygulama dağıtımı **üretecek.** *CmdLineDemo.application,* dağıtım [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimidir. *CmdLineDemo_1.0.0.0* klasörü, uygulama bildirimi *CmdLineDemo.exe* *veCmdLineDemo.exe.manifest* [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dosyalarını içerir. *Setup.exe* önyükleyicidir ve varsayılan olarak önyükleyiciyi yük .NET Framework. DotNetFX klasörü, dosyanın yeniden dağıtılabilir .NET Framework. Bu, uygulamanızı Web üzerinden veya UNC ya da CD/DVD aracılığıyla dağıtmak için ihtiyacınız olan tüm dosya kümesidir.

> [!NOTE]
> Bu MSBuild, **çıktının konumunu** belirtmek için PublishDir seçeneğini kullanır, örneğin `msbuild /t:publish /p:PublishDir="<specific location>"` .

::: moniker range=">=vs-2019"

## <a name="build-net-clickonce-applications-from-the-command-line"></a>Komut ClickOnce .NET uygulama derleme

Komut ClickOnce .NET ClickOnce uygulamaları oluşturmak benzer bir deneyimdir. Tek bir örnek komut satırına yayımlama profili için ek bir özellik MSBuild gerekir. Yayımlama profili oluşturmanın en kolay yolu, Visual Studio.  Daha [fazla bilgi için bkz. Windows kullanarak .NET ClickOnce](quickstart-deploy-using-clickonce-folder.md) uygulaması dağıtma.

Yayımlama profilini oluşturduktan sonra pubxml dosyasını msbuild komut satırına bir özellik olarak sebilirsiniz. Örnek:

```cmd
    msbuild /t:publish /p:PublishProfile=<pubxml file> /p:PublishDir="<specific location>"
```
::: moniker-end

## <a name="publish-properties"></a>Özellikleri yayımlama

 Yukarıdaki yordamlarda uygulamayı yayımlarsanız, aşağıdaki özellikler Yayımlama Sihirbazı tarafından proje dosyanıza veya .NET Core 3.1 ya da sonraki projeler için yayımlama profili dosyasına eklenir. Bu özellikler uygulamanın nasıl [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] üretil olduğunu doğrudan etkiler.

 *CmdLineDemo.vbproj*  /  *CmdLineDemo.csproj içinde:*

```xml
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>
<GenerateManifests>true</GenerateManifests>
<TargetZone>LocalIntranet</TargetZone>
<PublisherName>Microsoft</PublisherName>
<ProductName>CmdLineDemo</ProductName>
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>
<Install>true</Install>
<ApplicationVersion>1.0.0.*</ApplicationVersion>
<ApplicationRevision>1</ApplicationRevision>
<UpdateEnabled>true</UpdateEnabled>
<UpdateRequired>false</UpdateRequired>
<UpdateMode>Foreground</UpdateMode>
<UpdateInterval>7</UpdateInterval>
<UpdateIntervalUnits>Days</UpdateIntervalUnits>
<UpdateUrlEnabled>false</UpdateUrlEnabled>
<IsWebBootstrapper>true</IsWebBootstrapper>
<BootstrapperEnabled>true</BootstrapperEnabled>
```

 Bu .NET Framework projelerde, proje dosyasının kendisini değiştirmeden komut satırına bu özelliklerden herhangi birini geçersiz kılabilirsiniz. Örneğin, aşağıdaki önyükleyici [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] olmadan uygulama dağıtımını derlemek için:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
 ```

::: moniker range=">=vs-2019"
.NET Core 3.1 veya sonraki projeler için bu ayarlar pubxml dosyasında sağlanır.

 Yayımlama özellikleri, Project [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Tasarımcısı'nın** Yayımlama, Güvenlik ve **İmzalama özellik sayfalarından denetlenmektedir.**   Aşağıda yayımlama özelliklerinin açıklaması ve her biri uygulama tasarımcısının çeşitli özellik sayfalarında nasıl ayarlanmıştır? açıklaması verilmiştir:

> [!NOTE]
> .NET Windows masaüstü projeleri için bu ayarlar artık Yayımlama Sihirbazı'nda bulunur
::: moniker-end

- `AssemblyOriginatorKeyFile` , uygulama bildirimlerinizi imzalamak için kullanılan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] anahtar dosyasını belirler. Aynı anahtar, derlemelerinize güçlü bir ad atamak için de kullanılabilir. Bu özellik, Project  **Designer'ın İmzalama sayfasında ayarlanır.**
::: moniker range=">=vs-2019"
.NET Windows uygulamaları için bu ayar proje dosyasında kalır
::: moniker-end

  Güvenlik sayfasında aşağıdaki özellikler **ayarlanır:**

- **Bildirimlerin ClickOnce olup olmadığını Ayarlar** güvenlik güvenlik ayarını [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] etkinleştirin. Bir proje ilk oluşturulduğunda bildirim [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] oluşturma varsayılan olarak kapalıdır. İlk kez yayımlarken sihirbaz bu bayrağı otomatik olarak açacaktır.

- **TargetZone,** uygulama bildiriminize yayma güven [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] düzeyini belirler. Olası değerler "Internet", "LocalIntranet" ve "Custom" değerleridir. Internet ve LocalIntranet, uygulama bildiriminize varsayılan bir izin kümesi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yaymanıza neden olur. LocalIntranet varsayılandır ve temelde tam güven anlamına gelir. Özel, yalnızca temel *app.manifest* dosyasında açıkça belirtilen izinlerin uygulama bildirimine yay olacağını [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] belirtir. *app.manifest* dosyası, yalnızca güven bilgileri tanımlarını içeren kısmi bir bildirim dosyasıdır. Bu gizli bir dosyadır ve Güvenlik sayfasında izinleri yapılandırırsanız projenize otomatik **olarak** eklenir.
-
::: moniker range=">=vs-2019"
> [!NOTE]
> .NET Core 3.1 veya sonraki Windows masaüstü projeleri için bu Güvenlik ayarları desteklanmaz.
::: moniker-end

  Yayımla sayfasında aşağıdaki **özellikler** ayarlanır:

- `PublishUrl` , uygulamanın IDE'de yayımlanacak konumu. veya özelliği [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] belirtilmezse uygulama `InstallUrl` `UpdateUrl` bildirimine eklenir.

- `ApplicationVersion` uygulamanın sürümünü [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] belirtir. Bu, dört basamaklı bir sürüm numarasıdır. Son basamak bir "*" ise derleme zamanında bildirime `ApplicationRevision` eklenen değerin yerine eklenir.

- `ApplicationRevision` düzeltmeyi belirtir. Bu, IDE'de her yayımlamada artıran bir tamsayıdır. Komut satırı üzerinde gerçekleştirilen derlemeler için otomatik olarak artırılamayabilirsiniz.

- `Install` uygulamanın yüklü bir uygulama mı yoksa bir Web'den çalıştır uygulaması mı olduğunu belirler.

- `InstallUrl` (gösterilmez) kullanıcıların uygulamayı yükleyecekleri konumtur. Belirtilirse, özellik etkinse *busetup.exe* önyükleyiciye `IsWebBootstrapper` girilmez. Belirtilmezse uygulama bildirimine `UpdateUrl` de eklenir.

- `SupportUrl` (gösterilmez), yüklü bir uygulamanın **Program Ekle/Kaldır** iletişim kutusunda bağlantılı konumtur.

  Aşağıdaki özellikler, Yayımla **sayfasından erişilen** Uygulama Güncelleştirmeleri iletişim **kutusunda** ayarlanır.

- `UpdateEnabled` uygulamanın güncelleştirmeleri denetlemesi gerekip gerek olmadığını gösterir.

- `UpdateMode` Ön plan güncelleştirmelerini veya Arka plan güncelleştirmelerini belirtir.
::: moniker range=">=vs-2019"
   .NET Core 3.1 veya sonraki projeler için Arka Plan desteklenmiyor.  
::: moniker-end
- `UpdateInterval` uygulamanın hangi sıklıkta güncelleştirmeleri denetlemesi gerektiğini belirtir.
::: moniker range=">=vs-2019"
   .NET Core 3,1 veya üzeri için bu ayar desteklenmez.
::: moniker-end

- `UpdateIntervalUnits``UpdateInterval`değerin saat, gün veya hafta cinsinden olup olmadığını belirtir.
::: moniker range=">=vs-2019"
   .NET Core 3,1 veya üzeri için bu ayar desteklenmez.
::: moniker-end

- `UpdateUrl` (gösterilmez), uygulamanın güncelleştirmeleri alacağı konumdur. Belirtilmişse, bu değer uygulama bildirimine eklenir.

  Aşağıdaki özellikler **Yayımla sayfasından erişilen** **Yayımla Seçenekleri** iletişim kutusunda ayarlanır.

- `PublisherName` uygulamayı yüklerken veya çalıştırırken gösterilen istem içinde gösterilen yayımcının adını belirtir. Yüklü bir uygulama söz konusu olduğunda, **Başlangıç** menüsünde Klasör adını belirtmek için de kullanılır.

- `ProductName` uygulamayı yüklerken veya çalıştırırken gösterilen istem içinde gösterilen ürünün adını belirtir. Yüklü bir uygulama söz konusu olduğunda, **Başlangıç** menüsünde kısayol adını belirtmek için de kullanılır.

  Aşağıdaki özellikler, **Yayımla** sayfasından erişilen **Önkoşullar** iletişim kutusunda ayarlanır.

- `BootstrapperEnabled`*setup.exe* önyükleyici oluşturulup oluşturulmayacağını belirler.

- `IsWebBootstrapper`*setup.exe* önyükleyicinin Web üzerinde veya disk tabanlı modda çalışıp çalışmadığını belirler.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallUrl, SupportUrl, PublishURL ve UpdateURL

 aşağıdaki tabloda ClickOnce dağıtım için dört URL seçeneği gösterilmektedir.

|URL seçeneği|Açıklama|
|----------------|-----------------|
|`PublishURL`|ClickOnce uygulamanızı bir Web sitesinde yayımlıyorsanız gereklidir.|
|`InstallURL`|İsteğe bağlı. Yükleme sitesi öğesinden farklıysa bu URL seçeneğini ayarlayın `PublishURL` . Örneğin, öğesini bir `PublishURL` FTP yolu olarak ayarlayabilir ve ' ı `InstallURL` BIR Web URL 'si olarak ayarlayabilirsiniz.|
|`SupportURL`|İsteğe bağlı. Destek sitesi öğesinden farklıysa bu URL seçeneğini ayarlayın `PublishURL` . Örneğin, seçeneğini `SupportURL` şirketinizin müşteri desteği web sitesine ayarlayabilirsiniz.|
|`UpdateURL`|İsteğe bağlı. Güncelleştirme konumu öğesinden farklıysa bu URL seçeneğini ayarlayın `InstallURL` . Örneğin, öğesini bir `PublishURL` FTP yolu olarak ayarlayabilir ve ' ı `UpdateURL` BIR Web URL 'si olarak ayarlayabilirsiniz.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
