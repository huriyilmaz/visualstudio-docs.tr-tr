---
title: Python ortamlarını ve yorumlayıcılarını yönetme
description: Python Ortamları penceresini kullanarak genel, sanal ve conda ortamlarını yönetin, Python yorumlayıcılarını ve paketlerini yükleyerek ve ortamlarınızı Visual Studio attayın.
ms.date: 08/06/2019
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 34f9df6d67307584de4084c92fd264405dd88f11
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129967710"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Visual Studio'de Python ortamları oluşturma ve yönetme

**Python ortamı,** Python kodunu çalıştırarak genel, sanal ve conda ortamlarını içeren bir bağlamdır. Ortam bir yorumlayıcı, bir kitaplık (genellikle Python Standart Kitaplığı) ve yüklü paketlerden oluşur. Bu bileşenler birlikte hangi dil yapılarını ve söz dizimlerini geçerli olduğunu, hangi işletim sistemi işlevlerine erişebilirsiniz ve hangi paketleri kullanabileceğini belirler.

Bu Visual Studio Windows, ortamları yönetmek ve yeni projeler için varsayılan olarak birini seçmek için bu makalede açıklandığı gibi **Python** Ortamları penceresini kullanırsınız. Ortamların diğer yönleri aşağıdaki makalelerde bulunabilir:

- Herhangi bir proje için [varsayılanı kullanmak yerine belirli bir](selecting-a-python-environment-for-a-project.md) ortamı seçin.

- Python projeleri için sanal ortam oluşturma ve kullanma hakkında ayrıntılı bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

- Paketleri bir ortama yüklemek için Paketler sekmesi [başvurusuna bakın.](python-environments-window-tab-reference.md#packages-tab)

- Başka bir Python yorumlayıcı yüklemek için [bkz. Python yorumlayıcılarını yükleme.](installing-python-interpreters.md) Genel olarak, ana Python dağıtımı için bir yükleyici indirip çalıştırıyorsanız, Visual Studio yeni yüklemenin ve ortamın **Python** Ortamları penceresinde görüntülendiğinden ve projeler için seçilene olduğunu algılar.

Python'da yeni bir Visual Studio, aşağıdaki makaleler de genel arka planda sağlar:

- [Visual Studio'de Python ile çalışma](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio’da Python desteğini yükleme](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Python kodu için yalnızca klasör olarak açılan ortamları Dosya Klasör Aç komutunu **kullanarak**  >  **yönetebilirsiniz.**  >   Bunun [yerine, ortamın ortam özelliklerinden keyif almak için](quickstart-01-python-in-visual-studio-project-from-existing-code.md) mevcut koddan bir Python Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Klasör olarak açılan Python kodu ortamlarını Dosya Klasör Aç **komutunu**  >  **kullanarak**  >  **yönetebilirsiniz.** Python araç çubuğu, algılanan tüm ortamlar arasında geçiş ve yeni bir ortam eklemenize olanak tanır. Ortam bilgileri Workspace .vs klasöründeki PythonSettings.json dosyasında depolanır.
::: moniker-end

## <a name="the-python-environments-window"></a>Python Ortamları penceresi

Hakkında Visual Studio ortamlar Python Ortamları **penceresinde** görüntülenir. Pencereyi açmak için aşağıdaki yöntemlerden birini kullanın:

- Diğer Öğeleri  >  **Görüntüle'Windows**  >  **Python Ortamları menü** komutunu seçin.
- Çözüm Gezgini'da **bir** projenin Python Ortamları **düğümüne sağ tıklayın ve** Tüm Python **Ortamlarını Görüntüle'yi seçin:**

    ::: moniker range="vs-2017"
    ![Görünüm Tüm Ortamlar komutu Çözüm Gezgini](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Görünüm Tüm Ortamlar komutu Çözüm Gezgini](media/environments/environments-view-all-2019.png)
    ::: moniker-end

Her iki durumda da **Python Ortamları penceresi,** **Çözüm Gezgini:**

::: moniker range="vs-2017"
![Python Ortamları penceresi](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamları penceresi](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio, sanal ortamlar ve conda ortamları (bkz. Ortam türleri) ile birlikte kayıt defterini [(PEP 514'ü](https://www.python.org/dev/peps/pep-0514/)takip eder) kullanarak yüklü genel [ortamları da bulun.](#types-of-environments) Beklenen bir ortamı listede görmüyorsanız bkz. Mevcut [ortamı el ile tanımlama.](#manually-identify-an-existing-environment)

Listeden bir ortam seçerek Visual Studio genel bakış sekmesinde bu ortam için çeşitli özellikler ve **komutlar** görüntülenir. Örneğin yukarıdaki görüntüde yorumlayıcının konumunun *C:\Python36-32 olduğunu görebilirsiniz.* Genel Bakış sekmesinin alt kısmında yer **alan dört komutun** her biri yorumlayıcı çalıştırarak bir komut istemi açar. Daha fazla bilgi için [bkz. Python Ortamları pencere sekmesi başvurusu - Genel Bakış.](python-environments-window-tab-reference.md#overview-tab)

Paketler ve **IntelliSense** gibi farklı sekmelere geçmek için ortam **listesinin** altındaki açılan listeyi kullanın. Bu sekmeler Python Ortamları pencere [sekmesi başvurusunda da açıklanmıştır.](python-environments-window-tab-reference.md)

Ortam seçmek, hiçbir projeyle olan ilişkisini değiştirmez. Listede kalın yazıyla gösterilen varsayılan ortam, yeni projeler için Visual Studio olan ortamdır. Yeni projelerle farklı bir ortam kullanmak için Bunu yeni **projeler için varsayılan ortam yapma komutunu** kullanın. Proje bağlamında istediğiniz zaman belirli bir ortamı da kullanabilirsiniz. Daha fazla bilgi için [bkz. Proje için ortam seçme.](selecting-a-python-environment-for-a-project.md)

Listelenen her ortamın sağ tarafından, bu ortam için etkileşimli bir **pencere açan** bir denetim vardır. (2017 Visual Studio 15.5 ve önceki sürümlerde, bu ortam için IntelliSense veritabanını yenilene başka bir denetim görünür. Veritabanıyla [ilgili ayrıntılar için Ortamlar](python-environments-window-tab-reference.md) penceresi sekmesi başvurusuna bakın.)

::: moniker range="vs-2017"
> [!Tip]
> Python Ortamları penceresini **yeterince genişletip** ortamlarınızı daha kapsamlı bir şekilde görüntüleyecek ve bu görünümle daha rahat çalışabilirsiniz.
>
> ![Python Ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> Python Ortamları penceresini **yeterince genişletip** ortamlarınızı daha kapsamlı bir şekilde görüntüleyecek ve bu görünümle daha rahat çalışabilirsiniz.
>
> ![Python Ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Bu Visual Studio system-site-packages seçeneğine uygun olsa da, bunu sistem içinde değiştirmek için bir Visual Studio.

### <a name="what-if-no-environments-appear"></a>Ortam görünmüyorsa ne olur?

Ortam görünmüyorsa, bu Visual Studio konumlarda herhangi bir Python yüklemesi algılanamadı anlamına gelir. Örneğin, 2017 veya Visual Studio yüklemiş ancak Python iş yükü için yükleyici seçeneklerinde tüm yorumlayıcı seçeneklerini temizlemiş olabilirsiniz. Benzer şekilde, 2015 veya Visual Studio ancak el ile bir yorumlayıcı yüklememiş olabilir (bkz. [Python yorumlayıcılarını yükleme).](installing-python-interpreters.md)

Bilgisayarınızda Python yorumlayıcınız olduğunu biliyorsanız ancak Visual Studio (herhangi bir sürüm) algılamadıysanız, **+ Özel** komutunu kullanarak konumunu el ile belirtin. Var olan bir ortamı el [ile tanımlama bölümüne bakın.](#manually-identify-an-existing-environment)

::: moniker range="<=vs-2017"

> [!Tip]
> Visual Studio, python 2.7.11'den 2.7.14'e yükseltme gibi mevcut yorumlayıcı güncelleştirmelerini python.org. Yükleme işlemi sırasında, eski ortam güncelleştirme yerinde olmadan önce **Python** Ortamları listesinden kaybolur.
>
> Ancak, dosya sistemini kullanarak bir yorumlayıcıyı ve ortamını el ile Visual Studio konum hakkında bilginiz olmayacaktır. Daha fazla bilgi için [bkz. Yorumlayıcıyı taşıma.](installing-python-interpreters.md#move-an-interpreter)
::: moniker-end

### <a name="types-of-environments"></a>Ortam türleri

Visual Studio, sanal ve conda ortamları ile çalışabilirsiniz.

#### <a name="global-environments"></a>Genel ortamlar

Her Python yüklemesi (örneğin, Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0 vb., bkz. [Python yorumlayıcılarını](installing-python-interpreters.md)yükleme) kendi genel ortamını *sürdürür.* Her ortam belirli Python yorumlayıcısından, standart kitaplığına, önceden yüklenmiş paket kümesine ve bu ortam etkinleştirildiğinde yüklemiş ek paketlerden oluşur. Bir paketi genel bir ortama yüklemek, paketi bu ortamı kullanan tüm projelerin kullanımına sunar. Ortam, dosya sisteminin korumalı bir alanında *(örneğin, c:\program dosyaları* içinde) bulunuyorsa, paketleri yüklemek için yönetici ayrıcalıkları gerekir.

Genel ortamlar, bilgisayar üzerinde tüm projeler tarafından kullanılabilir. Bu Visual Studio, bir proje için özel olarak farklı bir ortam seçmedikçe tüm projeler için kullanılan varsayılan olarak bir genel ortam seçersiniz. Daha fazla bilgi için [bkz. Proje için ortam seçme.](selecting-a-python-environment-for-a-project.md)

#### <a name="virtual-environments"></a>Sanal ortamlar

Küresel bir ortamda çalışmak, çalışmaya başlamanın kolay bir yolu olsa da, bu ortam zaman içinde farklı projeler için yüklemiş olduğunuz birçok farklı paketle karmaşık hale gelir. Bu tür dağınıklıklar, uygulamanın bilinen sürümlere sahip belirli bir paket kümesine karşı kapsamlı bir şekilde test sınanmasını zorlaştırır. Bu, derleme sunucusunda veya web sunucusunda tam olarak ayarlayışınız ortam t türlerindedir. İki proje uyumsuz paketler veya aynı paketin farklı sürümlerini gerektirirken de çakışmalar oluşabilir.

Bu nedenle geliştiriciler genellikle bir proje için *sanal ortam* oluşturabilir. Sanal ortam, projesinde belirli bir yorumlayıcının kopyasını içeren bir alt klasördir. Sanal ortamı etkinleştirerek, yüklemiş olduğunuz tüm paketler yalnızca o ortamın alt klasörüne yüklenir. Ardından bu ortamda bir Python programı çalıştırsanız, yalnızca bu belirli paketlere karşı çalıştırılı olduğunu bilirsiniz.

Visual Studio proje için sanal ortam oluşturmaya yönelik doğrudan destek sağlar. Örneğin, *requirements.txt* içeren bir proje açar veya bu dosyayı içeren bir şablondan proje oluşturursanız, Visual Studio otomatik olarak bir sanal ortam oluşturmanız ve bu bağımlılıkları yüklemeniz istenir.

Açık bir proje içinde herhangi bir zamanda yeni bir sanal ortam oluşturabilirsiniz. Bu **Çözüm Gezgini** proje düğümünü genişletin, Python Ortamları'ne sağ **tıklayın** ve "Sanal Ortam Ekle"yi seçin. Daha fazla bilgi için [bkz. Sanal ortam oluşturma.](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1)

Visual Studio sanal ortamdan bir *requirements.txt* dosyası oluşturmak için bir komut da sağlar, bu da ortamı diğer bilgisayarlarda yeniden oluşturmayı kolaylaştırır. Daha fazla bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

#### <a name="conda-environments"></a>Conda ortamları

Conda ortamı, araç kullanılarak veya `conda` 2017 sürüm 15.7 ve Visual Studio tümleşik conda yönetimi ile oluşturulur. (Anaconda veya Miniconda gerektirir; bu, Visual Studio yükleyicisi aracılığıyla kullanılabilir, [bkz. Yükleme.)](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017)

::: moniker range="vs-2017"

1. Python **Ortamları penceresinde + Conda** ortamı **oluştur'a tıklayın.** Bu pencerede Yeni **conda ortamı oluştur sekmesi** açılır:

    ![Yeni conda ortamı için sekme oluşturma](media/environments/environments-conda-1.png)

1. Ad alanına ortam için bir ad **girin,** Python alanında temel bir Python yorumlayıcı seçin ve **Oluştur'a** **basın.**

1. Çıkış **penceresi,** oluşturma işlemi tamamlandıktan sonra birkaç CLI yönergeleriyle birlikte yeni ortamın ilerlemesini gösterir:

    ![Conda ortamının başarıyla oluşturulması](media/environments/environments-conda-2.png)

1. Bu Visual Studio proje için Bir ortam seçin konusunda açıklandığı gibi bir proje için conda ortamını etkinleştirerek diğer tüm [ortamlar gibi etkinleştirabilirsiniz.](selecting-a-python-environment-for-a-project.md)

1. Ortama paket yüklemek için Paketler sekmesini [kullanın.](python-environments-window-tab-reference.md#packages-tab)
::: moniker-end

::: moniker range=">=vs-2019"

1. Ortam Ekle iletişim kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) Ortam **Ekle...** **öğesini** seçin. Bu iletişim kutusunda **Conda ortamı sekmesini** seçin:

    ![Ortam ekle iletişim kutusundaki Conda ortamı sekmesi](media/environments/environments-conda-1-2019.png)

1. Aşağıdaki alanları yapılandırma:

    | Alan | Açıklama |
    | --- | --- |
    | Project | ortamın oluşturulacağı proje (aynı Visual Studio çözümünde birden çok projeniz varsa). |
    | Name | Conda ortamının adı. |
    | Paket ekle | Bağımlılıklarınızı tanımlayan bir *Environment. yıml* dosyanız varsa **ortam dosyası** ' nı seçin veya **bir veya daha fazla Anaconda paketi adı** seçin ve en az bir Python paketi veya aşağıdaki alanda bir Python sürümü listeleyin. Paket listesi, Conda 'ın Python ortamı oluşturmasını söyler. Python 'un en son sürümünü yüklemek için; kullanın `python` ; belirli bir sürümü yüklemek için `python=,major>.<minor>` içinde olarak kullanın `python=3.7` . Ayrıca, bir dizi menüden Python sürümlerini ve ortak paketleri seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarla | Ortam oluşturulduktan sonra seçili projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarla | , Visual Studio ' de oluşturulan tüm yeni projelerde Conda ortamını otomatik olarak ayarlar ve etkinleştirir. Bu seçenek, **Python ortamları** penceresinde **yeni projeler için bu varsayılan ortamı yap** ' ın kullanılmasıyla aynıdır. |
    | Python ortamları penceresinde görüntüle | Ortamı oluşturduktan sonra  **Python ortamları** penceresinin gösterilip gösterilmeyeceğini belirtir. |

    > [!Important]
    > Bir Conda ortamı oluştururken, ya da paket listesini kullanarak en az bir Python sürümü veya Python paketi belirttiğinizden emin olun `environments.yml` . Bu, ortamın bir Python çalışma zamanı içerdiğinden emin olmanızı sağlar. aksi takdirde, Visual Studio ortamı yoksayar: ortam, **Python ortamları** penceresinde hiçbir yerde görünmez, bir proje için geçerli ortam olarak ayarlanmamış ve genel bir ortam olarak kullanılamıyor.
    >
    > Python sürümü olmadan bir Conda ortamı oluşturursanız, `conda info` Conda ortam klasörlerinin konumlarını görmek için komutunu kullanın, ardından ortamın alt klasörünü bu konumdan el ile kaldırın.

1. **Oluştur**' u seçin ve **Çıkış** penceresinde ilerlemeyi gözlemleyin. Çıktı, oluşturma işlemi tamamlandıktan sonra birkaç CLı yönergesi içerir:

    ![Conda ortamının başarıyla oluşturulması](media/environments/environments-conda-2-2019.png)

1. Visual Studio içinde, proje için bir [ortam seçin](selecting-a-python-environment-for-a-project.md)bölümünde açıklandığı gibi bir proje için conda ortamını etkinleştirebilirsiniz.

1. Ortama ek paketler yüklemek için [paketler sekmesini](python-environments-window-tab-reference.md#packages-tab)kullanın.
::: moniker-end

> [!Note]
> Conda ortamlarındaki en iyi sonuçları elde etmek için Conda 4.4.8 veya üstünü kullanın (Conda sürümleri, Anaconda sürümlerinden farklıdır). Visual Studio yükleyicisi aracılığıyla miniconda (Visual Studio 2019) ve anaconda (Visual Studio 2017) için uygun sürümleri yükleyebilirsiniz.

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

standart olmayan bir konumda yüklü olan bir ortamı (Visual Studio 2017 sürüm 15,6 ve önceki sürümlerde bulunan conda dahil olmak üzere) tanımlamak için aşağıdaki adımları kullanın:

::: moniker range="vs-2017"

1. **Yapılandırma** sekmesini açan **Python ortamları** penceresinde **+ özel** ' i seçin:

    ![Yeni bir özel ortam için varsayılan görünüm](media/environments/environments-custom-1.png)

1. **Açıklama** alanına ortam için bir ad girin.

1. **Önek yolu** alanındaki yorumlayıcı yolunun yolunu ( **.**..) girin veya buraya gidin.

1. Visual Studio bu konumda bir Python yorumlayıcı algılarsa (bir conda ortamı için aşağıda gösterilen yol gibi), **otomatik algıla** komutu etkinleştirilir. **Otomatik algılamayı** seçmek kalan alanları tamamlar. Ayrıca, bu alanları el ile de tamamlayabilirsiniz.

    ![Auto Detect komutunu etkinleştirme](media/environments/environments-custom-2.png)

    ![Otomatik Algıla kullanıldıktan sonra ortam alanlarını tamamlama](media/environments/environments-custom-3.png)

1. Alanlar istediğiniz değerleri içeriyorsa, yapılandırmayı kaydetmek için **Uygula** ' yı seçin. Artık Visual Studio içindeki diğer gibi ortamı kullanabilirsiniz.

1. El ile tanımlanmış bir ortamı kaldırmanız gerekiyorsa, **Yapılandır** sekmesinde **Kaldır** komutunu seçin. Otomatik algılanan ortamlar bu seçeneği sağlamaz. Daha fazla bilgi için bkz. [Configure Tab](python-environments-window-tab-reference.md#configure-tab).

::: moniker-end

::: moniker range=">=vs-2019"

1. **Python ortamları** penceresinde (veya Python araç çubuğundan) ortam **Ekle Iletişim kutusunu** açan **ortam ekle...** seçeneğini belirleyin. Bu iletişim kutusunda, **var olan ortam** sekmesini seçin:

    ![Ortam Ekle iletişim kutusunda var olan ortam sekmesi](media/environments/environments-custom-1-2019.png)

1. **Ortam** açılan öğesini seçin ve ardından **özel**' i seçin:

    ![Ortam Ekle iletişim kutusunda özel ortam seçeneği](media/environments/environments-custom-2-2019.png)

1. İletişim kutusundaki belirtilen alanlarda, diğer alanların çoğunu dolduran **ön ek yolu** altındaki yorumlayıcı yoluna ( **.**..) girin veya bu yolu inceleyin. Bu değerleri inceledikten ve gerektiğinde değiştirdikten sonra **Ekle**' yi seçin.

    ![Ortam Ekle iletişim kutusunda özel ortam seçeneğinin ayrıntılarını belirtme alanları](media/environments/environments-custom-3-2019.png)

1. Ortam ayrıntıları, **Python ortamları** penceresinde herhangi bir zamanda incelenebilir ve değiştirilebilir. Bu pencerede, ortamı seçin ve ardından **Yapılandır** sekmesini seçin. Değişiklik yaptıktan sonra **Uygula** komutunu seçin. Ayrıca **Remove** komutunu kullanarak ortamı kaldırabilirsiniz (otomatik algılanan ortamlar için kullanılamaz). Daha fazla bilgi için bkz. [Configure Tab](python-environments-window-tab-reference.md#configure-tab).
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Geçersiz ortamları çözme veya silme

Visual Studio bir ortamın kayıt defteri girişlerini bulursa, ancak yorumlayıcı yolu geçersizse, **Python ortamları** penceresi adı bir üstü çizili yazı tipiyle gösterir:

::: moniker range="vs-2017"
![Geçersiz bir ortamı gösteren Python ortamları penceresi](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Geçersiz bir ortamı gösteren Python ortamları penceresi](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Tutmak istediğiniz bir ortamı düzeltmek için öncelikle yükleyicinin **onarma** işlemini kullanmayı deneyin. Standart Python 3. x yükleyicileri, örneğin, bu seçeneği içerir.

Onarma seçeneği olmayan bir ortamı düzeltmek veya geçersiz bir ortamı kaldırmak için, kayıt defterini doğrudan değiştirmek için aşağıdaki adımları kullanın. Visual Studio, kayıt defterinde değişiklik yaptığınızda **Python ortamları** penceresini otomatik olarak güncelleştirir.

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