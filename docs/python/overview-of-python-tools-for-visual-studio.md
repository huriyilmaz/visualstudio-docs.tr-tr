---
title: Windows üzerinde Visual Studio Python desteği
titleSuffix: ''
description: Visual Studio python özelliklerinin özeti (Visual Studio için Python Araçları, ptv 'ler olarak da bilinir) Windows üzerinde en iyi python ıde 'si.
ms.date: 12/11/2021
ms.custom: devdivchpfy22
ms.topic: overview
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 99572fab435639bb233d494aca21a2ece50a9ebf
ms.sourcegitcommit: 04fb8ba0f7ea73ba17baa88f10563c8600e7fd7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "135121548"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Windows üzerinde Visual Studio Python ile çalışma

Python, güvenilir, esnek, öğrenilmesi kolay, tüm işletim sistemlerinde kullanılmak üzere ücretsiz olan ve güçlü bir geliştirici topluluğu ve çok sayıda ücretsiz kitaplık tarafından desteklenen popüler bir programlama dilidir. Python, Web uygulamaları, Web Hizmetleri, masaüstü uygulamaları, betik oluşturma ve bilimsel bilgi işlem gibi tüm geliştirmeyi destekler. Bilimciler, gündelik geliştiriciler, profesyonel geliştiriciler ve birçok üniversiteler, programlama için Python kullanır. [Python.org](https://www.python.org) ve [Yeni başlayanlar için Python](https://www.python.org/about/gettingstarted/)'da dil hakkında daha fazla bilgi edinebilirsiniz.

Visual Studio, Windows güçlü bir Python ıde 'dir. Visual Studio **python geliştirme** ve **veri bilimi** iş yükleri (Visual Studio 2017 ve üzeri) ve ücretsiz Visual Studio için Python Araçları uzantısı aracılığıyla python dili için [açık kaynak](https://github.com/Microsoft/ptvs) desteği sağlar (Visual Studio 2015 ve daha önce).

Visual Studio, Mac 'te artık Python 'u desteklemiyor. Ancak Visual Studio Code aracılığıyla Mac ve Linux 'ta kullanılabilir. (bkz. [sorular ve yanıtlar](#questions-and-answers)).

Başlamak için:

- Python iş yükünü ayarlamak için [yükleme yönergelerini](installing-python-support-in-visual-studio.md) izleyin.
- bu makaledeki bölümler aracılığıyla Visual Studio Python özellikleri hakkında bilgi edinin.
::: moniker range="vs-2017"
- Bir veya daha fazla hızlı başlangıç üzerinden bir proje oluşturun. Emin değilseniz [Flask ile Web uygulaması oluşturma](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)ile başlayın.
::: moniker-end
::: moniker range="<=vs-2017"

> [!Note]
> Visual Studio Python sürüm 2,7 ' i ve 3,5 ile 3,7 sürümünü destekler. Python 'un diğer sürümlerinde yazılmış kodu düzenlemek için Visual Studio kullanmak mümkün olsa da, bu sürümler resmi olarak desteklenmez ve ıntellisense ve hata ayıklama gibi özellikler çalışmayabilir. Python sürüm 3,8 desteği hala geliştirme aşamasındadır, GitHub ilgili bu izleme [sorunu](https://github.com/microsoft/PTVS/issues/5822)bölümünde destek ile ilgili belirli Ayrıntılar görülebilir.
::: moniker-end

::: moniker range=">=vs-2019"

- Bir veya daha fazla hızlı başlangıç üzerinden bir proje oluşturun. Emin değilseniz, [hızlı başlangıç: bir klasörde Python kodu açın ve çalıştırın](quickstart-05-python-visual-studio-open-folder.md) ya da [Flask ile bir Web uygulaması oluşturun](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end

- eksiksiz bir uçtan uca deneyim için Visual Studio öğreticisinde [Python ile çalışmayı](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) izleyin.

## <a name="support-for-multiple-interpreters"></a>Birden çok yorumlayıcılar için destek

Visual Studio **Python ortamları** penceresi (aşağıda, geniş ve genişletilmiş bir görünümde gösterilmektedir), tüm genel Python ortamlarınızı, conda ortamlarınızı ve sanal ortamlarınızı yönetmek için size tek bir yer sunar. Visual Studio, standart konumlarda Python yüklemelerini otomatik olarak algılar ve özel yüklemeleri yapılandırmanıza olanak tanır. Her ortamla, paketleri kolayca yönetebilir, bu ortam için etkileşimli bir pencere açabilir ve ortam klasörlerine erişebilirsiniz.

::: moniker range="vs-2017"

  ![Python ortamları penceresinin genişletilmiş görünümü](media/environments/environments-expanded-view.png)
::: moniker-end

::: moniker range="vs-2019"

   ![Python ortamları penceresinin genişletilmiş görünümü-2019](media/environments/environments-expanded-view-2019.png)
::: moniker-end

:::moniker range=">=vs-2022"

   ![Python ortamları penceresinin genişletilmiş görünümü-2022](media/environments/environments-expanded-view-2022.png)
:::moniker-end

Visual Studio bağlamında Python 'ı etkileşimli olarak çalıştırmak için **etkileşimli pencere aç** komutunu kullanın. Seçili ortamın klasöründe ayrı bir komut penceresi açmak için **PowerShell 'de aç** komutunu kullanın. Bu komut penceresinden, herhangi bir Python betiğini çalıştırabilirsiniz.

Daha fazla bilgi için:

- [Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Python ortamları başvurusu](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Zengin düzenlemeler, IntelliSense ve kod kavrama

Visual Studio, sözdizimi renklendirme, tüm kod ve kitaplıklarınızda otomatik tamamlama, kod biçimlendirme, imza yardımı, yeniden düzenleme, oluşturma ve tür ipuçlarına dahil olmak üzere birinci sınıf bir Python düzenleyicisi sağlar. Visual Studio ayrıca sınıf görünümü, **tanıma git**, **tüm başvuruları bul** ve kod parçacıkları gibi benzersiz özellikler de sağlar. [Etkileşimli pencereyle](#interactive-window) doğrudan tümleştirme, bir dosyaya zaten kaydedilmiş Python kodunu hızlı bir şekilde geliştirmenize yardımcı olur.

   ![Visual Studio Python kodu için kod tamamlama](media/code-editing-completions-simple.png)

Daha fazla bilgi için:

- Docs: [Python kodunu Düzenle](editing-python-code-in-visual-studio.md)
- Docs: [Biçim kodu](formatting-python-code.md)
- Docs: [kodu yeniden düzenleme](refactoring-python-code.md)
- Docs: [bir lter kullanın](linting-python-code.md)
- genel Visual Studio özellik belgeleri: [kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Etkileşimli pencere

Visual Studio bilinen her Python ortamında, ayrı bir komut istemi kullanmak yerine doğrudan Visual Studio içindeki bir Python yorumlayıcı için aynı etkileşimli (REPL) ortamı açabilirsiniz. Ortamlar arasında kolayca geçiş yapabilirsiniz. (Ayrı bir komut istemi açmak için, **Python ortamları** penceresinde istediğiniz ortamı seçin ve daha önce [birden çok Yorumlayıcıiçin destek](#support-for-multiple-interpreters)altında açıklandığı gibi **PowerShell 'de aç** komutunu seçin.)

:::moniker range="<=vs-2019"
   ![Visual Studio-2019 ' de Python etkileşimli penceresi](media/interactive-window.png)
:::moniker-end

:::moniker range=">=vs-2022"
   ![Visual Studio-2022 ' de Python etkileşimli penceresi](media/interactive-window-2022.png)
:::moniker-end

Visual Studio ayrıca Python kod düzenleyicisi ve **etkileşimli** pencere arasında sıkı tümleştirme sağlar. **Ctrl tuşu** +  klavye kısayolu, düzenleyicide geçerli kod satırını (veya kod bloğunu) **etkileşimli** pencereye kolayca gönderir ve ardından sonraki satıra (veya bloğa) gider. **CTRL** + **ENTER** , hata ayıklayıcıyı çalıştırmak zorunda kalmadan kodu kolayca adımlamanızı sağlar. Ayrıca, seçilen kodu aynı tuş vuruşu ile **etkileşimli** pencereye gönderebilir ve **etkileşimli** penceredeki kodu kolayca düzenleyiciye yapıştırabilirsiniz. Bu yetenekler birlikte, **etkileşimli** penceredeki bir kod segmenti için ayrıntıları çalışmanıza ve sonuçları düzenleyicide bir dosyaya kolayca kaydetmenizi sağlar.

Visual Studio ayrıca satır içi çizimler, .net ve Windows Presentation Foundation (WPF) dahil olmak üzere REPL 'da ıpython/jupyter 'yı da destekler.

Daha fazla bilgi için:

- [Etkileşimli pencere](python-interactive-repl-in-visual-studio.md)
- [Visual Studio içinde IPython](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Project sistemi ve proje ve öğe şablonları

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019, Python kodu içeren bir klasörü açmayı ve bu kodu Visual Studio proje ve çözüm dosyaları oluşturmadan çalıştırmayı destekler. Daha fazla bilgi için bkz. [hızlı başlangıç: Python kodunu bir klasörde açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md). Ancak, bu bölümde açıklandığı gibi bir proje dosyası kullanmanın avantajları vardır.
::: moniker-end

::: moniker range="vs-2022"
> [!Note]
> Visual Studio 2022, Python kodu içeren bir klasörü açmayı ve bu kodu Visual Studio proje ve çözüm dosyaları oluşturmadan çalıştırmayı destekler. Daha fazla bilgi için bkz. [hızlı başlangıç: Python kodunu bir klasörde açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md). Ancak, bu bölümde açıklandığı gibi bir proje dosyası kullanmanın avantajları vardır.
::: moniker-end

Visual Studio, zaman içinde büyürken projenin karmaşıklığını yönetmenize yardımcı olur. bir *Visual Studio projesi* bir klasör yapısına çok daha fazla: farklı dosyaların nasıl kullanıldığına ve birbirleriyle nasıl ilişkilendirildiğine ilişkin bilgiler içerir. Visual Studio, uygulama kodu, test kodu, web sayfaları, JavaScript, derleme betikleri vb. ayırt etmenize yardımcı olur ve böylece dosyayla ilgili özellikleri etkinleştirir. ayrıca, bir Visual Studio çözümü, Python projesi ve C++ uzantı projesi gibi birden çok ilgili projeyi yönetmenize yardımcı olur.

   ![hem Python hem de C++ projelerini içeren bir Visual Studio çözümü](media/projects-solution-explorer-two-projects.png)

Project ve öğe şablonları, farklı proje ve dosya türlerini ayarlama, değerli zamandan tasarruf etme ve karmaşık ve hataya açık ayrıntıları yönetme sürecini otomatikleştirme işlemini otomatik hale getirir. Visual Studio, web, Azure, veri bilimi, konsol ve diğer proje türleri için şablonlar ve Python sınıfları, birim testleri, Azure web yapılandırması, HTML ve hatta docgo uygulamaları gibi dosyalar için şablonlar sağlar.

   [![Visual Studio Python projesi ve öğe şablonları](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Daha fazla bilgi için:

- Docs: [Python projelerini yönetme](managing-python-projects-in-visual-studio.md)
- Docs: [öğe şablonları başvurusu](python-item-templates.md)
- Docs: [Python proje şablonları](managing-python-projects-in-visual-studio.md#project-templates)
- Docs: [C++ ve Python Ile çalışma](working-with-c-cpp-python-in-visual-studio.md)
- genel Visual Studio özellik belgeleri: [Project ve öğe şablonları](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- genel Visual Studio özellik belgeleri: [Visual Studio çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Tam özellikli hata ayıklama

Visual Studio güçlerinden biri güçlü hata ayıklayıcısıdır. özellikle python için, Visual Studio python/C++ karışık mod hata ayıklaması, Linux 'ta uzaktan hata ayıklama, **etkileşimli** pencerede hata ayıklama ve Python birim testlerinde hata ayıklama dahildir.

   ![özel durum açılan penceresini gösteren Python için Visual Studio hata ayıklayıcı](media/debugging-exception-popup.png)

::: moniker range="vs-2019"

Visual Studio 2019 ' de, Visual Studio proje dosyası olmadan kodu çalıştırabilir ve hata ayıklaması yapabilirsiniz. Bkz. [hızlı başlangıç: Python kodunu bir klasör Içinde açma ve çalıştırma-2019 bir](quickstart-05-python-visual-studio-open-folder.md) örnek için.
::: moniker-end

::: moniker range=">=vs-2022"

Visual Studio 2022 ' de, Visual Studio proje dosyası olmadan kodu çalıştırabilir ve hata ayıklaması yapabilirsiniz. Bkz. [hızlı başlangıç: Python kodunu bir klasör Içinde açma ve çalıştırma-2022 bir](quickstart-05-python-visual-studio-open-folder.md) örnek için.
::: moniker-end

Daha fazla bilgi için:

- Docs: [Python hata ayıkla](debugging-python-in-visual-studio.md)
- Docs: [Python/C++ karışık modda hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Docs: [Linux 'Ta uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- genel Visual Studio özellik belgeleri: [Visual Studio hata ayıklayıcının özellik turu](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Kapsamlı raporlama ile profil oluşturma araçları

Profil oluşturma, uygulamanızda saatin nasıl harcandığını araştırır. Visual Studio, cpyıthon tabanlı yorumlayıcılarla profil oluşturmayı destekler ve farklı profil oluşturma çalıştırmaları arasındaki performansı karşılaştırma olanağını içerir.

   [![Visual Studio Python projesi için profil oluşturma sonuçlarını oluşturma](media/profiling-results.png)](media/profiling-results.png#lightbox)

Daha fazla bilgi için:

- Docs: [Python profil oluşturma araçları](profiling-python-code-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [Profil Oluşturma Özelliği Turu.](../profiling/profiling-feature-tour.md) (Tüm Visual Studio profil oluşturma özellikleri Python'da kullanılamaz).

## <a name="unit-testing-tools"></a>Birim testi araçları

Test Gezgini'nde testleri keşfedin, çalıştırın Visual Studio **yönetin** ve birim testlerinde kolayca hata ayıklayabilirsiniz.

   ![Visual Studio'da Python birim testinde hata ayıklama](media/unit-test-debugging.png)

Daha fazla bilgi için:

- Docs: [Python için birim testi araçları](unit-testing-python-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [Kodunuzu birim testi.](../test/unit-test-your-code.md)

## <a name="azure-sdk-for-python"></a>Python için Azure SDK

Python için Azure kitaplıkları, azure, macOS X ve Linux Windows Azure hizmetlerini basitleştirir. Bunları kullanarak Azure kaynaklarını oluşturabilir, yönetebilir ve Azure hizmetleriyle bağlantı kurabilirsiniz.

Daha fazla bilgi için [bkz. Python için Azure SDK'sı](/azure/python/) [ve Python için Azure kitaplıkları.](/azure/python/python-sdk-azure-overview)

## <a name="questions-and-answers"></a>Sorular ve cevaplar

**S. Python desteği Mac için Visual Studio?**

A. Şu anda değil, ancak isteği Developer Community [üzerinde oy ve Community.](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html) Aşağıdaki [Mac için Visual Studio,](/visualstudio/mac/) desteklemektedir geçerli geliştirme türlerini tanımlar. Bu arada, Visual Studio Code, Mac Windows Linux'ta kullanılabilir uzantılar aracılığıyla [Python ile iyi çalışır.](https://code.visualstudio.com/docs/languages/python)

**S. Python ile kullanıcı arabirimi oluşturmak için ne kullanabilirim?**

A. Bu alanda temel teklif, [PySide (resmi bağlama)](https://wiki.qt.io/PySide) (ayrıca bkz. [PySide](https://download.qt.io/official_releases/pyside/.)indirmeleri) ve [PyQt](https://wiki.python.org/moin/PyQt)olarak bilinen Python bağlamaları ile [Qt](https://www.qt.io/qt-for-application-development/)Project 'dır. Kullanıcı arabirimi Visual Studio Python desteği, kullanıcı arabirimi geliştirmesi için herhangi bir araç içermemektedir.

**S. Python projesi tek başına yürütülebilir dosya üretebilir mi?**

A. Python genellikle yorumlanabilen bir dildir ve kod, web sunucuları ve web sunucuları gibi uygun bir Python özellikli Visual Studio üzerinde isteğe bağlı olarak çalıştırıldı. Visual Studio artık tek başına yürütülebilir dosya oluşturmak için gerekli olan yolu sağlamaz. Bu, aslında ekli Python yorumlayıcıya sahip bir program anlamına gelir. Ancak, Python topluluğu StackOverflow'da açıklandığı gibi yürütülebilir dosyalar oluşturmak için [farklı yollar sağlar.](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) CPython, [CPython'un](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)katıştırılabilir zip dosyasını kullanma blog gönderisi üzerinde açıklandığı gibi yerel bir uygulamanın içine katıştırma desteği de sağlar.

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Özellik desteği

Python özellikleri, yükleme kılavuzunda açıklandığı gibi Visual Studio sürümlerine [yükleyebilirsiniz:](installing-python-support-in-visual-studio.md)

- [Visual Studio 2022 (tüm sürümler)](https://visualstudio.microsoft.com/vs/)
- [Visual Studio 2019 (tüm sürümler)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (tüm sürümler)
- Visual Studio 2015 (tüm sürümler)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 için Express, Güncelleştirme 2 veya daha yenisi
- Visual Studio 2013 Için Express, Güncelleştirme 2 veya daha yenisi
- Visual Studio 2013 (Pro sürümü veya daha yüksek)
- Visual Studio 2012 (Pro sürümü veya daha yüksek)
- Visual Studio 2010 SP1 (Pro veya sonraki bir sürüm; .NET 4.5 gereklidir)

Visual Studio 2015 ve önceki sürümleri [visualstudio.microsoft.com/vs/older-downloads/.](https://visualstudio.microsoft.com/vs/older-downloads/)

> [!Important]
> Özellikler, yalnızca en son sürümler için tam olarak Visual Studio. Özellikler eski sürümlerde kullanılabilir, ancak etkin bir şekilde bakıma açık değildir.

|          Python desteği          |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Birden çok yorumlayıcıyı yönetme   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Popüler yorumlayıcıları otomatik algılama | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Özel yorumlayıcılar ekleme      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Sanal Ortamlar       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Pip/Easy Install         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Proje sistemi         |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro + |      2012 Pro +       | 2010 SP1 Pro + |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Mevcut koddan yeni proje | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Tüm dosyaları göster         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Kaynak denetimi         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Git ile tümleştirme         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Düzenleme            |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Söz dizimi vurgulama      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Otomatik Tamamlama         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        İmza yardımı        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Hızlı bilgi          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Nesne tarayıcısı/sınıf görünümü   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Gezinti çubuğu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Tanıma Git       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          sayfasına gidin          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Tüm Başvuruları Bul      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Otomatik girintileme       | &#10004;e | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Kod biçimlendirme        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Yeniden Düzenle-yeniden adlandır       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Yeniden düzenleme-ayıklama yöntemi   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Yeniden Düzenle-içeri aktarma Ekle/Kaldır | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Etkileşimli pencere     |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Etkileşimli pencere     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Satır içi grafiklerle IPython | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Masaüstü               |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     konsol/Windows uygulaması     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IronPython WPF (XAML Tasarımcısı ile) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      ıronpython Windows Forms       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Docgo Web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Şişe Web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Flask Web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Genel Web projesi | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü |       2013 Web       |      2013 Pro +       |      2012 Pro +       |    2010 SP1 Pro +     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Web sitesine dağıt   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Web rolüne dağıt   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Çalışan rolüne dağıt  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Azure öykünücüsü 'nde Çalıştır  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Uzaktan hata ayıklama    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Sunucu Gezgini Ekle | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Docgo şablonları           |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü |       2013 Web       |      2013 Pro +       | 2012 Pro + | 2010 SP1 Pro + |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Hata Ayıklama               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Otomatik Tamamlama             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| CSS ve JavaScript için otomatik tamamlama | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Hata Ayıklama                  |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Hata Ayıklama                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Proje olmadan hata ayıklama         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Hata ayıklama - düzenlemeye ekleme        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Karma mod hata ayıklama             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Uzaktan hata ayıklama (Windows, macOS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Hata ayıklama Etkileşimli penceresi           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profil Oluşturma |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profil Oluşturma | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Test etme      |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Test gezgini | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Testi çalıştırma    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Hata ayıklama testi   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Visual Studio 2012 için git desteği, [Visual Studio marketi](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit)'nde bulunan git uzantısı için Visual Studio Araçları kullanılabilir.

1. azure Web sitesine dağıtım, [.net için azure SDK 2,1-Visual Studio 2010 SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids)gerektirir. sonraki sürümler Visual Studio 2010 ' i desteklemez.

1. Azure Web rolü ve çalışan rolü için destek, [.net 2,3-VS 2012 veya üzeri Için Azure SDK](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) gerektirir.

1. Azure Web rolü ve çalışan rolü için destek, [.net 2,3-VS 2013 veya üzeri Için Azure SDK](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) gerektirir.

1. Visual Studio 2013 'deki docgo şablon düzenleyicisi, güncelleştirme 2 ' ye yükleyerek çözümlenen bazı bilinen sorunlara sahiptir.

1. Windows 8 veya üstünü gerektirir. Web için Visual Studio 2013 Express **işleme ekle** iletişim kutusuna sahip değil, ancak Azure Web sitesi uzaktan hata ayıklama, **Sunucu Gezgini** **hata ayıklayıcı (Python)** komutu kullanılarak hala mümkün. uzaktan hata ayıklama, [.net 2,3-Visual Studio 2013 veya üzeri için Azure SDK](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) gerektirir.

1. Windows 8 veya üstünü gerektirir. **Sunucu Gezgini** **hata ayıklayıcı (Python) komutunun eklenmesi** , [.net 2,3-Visual Studio 2013 veya üzeri için Azure SDK](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) gerektirir.

1. Windows 8 veya üstünü gerektirir.
::: moniker-end
