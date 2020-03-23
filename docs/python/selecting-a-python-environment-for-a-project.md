---
title: Bir proje için bir Python yorumlayıcısı ve ortamı seçin
description: Belirli bir projeye uygulamak için Anaconda ve sanal ortamlar da dahil olmak üzere bir Python ortamını özellikle seçebilirsiniz.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302730"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Proje için Python ortamı nasıl seçilir?

Python projesindeki tüm kodlar, genel Python ortamı, Anaconda ortamı, sanal ortam veya conda ortamı gibi belirli bir ortam bağlamında çalışır. Visual Studio ayrıca hata ayıklama, alma ve üye tamamlamaları, sözdizimi denetimi ve Python sürümüne ve yüklü paketler kümesine özgü dil hizmetleri gerektiren diğer görevler için de bu ortamı kullanır.

Visual Studio'daki tüm yeni Python projeleri başlangıçta **Solution Explorer'daki** **Python Ortamları** düğümü altında görünen varsayılan genel ortamı kullanacak şekilde yapılandırılmıştır:

![Çözüm Gezgini'nde gösterilen genel varsayılan Python ortamı](media/environments/environments-project.png)

::: moniker range="vs-2017"
Projenin ortamını değiştirmek için **Python Ortamları** düğümüne sağ tıklayın ve **Python Ortamlarını Ekle/Kaldır'ı**seçin. Genel, sanal ve conda ortamlarını içeren görüntülenen listeden Python **Ortamları** düğümü altında görünmesini istediğiniz tüm lerini seçin:

![Python Ortamları ekleme/Kaldırma iletişim kutusu](media/environments/environments-add-remove.png)

**Tamam'ı**seçtikten sonra, seçilen tüm ortamlar **Python Ortamları** düğümünün altında görünür. Şu anda etkinleştirilen ortam kalın görünür:

![Çözüm Gezgini'nde gösterilen birden çok Python ortamı](media/environments/environments-project-multiple.png)

Farklı bir ortamı hızlı bir şekilde etkinleştirmek için, bu ortam adını sağ tıklatın ve **ortamı etkinleştir'i**seçin. Seçiminiz projeyle birlikte kaydedilir ve gelecekte projeyi her açtığınızda bu ortam etkinleştirilir. **Python Ortamları Ekle/Kaldır** iletişim kutusundaki tüm seçenekleri temizlerseniz, Visual Studio genel varsayılan ortamı etkinleştirir.

**Python Ortamları** düğümündeki bağlam menüsü de ek komutlar sağlar:

| Komut | Açıklama |
| --- | --- |
| **Sanal Ortam Ekle** | Projede yeni bir sanal ortam oluşturma işlemini başlatır. Bkz. [Sanal ortam oluşturma](#create-a-virtual-environment). |
| **Varolan Sanal Ortam Ekle** | Sanal ortam içeren bir klasör seçmenizi ister ve **Python Ortamları**altındaki listeye ekler, ancak etkinleştirmez. Bkz. [Varolan sanal ortamı etkinleştir.](#activate-an-existing-virtual-environment) |
| **Conda ortamı oluşturma** | Ortam için bir ad girdiğiniz **python ortamları** *penceresine* geçer ve temel yorumlayıcısını belirtir. [Bkz. Conda ortamları.](managing-python-environments-in-visual-studio.md#conda-environments) |
::: moniker-end

::: moniker range=">=vs-2019"
Projenin ortamını değiştirmek için **Python Ortamları** düğümüne sağ tıklayın ve **Çevre Ekle'yi**seçin veya Python araç çubuğundaki ortamdan **Ortam** Ekle'yi seçin.

**Ortam Ekle** iletişim kutusuna girdiğinde, **Varolan Ortam** sekmesini seçin ve ardından **Çevre** açılır listesinden yeni bir ortam seçin:

![Ortam Ekle iletişim kutusunda proje ortamı seçme](media/environments/environments-project-2019.png)

Bir projeye genel varsayılan dışında bir ortam eklediyseniz, yeni eklenen bir ortamı etkinleştirmeniz gerekebilir. **Python Ortamları** düğümünün altındaki ortama sağ tıklayın ve **Ortamı Etkinleştir'i**seçin. Bir ortamı projeden kaldırmak için **Kaldır'ı**seçin.

![Proje ortamını etkinleştirme ve kaldırma](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Sanal ortamları kullanma

Sanal ortam, belirli bir Python yorumlayıcısı ve diğer genel ve conda ortamlarından farklı belirli bir kitaplık kümesinin benzersiz bir birleşimidir. Sanal ortam projeye özgüdür ve proje klasöründe tutulur. Bu klasör, dosya sisteminde başka bir yerde ortamın *temel yorumlayıcısına* giden yolu belirten bir *pyvenv.cfg* dosyasıyla birlikte ortamın yüklü kitaplıklarını içerir. (Diğer bir şey, sanal bir ortam yorumlayıcının bir kopyasını içermez, yalnızca ona bir bağlantı içerir.)

Sanal ortamı kullanmanın bir yararı, zaman içinde proje geliştirdikçe, sanal ortamın her zaman projenin tam bağımlılıklarını yansıtmasıdır. (Diğer taraftan, paylaşılan bir genel ortam, projenizde kullansanız da kullanmasanız da istediğiniz sayıda kitaplık içerir.) Daha sonra kolayca başka bir geliştirme veya üretim bilgisayarında bu bağımlılıkları yeniden yüklemek için kullanılan sanal ortamdan bir *requirements.txt* dosyası oluşturabilirsiniz. Daha fazla bilgi için [gereksinimleri.txt ile gerekli paketleri yönet'e](managing-required-packages-with-requirements-txt.md)bakın.

Visual Studio'da *gereksinimler.txt* dosyası içeren bir proje açtığınızda, Visual Studio size otomatik olarak sanal ortamı yeniden oluşturma seçeneği sunar. Visual Studio'nun yüklü olmadığı bilgisayarlarda paketleri `pip install -r requirements.txt` geri yüklemek için kullanabilirsiniz.

Sanal ortam temel yorumlayıcıya sabit kodlanmış bir yol içerdiğinden ve *gereksinimleri.txt*kullanarak ortamı yeniden oluşturabildiğiniziçin, genellikle tüm sanal ortam klasörünü kaynak denetiminden atlarsınız.

Aşağıdaki bölümlerde, projede varolan bir sanal ortamın nasıl etkinleştirilen ve yeni bir sanal ortamın nasıl oluşturulabildiğini açıklayınız.

Visual Studio'da, **Solution Explorer'daki** **Python Ortamları** düğümü aracılığıyla diğer projeler gibi bir proje için sanal ortam etkinleştirilebilir.

Projenize sanal bir ortam eklendikten sonra **Python Ortamları** penceresinde görünür. Daha sonra herhangi bir diğer ortam gibi etkinleştirebilirsiniz ve paketleri yönetebilirsiniz.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Sanal ortam oluşturma

Doğrudan Visual Studio'da aşağıdaki gibi yeni bir sanal ortam oluşturabilirsiniz:

1. **Solution Explorer'da** **Python Ortamları'na** sağ tıklayın ve aşağıdaki iletişim kutusunu oluşturan **Sanal Ortam Ekle'yi**seçin:

    ![Sanal ortam oluşturma](media/environments/environments-add-virtual-1.png)

1. Sanal **ortam alanının konumunda,** sanal ortam için bir yol belirtin. Yalnızca bir ad belirtirseniz, sanal ortam geçerli proje içinde bu ada sahip bir alt klasörde oluşturulur.

1. Temel yorumlayıcı olarak bir ortam seçin ve **Oluştur'u**seçin. Visual Studio, ortamı yapılandırırken ve gerekli paketleri indirirken bir ilerleme çubuğu görüntüler. Tamamlandıktan sonra, sanal ortam içeren proje için **Python Ortamları** penceresinde görünür.

1. Sanal ortam varsayılan olarak etkinleştirilmez. Proje için etkinleştirmek için sağ tıklatın ve **Ortamı Etkinleştir'i**seçin.

> [!Note]
> Konum yolu varolan sanal ortamı tanımlıyorsa, Visual Studio temel yorumlayıcıyı otomatik olarak algılar (ortamın *lib* dizinindeki *orig-önek.txt* dosyasını kullanarak) ve **Ekle**düğmesini **oluştur** düğmesini değiştirir.
>
> Sanal ortam eklerken *bir requirements.txt* dosyası varsa, **Sanal Ortam Ekle** iletişim kutusu paketleri otomatik olarak yükleme seçeneği görüntüler ve bu da başka bir bilgisayarda ortamı yeniden oluşturmayı kolaylaştırır:
>
> ![requirements.txt ile sanal ortam oluşturma](media/environments/environments-requirements-txt.png)
>
> Her iki şekilde de, sonuç **Varolan Sanal Ortam Ekle** komutunu kullanmış gibi aynıdır.

### <a name="activate-an-existing-virtual-environment"></a>Varolan sanal ortamı etkinleştirme

Başka bir yerde sanal bir ortam oluşturduysanız, proje için aşağıdaki gibi etkinleştirebilirsiniz:

1. **Solution Explorer'da** **Python Ortamları'na** sağ tıklayın ve **Varolan Sanal Ortam Ekle'yi**seçin.

1. Görünen **Gözat** iletişim kutusunda, sanal ortamı içeren klasöre gidin ve seçin ve **Tamam'ı**seçin. Visual Studio bu ortamda bir *requirements.txt* dosyası algılarsa, bu paketleri yükleyip yüklemememi ister.

1. Birkaç dakika sonra, sanal ortam Solution **Explorer'da Python Ortamlar** düğümüaltında görünür. **Solution Explorer** Sanal ortam varsayılan olarak etkinleştirilmez, bu nedenle sağ tıklatın ve **Ortamı Etkinleştir'i**seçin.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Sanal ortam oluşturma

Doğrudan Visual Studio'da aşağıdaki gibi yeni bir sanal ortam oluşturabilirsiniz:

1. **Solution Explorer'da** **Python Ortamları'nı** sağ tıklatın ve **Ortam Ekle'yi**seçin veya Python araç çubuğundaki ortamlar listesinden **Ortam Ekle'yi** seçin. Görünen **Çevre Ekle** iletişim kutusunda Sanal **Ortam** sekmesini seçin:

    ![Çevre Ekle iletişim kutusunun sanal ortam sekmesi](media/environments/environments-add-virtual-1-2019.png)

1. Sanal ortam için bir ad belirtin, bir temel yorumlayıcı seçin ve konumunu doğrulayın. **Dosyadan Paketleri Yükle**altında, istenirse *bir requirements.txt* dosyasına giden yolu sağlayın.

1. İletişim kutusundaki diğer seçenekleri gözden geçirin:

    | Seçenek | Açıklama |
    | --- | --- |
    | Geçerli ortam olarak ayarlayın | Ortam oluşturulduktan sonra seçili projedeki yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarlayın | Visual Studio'da oluşturulan tüm yeni projelerde sanal ortamı otomatik olarak ayarlar ve etkinleştirir. Bu seçeneği kullanırken, sanal ortam belirli bir projenin dışındaki bir konuma yerleştirilmelidir.  |
    | Python Ortamları penceresinde görünüm | Ortamı oluşturduktan sonra **Python Ortamları** penceresini açıp açmayacağını belirtir. |
    | Bu ortamı küresel olarak kullanılabilir hale getirin | Sanal ortamın da küresel bir ortam olarak hareket edip etmediğini belirtir. Bu seçeneği kullanırken, sanal ortam belirli bir projenin dışındaki bir konuma yerleştirilmelidir. |

1. Sanal ortamı sonuçlandırmak için **Oluştur'u** seçin. Visual Studio, ortamı yapılandırırken ve gerekli paketleri indirirken bir ilerleme çubuğu görüntüler. Tamamlandıktan sonra, sanal ortam etkinleştirilir ve **Solution Explorer'daki** **Python Ortamları** düğümünde ve içeren proje için **Python Ortamları** penceresinde görünür.

### <a name="activate-an-existing-virtual-environment"></a>Varolan sanal ortamı etkinleştirme

Başka bir yerde sanal bir ortam oluşturduysanız, proje için aşağıdaki gibi etkinleştirebilirsiniz:

1. **Solution Explorer'da** **Python Ortamları'na** sağ tıklayın ve **Ortam Ekle'yi**seçin.

1. Görünen **Gözat** iletişim kutusunda, sanal ortamı içeren klasöre gidin ve seçin ve **Tamam'ı**seçin. Visual Studio bu ortamda bir *requirements.txt* dosyası algılarsa, bu paketleri yükleyip yüklemememi ister.

1. Birkaç dakika sonra, sanal ortam Solution **Explorer'da Python Ortamlar** düğümüaltında görünür. **Solution Explorer** Sanal ortam varsayılan olarak etkinleştirilmez, bu nedenle sağ tıklatın ve **Ortamı Etkinleştir'i**seçin.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Sanal ortamı kaldırma

1. **Çözüm Gezgini'nde,** sanal ortama sağ tıklayın ve **Kaldır'ı**seçin.

1. Visual Studio sanal ortamı kaldırmak veya silmek ister sorar. **Kaldır'ı** seçmek proje için kullanılamaz hale getirir, ancak dosya sisteminde bırakır. **Sil'i** seçmek hem ortamı projeden kaldırır hem de dosya sisteminden siler. Temel tercüman etkilenmez.

## <a name="view-installed-packages"></a>Yüklü paketleri görüntüleme

Çözüm Gezgini'nde, o ortamda yüklü olan paketleri hızla görüntülemek için belirli bir ortamın düğümlerini genişletin (ortam etkinken bu paketleri kodunuzda içe aktarıp kullanabileceğiniz anlamına gelir):

![Solution Explorer'da bir ortam için Python paketleri](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Yeni paketler yüklemek için ortama sağ tıklayın ve **Python Ortamları** penceresindeuygun **Paketler** sekmesine geçmek için **Python Paketini Yükle'yi** seçin. Bir arama terimi (genellikle paket adı) girin ve Visual Studio eşleşen paketleri görüntüler.
::: moniker-end
::: moniker range=">=vs-2019"
Yeni paketler yüklemek için ortama sağ tıklayın ve **Python Ortamları** penceresindeki uygun **Paketler** sekmesine geçmek için **Python Paketlerini Yönet'i** (veya Python araç çubuğundaki paket düğmesini kullanın) seçin. **Paketler** sekmesine girdikten sonra, bir arama terimi (genellikle paket adı) girin ve Visual Studio eşleşen paketleri görüntüler.
::: moniker-end

Visual Studio içinde, çoğu ortam için paketler (ve [bağımlılıklar) python paket dizini (PyPI)](https://pypi.org)indirilir, burada da kullanılabilir paketleri arayabilirsiniz. Visual Studio'nun durum çubuğu ve çıkış penceresi yükleme yle ilgili bilgileri gösterir. Bir paketi kaldırmak için, sağ tıklatın ve **Kaldır'ı**seçin.

Conda paket yöneticisi genellikle `https://repo.continuum.io/pkgs/` varsayılan kanal olarak kullanır, ancak diğer kanallar kullanılabilir. Daha fazla bilgi için [Kanalları Yönet](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.conda.io) bölümüne bakın.

Görüntülenen girişlerin her zaman doğru olmayabileceğini ve yükleme ve yüklemenin artık güvenilir veya kullanılabilir olmayabileceğini unutmayın. Visual Studio varsa pip paket yöneticisini kullanır ve gerektiğinde indirir ve yükler. Visual Studio da easy_install paket yöneticisi kullanabilirsiniz. Komut satırı `pip` kullanılarak `easy_install` veya komut satırından yüklenen paketler de görüntülenir.

Ayrıca Visual Studio'nun paketleri bir `conda` conda ortamına yüklemek için kullanmayı şu anda desteklemediğini de unutmayın. Bunun `conda` yerine komut satırından kullanın.

> [!Tip]
> Pip'in bir paketi yükleyemediği yaygın bir durum, paketin * \*.pyd* dosyalarında yerel bileşenler için kaynak kodu eklemesidir. Visual Studio'nun gerekli sürümü yüklenmeden pip bu bileşenleri derleyemez. Bu durumda görüntülenen hata iletisi **hatadır: vcvarsall.bat bulamıyorum.** `easy_install`genellikle önceden derlenmiş ikilileri indirebilir ve Python'un eski sürümleri için uygun [https://www.microsoft.com/download/details.aspx?id=44266](https://www.microsoft.com/download/details.aspx?id=44266)bir derleyiciyi . Daha fazla bilgi için Python araçları ekibi blogunda ["vcvarsallbat bulamıyor" acısıyla nasıl başa çıkılacağı](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Bağımlılıklar için requirements.txt kullanın](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
