---
title: Projenize bir NuGet paketi dahil
description: Bu belge, Mac için Visual Studio'u kullanarak bir projeye NuGet paketinin nasıl ekleştirilebildiğini kapsar. Bir paket bulma ve indirmenin yanı sıra IDE tümleştirme özelliklerini de kullanıma sunar.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74127207"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Mac için Visual Studio'da NuGet paketlerini yükleyin ve yönetin

Mac için Visual Studio'daki NuGet Paket Yöneticisi Kullanıcı Arabirimi, projelerde ve çözümlerde NuGet paketlerini kolayca yüklemenize, kaldırmanıza ve güncellemenize olanak tanır. .NET Core, ASP.NET Core ve Xamarin projelerinize paket arayabilir ve ekleyebilirsiniz.

Bu makalede, bir projeye NuGet paketinin nasıl dahil edilebildiğini açıklar ve işlemi sorunsuz hale getiren takım zincirini gösterir.

Mac için Visual Studio'da NuGet'i kullanmak için bir giriş için [Quickstart: Mac için Visual Studio'da bir paket yükleyin ve kullanın](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Paket Bulma ve Yükleme

1. Mac için Visual Studio'da açık olan bir projeyle, **Solution Pad'deki** **Bağımlılıklar** klasörüne (Xamarin projesi kullanıyorsanız**paketler** klasörü) sağ tıklayın ve **NuGet Paketlerini Yönet'i seçin...**.

    ![Yeni NuGet paketi bağlam eylemi ekleme](media/nuget-walkthrough-packages-menu.png)

2. Bu, **NuGet Paketlerini Yönet** penceresini başlatıyor. İletişim kutusunun sol üst köşesindeki Kaynak açılır bırakma nın `nuget.org`, merkezi NuGet paket deposunda arama yapmak üzere ayarlandığından emin olun.

    ![NuGet Paketlerini Listele](media/nuget-walkthrough-add-packages1.png)

3. Örneğin, `EntityFramework`belirli bir paketi bulmak için sağ üst köşedeki arama kutusunu kullanın. Kullanmak istediğiniz bir paket bulduğunuzda, paketi seçin ve yüklemeye başlamak için **Paket Ekle** düğmesini tıklatın.

    ![EntityFramework NuGet Paketi Ekle](media/nuget-walkthrough-add-packages2.png)

4. Paket indirildikten sonra projenize eklenir. Çözüm, düzenlediğiniz projenin türüne bağlı olarak değişecektir:

    **Xamarin Projeleri**
    * **Başvuru** düğümü, NuGet paketinin parçası olan tüm derlemelerin listesini içerir.
    * **Paket** düğümü, indirdiğiniz her NuGet paketini görüntüler. Bir paketi bu listeden güncelleyebilir veya kaldırabilirsiniz.
    
    **.NET Çekirdek Projeleri**

    * **Bağımlılıklar > NuGet** düğümü indirdiğiniz her NuGet paketini görüntüler. Bir paketi bu listeden güncelleyebilir veya kaldırabilirsiniz.

## <a name="using-nuget-packages"></a>NuGet Paketlerini Kullanma

NuGet paketi eklendikten ve proje başvuruları güncellendikten sonra, api'ler karşısında herhangi bir proje referansı ile olduğu gibi programlayabilirsiniz.

Dosyanızın en üstüne `using` gerekli yönergeleri eklediğinizden emin olun:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Paketleri Güncelleme

Paket güncelleştirmeleri, **Bağımlılıklar** düğümüne (Xamarin projeleri için**paket** düğümü) sağ tıklayarak veya her pakette ayrı ayrı tek tek yapılabilir. NuGet paketinin yeni bir sürümü kullanılabilir olduğunda, ![bir güncelleştirme](media/nuget-walkthrough-update-icon.png)simgesi daire ile yukarı ok görünür.

Bağlam menüsüne erişmek için **Bağımlılıklar'a** sağ tıklayın ve tüm paketleri güncelleştirmek için **Güncelleştir'i** seçin:

![Paketler menüsü](media/nuget-walkthrough-packages-menu-update.png)

* **NuGet Paketlerini Yönet** - Projeye daha fazla paket eklemek için pencereyi açar.
* **Güncelleştirme** - Her paket için kaynak sunucuyu denetler ve daha yeni sürümleri indirir.
* **Geri Yükleme** - Eksik paketleri indirir (varolan paketleri yeni sürümlere güncelleştirmeden).

Güncelleştirme ve Geri Yükleme seçenekleri de Çözüm düzeyinde mevcuttur ve çözümdeki tüm projeleri etkiler.

### <a name="locating-outdated-packages"></a>Eski paketleri bulma
Çözüm defterinden, bir paketin şu anda hangi sürümünün yüklü olduğunu görüntüleyebilir ve güncelleştirmek için pakete sağ tıklayabilirsiniz.

![Güncelleme, Kaldırma, Yenileme seçenekleri yle paketler menüsü](media/nuget-walkthrough-PackageMenu.png)

Ayrıca, paketin yeni bir sürümü kullanılabilir olduğunda paket adının yanında bir bildirim görürsünüz, böylece paketi güncelleştirmek isteyip istemediğinize karar verebilirsiniz.

![Yeni bir paket sürümü kullanılabilir olduğunda gösterilen bildirim](media/nuget-walkthrough-package-update-available.png)

Gösterilen menüde iki seçeneğiniz var:

* **Güncelleştirme** - Kaynak sunucuyu denetler ve daha yeni bir sürümü karşıdan yükler (varsa).
* **Kaldır** - Paketi bu projeden kaldırır ve ilgili derlemeleri projenin Başvuruları'ndan kaldırır.

## <a name="manage-packages-for-the-solution"></a>Çözüm için paketleri yönetme

Bir çözüm için paketleri yönetmek, aynı anda birden fazla projeyle çalışmak için kullanışlı bir araçtır.

1. Çözüme sağ tıklayın ve **NuGet Paketlerini Yönet'i seçin...**:

    ![Çözüm için NuGet paketlerini yönetin](media/nuget-walkthrough-manage-packages-solution.png)

1. Çözüm için paketleri yönetirken, UI operasyonlardan etkilenen projeleri seçmenize olanak tanır:

    ![Çözüm için paketleri yönetirken proje seçici](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Sekmeyi birleştir

Birden çok projeiçeren bir çözümde çalışırken, her projede aynı NuGet paketini kullandığınız her yerde aynı paketin sürüm numarasını kullandığınızdan emin olmak en iyi yöntem olarak kabul edilir. Mac için Visual Studio, bir çözüm için paketleri yönetmeyi seçtiğinizde Paket Yöneticisi UI'de **Birleştirilmiş** sekme sağlayarak bunu kolaylaştırmaya yardımcı olur. Bu sekmeyi kullanarak, farklı sürüm numaralarına sahip paketlerin çözümde farklı projeler tarafından nerede kullanıldığını kolayca görebilirsiniz:

![Paket Yöneticisi UI Birleştirme sekmesi](media/nuget-walkthrough-consolidate-tab.png)

Bu örnekte, NuGetDemo projesi Microsoft.EntityFrameworkCore 2.20'yi kullanırken, NuGetDemo.Shared Microsoft.EntityFrameworkCore 2.2.6'yı kullanıyor. Paket sürümlerini birleştirmek için aşağıdakileri yapın:

- Proje listesinde güncelleştirilecek projeleri seçin.
- Microsoft.EntityFrameworkCore 3.0.0 gibi **Yeni Sürüm** listesindeki tüm bu projelerde kullanılacak sürümü seçin.
- Paketi **Birleştir** düğmesini seçin.

Paket Yöneticisi, seçili paket sürümünü seçili tüm projelere yükler ve ardından paket **Birleştirme** sekmesinde görünmez.

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
