---
title: Projenize NuGet paketi dahil
description: Bu belgede bir Xamarin projesine NuGet paketin nasıl dahil olduğu açıklanıyor. Paket bulma ve indirmenin yanı sıra IDE tümleştirme özelliklerini tanıtma konusunda size yol sunar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 274e8defe25fa78c30aee72834e486b302a9af4e
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962282"
---
# <a name="include-a-nuget-package-in-your-project"></a>Projenize NuGet paketi dahil etmek

NuGet .NET geliştirme için en popüler paket yöneticisidir ve yerleşik olarak Mac için Visual Studio ve Visual Studio'Windows. IDE'den birini kullanarak Xamarin.iOS ve Xamarin.Android projelerinize paket arayabilir ve bu projelere paket ebilirsiniz.

Bu makalede, bir NuGet paketinin projeye nasıl dahil olduğu açıklanmıştır ve süreci sorunsuz bir şekilde sağlayan araç zinciri açıklanmıştır.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet'Mac için Visual Studio

Paket NuGet göstermek için öncelikle yeni bir uygulama oluşturma ve paket ekleme adımlarını göstereceğiz. Ardından paketleri yönetmeye yardımcı olan IDE özelliklerini ele aacağız.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

İlk olarak, aşağıda gösterildiği gibi `HelloNuget` adlı bir proje oluşturun. Bu örnekte iOS Tek Görünüm Uygulaması şablonu gösterir, ancak desteklenen tüm proje türlerini kullanabilirsiniz:

![Yeni iOS Project](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Paket Ekleme

Proje Mac için Visual Studio açıkken, dosyanın Paket **klasörüne** sağ **tıklayın ve Çözüm Bölmesi** Ekle'yi **seçin:**

![Yeni paket NuGet eylemi ekleme](media/nuget-walkthrough-PackagesMenu.png)

Bu, Paket **Ekle penceresini** açar. Kaynak açılan listesinden olarak ayarlanmış olduğundan emin `nuget.org` olun:

![Kaynak listesi açılan listesi](media/nuget-walkthrough-Source.png)

Pencere açıldığında, varsayılan paket kaynağından paketlerin listesini yükler: nuget.org. İlk sonuçlar şöyle olur:

![Paket NuGet Listele](media/nuget-walkthrough-AddPackages1.png)

Belirli bir paketi bulmak için sağ üst köşedeki arama kutusunu kullanın, örneğin `azure` . Kullanmak istediğiniz bir paket bulana kadar paketi seçin ve Paket Ekle **düğmesine tıklayarak** yükleme işlemini başlatın.

[Azure NuGet Paketi Ekleme](media/nuget-walkthrough-AddPackages2.png)

Paket indirildikten sonra projenize eklenir. Çözüm aşağıdaki gibi değişir:

* **Başvurular** düğümü, bir NuGet paketinin parçası olan tüm derlemelerin listesini içerir.
* Paketler **düğümü,** indirdiğiniz NuGet her bir paket paketini görüntüler. Bir paketi bu listeden güncelleştirebilirsiniz veya kaldırabilirsiniz.
* Projeye **packages.config** bir dosya eklenir. Bu XML dosyası, bu projede başvurulan paket sürümlerini izlemek için IDE tarafından kullanılır. Bu dosya el ile düzenlenemez, ancak sürüm denetiminde tutmanız gerekir. Bir project.jsdosya yerine dosya üzerinde bir packages.config unutmayın. Dosyadaki project.js, geçişli geri yüklemeyi destekleyen NuGet 3 ile birlikte gelen yeni bir paket dosyası biçimidir. hakkında daha ayrıntılı project.jsdaha fazla bilgi için NuGet [bulunabilir.](/NuGet/Schema/Project-Json) Dosyada project.jsdosyanın el ile ekleniyor olması ve dosyada dosyanın project.jskullanılmadan önce projenin kapatılan ve yeniden açılması Mac için Visual Studio.

## <a name="using-nuget-packages"></a>NuGet Paketlerini Kullanma

Uygulama NuGet ve proje başvuruları güncelleştirildiğinde, herhangi bir proje başvurusunda olduğu gibi API'lere göre programlandırabilirsiniz.

Dosyanın en üstüne `using` gerekli yönergelerini ekleyin:

```csharp
using Newtonsoft.Json;
```

Çoğu NuGet Nuget kaynağına yönelik README veya Project sayfası bağlantısı gibi ek bilgiler sağlar. Normalde bunun bağlantısını Paket Ekle sayfasındaki paket gölgesinde bulabilirsiniz:

[Görünüm Project Sayfası bağlantısı](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Paket Güncelleştirmeleri

Paket güncelleştirmeleri tek tek, Paketler düğümüne sağ tıklar veya **tek** tek her bileşende yapılabilir.

Bağlam menüsüne erişmek **için** Paketler'e sağ tıklayın:

![Paket Ekle, Güncelleştir, Geri Yükle ve Yenile komutlarını içeren, seçili Paketler düğümünü ve sağ tıklama bağlam menüsünü gösteren ekran görüntüsü.](media/nuget-walkthrough-PackagesMenu.png)

* **Paket Ekle** - Projeye daha fazla paket eklemek için pencereyi açar.
* **Güncelleştirme** - Her paket için kaynak sunucuyu denetler ve daha yeni sürümleri indirir.
* **Geri** yükleme - Eksik paketleri indirir (mevcut paketleri daha yeni sürümlere güncelleştirmeden).

Güncelleştirme ve Geri Yükleme seçenekleri Çözüm düzeyinde de kullanılabilir ve çözümde yer alan tüm projeleri etkiler.

Bağlam menüsüne erişmek için ayrı ayrı paketlere sağ tıkabilirsiniz:

![Tek bir Paketin seçili olduğunu ve sağ tıklama bağlam menüsünün Güncelleştirme, Kaldırma ve Yenile komutlarını içeren açık olduğunu gösteren ekran görüntüsü.](media/nuget-walkthrough-PackageMenu.png)

* **Sürüm Numarası** - Sürüm numarası devre dışı bırakılmış bir menü öğesidir; yalnızca bilgilendirme amacıyla sağlanır.
* **Güncelleştirme** - Kaynak sunucuyu denetler ve daha yeni bir sürüm indirir (varsa).
* **Kaldır** - Paketi bu projeden kaldırır ve projenin Başvurularından ilgili derlemeleri kaldırır.

## <a name="adding-package-sources"></a>Paket Kaynakları Ekleme

Yükleme için kullanılabilir paketler başlangıçta nuget.org. Ancak, bu konuma başka paket konumları Mac için Visual Studio. Bu, geliştirme aşamasındaki kendi NuGet paketlerinizi test etmek veya şirket veya kuruluş içinde özel NuGet sunucusu kullanmak için yararlı olabilir.

Paket Mac için Visual Studio listesini görüntülemek **Visual Studio > düzenlemek için > NuGet > Tercihler** ve Kaynaklar'a gidin. Kaynakların uzak sunucu (URL ile belirtilir) veya yerel bir dizin olduğunu unutmayın.

![Paket Kaynakları](media/nuget-walkthrough-PackageSource.png)

Yeni **bir** kaynak ayarlamak için Ekle'ye tıklayın. Paket kaynağının kolay adını ve URL'sini (veya dosya yolunu) girin. Kaynak güvenli bir web sunucusu ise kullanıcı adını ve parolayı da girin, aksi takdirde şu girişleri boş bırakın:

![Ad, Konum, Kullanıcı Adı ve Parola alanlarını içeren Paket Kaynağı Ekle iletişim kutusunun ekran görüntüsü.](media/nuget-walkthrough-PackageSource2.png)

Daha sonra paketler aranken farklı kaynaklar seçilebilir:

![Paket araması için seçilecek kaynakların açılan listesini gösteren Paket Ekle ekran görüntüsü.](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Sürüm Denetimi

Bu NuGet, paketleri kaynak [denetimine NuGet bir şekilde nasıl kullanacağız?](/nuget/consume-packages/packages-and-source-control) Kaynak denetiminde ikili dosyaları ve kullanılmayan bilgileri depolamamayı tercih ederseniz, Mac için Visual Studio otomatik olarak sunucudan geri yüklemek için yapılandırmayı yapılandırabilirsiniz. Başka bir ifadeyle, geliştirici projeyi kaynak denetiminden ilk kez Mac için Visual Studio gerekli paketleri otomatik olarak indirecek ve yükleyecek.

![Paketleri otomatik olarak geri yükleme](media/nuget-walkthrough-AutoRestore.png)

Dizini izlemenin dışında nasıl dışlayabilirsiniz? hakkında ayrıntılı bilgi için `packages` kaynak denetimi belgelerinize bakın.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'de bir paket yükleme ve kullanma (Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
