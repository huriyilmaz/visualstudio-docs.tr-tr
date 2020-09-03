---
title: VSıX uzantı Şeması 2,0 başvurusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b63f226b7aaadb851eab95f9b60f88f8f2be5ff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68869987"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX Uzantı Şeması 2.0 Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSıX dağıtımı bildirim dosyası bir VSıX paketinin içeriğini açıklar. Dosya biçimi bir şemaya tabidir. Bu şemanın sürüm 2,0, özel türlerin ve özniteliklerin eklenmesini destekler.  Bildirimin şeması genişletilebilir. Bildirim yükleyicisi, anladığı XML öğelerini ve özniteliklerini yoksayar.

> [!IMPORTANT]
> Visual Studio 2015, Visual Studio 2010, Visual Studio 2012 veya Visual Studio 2013 biçimlerinde VSıX dosyaları yükleyebilir.

## <a name="package-manifest-schema"></a>Paket bildirim şeması
 Bildirim XML dosyasının kök öğesi, `<PackageManifest>` bildirim biçiminin sürümü olan tek bir özniteliğiyle birlikte bulunur `Version` . Biçimde büyük değişiklikler yapılırsa, sürüm biçimi değiştirilir. Bu konuda, `Version` özniteliği Version = "2.0" değerine ayarlanarak bildirimde belirtilen bildirim biçimi sürüm 2,0 açıklanmaktadır.

### <a name="packagemanifest-element"></a>PackageManifest öğesi
 `<PackageManifest>`Kök öğesi içinde, aşağıdaki öğeleri kullanabilirsiniz:

- `<Metadata>` -Paketin kendisi hakkındaki meta veriler ve reklam bilgileri. Bildirimde yalnızca bir `Metadata` öğeye izin veriliyor.

- `<Installation>` -Bu bölümde, bu uzantı paketinin yüklenebileceğine yönelik uygulama SKU 'Ları dahil olmak üzere nasıl yüklenebileceğine ilişkin tanımlar. Bildirimde yalnızca tek bir `Installation` öğeye izin veriliyor. Bildirimin bir `Installation` öğesi olmalıdır veya bu paket herhangi BIR SKU 'ya yüklenmez.

- `<Dependencies>` -Bu paket için isteğe bağlı bağımlılıkların listesi burada tanımlanmıştır.

- `<Assets>` -Bu bölüm, bu pakette bulunan tüm varlıkları içerir. Bu bölüm olmadan, bu paket herhangi bir içerik yüzeyine sahip değildir.

- `<AnyElement>*` -Bildirim şeması, diğer öğelere izin vermek için yeterince esnektir. Bildirim yükleyicisi tarafından tanınmayan tüm alt öğeler, ek XmlElement nesneleri olarak Uzantı Yöneticisi API 'sinde kullanıma sunulur. VSıX uzantıları bu alt öğeleri kullanarak, Visual Studio 'da çalışan kodun çalışma zamanında erişebileceği bildirim dosyasında ek veriler tanımlayabilir. Bkz. [Adtionalelements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Metadata öğesi
 Bu bölüm, paket, kimlik ve reklam bilgileri hakkındaki meta verilerdir. `<Metadata>` Aşağıdaki öğeleri içerir:

- `<Identity>` -Bu, bu paket için tanımlama bilgilerini tanımlar ve aşağıdaki öznitelikleri içerir:

  - `Id` – Bu öznitelik, yazarı tarafından seçilen paket için benzersiz bir KIMLIK olmalıdır. Ad, CLR türleri gösterilemez: Company.Product.Feature.Name gibi nitelenmelidir. `Id`Öznitelik 100 karakterle sınırlıdır.

  - `Version` – Bu, paketin ve içeriğinin sürümünü tanımlar. Bu öznitelik CLR derleme sürümü oluşturma biçimini izler: Ana. Ikincil. derleme. Düzeltme (1.2.40308.00). Daha yüksek sürüm numarasına sahip bir paket, paket için güncelleştirmeler olarak değerlendirilir ve var olan yüklü sürümü üzerine yüklenebilir.

  - `Language` – Bu öznitelik, paket için varsayılan dildir ve bu bildirimdeki metin verilerine karşılık gelir. Bu öznitelik, kaynak derlemeleri için CLR yerel ayar kod kuralına uyar, örneğin: en-US, en, fr-fr. `neutral`Visual Studio 'nun herhangi bir sürümünde çalışacak dilden bağımsız bir uzantı bildirmek için öğesini belirtebilirsiniz. Varsayılan değer: `neutral`.

  - `Publisher` – Bu öznitelik, bu paketin yayımcısını bir şirket veya tek bir ad olarak tanımlar. `Publisher`Öznitelik 100 karakterle sınırlıdır.

- `<DisplayName>` -Bu öğe, Uzantı Yöneticisi Kullanıcı arabiriminde görüntülenen kullanıcı dostu paket adını belirtir. `DisplayName`İçerik 100 karakterle sınırlıdır.

- `<Description>` -Bu isteğe bağlı öğe, paketin ve Uzantı Yöneticisi Kullanıcı arabiriminde görüntülenen içeriğinin kısa bir açıklamasıdır. `Description`İçerik istediğiniz herhangi bir metin içerebilir, ancak 1000 karakterle sınırlıdır.

- `<MoreInfo>` -Bu isteğe bağlı öğe, çevrimiçi bir sayfanın bir URL 'sidir ve bu paketin tam açıklamasını içerir. Protokol http olarak belirtilmelidir.

- `<License>` -Bu isteğe bağlı öğe, pakette bulunan bir lisans dosyasının (. txt,. rtf) göreli yoludur.

- `<ReleaseNotes>` -Bu isteğe bağlı öğe, pakette (. txt,. rtf) bulunan bir sürüm notları dosyasının göreli yoludur veya sürüm notlarını görüntüleyen bir Web sitesinin URL 'sidir.

- `<Icon>` -Bu isteğe bağlı öğe, pakette bulunan bir görüntü dosyası (PNG, BMP, JPEG, ico) için göreli bir yoldur. Simge görüntüsü 32x32 piksel olmalıdır (veya bu boyuta küçültülecektir) ve ListView Kullanıcı arabiriminde görünür. Hiçbir `Icon` öğe belirtilmemişse, Kullanıcı arabirimi varsayılan kullanır.

- `<PreviewImage>` -Bu isteğe bağlı öğe, pakette bulunan bir görüntü dosyasının (PNG, BMP, JPEG) göreli yoludur. Önizleme resmi 200x200 piksel olmalıdır ve Ayrıntılar Kullanıcı arabiriminde görüntülenir. Hiçbir `PreviewImage` öğe belirtilmemişse, Kullanıcı arabirimi varsayılan kullanır.

- `<Tags>` -Bu isteğe bağlı öğe, arama ipuçları için kullanılan ek noktalı virgülle ayrılmış metin etiketlerini listeler. `Tags`Öğesi 100 karakterle sınırlıdır.

- `<GettingStartedGuide>` -Bu isteğe bağlı öğe, bir HTML dosyasına yönelik göreli bir yoldur veya uzantının veya içeriğin Bu pakette nasıl kullanılacağı hakkında bilgi içeren bir Web sitesinin URL 'sidir. Bu kılavuz, bir yüklemenin parçası olarak başlatılır.

- `<AnyElement>*` -Bildirim şeması, diğer öğelere izin vermek için yeterince esnektir. Bildirim yükleyicisi tarafından tanınmayan tüm alt öğeler, XmlElement nesnelerinin bir listesi olarak gösterilir. VSıX uzantıları bu alt öğeleri kullanarak, bildirim dosyasında ek veri tanımlayabilir ve bunları çalışma zamanında numaralandırabilirsiniz.

### <a name="installation-element"></a>Yükleme öğesi
 Bu bölüm, bu paketin yüklenebileceğine ve yüklenebileceğine yönelik uygulama SKU 'Larının yolunu tanımlar. Bu bölüm aşağıdaki öznitelikleri içerir:

- `Experimental` – Tüm kullanıcılar için o anda yüklü olan bir uzantıya sahipseniz, ancak aynı bilgisayarda güncelleştirilmiş bir sürüm geliştirdiğinizi bu özniteliği true olarak ayarlayın. Örneğin, tüm kullanıcılar için MyExtension 1,0 ' i yüklediyseniz, ancak aynı bilgisayarda MyExtension 2,0 ' de hata ayıklamak istiyorsanız, deneysel = "true" olarak ayarlayın. Bu öznitelik, Visual Studio 2015 güncelleştirme 1 ve sonraki sürümlerinde kullanılabilir.

- `Scope` – Bu öznitelik "Global" veya "ProductExtension" değerini alabilir:

  - "Genel", yüklemenin belirli bir SKU 'ya kapsam dışı olduğunu belirtir. Örneğin, bu değer bir uzantı SDK 'Sı yüklendiğinde kullanılır.

  - "ProductExtension" geleneksel bir VSıX uzantısının (sürüm 1,0) tek tek Visual Studio SKU 'Larının yüklü olduğunu belirtir. Varsayılan değer budur.

- `AllUsers` – Bu isteğe bağlı öznitelik, bu paketin tüm kullanıcılar için yüklenip yüklenmeyeceğini belirtir. Varsayılan olarak, bu öznitelik false şeklindedir ve paketin Kullanıcı başına olduğunu belirtir. (Bu değeri true olarak belirlediğinizde, yükleme Kullanıcı, sonuçta elde edilen VSıX 'i yüklemek için yönetici ayrıcalık düzeyine yükseltilmelidir.

- `InstalledByMsi` – Bu isteğe bağlı öznitelik, bu paketin bir MSI tarafından yüklenip yüklenmediğini belirtir. MSI tarafından yüklenen paketler, Visual Studio Uzantı Yöneticisi tarafından değil, MSI (Programlar ve Özellikler) tarafından yüklenir ve yönetilir.  Varsayılan olarak, bu öznitelik, paketin bir MSI tarafından yüklenmediğini belirten false değeridir.

- `SystemComponent` – Bu isteğe bağlı öznitelik, bu paketin bir sistem bileşeni olarak kabul edilip edilmeyeceğini belirtir. Sistem bileşenleri Uzantı Yöneticisi Kullanıcı arabiriminde gösterilmez ve güncelleştirilemez. Varsayılan olarak, bu öznitelik, paketin bir sistem bileşeni olmadığını belirten false değeridir.

- `AnyAttribute*` – `Installation` Öğesi, çalışma zamanında bir ad-değer çifti sözlüğü olarak sunulacak bir açık uçlu Öznitelikler kümesini kabul eder.

- `<InstallationTarget>` – Bu öğe, VSıX yükleyicisinin paketi yüklediği konumu denetler. `Scope`Özniteliğin değeri "ProductExtension" ise paketin, kendi içeriğinin bir parçası olarak bir bildirim dosyası yükleyen BIR SKU 'yu hedeflemesi gerekir. `<InstallationTarget>` `Scope` Özniteliği açık veya varsayılan "ProductExtension" değerine sahip olduğunda öğesi aşağıdaki özniteliklere sahiptir:

  - `Id` – Bu öznitelik, paketini tanımlar.  Öznitelik, ad alanı kuralına uyar: Company.Product.Feature.Name. `Id`Öznitelik yalnızca alfasayısal karakterler içerebilir ve 100 karakterle sınırlıdır. Beklenen değerler:

    - Microsoft. VisualStudio. ıntegratedshell

    - Microsoft.VisualStudio.Pro

    - Microsoft. VisualStudio. Premium

    - Microsoft. VisualStudio. Ultimate

    - Microsoft. VisualStudio. Ödexpress

    - Microsoft. VisualStudio. VPDExpress

    - Microsoft. VisualStudio. VSWinExpress

    - Microsoft. VisualStudio. VSLS

    - My. Shell. app

  - `Version` – Bu öznitelik, bu SKU 'nun en düşük ve en yüksek desteklenen sürümlerini içeren bir sürüm aralığı belirtir. Bir paket, desteklediği SKU 'ların sürümlerini ayrıntılandırır. Sürüm aralığı gösterimi [10,0 – 11,0], burada

    - [– en düşük sürüm dahil.

    - ] – en yüksek sürüm dahil.

    - (-en düşük sürüm dışlamalı.

    - ) – en yüksek sürüm dışlamalı.

    - Tek sürüm #-yalnızca belirtilen sürüm.

    > [!IMPORTANT]
    > VSıX şemasının sürüm 2,0 sürümü Visual Studio 2012 ' de tanıtılmıştı. Bu şemayı kullanmak için makinede Visual Studio 2012 veya sonraki bir sürümünün yüklü olması ve söz konusu ürünün parçası olan VSIXInstaller.exe kullanmanız gerekir. Visual Studio 'nun önceki sürümlerini Visual Studio 2012 veya sonraki bir Valtıyükleyicisi ile, ancak yalnızca yükleyicinin sonraki sürümlerini kullanarak hedefleyebilirsiniz.

  - `AnyAttribute*` – `<InstallationTarget>` Öğesi, çalışma zamanında bir ad-değer çifti sözlüğü olarak kullanıma sunulacak bir açık uçlu öznitelikler kümesine izin verir.

### <a name="dependencies-element"></a>Dependencies öğesi
 Bu öğe, bu paketin bildirdiği bağımlılıkların bir listesini içerir. Herhangi bir bağımlılık belirtilmişse, bu paketlerin (kendileri tarafından tanımlanan `Id` ) daha önce yüklenmiş olması gerekir.

- `<Dependency>` öğesi – bu alt öğe aşağıdaki özniteliklere sahiptir:

  - `Id` – Bu özniteliğin bağımlı paket için benzersiz bir KIMLIK olması gerekir. Bu kimlik değeri, `<Metadata><Identity>Id` Bu paketin bağımlı olduğu bir paketin özniteliğiyle eşleşmelidir. `Id`Öznitelik, ad alanı kuralına uyar: Company.Product.Feature.Name. Öznitelik yalnızca alfasayısal karakterler içerebilir ve 100 karakterle sınırlıdır.

  - `Version` – Bu öznitelik, bu SKU 'nun en düşük ve en yüksek desteklenen sürümlerini içeren bir sürüm aralığı belirtir. Bir paket, desteklediği SKU 'ların sürümlerini ayrıntılandırır. Sürüm aralığı gösterimi [12,0, 13,0], burada:

    - [– en düşük sürüm dahil.

    - ] – en yüksek sürüm dahil.

    - (-en düşük sürüm dışlamalı.

    - ) – en yüksek sürüm dışlamalı.

    - Tek sürüm #-yalnızca belirtilen sürüm.

  - `DisplayName` -Bu öznitelik, iletişim kutuları ve hata iletileri gibi kullanıcı arabirimi öğelerinde kullanılan bağımlı paketin görünen adıdır. Bağımlı paket MSI tarafından yüklenmediği takdirde öznitelik isteğe bağlıdır.

  - `Location` – Bu isteğe bağlı öznitelik, bu VSıX içindeki göreli yolu, iç içe geçmiş bir VSıX paketine ya da bağımlılık için indirme konumunun URL 'sini belirtir. Bu öznitelik, kullanıcının önkoşul paketini bulmasını sağlamak için kullanılır.

  - `AnyAttribute*` – `Dependency` Öğesi, çalışma zamanında bir ad-değer çifti sözlüğü olarak sunulacak bir açık uçlu Öznitelikler kümesini kabul eder.

### <a name="assets-element"></a>Varlıklar öğesi
 Bu öğe, `<Asset>` Bu paketin karşılaştığı her bir uzantı veya içerik öğesi için etiket listesi içerir.

- `<Asset>` -Bu öğe aşağıdaki öznitelikleri ve öğeleri içerir:

  - `Type` – Bu, uzantı veya bu öğe tarafından temsil edilen içerik türüdür. Her `<Asset>` öğenin tek bir olması gerekir `Type` , ancak birden çok `<Asset>` öğe aynı olabilir `Type` . Bu öznitelik, ad alanı kurallarına göre tam nitelikli bir ad olarak temsil edilmelidir. Bilinen türler şunlardır:

    1. Microsoft. VisualStudio. VsPackage

    2. Microsoft. VisualStudio. MefComponent

    3. Microsoft. VisualStudio. ToolboxControl

    4. Microsoft. VisualStudio. Samples

    5. Microsoft. VisualStudio. ProjectTemplate

    6. Microsoft. VisualStudio. ItemTemplate

    7. Microsoft. VisualStudio. Assembly

       Kendi türlerinizi oluşturabilir ve bunlara benzersiz adlar verebilirsiniz. Visual Studio içindeki çalışma zamanında, kodunuz Uzantı Yöneticisi API 'SI aracılığıyla bu özel türleri listeleyemez ve bunlara erişebilir.

  - Yol: varlığı içeren paket içindeki dosya veya klasörün göreli yolu.

  - `AnyAttribute*` – Çalışma zamanında bir ad-değer çifti sözlüğü olarak sunulacak bir açık uçlu öznitelikler kümesi.

     `<AnyElement>*` – Başlangıç ve bitiş etiketi arasında yapılandırılmış içeriğe izin verilir `<Asset>` . Tüm öğeler XmlElement nesnelerinin bir listesi olarak gösterilir. VSıX uzantıları, bildirim dosyasında yapılandırılmış türe özgü meta verileri tanımlayabilir ve çalışma zamanında bunları numaralandırır.

### <a name="sample-manifest"></a>Örnek bildirim

```
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

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
