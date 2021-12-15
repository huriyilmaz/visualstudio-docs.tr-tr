---
title: Python ortamlarını ve yorumlayıcıları yönetme
description: Genel, sanal ve Conda ortamlarını yönetmek için Python ortamları penceresini kullanın. Python yorumlayıcıları ve paketleri yükleyip Visual Studio projelerine ortamlar atayın.
ms.date: 12/11/2021
ms.customL: devdivchpfy22
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: a3b82b65d5991a6606ad4894786bbda199b1ca17
ms.sourcegitcommit: 04fb8ba0f7ea73ba17baa88f10563c8600e7fd7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "135121572"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Visual Studio 'da Python ortamları oluşturma ve yönetme

**Python ortamı** , Python kodunu çalıştırdığınız ve genel, sanal ve Conda ortamlarını içeren bir bağlamdır. Bir ortam yorumlayıcı, bir kitaplık (genellikle Python Standart Kitaplığı) ve yüklü paketlerin bir kümesini içerir. Bu bileşenler, geçerli dil yapılarını ve sözdizimini, erişebileceğiniz işletim sistemi işlevselliğini ve kullanabileceğiniz paketleri bir araya getirebilirsiniz.

Windows üzerinde Visual Studio, bu makalede açıklandığı gibi, ortamları yönetmek ve yeni projeler için varsayılan değer olarak seçmek için **Python ortamları** penceresini kullanın. Ortamların diğer yönleri aşağıdaki makalelerde bulunur:

- Belirli bir proje için, Varsayılanı kullanmak yerine [belirli bir ortamı seçebilirsiniz](selecting-a-python-environment-for-a-project.md) .

- Python projeleri için sanal ortamlar oluşturma ve kullanma hakkında ayrıntılı bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

- Paketleri bir ortama yüklemek istiyorsanız, [Paketler sekmesi başvurusuna](python-environments-window-tab-reference.md#packages-tab)bakın.

- Başka bir Python yorumlayıcı yüklemek için bkz. [Python yorumlayıcıları 'Nı yüklemek](installing-python-interpreters.md). genel olarak, bir ana hat Python dağıtımı için yükleyici indirip çalıştırırsanız, Visual Studio yeni yüklemenin ve ortamın **Python ortamları** penceresinde göründüğünü algılar ve projeler için seçilebilir.

Visual Studio 'de Python 'a yeni başladıysanız, aşağıdaki makaleler genel arka plandan de sağlanır:

- [Visual Studio 'de Python ile çalışma](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio’da Python desteğini yükleme](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> **Dosya**  >  **Aç**  >  **klasörü** komutunu kullanarak yalnızca bir klasör olarak açılan Python kodu için ortamları yönetemezsiniz. Bunun yerine, Visual Studio ortam özelliklerinin tadını çıkarmak için [mevcut koddan bir Python projesi oluşturun](quickstart-01-python-in-visual-studio-project-from-existing-code.md) .
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> **Dosya**  >  **Aç**  >  **klasörü** komutunu kullanarak bir klasör olarak açılan Python kodu için ortamları yönetebilirsiniz. Python araç çubuğu, algılanan tüm ortamlar arasında geçiş yapmanıza ve ayrıca yeni bir ortam eklemenize olanak tanır. Ortam bilgileri, Workspace. vs klasöründeki PythonSettings. json dosyasında depolanır.
::: moniker-end

## <a name="the-python-environments-window"></a>Python ortamları penceresi

Visual Studio bildiği ortamlar, **Python ortamları** penceresinde görüntülenir. Pencereyi açmak için aşağıdaki yöntemlerden birini kullanın:

-   >  **diğer Windows**  >  **Python ortamlarını** görüntüle menü komutunu seçin.
- **Çözüm Gezgini** bir proje Için **Python ortamları** düğümüne sağ tıklayın ve **Tüm Python ortamlarını görüntüle**' yi seçin:

::: moniker range="vs-2017"
   ![Çözüm Gezgini-2017 ' de tüm ortamları görüntüle komutu](media/environments/environments-view-all.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Çözüm Gezgini-2019 ' de tüm ortamları görüntüle komutu](media/environments/environments-view-all-2019.png)
::: moniker-end
::: moniker range=">=vs-2022"
   ![Çözüm Gezgini-2022 ' de tüm ortamları görüntüle komutu](media/environments/environments-view-all-2022.png)
::: moniker-end

Tüm bu durumlarda, **Python ortamları** penceresi **Çözüm Gezgini**' nin yanında görünür:

::: moniker range="vs-2017"
   ![Python ortamları penceresi-2017](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Python ortamları penceresi-2019](media/environments/environments-default-view-2019.png)
::: moniker-end
::: moniker range=">=vs-2022"
   ![Python ortamları penceresi-2022](media/environments/environments-default-view-2022.png)
::: moniker-end

Visual Studio, sanal ortamlar ve conda ortamları (bkz. [ortam türleri](#types-of-environments)) ile birlikte kayıt defteri ( [pep 514](https://www.python.org/dev/peps/pep-0514/)) kullanılarak yüklenen küresel ortamlara bakar. Listede beklenen bir ortam görmüyorsanız, bkz. [var olan bir ortamı el ile tanımla](#manually-identify-an-existing-environment).

listeden bir ortam seçtiğinizde, Visual Studio **genel bakış** sekmesinde bu ortam için çeşitli özellikleri ve komutları görüntüler.

:::moniker range="vs-2017"
 Örneğin, yukarıdaki resimde yorumlayıcı konumunun **C:\Python36-32** olduğunu görebilirsiniz. **Genel bakış** sekmesinin alt kısmındaki dört komut, yorumlayıcı çalıştıran bir komut istemi açar. Daha fazla bilgi için bkz. [Python ortamları pencere sekmesi başvurusu 2017-genel bakış](python-environments-window-tab-reference.md#overview-tab).
:::moniker-end

:::moniker range="vs-2019"
 Örneğin, yukarıdaki resimde yorumlayıcı konumunun **C:\Python36-32** olduğunu görebilirsiniz. **Genel bakış** sekmesinin alt kısmındaki dört komut, yorumlayıcı çalıştıran bir komut istemi açar. Daha fazla bilgi için bkz. [Python ortamları pencere sekmesi başvurusu 2019-genel bakış](python-environments-window-tab-reference.md#overview-tab).
:::moniker-end

:::moniker range="vs-2022"
 örneğin, yukarıdaki resimde yorumlayıcı konumunun **C:\Program Files (x86) \ Microsoft Visual Studio \Python310** olduğunu görebilirsiniz. **Genel bakış** sekmesinin alt kısmındaki dört komut, yorumlayıcı çalıştıran bir komut istemi açar. Daha fazla bilgi için bkz. [Python ortamları pencere sekmesi başvurusu 2022-genel bakış](python-environments-window-tab-reference.md#overview-tab).
:::moniker-end

**Paketler** ve **IntelliSense** gibi farklı sekmelere geçiş yapmak için ortamlar listesinin altındaki açılan listeyi kullanın. Bu sekmeler Ayrıca [Python ortamları penceresi sekmesi başvurusu](python-environments-window-tab-reference.md)' nda açıklanmıştır.

Bir ortamın seçilmesi, herhangi bir projeyle ilişkisini değiştirmez. listede kalýn olarak gösterilen varsayılan ortam, Visual Studio yeni projeler için tarafından kullanılan bir ortamdır. Yeni projelerle farklı bir ortam kullanmak için **bunu yeni projeler için varsayılan ortamı yap** komutunu kullanın. Bir proje bağlamında, her zaman belirli bir ortamı seçebilirsiniz. Daha fazla bilgi için bkz. [proje için ortam seçme](selecting-a-python-environment-for-a-project.md#how-to-select-a-python-environment-for-a-project).

Listelenen her ortamın sağında, bu ortam için **etkileşimli** bir pencere açan bir denetimdir. (Visual Studio 2017 15,5 ve önceki sürümlerde, bu ortam için ıntellisense veritabanını yenileyen bir denetim görüntülenir. Veritabanı hakkındaki ayrıntılar için bkz. [ortamlar pencere sekmesi başvurusu](python-environments-window-tab-reference.md) .)

::: moniker range="vs-2017"
> [!Tip]
> **Python ortamları** penceresini yeterince genişlettikten sonra, ile çalışmaya daha uygun olan ortamlarınızın daha kapsamlı bir görünümünü alırsınız.
   > ![Python ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range="vs-2019"
> [!Tip]
> **Python ortamları** penceresini yeterince genişlettikten sonra, ile çalışmaya daha uygun olan ortamlarınızın daha kapsamlı bir görünümünü alırsınız.
   > ![Python ortamları penceresi genişletilmiş görünümü-2019](media/environments/environments-expanded-view-2019.png)
::: moniker-end

::: moniker range=">=vs-2022"
> [!Tip]
> **Python ortamları** penceresini yeterince genişlettikten sonra, ile çalışmaya daha uygun olan ortamlarınızın daha kapsamlı bir görünümünü alırsınız.
  > ![Python ortamları penceresi genişletilmiş görünümü-2022](media/environments/environments-expanded-view-2022.png)
::: moniker-end

> [!Note]
> Visual Studio sistem-site-paketleri seçeneğine gelse de, bunu Visual Studio içinden değiştirmek için bir yol sağlamaz.

### <a name="what-if-no-environments-appear"></a>Ortam görünmezse ne olacak?

hiçbir ortam görünmezse, Visual Studio standart konumlarda hiçbir Python yüklemesinin algılanamadığı anlamına gelir. örneğin, Visual Studio 2017 veya sonraki bir sürümü yüklemiş olabilirsiniz ancak Python iş yükünün yükleyici seçeneklerinde tüm yorumlayıcı seçeneklerini temizlemiş olabilirsiniz. benzer şekilde, 2015 veya daha eski bir sürümü Visual Studio yüklemiş olabilirsiniz ancak bir yorumlayıcı el ile yüklenmediniz (bkz. [Python yorumlayıcıları yükleme](installing-python-interpreters.md)).

bilgisayarınızda bir Python yorumlayıcı olduğunu, ancak Visual Studio (herhangi bir sürüm) algılamadığı biliyorsanız, konumunu el ile belirtmek için **+ Custom** komutunu kullanın. [Mevcut bir ortamı el ile tanımlamak](#manually-identify-an-existing-environment)için sonraki bölüme bakın.

::: moniker range="<=vs-2017"
> [!Tip]
> Visual Studio, python.org ' den yükleyicileri kullanarak Python 2.7.11 'i özelleştirme ' yi 2.7.14 'e yükseltmek gibi var olan yorumlayıcı güncelleştirmelerini algılar. Yükleme işlemi sırasında, eski ortam, güncelleştirme yerinde görüntülenmeden önce **Python ortamları** listesinden kaybolur.

> ancak, dosya sistemini kullanarak bir yorumlayıcı ve ortamını el ile taşırsanız Visual Studio yeni konumu bilmez. Daha fazla bilgi için bkz. [yorumlayıcı taşıma](installing-python-interpreters.md#move-an-interpreter).
::: moniker-end

### <a name="types-of-environments"></a>Ortam türleri

Visual Studio, genel, sanal ve conda ortamları ile çalışabilir.

#### <a name="global-environments"></a>Küresel ortamlar

Her Python yüklemesi kendi *genel ortamını* korur. Örneğin, Python 2,7, Python 3,6, Python 3,7, Anaconda 4.4.0, vb. Bkz. [Python yorumlayıcıları 'Nı yüklemeye](installing-python-interpreters.md)bakın)

Her ortam, belirli Python yorumlayıcı, standart kitaplığı, önceden yüklenmiş bir paket kümesi ve bu ortam etkinleştirilirken yüklediğiniz diğer paketlerle oluşur. Bir paketin küresel bir ortama yüklenmesi, bu ortamı kullanan tüm projeler tarafından kullanılabilmesini sağlar. Ortam, dosya sisteminin korumalı bir alanında bulunuyorsa (örneğin, *c:\Program Files* içinde), paket yükleme için yönetici ayrıcalıkları gerekir.

Küresel ortamlar bilgisayardaki tüm projeler için kullanılabilir. Visual Studio, özellikle bir proje için farklı bir tane seçmediğiniz sürece tüm projeler için kullanılan varsayılan olarak bir genel ortamı seçersiniz. Daha fazla bilgi için bkz. [proje için ortam seçme](selecting-a-python-environment-for-a-project.md).

#### <a name="virtual-environments"></a>Sanal ortamlar

Genel ortamda çalışmak, başlamak için kolay bir yoldur. Zamanla, ortamlar farklı projeler için yüklediğiniz birçok farklı paket ile karışık hale gelir. Bu tür dağınıklığı, uygulamanızı bilinen sürümlere sahip belirli bir paket kümesiyle kapsamlı bir şekilde test yapmayı zorlaştırır. Ancak, ortam türü bir yapı sunucusunda veya Web sunucusunda ayarladığınız şekilde tamamen aynıdır. İki proje aynı paketin uyumsuz paketlerini veya farklı sürümlerini gerektirdiğinde, çakışmalar da oluşabilir.

Bu nedenle, geliştiriciler genellikle proje için bir *sanal ortam* oluşturur. Sanal ortam, belirli bir yorumlayıcının kopyasını içeren bir projedeki alt klasördür. Sanal ortamı etkinleştirirseniz, yüklediğiniz tüm paketler yalnızca o ortamın alt klasörüne yüklenir. Daha sonra bu ortam içinde bir Python programı çalıştırdığınızda, bu belirli paketlere karşı çalıştığını bilirsiniz.

Visual Studio, bir proje için sanal ortam oluşturmaya yönelik doğrudan destek sağlar. örneğin, bir *requirements.txt* içeren bir projeyi açarsanız veya bu dosyayı içeren şablondan bir proje oluşturursanız, Visual Studio otomatik olarak bir sanal ortam oluşturmanızı ve bu bağımlılıkları yüklemenizi ister.

Açık bir proje içinde dilediğiniz zaman yeni bir sanal ortam oluşturabilirsiniz. **Çözüm Gezgini**, proje düğümünü genişletin, **Python ortamları**' na sağ tıklayın ve **ortam ekle**' yi seçin. **Ortam ekle**' de **sanal ortam**' ı seçin.

:::moniker range="vs-2019"
 Daha fazla bilgi için bkz. [sanal ortam oluşturma-2019](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1).
:::moniker-end
:::moniker range=">=vs-2022"
Daha fazla bilgi için [bkz. Sanal ortam oluşturma-2022](./selecting-a-python-environment-for-a-project.md?view=vs-2022&preserve-view=true#create-a-virtual-environment-1).
:::moniker-end

Visual Studio sanal ortamdan bir *requirements.txt* dosyası oluşturmak için bir komut da sağlar, bu da ortamı diğer bilgisayarlarda yeniden oluşturmayı kolaylaştırır. Daha fazla bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

#### <a name="conda-environments"></a>Conda ortamları

Conda ortamı, aracı kullanarak veya `conda` Visual Studio 2017 sürüm 15.7 ve üzerinde tümleşik conda yönetimiyle oluşturabilirsiniz. (Anaconda veya Miniconda gerektirir; bu, Visual Studio yükleyicisi aracılığıyla kullanılabilir, bkz. [Install Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017)

::: moniker range="vs-2017"

1. Python **Ortamları penceresinde + Conda** ortamı **oluştur'a tıklayın.** Bu pencerede Yeni **conda ortamı oluştur sekmesi** açılır:

   ![Yeni bir conda ortamı için oluştur sekmesi-1](media/environments/environments-conda-1.png)

1. Ad alanına ortam için bir ad **girin,** Python alanında temel bir Python yorumlayıcı seçin ve **Oluştur'a** **basın.**

1. Çıkış **penceresi,** oluşturma işlemi tamamlandıktan sonra birkaç CLI yönergeleriyle birlikte yeni ortamın ilerlemesini gösterir:

   ![Conda ortamının başarıyla oluşturulması-2](media/environments/environments-conda-2.png)

1. Bu Visual Studio proje için Bir ortam seçin konusunda açıklandığı gibi bir proje için conda ortamını etkinleştirerek diğer tüm [ortamlar gibi etkinleştirabilirsiniz.](selecting-a-python-environment-for-a-project.md)

1. Ortama paket yüklemek için Paketler sekmesini [kullanın.](python-environments-window-tab-reference.md#packages-tab)
::: moniker-end

::: moniker range="vs-2019"

1. Ortam Ekle iletişim kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) Ortam **Ekle...** **öğesini** seçin.

1. Ortam ekle iletişim kutusunda **Conda ortamı sekmesini** seçin:

   ![Ortam ekle iletişim kutusundaki Conda ortamı sekmesi-2019](media/environments/environments-conda-1-2019.png)

1. Aşağıdaki alanları yapılandırma:

    | Alan | Açıklama |
    | --- | --- |
    | Project | Ortamın oluşturulacak proje (aynı çözümde birden çok projeniz Visual Studio. |
    | Name | Conda ortamının adı. |
    | 'den paket ekleme | Bağımlılıklarınızı **açıklayan** bir *environment.yml* dosyanız varsa Ortam dosyası'yı seçin veya Bir veya daha fazla **Anaconda** paket adı'ı seçin ve aşağıdaki alanda en az bir Python paketi veya Python sürümü listelenin. Paket listesi conda'ya bir Python ortamı oluşturma talimatı sağlar. Python'ın en son sürümünü yüklemek için `python` kullanın; belirli bir sürümü yüklemek için içinde `python=,major>.<minor>` olduğu gibi `python=3.7` kullanın. Bir menü dizisinde Python sürümlerini ve ortak paketleri seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarlayın | Ortam oluşturulduktan sonra seçilen projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarlayın | Conda ortamını otomatik olarak ayarlar ve bu ortamda oluşturulan yeni projelerde Visual Studio. Bu seçenek, Python Ortamları **penceresindeki Yeni projeler için bunu varsayılan ortam yapma** seçeneğinin **kullanımıyla aynıdır.** |
    | Python Ortamlarında Görüntüle penceresi | Ortamı oluşturdukktan sonra Python Ortamları **penceresinin** gösterip göstermey kararını belirtir. |

    > [!Important]
    > Conda ortamı oluştururken, ortamın bir Python çalışma zamanı içerdiğini sağlayan veya paket listesini kullanarak en az bir Python sürümü veya Python paketi `environments.yml` belirttiğinizden emin olun. Aksi Visual Studio, ortamı yoksayıyorsa: ortam **Python** Ortamları penceresinin herhangi bir yerinde görünmez, bir projenin geçerli ortamı olarak ayarlanmıyor ve genel bir ortam olarak kullanılamaz.
    >
    > Python sürümü olmadan bir conda ortamı oluşturursanız, conda ortam klasörlerinin konumlarını görmek için komutunu kullanın ve ardından ortamın alt klasörünü bu konumdan el `conda info` ile kaldırın.

1. **Oluştur'a** tıklayın ve Çıkış penceresinde **ilerlemeyi gözlemle.**

Çıkış, oluşturma işlemi tamamlandıktan sonra birkaç CLI yönergeleri içerir:

   ![Conda ortamının başarıyla oluşturulması-2019](media/environments/environments-conda-2-2019.png)

1. Bu Visual Studio proje için Bir ortam seçin konusunda açıklandığı gibi bir proje için conda ortamını etkinleştirerek diğer tüm [ortamlar gibi etkinleştirabilirsiniz.](selecting-a-python-environment-for-a-project.md)

1. Ortama daha fazla paket yüklemek için Paketler sekmesini [kullanın.](python-environments-window-tab-reference.md#packages-tab)
::: moniker-end

::: moniker range=">=vs-2022"

1. Ortam Ekle iletişim kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) Ortam **Ekle...** **öğesini** seçin.

1. Ortam ekle iletişim kutusunda **Conda ortamı sekmesini** seçin:

   ![Ortam ekle iletişim kutusundaki Conda ortamı sekmesi-2022](media/environments/environments-conda-1-2022.png)

1. Aşağıdaki alanları yapılandırma:

    | Alan | Açıklama |
    | --- | --- |
    | Project | Ortamın oluşturulacak proje (aynı çözümde birden çok projeniz Visual Studio. |
    | Name | Conda ortamının adı. |
    | 'den paket ekleme | Bağımlılıklarınızı **açıklayan** bir *environment.yml* dosyanız varsa Ortam dosyası'yı seçin veya Bir veya daha fazla **Anaconda** paket adı'ı seçin ve aşağıdaki alanda en az bir Python paketi veya Python sürümü listelenin. Paket listesi conda'ya bir Python ortamı oluşturma talimatı sağlar. Python'ın en son sürümünü yüklemek için `python` kullanın; belirli bir sürümü yüklemek için içinde `python=,major>.<minor>` olduğu gibi `python=3.7` kullanın. Bir menü dizisinde Python sürümlerini ve ortak paketleri seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarlayın | Ortam oluşturulduktan sonra seçilen projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarlayın | Conda ortamını otomatik olarak ayarlar ve bu ortamda oluşturulan yeni projelerde Visual Studio. Bu seçenek, Python Ortamları **penceresindeki Yeni projeler için bunu varsayılan ortam yapma** seçeneğinin **kullanımıyla aynıdır.** |
    | Python Ortamlarında Görüntüle penceresi | Ortamı oluşturdukktan sonra Python Ortamları **penceresinin** gösterip göstermey kararını belirtir. |

    > [!Important]
    > Conda ortamı oluştururken, ortamın bir Python çalışma zamanı içerdiğini sağlayan veya paket listesini kullanarak en az bir Python sürümü veya Python paketi `environments.yml` belirttiğinizden emin olun. Aksi Visual Studio, ortamı yoksayıyorsa: ortam **Python** Ortamları penceresinin herhangi bir yerinde görünmez, bir projenin geçerli ortamı olarak ayarlanmıyor ve genel bir ortam olarak kullanılamaz.
    >
    > Python sürümü olmadan bir conda ortamı oluşturursanız, conda ortam klasörlerinin konumlarını görmek için komutunu kullanın ve ardından ortamın alt klasörünü bu konumdan el `conda info` ile kaldırın.

1. **Oluştur'a** tıklayın ve Çıkış penceresinde **ilerlemeyi gözlemle.** Çıkış, oluşturma işlemi tamamlandıktan sonra birkaç CLI yönergeleri içerir:

   ![Conda ortamı 2022 başarıyla oluşturma](media/environments/environments-conda-2-2022.png)

1. Bu Visual Studio proje için Bir ortam seçin konusunda açıklandığı gibi bir proje için conda ortamını etkinleştirerek diğer tüm [ortamlar gibi etkinleştirabilirsiniz.](selecting-a-python-environment-for-a-project.md)

1. Ortama daha fazla paket yüklemek için Paketler sekmesini [kullanın.](python-environments-window-tab-reference.md#packages-tab)
::: moniker-end

> [!Note]
> Conda ortamlarında en iyi sonuçları elde etmek için conda 4.4.8 veya sonraki sürümleri kullanın (conda sürümleri Anaconda sürümlerinden farklıdır). Miniconda'nın uygun sürümlerini (Visual Studio 2019 ve Visual Studio 2022) ve Anaconda (Visual Studio 2017) Visual Studio yükleyebilirsiniz.

Conda ortamlarının depolandığı conda sürümünü ve diğer bilgileri görmek için anaconda komut isteminde (anaconda'nın yolda olduğu bir komut istemi) `conda info` komutunu çalıştırın:

```cli
conda info
```

Conda ortam klasörleriniz aşağıdaki gibi görünür:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Conda ortamları bir projeyle depolandığı için genel ortamlara benzer şekilde davranır. Örneğin, conda ortamına yeni bir paket yüklemek, bu paketi bu ortamı kullanan tüm projeler için kullanılabilir yapar.

2017 Visual Studio 15.6 ve önceki sürümler için conda ortamlarını, mevcut ortamı el ile tanımlama altında açıklandığı gibi el ile işaret [edersiniz.](#manually-identify-an-existing-environment)

Visual Studio 2017 sürüm 15.7 ve sonraki sürümler conda ortamlarını otomatik olarak algılar ve sonraki bölümde açıklandığı gibi **Python** Ortamları penceresinde görüntüler.

## <a name="manually-identify-an-existing-environment"></a>Mevcut ortamı el ile tanımlama

Standart olmayan bir konumda yüklü bir ortamı belirlemek için aşağıdaki adımları kullanın:

::: moniker range="<=vs-2017"

Standart olmayan bir konuma (Visual Studio 2017 sürüm 15.6 ve önceki sürümlerde conda ortamları dahil) yüklenmiş bir ortamı belirlemek için aşağıdaki adımları kullanın:

1. Python Ortamları penceresinde Yapılandır **sekmesini açan** **+** **Özel'i** seçin:

   ![Yeni bir özel ortam için varsayılan görünüm](media/environments/environments-custom-1.png)

1. Açıklama alanına ortam için bir **ad** girin.

1. Ön ek yolu alanına yorumlayıcının yoluna **(...** kullanarak) **gidin veya** göz atın.

1. Bu Visual Studio bir Python yorumlayıcı (conda ortamı için aşağıda gösterilen yol gibi) algılarsa, Otomatik Algıla **komutunu** sağlar. Otomatik **Algıla seçeneği,** kalan alanları tamamlar. Ayrıca bu alanları el ile de tamamabilirsiniz.

   ![Otomatik Algıla komutunu etkinleştirme](media/environments/environments-custom-2.png)

   ![Otomatik Algıla'nın kullanımından sonra ortam alanlarının tamamlanması](media/environments/environments-custom-3.png)

1. Alanlar istediğiniz değerleri içerdiği zaman, yapılandırmayı kaydetmek **için Uygula'ya** tıklayın. Artık ortamı, ortam içindeki diğer tüm ortamlar gibi Visual Studio.

1. El ile tanımlanan bir ortamı kaldırmanız gerekirse Yapılandır **sekmesinde Kaldır** **komutunu** seçin. Otomatik olarak algılanan ortamlar bu seçeneği sağlamaz. Daha fazla bilgi için [bkz. Yapılandırma sekmesi.](python-environments-window-tab-reference.md#configure-tab)

::: moniker-end

::: moniker range="vs-2019"

1. Ortam Ekle iletişim kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) Ortam **Ekle...** **öğesini** seçin.

1. Ortam ekle iletişim kutusunda Mevcut ortam **sekmesini** seçin:

   ![Ortam ekle iletişim kutusundaki mevcut ortam sekmesi-2019](media/environments/environments-custom-1-2019.png)

1. **Ortam** açılan öğesini seçin ve ardından **özel**' i seçin:

   ![Ortam Ekle iletişim kutusunda özel ortam seçeneği-2019](media/environments/environments-custom-2-2019.png)

1. İletişim kutusundaki belirtilen alanlarda, diğer alanların çoğunu dolduran **ön ek yolu** altındaki yorumlayıcı yoluna ( **.**..) girin veya bu yolu inceleyin.

1. Bu değerleri inceledikten ve gerektiğinde değiştirdikten sonra **Ekle**' yi seçin.

   ![Ortam ekle dialog0-2019 içindeki özel bir ortam seçeneğinin ayrıntılarını belirtme alanları](media/environments/environments-custom-3-2019.png)

Ayrıca, **Python ortamları** penceresinde istediğiniz zaman ortamın ayrıntılarını gözden geçirebilir ve değiştirebilirsiniz.

1. Python ortamı penceresinde, ortamı seçin ve ardından **Yapılandır** sekmesini seçin.

1. Değişiklik yaptıktan sonra **Uygula** komutunu seçin.
   Ayrıca **Remove** komutunu kullanarak ortamı kaldırabilirsiniz (Oto algılanan ortamlar için kullanılamaz). Daha fazla bilgi için bkz. [Configure Tab](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

::: moniker range=">=vs-2022"

1. **Python ortamları** penceresinde (veya Python araç çubuğundan) ortam **Ekle Iletişim kutusunu** açan **ortam ekle...** seçeneğini belirleyin.

1. Ortam Ekle iletişim kutusunda **var olan ortam** sekmesini seçin:

   ![Ortam Ekle iletişim kutusunda var olan ortam sekmesi-2022](media/environments/environments-custom-1-2022.png)

    Örneğin, var olan bir ortamı ve mevcut ortamın yolunu seçin.

1. **Ortam** açılan öğesini seçin ve ardından **özel**' i seçin:

   ![Ortam Ekle iletişim kutusunda özel ortam seçeneği-2022](media/environments/environments-custom-2-2022.png).

    Örneğin, C:\Users\user\Anaconda3\python.exe bir Anaconda 2021,05

1. İletişim kutusundaki belirtilen alanlarda, diğer alanların çoğunu dolduran **ön ek yolu** altındaki yorumlayıcı yoluna ( **.**..) girin veya bu yolu inceleyin.

1. Bu değerleri inceledikten ve gerektiğinde değiştirdikten sonra **Ekle**' yi seçin.
   ![Ortam Ekle iletişim kutusunda özel ortam seçeneğinin ayrıntılarını belirtme alanları-2022](media/environments/environments-custom-3-2022.png)

Ayrıca, **Python ortamları** penceresinde istediğiniz zaman ortamın ayrıntılarını gözden geçirebilir ve değiştirebilirsiniz.

1. Python ortamı penceresinde, ortamı seçin ve ardından **Yapılandır** sekmesini seçin.  

1. Değişiklik yaptıktan sonra **Uygula** komutunu seçin.
    Ayrıca **Remove** komutunu kullanarak ortamı kaldırabilirsiniz (Oto algılanan ortamlar için kullanılamaz). Daha fazla bilgi için bkz. [Configure Tab](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Geçersiz ortamları çözme veya silme

Visual Studio bir ortamın kayıt defteri girişlerini bulursa, ancak yorumlayıcı yolu geçersizse, **Python ortamları** penceresi adı bir üstü çizili yazı tipiyle gösterir:

::: moniker range="vs-2017"
  ![Geçersiz bir ortamı gösteren Python ortamları penceresi-2017](media/environments/environments-invalid-entry.png)
::: moniker-end

::: moniker range=">=vs-2019"
  ![Geçersiz bir ortamı gösteren Python ortamları penceresi-2019-2022](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Tutmak istediğiniz bir ortamı düzeltmek için öncelikle yükleyicinin **onarma** işlemini kullanmayı deneyin. Standart Python 3. x yükleyicileri, örneğin, bu seçeneği içerir.

## <a name="modify-the-registry-to-correct-an-environment-that-doesnt-have-a-repair-option-or-to-remove-an-invalid-environment"></a>Kayıt defterini, onarım seçeneği olmayan bir ortamı düzeltmek ya da geçersiz bir ortamı kaldırmak için değiştirin

Kayıt defterini doğrudan değiştirmek için aşağıdaki adımları kullanın. Visual Studio, kayıt defterinde değişiklik yaptığınızda **Python ortamları** penceresini otomatik olarak güncelleştirir.

1. *regedit.exe* çalıştırın.
1. **HKEY_LOCAL_MACHINE\SOFTWARE\Python** veya **HKEY_CURRENT_USER\SOFTWARE\Python** gidin. IronPython için, bunun yerine **IronPython** öğesini arayın.
1. Anaconda için, Cpyıthon veya **Continuumanalytics** Için **Python Core** gibi dağıtımla eşleşen düğümü genişletin. IronPython için sürüm numarası düğümünü genişletin.
1. **InstallPath** düğümünün altındaki değerleri inceleyin:

   ![Tipik bir Cpne Thon yüklemesi için kayıt defteri girişleri](media/environments/environments-registry-entries.png)

    - Ortam bilgisayarınızda hala mevcutsa, **ExecutablePath** değerini doğru konum olarak değiştirin. Ayrıca, **(varsayılan)** ve **WindowedExecutablePath** değerlerini gereken şekilde düzeltin.
    - Ortam bilgisayarınızda artık yoksa ve **Python ortamları** penceresinden kaldırmak istiyorsanız, yukarıdaki görüntüde **3,6** gibi **InstallPath**'in üst düğümünü silin.
    - **HKEY_CURRENT_USER\SOFTWARE\Python** geçersiz ayarlar **HKEY_LOCAL_MACHINE\SOFTWARE\Python** ayarları geçersiz kılar

## <a name="see-also"></a>Ayrıca bkz.

- [Python yorumlayıcılarını yükleme](installing-python-interpreters.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
