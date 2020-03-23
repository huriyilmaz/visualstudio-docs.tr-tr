---
title: Projenize bir NuGet paketi dahil
description: Bu belge, bir Xamarin projesine bir NuGet paketinin nasıl dahil edilebildiğini kapsar. Bir paket bulma ve indirmenin yanı sıra IDE tümleştirme özelliklerini de kullanıma sunar.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.openlocfilehash: 728a225f4a1d14af986039cae7cb2fc8a493ecc9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983310"
---
# <a name="include-a-nuget-package-in-your-project"></a>Projenize bir NuGet paketi ekleyin

NuGet .NET geliştirme için en popüler paket yöneticisidir ve Windows'da Mac ve Visual Studio için Visual Studio'da yerleşiktir. IDE'yi kullanarak Xamarin.iOS ve Xamarin.Android projelerinize paket arayabilir ve ekleyebilirsiniz.

Bu makalede, bir projeye NuGet paketinin nasıl dahil edilebildiğini açıklar ve işlemi sorunsuz hale getiren takım zincirini gösterir.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet in Visual Studio for Mac

NuGet paketi işlevselliğini göstermek için, öncelikle yeni bir uygulama oluşturma ve paket ekleme ile yürüyeceğiz. Daha sonra paketleri yönetmenize yardımcı olan IDE özelliklerini tartışırız.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

İlk olarak, aşağıda `HelloNuget` gösterildiği gibi adlı bir proje oluşturun. Bu örnek, iOS Tek Görünüm Uygulaması şablonu gösterir, ancak desteklenen herhangi bir proje türü çalışır:

![Yeni iOS Projesi Oluşturma](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Paket Ekleme

Mac için Visual Studio'da proje açıkken, **Solution Pad'deki** **Paketler** klasörüne sağ tıklayın ve **Paket Ekle'yi**seçin:

![Yeni NuGet paketi bağlam eylemi ekleme](media/nuget-walkthrough-PackagesMenu.png)

Bu, **Paket Ekle** penceresini başlatıyor. Kaynak açılır, aşağıdakiler için `nuget.org`ayarlandığından emin olun:

![Kaynak listesi açılır](media/nuget-walkthrough-Source.png)

Pencere açıldığında varsayılan paket kaynağından paketlerin listesini yükler: nuget.org. İlk sonuçlar şu na benzer:

![NuGet Paketlerini Listele](media/nuget-walkthrough-AddPackages1.png)

Örneğin, `azure`belirli bir paketi bulmak için sağ üst köşedeki arama kutusunu kullanın. Kullanmak istediğiniz bir paket bulduğunuzda, paketi seçin ve yüklemeye başlamak için **Paket Ekle** düğmesini tıklatın.

[Azure NuGet Paketi Ekle](media/nuget-walkthrough-AddPackages2.png)

Paket indirildikten sonra projenize eklenir. Çözüm aşağıdaki gibi değişecektir:

* **Başvuru** düğümü, NuGet paketinin parçası olan tüm derlemelerin listesini içerir.
* **Paket** düğümü, indirdiğiniz her NuGet paketini görüntüler. Bir paketi bu listeden güncelleyebilir veya kaldırabilirsiniz.
* Projeye bir **packages.config** dosyası eklenecektir. Bu XML dosyası, bu projede hangi paket sürümlerinin başvurulmasını izlemek için IDE tarafından kullanılır. Bu dosya elle düzenlenmemeli, ancak sürüm denetiminde tutmalısınız. Bir project.json dosyasının packages.config dosyası yerine kullanılabileceğini unutmayın. Project.json dosyası, geçişli geri yüklemeyi destekleyen NuGet 3 ile tanıtılan yeni bir paket dosyası biçimidir. Project.json hakkında daha ayrıntılı bilgi [NuGet belgelerinde](/NuGet/Schema/Project-Json)bulunabilir. Project.json dosyasının el ile eklenmesi ve project.json dosyası Mac için Visual Studio'da kullanılmadan önce projenin kapatılması ve yeniden açılması gerekir.

## <a name="using-nuget-packages"></a>NuGet Paketlerini Kullanma

NuGet paketi eklendikten ve proje başvuruları güncellendikten sonra, api'ler karşısında herhangi bir proje referansı ile olduğu gibi programlayabilirsiniz.

Dosyanızın en üstüne `using` gerekli yönergeleri eklediğinizden emin olun:

```csharp
using Newtonsoft.Json;
```

Çoğu NuGet, README veya Proje sayfası bağlantısı gibi ek bilgiler sağlar. Normalde Paket Ekle sayfasındaki paket cümlesinde buna bir bağlantı bulabilirsiniz:

[Proje Sayfası bağlantısını görüntüle](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Paket Güncellemeleri

Package updates can be done either all at once, by right-clicking on the **Packages** node, or individually on each component.

Bağlam menüsüne erişmek için **Paketler'e** sağ tıklayın:

![Paketler menüsü](media/nuget-walkthrough-PackagesMenu.png)

* **Paket Ekle** - Projeye daha fazla paket eklemek için pencereyi açar.
* **Güncelleştirme** - Her paket için kaynak sunucuyu denetler ve daha yeni sürümleri indirir.
* **Geri Yükleme** - Eksik paketleri indirir (varolan paketleri yeni sürümlere güncelleştirmeden).

Güncelleştirme ve Geri Yükleme seçenekleri de Çözüm düzeyinde mevcuttur ve çözümdeki tüm projeleri etkiler.

Ayrıca, bağlam menüsüne erişmek için tek tek paketlere sağ tıklayabilirsiniz:

![Paketler menüsü](media/nuget-walkthrough-PackageMenu.png)

* **Sürüm Numarası** - Sürüm numarası devre dışı bırakılmış bir menü öğesidir - yalnızca bilgilendirme amaçlı dır.
* **Güncelleştirme** - Kaynak sunucuyu denetler ve daha yeni bir sürümü karşıdan yükler (varsa).
* **Kaldır** - Paketi bu projeden kaldırır ve ilgili derlemeleri projenin Başvuruları'ndan kaldırır.

## <a name="adding-package-sources"></a>Paket Kaynakları Ekleme

Yükleme için kullanılabilen paketler başlangıçta nuget.org'dan alınır. Ancak, Mac için Visual Studio'ya başka paket konumları ekleyebilirsiniz. Bu, geliştirme aşamasındaki kendi NuGet paketlerinizi test etmek veya şirketiniz veya kuruluşunuz içinde özel bir NuGet sunucusu kullanmak için yararlı olabilir.

Mac için Visual Studio'da, paket kaynaklarının listesini görüntülemek ve için **Visual Studio > Preferences > NuGet > Kaynakları'na** gidin. Kaynakların uzak bir sunucu (URL tarafından belirtilir) veya yerel bir dizin olabileceğini unutmayın.

![Paket Kaynakları](media/nuget-walkthrough-PackageSource.png)

Yeni bir kaynak ayarlamak için **Ekle'yi** tıklatın. Paket kaynağına uygun bir ad ve URL (veya dosya yolu) girin. Kaynak güvenli bir web sunucusuysa, kullanıcı adı ve parolayı da girin, aksi takdirde bu girişleri boş bırakın:

![Paket Kaynakları Ekle](media/nuget-walkthrough-PackageSource2.png)

Daha sonra paketler aranırken farklı kaynaklar seçilebilir:

![Paket Kaynakları Ekle](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Sürüm Denetimi

NuGet belgeleri [kaynak denetimine paket işlemeden NuGet'i kullanmayı](/nuget/consume-packages/packages-and-source-control)tartışır. Kaynak denetiminde ikili ve kullanılmayan bilgileri depolamamayı tercih ederseniz, sunucudan paketleri otomatik olarak geri yüklemek için Visual Studio for Mac'i yapılandırabilirsiniz. Bu, bir geliştirici projeyi ilk kez kaynak denetiminden aldığında, Mac için Visual Studio'nun gerekli paketleri otomatik olarak indireceği ve yükleyeceği anlamına gelir.

![Paketleri otomatik olarak geri yükleme](media/nuget-walkthrough-AutoRestore.png)

Dizinin izlenmesini nasıl dışlayacak `packages` larına ilişkin ayrıntılar için özel kaynak denetim belgelerinize bakın.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'da (Windows'da) bir paket yükleme ve kullanma](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
