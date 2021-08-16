---
title: Başvuru Eklerken NuGet veya Uzantı SDK Kullanma Karşılaştırması
description: Bir yazılım paketi olarak paketleme veya NuGet geliştirme seti olarak yazılım geliştirme seti olarak paketleme arasındaki farklar hakkında bilgi Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- multiple
ms.openlocfilehash: 446d8824d75f7728b766ca40783c51d6f5a394797181612c7e7e55807ce7894a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359108"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>NuGet başvurusu olarak SDK karşılaştırması

Bu makale, geliştiricilerin yazılımlarını bir NuGet paketi olarak mı yoksa yazılım geliştirme seti (SDK) olarak mı paketleyeceklerini seçmelerine yardımcı olmak için tasarlanmıştır. Özellikle, bir Visual Studio projesinde başvurıldıklarında ikisi arasındaki farklar ele Visual Studio ele atır.

- [NuGet,](/nuget) kitaplıkları bir projeye ekleme işlemini basitleştiren bir açık kaynak paket yönetim sistemidir. .NET için (.NET Core dahil), NuGet Microsoft tarafından desteklenen kod paylaşımı mekanizmasıdır. NuGet .NET paketlerinin nasıl oluşturulacak, barındırıldı ve tüketiliyor olduğunu tanımlar ve bu rollerin her biri için araçlar sağlar. Bu Visual Studio, NuGet arabirimini kullanarak projeye Paket Yöneticisi [paketleri](/nuget/consume-packages/install-use-packages-visual-studio) eklersiniz.

- [SDK,](../extensibility/creating-a-software-development-kit.md) tek bir başvuru öğesi olarak Visual Studio bir dosya koleksiyonudur. Visual Studio'daki Başvuru Yöneticisi iletişim kutusu, Başvuru Ekle'yi seçerseniz geçerli projeyle ilgili tüm SDK'leri **listeler.** Bir projeye SDK eklerken IntelliSense, Araç Kutusu penceresi, tasarımcılar, Nesne Tarayıcısı, MSBuild, dağıtım, hata ayıklama ve paketleme aracılığıyla bu SDK'nın tüm içeriğine erişebilirsiniz.

## <a name="which-mechanism-should-i-use"></a>Hangi mekanizmayı kullanacağız?

Aşağıdaki tablo, bir SDK'nın başvuru özelliklerini sdk'nın başvuran özellikleriyle karşılaştırmanıza yardımcı NuGet.

| Özellik | SDK Desteği | SDK Notları | NuGet Destek | NuGet Notlar |
| - | - | - |---------------| - |
| Mekanizma bir varlığa başvurur ve ardından tüm dosya ve işlevler kullanılabilir. | Y | Başvuru Yöneticisi iletişim kutusunu kullanarak bir SDK **eklersiniz** ve geliştirme iş akışı sırasında tüm dosyalar ve işlevler kullanılabilir. | Y | |
| MSBuild derlemeleri otomatik olarak kullanır ve meta Windows (*.winmd*) dosyalarını kullanır. | Y | SDK'daki başvurular otomatik olarak derleyiciye geçirilir. | Y | |
| MSBuild .h veya .lib dosyalarını otomatik olarak kullanır. | Y | *SDKName.props* dosyası, Visual Studio *.h* veya *.lib* dosyası tüketimi için Visual C++ dizininin nasıl ayarlandır vb. olduğunu söyler. | N | |
| MSBuild veya .css *.js* otomatik olarak *tüketir.* | Y | Bu **Çözüm Gezgini**, JavaScript SDK başvuru düğümünü genişleterek tek tek *.js* *veya .css* dosyalarını gösterebilir ve ardından bu dosyaları kaynak dosyalarına sürükleyerek etiketler `<source include/>` oluşturabilirsiniz. SDK, F5 ve otomatik paket kurulumunu destekler. | Y | |
| MSBuild araç kutusuna denetimi otomatik **olarak ekler.** | Y | Araç **Kutusu,** BELIRTTIĞINIZ sekmelerde SDK'ları tüketir ve denetimleri gösterebilir. | N | |
| Mekanizma, uzantılar Visual Studio Yükleyicisi (VSIX) desteği sağlar. | Y | VSIX'in SDK paketleri oluşturmak için özel bir bildirimi ve mantığı vardır | Y | VSIX başka bir kurulum programına katıştırabilirsiniz. |
| Object **Browser** başvuruları numaralandırıyor. | Y | Nesne **Tarayıcısı,** SDK'larda başvuru listesini otomatik olarak alır ve bunları numaralandıracaktır. | N | |
| Dosyalar ve bağlantılar Başvuru Yöneticisi iletişim kutusuna otomatik **olarak** eklenir (yardım bağlantıları vb. otomatik olarak doldurmak) | Y | Başvuru **Yöneticisi** iletişim kutusu, yardım bağlantıları ve SDK bağımlılıklarının listesiyle birlikte SDK'ları otomatik olarak numaralandıracaktır. | N | NuGet, Kendi NuGet **Paketlerini Yönet iletişim** kutusunu sağlar. |
| Mekanizma birden çok mimariyi destekler. | Y | SDK'ler birden çok yapılandırmayı gönderebilirsiniz. MSBuild her proje yapılandırması için uygun dosyaları kullanır. | N | |
| Mekanizma birden çok yapılandırmayı destekler. | Y | SDK'ler birden çok yapılandırmayı gönderebilirsiniz. Proje mimarisine bağlı olarak, MSBuild her proje mimarisi için uygun dosyaları kullanır. | N | |
| Mekanizma "kopyalanmay" ifadesini belirtebilir. | Y | Dosyaların *\redist* veya *\designtime* klasörüne bırakıldıklarına bağlı olarak, hangi dosyaların tüketen uygulamanın paketine kopyalanıp kopyalanmayacaklarını kontrol edin. | N | Paket bildiriminde kopyalayacak dosyaları bildirebilirsiniz. |
| İçerik yerelleştirilmiş dosyalarda görünür. | Y | DAHA iyi bir tasarım zamanı deneyimi için, SDK'larda yerelleştirilmiş XML belgeleri otomatik olarak eklenir. | N | |
| MSBuild SDK'nın birden çok sürümünü aynı anda tüketmek için destek sağlar. | Y | SDK, aynı anda birden çok sürümün tüket inging destekler. | N | Bu başvuru değil. Projenize aynı anda birden fazla NuGet dosya sürümüne sahip olayazabilirsiniz. |
| Bu mekanizma, geçerli hedef çerçeveleri, Visual Studio ve proje türlerini belirtmeyi destekler. | Y | Başvuru **Yöneticisi** iletişim kutusu ve **Araç** Kutusu yalnızca bir proje için geçerli olan SDK'ları gösterir, böylece kullanıcılar uygun SDK'ları daha kolay seçebilir. | Y (kısmi) | Özet, Hedef Çerçeve'dir. Kullanıcı arabiriminde filtreleme yoktur. Yükleme zamanında bir hata döndürür. |
| Mekanizma, yerel WinMD'ler için kayıt bilgilerini belirtmeyi destekler. | Y | .winmd dosyası ile dosya arasındaki bağıntıyı .dll için *SDKManifest.xml.* | N | |
| Mekanizma, diğer SDK'lara bağımlılık belirtmeyi destekler. | Y | SDK yalnızca kullanıcıya bilgi sağlar; kullanıcı yine de bunları yüklemeli ve el ile başvurmalısınız. | Y | NuGet otomatik olarak çeker; kullanıcıya bildirlanmaz. |
| Mekanizma, uygulama bildirimi  [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] ve Çerçeve Kimliği gibi kavramlarla tümleştirilmiştir. | Y | PAKETLEME ve F5'in içinde kullanılabilen SDK'larla doğru şekilde çalışması için SDK'nın'a özgü [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] kavramları geçmesi [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] gerekir. | N | |
| Mekanizma, uygulamalar için uygulama hata ayıklama işlem hattıyla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] tümleştirilmiştir. | Y | SDK [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 'nın, paketlenmesi ve F5 'in ' de bulunan SDK 'lar ile düzgün çalışması için özel kavramlara sahip olması gerekir [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] . | Y | NuGet içerik projenin bir parçası haline gelir. Özel bir F5 değerlendirmesi gerekmez. |
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
