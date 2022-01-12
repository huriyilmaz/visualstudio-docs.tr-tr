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
ms.openlocfilehash: 57258ad766e34aeeec770ea1056472b309e253d7
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805890"
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

Bir ortamın seçilmesi, herhangi bir projeyle ilişkisini değiştirmez. listede kalýn olarak gösterilen varsayılan ortam, Visual Studio yeni projeler için tarafından kullanılan bir ortamdır. Yeni projelerle farklı bir ortam kullanmak için **bunu yeni projeler için varsayılan ortamı yap** komutunu kullanın. Bir proje bağlamında, her zaman belirli bir ortamı seçebilirsiniz. Daha fazla bilgi için bkz. [proje için ortam seçme](selecting-a-python-environment-for-a-project.md).

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
Daha fazla bilgi için bkz. [sanal ortam oluşturma-2022](./selecting-a-python-environment-for-a-project.md?view=vs-2022&preserve-view=true#create-a-virtual-environment-1).
:::moniker-end

Visual Studio ayrıca, sanal bir ortamdan bir *requirements.txt* dosyası oluşturmak için bir komut sağlar, bu da ortamı diğer bilgisayarlarda yeniden oluşturmayı kolaylaştırır. Daha fazla bilgi için bkz. [sanal ortamları kullanma](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

#### <a name="conda-environments"></a>Conda ortamları

conda ortamı, `conda` aracını kullanarak veya Visual Studio 2017 sürüm 15,7 ve üzeri sürümlerde tümleşik conda management ile oluşturduğunuz bir sürümdür. (Visual Studio yükleyicisi aracılığıyla kullanılabilen anaconda veya miniconda gerektirir, bkz. [yükleme Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017)

::: moniker range="vs-2017"

1. **Yeni bir Conda ortamı oluştur** sekmesi açan **Python ortamları** penceresinde **+ Conda ortamı oluştur** ' u seçin:

   ![Yeni bir Conda ortamı için sekme Oluştur-1](media/environments/environments-conda-1.png)

1. **Ad** alanına ortam için bir ad girin, **Python** alanında bir temel Python yorumlayıcı seçin ve **Oluştur**' u seçin.

1. **Çıkış** penceresinde, oluşturma işlemi tamamlandıktan sonra bazı CLI yönergeleriyle yeni ortam için ilerleme durumu gösterilir:

   ![Conda ortamının başarıyla oluşturulması-2](media/environments/environments-conda-2.png)

1. Visual Studio içinde, proje için bir [ortam seçin](selecting-a-python-environment-for-a-project.md)bölümünde açıklandığı gibi bir proje için conda ortamını etkinleştirebilirsiniz.

1. Ortama paket yüklemek için [paketler sekmesini](python-environments-window-tab-reference.md#packages-tab)kullanın.
::: moniker-end

::: moniker range="vs-2019"

1. **Python ortamları** penceresinde (veya Python araç çubuğundan) ortam **Ekle Iletişim kutusunu** açan **ortam ekle...** seçeneğini belirleyin.

1. Ortam Ekle iletişim kutusunda **Conda ortamı** sekmesini seçin:

   ![Ortam Ekle iletişim kutusunda Conda ortamı sekmesi-2019](media/environments/environments-conda-1-2019.png)

1. Aşağıdaki alanları yapılandırın:

    | Alan | Açıklama |
    | --- | --- |
    | Project | ortamın oluşturulacağı proje (aynı Visual Studio çözümünde birden çok projeniz varsa). |
    | Name | Conda ortamının adı. |
    | Paket ekle | Bağımlılıklarınızı tanımlayan bir *Environment. yıml* dosyanız varsa **ortam dosyası** ' nı seçin veya **bir veya daha fazla Anaconda paketi adı** seçin ve en az bir Python paketi veya aşağıdaki alanda bir Python sürümü listeleyin. Paket listesi, Conda 'ın Python ortamı oluşturmasını söyler. Python 'un en son sürümünü yüklemek için; kullanın `python` ; belirli bir sürümü yüklemek için `python=,major>.<minor>` içinde olarak kullanın `python=3.7` . Ayrıca, bir dizi menüden Python sürümlerini ve ortak paketleri seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarla | Ortam oluşturulduktan sonra seçili projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarla | , Visual Studio ' de oluşturulan tüm yeni projelerde Conda ortamını otomatik olarak ayarlar ve etkinleştirir. Bu seçenek, **Python ortamları** penceresinde **yeni projeler için bu varsayılan ortamı yap** ' ın kullanılmasıyla aynıdır. |
    | Python ortamları penceresinde görüntüle | Ortamı oluşturduktan sonra **Python ortamları** penceresinin gösterilip gösterilmeyeceğini belirtir. |

    > [!Important]
    > Bir Conda ortamı oluştururken, ya da paket listesini kullanarak en az bir Python sürümü veya Python paketi belirttiğinizden emin olun `environments.yml` . Bu, ortamın bir Python çalışma zamanı içerdiğinden emin olmanızı sağlar. aksi takdirde, Visual Studio ortamı yoksayar: ortam, **Python ortamları** penceresinde hiçbir yerde görünmez, bir proje için geçerli ortam olarak ayarlanmamış ve genel bir ortam olarak kullanılamıyor.
    >
    > Python sürümü olmadan bir Conda ortamı oluşturursanız, `conda info` Conda ortam klasörlerinin konumlarını görmek için komutunu kullanın, ardından ortamın alt klasörünü bu konumdan el ile kaldırın.

1. **Oluştur**' u seçin ve **Çıkış** penceresinde ilerlemeyi gözlemleyin.

Çıktı, oluşturma işlemi tamamlandıktan sonra birkaç CLı yönergesi içerir:

   ![Conda ortamının başarıyla oluşturulması-2019](media/environments/environments-conda-2-2019.png)

1. Visual Studio içinde, proje için bir [ortam seçin](selecting-a-python-environment-for-a-project.md)bölümünde açıklandığı gibi bir proje için conda ortamını etkinleştirebilirsiniz.

1. Ortama daha fazla paket yüklemek için [paketler sekmesini](python-environments-window-tab-reference.md#packages-tab)kullanın.
::: moniker-end

::: moniker range=">=vs-2022"

1. **Python ortamları** penceresinde (veya Python araç çubuğundan) ortam **Ekle Iletişim kutusunu** açan **ortam ekle...** seçeneğini belirleyin.

1. Ortam Ekle iletişim kutusunda **Conda ortamı** sekmesini seçin:

   ![Ortam Ekle iletişim kutusunda Conda ortamı sekmesi-2022](media/environments/environments-conda-1-2022.png)

1. Aşağıdaki alanları yapılandırın:

    | Alan | Açıklama |
    | --- | --- |
    | Project | ortamın oluşturulacağı proje (aynı Visual Studio çözümünde birden çok projeniz varsa). |
    | Name | Conda ortamının adı. |
    | Paket ekle | Bağımlılıklarınızı tanımlayan bir *Environment. yıml* dosyanız varsa **ortam dosyası** ' nı seçin veya **bir veya daha fazla Anaconda paketi adı** seçin ve en az bir Python paketi veya aşağıdaki alanda bir Python sürümü listeleyin. Paket listesi, Conda 'ın Python ortamı oluşturmasını söyler. Python 'un en son sürümünü yüklemek için; kullanın `python` ; belirli bir sürümü yüklemek için `python=,major>.<minor>` içinde olarak kullanın `python=3.7` . Ayrıca, bir dizi menüden Python sürümlerini ve ortak paketleri seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarla | Ortam oluşturulduktan sonra seçili projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarla | , Visual Studio ' de oluşturulan tüm yeni projelerde Conda ortamını otomatik olarak ayarlar ve etkinleştirir. Bu seçenek, **Python ortamları** penceresinde **yeni projeler için bu varsayılan ortamı yap** ' ın kullanılmasıyla aynıdır. |
    | Python ortamları penceresinde görüntüle | Ortamı oluşturduktan sonra **Python ortamları** penceresinin gösterilip gösterilmeyeceğini belirtir. |

    > [!Important]
    > Bir Conda ortamı oluştururken, ya da paket listesini kullanarak en az bir Python sürümü veya Python paketi belirttiğinizden emin olun `environments.yml` . Bu, ortamın bir Python çalışma zamanı içerdiğinden emin olmanızı sağlar. aksi takdirde, Visual Studio ortamı yoksayar: ortam, **Python ortamları** penceresinde hiçbir yerde görünmez, bir proje için geçerli ortam olarak ayarlanmamış ve genel bir ortam olarak kullanılamıyor.
    >
    > Python sürümü olmadan bir Conda ortamı oluşturursanız, `conda info` Conda ortam klasörlerinin konumlarını görmek için komutunu kullanın, ardından ortamın alt klasörünü bu konumdan el ile kaldırın.

1. **Oluştur**' u seçin ve **Çıkış** penceresinde ilerlemeyi gözlemleyin. Çıktı, oluşturma işlemi tamamlandıktan sonra birkaç CLı yönergesi içerir:

   ![Conda ortamının başarıyla oluşturulması-2022](media/environments/environments-conda-2-2022.png)

1. Visual Studio içinde, proje için bir [ortam seçin](selecting-a-python-environment-for-a-project.md)bölümünde açıklandığı gibi bir proje için conda ortamını etkinleştirebilirsiniz.

1. Ortama daha fazla paket yüklemek için [paketler sekmesini](python-environments-window-tab-reference.md#packages-tab)kullanın.
::: moniker-end

> [!Note]
> Conda ortamlarındaki en iyi sonuçları elde etmek için Conda 4.4.8 veya üstünü kullanın (Conda sürümleri, Anaconda sürümlerinden farklıdır). Visual Studio yükleyicisi aracılığıyla miniconda (Visual Studio 2019 ve Visual Studio 2022) ve anaconda (Visual Studio 2017) için uygun sürümleri yükleyebilirsiniz.

Conda ortamlarının depolandığı Conda sürümünü ve diğer bilgileri görmek için, `conda info` bir Anaconda komut isteminde (Anaconda 'nın yolda bulunduğu bir komut istemi) çalıştırın:

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

Visual Studio 2017 sürüm 15,6 ve önceki sürümlerde, [var olan bir ortamı el ile tanımlamak](#manually-identify-an-existing-environment)altında açıklandığı gibi, conda ortamlarını el ile işaret ederek kullanabilirsiniz.

Visual Studio 2017 sürüm 15,7 ve üzeri, conda ortamlarını otomatik olarak algılar ve bu ortamları bir sonraki bölümde açıklandığı gibi **Python ortamları** penceresinde görüntüler.

## <a name="manually-identify-an-existing-environment"></a>Mevcut bir ortamı el ile tanımla

Standart olmayan bir konumda yüklü olan bir ortamı tanımlamak için aşağıdaki adımları kullanın:

::: moniker range="<=vs-2017"

standart olmayan bir konumda yüklü olan bir ortamı (Visual Studio 2017 sürüm 15,6 ve önceki sürümlerde bulunan conda dahil olmak üzere) tanımlamak için aşağıdaki adımları kullanın:

1. **Yapılandırma** sekmesini açan **Python ortamları** penceresinde **+ özel** ' i seçin:

   ![Yeni bir özel ortam için varsayılan görünüm](media/environments/environments-custom-1.png)

1. **Açıklama** alanına ortam için bir ad girin.

1. **Önek yolu** alanındaki yorumlayıcı yolunun yolunu ( **.**..) girin veya buraya gidin.

1. Visual Studio bu konumda bir Python yorumlayıcı algılarsa (bir conda ortamı için aşağıda gösterilen yol gibi), **otomatik algıla** komutu etkinleştirilir. **Otomatik algılamayı** seçmek kalan alanları tamamlar. Ayrıca, bu alanları el ile de tamamlayabilirsiniz.

   ![Auto Detect komutunu etkinleştirme](media/environments/environments-custom-2.png)

   ![Otomatik Algıla kullanıldıktan sonra ortam alanlarını tamamlama](media/environments/environments-custom-3.png)

1. Alanlar istediğiniz değerleri içeriyorsa, yapılandırmayı kaydetmek için **Uygula** ' yı seçin. Artık Visual Studio içindeki diğer gibi ortamı kullanabilirsiniz.

1. El ile tanımlanmış bir ortamı kaldırmanız gerekiyorsa, **Yapılandır** sekmesinde **Kaldır** komutunu seçin. Oto algılanan ortamlar bu seçeneği sağlamaz. Daha fazla bilgi için bkz. [Configure Tab](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range="vs-2019"

1. **Python ortamları** penceresinde (veya Python araç çubuğundan) ortam **Ekle Iletişim kutusunu** açan **ortam ekle...** seçeneğini belirleyin.

1. Ortam Ekle iletişim kutusunda **var olan ortam** sekmesini seçin:

   ![Ortam Ekle iletişim kutusunda var olan ortam sekmesi-2019](media/environments/environments-custom-1-2019.png)

1. Ortam **açılan öğesini** ve ardından Özel'i **seçin:**

   ![Ortam ekle iletişim kutusundaki özel ortam seçeneği-2019](media/environments/environments-custom-2-2019.png)

1. İletişim kutusundaki sağlanan alanlara, diğer alanların çoğunu dolduran Ön Ek yolu altındaki yorumlayıcının yoluna **(kullanarak )** gidin veya gözatın.

1. Bu değerleri gözden geçirdikten ve gerektiğinde değiştirdikten sonra Ekle'yi **seçin.**

   ![Ortam ekle iletişim kutusundaki özel ortam seçeneğinin ayrıntılarını belirten alanlar0-2019](media/environments/environments-custom-3-2019.png)

Ayrıca Python Ortamları penceresinde ortamın ayrıntılarını herhangi bir zamanda gözden geçirebilirsiniz ve **değiştirebilirsiniz.**

1. Python ortamı penceresinde ortamı seçin ve ardından Yapılandır **sekmesini** seçin.

1. Değişiklik yaptıktan sonra Uygula **komutunu** seçin.
   Kaldır komutunu kullanarak da ortamı **kaldırabilirsiniz** (otomatik olarak algılanan ortamlar için kullanılamaz). Daha fazla bilgi için [bkz. Yapılandırma sekmesi.](python-environments-window-tab-reference.md#configure-tab)
::: moniker-end

::: moniker range=">=vs-2022"

1. Ortam Ekle iletişim kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) Ortam **Ekle...** **öğesini** seçin.

1. Ortam ekle iletişim kutusunda Mevcut ortam **sekmesini** seçin:

   ![Ortam ekle iletişim kutusundaki mevcut ortam sekmesi-2022](media/environments/environments-custom-1-2022.png)

    Örneğin, mevcut bir ortamı ve mevcut ortamın yolunu seçin.

1. Ortam **açılan öğesini** ve ardından Özel'i **seçin:**

   ![Ortam ekle iletişim kutusundaki özel ortam seçeneği-2022](media/environments/environments-custom-2-2022.png).

    Örneğin, C:\Users\user\Anaconda3\python.exe'de Anaconda 2021.05

1. İletişim kutusundaki sağlanan alanlara, diğer alanların çoğunu dolduran Ön Ek yolu altındaki yorumlayıcının yoluna **(kullanarak )** gidin veya gözatın.

1. Bu değerleri gözden geçirdikten ve gerektiğinde değiştirdikten sonra Ekle'yi **seçin.**
   ![Ortam ekle iletişim kutusundaki özel ortam seçeneğinin ayrıntılarını belirten alanlar-2022](media/environments/environments-custom-3-2022.png)

Ayrıca Python Ortamları penceresinde ortamın ayrıntılarını herhangi bir zamanda gözden geçirebilirsiniz ve **değiştirebilirsiniz.**

1. Python ortamı penceresinde ortamı ve ardından Yapılandır **sekmesini** seçin.  

1. Değişiklik yaptıktan sonra Uygula **komutunu** seçin.
    Kaldır komutunu kullanarak da ortamı **kaldırabilirsiniz** (otomatik olarak algılanan ortamlar için kullanılamaz). Daha fazla bilgi için [bkz. Yapılandırma sekmesi.](python-environments-window-tab-reference.md#configure-tab)
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Geçersiz ortamları düzeltme veya silme

Bir Visual Studio kayıt defteri girdilerini bulursanız ancak yorumlayıcının yolu geçersizse **Python Ortamları** penceresinde adı bir yazı tipiyle gösterilir:

::: moniker range="vs-2017"
  ![Geçersiz bir ortamı gösteren Python Ortamları penceresi-2017](media/environments/environments-invalid-entry.png)
::: moniker-end

::: moniker range=">=vs-2019"
  ![Geçersiz bir ortamı gösteren Python Ortamları penceresi-2019-2022](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Tutmak istediğiniz bir ortamı düzeltmek için önce yükleyicinin Onarım işlemini **kullanmayı** deneyin. Örneğin, standart Python 3.x yükleyicileri bu seçeneği içerir.

## <a name="modify-the-registry-to-correct-an-environment-that-doesnt-have-a-repair-option-or-to-remove-an-invalid-environment"></a>Onarım seçeneği olmayan bir ortamı düzeltmek veya geçersiz bir ortamı kaldırmak için kayıt defterini değiştirme

Kayıt defterini doğrudan değiştirmek için aşağıdaki adımları kullanın. Visual Studio değişiklik yaptığınız **zaman Python Ortamları** penceresini otomatik olarak güncelleştirmeniz gerekir.

1. *regedit.exe.*
1. HKEY_LOCAL_MACHINE\SOFTWARE\Python **veya** **HKEY_CURRENT_USER\SOFTWARE\Python.** IronPython için bunun yerine **IronPython'a** bakın.
1. Dağıtımla eşleşen düğümü genişletin; örneğin CPython için **Python Core** veya Anaconda için **ContinuumAnalytics.** IronPython için sürüm numarası düğümünü genişletin.
1. InstallPath düğümü altındaki **değerleri inceleme:**

   ![Tipik bir CPython yüklemesi için kayıt defteri girdileri](media/environments/environments-registry-entries.png)

    - Ortam bilgisayarınızda hala mevcutsa **ExecutablePath** değerini doğru konumla değiştirebilirsiniz. Ayrıca **(Varsayılan) ve** **WindowedExecutablePath değerlerini de** gereken şekilde düzeltin.
    - Ortam artık bilgisayarınızda yoksa ve **bunu Python** Ortamları penceresinden kaldırmak için yukarıdaki görüntüde yer alan **3.6** gibi **InstallPath** üst düğümünü silin.
    - **HKEY_CURRENT_USER\SOFTWARE\Python'de** geçersiz ayarlar,HKEY_LOCAL_MACHINE\SOFTWARE\Python

## <a name="see-also"></a>Ayrıca bkz.

- [Python yorumlayıcılarını yükleme](installing-python-interpreters.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar requirements.txt kaynak kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
