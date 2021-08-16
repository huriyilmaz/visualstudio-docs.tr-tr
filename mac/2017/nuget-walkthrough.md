---
title: projenize bir NuGet paketi dahil etme
description: bu belge bir Xamarin projesine NuGet paketinin nasıl ekleneceğini kapsar. Bir paketi bulmayı ve indirmeyi, Ayrıca IDE tümleştirme özelliklerini tanıtmayı da açıklar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 1a9e71e1dd89f80ae503f7ffb54dbcae0c8b84b4056645be1cf6092331bd5156
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121422506"
---
# <a name="include-a-nuget-package-in-your-project"></a>projenize bir NuGet paketi ekleyin

NuGet, .net geliştirme için en popüler paket yöneticisidir ve Windows üzerinde Mac için Visual Studio ve Visual Studio yerleşiktir. Android kullanarak, Xamarin. iOS ve Xamarin. Android projelerinize paket arayabilir ve bunları ekleyebilirsiniz.

bu makalede, bir projeye NuGet paketinin nasıl dahil edileceğini ve işlemin sorunsuz hale getiren araç zincirini nasıl gösterdiği açıklanmaktadır.

## <a name="nuget-in-visual-studio-for-mac"></a>Mac için Visual Studio NuGet

NuGet paketi işlevlerini göstermek için, ilk olarak yeni bir uygulama oluşturma ve buna paket ekleme adımlarını inceleyeceğiz. Daha sonra paketlerin yönetilmesine yardımcı olan IDE özellikleri ele alınacaktır.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

İlk olarak, aşağıda gösterildiği gibi adlı bir proje oluşturun `HelloNuget` . Bu örnekte iOS tek görünüm uygulama şablonu gösterilmektedir, ancak desteklenen tüm proje türleri çalışır:

![Yeni iOS Project oluştur](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Paket ekleme

Mac için Visual Studio proje açıkken, **Çözüm Bölmesi** **paketler** klasörüne sağ tıklayın ve **paketleri ekle**' yi seçin:

![yeni NuGet paketi bağlam eylemi ekle](media/nuget-walkthrough-PackagesMenu.png)

Bu, **paket Ekle** penceresini başlatır. Kaynak açılan, ' ın şu şekilde ayarlandığından emin olun `nuget.org` :

![Kaynak listesi açılan listesi](media/nuget-walkthrough-Source.png)

Pencere açıldığında, varsayılan paket kaynağından bir paket listesi yükler: nuget.org. İlk sonuçlar şuna benzer:

![NuGet paketlerini listele](media/nuget-walkthrough-AddPackages1.png)

Belirli bir paketi bulmak için sağ üst köşedeki arama kutusunu kullanın (örneğin,) `azure` . Kullanmak istediğiniz bir paket buldığınızda, yüklemeyi başlatmak için seçin ve **paket Ekle** düğmesine tıklayın.

[Azure NuGet paketini ekle](media/nuget-walkthrough-AddPackages2.png)

Paket indirildikten sonra projenize eklenir. Çözüm aşağıdaki gibi değişecektir:

* **başvurular** düğümü, bir NuGet paketinin parçası olan tüm derlemelerin bir listesini içerir.
* **paketler** düğümü, indirdiğiniz her bir NuGet paketini görüntüler. Bu listeden bir paketi güncelleştirebilir veya kaldırabilirsiniz.
* Projeye bir **packages.config** dosyası eklenecektir. Bu XML dosyası IDE tarafından bu projede hangi paket sürümlerinin başvurulduğunu izlemek için kullanılır. Bu dosya el ile düzenlenmemelidir, ancak sürüm denetiminde saklamanız gerekir. Dosya project.jsbir packages.config dosyası yerine kullanılabileceğini unutmayın. dosyadaki project.js, geçişli geri yüklemeyi destekleyen NuGet 3 ile sunulan yeni bir paket dosyası biçimidir. project.jshakkında daha ayrıntılı bilgi [NuGet belgelerinde](/NuGet/Schema/Project-Json)bulunabilir. project.jsdosyadaki project.jsel ile eklenmesi gerekir ve proje, Mac için Visual Studio dosya üzerinde kullanılmadan önce kapatılıp yeniden açılır.

## <a name="using-nuget-packages"></a>NuGet paketlerini kullanma

NuGet paketi eklendikten ve proje güncelleştirildikten sonra, herhangi bir proje başvurusunda yaptığınız gibi apı 'lerle programlama yapabilirsiniz.

Dosyanızın en üstüne gerekli yönergeleri eklemediğinizden emin olun `using` :

```csharp
using Newtonsoft.Json;
```

çoğu NuGet NuGet kaynağına yönelik benioku veya Project sayfası bağlantısı gibi ek bilgiler sağlar. Normal olarak, paket Ekle sayfasında Bu pakette bir bağlantı bulabilirsiniz.

[Project sayfa bağlantısını görüntüle](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Paket güncelleştirmeleri

Paket güncelleştirmeleri tek seferde, **paketler** düğümüne sağ tıklayarak ya da her bir bileşen üzerinde ayrı ayrı yapılabilir.

Bağlam menüsüne erişmek için **paketlere** sağ tıklayın:

![Seçilen paketler düğümünü gösteren ekran görüntüsü ve sağ tıklama bağlam menüsü, paket Ekle, Güncelleştir, geri yükle ve Yenile komutlarıyla birlikte açılır.](media/nuget-walkthrough-PackagesMenu.png)

* **Paket Ekle** -projeye daha fazla paket eklemek için pencereyi açar.
* **Güncelleştir** -kaynak sunucuyu her bir paket için denetler ve daha yeni sürümleri indirir.
* **Restore** -eksik paketleri indirir (var olan paketleri yeni sürümlere güncelleştirmeden önce).

Güncelleştirme ve geri yükleme seçenekleri de çözüm düzeyinde bulunur ve Çözümdeki tüm projeleri etkiler.

Ayrıca, bir bağlam menüsüne erişmek için tek tek paketlere sağ tıklayabilirsiniz:

![Seçili tek bir paketi gösteren ekran görüntüsü ve sağ tıklama bağlam menüsü, güncelleştirme, kaldırma ve yenileme komutlarıyla birlikte açılır.](media/nuget-walkthrough-PackageMenu.png)

* **Sürüm numarası** -sürüm numarası devre dışı bir menü öğesi; yalnızca bilgilendirme amacıyla sağlanır.
* **Güncelleştir** -kaynak sunucuyu denetler ve daha yeni bir sürümü indirir (varsa).
* **Remove** -paketi bu projeden kaldırır ve ilgili derlemeleri projenin başvurularından kaldırır.

## <a name="adding-package-sources"></a>Paket kaynakları ekleniyor

Yükleme için kullanılabilen paketler başlangıçta nuget.org adresinden alınır. bununla birlikte, Mac için Visual Studio başka paket konumları da ekleyebilirsiniz. bu, geliştirme kapsamındaki kendi NuGet paketlerinizi test etmek veya şirketinizin veya kuruluşunuzun içinde özel bir NuGet sunucusunu kullanmak için yararlı olabilir.

Mac için Visual Studio, paket kaynakları listesini görüntülemek ve düzenlemek için **Visual Studio > tercihleri > NuGet > kaynakları** ' na gidin. Kaynakların uzak bir sunucu (bir URL ile belirtilir) veya yerel bir dizin olabileceğini unutmayın.

![Paket kaynakları](media/nuget-walkthrough-PackageSource.png)

Yeni bir kaynak kurmak için **Ekle** ' ye tıklayın. Paket kaynağına kolay bir ad ve URL (ya da dosya yolu) girin. Kaynak güvenli bir Web sunucusu ise, Kullanıcı adını ve parolayı da girin, aksi takdirde bu girdileri boş bırakın:

![Ad, konum, Kullanıcı adı ve parola alanlarını içeren paket kaynağı Ekle iletişim kutusunun ekran görüntüsü.](media/nuget-walkthrough-PackageSource2.png)

Paketler aranırken farklı kaynaklar seçilebilir:

![Paket ekleme ekranının, paketler aranırken seçilemeyen kaynakların açılan listesini gösteren ekran görüntüsü.](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Sürüm Denetimi

NuGet belgeleri, [kaynak denetimine paket işlemeden NuGet kullanmayı](/nuget/consume-packages/packages-and-source-control)tartışır. ikili dosyaları ve kullanılmayan bilgileri kaynak denetiminde depolamamayı tercih ediyorsanız, paketleri sunucudan otomatik olarak geri yüklemek için Mac için Visual Studio yapılandırabilirsiniz. bu, bir geliştirici projeyi kaynak denetiminden ilk kez aldığında Mac için Visual Studio gerekli paketleri otomatik olarak indirecek ve yükleymeyeceği anlamına gelir.

![Paketleri otomatik olarak geri yükle](media/nuget-walkthrough-AutoRestore.png)

Dizinin izlenmesini nasıl dışlayacak hakkında daha fazla bilgi için, belirli kaynak denetimi belgelerinize bakın `packages` .

## <a name="related-video"></a>İlgili video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio bir paketi yükleyip kullanma (Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
