---
title: Komut satırından ClickOnce uygulamaları oluşturma | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 065eea058ffa78c84428e031832e24837eb81d08
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797206"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>Komut satırından ClickOnce uygulamalarını derleme
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], tümleşik geliştirme ortamında (IDE) oluşturulmuş olsalar bile, komut satırından projeler oluşturabilirsiniz. Aslında, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ile oluşturulmuş bir projeyi yalnızca .NET Framework yüklü başka bir bilgisayarda yeniden oluşturabilirsiniz. Bu, bir derlemeyi otomatik bir işlem kullanarak yeniden oluşturmanızı sağlar (örneğin, merkezi bir yapı laboratuvarında veya projenin kendisini oluşturma kapsamının ötesinde gelişmiş betik oluşturma tekniklerini kullanarak).

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>ClickOnce uygulama dağıtımlarını yeniden oluşturmak için MSBuild 'i kullanma
 MSBuild/target: Publish komutunu komut satırında çağırdığınızda, MSBuild sistemine projeyi oluşturmasını ve Publish klasöründe bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulaması oluşturmasını söyler. Bu, IDE 'de **Publish** komutunu seçmeye eşdeğerdir.

 Bu komut, Visual Studio komut istemi ortamındaki yolda bulunan *MSBuild. exe*' yi yürütür.

 "Target", komutun nasıl işlenmesi üzerine MSBuild için bir göstergedir. Anahtar hedefleri "derleme" hedefi ve "Yayımla" hedefidir. Yapı hedefi, IDE 'de Yapı komutunu seçmeye (veya F5 tuşuna basarak) eşdeğerdir. Yalnızca projenizi derlemek istiyorsanız `msbuild`yazarak bunu yapabilirsiniz. Bu komut, derleme hedefi [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]tarafından oluşturulan tüm projeler için varsayılan hedef olduğundan işe yarar. Bu, açıkça derleme hedefini belirtmeniz gerekmediği anlamına gelir. Bu nedenle `msbuild` yazmak, `msbuild /target:build`yazmaya yönelik aynı işlemdir.

 `/target:publish` komutu MSBuild 'in Yayımla hedefini çağırmasını söyler. Yayımla hedefi derleme hedefine bağlıdır. Bu, yayımlama işleminin derleme işleminin bir üst kümesi olduğu anlamına gelir. Örneğin, Visual Basic veya C# kaynak dosyalarından birine bir değişiklik yaptıysanız, ilgili derleme Yayımla işlemi tarafından otomatik olarak yeniden oluşturulur.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildiriminizi oluşturmak için Mage. exe komut satırı aracını kullanarak tam [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım oluşturma hakkında bilgi için bkz. [Izlenecek yol: el ile bir ClickOnce uygulaması dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>MSBuild ile temel bir ClickOnce uygulaması oluşturma ve derleme

#### <a name="to-create-and-publish-a-clickonce-project"></a>ClickOnce projesi oluşturmak ve yayımlamak için

1. Visual Studio 'Yu açın ve yeni bir proje oluşturun.

    **Windows masaüstü uygulaması** proje şablonunu seçin ve proje `CmdLineDemo`adlandırın.

1. **Build** menüsünden **Publish** komutuna tıklayın.

    Bu adım, projenin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama dağıtımı oluşturmak üzere düzgün şekilde yapılandırılmasını sağlar.

    Yayınla Sihirbazı görüntülenir.

1. Yayımla sihirbazında **son**' a tıklayın.

    Visual Studio, *Publish. htm*adlı varsayılan Web sayfasını oluşturur ve görüntüler.

1. Projenizi kaydedin ve depolandığı klasör konumunu aklınızda olun.

   Yukarıdaki adımlar ilk kez yayımlanmış bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projesi oluşturur. Artık derlemeyi IDE dışında yeniden oluşturabilirsiniz.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>Derlemeyi komut satırından yeniden oluşturmak için

1. Çık [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

2. Windows **Başlat** menüsünde **tüm programlar**' a ve ardından **Microsoft Visual Studio** **Visual Studio Araçları**, sonra da **Visual Studio komut istemi**' ne tıklayın. Bu, geçerli kullanıcının kök klasöründe bir komut istemi açması gerekir.

3. **Visual Studio komut isteminde**, geçerli dizini yukarıda oluşturduğunuz projenin konumuyla değiştirin. Örneğin `chdir My Documents\Visual Studio\Projects\CmdLineDemo`'ya tıklayın.

4. "Bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projesi oluşturmak ve yayımlamak Için" içinde oluşturulan mevcut dosyaları kaldırmak için, `rmdir /s publish`yazın.

    Bu adım isteğe bağlıdır, ancak yeni dosyaların tümünün komut satırı derlemesi tarafından üretilmiş olmasını sağlar.

5. `msbuild /target:publish` yazın.

   Yukarıdaki adımlar, projenizin **Publish**adlı bir alt klasöründe tam [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama dağıtımı oluşturacak. *CmdLineDemo. Application* , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimidir. *CmdLineDemo_1.0.0.0* klasörü, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi olan *CmdLineDemo. exe* ve *CmdLineDemo. exe. manifest*dosyalarını içerir. *Setup. exe* , varsayılan olarak .NET Framework yüklemek için yapılandırılmış olan önyükleyici olur. DotNetFX klasörü .NET Framework için yeniden dağıtılabilir içerir. Bu, uygulamanızı Web üzerinden veya UNC veya CD/DVD aracılığıyla dağıtmanız için gereken tüm dosya kümesidir.
   
> [!NOTE]
> MSBuild sistemi, çıkış konumunu belirtmek için **PublishDir** seçeneğini kullanır, örneğin `msbuild /t:publish /p:PublishDir="<specific location>"`.

## <a name="publish-properties"></a>Özellikleri Yayımla
 Uygulamayı yukarıdaki yordamlarda yayımladığınızda, Yayımlama Sihirbazı tarafından proje dosyanıza aşağıdaki özellikler eklenir. Bu özellikler, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamasının nasıl üretildiğini doğrudan etkiler.

 *CmdLineDemo. vbproj* / *CmdLineDemo. csproj*içinde:

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

 Bu özelliklerden herhangi birini, proje dosyasının kendisini değiştirmeden, komut satırında geçersiz kılabilirsiniz. Örneğin, aşağıdakiler önyükleyici olmadan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama dağıtımını oluşturur:

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 Yayımlama özellikleri, **Proje Tasarımcısı**'nın **Yayımlama**, **güvenlik**ve **imzalama** Özellik sayfalarından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] denetlenir. Aşağıda, yayımlama özelliklerinin açıklaması ve bunların her birinin Uygulama Tasarımcısı 'nın çeşitli özellik sayfalarında nasıl ayarlandığı hakkında bir gösterge verilmiştir:

- `AssemblyOriginatorKeyFile`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimlerinizi imzalamak için kullanılan anahtar dosyasını belirler. Bu aynı anahtar, derlemelerinize güçlü bir ad atamak için de kullanılabilir. Bu özellik, **Proje Tasarımcısı**' nın **imzalama** sayfasında ayarlanır.

  Aşağıdaki özellikler **güvenlik** sayfasında ayarlanır:

- **ClickOnce güvenlik ayarlarını etkinleştirin** [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimlerinin oluşturulup oluşturulmayacağını belirler. Bir proje ilk oluşturulduğunda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirim oluşturma varsayılan olarak kapalıdır. İlk kez yayımladığınızda sihirbaz otomatik olarak bu bayrağı kullanacaktır.

- **TargetZone** , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildiriminiz için kullanılacak güven düzeyini belirler. Olası değerler şunlardır. "Internet", "LocalIntranet" ve "özel". Internet ve LocalIntranet, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildiriminiz için varsayılan bir izin kümesine yayılmasına neden olur. LocalIntranet varsayılandır ve temel olarak tam güven anlamına gelir. Custom, yalnızca temel *app. manifest* dosyasında açıkça belirtilen izinlerin [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimine yayınlandığını belirtir. *App. manifest* dosyası, yalnızca güven bilgileri tanımlarını içeren kısmi bir bildirim dosyasıdır. **Güvenlik** sayfasında izinleri yapılandırdığınızda otomatik olarak projenize eklenen gizli bir dosyadır.

  **Yayımla** sayfasında aşağıdaki özellikler ayarlanır:

- `PublishUrl`, uygulamanın IDE 'de yayımlanacağı konumdur. `InstallUrl` veya `UpdateUrl` özelliği belirtilmediyse [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimine eklenir.

- `ApplicationVersion` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamasının sürümünü belirtir. Bu, dört basamaklı bir sürüm numarasıdır. Son basamak bir "*" ise, derleme zamanında bildirime yerleştirilen değerin yerine `ApplicationRevision` değiştirilir.

- `ApplicationRevision` düzeltmeyi belirtir. Bu, IDE 'de yayımladığınız her seferinde artan bir tamsayıdır. Komut satırında gerçekleştirilen derlemeler için otomatik olarak arttırılmadığından emin olun.

- `Install`, uygulamanın yüklü bir uygulama mı yoksa bir Web 'den Çalıştırma uygulaması mı olduğunu belirler.

- `InstallUrl` (gösterilmez), kullanıcıların uygulamayı yükleymesinin konumu olur. Belirtilmişse, `IsWebBootstrapper` özelliği etkinse bu değer *Setup. exe önkurulumuna* yazılır. Ayrıca, `UpdateUrl` belirtilmemişse uygulama bildirimine de eklenir.

- `SupportUrl` (gösterilmez), yüklü bir uygulama için **Program Ekle/Kaldır** iletişim kutusunda bağlanan konumdur.

  Aşağıdaki özellikler **Yayımla** sayfasından erişilen **uygulama güncelleştirmeleri** iletişim kutusunda ayarlanır.

- `UpdateEnabled`, uygulamanın güncelleştirmeleri denetleyip denetmeyeceğini gösterir.

- `UpdateMode` ön plan veya arka plan güncelleştirmelerini belirtir.

- `UpdateInterval`, uygulamanın hangi sıklıkta güncelleştirmeleri denetlemesi gerektiğini belirtir.

- `UpdateIntervalUnits`, `UpdateInterval` değerinin saat, gün veya hafta birimi cinsinden olup olmadığını belirtir.

- `UpdateUrl` (gösterilmez), uygulamanın güncelleştirmeleri alacağı konumdur. Belirtilmişse, bu değer uygulama bildirimine eklenir.

  Aşağıdaki özellikler **Yayımla sayfasından erişilen** **Yayımla Seçenekleri** iletişim kutusunda ayarlanır.

- `PublisherName`, uygulamayı yüklerken veya çalıştırırken gösterilen istem içinde gösterilen yayımcının adını belirtir. Yüklü bir uygulama söz konusu olduğunda, **Başlangıç** menüsünde Klasör adını belirtmek için de kullanılır.

- `ProductName`, uygulamayı yüklerken veya çalıştırırken gösterilen istem içinde gösterilen ürünün adını belirtir. Yüklü bir uygulama söz konusu olduğunda, **Başlangıç** menüsünde kısayol adını belirtmek için de kullanılır.

  Aşağıdaki özellikler, **Yayımla** sayfasından erişilen **Önkoşullar** iletişim kutusunda ayarlanır.

- `BootstrapperEnabled` *Setup. exe* önyükleyicisinin oluşturulup oluşturulmayacağını belirler.

- `IsWebBootstrapper`, *Setup. exe* önyükleyicisinin Web üzerinden veya disk tabanlı modda çalışıp çalışmadığını belirler.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallUrl, SupportUrl, PublishURL ve UpdateURL
 Aşağıdaki tabloda ClickOnce dağıtımı için dört URL seçeneği gösterilmektedir.

|URL seçeneği|Açıklama|
|----------------|-----------------|
|`PublishURL`|ClickOnce uygulamanızı bir Web sitesinde yayımlıyorsanız gereklidir.|
|`InstallURL`|İsteğe bağlı. Yükleme sitesi `PublishURL`farklıysa bu URL seçeneğini ayarlayın. Örneğin, `PublishURL` bir FTP yolu olarak ayarlayabilir ve `InstallURL` bir Web URL 'SI olarak ayarlayabilirsiniz.|
|`SupportURL`|İsteğe bağlı. Destek sitesi `PublishURL`göre farklıysa bu URL seçeneğini ayarlayın. Örneğin, `SupportURL` şirketinizin müşteri desteği web sitesi olarak ayarlayabilirsiniz.|
|`UpdateURL`|İsteğe bağlı. Güncelleştirme konumu `InstallURL`farklıysa bu URL seçeneğini ayarlayın. Örneğin, `PublishURL` bir FTP yolu olarak ayarlayabilir ve `UpdateURL` bir Web URL 'SI olarak ayarlayabilirsiniz.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [İzlenecek yol: ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
