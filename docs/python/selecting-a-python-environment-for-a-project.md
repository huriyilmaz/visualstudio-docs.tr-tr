---
title: Python yorumlayıcısı ve ortamınız için bir proje seçin
description: Anaconda ve sanal ortamlar, belirli bir projeye uygulamak da dahil olmak üzere bir Python ortamı özel olarak seçebilirsiniz.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 34ceb2ec7cc923f6642977cf4c70fbfae07bf523
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409630"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Nasıl bir proje için bir Python ortamı seçin

Bir global Python ortamı, Anaconda ortamı, bir sanal ortam ya da conda ortamı gibi belirli bir ortama bağlamında bir Python projesindeki tüm kod çalıştırır. Visual Studio bu ortamda hata ayıklama, içeri aktarma ve üye tamamlama, sözdizimi denetimi ve Python sürümü ve yüklü paketleri birtakım özel dil hizmetleri gerektiren herhangi bir görev için de kullanır.

Visual Studio 'daki tüm yeni Python projeleri başlangıçta **Çözüm Gezgini**' deki **Python ortamları** düğümü altında görünen varsayılan genel ortamı kullanacak şekilde yapılandırılmıştır:

![Çözüm Gezgini'nde gösterilen genel varsayılan Python ortamı](media/environments/environments-project.png)

::: moniker range="vs-2017"
Bir projenin ortamını değiştirmek için, **Python ortamları** düğümüne sağ tıklayın ve **Python ortamlarını Ekle/Kaldır**' ı seçin. Genel, sanal ve Conda ortamlarını içeren görüntülenen listeden, **Python ortamları** düğümü altında görünmesini istediklerinizi seçin:

![Python ortamları Ekle/Kaldır iletişim kutusu](media/environments/environments-add-remove.png)

**Tamam**' ı seçtiğinizde, seçilen tüm ortamlar **Python ortamları** düğümünün altında görünür. Şu anda etkin ortam kalın yazı tipinde görünür:

![Çözüm Gezgini'nde birden çok Python ortamları](media/environments/environments-project-multiple.png)

Farklı bir ortamı hızlıca etkinleştirmek için, bu ortam adına sağ tıklayın ve **ortamı etkinleştir**' i seçin. Seçtiğiniz proje ile kaydedilir ve proje gelecekte açtığınızda bu ortamda etkinleştirilir. **Python ortamlarını Ekle/Kaldır** iletişim kutusundaki tüm seçenekleri temizlerseniz, Visual Studio genel varsayılan ortamı etkinleştirir.

**Python ortamları** düğümündeki bağlam menüsü ek komutlar da sağlar:

| Komut | Açıklama |
| --- | --- |
| **Sanal ortam ekle** | Projede yeni bir sanal ortam oluşturma işlemi başlar. Bkz. [sanal ortam oluşturma](#create-a-virtual-environment). |
| **Var olan sanal ortamı Ekle** | Sanal ortam içeren bir klasör seçmenizi ve bunu **Python ortamları**altındaki listeye eklememenizi ister, ancak etkinleştirmez. Bkz. [var olan sanal ortamı etkinleştirme](#activate-an-existing-virtual-environment). |
| **Conda ortamı oluşturma** | Ortam için bir ad girdiğiniz ve temel yorumlayıcısını belirten **Python ortamları** *penceresine* geçiş yapar. Bkz. [Conda ortamları](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Bir projenin ortamını değiştirmek için, **Python ortamları** düğümüne sağ tıklayın ve **ortam ekle**' yi seçin veya Python araç çubuğunda ortam açılır listesinden **ortam ekle** ' yi seçin.

**Ortam ekle** iletişim kutusunda, **var olan ortam** sekmesini seçin ve ardından **ortam** açılan listesinden yeni bir ortam seçin:

![Ortam Ekle iletişim kutusunda bir proje ortamı seçme](media/environments/environments-project-2019.png)

Zaten genel varsayılandan farklı bir ortam eklediyseniz, yeni eklenen bir ortamı etkinleştirmeniz gerekebilir. **Python ortamları** düğümünün altında bu ortama sağ tıklayın ve **ortamı etkinleştir**' i seçin. Bir ortamı projeden kaldırmak için **Kaldır**' ı seçin.

![Proje ortamını etkinleştirme ve kaldırma](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Sanal ortamları kullanma

Bir sanal ortam belirli bir Python yorumlayıcısı eşsiz bir bileşimiyle ve diğer genel ve conda ortamları farklı olan belirli bir kümesini kitaplıkları ' dir. Bir sanal ortam, projeye özgü ve proje klasöründe saklanır. Bu klasör, ortamın yüklü kitaplıklarını ve dosya sisteminde başka bir yerde ortamın *temel yorumlayıcısı* yolunu belirten *pyvenv. cfg* dosyasını içerir. (Diğer bir deyişle, bir sanal ortamın bir kopyasını Yorumlayıcı, yalnızca bir bağlantı içermiyor.)

Bir sanal ortam kullanmanın bir avantajı, zaman içinde proje geliştirirken, sanal ortamı her zaman tam proje bağımlılıkları yansıtır ' dir. (Diğer yandan paylaşılan küresel bir ortam, bunları projenizde kullanmanıza bakılmaksızın herhangi bir sayıda kitaplık içerir.) Daha sonra bu bağımlılıkları başka bir geliştirme veya üretim bilgisayarına yeniden yüklemek için kullanılan sanal ortamdan bir *requirements. txt* dosyasını kolayca oluşturabilirsiniz. Daha fazla bilgi için bkz [. requirements. txt ile gerekli paketleri yönetme](managing-required-packages-with-requirements-txt.md).

Visual Studio 'da *requirements. txt* dosyası içeren bir projeyi açtığınızda, Visual Studio otomatik olarak sanal ortamı yeniden oluşturma seçeneğini sağlar. Visual Studio 'Nun yüklü olmadığı bilgisayarlarda, paketleri geri yüklemek için `pip install -r requirements.txt` kullanabilirsiniz.

Sanal bir ortam temel yorumlayıcı için sabit kodlanmış bir yol içerdiğinden ve *gereksinimleri. txt*' yi kullanarak ortamı yeniden oluşturabileceğinden, genellikle kaynak denetiminden tüm sanal ortam klasörünü atlayabilirsiniz.

Aşağıdaki bölümlerde, bir proje var olan bir sanal ortamda etkinleştirme ve yeni bir sanal ortamının nasıl oluşturulacağı açıklanmaktadır.

Visual Studio 'da, bir proje için bir sanal ortam, **Çözüm Gezgini**üzerinde **Python ortamları** düğümü aracılığıyla başka bir şekilde etkinleştirilebilir.

Projenize bir sanal ortam eklendikten sonra, bu, **Python ortamları** penceresinde görünür. Ardından, herhangi bir ortam gibi etkinleştirebilir ve kendi paketleri yönetebilirsiniz.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Sanal ortam oluştur

Visual Studio 'da doğrudan aşağıdaki gibi yeni bir sanal ortam oluşturabilirsiniz:

1. **Çözüm Gezgini** ' de **Python ortamları** ' na sağ tıklayın ve aşağıdaki Iletişim kutusunu gösteren **sanal ortam ekle**' yi seçin:

    ![Bir sanal ortam oluşturma](media/environments/environments-add-virtual-1.png)

1. **Sanal ortam alanının konumunda** , sanal ortam için bir yol belirtin. Yalnızca bir ad belirtirseniz, sanal ortamın içinde bu ada sahip bir alt klasör geçerli projeye oluşturulur.

1. Temel yorumlayıcı olarak bir ortam seçin ve **Oluştur**' u seçin. Visual Studio ortamı yapılandırır ve gerekli tüm paketleri indirir bir ilerleme çubuğu görüntülenir. Tamamlandıktan sonra, sanal ortam, kapsayan proje için **Python ortamları** penceresinde görünür.

1. Sanal ortam varsayılan olarak etkin değildir. Projeyi etkinleştirmek için, sağ tıklayın ve **ortamı etkinleştir**' i seçin.

> [!Note]
> Konum yolu mevcut bir sanal ortamı tanımlarsa, Visual Studio temel yorumlayıcı 'yı otomatik olarak algılar (ortamın *lib* dizinindeki *orig-prefix. txt* dosyasını kullanarak) ve **Oluştur** düğmesini **Ekle**olarak değiştirir.
>
> Bir sanal ortam eklenirken *requirements. txt* dosyası varsa, **sanal ortam ekle** iletişim kutusu paketleri otomatik olarak yüklemek için bir seçenek görüntüler, bu da bir ortamın başka bir bilgisayarda yeniden oluşturulması kolaylaşır:
>
> ![Requirements.txt ile sanal ortam oluştur](media/environments/environments-requirements-txt.png)
>
> Her iki durumda da, **mevcut sanal ortam ekle** komutunu kullanmanız durumunda sonuç aynıdır.

### <a name="activate-an-existing-virtual-environment"></a>Mevcut bir sanal ortam etkinleştir

Bir sanal ortam başka bir yerde zaten oluşturduysanız, proje için şu şekilde etkinleştirebilirsiniz:

1. **Çözüm Gezgini** 'de **Python ortamları** ' na sağ tıklayın ve **var olan sanal ortamı Ekle**' yi seçin.

1. Görüntülenen **gezinme** iletişim kutusunda, öğesine gidin ve sanal ortamı içeren klasörü seçin ve **Tamam**' ı seçin. Visual Studio bu ortamda bir *requirements. txt* dosyası algılarsa, bu paketlerin yüklenip yüklenmeyeceğini sorar.

1. Birkaç dakika sonra, sanal ortam **Çözüm Gezgini**'Daki **Python ortamları** düğümünün altında görüntülenir. Sanal ortam varsayılan olarak etkin değildir, bu nedenle sağ tıklayın ve **ortamı etkinleştir**' i seçin.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Sanal ortam oluştur

Visual Studio 'da doğrudan aşağıdaki gibi yeni bir sanal ortam oluşturabilirsiniz:

1. **Çözüm Gezgini** ' de **Python ortamları** ' na sağ tıklayın ve **ortam ekle**' yi seçin veya Python araç çubuğundaki ortamlar açılan listesinden **ortam ekle** ' yi seçin. Görüntülenen **ortam ekle** Iletişim kutusunda **sanal ortam** sekmesini seçin:

    ![Ortam Ekle iletişim kutusunun sanal ortam sekmesi](media/environments/environments-add-virtual-1-2019.png)

1. Sanal ortam için bir ad belirtin, bir temel yorumlayıcı seçin ve konumunu doğrulayın. **Paketi dosyadan Kur**' un altında, isterseniz *requirements. txt* dosyasının yolunu belirtin.

1. İletişim kutusundaki diğer seçenekleri gözden geçirin:

    | Seçenek | Açıklama |
    | --- | --- |
    | Geçerli ortam olarak ayarla | Ortam oluşturulduktan sonra seçili projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarla | , Visual Studio 'da oluşturulan tüm yeni projelerde sanal ortamı otomatik olarak ayarlar ve etkinleştirir. Bu seçenek kullanıldığında, sanal ortam belirli bir proje dışında bir konuma yerleştirilmelidir.  |
    | Python ortamları penceresinde görüntüle | Ortam oluşturulduktan sonra **Python ortamları** penceresinin açılması gerekip gerekmediğini belirtir. |
    | Bu ortamı küresel olarak kullanılabilir yap | Sanal ortamın aynı zamanda küresel bir ortam görevi yapıp görmediğini belirtir. Bu seçenek kullanıldığında, sanal ortam belirli bir proje dışında bir konuma yerleştirilmelidir. |

1. Sanal ortamı sonlandırmak için **Oluştur** ' u seçin. Visual Studio ortamı yapılandırır ve gerekli tüm paketleri indirir bir ilerleme çubuğu görüntülenir. Tamamlandıktan sonra, sanal ortam etkinleştirilir ve **Çözüm Gezgini** Içindeki **Python ortamları** düğümünde ve kapsayan proje için **Python ortamları** penceresinde görünür.

### <a name="activate-an-existing-virtual-environment"></a>Mevcut bir sanal ortam etkinleştir

Bir sanal ortam başka bir yerde zaten oluşturduysanız, proje için şu şekilde etkinleştirebilirsiniz:

1. **Çözüm Gezgini** 'de **Python ortamları** ' na sağ tıklayın ve **ortam ekle**' yi seçin.

1. Görüntülenen **gezinme** iletişim kutusunda, öğesine gidin ve sanal ortamı içeren klasörü seçin ve **Tamam**' ı seçin. Visual Studio bu ortamda bir *requirements. txt* dosyası algılarsa, bu paketlerin yüklenip yüklenmeyeceğini sorar.

1. Birkaç dakika sonra, sanal ortam **Çözüm Gezgini**'Daki **Python ortamları** düğümünün altında görüntülenir. Sanal ortam varsayılan olarak etkin değildir, bu nedenle sağ tıklayın ve **ortamı etkinleştir**' i seçin.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Bir sanal ortam Kaldır

1. **Çözüm Gezgini**' de sanal ortama sağ tıklayıp **Kaldır**' ı seçin.

1. Visual Studio kaldırın veya sanal ortamın silinmesini ister. **Kaldır** seçildiğinde proje için kullanılamaz hale gelir ancak dosya sisteminde kalır. **Sil** ' i seçtiğinizde, ortam projeden kaldırılır ve dosya sisteminden silinir. Temel yorumlayıcı etkilenmez.

## <a name="view-installed-packages"></a>Paketleri yüklü görüntüle

Çözüm Gezgini'nde hızlı bir şekilde (içeri aktarıp ortamı etkin olduğunda bu paketleri kodunuzu kullanmak anlamına gelir) bu ortamda yüklü paketleri görüntülemek için belirli bir ortamın düğümünü genişletin:

![Çözüm Gezgini'nde bir ortam için Python paketleri](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Yeni paketleri yüklemek için, ortama sağ tıklayın ve Python **ortamları** penceresindeki uygun **paketler** sekmesine geçiş yapmak için **Python paketini yükler** ' i seçin. Bir arama girin (genellikle paket adı) terim ve Visual Studio eşleşen paketleri görüntüler.
::: moniker-end
::: moniker range=">=vs-2019"
Yeni paketleri yüklemek için, ortama sağ tıklayıp Python **paketlerini Yönet** ' i (veya Python araç çubuğundaki paket düğmesini kullanın) seçerek **Python ortamları** penceresindeki uygun **paketler** sekmesine geçin. **Paketler** sekmesinden bir arama terimi (genellikle paket adı) girin ve Visual Studio eşleşen paketleri görüntüler.
::: moniker-end

Visual Studio içinde çoğu ortam için paketler (ve bağımlılıklar), kullanılabilir paketleri de araykabileceğiniz [Python paket dizininden (Pypı)](https://pypi.org)indirilir. Visual Studio'nun durum çubuğu ve çıkış penceresine yükleme hakkında bilgi gösterir. Bir paketi kaldırmak için sağ tıklayın ve **Kaldır**' ı seçin.

Conda Package Manager genellikle varsayılan kanal olarak `https://repo.continuum.io/pkgs/` kullanır, ancak diğer kanallar kullanılabilir. Daha fazla bilgi için bkz. [kanalları yönetme](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.Conda.io).

Görüntülenen girişler her zaman doğru olmayabilir ve yüklenmesi veya kaldırılması güvenilir veya kullanılabilir olmayabilir unutmayın. Visual Studio indirmeleri varsa, pip Paket Yöneticisi'ni kullanır ve gerektiğinde yükler. Visual Studio easy_install Paket Yöneticisi'ni de kullanabilirsiniz. Komut satırından `pip` veya `easy_install` kullanılarak yüklenen paketler de görüntülenir.

Ayrıca, Visual Studio 'Nun paketleri bir Conda ortamına yüklemek için `conda` kullanmayı desteklemediğine de unutmayın. Bunun yerine komut satırından `conda` kullanın.

> [!Tip]
> Bir paketin yüklenemediği yaygın bir durum, paketin *\*. PYD* dosyalarındaki yerel bileşenlere ait kaynak kodu içeruğradığında oluşur. Yüklü Visual Studio gerekli sürümü, bu bileşenlerin pip derlenemiyor. Bu durumda görünen hata iletisi **hata: vcvarsall. bat bulunamıyor**. `easy_install`, önceden derlenmiş ikili dosyaları indirebiliyor ve [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266)Python 'un eski sürümleri için uygun bir derleyici indirebilirsiniz. Daha fazla ayrıntı için bkz. Python araçları ekibi blogu üzerinde ["vcvarsallbat bulunamıyor" sorunuyla ilgili sorun giderme](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) .

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Bağımlılıklar için requirements. txt kullanın](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
