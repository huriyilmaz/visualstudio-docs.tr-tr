---
title: Python ortamlarını ve yorumlayıcılarını yönetme
description: Python Ortamları penceresini kullanarak genel, sanal ve conda ortamlarını yönetin, Python yorumlayıcılarını ve paketlerini yükleyerek ve ortamlarınızı Visual Studio attayın.
ms.date: 08/06/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: e75f433c3949ecb623dbe14ee7289060f7cc463b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625370"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Visual Studio'da Python ortamları oluşturma ve yönetme

**Python ortamı,** Python kodunu çalıştırarak genel, sanal ve conda ortamlarını içeren bir bağlamdır. Ortam bir yorumlayıcı, kitaplık (genellikle Python Standart Kitaplığı) ve yüklü paketlerden oluşur. Bu bileşenler birlikte hangi dil yapılarını ve söz dizimlerini geçerli olduğunu, hangi işletim sistemi işlevlerine erişebilirsiniz ve hangi paketleri kullanabileceğini belirler.

Bu Visual Studio Windows, ortamları yönetmek ve yeni projeler için varsayılan olarak birini seçmek için bu makalede açıklandığı gibi **Python** Ortamları penceresini kullanırsınız. Ortamların diğer yönleri aşağıdaki makalelerde bulunabilir:

- Herhangi bir proje için [varsayılanı kullanmak yerine belirli bir](selecting-a-python-environment-for-a-project.md) ortamı seçin.

- Python projeleri için sanal ortam oluşturma ve kullanma hakkında ayrıntılı bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

- Paketleri bir ortama yüklemek için Paketler sekmesi [başvurusuna bakın.](python-environments-window-tab-reference.md#packages-tab)

- Başka bir Python yorumlayıcı yüklemek için [bkz. Python yorumlayıcılarını yükleme.](installing-python-interpreters.md) Genel olarak, ana Python dağıtımı için bir yükleyici indirip çalıştırıyorsanız, Visual Studio yeni yüklemenin ve ortamın **Python** Ortamları penceresinde görüntülendiğinden ve projeler için seçilene olduğunu algılar.

Python'da yeniydiniz Visual Studio aşağıdaki makaleler de genel arka planda sağlar:

- [Visual Studio'da Python ile çalışma](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio’da Python desteğini yükleme](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> Python kodu için yalnızca klasör olarak açılan ortamları Dosya Klasör Aç komutunu **kullanarak**  >  **yönetebilirsiniz.**  >   Bunun [yerine, ortamın ortam özelliklerinden keyif almak için](quickstart-01-python-in-visual-studio-project-from-existing-code.md) mevcut koddan bir Python Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Klasör olarak açılan Python kodu ortamlarını Dosya Klasör Aç **komutunu**  >  **kullanarak**  >  **yönetebilirsiniz.** Python araç çubuğu, algılanan tüm ortamlar arasında geçiş yapmak ve yeni bir ortam eklemek için kullanılabilir. Ortam bilgileri Workspace .vs klasöründeki PythonSettings.json dosyasında depolanır.
::: moniker-end

## <a name="the-python-environments-window"></a>Python Ortamları penceresi

Hakkında Visual Studio ortamlar Python Ortamları **penceresinde** görüntülenir. Pencereyi açmak için aşağıdaki yöntemlerden birini kullanın:

- Diğer Öğeleri  >  **Görüntüle'Windows**  >  **Python Ortamları menü** komutunu seçin.
- Çözüm Gezgini'da **bir** projenin Python Ortamları düğümüne **sağ tıklayın ve** Tüm Python **Ortamlarını Görüntüle'yi seçin:**

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

Visual Studio, sanal ortamlar ve conda ortamları (bkz. Ortam türleri) ile birlikte kayıt defterini kullanarak [(PEP 514'ü](https://www.python.org/dev/peps/pep-0514/)takip eder) yüklü genel [ortamları da bulun.](#types-of-environments) Beklenen bir ortamı listede görmüyorsanız bkz. Mevcut [ortamı el ile tanımlama.](#manually-identify-an-existing-environment)

Listeden bir ortam seçerek Visual Studio genel bakış sekmesinde bu ortam için çeşitli özellikler ve **komutlar** görüntülenir. Örneğin yukarıdaki görüntüde yorumlayıcının konumunun *C:\Python36-32 olduğunu görebilirsiniz.* Genel Bakış sekmesinin alt kısmında yer **alan dört komutun** her biri yorumlayıcı çalıştırarak bir komut istemi açar. Daha fazla bilgi için [bkz. Python Ortamları pencere sekmesi başvurusu - Genel Bakış.](python-environments-window-tab-reference.md#overview-tab)

Paketler ve **IntelliSense** gibi farklı sekmelere geçmek için ortam **listesinin** altındaki açılan listeyi kullanın. Bu sekmeler Python Ortamları pencere [sekmesi başvurusunda da açıklanmıştır.](python-environments-window-tab-reference.md)

Ortam seçmek, hiçbir projeyle olan ilişkisini değiştirmez. Listede kalın yazıyla gösterilen varsayılan ortam, yeni projelerde Visual Studio olan ortamdır. Yeni projelerle farklı bir ortam kullanmak için Bunu yeni **projeler için varsayılan ortam yapma komutunu** kullanın. Proje bağlamında istediğiniz zaman belirli bir ortamı da kullanabilirsiniz. Daha fazla bilgi için [bkz. Proje için ortam seçme.](selecting-a-python-environment-for-a-project.md)

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

> [!Tip]
> Visual Studio, Python 2.7.11'den 2.7.14 sürümüne yükseltme gibi mevcut yorumlayıcı güncelleştirmelerini python.org. Yükleme işlemi sırasında, eski ortam güncelleştirme yerinde olmadan önce **Python** Ortamları listesinden kaybolur.
>
> Ancak, dosya sistemini kullanarak bir yorumlayıcıyı ve ortamını el ile Visual Studio konum hakkında bilginiz olmayacaktır. Daha fazla bilgi için [bkz. Yorumlayıcıyı taşıma.](installing-python-interpreters.md#move-an-interpreter)

### <a name="types-of-environments"></a>Ortam türleri

Visual Studio, sanal ve conda ortamları ile çalışabilirsiniz.

#### <a name="global-environments"></a>Genel ortamlar

Her Python yüklemesi (örneğin, Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0 vb., bkz. [Python yorumlayıcılarını](installing-python-interpreters.md)yükleme) kendi genel ortamını *sürdürür.* Her ortam belirli Python yorumlayıcısından, standart kitaplığına, önceden yüklenmiş bir paket kümesine ve bu ortam etkinleştirildiğinde yüklemiş ek paketlerden oluşur. Bir paketi genel bir ortama yüklemek, paketi bu ortamı kullanan tüm projelerin kullanımına sunar. Ortam, dosya sisteminin korumalı bir alanında *(örneğin, c:\program dosyaları* içinde) bulunuyorsa, paketleri yüklemek için yönetici ayrıcalıkları gerekir.

Genel ortamlar, bilgisayar üzerinde tüm projeler tarafından kullanılabilir. Bu Visual Studio, bir proje için özel olarak farklı bir ortam seçmedikçe tüm projeler için kullanılan varsayılan olarak bir genel ortam seçersiniz. Daha fazla bilgi için [bkz. Proje için ortam seçme.](selecting-a-python-environment-for-a-project.md)

#### <a name="virtual-environments"></a>Sanal ortamlar

Küresel bir ortamda çalışmak, çalışmaya başlamanın kolay bir yolu olsa da, bu ortam zaman içinde farklı projeler için yüklemiş olduğunuz birçok farklı paketle karmaşık hale gelir. Bu tür dağınıklıklar, uygulamanın bilinen sürümlere sahip belirli bir paket kümesine karşı kapsamlı bir şekilde test sınanmasını zorlaştırır. Bu, derleme sunucusunda veya web sunucusunda tam olarak ayarlayışınız ortam t türlerindedir. İki proje uyumsuz paketler veya aynı paketin farklı sürümlerini gerektirirken de çakışmalar oluşabilir.

Bu nedenle geliştiriciler genellikle bir proje için *sanal ortam* oluşturabilir. Sanal ortam, projesinde belirli bir yorumlayıcının kopyasını içeren bir alt klasördir. Sanal ortamı etkinleştirerek, yüklemiş olduğunuz tüm paketler yalnızca o ortamın alt klasörüne yüklenir. Ardından bu ortamda bir Python programı çalıştırsanız, yalnızca bu belirli paketlere karşı çalıştırılı olduğunu bilirsiniz.

Visual Studio proje için sanal ortam oluşturmaya yönelik doğrudan destek sağlar. Örneğin, *requirements.txt* içeren bir proje açarsanız veya bu dosyayı içeren bir şablondan proje oluşturursanız, Visual Studio otomatik olarak bir sanal ortam oluşturmanızı ve bu bağımlılıkları yüklemeniz istenir.

Açık bir proje içinde herhangi bir zamanda yeni bir sanal ortam oluşturabilirsiniz. Bu **Çözüm Gezgini** proje düğümünü genişletin, Python Ortamları'ne **sağ tıklayın** ve "Sanal Ortam Ekle"yi seçin. Daha fazla bilgi için [bkz. Sanal ortam oluşturma.](./selecting-a-python-environment-for-a-project.md?view=vs-2019&preserve-view=true#create-a-virtual-environment-1)

Visual Studio sanal ortamdan bir *requirements.txt* dosyası oluşturmak için bir komut da sağlar, bu da ortamı diğer bilgisayarlarda yeniden oluşturmayı kolaylaştırır. Daha fazla bilgi için [bkz. Sanal ortamları kullanma.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

#### <a name="conda-environments"></a>Conda ortamları

Conda ortamı, araç kullanılarak veya `conda` 2017 sürüm 15.7 ve Visual Studio tümleşik conda yönetimi ile oluşturulur. (Anaconda veya Miniconda gerektirir, bu yükleyici aracılığıyla Visual Studio, bkz. [Yükleme.)](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017)

::: moniker range="vs-2017"

1. Python **Ortamları penceresinde + Conda** ortamı **oluştur'a tıklayın.** Bu pencerede Yeni **conda ortamı oluştur sekmesi** açılır:

    ![Yeni conda ortamı için sekme oluşturma](media/environments/environments-conda-1.png)

1. Ad alanına ortam için bir ad **girin,** Python alanında temel bir Python yorumlayıcı seçin ve **Oluştur'a** **basın.**

1. Çıkış **penceresi,** oluşturma işlemi tamamlandıktan sonra birkaç CLI yönergeleriyle birlikte yeni ortamın ilerlemesini gösterir:

    ![Conda ortamının başarıyla oluşturulması](media/environments/environments-conda-2.png)

1. Bu Visual Studio proje için Bir ortam seçin konusunda açıklandığı gibi bir proje için conda [ortamını etkinleştirebileceksiniz.](selecting-a-python-environment-for-a-project.md)

1. Ortama paket yüklemek için Paketler sekmesini [kullanın.](python-environments-window-tab-reference.md#packages-tab)
::: moniker-end

::: moniker range=">=vs-2019"

1. Ortam Ekle iletişim kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) Ortam **Ekle...** **öğesini** seçin. Bu iletişim kutusunda **Conda ortamı sekmesini** seçin:

    ![Ortam ekle iletişim kutusundaki Conda ortamı sekmesi](media/environments/environments-conda-1-2019.png)

1. Aşağıdaki alanları yapılandırma:

    | Alan | Açıklama |
    | --- | --- |
    | Project | Ortamın oluşturulacak proje (aynı çözümde birden fazla projeniz Visual Studio. |
    | Name | Conda ortamının adı. |
    | 'den paket ekleme | Bağımlılıklarınızı **açıklayan** bir *environment.yml* dosyanız varsa Ortam dosyası'yı seçin veya Bir veya daha fazla **Anaconda** paket adı'ı seçin ve aşağıdaki alanda en az bir Python paketi veya Python sürümü listelenin. Paket listesi conda'ya bir Python ortamı oluşturma talimatı sağlar. Python'ın en son sürümünü yüklemek için `python` kullanın; belirli bir sürümü yüklemek için içinde `python=,major>.<minor>` olduğu gibi `python=3.7` kullanın. Bir menü dizisinde Python sürümlerini ve ortak paketleri seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarlayın | Ortam oluşturulduktan sonra seçili projede yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarlayın | Conda ortamını, Visual Studio'da oluşturulan tüm yeni projelerde otomatik olarak ayarlar ve Visual Studio. Bu seçenek, Python Ortamları **penceresindeki Yeni projeler için bunu varsayılan ortam yapma** seçeneğinin **kullanımıyla aynıdır.** |
    | Python Ortamlarında Görüntüle penceresi | Ortamı oluşturdukktan sonra Python Ortamları  **penceresinin** gösterip göstermey kararını belirtir. |

    > [!Important]
    > Conda ortamı oluştururken, ortamın bir Python çalışma zamanı içerdiğini sağlayan veya paket listesini kullanarak en az bir Python sürümü veya Python paketi `environments.yml` belirttiğinizden emin olun. Aksi Visual Studio yoksayıyorsa: ortam **Python** Ortamları penceresinin herhangi bir yerinde görünmez, projenin geçerli ortamı olarak ayarlanmıyor ve genel bir ortam olarak kullanılamaz.
    >
    > Python sürümü olmayan bir conda ortamı oluşturursanız, conda ortam klasörlerinin konumlarını görmek için komutunu kullanın ve ardından ortamın alt klasörünü bu konumdan el `conda info` ile kaldırın.

1. **Oluştur'a** tıklayın ve Çıkış penceresinde **ilerlemeyi gözlemle.** Çıkış, oluşturma işlemi tamamlandıktan sonra birkaç CLI yönergeleri içerir:

    ![Conda ortamının başarıyla oluşturulması](media/environments/environments-conda-2-2019.png)

1. Bu Visual Studio proje için bir ortam seçin konusunda açıklandığı gibi bir proje için conda [ortamını etkinleştirebileceksiniz.](selecting-a-python-environment-for-a-project.md)

1. Ortama ek paketler yüklemek için Paketler sekmesini [kullanın.](python-environments-window-tab-reference.md#packages-tab)
::: moniker-end

> [!Note]
> Conda ortamlarında en iyi sonuçları elde etmek için conda 4.4.8 veya sonraki sürümleri kullanın (conda sürümleri Anaconda sürümlerinden farklıdır). Miniconda (Visual Studio 2019) ve Anaconda 'nın (Visual Studio 2017) uygun sürümlerini Visual Studio yükleyebilirsiniz.

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

Conda ortamları bir projeyle depolanmaz, genel ortamlara benzer şekilde davranır. Örneğin, conda ortamına yeni bir paket yüklemek, bu paketi bu ortamı kullanan tüm projelerin kullanımına sunar.

2017 Visual Studio 15.6 ve önceki sürümler için conda ortamlarını, mevcut ortamı el ile tanımlama altında açıklandığı gibi el ile işaret [edersiniz.](#manually-identify-an-existing-environment)

Visual Studio 2017 sürüm 15.7 ve sonraki sürümler conda ortamlarını otomatik olarak algılar ve sonraki bölümde açıklandığı gibi **Python** Ortamları penceresinde görüntüler.

## <a name="manually-identify-an-existing-environment"></a>Mevcut ortamı el ile tanımlama

Standart olmayan bir konuma (Visual Studio 2017 sürüm 15.6 ve önceki sürümlerde conda ortamları dahil) yüklenmiş bir ortamı belirlemek için aşağıdaki adımları kullanın:

::: moniker range="vs-2017"

1. Python Ortamları penceresinde Yapılandır **sekmesini açan** **+** **Özel'i** seçin:

    ![Yeni bir özel ortam için varsayılan görünüm](media/environments/environments-custom-1.png)

1. Açıklama alanına ortam için bir **ad** girin.

1. Ön ek yolu alanında yorumlayıcının yoluna gidin  **(...** kullanarak).

1. Bu Visual Studio bir Python yorumlayıcı (conda ortamı için aşağıda gösterilen yol gibi) algılarsa, Otomatik Algıla **komutunu** sağlar. Otomatik **Algıla seçeneği,** kalan alanları tamamlar. Ayrıca bu alanları el ile de tamamabilirsiniz.

    ![Otomatik Algıla komutunu etkinleştirme](media/environments/environments-custom-2.png)

    ![Otomatik Algılama'nın kullanımından sonra ortam alanlarının tamamlanması](media/environments/environments-custom-3.png)

1. Alanlar istediğiniz değerleri içerdiği zaman, yapılandırmayı kaydetmek **için Uygula'ya** tıklayın. Artık ortamı, ortam içindeki diğer tüm ortamlar gibi Visual Studio.

1. El ile tanımlanan bir ortamı kaldırmanız gerekirse Yapılandır **sekmesinde Kaldır** **komutunu** seçin. Otomatik olarak algılanan ortamlar bu seçeneği sağlamaz. Daha fazla bilgi için [bkz. Yapılandırma sekmesi.](python-environments-window-tab-reference.md#configure-tab)

::: moniker-end

::: moniker range=">=vs-2019"

1. Ortam Ekle iletişim kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) Ortam **Ekle...** **öğesini** seçin. Bu iletişim kutusunda Mevcut ortam **sekmesini** seçin:

    ![Ortam ekle iletişim kutusundaki mevcut ortam sekmesi](media/environments/environments-custom-1-2019.png)

1. Ortam **açılan öğesini** ve ardından Özel'i **seçin:**

    ![Ortam ekle iletişim kutusundaki özel ortam seçeneği](media/environments/environments-custom-2-2019.png)

1. İletişim kutusundaki sağlanan alanlara, diğer alanların çoğunu dolduran Ön Ek yolu altındaki yorumlayıcının yoluna **(kullanarak )** gidin veya gözatın. Bu değerleri gözden geçirdikten ve gerektiğinde değiştirdikten sonra Ekle'yi **seçin.**

    ![Ortam ekle iletişim kutusundaki özel ortam seçeneğinin ayrıntılarını belirten alanlar](media/environments/environments-custom-3-2019.png)

1. Python Ortamları penceresinde ortamın ayrıntıları herhangi bir zamanda gözden **geçirilsin ve değiştirilebilir.** Bu pencerede ortamı ve ardından Yapılandır **sekmesini** seçin. Değişiklik yaptıktan sonra Uygula **komutunu** seçin. Kaldır komutunu kullanarak da ortamı **kaldırabilirsiniz** (otomatik olarak algılanan ortamlar için kullanılamaz). Daha fazla bilgi için [bkz. Yapılandırma sekmesi.](python-environments-window-tab-reference.md#configure-tab)
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Geçersiz ortamları düzeltme veya silme

Bir Visual Studio kayıt defteri girdilerini bulan ancak yorumlayıcının yolu geçersizse **Python Ortamları** penceresinde adı bir yazı tipiyle birlikte gösterir:

::: moniker range="vs-2017"
![Geçersiz bir ortamı gösteren Python Ortamları penceresi](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Geçersiz bir ortamı gösteren Python Ortamları penceresi](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Tutmak istediğiniz bir ortamı düzeltmek için önce yükleyicinin Onarım işlemini **kullanmayı** deneyin. Örneğin, standart Python 3.x yükleyicileri bu seçeneği içerir.

Onarım seçeneği olmayan bir ortamı düzeltmek veya geçersiz bir ortamı kaldırmak için aşağıdaki adımları kullanarak kayıt defterini doğrudan değiştirebilirsiniz. Visual Studio değişiklik yaptığınız **zaman Python Ortamları** penceresini otomatik olarak güncelleştirmeniz gerekir.

1. *regedit.exe.*
1. HKEY_LOCAL_MACHINE\SOFTWARE\Python **veya** **HKEY_CURRENT_USER\SOFTWARE\Python.** IronPython için bunun yerine **IronPython'a** bakın.
1. Dağıtımla eşleşen düğümü genişletin; örneğin CPython için **Python Core** veya Anaconda için **ContinuumAnalytics.** IronPython için sürüm numarası düğümünü genişletin.
1. InstallPath düğümü altındaki **değerleri inceleme:**

    ![Tipik bir CPython yüklemesi için kayıt defteri girdileri](media/environments/environments-registry-entries.png)

    - Ortam bilgisayarınızda hala mevcutsa **ExecutablePath** değerini doğru konumla değiştirebilirsiniz. Ayrıca **(Varsayılan) ve** **WindowedExecutablePath değerlerini de** gereken şekilde düzeltin.
    - Ortam artık bilgisayarınızda yoksa ve **bunu Python** Ortamları penceresinden kaldırmak için yukarıdaki görüntüde yer alan **3.6** gibi **InstallPath** üst düğümünü silin.
    - Uygulama içinde geçersiz **HKEY_CURRENT_USER\SOFTWARE\Python** ayarları geçersiz **kılacakHKEY_LOCAL_MACHINE\SOFTWARE\Python**

## <a name="see-also"></a>Ayrıca bkz.

- [Python yorumlayıcılarını yükleme](installing-python-interpreters.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar requirements.txt kullanım](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)