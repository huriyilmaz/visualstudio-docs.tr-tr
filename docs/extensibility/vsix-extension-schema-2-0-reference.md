---
title: VSIX Uzatma Şeması 2.0 Referans | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697924"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX uzantı şeması 2.0 referans
VSIX dağıtım bildirimi dosyası, bir VSIX paketinin içeriğini açıklar. Dosya biçimi bir şema tarafından yönetilir. Bu şema Sürüm 2.0 özel türleri ve öznitelikleri ekleme destekler.  Manifestonun şeması genişletilebilir. Manifest yükleyici XML öğelerini ve anlamadığı öznitelikleri yok sayar.

> [!IMPORTANT]
> Visual Studio 2015, Visual Studio 2010, Visual Studio 2012 veya Visual Studio 2013 formatlarında VSIX dosyalarını yükleyebilir.

## <a name="package-manifest-schema"></a>Paket manifesto şeması
 Manifeste XML dosyasının kök `<PackageManifest>`öğesi. Bu manifesto biçiminin `Version`sürümü olan tek bir özniteliği vardır. Biçimde büyük değişiklikler yapılırsa, sürüm biçimi değiştirilir. Bu makalede, Sürüm="2.0" değerine özniteliği `Version` ayarlayarak bildirimde belirtilen manifesto biçimi sürüm 2.0 açıklanmaktadır.

### <a name="packagemanifest-element"></a>PackageManifest öğesi
 `<PackageManifest>` Kök öğesi içinde aşağıdaki öğeleri kullanabilirsiniz:

- `<Metadata>`- Meta veri ve paketin kendisi hakkında reklam bilgileri. Bildirimde `Metadata` yalnızca bir öğeye izin verilir.

- `<Installation>`- Bu bölümde, bu uzantı paketinin yüklenebildiği uygulama SUS'ları da dahil olmak üzere nasıl yüklenebileceği tanımlanır. Bildirimde `Installation` yalnızca tek bir öğeye izin verilir. Bir bildirimin `Installation` bir öğesi olmalıdır veya bu paket herhangi bir SKU'ya yüklenmez.

- `<Dependencies>`- Bu paket için isteğe bağlı bağımlılıklistesi burada tanımlanır.

- `<Assets>`- Bu bölümde, bu pakette yer alan tüm varlıklar yer almaktadır. Bu bölüm olmadan, bu paket herhangi bir içerik yüzey olmaz.

- `<AnyElement>*`- Manifesto şeması diğer unsurlara izin verecek kadar esnektir. Bildirim yükleyici tarafından tanınmayan alt öğeler, Uzantı Yöneticisi API'sinde ekstra XmlElement nesneleri olarak ortaya çıkar. Bu alt öğeleri kullanarak, VSIX uzantıları Visual Studio'da çalışan kodun çalışma zamanında erişebileceği bildirim dosyasında ek veriler tanımlayabilir. Bkz. [Microsoft.visualstudio.extensionManager.iextension.additionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Meta veri öğesi
 Bu bölüm, paket, kimliği ve reklam bilgileri yle ilgili meta verilerdir. `<Metadata>`aşağıdaki öğeleri içerir:

- `<Identity>`- Bu paketin kimlik bilgilerini tanımlar ve aşağıdaki öznitelikleri içerir:

  - `Id`- Bu öznitelik, yazarı tarafından seçilen paket için benzersiz bir kimlik olmalıdır. Ad, CLR türlerinin ad alanı olarak nitelenmiş olması gerekir: Company.Product.Feature.Name. Öznitelik `Id` 100 karakterle sınırlıdır.

  - `Version`- Bu paketin sürümünü ve içeriğini tanımlar. Bu öznitelik CLR derleme sürüm biçimini izler: Major.Minor.Build.Revision (1.2.40308.00). Daha yüksek sürüm numarasına sahip bir paket, paketin güncelleştirmeleri olarak kabul edilir ve varolan yüklenen sürümün üzerine yüklenebilir.

  - `Language`- Bu öznitelik paketin varsayılan dilidir ve bu bildirimdeki metin verilerine karşılık gelir. Bu öznitelik, kaynak derlemeleri için CLR yerel kod kuralını izler, örneğin: en-us, en, fr-fr. Visual Studio'nun herhangi bir sürümünde çalışacak dilden bağımsız bir uzantı bildirmek için belirtebilirsiniz. `neutral` Varsayılan değer: `neutral`.

  - `Publisher`- Bu öznitelik, bu paketin yayımcısını, bir şirket veya tek tek adı tanımlar. Öznitelik `Publisher` 100 karakterle sınırlıdır.

- `<DisplayName>`- Bu öğe, Uzantı Yöneticisi Kullanıcı Arabirimi'nde görüntülenen kullanıcı dostu paket adını belirtir. İçerik `DisplayName` 50 karakterle sınırlıdır.

- `<Description>`- Bu isteğe bağlı öğe, uzantı yöneticisi ui'de görüntülenen paketin ve içeriğinin kısa bir açıklamasıdır. İçerik `Description` istediğiniz herhangi bir metni içerebilir, ancak 1000 karakterle sınırlıdır.

- `<MoreInfo>`- Bu isteğe bağlı öğe, bu paketin tam açıklamasını içeren çevrimiçi bir sayfanın URL'sidir. Protokol http olarak belirtilmelidir.

- `<License>`- Bu isteğe bağlı öğe, pakette bulunan bir lisans dosyasına (.txt, .rtf) göreli bir yoldur.

- `<ReleaseNotes>`- Bu isteğe bağlı öğe, pakette bulunan bir sürüm notları dosyasına göreli bir yoldur (.txt, .rtf) veya sürüm notlarını görüntüleyen bir web sitesinin URL'sidir.

- `<Icon>`- Bu isteğe bağlı öğe, pakette bulunan bir görüntü dosyasına (png, bmp, jpeg, ico) göreli bir yoldur. Simge görüntüsü 32x32 piksel olmalıdır (veya bu boyuta küçültülecek) ve listview UI görünür. Hiçbir `Icon` öğe belirtilmemişse, UI varsayılan kullanır.

- `<PreviewImage>`- Bu isteğe bağlı öğe, pakette bulunan bir görüntü dosyasına (png, bmp, jpeg) göreli bir yoldur. Önizleme görüntüsü 200x200 piksel olmalı ve ayrıntılarda UI görüntülenmelidir. Hiçbir `PreviewImage` öğe belirtilmemişse, UI varsayılan kullanır.

- `<Tags>`- Bu isteğe bağlı öğe, arama ipuçları için kullanılan ek yarı sütunlu sınırlı metin etiketlerini listeler. Öğe `Tags` 100 karakterle sınırlıdır.

- `<GettingStartedGuide>`- Bu isteğe bağlı öğe, bir HTML dosyasına göreli bir yoldur veya bu paketteki uzantı veya içeriğin nasıl kullanılacağı hakkında bilgi içeren bir web sitesinin URL'sidir. Bu kılavuz yüklemenin bir parçası olarak başlatılır.

- `<AnyElement>*`- Manifesto şeması diğer unsurlara izin verecek kadar esnektir. Bildirim yükleyici tarafından tanınmayan tüm alt öğeler XmlElement nesnelerinin listesi olarak ortaya çıkar. Bu alt öğeleri kullanarak, VSIX uzantıları bildirim dosyasında ek verileri tanımlayabilir ve çalışma zamanında numaralandırmak.

### <a name="installation-element"></a>Kurulum elemanı
 Bu bölümde, bu paketin nasıl yüklenebileceği ve yükleyebileceği uygulama SUS'ları tanımlanır. Bu bölümde aşağıdaki öznitelikleri içerir:

- `Experimental`- Şu anda tüm kullanıcılar için yüklü bir uzantınız varsa, ancak aynı bilgisayarda güncelleştirilmiş bir sürüm geliştiriyorsanız, bu özniteliği doğru olarak ayarlayın. Örneğin, tüm kullanıcılar için MyExtension 1.0 yüklediyseniz, ancak MyExtension 2.0'ı aynı bilgisayarda hata ayıklamak istiyorsanız, Experimental="true"u ayarlayın. Bu özellik Visual Studio 2015 Update 1 ve sonraki yerlerde kullanılabilir.

- `Scope`- Bu öznitelik "Global" veya "ProductExtension" değerini alabilir:

  - "Global", yüklemenin belirli bir SKU kapsamına dahil olmadığını belirtir. Örneğin, bir Uzantı SDK yüklendiğinde bu değer kullanılır.

  - "ProductExtension", bireysel Visual Studio SKU'ları içeren geleneksel bir VSIX Uzantısının (sürüm 1.0) yüklü olduğunu belirtir. Varsayılan değer budur.

- `AllUsers`- Bu isteğe bağlı öznitelik, bu paketin tüm kullanıcılar için yüklenip yüklenmeyeceğini belirtir. Varsayılan olarak, bu öznitelik, paketin kullanıcı başına olduğunu belirten yanlıştır. (Bu değeri doğru ayarladığınızda, yükleme kullanıcısının elde edilen VSIX'yi yüklemek için yönetim ayrıcalık düzeyine yükseltmesi gerekir.

- `InstalledByMsi`- Bu isteğe bağlı öznitelik, bu paketin bir MSI tarafından yüklenip yüklenmediğini belirtir. MSI tarafından yüklenen paketler Visual Studio Extension Manager tarafından değil, MSI (Programlar ve Özellikler) tarafından yüklenir ve yönetilir.  Varsayılan olarak, bu öznitelik, paketin bir MSI tarafından yüklenmediğini belirten yanlıştır.

- `SystemComponent`- Bu isteğe bağlı öznitelik, bu paketin bir sistem bileşeni olarak kabul edilip edilmemesi gerektiğini belirtir. Sistem bileşenleri Uzantı Yöneticisi UI'de gösterilmez ve güncelleştirilemez. Varsayılan olarak, bu öznitelik, paketin bir sistem bileşeni olmadığını belirten yanlıştır.

- `AnyAttribute*`- `Installation` Öğe, çalışma zamanında açık uçlu öznitelikler kümesini ad değeri çifti sözlüğü olarak kabul eder.

- `<InstallationTarget>`-Bu eleman, VSIX yükleyicisinin paketi yüklendiği yeri kontrol eder. Özniteliğin `Scope` değeri "ProductExtension" ise, paketin uzantılarına kullanılabilirliğini bildirmek için içeriğinin bir parçası olarak bir manifesto dosyası yüklemiş olan bir SKU'yu hedeflemesi gerekir. Öznitelik `<InstallationTarget>` açık veya varsayılan `Scope` değeri "ProductExtension" olduğunda öğe aşağıdaki özniteliklere sahiptir:

  - `Id`- Bu öznitelik paketi tanımlar.  Öznitelik ad alanı kuralını izler: Company.Product.Feature.Name. Öznitelik `Id` yalnızca alfasayısal karakterler içerebilir ve 100 karakterle sınırlıdır. Beklenen değerler:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version`- Bu özellik, bu SKU'nun en az ve maksimum desteklenen sürümlerine sahip bir sürüm aralığı belirtir. Paket, desteklediği SNU'ların sürümlerini ayrıntılarıyla anlatabilir. Sürüm aralığı gösterimi [10.0 - 11.0], nerede

    - [ - minimum sürüm dahil.

    - ] - maksimum sürüm dahil.

    - ( - minimum sürüm özel.

    - ) - maksimum sürüm özel.

    - Tek sürüm # - sadece belirtilen sürümü.

    > [!IMPORTANT]
    > VSIX Schema sürümü 2.0 Visual Studio tanıtıldı 2012. Bu şemayı kullanmak için Visual Studio 2012 veya daha sonra makineye yüklenmiş olmalı ve bu ürünün bir parçası olan VSIXInstaller.exe'yi kullanmalısınız. Visual Studio'nun önceki sürümlerini Visual Studio 2012 veya daha sonra VSIXInstaller ile, ancak yükleyicinin sonraki sürümlerini kullanarak hedefleyebilirsiniz.

    Visual Studio 2017 sürüm numaraları [Visual Studio yapı numaraları ve çıkış tarihlerinde](../install/visual-studio-build-numbers-and-release-dates.md)bulunabilir.

    Visual Studio 2017 sürümleri için sürümü ifade ederken, küçük sürümü her zaman **0**olmalıdır . Örneğin, Visual Studio 2017 sürüm 15.3.26730.0 [15.0.26730.0,16.0) olarak ifade edilmelidir. Bu sadece Visual Studio 2017 ve sonraki sürüm numaraları için gereklidir.

  - `AnyAttribute*`- `<InstallationTarget>` Öğe, çalışma zamanında ad değeri çifti sözlüğü olarak açık uçlu özniteliklerkümesine izin verir.

### <a name="dependencies-element"></a>Bağımlılıklar öğesi
 Bu öğe, bu paketin bildirdiği bağımlılıkların listesini içerir. Herhangi bir bağımlılık belirtilmişse, bu `Id`paketler (kendi tarafından tanımlanan) daha önce yüklenmiş olmalıdır.

- `<Dependency>`eleman - Bu alt öğe aşağıdaki özniteliklere sahiptir:

  - `Id`- Bu öznitelik bağımlı paket için benzersiz bir kimlik olmalıdır. Bu kimlik değeri, `<Metadata><Identity>Id` bu paketin bağımlı olduğu bir paketin özniteliğiyle eşleşmelidir. Öznitelik `Id` ad alanı kuralını izler: Company.Product.Feature.Name. Öznitelik yalnızca alfasayısal karakterler içerebilir ve 100 karakterle sınırlıdır.

  - `Version`- Bu özellik, bu SKU'nun en az ve maksimum desteklenen sürümlerine sahip bir sürüm aralığı belirtir. Paket, desteklediği SNU'ların sürümlerini ayrıntılarıyla anlatabilir. Sürüm aralığı gösterimi [12.0, 13.0], nerede:

    - [ - minimum sürüm dahil.

    - ] - maksimum sürüm dahil.

    - ( - minimum sürüm özel.

    - ) - maksimum sürüm özel.

    - Tek sürüm # - sadece belirtilen sürümü.

  - `DisplayName`- Bu öznitelik, iletişim kutuları ve hata iletileri gibi Kullanıcı Arabirimi öğelerinde kullanılan bağımlı paketin görüntü adıdır. Bağımlı paket MSI tarafından yüklenmediği sürece öznitelik isteğe bağlıdır.

  - `Location`- Bu isteğe bağlı öznitelik, bu VSIX içindeki göreli yolu iç içe geçen bir VSIX paketine veya bağımlılık için indirme konumuna bir URL olarak belirtir. Bu öznitelik, kullanıcının ön koşul paketini bulmasına yardımcı olmak için kullanılır.

  - `AnyAttribute*`- `Dependency` Öğe, çalışma zamanında açık uçlu öznitelikler kümesini ad değeri çifti sözlüğü olarak kabul eder.

### <a name="assets-element"></a>Varlıklar öğesi
 Bu öğe, bu `<Asset>` paket tarafından su yüzüne çıkan her uzantı veya içerik öğesi için etiketlerin listesini içerir.

- `<Asset>`- Bu öğe aşağıdaki öznitelikleri ve öğeleri içerir:

  - `Type`- Bu öğe tarafından temsil edilen uzantı veya içerik türü. Her `<Asset>` öğenin tek `Type`bir `<Asset>` öğesi olmalıdır, `Type`ancak birden çok öğe aynı olabilir. Bu öznitelik, ad alanı kurallarına göre tam nitelikli bir ad olarak temsil edilmelidir. Bilinen türleri şunlardır:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       Kendi türlerinizi oluşturabilir ve onlara benzersiz adlar verebilirsiniz. Visual Studio içinde çalışma zamanında, kodunuz uzantı yöneticisi API üzerinden numaralandırma ve bu özel türleri erişebilirsiniz.

  - `Path`- kıymeti içeren paket içindeki dosya veya klasöre göreli yol.

  - `TargetVersion`- verilen varlığın uygulandığı sürüm aralığı. Varlıkların birden çok versiyonunu Visual Studio'nun farklı sürümlerine nakletmek için kullanılır. Visual Studio 2017.3 veya daha yeni etkisi olmasını gerektirir.

  - `AnyAttribute*`- Ad değeri çifti sözlüğü olarak çalışma zamanında ortaya çıkarılan açık uçlu öznitelikler kümesi.

    `<AnyElement>*`- Herhangi bir yapılandırılmış `<Asset>` içerik bir başlangıç ve bitiş etiketi arasında izin verilir. Tüm öğeler XmlElement nesnelerin in bir listesi olarak maruz kalır. VSIX uzantıları, bildirim dosyasında yapılı türe özgü meta verileri tanımlayabilir ve bunları çalışma zamanında numaralandırmak için kullanılabilir.

### <a name="sample-manifest"></a>Örnek manifesto

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

- [Gemi Görsel Stüdyo uzantıları](../extensibility/shipping-visual-studio-extensions.md)
