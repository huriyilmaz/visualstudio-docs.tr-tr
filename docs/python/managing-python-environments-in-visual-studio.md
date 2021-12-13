---
title: Python ortamlarını ve yorumlayıcılarını yönetme
description: Genel, sanal ve conda ortamlarını yönetmek için Python Ortamları penceresini kullanın. Python yorumlayıcılarını ve paketlerini yükleyin ve ortamlara Visual Studio attayın.
ms.date: 08/06/2019
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 5307dbff80bdbe9942b2aaf53517b935ad374202
ms.sourcegitcommit: 0f2af2f1a8cf0a481fd8f673accf3aebf2e262c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "134713897"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Visual Studio'de Python ortamları oluşturma ve yönetme

**Python ortamı,** Python kodunu çalıştırarak genel, sanal ve conda ortamlarını içeren bir bağlamdır. Ortam bir yorumlayıcı, bir kitaplık (genellikle Python Standart Kitaplığı) ve yüklü paketlerden oluşur. Bu bileşenler birlikte geçerli dil yapılarını ve söz dizimi, erişebilirsiniz işletim sistemi işlevlerini ve kullanabileceğiniz paketleri belirler.

Bu Visual Studio açık Windows, ortamları yönetmek ve yeni projeler için varsayılan olarak birini seçmek için bu makalede açıklandığı gibi **Python** Ortamları penceresini kullanırsınız. Ortamların diğer yönleri aşağıdaki makalelerde bulunabilir:

- Herhangi bir proje için [varsayılanı kullanmak yerine belirli bir](selecting-a-python-environment-for-a-project.md) ortamı seçin.

- Python projeleri için sanal ortam oluşturma ve kullanma hakkında ayrıntılı bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

- Paketleri bir ortama yüklemek için Paketler sekmesi [başvurusuna bakın.](python-environments-window-tab-reference.md#packages-tab)

- Başka bir Python yorumlayıcı yüklemek için [bkz. Python yorumlayıcılarını yükleme.](installing-python-interpreters.md) Genel olarak, ana Python dağıtımı için bir yükleyici indirip çalıştırıyorsanız, Visual Studio yeni yüklemenin ve ortamın **Python** Ortamları penceresinde görüntülendiğinden ve projeler için seçilene olduğunu algılar.

Python'da yeni bir Visual Studio aşağıdaki makaleler de genel arka plan bilgileri sağlar:

- [Visual Studio'da Python ile çalışma](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio’da Python desteğini yükleme](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Python kodu için yalnızca klasör olarak açılan ortamları Dosya Klasör Aç komutunu **kullanarak**  >  **yönetesiniz.**  >   Bunun [yerine, ortamın ortam özelliklerinden keyif almak için](quickstart-01-python-in-visual-studio-project-from-existing-code.md) mevcut koddan bir Python Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Klasör olarak açılan Python kodu ortamlarını Dosya Klasör Aç **komutunu**  >  **kullanarak**  >  **yönetebilirsiniz.** Python araç çubuğu, algılanan tüm ortamlar arasında geçiş ve yeni bir ortam eklemenize olanak tanır. Ortam bilgileri Workspace .vs klasöründeki PythonSettings.json dosyasında depolanır.
::: moniker-end

## <a name="the-python-environments-window"></a>Python Ortamları penceresi

Hakkında Visual Studio ortamlar Python Ortamları **penceresinde** görüntülenir. Pencereyi açmak için aşağıdaki yöntemlerden birini kullanın:

- Diğer Öğeleri  >  **Görüntüle'Windows**  >  **Python Ortamları menü** komutunu seçin.
- Çözüm Gezgini'da **bir** proje için Python Ortamları **düğümüne sağ tıklayın ve Tüm** Python **Ortamlarını Görüntüle'yi seçin:**

::: moniker range="vs-2017"
   ![Çözüm Gezgini-2017'de Tüm Ortamları Görüntüle komutu](media/environments/environments-view-all.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Çözüm Gezgini-2019'da Tüm Ortamları Görüntüle komutu](media/environments/environments-view-all-2019.png)
::: moniker-end
::: moniker range=">=vs-2022"
   ![Çözüm Gezgini-2022'de Tüm Ortamları Görüntüle komutu](media/environments/environments-view-all-2022.png)
::: moniker-end

Tüm bu durumlarda Python Ortamları **penceresi,** aşağıdakilerle **Çözüm Gezgini:**

::: moniker range="vs-2017"
   ![Python Ortamları penceresi-2017](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Python Ortamları penceresi-2019](media/environments/environments-default-view-2019.png)
::: moniker-end
::: moniker range=">=vs-2022"
   ![Python Ortamları penceresi-2022](media/environments/environments-default-view-2022.png)
::: moniker-end

Visual Studio kayıt defteri [(PEP 514'ü](https://www.python.org/dev/peps/pep-0514/)takip eder) ve sanal ortamlar ve conda ortamları (bkz. Ortam türleri) kullanılarak yüklü genel [ortamların yanı](#types-of-environments)sıra, Beklenen bir ortamı listede görmüyorsanız bkz. Mevcut [ortamı el ile tanımlama.](#manually-identify-an-existing-environment)

Listeden bir ortam seçerek Visual Studio genel bakış sekmesinde bu ortam için çeşitli özellikler ve **komutlar** görüntülenir.

:::moniker range="vs-2017"
 Örneğin yukarıdaki görüntüde yorumlayıcının konumunun **C:\Python36-32 olduğunu görebilirsiniz.** Genel Bakış sekmesinin alt kısmında yer **alan dört komutun** her biri yorumlayıcı çalıştırarak bir komut istemi açar. Daha fazla bilgi için [bkz. Python Ortamları pencere sekmesi başvurusu 2017- Genel Bakış.](python-environments-window-tab-reference.md#overview-tab)
:::moniker-end

:::moniker range="vs-2019"
 Örneğin yukarıdaki görüntüde yorumlayıcının konumunun **C:\Python36-32 olduğunu görebilirsiniz.** Genel Bakış sekmesinin alt kısmında yer **alan dört komutun** her biri yorumlayıcı çalıştırarak bir komut istemi açar. Daha fazla bilgi için [bkz. Python Ortamları pencere sekmesi başvurusu 2019- Genel Bakış.](python-environments-window-tab-reference.md#overview-tab)
:::moniker-end

:::moniker range="vs-2022"
 Örneğin, yukarıdaki görüntüde yorumlayıcının konumunun **C:\Program Files (x86)\Microsoft Visual Studio\Python310 olduğunu görebilirsiniz.** Genel Bakış sekmesinin alt kısmında yer **alan dört komutun** her biri yorumlayıcı çalıştırarak bir komut istemi açar. Daha fazla bilgi için [bkz. Python Ortamları pencere sekmesi başvurusu 2022 - Genel Bakış.](python-environments-window-tab-reference.md#overview-tab)
:::moniker-end

Paketler ve **IntelliSense** gibi farklı sekmelere geçmek için ortam **listesinin** altındaki açılan listeyi kullanın. Bu sekmeler Python Ortamları pencere [sekmesi başvurusunda da açıklanmıştır.](python-environments-window-tab-reference.md)

Ortam seçmek, hiçbir projeyle olan ilişkisini değiştirmez. Listede kalın yazıyla gösterilen varsayılan ortam, yeni projelerde Visual Studio olan ortamdır. Yeni projelerle farklı bir ortam kullanmak için Bunu yeni **projeler için varsayılan ortam yapma komutunu** kullanın. Bir proje bağlamında, her zaman belirli bir ortamı seçerek. Daha fazla bilgi için [bkz. Proje için ortam seçme](selecting-a-python-environment-for-a-project.md#how-to-select-a-python-environment-for-a-project)).

Listelenen her ortamın sağ tarafından, bu ortam için etkileşimli bir **pencere açan** bir denetimdir. (2017 Visual Studio 15.5 ve önceki sürümlerde, bu ortam için IntelliSense veritabanını yenilene başka bir denetim görünür. Veritabanıyla [ilgili ayrıntılar için Ortamlar](python-environments-window-tab-reference.md) penceresi sekmesi başvurusuna bakın.)

::: moniker range="vs-2017"
> [!Tip]
> Python Ortamları **penceresini yeterince** genişletip ortamlarınızı daha kapsamlı bir şekilde görüntüleyecek ve bu görünümle daha rahat çalışabilirsiniz.
   > ![Python Ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range="vs-2019"
> [!Tip]
> Python Ortamları **penceresini yeterince** genişletip ortamlarınızı daha kapsamlı bir şekilde görüntüleyecek ve bu görünümle daha rahat çalışabilirsiniz.
   > ![Python Ortamları penceresi genişletilmiş görünüm-2019](media/environments/environments-expanded-view-2019.png)
::: moniker-end

::: moniker range=">=vs-2022"
> [!Tip]
> Python Ortamları **penceresini yeterince** genişletip ortamlarınızı daha kapsamlı bir şekilde görüntüleyecek ve bu görünümle daha rahat çalışabilirsiniz.
  > ![Python Ortamları penceresi genişletilmiş görünüm-2022](media/environments/environments-expanded-view-2022.png)
::: moniker-end

> [!Note]
> Bu Visual Studio system-site-packages seçeneğine uygun olsa da, bunu sistem içinde değiştirmek için bir Visual Studio.

### <a name="what-if-no-environments-appear"></a>Ortam görünmüyorsa ne olur?

Ortam görünmüyorsa, bu Visual Studio konumlarda herhangi bir Python yüklemesi algılanamadı anlamına gelir. Örneğin, 2017 veya Visual Studio yüklemiş ancak Python iş yükü için yükleyici seçeneklerinde tüm yorumlayıcı seçeneklerini temizlemiş olabilirsiniz. Benzer şekilde, 2015 veya Visual Studio 2015 veya önceki bir sürümü yüklemiş ancak el ile bir yorumlayıcı yüklememişsinizdir (bkz. [Python yorumlayıcılarını yükleme).](installing-python-interpreters.md)

Bilgisayarınızda Python yorumlayıcınız olduğunu biliyorsanız ancak Visual Studio (herhangi bir sürüm) algılamadıysanız, **+ Özel** komutunu kullanarak konumunu el ile belirtin. Var olan bir ortamı el [ile tanımlama bölümüne bakın.](#manually-identify-an-existing-environment)

::: moniker range="<=vs-2017"
> [!Tip]
> Visual Studio, python 2.7.11'den 2.7.14'e yükseltme gibi mevcut yorumlayıcı güncelleştirmelerini python.org. Yükleme işlemi sırasında, eski ortam güncelleştirme yerinde olmadan önce **Python** Ortamları listesinden kaybolur.

> Ancak, dosya sistemini kullanarak bir yorumlayıcıyı ve ortamını el ile Visual Studio konum hakkında bilginiz olmayacaktır. Daha fazla bilgi için [bkz. Yorumlayıcıyı taşıma.](installing-python-interpreters.md#move-an-interpreter)
::: moniker-end

### <a name="types-of-environments"></a>Ortam türleri

Visual Studio, sanal ve conda ortamları ile çalışabilirsiniz.

#### <a name="global-environments"></a>Genel ortamlar

Her Python yüklemesi kendi genel *ortamını sürdürür.* Örneğin Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0 gibi. Bkz. [Python yorumlayıcılarını yükleme](installing-python-interpreters.md))

Her ortam belirli Python yorumlayıcısından, standart kitaplığına, önceden yüklenmiş paket kümesine ve bu ortam etkinleştirildiğinde yüklemiş olduğunuz diğer paketlerden oluşur. Bir paketi genel bir ortama yüklemek, paketi bu ortamı kullanan tüm projelerin kullanımına sunar. Ortam, dosya sisteminin korumalı bir alanında *(örneğin, c:\program dosyaları* içinde) bulunuyorsa, paketleri yüklemek için yönetici ayrıcalıkları gerekir.

Genel ortamlar, bilgisayar üzerinde tüm projeler tarafından kullanılabilir. Bu Visual Studio, bir proje için özel olarak farklı bir ortam seçmedikçe tüm projeler için kullanılan varsayılan olarak bir genel ortam seçersiniz. Daha fazla bilgi için [bkz. Proje için ortam seçme.](selecting-a-python-environment-for-a-project.md)

#### <a name="virtual-environments"></a>Sanal ortamlar

Küresel bir ortamda çalışmak, çalışmaya başlamanın kolay bir yoludur. Zamanla ortamlar, farklı projeler için yüklemiş olduğunuz birçok farklı paketle dağınık hale gelir. Bu tür dağınıklıklar, uygulamalarınızı bilinen sürümlere sahip belirli bir paket kümesine karşı ayrıntılı bir şekilde test etmek için zorlaştırır. Ancak, ortam, bir derleme sunucusu veya web sunucusu üzerinde ayar varsayılan olarak yukarıdakiyle aynı şekildedir. İki proje uyumsuz paketler veya aynı paketin farklı sürümlerine ihtiyaç olduğunda da çakışmalar oluşabilir.

Bu nedenle geliştiriciler genellikle bir proje için *sanal ortam* oluşturabilir. Sanal ortam, projesinde belirli bir yorumlayıcının kopyasını içeren bir alt klasördir. Sanal ortamı etkinleştirirsanız, yüklemiş olduğunu tüm paketler yalnızca o ortamın alt klasörüne yüklenir. Daha sonra bu ortamda bir Python programı çalıştırarak yalnızca bu belirli paketlerde çalıştırılanın olduğunu bilirsiniz.

Visual Studio proje için sanal ortam oluşturmaya yönelik doğrudan destek sağlar. Örneğin, *requirements.txt* içeren bir proje açar veya bu dosyayı içeren bir şablondan proje oluşturursanız, Visual Studio otomatik olarak bir sanal ortam oluşturmanız ve bu bağımlılıkları yüklemeniz istenir.

Açık bir proje içinde herhangi bir zamanda yeni bir sanal ortam oluşturabilirsiniz. Bu **Çözüm Gezgini** proje düğümünü genişletin, Python Ortamları'ne **sağ tıklayın ve Ortam** **ekle'yi seçin.** Ortam **Ekle'de** Sanal **ortam'ı seçin.**

:::moniker range="vs-2019"
 Daha fazla bilgi için [bkz. Sanal ortam oluşturma-2019](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1).
:::moniker-end
:::moniker range=">=vs-2022"
Daha fazla bilgi için [bkz. Sanal ortam oluşturma-2022](./selecting-a-python-environment-for-a-project.md?view=vs-2022&preserve-view=true#create-a-virtual-environment-1).
:::moniker-end

Visual Studio sanal ortamdan bir *requirements.txt* dosyası oluşturmak için bir komut da sağlar, bu da ortamı diğer bilgisayarlarda yeniden oluşturmayı kolaylaştırır. Daha fazla bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

#### <a name="conda-environments"></a>Conda ortamları

Conda ortamı, aracı kullanarak veya `conda` Visual Studio 2017 sürüm 15.7 ve üzerinde tümleşik conda yönetimiyle oluşturabilirsiniz. (Anaconda veya Miniconda gerektirir; bu yükleyici Visual Studio kullanılabilir, bkz. [Yükleme Visual Studio 2017](installing-python-support-in-visual-studio.md#visual-studio-2017)

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
    | Adı | Conda ortamının adı. |
    | 'den paket ekleme | Bağımlılıklarınızı **açıklayan** bir *environment.yml* dosyanız varsa Ortam dosyası'yı seçin veya Bir veya daha fazla **Anaconda** paket adı'ı seçin ve aşağıdaki alanda en az bir Python paketi veya Python sürümü listelenin. Paket listesi conda'ya bir Python ortamı oluşturma talimatı sağlar. Python'ın en son sürümünü yüklemek için `python` kullanın; belirli bir sürümü yüklemek için içinde `python=,major>.<minor>` olduğu gibi `python=3.7` kullanın. Bir menü dizisinde Python sürümlerini ve ortak paketleri seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarlayın | Ortam oluşturulduktan sonra seçilen projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarlayın | Conda ortamını otomatik olarak ayarlar ve bu ortamda oluşturulan yeni projelerde Visual Studio. Bu seçenek, Python Ortamları **penceresindeki Yeni projeler için bunu varsayılan ortam yapma** seçeneğinin **kullanımıyla aynıdır.** |
    | Python Ortamlarında Görüntüle penceresi | Ortamı oluşturdukktan sonra Python Ortamları **penceresinin** gösterip göstermey kararını belirtir. |

    > [!Important]
    > Conda ortamı oluştururken, ortamın bir Python çalışma zamanı içerdiğini sağlayan veya paket listesini kullanarak en az bir Python sürümü veya Python paketi `environments.yml` belirttiğinizden emin olun. Aksi Visual Studio yoksayıyorsa: ortam **Python** Ortamları penceresinin herhangi bir yerinde görünmez, bir projenin geçerli ortamı olarak ayarlanmıyor ve genel bir ortam olarak kullanılamaz.
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
    | Adı | Conda ortamının adı. |
    | 'den paket ekleme | Bağımlılıklarınızı **açıklayan** bir *environment.yml* dosyanız varsa Ortam dosyası'yı seçin veya Bir veya daha fazla **Anaconda** paket adı'ı seçin ve aşağıdaki alanda en az bir Python paketi veya Python sürümü listelenin. Paket listesi conda'ya bir Python ortamı oluşturma talimatı sağlar. Python'ın en son sürümünü yüklemek için `python` kullanın; belirli bir sürümü yüklemek için içinde `python=,major>.<minor>` olduğu gibi `python=3.7` kullanın. Bir menü dizisinde Python sürümlerini ve ortak paketleri seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarlayın | Ortam oluşturulduktan sonra seçilen projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarlayın | Conda ortamını otomatik olarak ayarlar ve bu ortamda oluşturulan yeni projelerde Visual Studio. Bu seçenek, Python Ortamları **penceresindeki Yeni projeler için bunu varsayılan ortam yapma** seçeneğinin **kullanımıyla aynıdır.** |
    | Python Ortamlarında Görüntüle penceresi | Ortamı oluşturdukktan sonra Python Ortamları **penceresinin** gösterip göstermey kararını belirtir. |

    > [!Important]
    > Conda ortamı oluştururken, ortamın bir Python çalışma zamanı içerdiğini sağlayan veya paket listesini kullanarak en az bir Python sürümü veya Python paketi `environments.yml` belirttiğinizden emin olun. Aksi Visual Studio yoksayıyorsa: ortam **Python** Ortamları penceresinin herhangi bir yerinde görünmez, bir projenin geçerli ortamı olarak ayarlanmıyor ve genel bir ortam olarak kullanılamaz.
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

1. Alanlar istediğiniz değerleri içerdiği zaman, yapılandırmayı kaydetmek **için Uygula'ya** tıklayın. Artık ortamı, ortam içindeki diğer tüm Visual Studio.

1. El ile tanımlanan bir ortamı kaldırmanız gerekirse Yapılandır **sekmesinde Kaldır** **komutunu** seçin. Otomatik olarak algılanan ortamlar bu seçeneği sağlamaz. Daha fazla bilgi için [bkz. Yapılandırma sekmesi.](python-environments-window-tab-reference.md#configure-tab)

::: moniker-end

::: moniker range="vs-2019"

1. Ortam Ekle iletişim kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) Ortam **Ekle...** **öğesini** seçin.

1. Ortam ekle iletişim kutusunda Mevcut ortam **sekmesini** seçin:

   ![Ortam ekle iletişim kutusundaki mevcut ortam sekmesi-2019](media/environments/environments-custom-1-2019.png)

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

    Örneğin, anaconda 2021.05 C:\Users\user\Anaconda3\python.exe

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
- [Bağımlılıklar requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
