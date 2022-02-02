---
title: Python ortamı seçme
description: Belirli bir projeye uygulamak için Anaconda ve sanal ortamlar dahil olmak üzere bir Python ortamını özel olarak seçebilirsiniz.
ms.date: 01/29/2022
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: e9c2e2f2c1696445cdb7448efa0be24f9a4b008b
ms.sourcegitcommit: 3766c051f9a8b35106b16f751db7fecde0b92254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137951526"
---
# <a name="select-a-python-environment-for-a-project-in-visual-studio"></a>Visual Studio'da bir proje için Python ortamı seçme

Python projesinde yer alan tüm kodlar genel Python ortamı, Anaconda ortamı, sanal ortam veya conda ortamı gibi belirli bir ortam bağlamında çalışır. Visual Studio hata ayıklama, içeri aktarma ve üye tamamlamaları, söz dizimi denetimi ve Python sürümüne özgü dil hizmetleri gerektiren diğer görevler ve yüklü paketler için de bu ortamı kullanır.

Visual Studio'daki tüm yeni Python projeleri başlangıçta, Çözüm Gezgini'daki **Python Ortamları** düğümü altında görünen varsayılan genel ortamı **kullanmak üzere Çözüm Gezgini**:

![Genel varsayılan Python ortamı Çözüm Gezgini](media/environments/environments-project.png)

::: moniker range="vs-2017"
Projenin ortamını değiştirmek için Python Ortamları düğümüne sağ tıklayın ve **Python Ortamları** Ekle **/Kaldır'ı seçin**. Genel, sanal ve conda ortamlarını içeren görüntülenen listeden Python Ortamları düğümü altında görünmesini istediğiniz **tüm ortamları** seçin:

![Python Ortamları Ekle/Kaldır iletişim kutusu](media/environments/environments-add-remove.png)

**Tamam'ı seçtikten** sonra, seçili tüm ortamlar **Python Ortamları düğümü altında** görünür. Şu anda etkinleştirilen ortam kalın olarak görünür:

![Çözüm Gezgini'de birden çok Python Çözüm Gezgini](media/environments/environments-project-multiple.png)

Farklı bir ortamı hızlı bir şekilde etkinleştirmek için bu ortam adına sağ tıklayın ve Ortamı **etkinleştir'i seçin**. Seçiminiz projeyle birlikte kaydedilir ve gelecekte projeyi her açabilirsiniz. Python Ortamları Ekle/Kaldır iletişim kutusundaki **tüm seçenekleri** temizler Visual Studio genel varsayılan ortamı etkinleştirir.

Python Ortamları düğümünde **bağlam menüsü ek** komutlar da sağlar:

| Komut | Açıklama |
| --- | --- |
| **Sanal Ortam Ekleme** | Projede yeni bir sanal ortam oluşturma işlemini başlar. Bkz [. Sanal ortam oluşturma](#create-a-virtual-environment). |
| **Mevcut Sanal Ortamı Ekleme** | Sanal ortam içeren bir klasör seçmenizi ve **Python** Ortamları altındaki listeye eklemenizi ancak etkinleştirmenizi istenir. Bkz [. Mevcut bir sanal ortamı etkinleştirme](#activate-an-existing-virtual-environment). |
| **Conda ortamı oluşturma** | Ortam için bir **ad** *girmeniz ve* temel yorumlayıcısını belirttiğiniz Python Ortamları penceresine geçişler. Bkz [. Conda ortamları](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Projenin ortamını değiştirmek için Python Ortamları düğümüne sağ tıklayın ve **Ortam** **Ekle'yi seçin**. Python araç **çubuğundaki ortam** açılan menüsünden Ortam Ekle'yi de seçin.

Ortam Ekle **iletişim kutusunda** Mevcut ortam sekmesini **ve ardından Ortam** açılan listesinden **yeni bir** ortam seçin:

![Ortam Ekle iletişim kutusunda proje ortamı seçme](media/environments/environments-project-2019.png)

Bir projeye genel varsayılan dışında bir ortam eklediysanız, yeni eklenen bir ortamı etkinleştirmeniz gerekir. Python Ortamları düğümü altında bu ortama sağ **tıklayın ve** Ortamı **Etkinleştir'i seçin**. Projeden bir ortamı kaldırmak için Kaldır'ı **seçin**.

![Proje ortamını etkinleştirme ve kaldırma](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Sanal ortamları kullanma

Sanal ortam, belirli bir Python yorumlayıcının ve diğer genel ve conda ortamlarından farklı olan belirli bir kitaplık kümesiyle benzersiz bir bileşimidir. Sanal ortam bir projeye özgüdür ve proje klasöründe korunur. Bu klasör, ortamın yüklü kitaplıklarını ve dosya sisteminin başka bir yerinde ortamın temel yorumlayıcı yolunu belirten *pyvenv.cfg* dosyasını içerir. (Başka bir ifadeyle, sanal ortam yorumlayıcının bir kopyasını değil, yalnızca bağlantısını içerir.)

Sanal ortam kullanmanın bir avantajı, zaman içinde proje geliştirirken sanal ortamın her zaman projenin tam bağımlılıklarını yansıtmasıdır. (Paylaşılan bir genel ortam, diğer yandan, projesinde kullanıp kullanmamanıza bakarak istediğiniz sayıda kitaplığı içerir.) Daha sonra sanal *ortamdan kolaycarequirements.txt* bir dosya oluşturabilirsiniz. Bu dosya daha sonra bu bağımlılıkları başka bir geliştirme veya üretim bilgisayarına yeniden yüklemek için kullanılır. Daha fazla bilgi için, bkz [. Manage required packages with requirements.txt](managing-required-packages-with-requirements-txt.md).

Bir projeyi bir Visual Studio dosyası içeren bir *requirements.txt* Visual Studio otomatik olarak sanal ortamı yeniden oluşturmanıza izin verir. Yükleme Visual Studio yüklü olmayan bilgisayarlarda, paketleri geri yüklemek `pip install -r requirements.txt` için kullanabilirsiniz.

Bir sanal ortam temel yorumlayıcıya sabit kodlu bir yol içerdiğinden ve *requirements.txt* kullanarak ortamı yeniden oluşturasınız, genellikle kaynak denetiminden sanal ortam klasörünün tamamını atlarsınız.

Aşağıdaki bölümlerde, bir projede var olan bir sanal ortamı etkinleştirme ve yeni bir sanal ortam oluşturma açıklanmaktadır.

Bu Visual Studio, bir proje için bir sanal ortam, sanal makinedeki **Python Ortamları düğümü aracılığıyla** herhangi bir **Çözüm Gezgini**.

Sanal ortam projenize eklendiktan sonra **Python Ortamları penceresinde** görünür. Daha sonra bunu diğer ortamlar gibi etkinleştirebilirsiniz ve paketlerini yönetebilirsiniz.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Sanal ortam oluşturma

Yeni bir sanal ortamı doğrudan aşağıdaki gibi Visual Studio oluşturabilirsiniz:

1. **Çözüm Gezgini'da Python** **Ortamları'Çözüm Gezgini** **sağ tıklayın ve** Aşağıdaki iletişim kutusunu getiren Sanal Ortam Ekle'yi seçin:

    ![Sanal ortam oluşturma](media/environments/environments-add-virtual-1.png)

1. Sanal **ortamın konumu alanında** , sanal ortam için bir yol belirtin. Yalnızca bir ad belirtirsiniz, sanal ortam geçerli proje içinde bu adla bir alt klasör içinde oluşturulur.

1. Temel yorumlayıcı olarak bir ortam seçin ve Oluştur'a **seçin**. Visual Studio ortamı yapılandırırken bir ilerleme çubuğu görüntüler ve gerekli paketleri indirir. Tamamlandıktan sonra sanal ortam, içeren **projenin Python Ortamları** penceresinde görünür.

1. Sanal ortam varsayılan olarak etkinleştirilmez. Projenin sanal ortamını etkinleştirmek için projeye sağ tıklayın ve Ortamı **Etkinleştir'i seçin**.

> [!Note]
> Konum yolu mevcut bir sanal ortamı tanımlarsa Visual Studio yorumlayıcıyı otomatik olarak algılar (ortamın *lib* dizininde *orig-prefix.txt* dosyasını kullanarak) ve Oluştur düğmesini Ekle olarak **değiştirir**.
>
> Sanal *requirements.txt* eklerken bir dosya varsa, Sanal Ortam Ekle iletişim kutusunda paketleri  otomatik olarak yükleme seçeneği görüntülenir ve bu da başka bir bilgisayarda ortamın yeniden oluşturulmasını kolaylaştırır:
>
> ![requirements.txt ile sanal ortam oluşturma](media/environments/environments-requirements-txt.png)
>
> Her iki şekilde de sonuç, Var Olan Sanal Ortamı Ekle **komutunun kullanılmış olmasıyla** aynıdır.

### <a name="activate-an-existing-virtual-environment"></a>Mevcut bir sanal ortamı etkinleştirme

Başka bir yerde zaten sanal ortam oluşturduysanız, bir proje için aşağıdaki gibi etkinleştirebilirsiniz:

1. Çalışma Alanı'Çözüm Gezgini **Python** **Ortamları'Çözüm Gezgini** **Ekle'yi seçin**.

1. Görüntülenen **Gözat** iletişim kutusunda sanal ortamı içeren klasöre gidin, seçin ve Tamam'ı **seçin**. Bu Visual Studio ortamda bir *requirements.txt* dosyası algılarsa, bu paketlerin yük olup olmadığını sorar.

1. Birkaç dakika sonra sanal ortam, **Çözüm Gezgini'daki Python** **Ortamları düğümü altında Çözüm Gezgini**. Sanal ortam varsayılan olarak etkinleştirilmez, bu nedenle sağ tıklayın ve Ortamı **Etkinleştir'i seçin**.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="create-a-virtual-environment"></a>Sanal ortam oluşturma

Yeni bir sanal ortamı doğrudan aşağıdaki gibi Visual Studio oluşturabilirsiniz:

1.  **Çözüm Gezgini'da** **Python** Ortamları'Çözüm Gezgini'e sağ tıklayın ve Ortam Ekle'yi seçin veya Python araç çubuğundaki ortamlar açılan listesinden Ortam Ekle'yi seçin. Görüntülenen **Ortam Ekle** iletişim kutusunda Sanal Ortam **sekmesini** seçin:

    ![Ortam Ekle iletişim kutusunun Sanal ortam sekmesi](media/environments/environments-add-virtual-1-2019.png)

1. Sanal ortam için bir ad belirtin, bir temel yorumlayıcı seçin ve konumunu doğrulayın. **Paketlerden dosyadan yükle** altında, istenirse bir *requirements.txt* dosyasının yolunu sağlar.

1. İletişim kutusundaki diğer seçenekleri gözden geçirme:

    | Seçenek | Açıklama |
    | --- | --- |
    | Geçerli ortam olarak ayarlayın | Ortam oluşturulduktan sonra seçilen projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarlayın | Sanal ortamda oluşturulan tüm yeni projelerde sanal ortamı otomatik olarak ayarlar ve Visual Studio. Bu seçenek kullanırken, sanal ortam belirli bir projenin dışında bir konuma yerleştirilmalıdır.  |
    | Python Ortamlarında Görüntüle penceresi | Ortamı oluşturdukta **Python Ortamları penceresinin açıp** açılmay olmadığını belirtir. |
    | Bu ortamı genel olarak kullanılabilir hale | Sanal ortamın genel ortam olarak da davranıp davranmay olmadığını belirtir. Bu seçenek kullanırken, sanal ortam belirli bir projenin dışında bir konuma yerleştirilmalıdır. |

1. Sanal **ortamı sonleştirmek** için Oluştur'a seçin. Visual Studio ortamı yapılandırırken bir ilerleme çubuğu görüntüler ve gerekli paketleri indirir. Tamamlandıktan sonra, sanal ortam etkinleştirilir ve Çözüm Gezgini **Python** Ortamları düğümünde ve içeren projenin  **Python** Ortamları penceresinde görünür.

### <a name="activate-an-existing-virtual-environment"></a>Mevcut bir sanal ortamı etkinleştirme

Başka bir yerde zaten sanal ortam oluşturduysanız, bir proje için aşağıdaki gibi etkinleştirebilirsiniz:

1. **Çözüm Gezgini'da Python** **Ortamları'Çözüm Gezgini** **Ekle'yi seçin**.

1. Görüntülenen **Gözat** iletişim kutusunda sanal ortamı içeren klasöre gidin, seçin ve Tamam'ı **seçin**. Bu Visual Studio ortamda bir *requirements.txt* dosyası algılarsa, bu paketlerin yük olup olmadığını sorar.

1. Birkaç dakika sonra sanal ortam, **Çözüm Gezgini'daki Python** **Ortamları düğümü altında Çözüm Gezgini**. Sanal ortam varsayılan olarak etkinleştirilmez, bu nedenle sağ tıklayın ve Ortamı **Etkinleştir'i seçin**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Sanal ortamı kaldırma

1. Bu **Çözüm Gezgini** sanal ortama sağ tıklayın ve Kaldır'ı **seçin**.

1. Visual Studio ortamı kaldırmayı veya silmeyi sorar. **Kaldır'ı** seçmek projeyi kullanılamaz hale getirir ancak dosya sisteminde bırakır. Her ikisini **de** sil'i seçmek, ortamı projeden kaldırır ve dosya sisteminden siler. Temel yorumlayıcı etkilenmez.

## <a name="view-installed-packages"></a>Yüklü paketleri görüntüleme

Bu Çözüm Gezgini ortamda yüklü paketleri hızla görüntülemek için belirli bir ortamın düğümünü genişletin (yani, ortam etkin olduğunda bu paketleri içeri aktarabilir ve kodunda kullanabilirsiniz):

![Çözüm Gezgini'de bir ortam için Python paketleri](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Yeni paketleri yüklemek için ortama sağ tıklayın ve **Python** Ortamı penceresinde uygun Paketler sekmesine geçmek için Python **Paketini** **Yükle'yi** seçin. Bir arama terimi (genellikle paket adı) girin ve eşleşen Visual Studio görüntüler.
::: moniker-end
::: moniker range=">=vs-2019"
Yeni paketleri yüklemek için ortama sağ tıklayın ve Python Paketlerini Yönet'i seçin (veya **Python** araç çubuğundaki paket düğmesini kullanın) Python Ortamları penceresinde uygun Paketler **sekmesine** geçiş yapın. Paketler sekmesine **bir** arama terimi (genellikle paket adı) girin ve eşleşen Visual Studio görüntüler.
::: moniker-end

Bu Visual Studio çoğu ortam için paketler (ve bağımlılıklar) [Python Paket Dizini'ne (PyPI)](https://pypi.org) indirilir ve burada kullanılabilir paketleri de arayabilirsiniz. Visual Studio çubuğunda ve çıkış penceresinde yüklemeyle ilgili bilgiler gösterilir. Bir paketi kaldırmak için pakete sağ tıklayın ve Kaldır'ı **seçin**.

Conda paket yöneticisi genellikle varsayılan `https://repo.continuum.io/pkgs/` kanal olarak kullanır, ancak diğer kanallar kullanılabilir. Daha fazla bilgi için bkz [. Kanalları Yönetme](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.conda.io).

Görüntülenen girdilerin her zaman doğru olmadığını ve yükleme ve kaldırmanın güvenilir veya kullanılabilir olmadığının farkında olun. Visual Studio varsa pip paket yöneticisini kullanır ve gerektiğinde indirir ve indirir. Visual Studio paket yöneticisini easy_install kullanabilirsiniz. veya komut satırı kullanılarak `pip` `easy_install` yüklenmiş paketler de görüntülenir.

Ayrıca, Visual Studio conda ortamına paketleri yüklemek `conda` için kullanmayı şu anda desteklememektedir. Bunun `conda` yerine komut satırı kullanın.

> [!Tip]
> Pip'in bir paketi yükleyememe durumu, paketin .pyd dosyalarındaki yerel bileşenler için *\*kaynak kodu dahil olmasıdır* . Gerekli sürüm yüklü Visual Studio pip bu bileşenleri derleyemzamaz. Bu durumda görüntülenen hata iletisi şudur **: Hata: vcvarsall.bat**. `easy_install` genellikle önceden derlenmiş ikili dosyaları indirebilir ve Python'ın eski sürümleri için uygun bir derleyiciyi 'den indirebilirsiniz [https://python.en.uptodown.com/windows/versions](https://python.en.uptodown.com/windows/versions). Diğer ayrıntılar için Python araçları ekip [blog'unda "vcvarsallbat](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) bulunamıyor" ile başa çıkıyoruz.

## <a name="see-also"></a>Ayrıca bkz.

- [Python ortamlarını Visual Studio](managing-python-environments-in-visual-studio.md)
- [Bağımlılıklar requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
