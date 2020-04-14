---
title: Python ortamlarını ve yorumlayıcıları yönetme
description: Genel, sanal ve conda ortamlarını yönetmek, Python yorumlayıcıları ve paketleri yüklemek ve Visual Studio projelerine ortamlar atamak için Python Ortamları penceresini kullanın.
ms.date: 08/06/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: a47af0e87907608ec9f71de4e605772eb1caed8e
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224569"
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Visual Studio'da Python ortamları oluşturma ve yönetme

**Python ortamı,** Python kodunu çalıştırdığınız ve genel, sanal ve conda ortamlarını içeren bir bağlamdır. Ortam bir yorumlayıcı, kitaplık (genellikle Python Standart Kitaplığı) ve yüklü paketler kümesinden oluşur. Bu bileşenler birlikte hangi dil yapılarının ve sözdiziminin geçerli olduğunu, hangi işletim sistemi işlevlerine erişebileceğinizi ve hangi paketleri kullanabileceğinizi belirler.

Windows'daki Visual Studio'da, ortamları yönetmek ve yeni projeler için varsayılan olarak birini seçmek için bu makalede açıklandığı gibi **Python Ortamları** penceresini kullanırsınız. Ortamların diğer yönleri aşağıdaki makalelerde yer alır:

- Belirli bir proje için varsayılanı kullanmak yerine [belirli bir ortam seçebilirsiniz.](selecting-a-python-environment-for-a-project.md)

- Python projeleri için sanal ortamlar oluşturma ve kullanma hakkında ayrıntılı bilgi [için](selecting-a-python-environment-for-a-project.md#use-virtual-environments)bkz.

- Paketleri bir ortama yüklemek istiyorsanız, [Paketler sekmesi başvurusuna](python-environments-window-tab-reference.md#packages-tab)bakın.

- Başka bir Python yorumlayıcısı yüklemek için [bkz.](installing-python-interpreters.md) Genel olarak, bir ana hat Python dağıtımı için bir yükleyici indirip çalıştırırsanız, Visual Studio **Python Ortamları** penceresinde yeni yüklemenin ve ortamın göründüğünü algılar ve projeler için seçilebilir.

Visual Studio'da Python'da yeniyseniz, aşağıdaki makaleler genel arka plandan da şunları sağlar:

- [Visual Studio'da Python ile çalışma](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio'da Python desteğini yükleyin](installing-python-support-in-visual-studio.md)

::: moniker range="vs-2017"
> [!Note]
> **Dosya** > **Aç** > **Klasör** komutunu kullanarak yalnızca klasör olarak açılan Python kodu ortamlarını yönetemezsiniz. Bunun yerine, Visual Studio'nun ortam özelliklerinden yararlanmak için [varolan koddan bir Python projesi oluşturun.](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> **Dosya** > **Aç** > **Klasör** komutunu kullanarak klasör olarak açılan Python kodu ortamlarını yönetebilirsiniz. Python araç çubuğu, algılanan tüm ortamlar arasında geçiş yapmanızı ve yeni bir ortam eklemenizi sağlar. Ortam bilgileri, Çalışma Alanı .vs klasöründeki PythonSettings.json dosyasında depolanır.
::: moniker-end

## <a name="the-python-environments-window"></a>Python Ortamları penceresi

Visual Studio'nun bildiği ortamlar **Python Ortamları** penceresinde görüntülenir. Pencereyi açmak için aşağıdaki yöntemlerden birini kullanın:

- **Diğer Windows** > **Python Ortamlarını** **Görüntüle** > menüsü komutunu seçin.
- **Solution Explorer'daki** bir proje için **Python Ortamları** düğümüne sağ tıklayın ve **Tüm Python Ortamlarını Görüntüle'yi**seçin:

    ::: moniker range="vs-2017"
    ![Solution Explorer'da Tüm Ortamları Görüntüle komutunu görüntüle](media/environments/environments-view-all.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Solution Explorer'da Tüm Ortamları Görüntüle komutunu görüntüle](media/environments/environments-view-all-2019.png)
    ::: moniker-end

Her iki durumda da, **Python Ortamları** penceresi **Çözüm Gezgini**yanında görünür:

::: moniker range="vs-2017"
![Python Ortamları penceresi](media/environments/environments-default-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamları penceresi](media/environments/environments-default-view-2019.png)
::: moniker-end

Visual Studio, sanal ortamlar ve conda ortamları ile birlikte kayıt defterini [(PEP 514'ü](https://www.python.org/dev/peps/pep-0514/)takip ederek) yüklü küresel ortamlar arar (bkz. [ortam türleri).](#types-of-environments) Listede beklenen bir ortam görmüyorsanız, [bkz.](#manually-identify-an-existing-environment)

Listede bir ortam seçtiğinizde, Visual Studio **genel bakış** sekmesinde bu ortama ilişkin çeşitli özellikleri ve komutları görüntüler. Örneğin, yukarıdaki resimde yorumlayıcının *konumunun C:\Python36-32*olduğunu görebilirsiniz. **Genel Bakış** sekmesinin altındaki dört komutun her biri, tercüman çalışırken bir komut istemi açar. Daha fazla bilgi için [Bkz. Python Ortamları pencere sekmesi başvurusu - Genel Bakış](python-environments-window-tab-reference.md#overview-tab).

**Paketler**ve **IntelliSense**gibi farklı sekmelere geçmek için ortamlar listesinin altındaki açılır listeyi kullanın. Bu sekmeler Python [Ortamları pencere sekmesi referansı](python-environments-window-tab-reference.md)da açıklanmıştır.

Bir ortamı seçmek, herhangi bir projeyle ilişkisini değiştirmez. Listede kalın yüzle gösterilen varsayılan ortam, Visual Studio'nun yeni projeler için kullandığı ortamdır. Yeni projelerle farklı bir ortam kullanmak **için, bu yeni projeler için varsayılan ortam yap** komutunu kullanın. Proje bağlamında her zaman belirli bir ortamı seçebilirsiniz. Daha fazla bilgi için [bkz.](selecting-a-python-environment-for-a-project.md)

Listelenen her ortamın sağında, o ortam için **Etkileşimli** pencere açan bir denetim yer alıyor. (Visual Studio 2017 15.5 ve daha önceki durumlarda, bu ortam için IntelliSense veritabanını yenileyen başka bir denetim görüntülenir. Veritabanı yla ilgili ayrıntılar için [Ortamlar pencere sekmesi başvurusuna](python-environments-window-tab-reference.md) bakın.)

::: moniker range="vs-2017"
> [!Tip]
> **Python Ortamları** penceresini yeterince genişlettiğinde, çalışmak için daha uygun bulabileceğiniz ortamlarınızın daha kapsamlı bir görünümünü elde elabilirsiniz.
>
> ![Python Ortamları penceresi genişletilmiş görünüm](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Tip]
> **Python Ortamları** penceresini yeterince genişlettiğinde, çalışmak için daha uygun bulabileceğiniz ortamlarınızın daha kapsamlı bir görünümünü elde elabilirsiniz.
>
> ![Python Ortamları penceresi genişletilmiş görünüm](media/environments/environments-expanded-view-2019.png)
::: moniker-end

> [!Note]
> Visual Studio sistem-site paketleri seçeneğine saygı gösterse de, Visual Studio'nun içinden değiştirmenin bir yolunu sağlamaz.

### <a name="what-if-no-environments-appear"></a>Ortam yoksa ne olur?

Ortam görünmüyorsa, Visual Studio'nun standart konumlardaki Python yüklemelerini algılayamadığı anlamına gelir. Örneğin, Visual Studio 2017 veya daha sonra yüklemiş olabilirsiniz, ancak Python iş yükü için yükleyici seçeneklerindeki tüm yorumlayıcı seçeneklerini temize çıkarmış olabilirsiniz. Benzer şekilde, Visual Studio 2015 veya daha önce yüklemiş olabilirsiniz, ancak bir yorumlayıcıyı el ile yüklememiş olabilirsiniz [(bkz. Python yorumlayıcılarını yükle).](installing-python-interpreters.md)

Bilgisayarınızda bir Python yorumlayıcısı olduğunu ancak Visual Studio'nun (herhangi bir sürüm) bunu algılamadığını biliyorsanız, konumunu el ile belirtmek için **+ Özel** komutunu kullanın. Bir sonraki bölüme bakın, [varolan bir ortamı el ile tanımlayın.](#manually-identify-an-existing-environment)

> [!Tip]
> Visual Studio, python 2.7.11'i python.org'dan yükleyenleri kullanarak 2.7.11'den 2.7.14'e yükseltme gibi varolan bir yorumlayıcının güncelleştirmelerini algılar. Yükleme işlemi sırasında, güncelleştirme yerine görünmeden önce eski ortam **Python Ortamları** listesinden kaybolur.
>
> Ancak, dosya sistemini kullanarak bir yorumcunu ve ortamını el ile taşırsanız, Visual Studio yeni konumu bilmez. Daha fazla bilgi için [bkz.](installing-python-interpreters.md#move-an-interpreter)

### <a name="types-of-environments"></a>Ortam türleri

Visual Studio küresel, sanal ve conda ortamlarıyla çalışabilir.

#### <a name="global-environments"></a>Küresel ortamlar

Her Python yüklemesi (örneğin, Python 2.7, Python 3.6, Python 3.7, Anaconda 4.4.0, vb., [bkz. Python yorumlayıcılarını yükle)](installing-python-interpreters.md)kendi *genel ortamını*korur. Her ortam belirli Python yorumlayıcısından, standart kitaplığından, önceden yüklenmiş paketler den ve bu ortam etkinleştirilirken yüklediğiniz ek paketlerden oluşur. Bir paketi genel bir ortama yüklemek, paketi bu ortamı kullanarak tüm projeleriçin kullanılabilir hale getirir. Ortam dosya sisteminin korumalı bir alanında bulunuyorsa *(örneğin, c:\program dosyaları*içinde), paketleri yüklemek yönetici ayrıcalıkları gerektirir.

Bilgisayardaki tüm projeler için genel ortamlar mevcuttur. Visual Studio'da, bir proje için özel olarak farklı bir ortam seçmediğiniz sürece tüm projeler için kullanılan varsayılan olarak bir genel ortam seçersiniz. Daha fazla bilgi için [bkz.](selecting-a-python-environment-for-a-project.md)

#### <a name="virtual-environments"></a>Sanal ortamlar

Küresel bir ortamda çalışmak başlamak için kolay bir yol olsa da, bu ortam zaman içinde farklı projeler için yüklediğiniz birçok farklı paketle karmakarışık olacaktır. Bu tür bir yığılmayı iyice bilinen sürümleri ile paketleri belirli bir dizi karşı bir uygulama test etmek zor laştırır, tam olarak bir yapı sunucusu veya web sunucusu üzerinde kurmak istiyorum ortam türüdür. Çakışmalar, iki proje de aynı paketin uyumsuz paketleri veya farklı sürümlerini gerektirdiğinde oluşabilir.

Bu nedenle, geliştiriciler genellikle bir proje için sanal bir *ortam* oluşturur. Sanal ortam, belirli bir yorumlayıcının kopyasını içeren projedeki bir alt klasördür. Sanal ortamı etkinleştirdiğinizde, yüklediğiniz tüm paketler yalnızca o ortamın alt klasörüne yüklenir. Daha sonra bu ortamda bir Python programı çalıştırdığınızda, yalnızca belirli paketlere karşı çalıştığını bilirsiniz.

Visual Studio, bir proje için sanal ortam oluşturmak için doğrudan destek sağlar. Örneğin, *gereksinimler.txt*içeren bir proje açarsanız veya bu dosyayı içeren bir şablondan bir proje oluşturursanız, Visual Studio otomatik olarak sanal bir ortam oluşturmanızı ve bu bağımlılıkları yüklemenizi ister.

Açık bir proje içinde istediğiniz zaman yeni bir sanal ortam oluşturabilirsiniz. **Çözüm Gezgini'nde**proje düğümünü genişletin, **Python Ortamları'nı**sağ tıklatın ve "Sanal Ortam Ekle"yi seçin. Daha fazla bilgi için [bkz.](/visualstudio/python/selecting-a-python-environment-for-a-project?view=vs-2019#create-a-virtual-environment-1)

Visual Studio ayrıca sanal ortamdan *bir requirements.txt* dosyası oluşturmak için bir komut sağlayarak diğer bilgisayarlarda ortamı yeniden oluşturmayı kolaylaştırır. Daha fazla bilgi için [bkz.](selecting-a-python-environment-for-a-project.md#use-virtual-environments)

#### <a name="conda-environments"></a>Conda ortamları

Bir conda ortamı `conda` bir araç kullanılarak oluşturulur, ya da Visual Studio entegre conda yönetimi ile 2017 sürüm 15.7 ve üstü. (Visual Studio yükleyicisi aracılığıyla kullanılabilen Anaconda veya Miniconda gerektirir, [bkz.](installing-python-support-in-visual-studio.md#visual-studio-2019-and-visual-studio-2017)

::: moniker range="vs-2017"

1. **Yeni conda ortamı oluşturma** sekmesini açan Python **Ortamları** penceresinde **+ Conda ortamı oluştur'u** seçin:

    ![Yeni bir conda ortamı için sekme oluşturma](media/environments/environments-conda-1.png)

1. **Ad** alanına ortam için bir ad girin, **Python** alanında bir temel Python karşıcı seçin ve **Oluştur'u**seçin.

1. **Çıktı** penceresi, oluşturma tamamlandıktan sonra birkaç CLI yönergesi ile yeni ortam için ilerleme gösterir:

    ![Bir conda ortamının başarılı yaratılması](media/environments/environments-conda-2.png)

1. Visual Studio içinde, [bir proje için bir ortam seçin'de](selecting-a-python-environment-for-a-project.md)açıklandığı gibi başka bir ortamda olduğu gibi bir proje için bir conda ortamı etkinleştirebilirsiniz.

1. Paketleri ortama yüklemek için [Paketler sekmesini](python-environments-window-tab-reference.md#packages-tab)kullanın.
::: moniker-end

::: moniker range=">=vs-2019"

1. Ortam Ekle **iletişim** kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) **+ Çevre Ekle'yi** seçin. Bu iletişim kutusunda, **Conda ortamı** sekmesini seçin:

    ![Ortam Ekle iletişim kutusunda conda ortamı sekmesi](media/environments/environments-conda-1-2019.png)

1. Aşağıdaki alanları yapılandırın:

    | Alan | Açıklama |
    | --- | --- |
    | Project | Ortamı oluşturabileceğiniz proje (aynı Visual Studio çözümünde birden fazla projeniz varsa). |
    | Adı | Conda ortamının adı. |
    | Paket ekleme | Bağımlılıklarınızı açıklayan bir *environment.yml* dosyanız varsa **Çevre dosyasını** seçin veya **bir veya daha fazla Anaconda paket adı** seçin ve aşağıdaki alanda en az bir Python paketi veya Python sürümü listeleyin. Paket listesi conda'ya Python ortamı oluşturmasını bildirir. Python'un en son sürümünü `python`yüklemek için; belirli bir sürümü yüklemek `python=,major>.<minor>` için, 'de `python=3.7`olduğu gibi kullanın. Python sürümlerini ve ortak paketleri bir dizi menüden seçmek için paket düğmesini de kullanabilirsiniz. |
    | Geçerli ortam olarak ayarlayın | Ortam oluşturulduktan sonra seçili projedeki yeni ortamı etkinleştirir. |
    | Yeni projeler için varsayılan ortam olarak ayarlayın | Visual Studio'da oluşturulan yeni projelerde conda ortamını otomatik olarak ayarlar ve etkinleştirir. Bu seçenek, **Python Ortamları** penceresinde ki **yeni projeler için varsayılan ortam yap'ı** kullanmakla aynıdır. |
    | Python Ortamları penceresinde görünüm | Ortamı oluşturduktan sonra **Python Ortamları** penceresinin gösterip göstermeyeceğini belirtir. |

    > [!Important]
    > Conda ortamı oluştururken, en az bir Python sürümü veya `environments.yml` Python paketini kullanarak veya ortamın python çalışma zamanı içermesini sağlayan paket listesini belirttiğinden emin olun. Aksi takdirde, Visual Studio ortamı yok sayar: ortam **Python Ortamları** penceresinin hiçbir yerinde görünmez, bir proje için geçerli ortam olarak ayarlanamaz ve genel bir ortam olarak kullanılamaz.
    >
    > Python sürümü olmayan bir conda ortamı oluşturursanız, `conda info` conda ortamı klasörlerinin konumlarını görmek için komutu kullanın ve ardından ortam alt klasörünü bu konumdan el ile kaldırın.

1. **Oluştur'u**seçin ve **Çıktı** penceresinde ilerlemeyi gözlemleyin. Oluşturma tamamlandıktan sonra çıktı birkaç CLI yönergeleri ile içerir:

    ![Bir conda ortamının başarılı yaratılması](media/environments/environments-conda-2-2019.png)

1. Visual Studio içinde, [bir proje için bir ortam seçin'de](selecting-a-python-environment-for-a-project.md)açıklandığı gibi başka bir ortamda olduğu gibi bir proje için bir conda ortamı etkinleştirebilirsiniz.

1. Ortama ek paketler yüklemek için [Paketler sekmesini](python-environments-window-tab-reference.md#packages-tab)kullanın.
::: moniker-end

> [!Note]
> Conda ortamları ile en iyi sonuçlar için, conda 4.4.8 veya daha sonra (conda sürümleri Anaconda sürümleri farklıdır) kullanın. Miniconda (Visual Studio 2019) ve Anaconda 'nın (Visual Studio 2017) uygun sürümlerini Visual Studio yükleyicisi aracılığıyla yükleyebilirsiniz.

Conda ortamlarının depolandığı conda sürümünü ve diğer bilgileri `conda info` görmek için, Anaconda komut isteminde çalışır (diğer bir deyişle, Anaconda'nın yolda olduğu bir komut istemi):

```cli
conda info
```

Conda ortam klasörleriniz aşağıdaki gibi görünür:

```output
       envs directories : C:\Users\user\.conda\envs
                          c:\anaconda3\envs
                          C:\Users\user\AppData\Local\conda\conda\envs
```

Conda ortamları bir projeyle depolanmadığından, genel ortamlara benzer şekilde davranırlar. Örneğin, bir conda ortamına yeni bir paket yüklemek, bu paketi bu ortamı kullanan tüm projeler için kullanılabilir hale getirir.

Visual Studio 2017 sürüm 15.6 ve daha önceki sürümiçin, mevcut bir [ortamı El ile tanımlandığı](#manually-identify-an-existing-environment)gibi el ile işaret ederek conda ortamlarını kullanabilirsiniz.

Visual Studio 2017 sürüm 15.7 ve daha sonra conda ortamlarını otomatik olarak algılar ve bir sonraki bölümde açıklandığı gibi **Python Ortamları** penceresinde görüntüler.

## <a name="manually-identify-an-existing-environment"></a>Varolan bir ortamı el ile tanımlama

Standart olmayan bir konumda yüklü bir ortamı tanımlamak için aşağıdaki adımları kullanın (Visual Studio 2017 sürüm 15.6 ve önceki sürümdeki conda ortamları dahil):

::: moniker range="vs-2017"

1. **Yapılandırma** sekmesini açan **Python Ortamları** penceresinde **+ Özel'i** seçin:

    ![Yeni bir özel ortam için varsayılan görünüm](media/environments/environments-custom-1.png)

1. **Açıklama** alanına ortam için bir ad girin.

1. **Önek yol** alanındaki yorumlayıcının yoluna girin veya göz atın **(...** kullanarak).

1. Visual Studio o konumda bir Python yorumlayıcısı algılarsa (conda ortamı için aşağıda gösterilen yol gibi), **Otomatik Algılama** komutunu etkinleştirirken. Otomatik **Algıla'yı** seçmek kalan alanları tamamlar. Bu alanları el ile de tamamlayabilirsiniz.

    ![Otomatik Algılama komutunu etkinleştirme](media/environments/environments-custom-2.png)

    ![Otomatik Algılama'yı kullandıktan sonra ortam alanlarının tamamlanması](media/environments/environments-custom-3.png)

1. Alanlar istediğiniz değerleri içerdikten sonra yapılandırmayı kaydetmek için **Uygula'yı** seçin. Artık Visual Studio içinde herhangi bir diğer gibi çevre kullanabilirsiniz.

1. El ile tanımlanmış bir ortamı kaldırmanız gerekiyorsa, **Yapılsekmesindeki** **Kaldır** komutunu seçin. Otomatik algılanan ortamlar bu seçeneği sağlamaz. Daha fazla bilgi için yapı [sekmesine](python-environments-window-tab-reference.md#configure-tab)bakın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ortam Ekle **iletişim** kutusunu açan **Python Ortamları** penceresinde (veya Python araç çubuğundan) **+ Çevre Ekle'yi** seçin. Bu iletişim kutusunda, **Varolan ortam** sekmesini seçin:

    ![Ortam Ekle iletişim kutusundaki varolan ortam sekmesi](media/environments/environments-custom-1-2019.png)

1. **Çevre** açılır'ı seçin, ardından **Özel'i**seçin:

    ![Ortam Ekle iletişim kutusunda özel ortam seçeneği](media/environments/environments-custom-2-2019.png)

1. İletişim kutusunda sağlanan alanlara, diğer alanların çoğunu dolduran **Önek yolu**altındaki yorumlayıcının yoluna girin veya göz atın **(...** kullanarak). Bu değerleri gözden geçirdikten ve gerektiği gibi değiştirdikten sonra **Ekle'yi**seçin. 

    ![Ortam Ekle iletişim kutusunda özel bir ortam seçeneğiiçin ayrıntıları belirtmek için alanlar](media/environments/environments-custom-3-2019.png)

1. Ortamın ayrıntıları **Python Ortamları** penceresinde herhangi bir zamanda gözden geçirilebilir ve değiştirilebilir. Bu pencerede ortamı seçin ve ardından **Yapılsekmesi'ni** seçin. Değişiklik yaptıktan sonra **Uygula** komutunu seçin. **Kaldır** komutunu kullanarak ortamı da kaldırabilirsiniz (otomatik algılanan ortamlar için kullanılamaz). Daha fazla bilgi için yapı [sekmesine](python-environments-window-tab-reference.md#configure-tab)bakın.
::: moniker-end

## <a name="fix-or-delete-invalid-environments"></a>Geçersiz ortamları düzeltme veya silme

Visual Studio bir ortam için kayıt defteri girişleri bulursa, ancak yorumlayıcıya giden yol geçersizse, **Python Ortamları** penceresi adı bir yazı tipiyle gösterir:

::: moniker range="vs-2017"
![Geçersiz bir ortamı gösteren Python Ortamları penceresi](media/environments/environments-invalid-entry.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Geçersiz bir ortamı gösteren Python Ortamları penceresi](media/environments/environments-invalid-entry-2019.png)
::: moniker-end

Tutmak istediğiniz ortamı düzeltmek için, öncelikle yükleyicinin **Onarım** işlemini kullanmayı deneyin. Standart Python 3.x için yükleyiciler, örneğin, bu seçeneği içerir.

Onarım seçeneği olmayan bir ortamı düzeltmek veya geçersiz bir ortamı kaldırmak için, kayıt defterini doğrudan değiştirmek için aşağıdaki adımları kullanın. Visual Studio, kayıt defterinde değişiklik yaptığınızda **Python Ortamları** penceresini otomatik olarak güncelleştirir.

1. Run *regedit.exe*.
1. **HKEY_LOCAL_MACHINE\SOFTWARE\Python**gidin. IronPython için, bunun yerine **IronPython'u** arayın.
1. CPython için **Python Core** veya Anaconda için **ContinuumAnalytics** gibi dağıtımla eşleşen düğümü genişletin. IronPython için sürüm numarası düğümunu genişletin.
1. **InstallPath** düğümü altındaki değerleri inceleyin:

    ![Tipik bir CPython yüklemesi için kayıt defteri girişleri](media/environments/environments-registry-entries.png)

    - Bilgisayarınızda ortam hala varsa, **ExecutablePath** değerini doğru konuma değiştirin. Ayrıca **(Varsayılan)** ve **WindowedExecutablePath** değerlerini gerektiği gibi düzeltin.
    - Ortamın bilgisayarınızda artık yoksa ve **python ortamları** penceresinden kaldırmak istiyorsanız, yukarıdaki resimde **3,6** gibi **InstallPath'in**ana düğümünü silin.

## <a name="see-also"></a>Ayrıca bkz.

- [Python yorumlayıcılarını yükleme](installing-python-interpreters.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanın](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
- [Python Ortamları pencere başvurusu](python-environments-window-tab-reference.md)
