---
title: Projenize NuGet paketi dahil
description: Bu belge, NuGet kullanarak NuGet paketinin nasıl dahil Mac için Visual Studio. Paket bulma ve indirmenin yanı sıra IDE tümleştirme özelliklerini tanıtma konusunda size yol sunar.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 199644f6df8edf2a23681525ffd88917fe2099cd2ee1f1cd44500a574da1c76e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121439428"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>NuGet paketleri yükleme ve Mac için Visual Studio

NuGet Paket Yöneticisi kullanıcı arabirimi Mac için Visual Studio proje ve çözümlerde paketleri kolayca yüklemenizi, kaldırmanızı ve NuGet güncelleştirmenizi sağlar. .NET Core, ASP.NET Core ve Xamarin projeleriniz için arama ve paket ekleme.

Bu makalede, bir NuGet paketinin projeye nasıl dahil olduğu açıklanmıştır ve süreci sorunsuz bir şekilde sağlayan araç zinciri açıklanmıştır.

Mac için Visual Studio'da NuGet kullanmaya giriş için bkz. Hızlı [Başlangıç: Mac için Visual Studio'de](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac) paket yükleme ve kullanma

## <a name="find-and-install-a-package"></a>Paket Bulma ve Yükleme

1. Mac için Visual Studio'de bir proje açıkken, Çözüm Penceresi'nde **Bağımlılıklar** klasörüne (Xamarin projesi  kullanıyorsanız Paketler klasörü) sağ tıklayın ve Paketleri **Yönet... NuGet seçin.**

    ![Yeni paket NuGet eylemi ekleme](media/nuget-walkthrough-packages-menu.png)

2. Bu, NuGet **Paketlerini Yönet penceresini** açar. Merkezi paket deposunda arama yapmak için iletişim kutusunun sol üst köşesindeki Kaynak açılan kutusunun olarak `nuget.org` NuGet olun.

    ![Paket NuGet Listele](media/nuget-walkthrough-add-packages1.png)

3. Belirli bir paketi bulmak için sağ üst köşedeki arama kutusunu kullanın, örneğin `EntityFramework` . Kullanmak istediğiniz bir paket bulana kadar paketi seçin ve Paket Ekle **düğmesine tıklayarak** yükleme işlemini başlatın.

    ![EntityFramework NuGet Paketi Ekleme](media/nuget-walkthrough-add-packages2.png)

4. Paket indirildikten sonra projenize eklenir. Çözüm, düzenlemekte olduğunu projenin türüne bağlı olarak değişir:

    **Xamarin Projeleri**
    * **Başvurular** düğümü, bir NuGet paketinin parçası olan tüm derlemelerin listesini içerir.
    * Paketler **düğümü,** indirdiğiniz NuGet her bir paket paketini görüntüler. Bir paketi bu listeden güncelleştirebilirsiniz veya kaldırabilirsiniz.
    
    **.NET Core Projeleri**

    * Düğümdeki **> NuGet,** indirdiğiniz NuGet paketi görüntüler. Bir paketi bu listeden güncelleştirebilirsiniz veya kaldırabilirsiniz.

## <a name="using-nuget-packages"></a>NuGet Paketlerini Kullanma

Uygulama NuGet ve proje başvuruları güncelleştirildiğinde, herhangi bir proje başvurusunda olduğu gibi API'lere göre programlandırabilirsiniz.

Dosyanın en üstüne `using` gerekli yönergelerini ekleyin:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Paketleri Güncelleştirme

Paket güncelleştirmeleri aynı anda, Bağımlılıklar düğümüne  **sağ** tıklar ( Xamarin projeleri için paketler düğümü) veya her pakette ayrı ayrı yapılabilir. Bir NuGet paketinin yeni bir sürümü kullanılabilir olduğunda, daire içeren Yukarı ![ ok simgesi ](media/nuget-walkthrough-update-icon.png) görüntülenir.

Bağlam menüsüne erişmek **için Bağımlılıklar'a** sağ tıklayın ve tüm paketleri güncelleştirmek **için** Güncelleştir'i seçin:

![Güncelleştir menüsünün vurgulanmış olduğu Bağımlılıklar bağlam menüsü](media/nuget-walkthrough-packages-menu-update.png)

* **Paket NuGet Yönet** - Projeye daha fazla paket eklemek için pencereyi açar.
* **Güncelleştirme** - Her paket için kaynak sunucuyu denetler ve daha yeni sürümleri indirir.
* **Geri** yükleme - Eksik paketleri indirir (mevcut paketleri daha yeni sürümlere güncelleştirmeden).

Güncelleştirme ve Geri Yükleme seçenekleri Çözüm düzeyinde de kullanılabilir ve çözümde yer alan tüm projeleri etkiler.

### <a name="updating-to-pre-release-versions-of-packages"></a>Paketlerin yayın öncesi sürümlerine güncelleştirme
Bir paketin daha yeni bir yayın öncesi sürümüne güncelleştirmek  için Bağımlılıklar'a sağ tıklar ve bağlam menüsünü açabilir ve Paketleri **Yönet... NuGet seçebilirsiniz.**

![Paketleri Yönet ile bağımlılıklar NuGet menüsü... menü vurgulanmış](media/nuget-walkthrough-packages-menu-manage-nuget-packages.png)

İletişim **kutusunun en altındaki Yayın** öncesi paketleri göster onay kutusunu işaretleyin.

!['NuGet öncesi paketleri göster' seçeneği işaretli olarak açılan Paket Paketlerini Yönet iletişim kutusu](media/nuget-walkthrough-show-pre-release-packages.png)

Son olarak, **iletişim** kutusunun Güncelleştirmeler sekmesinde güncelleştirmek istediğiniz paketi seçin ve Yeni Sürüm  açılan menüsünden yeni yayın öncesi sürümü seçin ve Paketi Güncelleştir'e **tıklayın.**

![Bir NuGet paketin seçili olduğu ve Yeni Sürüm açılan listesinin açık olduğu Yüklü sekmesine açılan Paketleri Yönet iletişim kutusu.](media/nuget-walkthrough-packages-nuget-dialog-update-installed-package.png)

### <a name="locating-outdated-packages"></a>Yeni paketleri bulma
Çözüm Penceresinde, bir paketin şu anda yüklü olan sürümünü görüntüp güncelleştirmek için pakete sağ tıklarsınız.

![Güncelleştirme, Kaldırma, Yenileme seçeneklerinin yer alan Paketler menüsü](media/nuget-walkthrough-PackageMenu.png)

Bir paketin yeni bir sürümü kullanılabilir olduğunda paket adının yanında bir bildirim de göreceğiniz için, paketi güncelleştirmek istediğinize karar veabilirsiniz.

![Yeni bir paket sürümü kullanılabilir olduğunda gösterilen bildirim](media/nuget-walkthrough-package-update-available.png)

Gösterilen menüde iki seçeneğiniz vardır:

* **Güncelleştirme** - Kaynak sunucuyu denetler ve daha yeni bir sürüm indirir (varsa).
* **Kaldır** - Paketi bu projeden kaldırır ve projenin Başvurularından ilgili derlemeleri kaldırır.

## <a name="manage-packages-for-the-solution"></a>Çözüm için paketleri yönetme

Bir çözüm için paketleri yönetmek, birden çok projeyle aynı anda çalışmak için kullanışlı bir olanaktır.

1. Çözüme sağ tıklayın ve Paketleri **Yönet... NuGet seçin:**

    ![Çözüm NuGet paketlerini yönetme](media/nuget-walkthrough-manage-packages-solution.png)

1. Kullanıcı arabirimi, çözümün paketlerini yöneterek işlemlerden etkilenen projeleri seçmenize olanak sağlar:

    ![Project paketleri yönetmeye yönelik seçiciyi seçin](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Birleştir sekmesi

Birden çok proje içeren bir çözümde çalışırken, her projede aynı NuGet paketini her yerde aynı sürüm numarasını da kullanmaya dikkat etmek en iyi yöntem olarak kabul edilir. Mac için Visual Studio, bir çözüm için paketleri  yönetmeyi seçtiğiniz zaman Paket Yöneticisi kullanıcı arabiriminde Birleştir sekmesi sağlayarak bunu kolaylaştırmanıza yardımcı olur. Bu sekmeyi kullanarak, çözümde farklı projeler tarafından farklı sürüm numaralarına sahip paketlerin nerede kullanı olduğunu kolayca görebilirsiniz:

![Paket Yöneticisi UI Birleştir sekmesi](media/nuget-walkthrough-consolidate-tab.png)

Bu örnekte NuGetDemo projesi Microsoft.EntityFrameworkCore 2.20 kullanırken NuGetDemo.Shared, Microsoft.EntityFrameworkCore 2.2.6 kullanıyor. Paket sürümlerini birleştirmek için şunları yapın:

- Proje listesinde güncelleştirilen projeleri seçin.
- Microsoft.EntityFrameworkCore 3.0.0 gibi Yeni Sürüm listesinde tüm bu projelerde kullanmak üzere sürümü seçin. 
- Paketi Birleştir **düğmesini** seçin.

Bu Paket Yöneticisi, seçili paket sürümünü tüm seçili projelere yükledikten sonra Paket Birleştir sekmesinde **artık** görünür.

## <a name="adding-package-sources"></a>Paket Kaynakları Ekleme

Yükleme için kullanılabilir paketler başlangıçta nuget.org. Bununla birlikte, uygulamanıza başka paket Mac için Visual Studio. Bu, geliştirme aşamasındaki kendi NuGet paketlerinizi test etmek veya şirket veya NuGet içinde özel bir NuGet sunucusu kullanmak için yararlı olabilir.

Paket Mac için Visual Studio listesini görüntülemek **Visual Studio > ve düzenlemek > NuGet > Için** Tercihler ve Kaynaklar'a gidin. Kaynakların uzak sunucu (URL ile belirtilir) veya yerel bir dizin olduğunu unutmayın.

![Paket Kaynakları](media/nuget-walkthrough-PackageSource.png)

Yeni **bir** kaynak ayarlamak için Ekle'ye tıklayın. Paket kaynağının kolay adını ve URL'sini (veya dosya yolunu) girin. Kaynak güvenli bir web sunucusu ise kullanıcı adını ve parolayı da girin, aksi takdirde şu girişleri boş bırakın:

![Ad, konum URL'si, kullanıcı adı ve parola istemi içeren Paket Kaynağı Ekle iletişim kutusu.](media/nuget-walkthrough-PackageSource2.png)

Daha sonra paketler aranken farklı kaynaklar seçilebilir:

![Paket kaynaklarının listesini içeren açılan listeyi gösteren Paket Kaynağı Ekle iletişim kutusu.](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Sürüm Denetimi

Bu NuGet, paketleri kaynak [denetimine NuGet olmadan uygulamanın nasıl kullanıla bir şekilde ele alınarak açıklanmıştır.](/nuget/consume-packages/packages-and-source-control) Kaynak denetiminde ikili dosyaları ve kullanılmayan bilgileri depolamamayı tercih ederseniz, Mac için Visual Studio otomatik olarak sunucudan geri yüklemek için yapılandırmayı yapılandırabilirsiniz. Başka bir ifadeyle, bir geliştirici projeyi kaynak denetiminden ilk kez Mac için Visual Studio gerekli paketleri otomatik olarak indirecek ve yükleyecek.

![Paketleri otomatik olarak geri yükleme](media/nuget-walkthrough-AutoRestore.png)

Dizini izlemenin dışında nasıl dışlayabilirsiniz? hakkında ayrıntılı bilgi için `packages` kaynak denetimi belgelerinize bakın.

## <a name="related-video"></a>İlgili Video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'de bir paket yükleme ve kullanma (Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
