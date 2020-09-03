---
title: Projenize bir NuGet paketi dahil etme
description: Bu belge, Mac için Visual Studio kullanarak bir projeye NuGet paketinin nasıl ekleneceğini kapsar. Bir paketi bulmayı ve indirmeyi, Ayrıca IDE tümleştirme özelliklerini tanıtmayı da açıklar.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74127207"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Mac için Visual Studio NuGet paketlerini yükleyip yönetme

Mac için Visual Studio 'daki NuGet Paket Yöneticisi Kullanıcı arabirimi, projelerde ve çözümlerde NuGet paketlerini kolayca yüklemenize, kaldırmanıza ve güncelleştirmenize olanak tanır. Paketleri arayıp .NET Core, ASP.NET Core ve Xamarin projelerinize ekleyebilirsiniz.

Bu makalede, bir projeye NuGet paketinin nasıl dahil edileceğini ve işlemin sorunsuz hale getiren araç zincirini nasıl gösterdiği açıklanmaktadır.

Mac için Visual Studio 'de NuGet kullanma girişi için bkz [. hızlı başlangıç: Mac için Visual Studio bir paketi yüklemek ve kullanmak](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Paket bulma ve yüklemeyi

1. Mac için Visual Studio bir proje açıkken, **çözüm bölmesi** **Bağımlılıklar** klasörüne (Xamarin projesi kullanılıyorsa**paketler** klasörü) sağ tıklayın ve **NuGet Paketlerini Yönet..**. seçeneğini belirleyin.

    ![Yeni NuGet paketi bağlam eylemi Ekle](media/nuget-walkthrough-packages-menu.png)

2. Bu, **NuGet Paketlerini Yönet** penceresi başlatılır. Merkezi NuGet paket deposunda arama yapmak için, iletişim kutusunun sol üst köşesindeki kaynak açılan penceresinde olarak ayarlandığından emin olun `nuget.org` .

    ![NuGet paketlerini listeleme](media/nuget-walkthrough-add-packages1.png)

3. Belirli bir paketi bulmak için sağ üst köşedeki arama kutusunu kullanın (örneğin,) `EntityFramework` . Kullanmak istediğiniz bir paket bulduğunuz zaman, yüklemeyi başlatmak için paketi seçin ve **paket Ekle** düğmesine tıklayın.

    ![EntityFramework NuGet paketi Ekle](media/nuget-walkthrough-add-packages2.png)

4. Paket indirildikten sonra projenize eklenir. Bu çözüm, düzenlemekte olduğunuz projenin türüne bağlı olarak değişir:

    **Xamarin projeleri**
    * **Başvurular** düğümü, bir NuGet paketinin parçası olan tüm derlemelerin bir listesini içerir.
    * **Paketler** düğümü, Indirdiğiniz her NuGet paketini görüntüler. Bu listeden bir paketi güncelleştirebilir veya kaldırabilirsiniz.
    
    **.NET Core projeleri**

    * **NuGet düğümü > bağımlılıklar** , Indirdiğiniz her NuGet paketini görüntüler. Bu listeden bir paketi güncelleştirebilir veya kaldırabilirsiniz.

## <a name="using-nuget-packages"></a>NuGet paketlerini kullanma

NuGet paketi eklendikten ve proje güncelleştirildikten sonra, herhangi bir proje başvurusunda yaptığınız gibi API 'Lerle programlama yapabilirsiniz.

Dosyanızın en üstüne gerekli yönergeleri eklemediğinizden emin olun `using` :

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Paketler güncelleştiriliyor

Paket güncelleştirmeleri, **Bağımlılıklar** düğümüne sağ tıklanarak (Xamarin projeleri için**paketler** düğümü) veya her bir pakette ayrı ayrı tek bir şekilde yapılabilir. NuGet paketinin yeni bir sürümü kullanılabilir olduğunda, bir güncelleştirme simgesi, ![ daireyle birlikte görüntülenir ](media/nuget-walkthrough-update-icon.png) .

Bağlam menüsüne erişmek için **Bağımlılıklar** ' a sağ tıklayın ve tüm paketleri güncelleştirmek için **Güncelleştir** ' i seçin:

![Paketler menüsü](media/nuget-walkthrough-packages-menu-update.png)

* **NuGet Paketlerini Yönet** -projeye daha fazla paket eklemek için pencereyi açar.
* **Güncelleştir** -kaynak sunucuyu her bir paket için denetler ve daha yeni sürümleri indirir.
* **Restore** -eksik paketleri indirir (var olan paketleri yeni sürümlere güncelleştirmeden önce).

Güncelleştirme ve geri yükleme seçenekleri de çözüm düzeyinde bulunur ve Çözümdeki tüm projeleri etkiler.

### <a name="locating-outdated-packages"></a>Güncel olmayan paketleri bulma
Çözüm panelinden, bir paketin hangi sürümünün yüklü olduğunu görüntüleyebilir ve güncelleştirilecek pakete sağ tıklamakta tıklayabilirsiniz.

![Güncelleştirme, kaldırma, yenileme seçeneklerini içeren paketler menüsü](media/nuget-walkthrough-PackageMenu.png)

Ayrıca, paketin yeni bir sürümü kullanılabilir olduğunda paket adının yanında bir bildirim görürsünüz. bu sayede, güncelleştirmeyi güncelleştirmek isteyebilir karar verebilirsiniz.

![Yeni bir paket sürümü kullanılabilir olduğunda bildirim gösteriliyor](media/nuget-walkthrough-package-update-available.png)

Gösterilen menüde iki seçeneğiniz vardır:

* **Güncelleştir** -kaynak sunucuyu denetler ve daha yeni bir sürümü indirir (varsa).
* **Remove** -paketi bu projeden kaldırır ve ilgili derlemeleri projenin başvurularından kaldırır.

## <a name="manage-packages-for-the-solution"></a>Çözüm için paketleri yönetme

Bir çözüm için paketlerin yönetilmesi, birden çok projeyle aynı anda çalışması için uygun bir yoldur.

1. Çözüme sağ tıklayın ve **NuGet Paketlerini Yönet..**. öğesini seçin:

    ![Çözüm için NuGet Paketlerini Yönet](media/nuget-walkthrough-manage-packages-solution.png)

1. Çözüm için paketleri yönetirken, Kullanıcı arabirimi işlemlerden etkilenen projeleri seçmenizi sağlar:

    ![Çözüm için paketleri yönetirken proje Seçicisi](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Birleştirme sekmesi

Birden çok projeyle bir çözümde çalışırken, her bir projede aynı NuGet paketini kullandığınızdan emin olmak için en iyi uygulama olarak kabul edilir. Ayrıca, bu paketin aynı sürüm numarasını da kullanıyorsunuz. Mac için Visual Studio, bir çözüm için paketleri yönetmeyi seçtiğinizde, Paket Yöneticisi Kullanıcı arabirimine bir **birleştirme** sekmesi sunarak bunu kolaylaştırır. Bu sekmeyi kullanarak, farklı sürüm numaralarına sahip paketlerin çözümdeki farklı projeler tarafından nasıl kullanıldığını kolayca görebilirsiniz:

![Paket Yöneticisi UI birleştirme sekmesi](media/nuget-walkthrough-consolidate-tab.png)

Bu örnekte, NuGetDemo projesi Microsoft. EntityFrameworkCore 2,20 ' i kullanıyor, Ngetdemo. Shared, Microsoft. EntityFrameworkCore 2.2.6 kullanıyor. Paket sürümlerini birleştirmek için aşağıdakileri yapın:

- Proje listesinde güncelleştirilecek projeleri seçin.
- **Yeni sürüm** listesindeki tüm projelerde kullanılacak sürümü seçin; örneğin, Microsoft. EntityFrameworkCore 3.0.0.
- **Paketi Birleştir** düğmesini seçin.

Paket Yöneticisi seçili paket sürümünü seçili tüm projelere yükleyerek, bu paket artık **birleştirme** sekmesinde görünmez.

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
