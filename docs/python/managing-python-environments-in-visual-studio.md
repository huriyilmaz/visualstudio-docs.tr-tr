---
title: Python ortamlarını ve yorumlayıcıları yönetme
description: Küresel, sanal ve Conda ortamlarını yönetmek, Python yorumlayıcıları ve paketleri yüklemek ve Visual Studio projelerine ortam atamak için Python ortamları penceresini kullanın.
ms.date: 08/06/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e269e19a09aec157e38eaf8938b5995c2647803
ms.sourcegitcommit: 77ef1dcc71057cd5fdc4733ff0cb6085bd6113e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73661936"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Visual Studio 'da Python ortamları oluşturma ve yönetme

Python *ortamı* , Python kodunu çalıştırdığınız ve genel, sanal ve Conda ortamlarını içeren bir bağlamdır. Bir ortam yorumlayıcı, bir kitaplık (genellikle Python Standart Kitaplığı) ve yüklü paketlerin bir kümesini içerir. Bu bileşenler birlikte hangi dil yapıları ve sözdiziminin geçerli olduğunu, hangi işletim sistemi işlevselliğine erişebileceğinize ve hangi paketlerin kullanılacağını tespit edebilir.

Windows üzerinde Visual Studio 'da, bu makalede açıklandığı gibi, ortamları yönetmek ve yeni projeler için varsayılan değer olarak seçmek üzere **Python ortamları** penceresini kullanırsınız. Ortamların diğer yönleri aşağıdaki makalelerde bulunur:

- Belirli bir proje için, Varsayılanı kullanmak yerine [belirli bir ortamı seçebilirsiniz](selecting-a-python-environment-for-a-project.md) .

- Python projeleri için sanal ortamlar oluşturma ve kullanma hakkında ayrıntılı bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Paketleri bir ortama yüklemek istiyorsanız, [Paketler sekmesi başvurusuna](python-environments-window-tab-reference.md#packages-tab)bakın.

- Başka bir Python yorumlayıcı yüklemek için bkz. [Python yorumlayıcıları 'Nı yüklemek](installing-python-interpreters.md). Genel olarak, bir ana hat Python dağıtımı için bir yükleyici indirip çalıştırırsanız, Visual Studio yeni yüklemenin ve ortamın **Python ortamları** penceresinde göründüğünü algılar ve projeler için seçilebilir.

Visual Studio 'da Python 'a yeni başladıysanız, aşağıdaki makaleler genel arka plandan de sağlanır:

- [Visual Studio 'da Python ile çalışma](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio 'da Python desteği 'ni yükler](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> **Dosya** > **Aç** > **Folder** komutunu kullanarak yalnızca bir klasör olarak açılan Python kodu için ortamları yönetemezsiniz. Bunun yerine, Visual Studio 'nun ortam özelliklerinin tadını çıkarmak için [mevcut koddan bir Python projesi oluşturun](quickstart-01-python-in-visual-studio-project-from-existing-code.md) .
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> **Dosya** > **Aç** > **Folder** komutunu kullanarak bir klasör olarak açılan Python kodu için ortamları yönetebilirsiniz. Python araç çubuğu, algılanan tüm ortamlar arasında geçiş yapmanıza ve ayrıca yeni bir ortam eklemenize olanak tanır. Ortam bilgileri, Workspace. vs klasöründeki PythonSettings. json dosyasında depolanır.
::: moniker-end

## <a name="the-python-environments-window"></a>Python ortamları penceresi

Visual Studio 'Nun hakkında bildiği ortamlar, **Python ortamları** penceresinde görüntülenir. Pencereyi açmak için aşağıdaki yöntemlerden birini kullanın:

-  > **diğer Windows** > **Python ortamlarını** **görüntüle** menü komutunu seçin.
- **Çözüm Gezgini** bir proje Için **Python ortamları** düğümüne sağ tıklayın ve **Tüm Python ortamlarını görüntüle**' yi seçin:

    ::: moniker range="vs-2017"
    ![Çözüm Gezgini tüm ortamları görüntüle komutu](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Çözüm Gezgini tüm ortamları görüntüle komutu](media/environments/environments-view-all-2019.png)
    ::: moniker-end

Her iki durumda da, **Python ortamları** penceresi **Çözüm Gezgini**' nin yanında görünür:

::: moniker range="vs-2017"
![Python ortamları penceresi](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları penceresi](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio, sanal ortamlar ve Conda ortamları (bkz. [ortam türleri](#types-of-environments)) ile birlikte kayıt defteri ( [Pep 514](https://www.python.org/dev/peps/pep-0514/)) kullanarak yüklü genel ortamlara bakar. Listede beklenen bir ortam görmüyorsanız, bkz. [var olan bir ortamı el ile tanımla](#manually-identify-an-existing-environment).

Listede bir ortam seçtiğinizde, Visual Studio **genel bakış** sekmesinde Bu ortam için çeşitli özellikleri ve komutları görüntüler. Örneğin, yukarıdaki resimde yorumlayıcı konumunun *C:\Python36-32*olduğunu görebilirsiniz. **Genel bakış** sekmesinin alt kısmındaki dört komut, yorumlayıcı çalıştıran bir komut istemi açar. Daha fazla bilgi için bkz. [Python ortamları pencere sekmesi başvurusu-genel bakış](python-environments-window-tab-reference.md#overview-tab).

**Paketler**ve **IntelliSense**gibi farklı sekmelere geçiş yapmak için ortamlar listesinin altındaki açılan listeyi kullanın. Bu sekmeler Ayrıca [Python ortamları penceresi sekmesi başvurusu](python-environments-window-tab-reference.md)' nda açıklanmıştır.

Bir ortamın seçilmesi, herhangi bir projeyle ilişkisini değiştirmez. Listede kalýn olarak gösterilen varsayılan ortam, Visual Studio 'nun tüm yeni projeler için kullandığı bir ortamdır. Yeni projelerle farklı bir ortam kullanmak için **bunu yeni projeler için varsayılan ortamı yap** komutunu kullanın. Bir proje bağlamında, her zaman belirli bir ortamı seçebilirsiniz. Daha fazla bilgi için bkz. [proje için ortam seçme](selecting-a-python-environment-for-a-project.md).

Listelenen her ortamın sağında, bu ortam için **etkileşimli** bir pencere açan bir denetimdir. (Visual Studio 2017 15,5 ve önceki sürümlerde, bu ortam için IntelliSense veritabanını yenileyen bir denetim görüntülenir. Veritabanı hakkındaki ayrıntılar için bkz. [ortamlar pencere sekmesi başvurusu](python-environments-window-tab-reference.md) .)

::: moniker range="vs-2017"
> [!Tip]
> **Python ortamları** penceresini yeterince genişlettikten sonra, ile çalışmanın daha uygun olduğunu bulabileceğiniz ortamlarınızın daha ayrıntılı bir görünümünü alırsınız.
>
> ![Python ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> **Python ortamları** penceresini yeterince genişlettikten sonra, ile çalışmanın daha uygun olduğunu bulabileceğiniz ortamlarınızın daha ayrıntılı bir görünümünü alırsınız.
>
> ![Python ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Visual Studio, sistem-site-paketleri seçeneğine uyar, ancak bu, Visual Studio içinden değiştirmek için bir yol sağlamaz.

### <a name="what-if-no-environments-appear"></a>Ortam görünmezse ne olacak?

Hiçbir ortam görünmezse, Visual Studio 'Nun standart konumlarda hiçbir Python yüklemesini algılayamadığı anlamına gelir. Örneğin, Visual Studio 2017 veya üstünü yüklemiş olabilirsiniz ancak Python iş yükünün yükleyici seçeneklerinde tüm yorumlayıcı seçeneklerini temizlemiş olabilirsiniz. Benzer şekilde, Visual Studio 2015 veya önceki bir sürümünü yüklemiş olabilirsiniz ancak bir yorumlayıcı el ile yüklenmeyebilirsiniz (bkz. [Python yorumlayıcıları yükleme](installing-python-interpreters.md)).

Bilgisayarınızda bir Python yorumlayıcı olduğunu bildiğiniz halde Visual Studio (herhangi bir sürüm) bunu algılayamadığından, konumunu el ile belirtmek için **+ Custom** komutunu kullanın. [Mevcut bir ortamı el ile tanımlamak](#manually-identify-an-existing-environment)için sonraki bölüme bakın.

> [!Tip]
> Visual Studio, python.org ' den yükleyicileri kullanarak Python 2.7.11 'i özelleştirme 'i 2.7.14 'e yükseltmek gibi mevcut bir yorumlayıcıya yönelik güncelleştirmeleri algılar. Yükleme işlemi sırasında, eski ortam, güncelleştirme yerinde görüntülenmeden önce **Python ortamları** listesinden kaybolur.
>
> Ancak, dosya sistemini kullanarak bir yorumlayıcı ve ortamını el ile taşırsanız, Visual Studio yeni konumu bilmez. Daha fazla bilgi için bkz. [yorumlayıcı taşıma](installing-python-interpreters.md#move-an-interpreter).

### <a name="types-of-environments"></a>Ortam türleri

Visual Studio, genel, sanal ve Conda ortamları ile çalışabilir.

#### <a name="global-environments"></a>Küresel ortamlar

Her Python yüklemesi (örneğin, Python 2,7, Python 3,6, Python 3,7, Anaconda 4.4.0 vb., bkz. [Python yorumlayıcıları yükleme](installing-python-interpreters.md)) kendi *genel ortamını*saklar. Her ortam, belirli bir Python yorumlayıcı, standart kitaplığı, önceden yüklenmiş bir paket kümesi ve bu ortam etkinleştirilirken yüklediğiniz diğer paketlerin oluşur. Bir paketin küresel bir ortama yüklenmesi, bu ortamı kullanan tüm projeler tarafından kullanılabilmesini sağlar. Ortam, dosya sisteminin korumalı bir alanında bulunuyorsa (örneğin, *c:\Program Files*içinde), paket yükleme için yönetici ayrıcalıkları gerekir.

Küresel ortamlar bilgisayardaki tüm projeler için kullanılabilir. Visual Studio 'da, özel olarak bir proje için farklı bir tane seçmediğiniz sürece tüm projeler için kullanılan varsayılan olarak bir genel ortam seçersiniz. Daha fazla bilgi için bkz. [proje için ortam seçme](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Sanal ortamlar

, Genel bir ortamda çalışmaya başlamak için kolay bir yoldur, ancak zaman içinde bu ortam, farklı projeler için yüklediğiniz birçok farklı paket ile karışık hale gelir. Bu tür dağınıklığı, bir uygulamayı bilinen sürümlere sahip belirli bir paket kümesine karşı test etmek zorlaştırır. Bu, bir yapı sunucusunda veya Web sunucusunda ayarlamış olduğunuz ortam türüdür. İki proje aynı paketin uyumsuz paketlerini veya farklı sürümlerini gerektirdiğinde, çakışmalar da oluşabilir.

Bu nedenle, geliştiriciler genellikle proje için bir *sanal ortam* oluşturur. Sanal ortam, belirli bir yorumlayıcının kopyasını içeren bir projedeki alt klasördür. Sanal ortamı etkinleştirdiğinizde, yüklediğiniz tüm paketler yalnızca o ortamın alt klasörüne yüklenir. Daha sonra bu ortam içinde bir Python programı çalıştırdığınızda, bu belirli paketlere karşı çalıştığını bilirsiniz.

Visual Studio, bir proje için sanal ortam oluşturmaya yönelik doğrudan destek sağlar. Örneğin, *requirements. txt*içeren bir projeyi açar veya bu dosyayı içeren bir şablondan proje oluşturursanız, Visual Studio otomatik olarak bir sanal ortam oluşturmanızı ve bu bağımlılıkları yüklemenizi ister.

Açık bir proje içinde dilediğiniz zaman yeni bir sanal ortam oluşturabilirsiniz. **Çözüm Gezgini**, proje düğümünü genişletin, **Python ortamları**' na sağ tıklayın ve "sanal ortam ekle" seçeneğini belirleyin. Daha fazla bilgi için bkz. [sanal ortam oluşturma](/visualstudio/python/selecting-a-python-environment-for-a-project?view=vs-2019#create-a-virtual-environment-1).

Visual Studio aynı zamanda bir sanal ortamdan *requirements. txt* dosyası oluşturmak için bir komut sağlar, bu da ortamı diğer bilgisayarlarda yeniden oluşturmayı kolaylaştırır. Daha fazla bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Conda ortamları

Conda ortamı, `conda` Aracı kullanılarak veya Visual Studio 2017 sürüm 15,7 ve üzeri sürümlerde tümleşik Conda Management ile oluşturulmuş bir ortamdır. (Visual Studio yükleyicisi aracılığıyla kullanılabilen Anaconda veya Miniconda gerektirir, bkz. [yükleme](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017).)

::: moniker range="vs-2017"

1. **Yeni bir Conda ortamı oluştur** sekmesi açan **Python ortamları** penceresinde **+ Conda ortamı oluştur** ' u seçin:

    ![Yeni bir Conda ortamı için sekme oluştur](media/environments/environments-conda-1.png)

1. **Ad** alanına ortam için bir ad girin, **Python** alanında bir temel Python yorumlayıcı seçin ve **Oluştur**' u seçin.

1. **Çıkış** penceresinde, oluşturma işlemi tamamlandıktan sonra bazı CLI yönergeleriyle yeni ortam için ilerleme durumu gösterilir:

    ![Conda ortamının başarıyla oluşturulması](media/environments/environments-conda-2.png)

1. Visual Studio içinde, bir proje için bir [ortam seçin](selecting-a-python-environment-for-a-project.md)bölümünde açıklandığı gibi, bir proje için Conda ortamını etkinleştirebilirsiniz.

1. Ortama paket yüklemek için [paketler sekmesini](python-environments-window-tab-reference.md#packages-tab)kullanın.
::: moniker-end

::: moniker range=">=vs-2019"

1. **Python ortamları** penceresinde (veya Python araç çubuğundan), **ortam ekle** Iletişim kutusunu açan **+ ortam ekle** ' yi seçin. Bu iletişim kutusunda **Conda ortamı** sekmesini seçin:

    ![Ortam Ekle iletişim kutusunda Conda ortamı sekmesi](media/environments/environments-conda-1-2019.png)

1. Aşağıdaki alanları yapılandırın:

    | Alan | Açıklama |
    | --- | --- |
    | Project | Ortamın oluşturulacağı proje (aynı Visual Studio çözümünde birden çok projeniz varsa). |
    | Name | Conda ortamının adı. |
    | Paket ekle | Bağımlılıklarınızı tanımlayan bir *Environment. yıml* dosyanız varsa **ortam dosyası** ' nı seçin veya **bir veya daha fazla Anaconda paketi adı** seçin ve en az bir Python paketi veya aşağıdaki alanda bir Python sürümü listeleyin. Paket listesi, Conda 'ın Python ortamı oluşturmasını söyler. Python 'un en son sürümünü yüklemek için `python`kullanın; belirli bir sürümü yüklemek için `python=3.7`olarak `python=,major>.<minor>` kullanın. Ayrıca, bir dizi menüden Python sürümlerini ve ortak paketleri seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarla | Ortam oluşturulduktan sonra seçili projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarla | , Conda ortamını Visual Studio 'da oluşturulan tüm yeni projelerde otomatik olarak ayarlar ve etkinleştirir. Bu seçenek, **Python ortamları** penceresinde **yeni projeler için bu varsayılan ortamı yap** ' ın kullanılmasıyla aynıdır. |
    | Python ortamları penceresinde görüntüle | Ortamı oluşturduktan sonra **Python ortamları** penceresinin gösterilip gösterilmeyeceğini belirtir. |

    > [!Important]
    > Bir Conda ortamı oluştururken, `environments.yml` veya paket listesini kullanarak, ortamın bir Python çalışma zamanı içerdiğinden emin olmak için en az bir Python sürümü ya da Python paketi belirttiğinizden emin olun. Aksi halde, Visual Studio ortamı yoksayar: ortam, **Python ortamları** penceresinde hiçbir yerde görünmez, bir proje için geçerli ortam olarak ayarlanmamış ve genel bir ortam olarak kullanılamaz.
    >
    > Python sürümü olmadan bir Conda ortamı oluşturursanız, Conda ortam klasörlerinin konumlarını görmek için `conda info` komutunu kullanın, sonra ortamın alt klasörünü bu konumdan el ile kaldırın.

1. **Oluştur**' u seçin ve **Çıkış** penceresinde ilerlemeyi gözlemleyin. Çıktı, oluşturma işlemi tamamlandıktan sonra birkaç CLı yönergesi içerir:

    ![Conda ortamının başarıyla oluşturulması](media/environments/environments-conda-2-2019.png)

1. Visual Studio içinde, bir proje için bir [ortam seçin](selecting-a-python-environment-for-a-project.md)bölümünde açıklandığı gibi, bir proje için Conda ortamını etkinleştirebilirsiniz.

1. Ortama ek paketler yüklemek için [paketler sekmesini](python-environments-window-tab-reference.md#packages-tab)kullanın.
::: moniker-end

> [!Note]
> Conda ortamlarındaki en iyi sonuçları elde etmek için Conda 4.4.8 veya üstünü kullanın (Conda sürümleri, Anaconda sürümlerinden farklıdır). Visual Studio yükleyicisi aracılığıyla uygun Miniconda (Visual Studio 2019) ve Anaconda (Visual Studio 2017) sürümlerini yükleyebilirsiniz.

Conda ortamlarının depolandığı Conda sürümünü ve diğer bilgileri görmek için, bir Anaconda komut isteminde `conda info` çalıştırın (yani, Anaconda 'nın yolda bulunduğu bir komut istemi):

```cli
conda info
```

Conda ortam klasörleriniz şu şekilde görünür:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Conda ortamları bir proje ile depolanmadığından, küresel ortamlara benzer şekilde davranır. Örneğin, bir Conda ortamına yeni bir paket yüklemek, bu paketin bu ortamı kullanan tüm projeler tarafından kullanılabilmesini sağlar.

Visual Studio 2017 sürüm 15,6 ve önceki sürümlerde, [var olan bir ortamı el ile tanımlamak](#manually-identify-an-existing-environment)altında açıklandığı şekilde bu ortamları el ile göstererek Conda ortamlarını kullanabilirsiniz.

Visual Studio 2017 sürüm 15,7 ve üzeri, Conda ortamlarını otomatik olarak algılar ve bunları bir sonraki bölümde açıklandığı gibi **Python ortamları** penceresinde görüntüler.

## <a name="manually-identify-an-existing-environment"></a>Mevcut bir ortamı el ile tanımla

Standart olmayan bir konumda yüklü olan bir ortamı (Visual Studio 2017 sürüm 15,6 ve önceki sürümleri dahil) belirlemek için aşağıdaki adımları kullanın:

::: moniker range="vs-2017"

1. **Yapılandırma** sekmesini açan **Python ortamları** penceresinde **+ özel** ' i seçin:

    ![Yeni bir özel ortam için varsayılan görünüm](media/environments/environments-custom-1.png)

1. **Açıklama** alanına ortam için bir ad girin.

1. **Önek yolu** alanındaki yorumlayıcı yolunun yolunu ( **.** ..) girin veya buraya gidin.

1. Visual Studio, bu konumda bir Python yorumlayıcı algılarsa (bir Conda ortamı için aşağıda gösterilen yol gibi), **Otomatik Algıla** komutu etkinleştirilir. **Otomatik algılamayı** seçmek kalan alanları tamamlar. Ayrıca, bu alanları el ile de tamamlayabilirsiniz.

    ![Auto Detect komutunu etkinleştirme](media/environments/environments-custom-2.png)

    ![Otomatik Algıla kullanıldıktan sonra ortam alanlarını tamamlama](media/environments/environments-custom-3.png)

1. Alanlar istediğiniz değerleri içeriyorsa, yapılandırmayı kaydetmek için **Uygula** ' yı seçin. Artık ortamı, Visual Studio içinde başka herhangi bir gibi kullanabilirsiniz.

1. El ile tanımlanmış bir ortamı kaldırmanız gerekiyorsa, **Yapılandır** sekmesinde **Kaldır** komutunu seçin. otomatik algılanan ortamlar bu seçeneği sağlamaz. Daha fazla bilgi için bkz. [Configure Tab](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. **Python ortamları** penceresinde (veya Python araç çubuğundan), **ortam ekle** Iletişim kutusunu açan **+ ortam ekle** ' yi seçin. Bu iletişim kutusunda, **var olan ortam** sekmesini seçin:

    ![Ortam Ekle iletişim kutusunda var olan ortam sekmesi](media/environments/environments-custom-1-2019.png)

1. **Ortam** açılan öğesini seçin ve ardından **özel**' i seçin:

    ![Ortam Ekle iletişim kutusunda özel ortam seçeneği](media/environments/environments-custom-2-2019.png)

1. İletişim kutusundaki belirtilen alanlarda, diğer alanların çoğunu dolduran **ön ek yolu**altındaki yorumlayıcı yoluna ( **.** ..) girin veya bu yolu inceleyin. Bu değerleri inceledikten ve gerektiğinde değiştirdikten sonra **Ekle**' yi seçin. 

    ![Ortam Ekle iletişim kutusunda özel ortam seçeneğinin ayrıntılarını belirtme alanları](media/environments/environments-custom-3-2019.png)

1. Ortam ayrıntıları, **Python ortamları** penceresinde herhangi bir zamanda incelenebilir ve değiştirilebilir. Bu pencerede, ortamı seçin ve ardından **Yapılandır** sekmesini seçin. Değişiklik yaptıktan sonra **Uygula** komutunu seçin. Ayrıca **Remove** komutunu kullanarak ortamı kaldırabilirsiniz (otomatik algılanan ortamlar için kullanılamaz). Daha fazla bilgi için bkz. [Configure Tab](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Geçersiz ortamları çözme veya silme

Visual Studio bir ortam için kayıt defteri girişleri bulursa, ancak yorumlayıcı yolu geçersizse, **Python ortamları** penceresi adı bir üstü çizili yazı tipiyle gösterir:

::: moniker range="vs-2017"
![Geçersiz bir ortamı gösteren Python ortamları penceresi](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Geçersiz bir ortamı gösteren Python ortamları penceresi](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Tutmak istediğiniz bir ortamı düzeltmek için öncelikle yükleyicinin **onarma** işlemini kullanmayı deneyin. Standart Python 3. x yükleyicileri, örneğin, bu seçeneği içerir.

Onarma seçeneği olmayan bir ortamı düzeltmek veya geçersiz bir ortamı kaldırmak için, kayıt defterini doğrudan değiştirmek için aşağıdaki adımları kullanın. Kayıt defterinde değişiklik yaptığınızda Visual Studio, **Python ortamları** penceresini otomatik olarak güncelleştirir.

1. *Regedit. exe*' yi çalıştırın.
1. **HKEY_LOCAL_MACHINE\SOFTWARE\Python**adresine gidin. IronPython için, bunun yerine **IronPython** öğesini arayın.
1. Anaconda için, Cpyıthon veya **Continuumanalytics** Için **Python Core** gibi dağıtımla eşleşen düğümü genişletin. IronPython için sürüm numarası düğümünü genişletin.
1. **InstallPath** düğümünün altındaki değerleri inceleyin:

    ![Tipik bir Cpne Thon yüklemesi için kayıt defteri girişleri](media/environments/environments-registry-entries.png)

    - Ortam bilgisayarınızda hala mevcutsa, **ExecutablePath** değerini doğru konum olarak değiştirin. Ayrıca, **(varsayılan)** ve **WindowedExecutablePath** değerlerini gereken şekilde düzeltin.
    - Ortam bilgisayarınızda artık yoksa ve **Python ortamları** penceresinden kaldırmak istiyorsanız, yukarıdaki görüntüde **3,6** gibi **InstallPath**'in üst düğümünü silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Python yorumlayıcılarını yükleme](installing-python-interpreters.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements. txt kullanın](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
