---
title: Python ortamı seçin
description: Belirli bir projeye uygulamak için, özel olarak, Anaconda ve sanal ortamları dahil olmak üzere bir Python ortamı seçebilirsiniz.
ms.date: 03/18/2019
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 6a906a69d581b0632c35baed548a52f9a8f3eb77
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135806319"
---
# <a name="select-a-python-environment-for-a-project-in-visual-studio"></a>Visual Studio bir proje için Python ortamı seçin

Bir Python projesindeki tüm kod, genel Python ortamı, Anaconda ortamı, sanal ortam veya Conda ortamı gibi belirli bir ortamın bağlamı içinde çalışır. Visual Studio ayrıca bu ortamı hata ayıklama, içeri aktarma ve üye tamamlamalar, sözdizimi denetimi ve Python sürümüne özgü dil hizmetleri gerektiren diğer görevler ve yüklü paketler kümesi için de kullanır.

Visual Studio ' deki tüm yeni Python projeleri, başlangıçta **Çözüm Gezgini**' deki **Python ortamları** düğümü altında görünen varsayılan genel ortamı kullanacak şekilde yapılandırılmıştır:

![Çözüm Gezgini gösterildiği genel varsayılan Python ortamı](media/environments/environments-project.png)

::: moniker range="vs-2017"
Bir projenin ortamını değiştirmek için, **Python ortamları** düğümüne sağ tıklayın ve **Python ortamlarını Ekle/Kaldır**' ı seçin. Genel, sanal ve Conda ortamlarını içeren görüntülenen listeden, **Python ortamları** düğümü altında görünmesini istediklerinizi seçin:

![Python ortamları Ekle/Kaldır iletişim kutusu](media/environments/environments-add-remove.png)

**Tamam**' ı seçtiğinizde, seçilen tüm ortamlar **Python ortamları** düğümünün altında görünür. Etkin durumda olan ortam kalın görünür:

![Çözüm Gezgini gösterildiği birden çok Python ortamı](media/environments/environments-project-multiple.png)

Farklı bir ortamı hızlıca etkinleştirmek için, bu ortam adına sağ tıklayın ve **ortamı etkinleştir**' i seçin. Seçiminiz proje ile kaydedilir ve projeyi gelecekte açtığınızda bu ortam etkinleştirilir. **Python ortamlarını ekle/kaldır** iletişim kutusundaki tüm seçenekleri temizlerseniz, Visual Studio genel varsayılan ortamı etkinleştirir.

**Python ortamları** düğümündeki bağlam menüsü ek komutlar da sağlar:

| Komut | Açıklama |
| --- | --- |
| **Sanal ortam ekle** | Projede yeni bir sanal ortam oluşturma işlemini başlatır. Bkz. [sanal ortam oluşturma](#create-a-virtual-environment). |
| **Var olan sanal ortamı Ekle** | Sanal ortam içeren bir klasör seçmenizi ve bunu **Python ortamları** altındaki listeye eklememenizi ister, ancak etkinleştirmez. Bkz. [var olan sanal ortamı etkinleştirme](#activate-an-existing-virtual-environment). |
| **Conda ortamı oluşturma** | Ortam için bir ad girdiğiniz ve temel yorumlayıcısını belirten **Python ortamları** *penceresine* geçiş yapar. Bkz. [Conda ortamları](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Bir projenin ortamını değiştirmek için, **Python ortamları** düğümüne sağ tıklayın ve **ortam ekle**' yi seçin. Ayrıca, Python araç çubuğunda ortam açılır listesinden **ortam Ekle ' yi** de seçebilirsiniz.

**Ortam ekle** iletişim kutusunda, **var olan ortam** sekmesini seçin ve ardından **ortam** açılan listesinden yeni bir ortam seçin:

![Ortam Ekle iletişim kutusunda bir proje ortamı seçme](media/environments/environments-project-2019.png)

Zaten genel varsayılandan farklı bir ortam eklediyseniz, yeni eklenen bir ortamı etkinleştirmeniz gerekebilir. **Python ortamları** düğümünün altında bu ortama sağ tıklayın ve **ortamı etkinleştir**' i seçin. Bir ortamı projeden kaldırmak için **Kaldır**' ı seçin.

![Proje ortamını etkinleştirme ve kaldırma](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Sanal ortamları kullanma

Sanal ortam, belirli bir Python yorumlayıcısının ve diğer genel ve Conda ortamlarından farklı olan belirli bir kitaplık kümesinin benzersiz bir birleşimidir. Bir sanal ortam, bir projeye özeldir ve proje klasöründe tutulur. Bu klasör, ortamın yüklü kitaplıklarını ve dosya sisteminde başka bir yerde ortamın *temel yorumlayıcısı* yolunu belirten *pyvenv. cfg* dosyasını içerir. (Diğer bir deyişle, bir sanal ortam yorumlayıcı bir kopyasını içermez, yalnızca bir bağlantısını içerir.)

Sanal ortam kullanmanın bir avantajı, zaman içinde proje geliştirdikçe, sanal ortamın her zaman projenin tam bağımlılıklarını yansıttığıdır. (Diğer yandan paylaşılan küresel bir ortam, bunları projenizde kullanmanıza bakılmaksızın herhangi bir sayıda kitaplık içerir.) Daha sonra bu bağımlılıkları başka bir geliştirme veya üretim bilgisayarına yeniden yüklemek için kullanılan sanal ortamdan kolayca bir *requirements.txt* dosyası oluşturabilirsiniz. Daha fazla bilgi için bkz. [requirements.txtgereken paketleri yönetme ](managing-required-packages-with-requirements-txt.md).

bir *requirements.txt* dosyası içeren Visual Studio bir proje açtığınızda, Visual Studio otomatik olarak sanal ortamı yeniden oluşturma seçeneğini sunar. Visual Studio yüklü olmadığı bilgisayarlarda, `pip install -r requirements.txt` paketleri geri yüklemek için kullanabilirsiniz.

Sanal bir ortam temel yorumlayıcı için sabit kodlanmış bir yol içerdiğinden ve *requirements.txt* kullanarak ortamı yeniden oluşturabileceğinden, genellikle kaynak denetiminden tüm sanal ortam klasörünü atlayabilirsiniz.

Aşağıdaki bölümlerde, bir projede var olan bir sanal ortamın nasıl etkinleştirileceği ve yeni bir sanal ortamın nasıl oluşturulacağı açıklanmaktadır.

Visual Studio, bir sanal ortam, bir proje için, **Çözüm Gezgini** **Python ortamları** düğümü aracılığıyla başka bir şekilde etkinleştirilebilir.

Projenize bir sanal ortam eklendikten sonra, bu, **Python ortamları** penceresinde görünür. Daha sonra bunu başka bir ortam gibi etkinleştirebilir ve paketleri yönetebilirsiniz.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Sanal ortam oluşturma

Visual Studio doğrudan aşağıdaki gibi yeni bir sanal ortam oluşturabilirsiniz:

1. **Çözüm Gezgini** ' de **Python ortamları** ' na sağ tıklayın ve aşağıdaki Iletişim kutusunu gösteren **sanal ortam ekle**' yi seçin:

    ![Sanal ortam oluşturma](media/environments/environments-add-virtual-1.png)

1. **Sanal ortam alanının konumunda** , sanal ortam için bir yol belirtin. Yalnızca bir ad belirtirseniz, sanal ortam geçerli proje içinde bu ada sahip bir alt klasörde oluşturulur.

1. Temel yorumlayıcı olarak bir ortam seçin ve **Oluştur**' u seçin. Visual Studio, ortamı yapılandırırken bir ilerleme çubuğu gösterir ve gerekli paketleri indirir. Tamamlandıktan sonra, sanal ortam, kapsayan proje için **Python ortamları** penceresinde görünür.

1. Sanal ortam varsayılan olarak etkinleştirilmez. Projenin sanal ortamını etkinleştirmek için, sağ tıklayın ve **ortamı etkinleştir**' i seçin.

> [!Note]
> konum yolu mevcut bir sanal ortamı tanımlarsa, Visual Studio taban yorumlayıcı otomatik olarak algılar (ortamın *lib* dizinindeki *orig-prefix.txt* dosyasını kullanarak) ve **oluştur** düğmesini **ekle** olarak değiştirir.
>
> Bir sanal ortam eklenirken bir *requirements.txt* dosyası varsa, **sanal ortam ekle** iletişim kutusu paketleri otomatik olarak yüklemek için bir seçenek görüntüler, bu da bir ortamın başka bir bilgisayarda yeniden oluşturulması kolaylaşır:
>
> ![requirements.txt ile sanal ortam oluşturma](media/environments/environments-requirements-txt.png)
>
> Her iki durumda da, **mevcut sanal ortam ekle** komutunu kullanmanız durumunda sonuç aynıdır.

### <a name="activate-an-existing-virtual-environment"></a>Mevcut bir sanal ortamı etkinleştir

Başka bir yerde zaten bir sanal ortam oluşturduysanız, bunu bir proje için aşağıdaki şekilde etkinleştirebilirsiniz:

1. **Çözüm Gezgini** 'de **Python ortamları** ' na sağ tıklayın ve **var olan sanal ortamı Ekle**' yi seçin.

1. Görüntülenen **gezinme** iletişim kutusunda, öğesine gidin ve sanal ortamı içeren klasörü seçin ve **Tamam**' ı seçin. Visual Studio bu ortamda *requirements.txt* bir dosya algılarsa, bu paketlerin yüklenip yüklenmediğini sorar.

1. Birkaç dakika sonra, sanal ortam **Çözüm Gezgini**'Daki **Python ortamları** düğümünün altında görüntülenir. Sanal ortam varsayılan olarak etkin değildir, bu nedenle sağ tıklayın ve **ortamı etkinleştir**' i seçin.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Sanal ortam oluşturma

Visual Studio doğrudan aşağıdaki gibi yeni bir sanal ortam oluşturabilirsiniz:

1. **Çözüm Gezgini** ' de **Python ortamları** ' na sağ tıklayın ve **ortam ekle**' yi seçin veya Python araç çubuğundaki ortamlar açılan listesinden **ortam ekle** ' yi seçin. Görüntülenen **ortam ekle** Iletişim kutusunda **sanal ortam** sekmesini seçin:

    ![Ortam Ekle iletişim kutusunun sanal ortam sekmesi](media/environments/environments-add-virtual-1-2019.png)

1. Sanal ortam için bir ad belirtin, bir temel yorumlayıcı seçin ve konumunu doğrulayın. **Paketi dosyadan Kur**' un altında, istenirse *requirements.txt* bir dosyanın yolunu belirtin.

1. İletişim kutusundaki diğer seçenekleri gözden geçirin:

    | Seçenek | Açıklama |
    | --- | --- |
    | Geçerli ortam olarak ayarla | Ortam oluşturulduktan sonra seçili projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarla | , Visual Studio oluşturulan tüm yeni projelerde sanal ortamı otomatik olarak ayarlar ve etkinleştirir. Bu seçenek kullanıldığında, sanal ortam belirli bir proje dışında bir konuma yerleştirilmelidir.  |
    | Python ortamları penceresinde görüntüle | Ortam oluşturulduktan sonra **Python ortamları** penceresinin açılması gerekip gerekmediğini belirtir. |
    | Bu ortamı küresel olarak kullanılabilir yap | Sanal ortamın aynı zamanda küresel bir ortam görevi yapıp görmediğini belirtir. Bu seçenek kullanıldığında, sanal ortam belirli bir proje dışında bir konuma yerleştirilmelidir. |

1. Sanal ortamı sonlandırmak için **Oluştur** ' u seçin. Visual Studio, ortamı yapılandırırken bir ilerleme çubuğu gösterir ve gerekli paketleri indirir. Tamamlandıktan sonra, sanal ortam etkinleştirilir ve **Çözüm Gezgini** Içindeki **Python ortamları** düğümünde ve kapsayan proje için **Python ortamları** penceresinde görünür.

### <a name="activate-an-existing-virtual-environment"></a>Mevcut bir sanal ortamı etkinleştir

Başka bir yerde zaten bir sanal ortam oluşturduysanız, bunu bir proje için aşağıdaki şekilde etkinleştirebilirsiniz:

1. **Çözüm Gezgini** 'de **Python ortamları** ' na sağ tıklayın ve **ortam ekle**' yi seçin.

1. Görüntülenen **gezinme** iletişim kutusunda, öğesine gidin ve sanal ortamı içeren klasörü seçin ve **Tamam**' ı seçin. Bu Visual Studio ortamda bir *requirements.txt* dosyası algılarsa, bu paketlerin yük olup olmadığını sorar.

1. Birkaç dakika sonra sanal ortam, içinde Python Ortamları düğümü **altında** **Çözüm Gezgini.** Sanal ortam varsayılan olarak etkinleştirilmez, bu nedenle sağ tıklayın ve Ortamı **Etkinleştir'i seçin.**
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Sanal ortamı kaldırma

1. Sanal **Çözüm Gezgini** sağ tıklayın ve Kaldır'ı **seçin.**

1. Visual Studio ortamı kaldırmayı veya silmeyi sorar. **Kaldır'ı** seçmek projeyi kullanılamaz hale getirir ancak dosya sisteminde bırakır. Her ikisini **de** sil'i seçmek, ortamı projeden kaldırır ve dosya sisteminden siler. Temel yorumlayıcı etkilenmez.

## <a name="view-installed-packages"></a>Yüklü paketleri görüntüleme

Bu Çözüm Gezgini ortamda yüklü paketleri hızla görüntülemek için belirli bir ortamın düğümünü genişletin (ortam etkin olduğunda bu paketleri içeri aktarabilir ve kodunda kullanabilirsiniz):

![Çözüm Gezgini'de bir ortam için Python paketleri](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Yeni paketleri yüklemek için ortama sağ tıklayın ve Python Ortamı penceresinde uygun Paketler sekmesine geçmek için **Python** **Paketini** **Yükle'yi** seçin. Bir arama terimi (genellikle paket adı) girin ve eşleşen Visual Studio görüntüler.
::: moniker-end
::: moniker range=">=vs-2019"
Yeni paketleri yüklemek için ortama sağ tıklayın ve Python Paketlerini Yönet'i seçin (veya **Python**  araç çubuğundaki paket düğmesini kullanın) Python Ortamları penceresinde uygun Paketler **sekmesine** geçiş yapın. Paketler sekmesine **bir** arama terimi (genellikle paket adı) girin ve eşleşen Visual Studio görüntüler.
::: moniker-end

Bu Visual Studio ortamlara ait paketler (ve bağımlılıklar) [Python Paket Dizini'ne (PyPI)](https://pypi.org)indirilir ve burada kullanılabilir paketleri de arayabilirsiniz. Visual Studio çubuğunda ve çıkış penceresinde yüklemeyle ilgili bilgiler gösterilir. Bir paketi kaldırmak için pakete sağ tıklayın ve **Kaldır'ı seçin.**

Conda paket yöneticisi genellikle varsayılan `https://repo.continuum.io/pkgs/` kanal olarak kullanır, ancak diğer kanallar kullanılabilir. Daha fazla bilgi için [bkz. Kanalları Yönetme](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.conda.io).

Görüntülenen girdilerin her zaman doğru olmadığını ve yükleme ve kaldırmanın güvenilir veya kullanılabilir olmadığının farkında olun. Visual Studio varsa pip paket yöneticisini kullanır ve gerektiğinde indirir ve indirir. Visual Studio paket yöneticisini easy_install kullanabilirsiniz. veya komut satırı `pip` kullanılarak yüklenmiş paketler de `easy_install` görüntülenir.

Ayrıca, Visual Studio conda ortamına paketleri yüklemek için kullanmanın şu `conda` anda destekçi olmadığını unutmayın. Bunun `conda` yerine komut satırı kullanın.

> [!Tip]
> Pip'in bir paketi yükleyememe durumu, paketin *\* .pyd* dosyalarındaki yerel bileşenler için kaynak kodu dahil olmasıdır. Gerekli sürüm yüklü Visual Studio pip bu bileşenleri derleyemzamaz. Bu durumda görüntülenen hata iletisi **şudur: Hata: vcvarsall.bat.** `easy_install` genellikle önceden derlenmiş ikili dosyaları indirebilir ve Python'ın eski sürümleri için uygun bir derleyiciyi 'den [https://python.en.uptodown.com/windows/versions](https://python.en.uptodown.com/windows/versions) indirebilirsiniz. Diğer ayrıntılar için Python araçları ekip blog'unda ["vcvarsallbat bulunamıyor"](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) ile başa çıkıyoruz.

## <a name="see-also"></a>Ayrıca bkz.

- [Python ortamlarını Visual Studio](managing-python-environments-in-visual-studio.md)
- [Bağımlılıklar requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
