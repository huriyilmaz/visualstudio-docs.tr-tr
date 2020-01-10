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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848420"
---
# <a name="how-to-select-a-python-environment-for-a-project"></a>Nasıl bir proje için bir Python ortamı seçin

Bir global Python ortamı, Anaconda ortamı, bir sanal ortam ya da conda ortamı gibi belirli bir ortama bağlamında bir Python projesindeki tüm kod çalıştırır. Visual Studio bu ortamda hata ayıklama, içeri aktarma ve üye tamamlama, sözdizimi denetimi ve Python sürümü ve yüklü paketleri birtakım özel dil hizmetleri gerektiren herhangi bir görev için de kullanır.

Tüm yeni Python projeleri Visual Studio'da ilk altında görüntülenen varsayılan genel ortam kullanmak üzere yapılandırılmış **Python ortamları** düğümünde **Çözüm Gezgini**:

![Çözüm Gezgini'nde gösterilen genel varsayılan Python ortamı](media/environments/environments-project.png)

::: moniker range="vs-2017"
Bir proje için ortamı değiştirmek için sağ **Python ortamları** düğümünü seçip alt **Ekle/Kaldır Python ortamları**. Conda ortamları altında görüntülenmesini istediğiniz tüm sürücüler seçin ve görüntülenen listeden hangi içerir genel, sanal **Python ortamları** düğüm:

![Python ortamları Ekle/Kaldır iletişim kutusu](media/environments/environments-add-remove.png)

Seçtiğinizde **Tamam**, seçilen tüm ortamlara altında görünür **Python ortamları** düğümü. Şu anda etkin ortam kalın yazı tipinde görünür:

![Çözüm Gezgini'nde birden çok Python ortamları](media/environments/environments-project-multiple.png)

Hızlı bir şekilde farklı bir ortama etkinleştirmek için bu ortam adını sağ tıklatın ve seçin **etkinleştirme ortam**. Seçtiğiniz proje ile kaydedilir ve proje gelecekte açtığınızda bu ortamda etkinleştirilir. Tüm seçenekleri işaretini kaldırırsanız **Ekle/Kaldır Python ortamları** iletişim kutusunda, Visual Studio genel varsayılan ortam etkinleştirir.

Bağlam menüsünde **Python ortamları** düğüm ayrıca ek komutlar sağlar:

| Komut | Açıklama |
| --- | --- |
| **Sanal ortam Ekle** | Projede yeni bir sanal ortam oluşturma işlemi başlar. Bkz: [sanal ortam Oluştur](#create-a-virtual-environment). |
| **Var olan sanal ortama Ekle** | Bir sanal ortam içeren bir klasör seçmenizi ister ve altındaki listeye ekler **Python ortamları**, ancak etkinleştirmez. Bkz: [var olan bir sanal ortam etkinleştirme](#activate-an-existing-virtual-environment). |
| **Conda ortamı oluşturma** | Ağınızdan **Python ortamları** *penceresi* , ortam için bir ad girin ve kendi temel yorumlayıcı belirtin. Bkz: [Conda ortamları](managing-python-environments-in-visual-studio.md#conda-environments). |
::: moniker-end

::: moniker range=">=vs-2019"
Bir projenin ortamını değiştirmek için, **Python ortamları** düğümüne sağ tıklayın ve **ortam ekle**' yi seçin veya Python araç çubuğunda ortam açılır listesinden **ortam ekle** ' yi seçin.

**Ortam ekle** iletişim kutusunda, **var olan ortam** sekmesini seçin ve ardından **ortam** açılan listesinden yeni bir ortam seçin:

![Ortam Ekle iletişim kutusunda bir proje ortamı seçme](media/environments/environments-project-2019.png)

Zaten genel varsayılandan farklı bir ortam eklediyseniz, yeni eklenen bir ortamı etkinleştirmeniz gerekebilir. **Python ortamları** düğümünün altında bu ortama sağ tıklayın ve **ortamı etkinleştir**' i seçin. Bir ortamı projeden kaldırmak için **Kaldır**' ı seçin.

![Proje ortamını etkinleştirme ve kaldırma](media/environments/environments-project-add-remove-2019.png)
::: moniker-end

## <a name="use-virtual-environments"></a>Sanal ortamları kullanma

Bir sanal ortam belirli bir Python yorumlayıcısı eşsiz bir bileşimiyle ve diğer genel ve conda ortamları farklı olan belirli bir kümesini kitaplıkları ' dir. Bir sanal ortam, projeye özgü ve proje klasöründe saklanır. Ortamının yüklü kitaplıkları ile birlikte bu klasörde bir *pyvenv.cfg* ortamın yolunu belirtir dosya *temel yorumlayıcı* dosya sistemindeki başka bir yerde. (Diğer bir deyişle, bir sanal ortamın bir kopyasını Yorumlayıcı, yalnızca bir bağlantı içermiyor.)

Bir sanal ortam kullanmanın bir avantajı, zaman içinde proje geliştirirken, sanal ortamı her zaman tam proje bağımlılıkları yansıtır ' dir. (Diğer yandan paylaşılan küresel bir ortam, bunları projenizde kullanmanıza bakılmaksızın herhangi bir sayıda kitaplık içerir.) Daha sonra bu bağımlılıkları başka bir geliştirme veya üretim bilgisayarına yeniden yüklemek için kullanılan sanal ortamdan bir *requirements. txt* dosyasını kolayca oluşturabilirsiniz. Daha fazla bilgi için [requirements.txt ile gerekli paketleri yönetme](managing-required-packages-with-requirements-txt.md).

Visual Studio'da içeren bir proje açtığınızda, bir *requirements.txt* dosya, Visual Studio otomatik olarak sanal ortam yeniden oluşturmak için seçeneği size sunar. Visual Studio'nun yüklü olmayan bilgisayarlarda kullanabilirsiniz `pip install -r requirements.txt` paketlerini geri yüklemek için.

Bir sanal ortam için temel yorumlayıcı sabit kodlanmış bir yol içerdiğinden ve ortam kullanarak yeniden oluşturabilirsiniz *requirements.txt*, genellikle kaynak denetiminden tüm sanal ortamın klasöre çıkarın.

Aşağıdaki bölümlerde, bir proje var olan bir sanal ortamda etkinleştirme ve yeni bir sanal ortamının nasıl oluşturulacağı açıklanmaktadır.

Visual Studio'da gibi başka bir proje için bir sanal ortam etkinleştirilebilmesi için **Python ortamları** düğümünde **Çözüm Gezgini**.

Bir sanal ortam projenize eklendikten sonra görünür **Python ortamları** penceresi. Ardından, herhangi bir ortam gibi etkinleştirebilir ve kendi paketleri yönetebilirsiniz.

::: moniker range="vs-2017"
### <a name="create-a-virtual-environment"></a>Sanal ortam oluştur

Visual Studio 'da doğrudan aşağıdaki gibi yeni bir sanal ortam oluşturabilirsiniz:

1. Sağ **Python ortamları** içinde **Çözüm Gezgini** seçip **sanal ortama ekleme**, aşağıdaki iletişim kutusunu getirir:

    ![Bir sanal ortam oluşturma](media/environments/environments-add-virtual-1.png)

1. İçinde **sanal ortam konumunu** alanında, sanal ortam için bir yol belirtin. Yalnızca bir ad belirtirseniz, sanal ortamın içinde bu ada sahip bir alt klasör geçerli projeye oluşturulur.

1. Temel yorumlayıcı bir ortam seçin ve seçin **Oluştur**. Visual Studio ortamı yapılandırır ve gerekli tüm paketleri indirir bir ilerleme çubuğu görüntülenir. Tamamlandıktan sonra, sanal ortam, kapsayan proje için **Python ortamları** penceresinde görünür.

1. Sanal ortam varsayılan olarak etkin değildir. Proje için etkinleştirmek için sağ tıklatın ve seçin **etkinleştirme ortam**.

> [!Note]
> Konumu yolu mevcut bir sanal ortam tanımlıyorsa, Visual Studio temel yorumlayıcı otomatik olarak algılar (kullanarak *ORIG prefix.txt* ortamın dosyasında *LIB* dizini) ve değişiklikleri **Oluştur** düğmesi **Ekle**.
>
> Varsa bir *requirements.txt* dosyası mevcut bir sanal ortamda eklerken **sanal ortama ekleme** iletişim kutusunu görüntüler paketleri otomatik olarak yüklemek için bir seçenek yeniden oluşturmayı kolaylaştıran bir ortam başka bir bilgisayarda:
>
> ![Requirements.txt ile sanal ortam oluştur](media/environments/environments-requirements-txt.png)
>
> Senaryosuyla her iki durumda da aynı sonucudur **var olan sanal ortama ekleme** komutu.

### <a name="activate-an-existing-virtual-environment"></a>Mevcut bir sanal ortam etkinleştir

Bir sanal ortam başka bir yerde zaten oluşturduysanız, proje için şu şekilde etkinleştirebilirsiniz:

1. Sağ **Python ortamları** içinde **Çözüm Gezgini** seçip **var olan sanal ortama ekleme**.

1. İçinde **Gözat** görüntülenen iletişim gidin ve sanal ortam içeren klasörü seçin ve **Tamam**. Visual Studio algılarsa bir *requirements.txt* dosya o ortamda, bu paketleri yüklenip yüklenmeyeceğini ister.

1. Birkaç dakika sonra sanal ortamı altında görünür. **Python ortamları** düğümünde **Çözüm Gezgini**. Sanal ortam varsayılan olarak etkin değildir, bu nedenle sağ tıklayın ve seçin **etkinleştirme ortam**.
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

1. İçinde **Gözat** görüntülenen iletişim gidin ve sanal ortam içeren klasörü seçin ve **Tamam**. Visual Studio algılarsa bir *requirements.txt* dosya o ortamda, bu paketleri yüklenip yüklenmeyeceğini ister.

1. Birkaç dakika sonra sanal ortamı altında görünür. **Python ortamları** düğümünde **Çözüm Gezgini**. Sanal ortam varsayılan olarak etkin değildir, bu nedenle sağ tıklayın ve seçin **etkinleştirme ortam**.
::: moniker-end

### <a name="remove-a-virtual-environment"></a>Bir sanal ortam Kaldır

1. İçinde **Çözüm Gezgini**, sanal ortama sağ tıklayıp **Kaldır**.

1. Visual Studio kaldırın veya sanal ortamın silinmesini ister. Seçme **Kaldır** projeye kullanılamaz duruma getirir, ancak dosya sisteminde bırakır. Seçme **Sil** hem ortamı projeden kaldırır ve dosya sisteminden siler. Temel yorumlayıcı etkilenmez.

## <a name="view-installed-packages"></a>Paketleri yüklü görüntüle

Çözüm Gezgini'nde hızlı bir şekilde (içeri aktarıp ortamı etkin olduğunda bu paketleri kodunuzu kullanmak anlamına gelir) bu ortamda yüklü paketleri görüntülemek için belirli bir ortamın düğümünü genişletin:

![Çözüm Gezgini'nde bir ortam için Python paketleri](media/environments/environments-installed-packages.png)

::: moniker range="vs-2017"
Yeni paketleri yüklemek için, ortama sağ tıklayın ve Python **ortamları** penceresindeki uygun **paketler** sekmesine geçiş yapmak için **Python paketini yükler** ' i seçin. Bir arama girin (genellikle paket adı) terim ve Visual Studio eşleşen paketleri görüntüler.
::: moniker-end
::: moniker range=">=vs-2019"
Yeni paketleri yüklemek için, ortama sağ tıklayıp Python **paketlerini Yönet** ' i (veya Python araç çubuğundaki paket düğmesini kullanın) seçerek **Python ortamları** penceresindeki uygun **paketler** sekmesine geçin. **Paketler** sekmesinden bir arama terimi (genellikle paket adı) girin ve Visual Studio eşleşen paketleri görüntüler.
::: moniker-end

Visual Studio içinde çoğu ortam için paketler (ve bağımlılıklar), kullanılabilir paketleri de araykabileceğiniz [Python paket dizininden (Pypı)](https://pypi.org)indirilir. Visual Studio'nun durum çubuğu ve çıkış penceresine yükleme hakkında bilgi gösterir. Bir paketi kaldırmak için sağ tıklayın ve seçin **Kaldır**.

Conda Package Manager genellikle varsayılan kanal olarak `https://repo.continuum.io/pkgs/` kullanır, ancak diğer kanallar kullanılabilir. Daha fazla bilgi için bkz. [kanalları yönetme](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-channels.html) (docs.Conda.io).

Görüntülenen girişler her zaman doğru olmayabilir ve yüklenmesi veya kaldırılması güvenilir veya kullanılabilir olmayabilir unutmayın. Visual Studio indirmeleri varsa, pip Paket Yöneticisi'ni kullanır ve gerektiğinde yükler. Visual Studio easy_install Paket Yöneticisi'ni de kullanabilirsiniz. Kullanarak yüklü paketleri `pip` veya `easy_install` komut satırından da görüntülenir.

Ayrıca Visual Studio kullanarak şu anda desteklemiyor Not `conda` conda ortamına paketlerini yükleyin. Kullanım `conda` komut satır yerine.

> [!Tip]
> Paket, kaynak kodu yerel bileşenlerin içerir. burada pip başarısız bir paketi yüklemek için ortak bir durum olduğunda  *\*.pyd* dosyaları. Yüklü Visual Studio gerekli sürümü, bu bileşenlerin pip derlenemiyor. Bu durumda görüntülenen hata iletisi **hata: vcvarsall.bat bulunamıyor**. `easy_install` önceden derlenmiş ikili dosyaları, genellikle indirebildiğini Python'dan eski sürümlerine yönelik bir uygun derleyici indirebilirsiniz [ https://www.microsoft.com/download/details.aspx?id=44266 ](https://www.microsoft.com/download/details.aspx?id=44266). Daha fazla ayrıntı için ["vcvarsallbat bulmak alınamıyor", sorunlu ile nasıl](https://devblogs.microsoft.com/python/unable-to-find-vcvarsall-bat/) üzerinde Python araçları ekip blogu.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Bağımlılıklar için Requirements.txt dosyasını kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
