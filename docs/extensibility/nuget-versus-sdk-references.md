---
title: Başvuru Eklerken NuGet veya Uzantı SDK Kullanma Karşılaştırması
description: bir Visual Studio projesinde başvuruluyorsa paketleme yazılımı NuGet paketi veya yazılım geliştirme seti olarak arasındaki farklar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- multiple
ms.openlocfilehash: 2ca8b3f2e7d0b75d0461a905832263635db5708f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158560"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>proje başvurusu olarak SDK ile NuGet karşılaştırması

bu makale, geliştiricilerin yazılımlarını bir NuGet paketi olarak veya yazılım geliştirme seti (SDK) olarak paketleyip paketedilmeyeceğini seçmesini sağlamak üzere tasarlanmıştır. özellikle, Visual Studio bir projede başvurulduklarında ikisi arasındaki farkları ele alır.

- [NuGet](/nuget) , kitaplıkları bir projeye ekleme sürecini kolaylaştıran açık kaynaklı bir paket yönetimi sistemidir. .net için (.net Core dahil), NuGet kodu paylaşmak için Microsoft tarafından desteklenen bir mekanizmadır. NuGet .net paketlerinin nasıl oluşturulduğunu, barındırıldığını ve kullanıldığını tanımlar ve bu rollerin her biri için araçlar sağlar. Visual Studio, [Paket Yöneticisi](/nuget/consume-packages/install-use-packages-visual-studio) kullanıcı arabirimini kullanarak bir projeye NuGet paketler eklersiniz.

- [SDK](../extensibility/creating-a-software-development-kit.md) , Visual Studio tek bir başvuru öğesi olarak ele alan bir dosya koleksiyonudur. Visual Studio başvuru yöneticisi iletişim kutusu, **başvuru ekle**' yi seçtiğinizde geçerli projeyle ilgili tüm sdk 'ları listeler. bir projeye sdk eklediğinizde, bu sdk 'nın tüm içeriğine ıntellisense, araç kutusu penceresi, tasarımcılar, Nesne Tarayıcısı, MSBuild, dağıtım, hata ayıklama ve paketleme aracılığıyla erişebilirsiniz.

## <a name="which-mechanism-should-i-use"></a>Hangi mekanizmayı kullanmalıyım?

Aşağıdaki tablo, bir SDK 'nın başvuru özelliklerini NuGet başvuru özellikleriyle karşılaştırmanıza yardımcı olur.

| Özellik | SDK desteği | SDK notları | NuGet Support | NuGet Larını |
| - | - | - |---------------| - |
| Mekanizma bir varlığa başvurur ve tüm dosya ve işlevler kullanılabilir. | Y | **Başvuru Yöneticisi** iletişim kutusunu kullanarak bir SDK eklersiniz ve geliştirme iş akışı sırasında tüm dosya ve işlevler kullanılabilir. | Y | |
| MSBuild derlemeleri ve Windows meta veri (*. winmd*) dosyalarını otomatik olarak tüketir. | Y | SDK 'daki başvurular otomatik olarak derleyiciye geçirilir. | Y | |
| MSBuild,. h veya. lib dosyalarını otomatik olarak kullanır. | Y | *sdkname. props* dosyası, otomatik *. h* veya *. lib* dosya tüketimi için Visual C++ dizinini nasıl ayarlayacağınızı Visual Studio söyler. | N | |
| MSBuild, *.js* veya *. css* dosyalarını otomatik olarak kullanır. | Y | **Çözüm Gezgini**, JavaScript SDK başvuru düğümünü genişleterek tek tek *.js* veya *. css* dosyalarını gösterebilir ve sonra `<source include/>` Bu dosyaları kaynak dosyalarına sürükleyerek Etiketler oluşturabilirsiniz. SDK, F5 ve otomatik paket kurulumunu destekler. | Y | |
| MSBuild **araç kutusuna** otomatik olarak denetim ekler. | Y | **Araç kutusu** SDK 'ları kullanabilir ve belirlediğiniz sekmelerde denetimleri gösterebilir. | N | |
| mekanizması, uzantılar (vsıx) için Visual Studio Yükleyicisi destekler. | Y | VSıX SDK paketleri oluşturmak için özel bir bildirime ve mantığa sahiptir | Y | VSıX başka bir kurulum programına katıştırılabilir. |
| **Nesne tarayıcısı** , başvuruları numaralandırır. | Y | **Nesne tarayıcısı** SDK 'larda başvuruların listesini otomatik olarak alır ve sıralar. | N | |
| Dosyalar ve bağlantılar otomatik olarak **başvuru Yöneticisi** iletişim kutusuna eklenir (Yardım bağlantıları, vb. otomatik doldurma) | Y | **Başvuru Yöneticisi** iletişim kutusu, yardım BAĞLANTıLARı ve SDK bağımlılıklarının listesi Ile birlikte SDK 'ları otomatik olarak numaralandırır. | N | NuGet kendi **NuGet paketlerini yönet** iletişim kutusunu sağlar. |
| Mekanizması birden çok mimariyi destekler. | Y | SDK 'lar birden çok yapılandırma gönderebilir. MSBuild her proje yapılandırması için uygun dosyaları tüketir. | N | |
| Mekanizması birden çok yapılandırmayı destekler. | Y | SDK 'lar birden çok yapılandırma gönderebilir. proje mimarisine bağlı olarak, MSBuild her proje mimarisi için uygun dosyaları tüketir. | N | |
| Mekanizma "kopyalama için değil" belirtebilir. | Y | Dosyaların *\redist* veya *\designtime* klasöründe bırakıldığına bağlı olarak, hangi dosyaların tüketen uygulamanın paketine kopyalanacağını denetleyebilirsiniz. | N | Paket bildiriminde kopyalanacak dosyaları bildirirsiniz. |
| Yerelleştirilmiş dosyalarda içerik görüntülenir. | Y | SDK 'larda yerelleştirilmiş XML belgeleri, daha iyi bir tasarım zamanı deneyimi için otomatik olarak eklenir. | N | |
| MSBuild, bir SDK 'nın birden çok sürümünü aynı anda kullanmayı destekler. | Y | SDK birden çok sürümü aynı anda kullanmayı destekler. | N | Bu başvuru değildir. projenizde aynı anda birden fazla NuGet dosyası sürümü olamaz. |
| mekanizması, uygulanabilir hedef çerçeveleri, Visual Studio sürümlerini ve proje türlerini belirtmeyi destekler. | Y | **Başvuru Yöneticisi** iletişim kutusu ve **araç kutusu** yalnızca bir projeye uygulanan SDK 'ları gösterir, böylece kullanıcılar uygun SDK 'ları daha kolay seçebilirler. | Y (kısmi) | Özet, hedef çerçevedir. Kullanıcı arabiriminde filtreleme yok. Yükleme sırasında bir hata döndürebilir. |
| Mekanizması yerel Wınmds için kayıt bilgilerini belirtmeyi destekler. | Y | . Winmd dosyası ile *SDKManifest.xml*.dll dosyası arasında bağıntı belirtebilirsiniz. | N | |
| Mekanizması diğer SDK 'larda bağımlılıkları belirtmeyi destekler. | Y | SDK yalnızca kullanıcıya bildirir; Kullanıcı yine de onları yükleyip el ile başvurmalıdır. | Y | NuGet onları otomatik olarak çeker; Kullanıcı bilgilendirilmez. |
| Mekanizması,  [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] uygulama bildirimi ve çerçeve kimliği gibi kavramlarla tümleştirilir. | Y | SDK, [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] paketleme ve F5 ' de bulunan SDK 'lar ile doğru şekilde çalışması için öğesine özgü kavramları iletmelidir [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] . | N | |
| Mekanizması, uygulamalar için uygulama hata ayıklama işlem hattı ile tümleşir [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] . | Y | SDK [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 'nın, paketlenmesi ve F5 'in ' de bulunan SDK 'lar ile düzgün çalışması için özel kavramlara sahip olması gerekir [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] . | Y | NuGet içerik projenin bir parçası haline gelir. Özel bir F5 değerlendirmesi gerekmez. |
| Mekanizması uygulama bildirimleri ile tümleşir. | Y | SDK [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 'nın, paketlenmesi ve F5 'in ' de bulunan SDK 'lar ile düzgün çalışması için özel kavramlara sahip olması gerekir [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] . | Y | NuGet içerik projenin bir parçası haline gelir. Özel bir F5 değerlendirmesi gerekmez. |
| Mekanizma, başvuru olmayan dosyaları dağıtır (örneğin, uygulama testlerinin çalıştırılacağı test çerçevesini dağıtın [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] ). | Y | Dosyaları *\redist* klasörüne bırakırsanız, dosyalar otomatik olarak dağıtılır. | Y | |
| mekanizması Visual Studio ıde 'ye platform sdk 'larını otomatik olarak ekler. | Y | [!INCLUDE[win8](../debugger/includes/win8_md.md)]sdk 'yı veya Windows Phone sdk 'sını belirli bir düzen ile belirli bir konuma bırakırsanız, sdk otomatik olarak tüm Visual Studio özellikleriyle tümleştirilir. | N | |
| Mekanizması temiz bir geliştirici makinesini destekler. (Yani, yükleme gerekmez ve kaynak kod denetiminden basit alma işlemi çalışacaktır.) | N | Bir SDK 'ya başvursanız, çözümünüzü ve SDK 'yı ayrı ayrı iade etmeniz gerekir. sdk 'yı, MSBuild sdk 'ları yineleyen iki kayıt defteri olmayan varsayılan konumdan iade edebilirsiniz (ayrıntılar için bkz. [yazılım geliştirme seti oluşturma](../extensibility/creating-a-software-development-kit.md)). Alternatif olarak, özel bir konum SDK 'Lardan oluşuyorsa, proje dosyasında aşağıdaki kodu belirtebilirsiniz:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> Daha sonra bu konuma SDK 'Ları kontrol edin. | Y | çözümü kullanıma alabilir ve dosyaları hemen tanır ve üzerinde davranır Visual Studio. |
| Paket yazarlarının büyük bir topluluğuna katabilirsiniz. | Yok | Topluluk yenidir. | Y | |
| Paket tüketicilerinin büyük bir topluluğunu birleştirebilirsiniz. | Yok | Topluluk yenidir. | Y | |
| İş ortaklarının bir ekosistemine (özel galeriler, depolar vb.) katabilirsiniz. | Yok | kullanılabilir depolar, Visual Studio market, Microsoft indirme merkezi ve ' yi içerir [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] . | Y | |
| Mekanizması, paket oluşturma ve tüketim için sürekli tümleştirme yapı sunucularıyla tümleştirilir. | Y | SDK, MSBuild için komut satırındaki iade edilme konumunu (SDKReferenceDirectoryRoot özelliği) iletmelidir. | Y | |
| Mekanizması hem kararlı hem de yayın öncesi paket sürümlerini destekler. | Y | SDK, birden çok sürüme başvuru eklemeyi destekler. | Y | |
| Mekanizması yüklü paketler için otomatik güncelleştirmeyi destekler. | Y | vsıx olarak veya Visual Studio otomatik güncelleştirmeler 'in bir parçası olarak sevk edildiğinde, SDK otomatik bildirimler sağlar. | Y | |
| Mekanizması, paket oluşturmak ve kullanmak için tek başına bir *.exe* dosyası içerir. | Y | SDK *MSBuild.exe* içerir. | Y | |
| Paketler sürüm denetimine iade edilebilir. | Y | Belge düğümü dışında bir şey iade edemeyebilirsiniz, bu da Uzantı SDK 'larının iade yapılmadığı anlamına gelir. Uzantı SDK 'sının boyutu büyük olabilir. | Y | |
| Paketleri oluşturmak ve kullanmak için bir PowerShell arabirimi kullanabilirsiniz. | Y (tüketim), N (oluşturma) | SDK oluşturmak için araç yok. tüketim, komut satırında MSBuild yürütüyor. | Y | |
| Hata ayıklama desteği için bir sembol paketi kullanabilirsiniz. | Y | *. Pdb* dosyalarını SDK 'ya düşürürsanız dosyalar otomatik olarak alınır. | Y | |
| Mekanizması, Paket Yöneticisi otomatik güncelleştirmelerini destekler. | Yok | SDK MSBuild ile düzeltilir. | Y | |
| Mekanizması bir hafif bildirim biçimini destekler. | Y | *SDKManifest.xml* birçok özniteliği destekler, ancak küçük bir alt küme genellikle gereklidir. | Y | |
| mekanizma tüm Visual Studio sürümlerinde kullanılabilir. | Y | SDK tüm Visual Studio sürümlerini destekler. | Y | NuGet tüm Visual Studio sürümlerini destekler. |

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
- [projedeki başvuruları yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-references-in-a-project)
