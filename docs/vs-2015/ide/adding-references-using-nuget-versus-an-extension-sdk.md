---
title: Bir uzantı SDK 'sına karşı NuGet kullanarak başvurular ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages.nuget_package_manager.general
- vs.toolsoptionspages.nuget_package_manager.package_sources
ms.assetid: 2175581e-83cb-444c-bb52-cc1fca8ea196
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95927385ce3218d73ba6b94819429163178bb65b
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917343"
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Başvuru Eklerken NuGet veya Uzantı SDK Kullanma Karşılaştırması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio için NuGet uzantısını veya bir yazılım geliştirme seti 'ni (SDK) kullanarak Visual Studio projeleri içinde tüketim için bir paket sağlayabilirsiniz. Bu konu, iki mekanizma arasındaki benzerlikleri ve farkları açıklayarak, göreviniz için en iyi olanı seçmenize yardımcı olabilir.

- NuGet, kitaplıkları bir proje çözümüne ekleme sürecini kolaylaştıran açık kaynaklı bir paket yönetimi sistemidir. Daha fazla bilgi için bkz. [NuGet genel bakış](/nuget/what-is-nuget).

- SDK, Visual Studio 'Nun tek bir başvuru öğesi olarak davrandığı bir dosya koleksiyonudur. **Başvuru Yöneticisi** iletişim kutusu, bu iletişim kutusunu görüntülediğinizde açık olan projeyle Ilgili tüm SDK 'ları listeler. Bir projeye SDK eklediğinizde, bu SDK 'nın tüm içeriğine IntelliSense, **araç kutusu**, tasarımcılar, **nesne tarayıcısı**, MSBuild, dağıtım, hata ayıklama ve paketleme aracılığıyla erişebilirsiniz. SDK 'lar hakkında daha fazla bilgi için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md).

## <a name="which-mechanism-should-i-use"></a>Hangi mekanizmayı kullanmalıyım?
 Aşağıdaki tablo, bir SDK 'nın başvuru özelliklerini NuGet 'in başvuru özellikleriyle karşılaştırmanıza yardımcı olur.

|Özellik|SDK Desteği|SDK notları|NuGet desteği|NuGet notları|
|-------------|-----------------|---------------|-------------------|-----------------|
|Mekanizma bir varlığa başvurur ve tüm dosya ve işlevler kullanılabilir.|Y|**Başvuru Yöneticisi** iletişim kutusunu kullanarak bir SDK eklersiniz ve geliştirme iş akışı sırasında tüm dosya ve işlevler kullanılabilir.|Y||
|MSBuild derlemeleri ve Windows meta veri (. winmd) dosyalarını otomatik olarak tüketir.|Y|SDK 'daki başvurular otomatik olarak derleyiciye geçirilir.|Y||
|MSBuild,. h veya. lib dosyalarını otomatik olarak kullanır.|Y|*SDKName*. props dosyası, Visual Studio 'nun Visual C++ Directory 'yi nasıl ayarlayacağını ve bu nedenle otomatik. h veya. lib dosya tüketimi için nasıl yapılacağını söyler.|N||
|MSBuild otomatik olarak. js veya. CSS dosyalarını kullanır.|Y|**Çözüm Gezgini**, JavaScript SDK başvuru düğümünü genişleterek tek bir. js veya. css dosyasını gösterebilir ve sonra bu dosyaları kaynak dosyalarına sürükleyerek `<source include/>` etiketleri oluşturabilirsiniz. SDK, F5 ve otomatik paket kurulumunu destekler.|Y||
|MSBuild, denetimi **araç kutusuna**otomatik olarak ekler.|Y|**Araç kutusu** SDK 'ları kullanabilir ve belirlediğiniz sekmelerde denetimleri gösterebilir.|N||
|Mekanizması, uzantılar (VSıX) için Visual Studio Yükleyicisi destekler.|Y|VSıX SDK paketleri oluşturmak için özel bir bildirime ve mantığa sahiptir|Y|VSıX başka bir kurulum programına katıştırılabilir.|
|**Nesne tarayıcısı** , başvuruları numaralandırır.|Y|**Nesne tarayıcısı** SDK 'larda başvuruların listesini otomatik olarak alır ve sıralar.|N||
|Dosyalar ve bağlantılar otomatik olarak **başvuru Yöneticisi** iletişim kutusuna eklenir (Yardım bağlantıları, vb. otomatik doldurma)|Y|**Başvuru Yöneticisi** iletişim kutusu, yardım BAĞLANTıLARı ve SDK bağımlılıklarının listesi Ile birlikte SDK 'ları otomatik olarak numaralandırır.|N|NuGet kendi **NuGet Paketlerini Yönet** iletişim kutusunu sağlar.|
|Mekanizması birden çok mimariyi destekler.|Y|SDK 'lar birden çok yapılandırma gönderebilir. MSBuild her proje yapılandırması için uygun dosyaları kullanır.|N||
|Mekanizması birden çok yapılandırmayı destekler.|Y|SDK 'lar birden çok yapılandırma gönderebilir. MSBuild, proje mimarisine bağlı olarak her proje mimarisi için uygun dosyaları kullanır.|N||
|Mekanizma "kopyalama için değil" belirtebilir.|Y|Dosyaların \redist veya \designtime klasöründe bırakıldığına bağlı olarak, hangi dosyaların tüketen uygulamanın paketine kopyalanacağını denetleyebilirsiniz.|N|Paket bildiriminde kopyalanacak dosyaları bildirirsiniz.|
|Yerelleştirilmiş dosyalarda içerik görüntülenir.|Y|SDK 'larda yerelleştirilmiş XML belgeleri, daha iyi bir tasarım zamanı deneyimi için otomatik olarak eklenir.|N||
|MSBuild aynı anda bir SDK 'nın birden çok sürümünü kullanmayı destekler.|Y|SDK birden çok sürümü aynı anda kullanmayı destekler.|N|Bu başvuru değildir. Projenizde aynı anda birden fazla NuGet dosyası sürümü olamaz.|
|Mekanizması, geçerli hedef çerçeveleri, Visual Studio sürümlerini ve proje türlerini belirtmeyi destekler.|Y|**Başvuru Yöneticisi** iletişim kutusu ve **araç kutusu** yalnızca bir projeye uygulanan SDK 'ları gösterir, böylece kullanıcılar uygun SDK 'ları daha kolay seçebilirler.|Y (kısmi)|Özet, hedef çerçevedir. Kullanıcı arabiriminde filtreleme yok. Yükleme sırasında bir hata döndürebilir.|
|Mekanizması yerel Wınmds için kayıt bilgilerini belirtmeyi destekler.|Y|SDKManifest. xml dosyasındaki. winmd dosyası ve. dll dosyası arasında bağıntı belirtebilirsiniz.|N||
|Mekanizması diğer SDK 'larda bağımlılıkları belirtmeyi destekler.|Y|SDK yalnızca kullanıcıya bildirir; Kullanıcı yine de onları yükleyip el ile başvurmalıdır.|Y|NuGet bunları otomatik olarak çeker; Kullanıcı bilgilendirilmez.|
|Mekanizması, uygulama bildirimi ve çerçeve KIMLIĞI gibi [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] kavramlarla tümleştirilir.|Y|SDK, paketleme ve F5 'in[!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)]kullanılabilir SDK 'lar ile düzgün çalışması için [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)] özgü kavramları iletmelidir.|N||
|Mekanizması [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar için uygulama hata ayıklama işlem hattı ile tümleşir.|Y|SDK ve F5 'in [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)]kullanılabilir SDK 'lar ile düzgün çalışması için SDK 'ya [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)]özgü kavramlar geçirmesi gerekir.|Y|NuGet içeriği projenin bir parçası haline gelir. Özel bir F5 değerlendirmesi gerekmez.|
|Mekanizması uygulama bildirimleri ile tümleşir.|Y|SDK ve F5 'in [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)]kullanılabilir SDK 'lar ile düzgün çalışması için SDK 'ya [!INCLUDE[win8_appstore_short](../includes/win8-appstore-short-md.md)]özgü kavramlar geçirmesi gerekir.|Y|NuGet içeriği projenin bir parçası haline gelir. Özel bir F5 değerlendirmesi gerekmez.|
|Mekanizma, başvuru olmayan dosyaları dağıtır (örneğin, [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Apps testlerinin çalıştırılacağı test çerçevesini dağıtın).|Y|Dosyaları \redist klasörüne bırakırsanız, dosyalar otomatik olarak dağıtılır.|Y||
|Mekanizması, Platform SDK 'larını otomatik olarak Visual Studio IDE 'ye ekler.|Y|[!INCLUDE[win8](../includes/win8-md.md)] SDK veya Windows Phone SDK 'sını belirli bir düzen ile belirli bir konuma bırakırsanız, SDK otomatik olarak tüm Visual Studio özellikleriyle tümleştirilir.|N||
|Mekanizması temiz bir geliştirici makinesini destekler. (Yani, yükleme gerekmez ve kaynak kod denetiminden basit alma işlemi çalışacaktır.)|N|Bir SDK 'ya başvursanız, çözümünüzü ve SDK 'yı ayrı ayrı iade etmeniz gerekir. SDK 'Yı, MSBuild 'in SDK 'Sı yineleme (Ayrıntılar için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md)) varsayılan konumlarından farklı konumlardan iade edebilirsiniz. Alternatif olarak, özel bir konum SDK 'Lardan oluşuyorsa, proje dosyasında aşağıdaki kodu belirtebilirsiniz:<br /><br /> `<PropertyGroup>    <SDKReferenceDirectoryRoot>C:\MySDKs</SDKReferenceDirectoryRoot>   </PropertyGroup>`<br /><br /> Daha sonra bu konuma SDK 'Ları kontrol edin.|Y|Çözümü kullanıma alabilirsiniz ve Visual Studio dosyaları hemen tanır ve üzerinde davranır.|
|Paket yazarlarının büyük bir topluluğuna katabilirsiniz.|YOK|Topluluk yenidir.|Y||
|Paket tüketicilerinin büyük bir topluluğunu birleştirebilirsiniz.|YOK|Topluluk yenidir.|Y||
|İş ortaklarının bir ekosistemine (özel galeriler, depolar vb.) katabilirsiniz.|YOK|Kullanılabilir depolar, Visual Studio Galerisi, Microsoft Indirme merkezi ve [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]içerir.|Y||
|Mekanizması, paket oluşturma ve tüketim için sürekli tümleştirme yapı sunucularıyla tümleştirilir.|Y|SDK, komut satırındaki iade edilme konumunu (SDKReferenceDirectoryRoot özelliği) MSBuild 'e iletmelidir.|Y||
|Mekanizması hem kararlı hem de yayın öncesi paket sürümlerini destekler.|Y|SDK, birden çok sürüme başvuru eklemeyi destekler.|Y||
|Mekanizması yüklü paketler için otomatik güncelleştirmeyi destekler.|Y|VSıX olarak veya Visual Studio otomatik güncelleştirme 'nin bir parçası olarak gönderilmemişse, SDK otomatik bildirimler sağlar.|Y||
|Mekanizması, paket oluşturmak ve kullanmak için tek başına bir. exe dosyası içerir.|Y|SDK, MSBuild. exe ' yi içerir.|Y||
|Paketler sürüm denetimine iade edilebilir.|Y|Belge düğümü dışında bir şey iade edemeyebilirsiniz, bu da Uzantı SDK 'larının iade yapılmadığı anlamına gelir. Uzantı SDK 'sının boyutu büyük olabilir.|Y||
|Paketleri oluşturmak ve kullanmak için bir PowerShell arabirimi kullanabilirsiniz.|Y (tüketim), N (oluşturma)|SDK oluşturmak için araç yok. Tüketim, komut satırında MSBuild 'i yürütüyor.|Y||
|Hata ayıklama desteği için bir sembol paketi kullanabilirsiniz.|Y|. Pdb dosyalarını SDK 'ya düşürürsanız dosyalar otomatik olarak alınır.|Y||
|Mekanizması, Paket Yöneticisi otomatik güncelleştirmelerini destekler.|YOK|SDK, MSBuild ile düzeltilir.|Y||
|Mekanizması bir hafif bildirim biçimini destekler.|Y|SDKManifest. xml pek çok özniteliği destekler, ancak küçük bir alt küme genellikle gereklidir.|Y||
|Mekanizmaya tüm Visual Studio sürümlerinde ulaşılabilir.|Y|SDK, Visual Studio Express ile [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]arasında tüm Visual Studio sürümlerini destekler.|Y|NuGet, tüm Visual Studio sürümlerini destekler, [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]ile hızlı bir şekilde ilerleyin.|
|Mekanizma tüm proje türleri için kullanılabilir.|N|SDK, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]başlayan [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları destekler.|N|İzin verilen projelerin bir listesini gözden geçirebilirsiniz.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
