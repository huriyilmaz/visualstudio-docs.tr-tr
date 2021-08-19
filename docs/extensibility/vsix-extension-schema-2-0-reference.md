---
title: VSIX Uzantı Şeması 2.0 Başvuru | Microsoft Docs
description: VSIX uzantı şeması 2.0, VSIX dağıtım bildirimi dosyasının dosya biçimini tanımlar ve bu dosya vsIX paketinin içeriğini açıklar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: baaa03b01e7f211bfc6822e7fcf017d1a49ad324
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158105"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX uzantı şeması 2.0 başvurusu
VSIX dağıtım bildirimi dosyası, vsIX paketinin içeriğini açıklar. Dosya biçimi bir şema tarafından yönetilir. Bu şemanın 2.0 sürümü, özel türler ve öznitelikler eklemeyi destekler.  Bildirimin şeması genişletilebilir. Bildirim yükleyicisi, anlamayabilecek XML öğelerini ve özniteliklerini yoksayıyor.

> [!IMPORTANT]
> Visual Studio 2015, VSIX dosyalarını Visual Studio 2010, Visual Studio 2012 veya Visual Studio 2013 yük olabilir.

## <a name="package-manifest-schema"></a>Paket bildirimi şeması
 Bildirim XML dosyasının kök `<PackageManifest>` öğesidir. Bildirim biçiminin `Version` sürümü olan tek bir özniteliği vardır. Biçimde büyük değişiklikler yapılırsa sürüm biçimi değiştirilir. Bu makalede, özniteliği Version="2.0" değerine ayarlanarak bildirimde belirtilen bildirim biçimi `Version` sürüm 2.0 açıklanmıştır.

### <a name="packagemanifest-element"></a>PackageManifest öğesi
 Kök `<PackageManifest>` öğe içinde aşağıdaki öğeleri kullanabilirsiniz:

- `<Metadata>` - Paketin kendisiyle ilgili meta veriler ve reklam bilgileri. Bildirimde `Metadata` yalnızca bir öğeye izin verilir.

- `<Installation>` - Bu bölüm, bu uzantı paketinin yüklenebilirsiniz uygulama S SU'ları dahil olmak üzere nasıl yüklenebilirsiniz tanımlar. Bildirimde `Installation` yalnızca tek bir öğeye izin verilir. Bildirimin bir öğesi `Installation` olması gerekir, yoksa bu paket herhangi bir SKU'ya yüklenmez.

- `<Dependencies>` - Bu paket için isteğe bağlı bir bağımlılık listesi burada tanımlanır.

- `<Assets>` - Bu bölüm, bu paket içinde yer alan tüm varlıkları içerir. Bu bölüm olmadan, bu paket herhangi bir içeriği ortaya çıkartır.

- `<AnyElement>*` - Bildirim şeması, diğer öğelere izin verecek kadar esnektir. Bildirim yükleyicisi tarafından tanınmaz tüm alt öğeler, Uzantı Yöneticisi API'sinde ek XmlElement nesneleri olarak açığa çıkar. VSIX uzantıları, bu alt öğeleri kullanarak, çalışma zamanında erişen bir dosyada çalışan kodun Visual Studio ek veriler tanımlayabilir. Bkz. [Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Meta veri öğesi
 Bu bölüm paket, kimliği ve reklam bilgileriyle ilgili meta verilerdir. `<Metadata>` aşağıdaki öğeleri içerir:

- `<Identity>` - Bu paket için tanımlama bilgilerini tanımlar ve aşağıdaki öznitelikleri içerir:

  - `Id` - Bu öznitelik, yazarı tarafından seçilen paket için benzersiz bir kimlik olmalıdır. Ad, CLR türlerinin ad alanıyla aynı şekilde tam olarak Company.Product.Feature.Name. özniteliği `Id` 100 karakterle sınırlıdır.

  - `Version` - Bu paketin sürümünü ve içeriğini tanımlar. Bu öznitelik CLR derleme sürümü oluşturma biçimini izler: Major.Minor.Build.Revision (1.2.40308.00). Sürüm numarası daha yüksek olan bir paket, pakette yapılan güncelleştirmeler olarak kabul edilir ve mevcut yüklü sürüme yükleyebilir.

  - `Language` - Bu öznitelik, paket için varsayılan dildir ve bu bildirimde yer alan metinsel verilere karşılık gelen dildir. Bu öznitelik kaynak derlemeleri için CLR yerel kod kuralına uyar, örneğin: en-us, en, fr-fr. Uygulamanın `neutral` herhangi bir sürümünde çalıştıracak, dilden bağımsız bir uzantıyı Visual Studio. `neutral` varsayılan değerdir.

  - `Publisher` - Bu öznitelik, bu paketin yayımcısı olan şirketi veya bireysel adı tanımlar. özniteliği `Publisher` 100 karakterle sınırlıdır.

- `<DisplayName>` - Bu öğe, Uzantı Yöneticisi kullanıcı arabiriminde görüntülenen kolay paket adını belirtir. İçerik `DisplayName` 50 karakterle sınırlıdır.

- `<Description>` - Bu isteğe bağlı öğe, Uzantı Yöneticisi kullanıcı arabiriminde görüntülenen paketin ve içeriğinin kısa bir açıklamasıdır. İçerik, `Description` istediğiniz herhangi bir metni içerebilir ancak 1000 karakterle sınırlıdır.

- `<MoreInfo>` - Bu isteğe bağlı öğe, bu paketin tam açıklamasını içeren çevrimiçi bir sayfanın URL'dir. Protokol http olarak belirtilmelidir.

- `<License>` - Bu isteğe bağlı öğe, pakette bulunan bir lisans dosyasının (.txt, .rtf) göreli yoludur.

- `<ReleaseNotes>` - Bu isteğe bağlı öğe, pakette yer alan bir sürüm notları dosyasının göreli yoludur (.txt, .rtf) veya sürüm notlarını görüntüleyen bir web sitesinin URL'sidir.

- `<Icon>` - Bu isteğe bağlı öğe, pakette bulunan bir görüntü dosyasının (png, bmp, jpeg, ico) göreli yoludur. Simge görüntüsü 32x32 piksel olmalıdır (veya bu boyuta küçültülür) ve listview kullanıcı arabiriminde görünür. Herhangi bir `Icon` öğe belirtilmezse, kullanıcı arabirimi varsayılanı kullanır.

- `<PreviewImage>` - Bu isteğe bağlı öğe, pakette bulunan bir görüntü dosyasının (png, bmp, jpeg) göreli yoludur. Önizleme görüntüsü 200x200 piksel olmalı ve ayrıntılar kullanıcı arabiriminde görüntüleniyor olmalıdır. Herhangi bir `PreviewImage` öğe belirtilmezse, kullanıcı arabirimi varsayılanı kullanır.

- `<Tags>` - Bu isteğe bağlı öğe, arama ipuçları için kullanılan noktalı virgülle ayrılmış ek metin etiketlerini listeler. öğesi `Tags` 100 karakterle sınırlıdır.

- `<GettingStartedGuide>` - Bu isteğe bağlı öğe, html dosyasının göreli yolu veya bu paket içindeki uzantıyı veya içeriği kullanma hakkında bilgi içeren bir web sitesinin URL'sidir. Bu kılavuz bir yüklemenin parçası olarak başlatıldı.

- `<AnyElement>*` - Bildirim şeması, diğer öğelere izin verecek kadar esnektir. Bildirim yükleyicisi tarafından tanınmaz tüm alt öğeler XmlElement nesnelerinin listesi olarak görüntülenir. VSIX uzantıları, bu alt öğeleri kullanarak bildirim dosyasında ek veriler tanımlayabilir ve çalışma zamanında bunları numaralarına numaralatabilirsiniz.

### <a name="installation-element"></a>Yükleme öğesi
 Bu bölümde, bu paketin nasıl yüklenebilirsiniz ve içine yüklenebilir uygulama SKUS'ları tanımlanıyor. Bu bölüm aşağıdaki öznitelikleri içerir:

- `Experimental` - Tüm kullanıcılar için yüklü olan bir uzantınız varsa ancak aynı bilgisayarda güncelleştirilmiş bir sürüm geliştiriyorsanız bu özniteliği true olarak ayarlayın. Örneğin, tüm kullanıcılar için MyExtension 1.0 yüklemiş ancak MyExtension 2.0 hata ayıklaması yapmak için Experimental="true" olarak ayarlayın. Bu öznitelik, Visual Studio 2015 Güncelleştirme 1 ve sonraki bir güncelleştirmede kullanılabilir.

- `Scope` - Bu öznitelik "Genel" veya "ProductExtension" değerini alır:

  - "Genel", yüklemenin kapsamı belirli bir SKU'nun olmadığını belirtir. Örneğin, bu değer bir Uzantı SDK'sı yüklü olduğunda kullanılır.

  - "ProductExtension", SKU'ların tek tek kapsamına alan geleneksel bir VSIX Uzantısının (sürüm 1.0) Visual Studio olduğunu belirtir. Varsayılan değer budur.

- `AllUsers` - Bu isteğe bağlı öznitelik, bu paketin tüm kullanıcılar için yük olup olmadığını belirtir. Varsayılan olarak bu öznitelik, paketin kullanıcı başına olduğunu belirten false özniteliğidir. (Bu değeri true olarak ayarsanız, sonuçta elde edilen VSIX'i yüklemek için yükleme kullanıcısı yönetici ayrıcalık düzeyine yükseltmeli.

- `InstalledByMsi` - Bu isteğe bağlı öznitelik, bu paketin bir MSI tarafından yük olup olmadığını belirtir. MSI tarafından yüklü paketler, Uzantı Yöneticisi tarafından değil, MSI (Programlar ve Özellikler) tarafından yüklenir ve Visual Studio yönetilir.  Varsayılan olarak, paketin bir MSI tarafından yüklenmemiş olduğunu belirten bu öznitelik false'tır.

- `SystemComponent` - Bu isteğe bağlı öznitelik, bu paketin bir sistem bileşeni olarak kabul ed mi olacağını belirtir. Sistem bileşenleri Uzantı Yöneticisi kullanıcı arabiriminde gösterlenmez ve güncelleştirilemez. Varsayılan olarak, paketin bir sistem bileşeni olmadığını belirten bu öznitelik false'tır.

- `AnyAttribute*` - öğesi, çalışma zamanında bir ad-değer çifti sözlüğü olarak açığa çıkacak açık bir öznitelik `Installation` kümesi kabul eder.

- `<InstallationTarget>` -Bu öğe, VSIX yükleyicinin paketi yükley olduğu konumu kontrol eder. Özniteliğin değeri "ProductExtension" ise paketin, kullanılabilirliğini uzantılara tanıtacak şekilde içeriğinin bir parçası olarak yüklemiş bir SKU'ya sahip `Scope` olması gerekir. özniteliği `<InstallationTarget>` "ProductExtension" açık veya varsayılan değerine sahip `Scope` olduğunda öğesi aşağıdaki özniteliklere sahip olur:

  - `Id` - Bu öznitelik paketi tanımlar.  özniteliği ad alanı kuralına uyar: Company.Product.Feature.Name. özniteliği `Id` yalnızca alfasayısal karakterler içerebilir ve 100 karakterle sınırlıdır. Beklenen değerler:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio. Pro

    - Microsoft.VisualStudio. Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version` - Bu öznitelik, bu SKU'nun desteklenen en düşük ve en yüksek sürümlerine sahip bir sürüm aralığı belirtir. Bir paket, desteklediği S SU'ların sürümlerini ayrıntılı olarak inceler. Sürüm aralığı notasyonu [10.0 - 11.0], burada

    - [ - en düşük sürüm dahil.

    - ] - en fazla sürüm dahil.

    - ( - en düşük sürüme özel.

    - ) - en yüksek sürüm özel.

    - Tek sürüm # - yalnızca belirtilen sürüm.

    > [!IMPORTANT]
    > VSIX Şemasının 2.0 sürümü, 2012 Visual Studio tanıtıldı. Bu şemayı kullanmak için makinede Visual Studio 2012 veya sonraki bir sürümün yüklü olması ve VSIXInstaller.exe parçası olan VSIXInstaller.exe'nin yüklü olması gerekir. Visual Studio 2012 veya sonraki vsIXInstaller ile Visual Studio'nin önceki sürümlerini hedefleyebilirsiniz, ancak yalnızca yükleyicinin sonraki sürümlerini kullanarak.

    Visual Studio 2017 sürüm numaraları derleme numaraları [Visual Studio yayın tarihleri içinde bulunabilir.](../install/visual-studio-build-numbers-and-release-dates.md)

    Visual Studio 2017 yayınlarını ifade etmek için ikincil sürüm her zaman **0 şeklindedir.** Örneğin, Visual Studio 2017 sürüm 15.3.26730.0 [15.0.26730.0,16.0) olarak ifade etmek gerekir. Bu yalnızca 2017 Visual Studio sonraki sürüm numaraları için gereklidir.

  - `AnyAttribute*` - `<InstallationTarget>` öğesi, çalışma zamanında bir ad-değer çifti sözlüğü olarak ortaya çıkar açık bir öznitelik kümesine izin verir.

### <a name="dependencies-element"></a>Dependencies öğesi
 Bu öğe, bu paketin bildir olduğu bağımlılıkların listesini içerir. Herhangi bir bağımlılık belirtilirse, bu paketler (ile `Id` tanımlanır) daha önce yüklenmiş olması gerekir.

- `<Dependency>` öğesi - Bu alt öğe aşağıdaki özniteliklere sahip:

  - `Id` - Bu öznitelik bağımlı paket için benzersiz bir kimlik olmalıdır. Bu kimlik değeri, bu `<Metadata><Identity>Id` paketin bağımlı olduğu bir paketin özniteliğiyle eşleşmesi gerekir. özniteliği `Id` ad alanı kuralına uyar: Company.Product.Feature.Name. özniteliği yalnızca alfasayısal karakterler içerebilir ve 100 karakterle sınırlıdır.

  - `Version` - Bu öznitelik, bu SKU'nun desteklenen en düşük ve en yüksek sürümlerine sahip bir sürüm aralığı belirtir. Bir paket, desteklediği S SU'ların sürümlerini ayrıntılı olarak inceler. Sürüm aralığı notasyonu [12.0, 13.0]'dır; burada:

    - [ - en düşük sürüm dahil.

    - ] - en fazla sürüm dahil.

    - ( - en düşük sürüme özel.

    - ) - en yüksek sürüm özel.

    - Tek sürüm # - yalnızca belirtilen sürüm.

  - `DisplayName` - Bu öznitelik, iletişim kutuları ve hata iletileri gibi kullanıcı arabirimi öğelerinde kullanılan bağımlı paketin görünen adıdır. Bağımlı paket MSI tarafından yüklenmediği sürece özniteliği isteğe bağlıdır.

  - `Location` - Bu isteğe bağlı öznitelik, bu VSIX içindeki göreli yolu iç içe vsIX paketine veya bağımlılığın indirme konumunun URL'sini belirtir. Bu öznitelik, kullanıcının önkoşul paketini bulmasını yardımcı olmak için kullanılır.

  - `AnyAttribute*` - öğesi, çalışma zamanında bir ad-değer çifti sözlüğü olarak açığa çıkacak açık bir öznitelik `Dependency` kümesi kabul eder.

### <a name="assets-element"></a>Assets öğesi
 Bu öğe, bu paket `<Asset>` tarafından ortaya çıkar her uzantı veya içerik öğesi için etiketlerin listesini içerir.

- `<Asset>` - Bu öğe aşağıdaki öznitelikleri ve öğeleri içerir:

  - `Type` - Bu öğe tarafından temsil edilen uzantı veya içerik türü. Her `<Asset>` öğe tek bir öğesine sahip `Type` olmalı, ancak birden çok öğe aynı `<Asset>` `Type` olabilir. Bu öznitelik, ad alanı kurallarına göre tam ad olarak temsil etmek gerekir. Bilinen türler:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       Kendi türlerinizi oluşturabilir ve onlara benzersiz adlar vesiniz. Uygulamanın içindeki çalışma Visual Studio, kodunuz Bu özel türleri Extension Manager API'si aracılığıyla numaralara numara olarak numaralar ve erişim sağlar.

  - `Path` - varlığı içeren paketin içindeki dosya veya klasörün göreli yolu.

  - `TargetVersion` - Verilen varlığın geçerli olduğu sürüm aralığı. Varlıkların birden çok sürümünü farklı Visual Studio. Geçerli Visual Studio 2017.3 veya daha yeni bir sürümü gerektirir.

  - `AnyAttribute*` - Çalışma zamanında bir ad-değer çifti sözlüğü olarak ortaya çıkar açık bir öznitelik kümesi.

    `<AnyElement>*` - Başlangıç ve bitiş etiketi arasında yapılandırılmış `<Asset>` içeriğe izin verilir. Tüm öğeler XmlElement nesnelerinin listesi olarak görüntülenir. VSIX uzantıları bildirim dosyasında türe özgü yapılandırılmış meta veriler tanımlayabilir ve çalışma zamanında bunları numaralandırabilirsiniz.

### <a name="sample-manifest"></a>Örnek bildirim

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
  <Metadata>
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />
    <DisplayName>Test Package</DisplayName>
    <Description>Information about my package</Description>
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>
    <License>eula.rtf</License>
    <ReleaseNotes>notes.txt</ReleaseNotes>
    <Icon>Images\icon.png</Icon>
    <PreviewImage>Images\preview.png</PreviewImage>
  </Metadata>
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio uzantıları gönder](../extensibility/shipping-visual-studio-extensions.md)
