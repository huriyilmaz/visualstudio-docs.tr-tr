---
title: Projenize bir NuGet paketi dahil etme
description: Bu belge bir Xamarin projesine bir NuGet paketinin nasıl ekleneceğini kapsar. Bir paketi bulmayı ve indirmeyi, Ayrıca IDE tümleştirme özelliklerini tanıtmayı da açıklar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 58d749a1d014288754dcd9eb7e620730933d742a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950404"
---
# <a name="include-a-nuget-package-in-your-project"></a>Projenize bir NuGet paketi ekleyin

NuGet, .NET geliştirme için en popüler paket yöneticisidir ve Windows üzerinde Mac için Visual Studio ve Visual Studio 'da yerleşiktir. Android kullanarak, Xamarin. iOS ve Xamarin. Android projelerinize paket arayabilir ve bunları ekleyebilirsiniz.

Bu makalede, bir projeye NuGet paketinin nasıl dahil edileceğini ve işlemin sorunsuz hale getiren araç zincirini nasıl gösterdiği açıklanmaktadır.

## <a name="nuget-in-visual-studio-for-mac"></a>Mac için Visual Studio 'de NuGet

NuGet paket işlevini göstermek için, ilk olarak yeni bir uygulama oluşturma ve buna paket ekleme adımlarını inceleyeceğiz. Daha sonra paketlerin yönetilmesine yardımcı olan IDE özellikleri ele alınacaktır.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

İlk olarak, aşağıda gösterildiği gibi adlı bir proje oluşturun `HelloNuget` . Bu örnekte iOS tek görünüm uygulama şablonu gösterilmektedir, ancak desteklenen tüm proje türleri çalışır:

![Yeni iOS projesi oluştur](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Paket ekleme

Mac için Visual Studio proje açıkken, **çözüm bölmesi** **paketler** klasörüne sağ tıklayın ve **Paketleri Ekle**' yi seçin:

![Yeni NuGet paketi bağlam eylemi Ekle](media/nuget-walkthrough-PackagesMenu.png)

Bu, **paket Ekle** penceresini başlatır. Kaynak açılan, ' ın şu şekilde ayarlandığından emin olun `nuget.org` :

![Kaynak listesi açılan listesi](media/nuget-walkthrough-Source.png)

Pencere açıldığında, varsayılan paket kaynağından bir paket listesi yükler: nuget.org. İlk sonuçlar şuna benzer:

![NuGet paketlerini listeleme](media/nuget-walkthrough-AddPackages1.png)

Belirli bir paketi bulmak için sağ üst köşedeki arama kutusunu kullanın (örneğin,) `azure` . Kullanmak istediğiniz bir paket buldığınızda, yüklemeyi başlatmak için seçin ve **paket Ekle** düğmesine tıklayın.

[Azure NuGet paketi ekleme](media/nuget-walkthrough-AddPackages2.png)

Paket indirildikten sonra projenize eklenir. Çözüm aşağıdaki gibi değişecektir:

* **Başvurular** düğümü, bir NuGet paketinin parçası olan tüm derlemelerin bir listesini içerir.
* **Paketler** düğümü, Indirdiğiniz her NuGet paketini görüntüler. Bu listeden bir paketi güncelleştirebilir veya kaldırabilirsiniz.
* Projeye bir **packages.config** dosyası eklenecektir. Bu XML dosyası IDE tarafından bu projede hangi paket sürümlerinin başvurulduğunu izlemek için kullanılır. Bu dosya el ile düzenlenmemelidir, ancak sürüm denetiminde saklamanız gerekir. Dosya project.jsbir packages.config dosyası yerine kullanılabileceğini unutmayın. project.jsdosya üzerinde, geçişli geri yüklemeyi destekleyen NuGet 3 ile sunulan yeni bir paket dosyası biçimi bulunur. Üzerinde project.jshakkında daha ayrıntılı bilgi [NuGet belgelerinde](/NuGet/Schema/Project-Json)bulunabilir. project.jsdosyadaki project.jsel ile eklenmesi gerekir ve proje, Mac için Visual Studio dosya üzerinde kullanılmadan önce kapatılıp yeniden açılır.

## <a name="using-nuget-packages"></a>NuGet paketlerini kullanma

NuGet paketi eklendikten ve proje güncelleştirildikten sonra, herhangi bir proje başvurusunda yaptığınız gibi API 'Lerle programlama yapabilirsiniz.

Dosyanızın en üstüne gerekli yönergeleri eklemediğinizden emin olun `using` :

```csharp
using Newtonsoft.Json;
```

Çoğu NuGet, NuGet kaynağına yönelik BENIOKU veya proje sayfası bağlantısı gibi ek bilgiler sağlar. Normal olarak, paket Ekle sayfasında Bu pakette bir bağlantı bulabilirsiniz.

[Proje sayfası bağlantısını görüntüle](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Paket güncelleştirmeleri

Paket güncelleştirmeleri tek seferde, **paketler** düğümüne sağ tıklayarak ya da her bir bileşen üzerinde ayrı ayrı yapılabilir.

Bağlam menüsüne erişmek için **paketlere** sağ tıklayın:

![Paketler menüsü](media/nuget-walkthrough-PackagesMenu.png)

* **Paket Ekle** -projeye daha fazla paket eklemek için pencereyi açar.
* **Güncelleştir** -kaynak sunucuyu her bir paket için denetler ve daha yeni sürümleri indirir.
* **Restore** -eksik paketleri indirir (var olan paketleri yeni sürümlere güncelleştirmeden önce).

Güncelleştirme ve geri yükleme seçenekleri de çözüm düzeyinde bulunur ve Çözümdeki tüm projeleri etkiler.

Ayrıca, bir bağlam menüsüne erişmek için tek tek paketlere sağ tıklayabilirsiniz:

![Paketler menüsü](media/nuget-walkthrough-PackageMenu.png)

* **Sürüm numarası** -sürüm numarası devre dışı bir menü öğesi; yalnızca bilgilendirme amacıyla sağlanır.
* **Güncelleştir** -kaynak sunucuyu denetler ve daha yeni bir sürümü indirir (varsa).
* **Remove** -paketi bu projeden kaldırır ve ilgili derlemeleri projenin başvurularından kaldırır.

## <a name="adding-package-sources"></a>Paket kaynakları ekleniyor

Yükleme için kullanılabilen paketler başlangıçta nuget.org adresinden alınır. Bununla birlikte, Mac için Visual Studio başka paket konumları da ekleyebilirsiniz. Bu, geliştirme aşamasındaki kendi NuGet paketlerinizi test etmek veya şirketinizin veya kuruluşunuzun içinde özel bir NuGet sunucusu kullanmak için yararlı olabilir.

Mac için Visual Studio, paket kaynakları listesini görüntülemek ve düzenlemek için **Visual Studio > tercihler > NuGet > kaynakları** ' na gidin. Kaynakların uzak bir sunucu (bir URL ile belirtilir) veya yerel bir dizin olabileceğini unutmayın.

![Paket kaynakları](media/nuget-walkthrough-PackageSource.png)

Yeni bir kaynak kurmak için **Ekle** ' ye tıklayın. Paket kaynağına kolay bir ad ve URL (ya da dosya yolu) girin. Kaynak güvenli bir Web sunucusu ise, Kullanıcı adını ve parolayı da girin, aksi takdirde bu girdileri boş bırakın:

![Paket kaynakları ekle](media/nuget-walkthrough-PackageSource2.png)

Paketler aranırken farklı kaynaklar seçilebilir:

![Paket kaynakları ekle](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Sürüm Denetimi

NuGet belgeleri, [kaynak denetimine paket Işlemeden NuGet kullanarak](/nuget/consume-packages/packages-and-source-control)açıklanır. İkili dosyaları ve kullanılmayan bilgileri kaynak denetiminde depolamamayı tercih ediyorsanız, paketleri sunucudan otomatik olarak geri yüklemek için Mac için Visual Studio yapılandırabilirsiniz. Bu, bir geliştirici projeyi kaynak denetiminden ilk kez aldığında Mac için Visual Studio gerekli paketleri otomatik olarak indirecek ve yükleymeyeceği anlamına gelir.

![Paketleri otomatik olarak geri yükle](media/nuget-walkthrough-AutoRestore.png)

Dizinin izlenmesini nasıl dışlayacak hakkında daha fazla bilgi için, belirli kaynak denetimi belgelerinize bakın `packages` .

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 'da bir paketi (Windows 'da) yükleyip kullanma](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
