---
title: VSıX uzantı Şeması 2,0 başvurusu | Microsoft Docs
description: VSIX uzantı Şeması 2,0, bir VSIX paketinin içeriğini açıklayan bir VSıX dağıtım bildirim dosyası için dosya biçimini tanımlar.
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
ms.workload:
- vssdk
ms.openlocfilehash: 66393bbe6383fcc6cae942a3d7e86f1d701a9634
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905247"
---
# <a name="vsix-extension-schema-20-reference"></a>VSıX uzantı Şeması 2,0 başvurusu
VSıX dağıtımı bildirim dosyası bir VSıX paketinin içeriğini açıklar. Dosya biçimi bir şemaya tabidir. Bu şemanın sürüm 2,0, özel türlerin ve özniteliklerin eklenmesini destekler.  Bildirimin şeması genişletilebilir. Bildirim yükleyicisi, anladığı XML öğelerini ve özniteliklerini yoksayar.

> [!IMPORTANT]
> Visual Studio 2015, Visual Studio 2010, Visual Studio 2012 veya Visual Studio 2013 biçimlerinde VSıX dosyaları yükleyebilir.

## <a name="package-manifest-schema"></a>Paket bildirim şeması
 Bildirim XML dosyasının kök öğesi `<PackageManifest>` . Bildirim biçiminin sürümü olan tek bir özniteliğe sahiptir `Version` . Biçimde büyük değişiklikler yapılırsa, sürüm biçimi değiştirilir. Bu makalede, `Version` özniteliği Version = "2.0" değerine ayarlanarak bildirimde belirtilen bildirim biçimi sürüm 2,0 açıklanmaktadır.

### <a name="packagemanifest-element"></a>PackageManifest öğesi
 `<PackageManifest>`Kök öğesi içinde, aşağıdaki öğeleri kullanabilirsiniz:

- `<Metadata>` -Paketin kendisi hakkındaki meta veriler ve reklam bilgileri. Bildirimde yalnızca bir `Metadata` öğeye izin veriliyor.

- `<Installation>` -Bu bölümde, bu uzantı paketinin yüklenebileceğine yönelik uygulama SKU 'Ları dahil olmak üzere nasıl yüklenebileceğine ilişkin tanımlar. Bildirimde yalnızca tek bir `Installation` öğeye izin veriliyor. Bildirimin bir `Installation` öğesi olmalıdır veya bu paket herhangi BIR SKU 'ya yüklenmez.

- `<Dependencies>` -Bu paket için isteğe bağlı bağımlılıkların listesi burada tanımlanmıştır.

- `<Assets>` -Bu bölüm, bu pakette bulunan tüm varlıkları içerir. Bu bölüm olmadan, bu paket herhangi bir içerik yüzeyine sahip değildir.

- `<AnyElement>*` -Bildirim şeması, diğer öğelere izin vermek için yeterince esnektir. Bildirim yükleyicisi tarafından tanınmayan tüm alt öğeler, ek XmlElement nesneleri olarak Uzantı Yöneticisi API 'sinde kullanıma sunulur. VSıX uzantıları, bu alt öğeleri kullanarak, Visual Studio 'da çalışan kodun çalışma zamanında erişebileceği bildirim dosyasında ek veriler tanımlayabilir. Bkz. [Microsoft. VisualStudio. ExtensionManager. IExtension. Adtionalelements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Metadata öğesi
 Bu bölüm, paket, kimlik ve reklam bilgileri hakkındaki meta verilerdir. `<Metadata>` Aşağıdaki öğeleri içerir:

- `<Identity>` -Bu paket için tanımlama bilgilerini tanımlar ve aşağıdaki öznitelikleri içerir:

  - `Id` -Bu öznitelik, yazarı tarafından seçilen paket için benzersiz bir KIMLIK olmalıdır. Ad, CLR türleri gösterilemez: Company.Product.Feature.Name gibi nitelenmelidir. `Id`Öznitelik 100 karakterle sınırlıdır.

  - `Version` -Bu paketin ve içeriğinin sürümünü tanımlar. Bu öznitelik CLR derleme sürümü oluşturma biçimini izler: Ana. Ikincil. derleme. Düzeltme (1.2.40308.00). Daha yüksek sürüm numarasına sahip bir paket, paket için güncelleştirmeler olarak değerlendirilir ve var olan yüklü sürümü üzerine yüklenebilir.

  - `Language` -Bu öznitelik, paket için varsayılan dildir ve bu bildirimdeki metin verilerine karşılık gelir. Bu öznitelik, kaynak derlemeleri için CLR yerel ayar kod kuralına uyar, örneğin: en-US, en, fr-fr. `neutral`Visual Studio 'nun herhangi bir sürümünde çalışacak dilden bağımsız bir uzantı bildirmek için öğesini belirtebilirsiniz. `neutral` varsayılan değerdir.

  - `Publisher` -Bu öznitelik, bu paketin yayımcısını bir şirket veya tek bir ad olarak tanımlar. `Publisher`Öznitelik 100 karakterle sınırlıdır.

- `<DisplayName>` -Bu öğe, Uzantı Yöneticisi Kullanıcı arabiriminde görüntülenen kullanıcı dostu paket adını belirtir. `DisplayName`İçerik 50 karakterle sınırlıdır.

- `<Description>` -Bu isteğe bağlı öğe, paketin ve Uzantı Yöneticisi Kullanıcı arabiriminde görüntülenen içeriğinin kısa bir açıklamasıdır. `Description`İçerik istediğiniz herhangi bir metin içerebilir, ancak 1000 karakterle sınırlıdır.

- `<MoreInfo>` -Bu isteğe bağlı öğe, çevrimiçi bir sayfanın bir URL 'sidir ve bu paketin tam açıklamasını içerir. Protokol http olarak belirtilmelidir.

- `<License>` -Bu isteğe bağlı öğe, pakette bulunan bir lisans dosyasının (.txt,. rtf) göreli yoludur.

- `<ReleaseNotes>` -Bu isteğe bağlı öğe, paketteki (.txt,. rtf) yer alan bir sürüm notları dosyasının göreli yoludur veya sürüm notlarını görüntüleyen bir Web sitesinin URL 'sidir.

- `<Icon>` -Bu isteğe bağlı öğe, pakette bulunan bir görüntü dosyası (PNG, BMP, JPEG, ico) için göreli bir yoldur. Simge görüntüsü 32x32 piksel olmalıdır (veya bu boyuta küçültülecektir) ve ListView Kullanıcı arabiriminde görünür. Hiçbir `Icon` öğe belirtilmemişse, Kullanıcı arabirimi varsayılan kullanır.

- `<PreviewImage>` -Bu isteğe bağlı öğe, pakette bulunan bir görüntü dosyasının (PNG, BMP, JPEG) göreli yoludur. Önizleme resmi 200x200 piksel olmalıdır ve Ayrıntılar Kullanıcı arabiriminde görüntülenir. Hiçbir `PreviewImage` öğe belirtilmemişse, Kullanıcı arabirimi varsayılan kullanır.

- `<Tags>` -Bu isteğe bağlı öğe, arama ipuçları için kullanılan ek noktalı virgülle ayrılmış metin etiketlerini listeler. `Tags`Öğesi 100 karakterle sınırlıdır.

- `<GettingStartedGuide>` -Bu isteğe bağlı öğe, bir HTML dosyasına yönelik göreli bir yoldur veya uzantının veya içeriğin Bu pakette nasıl kullanılacağı hakkında bilgi içeren bir Web sitesinin URL 'sidir. Bu kılavuz, bir yüklemenin parçası olarak başlatılır.

- `<AnyElement>*` -Bildirim şeması, diğer öğelere izin vermek için yeterince esnektir. Bildirim yükleyicisi tarafından tanınmayan tüm alt öğeler, XmlElement nesnelerinin bir listesi olarak gösterilir. VSıX uzantıları bu alt öğeleri kullanarak, bildirim dosyasında ek veriler tanımlayabilir ve bunları çalışma zamanında numaralandırabilirler.

### <a name="installation-element"></a>Yükleme öğesi
 Bu bölüm, bu paketin yüklenebileceğine ve yüklenebileceğine yönelik uygulama SKU 'Larının yolunu tanımlar. Bu bölüm aşağıdaki öznitelikleri içerir:

- `Experimental` -Tüm kullanıcılar için o anda yüklü olan bir uzantıya sahipseniz, ancak aynı bilgisayarda güncelleştirilmiş bir sürüm geliştirdiğinizi bu özniteliği true olarak ayarlayın. Örneğin, tüm kullanıcılar için MyExtension 1,0 ' i yüklediyseniz, ancak aynı bilgisayarda MyExtension 2,0 ' de hata ayıklamak istiyorsanız, deneysel = "true" olarak ayarlayın. Bu öznitelik, Visual Studio 2015 güncelleştirme 1 ve sonraki sürümlerinde kullanılabilir.

- `Scope` -Bu öznitelik "Global" veya "ProductExtension" değerini alabilir:

  - "Genel", yüklemenin belirli bir SKU 'ya kapsam dışı olduğunu belirtir. Örneğin, bu değer bir uzantı SDK 'Sı yüklendiğinde kullanılır.

  - "ProductExtension" geleneksel bir VSıX uzantısının (sürüm 1,0) tek tek Visual Studio SKU 'Larının yüklü olduğunu belirtir. Varsayılan değer budur.

- `AllUsers` -Bu isteğe bağlı öznitelik, bu paketin tüm kullanıcılar için yüklenip yüklenmeyeceğini belirtir. Varsayılan olarak, bu öznitelik false şeklindedir ve paketin Kullanıcı başına olduğunu belirtir. (Bu değeri true olarak belirlediğinizde, yükleme Kullanıcı, sonuçta elde edilen VSıX 'i yüklemek için yönetici ayrıcalık düzeyine yükseltilmelidir.

- `InstalledByMsi` -Bu isteğe bağlı öznitelik, bu paketin bir MSI tarafından yüklenip yüklenmediğini belirtir. MSI tarafından yüklenen paketler, Visual Studio Uzantı Yöneticisi tarafından değil, MSI (Programlar ve Özellikler) tarafından yüklenir ve yönetilir.  Varsayılan olarak, bu öznitelik, paketin bir MSI tarafından yüklenmediğini belirten false değeridir.

- `SystemComponent` -Bu isteğe bağlı öznitelik, bu paketin bir sistem bileşeni olarak kabul edilip edilmeyeceğini belirtir. Sistem bileşenleri Uzantı Yöneticisi Kullanıcı arabiriminde gösterilmez ve güncelleştirilemez. Varsayılan olarak, bu öznitelik, paketin bir sistem bileşeni olmadığını belirten false değeridir.

- `AnyAttribute*` - `Installation` Öğesi, çalışma zamanında ad-değer çifti sözlüğü olarak sunulacak bir açık uçlu Öznitelikler kümesini kabul eder.

- `<InstallationTarget>` -Bu öğe, VSıX yükleyicisinin paketi yüklediği konumu denetler. Eğer `Scope` özniteliğin değeri "ProductExtension" ise paketin, kendi içeriğinin bir parçası olarak bir bildirim dosyası yükleyen BIR SKU 'yu hedeflemesi gerekir. `<InstallationTarget>` `Scope` Özniteliği açık veya varsayılan "ProductExtension" değerine sahip olduğunda öğesi aşağıdaki özniteliklere sahiptir:

  - `Id` -Bu öznitelik, paketini tanımlar.  Öznitelik, ad alanı kuralına uyar: Company.Product.Feature.Name. `Id`Öznitelik yalnızca alfasayısal karakterler içerebilir ve 100 karakterle sınırlıdır. Beklenen değerler:

    - Microsoft. VisualStudio. ıntegratedshell

    - Microsoft.VisualStudio.Pro

    - Microsoft. VisualStudio. Premium

    - Microsoft. VisualStudio. Ultimate

    - Microsoft. VisualStudio. Ödexpress

    - Microsoft. VisualStudio. VPDExpress

    - Microsoft. VisualStudio. VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version` - Bu öznitelik, bu SKU'nun desteklenen en düşük ve en yüksek sürümlerine sahip bir sürüm aralığını belirtir. Bir paket, desteklediği S SU'ların sürümlerini ayrıntılı olarak inceler. Sürüm aralığı şu şekildedir: [10.0 - 11.0], burada

    - [ - en düşük sürüm dahil.

    - ] - en fazla sürüm dahil.

    - ( - en düşük sürüme özel.

    - ) - en yüksek sürüm özeldir.

    - Tek sürüm # - yalnızca belirtilen sürüm.

    > [!IMPORTANT]
    > VSIX Şemasının 2.0 sürümü, 2012 Visual Studio tanıtıldı. Bu şemayı kullanmak için makinede Visual Studio 2012 veya sonraki bir sürümün yüklü olması ve VSIXInstaller.exe parçası olan sanal makinelerin yüklü olması gerekir. Visual Studio 2012 veya sonraki vsIXInstaller ile Visual Studio'nin önceki sürümlerini hedefleyebilirsiniz, ancak yalnızca yükleyicinin sonraki sürümlerini kullanarak.

    Visual Studio 2017 sürüm numaraları derleme numaraları [Visual Studio yayın tarihleri içinde bulunabilir.](../install/visual-studio-build-numbers-and-release-dates.md)

    Visual Studio 2017 yayınlarını ifade etmek için ikincil sürüm her zaman **0 şeklindedir.** Örneğin, Visual Studio 2017 sürüm 15.3.26730.0 [15.0.26730.0,16.0) olarak ifade etmek gerekir. Bu yalnızca 2017 Visual Studio sonraki sürüm numaraları için gereklidir.

  - `AnyAttribute*` - `<InstallationTarget>` öğesi, çalışma zamanında bir ad-değer çifti sözlüğü olarak ortaya çıkar açık bir öznitelik kümesine izin verir.

### <a name="dependencies-element"></a>Dependencies öğesi
 Bu öğe, bu paketin bildir olduğu bağımlılıkların listesini içerir. Herhangi bir bağımlılık belirtilirse, bu paketler (ile `Id` tanımlanır) daha önce yüklenmiş olması gerekir.

- `<Dependency>` öğesi - Bu alt öğe aşağıdaki özniteliklere sahip:

  - `Id` - Bu öznitelik bağımlı paket için benzersiz bir kimlik olmalıdır. Bu kimlik değeri, bu `<Metadata><Identity>Id` paketin bağımlı olduğu bir paketin özniteliğiyle eşleşmesi gerekir. özniteliği `Id` ad alanı kuralına uyar: Company.Product.Feature.Name. özniteliği yalnızca alfasayısal karakterler içerebilir ve 100 karakterle sınırlıdır.

  - `Version` - Bu öznitelik, bu SKU'nun desteklenen en düşük ve en yüksek sürümlerine sahip bir sürüm aralığını belirtir. Bir paket, desteklediği S SU'ların sürümlerini ayrıntılı olarak inceler. Sürüm aralığı notasyonu [12.0, 13.0]'dır; burada:

    - [ - en düşük sürüm dahil.

    - ] - en fazla sürüm dahil.

    - ( - en düşük sürüme özel.

    - ) - en yüksek sürüm özeldir.

    - Tek sürüm # - yalnızca belirtilen sürüm.

  - `DisplayName` - Bu öznitelik, iletişim kutuları ve hata iletileri gibi kullanıcı arabirimi öğelerinde kullanılan bağımlı paketin görünen adıdır. Bağımlı paket MSI tarafından yüklenmediği sürece özniteliği isteğe bağlıdır.

  - `Location` - Bu isteğe bağlı öznitelik, bu VSIX içindeki göreli yolu iç içe vsIX paketine veya bağımlılığın indirme konumunun URL'sini belirtir. Bu öznitelik, kullanıcının önkoşul paketini bulmasını yardımcı olmak için kullanılır.

  - `AnyAttribute*` - öğesi, çalışma zamanında bir ad-değer çifti sözlüğü olarak açığa çıkacak açık bir öznitelik `Dependency` kümesi kabul eder.

### <a name="assets-element"></a>Assets öğesi
 Bu öğe, bu paket `<Asset>` tarafından ortaya çıkarıla her uzantı veya içerik öğesi için etiketlerin listesini içerir.

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
