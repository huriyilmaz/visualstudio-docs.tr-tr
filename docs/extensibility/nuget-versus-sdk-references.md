---
title: Başvuru Eklerken NuGet veya Uzantı SDK Kullanma Karşılaştırması
ms.date: 08/02/2019
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad7fc9132647988aee46a2bb07e992505109d33c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702426"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>Proje referansı olarak NuGet ve SDK

Bu makale, geliştiricilerin yazılımlarını NuGet paketi olarak mı yoksa yazılım geliştirme kiti (SDK) olarak mı paketlemeyi seçmelerine yardımcı olmak için tasarlanmıştır. Özellikle, bir Visual Studio projesinde başvurulan ikisi arasındaki farkları tartışır.

- [NuGet,](/nuget) kitaplıkları bir projeye dahil etme işlemini kolaylaştıran açık kaynak kodlu bir paket yönetim sistemidir. .NET (.NET Core dahil) için NuGet, kodu paylaşmak için Microsoft tarafından desteklenen mekanizmadır. NuGet, .NET paketlerinin nasıl oluşturulduğunu, barındırıldığını ve tüketilmesini tanımlar ve bu rollerin her biri için araçları sağlar. Visual Studio'da [Paket Yöneticisi](/nuget/consume-packages/install-use-packages-visual-studio) kullanıcı arabirimini kullanarak projeye NuGet paketleri eklersiniz.

- [SDK,](../extensibility/creating-a-software-development-kit.md) Visual Studio'nun tek bir başvuru öğesi olarak ele aldığı dosyalar topluluğudur. Visual Studio'daki Başvuru Yöneticisi iletişim kutusu, **Başvuru Ekle'yi**seçtiğinizde geçerli projeyle alakalı tüm SDK'ları listeler. Bir projeye Bir SDK eklediğinizde, bu SDK'nın tüm içeriğine IntelliSense, Toolbox penceresi, tasarımcılar, Object Browser, MSBuild, dağıtım, hata ayıklama ve paketleme aracılığıyla erişebilirsiniz.

## <a name="which-mechanism-should-i-use"></a>Hangi mekanizmayı kullanmalıyım?

Aşağıdaki tablo, Bir SDK'nın başvuru özelliklerini NuGet'in referans özellikleriyle karşılaştırmanıza yardımcı olur.

| Özellik | SDK Desteği | SDK Notları | NuGet Desteği | NuGet Notlar |
| - | - | - |---------------| - |
| Mekanizma bir varlık başvurur ve sonra tüm dosyaları ve işlevselliği kullanılabilir. | E | **Başvuru Yöneticisi** iletişim kutusunu kullanarak bir SDK eklersiniz ve geliştirme iş akışı sırasında tüm dosyalar ve işlevler kullanılabilir. | E | |
| MSBuild derlemeleri ve Windows meta verilerini (*.winmd*) dosyalarını otomatik olarak tüketir. | E | SDK'daki başvurular otomatik olarak derleyiciye iletilir. | E | |
| MSBuild otomatik olarak .h veya .lib dosyalarını tüketir. | E | *SDKName.props* dosyası Visual Studio'ya visual C++ dizininin nasıl ayarlanıştını ve benzeri, otomatik *.h* veya *.lib* dosya tüketimi için nasıl ayarlanınan söyler. | N | |
| MSBuild otomatik olarak *.js* veya *.css* dosyalarını tüketir. | E | **Solution Explorer'da,** JavaScript SDK başvuru düğümünü tek tek *.js* veya *.css* dosyalarını göstermek için genişletebilir ve ardından bu dosyaları kaynak dosyalarına sürükleyerek etiketler oluşturabilirsiniz. `<source include/>` SDK F5 ve otomatik paket kurulum destekler. | E | |
| MSBuild otomatik olarak **Toolbox'a**denetim ekler. | E | **Araç Kutusu** SDK'lar tüketebilir ve belirttiğiniz sekmelerde denetimleri gösterebilir. | N | |
| Mekanizma uzantıları (VSIX) için Visual Studio Installer destekler. | E | VSIX SDK paketleri oluşturmak için özel bir manifesto ve mantık vardır | E | VSIX başka bir kurulum programına katıştırılabilir. |
| **Nesne Tarayıcısı** başvuruları sayısallandırır. | E | **Nesne Tarayıcısı,** SDK'larda başvuru listesini otomatik olarak alır ve bunlara sayısal verir. | N | |
| Dosyalar ve bağlantılar otomatik olarak **Başvuru Yöneticisi** iletişim kutusuna eklenir (yardım bağlantıları ve benzeri otomatik doldurma) | E | **Başvuru Yöneticisi** iletişim kutusu, yardım bağlantıları ve SDK bağımlılıkları listesiyle birlikte SDK'ları otomatik olarak sıralar. | N | NuGet kendi **NuGet Paketlerini Yönet** iletişim kutusunu sağlar. |
| Mekanizma birden çok mimariyi destekler. | E | SDK'lar birden çok yapılandırma yı ekleyebilir. MSBuild, her proje yapılandırması için uygun dosyaları tüketir. | N | |
| Mekanizma birden çok yapılandırmayı destekler. | E | SDK'lar birden çok yapılandırma yı ekleyebilir. Proje mimarisine bağlı olarak, MSBuild her proje mimarisi için uygun dosyaları kullanır. | N | |
| Mekanizma "kopyalamamak" olarak belirtebilir. | E | *\redist* veya *\designtime* klasörüne dosyaların bırakılıp bırakılmadığına bağlı olarak, hangi dosyaların tüketen uygulamanın paketine kopyalanamayacağını denetleyebilirsiniz. | N | Paket bildiriminde hangi dosyaların kopyalanıp kopyalanıp kopyalanıp kaydedilen dosyalar olduğunu beyan eylesiniz. |
| İçerik yereldosyalarda görünür. | E | SDK'larda yerelleştirilmiş XML belgeleri, daha iyi bir tasarım zamanı deneyimi için otomatik olarak dahil edilir. | N | |
| MSBuild, bir SDK'nın birden çok versiyonunu aynı anda tüketen leri destekler. | E | SDK aynı anda birden çok sürümü tüketen destekler. | N | Bu bir atıfta bulunmak değil. Aynı anda projenizde Birden fazla NuGet dosyası sürümü olamaz. |
| Mekanizma, geçerli hedef çerçevelerin, Visual Studio sürümlerinin ve proje türlerinin belirtilmesine destek sağlar. | E | **Başvuru Yöneticisi** iletişim kutusu ve **Araç Kutusu,** kullanıcıların uygun SDK'ları daha kolay seçebilmeleri için yalnızca projeye uygulanan SDK'ları gösterir. | Y (kısmi) | Pivot Hedef Çerçevesi'dir. Kullanıcı arabiriminde filtreleme yoktur. Yükleme zamanında bir hata döndürebilir. |
| Mekanizma, yerel WinMD'ler için kayıt bilgilerinin belirtilmesine destek olur. | E | *SDKManifest.xml'de*.winmd dosyası ile .dll dosyası arasındaki ilişkiyi belirtebilirsiniz. | N | |
| Mekanizma, diğer SDK'lara bağımlılıkları belirtmeyi destekler. | E | SDK sadece kullanıcıya not eder; kullanıcı hala bunları yüklemek ve el ile başvuru gerekir. | E | NuGet bunları otomatik olarak çeker; kullanıcıya bildirilmez. |
| Mekanizma, uygulama [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] bildirimi ve Framework ID gibi kavramlarla bütünleşir. | E | SDK, ambalaj ve F5'in sdk'larda bulunan SDK'larla doğru çalışması [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] için[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]özel olan kavramları geçmelidir. | N | |
| Mekanizma, uygulamalar için [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] uygulama hata ayıklama ardışık hattıyla bütünleşir. | E | SDK, ambalaj [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]ve F5'in sdk'larda bulunan SDK'larla [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]doğru çalışması için özel kavramları geçmelidir. | E | NuGet içeriği projenin bir parçası haline gelir. Özel bir F5 dikkate gereklidir. |
| Mekanizma uygulama bildirimleriyle bütünleşir. | E | SDK, ambalaj [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]ve F5'in sdk'larda bulunan SDK'larla [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]doğru çalışması için özel kavramları geçmelidir. | E | NuGet içeriği projenin bir parçası haline gelir. Özel bir F5 dikkate gereklidir. |
| Mekanizma, başvuru dışı dosyaları dağıtur (örneğin, uygulamaların testlerini [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] çalıştırmak için test çerçevesini dağıtın). | E | Dosyaları *\redist* klasörüne bırakırsanız, dosyalar otomatik olarak dağıtılır. | E | |
| Mekanizma otomatik olarak Visual Studio IDE platformu SDK'lar ekler. | E | SDK'yı [!INCLUDE[win8](../debugger/includes/win8_md.md)] veya Windows Phone SDK'yı belirli bir düzene sahip belirli bir konuma bırakırsanız, SDK tüm Visual Studio özellikleriyle otomatik olarak tümleştirilir. | N | |
| Mekanizma temiz bir geliştirici makinesini destekler. (Yani, hiçbir yükleme gereklidir ve kaynak kodu denetiminden basit alma çalışacaktır.) | N | Bir SDK'ya başvuruyorsanız, çözümünüzü ve SDK'yı ayrı ayrı iade etmelisiniz. MsBuild'in SDK'ları itelediği iki kayıt defteri olmayan varsayılan konumdan SDK'yı iade edebilirsiniz (ayrıntılar için bkz. [Yazılım Geliştirme Kiti Oluşturma).](../extensibility/creating-a-software-development-kit.md) Alternatif olarak, özel bir konum SDK'lardan oluşuyorsa, proje dosyasında aşağıdaki kodu belirtebilirsiniz:<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> O zaman SDK'ları o yere doğru kontrol et. | E | Çözümü kontrol edebilirsiniz ve Visual Studio dosyaları hemen tanır ve üzerinde hareket eder. |
| Mevcut büyük bir paket yazar topluluğuna katılabilirsiniz. | Yok | Toplum yeni. | E | |
| Mevcut paket tüketicilerinden oluşan büyük bir topluluğa katılabilirsiniz. | Yok | Toplum yeni. | E | |
| Ortaklardan oluşan bir ekosisteme (özel galeriler, depolar vb.) katılabilirsiniz. | Yok | Kullanılabilir depolar Visual Studio Marketplace, Microsoft Download [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]Center ve . | E | |
| Mekanizma, hem paket oluşturma hem de tüketim için sürekli tümleştirme yapı sunucularıyla tümleştirir. | E | SDK, işaretli konumu (SDKReferenceDirectoryRoot özelliği) komut satırında MSBuild'e aktarmalıdır. | E | |
| Mekanizma hem kararlı hem de ön sürüm paket sürümlerini destekler. | E | SDK, birden çok sürüm için başvuru eklemeyi destekler. | E | |
| Mekanizma yüklü paketler için otomatik güncelleştirmeyi destekler. | E | VSIX veya Visual Studio otomatik güncelleştirmelerinin bir parçası olarak sevk edilirse, SDK otomatik bildirimler sağlar. | E | |
| Mekanizma, paket oluşturmak ve tüketmek için tek başına bir *.exe* dosyası içerir. | E | SDK *MSBuild.exe*içerir. | E | |
| Paketler sürüm denetimine kontrol edilebilir. | E | Belge düğümü dışında hiçbir şeyi iade edemezsiniz, bu da Uzantı SDK'larının iade edilmeyebileceği anlamına gelir. Uzantı SDK boyutu büyük olabilir. | E | |
| Paketleri oluşturmak ve tüketmek için PowerShell arabirimi kullanabilirsiniz. | Y (tüketim), N (oluşturma) | SDK oluşturmak için araç yok. Tüketim komut satırında MSBuild yürütüyor. | E | |
| Hata ayıklama desteği için bir Sembol paketi kullanabilirsiniz. | E | *.pdb* dosyalarını SDK'ya bırakırsanız, dosyalar otomatik olarak alınır. | E | |
| Mekanizma paket yöneticisi otomatik güncelleştirmelerini destekler. | Yok | SDK MSBuild ile revize olur. | E | |
| Mekanizma hafif bir bildirim biçimini destekler. | E | *SDKManifest.xml* birçok öznitelikleri destekler, ancak küçük bir alt kümesi genellikle gereklidir. | E | |
| Mekanizma tüm Visual Studio sürümleri için kullanılabilir. | E | SDK tüm Visual Studio sürümlerini destekler. | E | NuGet tüm Visual Studio sürümlerini destekler. |

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
- [Projedeki başvuruları yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-references-in-a-project)
