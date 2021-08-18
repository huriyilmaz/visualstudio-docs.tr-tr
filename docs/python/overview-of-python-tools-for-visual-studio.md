---
title: Windows'Visual Studio'da Python desteği
titleSuffix: ''
description: Visual Studio'daki Python özelliklerinin özeti, bu Windows (Visual Studio için Python Araçları, PTVS olarak da bilinir) en iyi Python IDE'leridir.
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 380a9a038ff48818fec213c86283328e01beb0d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100601"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Python ile Visual Studio'de Windows

Python hem güçlü bir geliştirici topluluğu hem de birçok ücretsiz kitaplık tarafından desteklenen, güvenilir, esnek, öğrenmesi kolay, tüm işletim sistemlerinde ücretsiz olarak kullanabileceğiniz popüler bir programlama dilidir. Python; web uygulamaları, web hizmetleri, masaüstü uygulamaları, betik ve bilimsel bilgi işlem gibi her türlü geliştirmeyi destekler ve birçok üniversite, bilim insanı, gündelik geliştirici ve profesyonel geliştirici tarafından kullanılır. Dil hakkında daha fazla bilgi edinmek için [python.org](https://www.python.org) [Python for Beginners hakkında bilgi edinmek için:](https://www.python.org/about/gettingstarted/).

Visual Studio, Windows üzerinde güçlü bir Python IDE'Windows. Visual Studio Python geliştirme [](https://github.com/Microsoft/ptvs) ve veri bilimi iş yükleri (Visual Studio  2017 ve sonrası) ve ücretsiz Visual Studio için Python Araçları uzantısı (Visual Studio 2015 ve önceki sürümler) aracılığıyla **Python** dili için açık kaynak desteği sağlar.

Python şu anda Mac için Visual Studio destek Mac için Visual Studio Mac ve Linux'ta Visual Studio Code (soru ve [yanıtlara bakın) aracılığıyla kullanılabilir.](#questions-and-answers)

Başlamak için:

- Python iş [yükünü ayarlamak](installing-python-support-in-visual-studio.md) için yükleme yönergelerini izleyin.
- Bu makaledeki bölümler aracılığıyla uygulamanın Python Visual Studio hakkında bilgi edinebilirsiniz.
::: moniker range="vs-2017"
- Proje oluşturmak için Bir veya daha fazla Hızlı Başlangıç'ın üzerinden gidin. Emin değilseniz [Flask ile web uygulaması oluşturma ile çalışmaya başlayabilirsiniz.](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)
::: moniker-end
::: moniker range=">=vs-2019"
- Proje oluşturmak için Bir veya daha fazla Hızlı Başlangıç'ın üzerinden gidin. Emin değilseniz Hızlı [Başlangıç:](quickstart-05-python-visual-studio-open-folder.md) Bir klasörde Python kodunu açma ve çalıştırma veya [Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)ile web uygulaması oluşturma ile çalışmaya başlama.
::: moniker-end
- Eksiksiz bir [uzlasma deneyimi Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) Python ile çalışma öğreticisi'ne bakın.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio Python sürüm 2.7'nin yanı sıra 3.5 ile 3.7 arasında bir sürümü destekler. Python'ın diğer Visual Studio yazılmış kodu düzenlemek için Visual Studio kullanılabilir, ancak bu sürümler resmi olarak desteklenemez ve IntelliSense ve hata ayıklama gibi özellikler çalışmayabiliyor. Python sürüm 3.8 desteği hala geliştirme aşamasındadır, destekle ilgili belirli ayrıntılar bu izleme [sorununda GitHub.](https://github.com/microsoft/PTVS/issues/5822)
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Birden çok yorumlayıcı desteği

Visual Studio **Python** Ortamları penceresi (aşağıda geniş ve genişletilmiş bir görünümde gösterilmiştir) tüm genel Python ortamlarınızı, conda ortamlarınızı ve sanal ortamlarınızı yönetmek için tek bir yer sağlar. Visual Studio, Standart konumlarda Python yüklemelerini otomatik olarak algılar ve özel yüklemeleri yapılandırmanızı sağlar. Her ortamla paketleri kolayca yönetebilir, bu ortam için etkileşimli bir pencere açabilir ve ortam klasörlerine erişebilirsiniz.

::: moniker range="vs-2017"
![Python Ortamları penceresinin genişletilmiş görünümü](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamları penceresinin genişletilmiş görünümü](media/environments/environments-expanded-view-2019.png)
::: moniker-end

**Python'ın etkileşimli bir** şekilde çalışması için Etkileşimli pencereyi aç komutunu Visual Studio. Seçili **ortamın klasöründe** ayrı bir komut penceresi açmak için PowerShell'de Aç komutunu kullanın. Bu komut penceresinden herhangi bir Python betiği çalıştırabilirsiniz.

Daha fazla bilgi için:

- [Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Python Ortamları başvurusu](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Zengin düzenleme, IntelliSense ve kod anlama

Visual Studio söz dizimi renklendirme, tüm kod ve kitaplıklar genelinde otomatik tamamlama, kod biçimlendirme, imza yardımı, yeniden düzenleme, linting ve tür ipuçları gibi birinci sınıf bir Python düzenleyicisi sağlar. Visual Studio sınıf görünümü, Tanıma Git, Tüm Başvuruları **Bul** ve kod parçacıkları **gibi** benzersiz özellikler de sağlar. Dosyayla doğrudan [Etkileşimli penceresi,](#interactive-window) zaten bir dosyaya kaydedilmiş Python kodunu hızlı bir şekilde geliştirmeye yardımcı olur.

![Python kodu için kod tamamlamaları Visual Studio](media/code-editing-completions-simple.png)

Daha fazla bilgi için:

- Docs: [Python kodunu düzenleme](editing-python-code-in-visual-studio.md)
- Docs: [Kodu biçimlendirme](formatting-python-code.md)
- Docs: [Kodu yeniden düzenleme](refactoring-python-code.md)
- Docs: [Linter kullanma](linting-python-code.md)
- Genel Visual Studio özellik belgeleri: [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Etkileşimli penceresi

Bilinen her Python ortamı Visual Studio, ayrı bir komut istemi kullanmak yerine aynı etkileşimli (REPL) ortamını bir Python yorumlayıcı için Visual Studio içinde kolayca açabilirsiniz. Ortamlar arasında da kolayca geçiş yapabilirsiniz. (Ayrı bir komut istemi açmak için **Python** Ortamları penceresinde istediğiniz ortamı seçin ve daha önce Birden çok yorumlayıcı desteği altında açıklanan **Şekilde PowerShell'de** Aç [komutunu seçin.)](#support-for-multiple-interpreters)

![Visual Studio'de Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio, Python kod düzenleyicisi ile Etkileşimli pencere arasında sıkı tümleştirme **de** sağlar. **Ctrl** Enter klavye kısayolu, düzenleyicide yer alan geçerli kod satırına (veya kod bloğuna) rahatça Etkileşimli pencereye gönderir ve sonraki satıra +  (veya bloğuna) ilerler.  **Ctrl tuşunu basılı tutarak** + **Enter,** hata ayıklayıcıyı çalıştırmak zorunda kalmadan kodda kolayca adım adım adım çalışmana olanak sağlar. Ayrıca, aynı tuş vuruşunu **kullanarak seçili** kodu Etkileşimli pencereye gönderebilir ve Etkileşimli penceresinden **düzenleyiciye** kolayca kod yapıştırabilirsiniz. Bu özellikler birlikte Etkileşimli penceresindeki bir kod kesiminin  ayrıntılarını bulup sonuçları düzenleyicide bir dosyaya kolayca kaydetmenize olanak sağlar.

Visual Studio satır içi çizimler, .NET ve IPyter (WPF) dahil olmak üzere REPL'de IPython/Jupyter'Windows Presentation Foundation destekler.

Daha fazla bilgi için:

- [Etkileşimli penceresi](python-interactive-repl-in-visual-studio.md)
- [Visual Studio'de IPython](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Project, proje ve öğe şablonları

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019, Python kodu içeren bir klasör açılmasını ve proje ve çözüm dosyaları oluşturmadan Visual Studio çalıştırmayı destekler. Daha fazla bilgi için [bkz. Hızlı Başlangıç: Python kodunu bir klasörde açma ve çalıştırma.](quickstart-05-python-visual-studio-open-folder.md) Ancak, bu bölümde açıklanan şekilde bir proje dosyası kullanmanın avantajları vardır.
::: moniker-end

Visual Studio, bir projenin zaman içinde büyüdükçe karmaşıklığını yönetmenize yardımcı olur. Bir *Visual Studio bir* klasör yapısından çok daha fazlasıdır: Farklı dosyaların nasıl kullanıldıklarının ve bunların birbirine nasıl ilişkili olduğunu anlamayı içerir. Visual Studio, uygulama kodunu, test kodunu, web sayfalarını, JavaScript'i, derleme betiklerini ve daha sonra dosyaya uygun özellikleri etkinleştirmeyi ayırt yardımcı olur. Ayrıca Visual Studio, Python projesi ve C++ uzantısı projesi gibi birden çok ilgili projeyi yönetmenize de yardımcı olur.

![Hem Python Visual Studio C++ projelerini içeren bir çözüm](media/projects-solution-explorer-two-projects.png)

Project ve öğe şablonları, farklı türlerde projeler ve dosyalar ayarlama sürecini otomatikleştirerek değerli zaman tasarrufu sağlar ve karmaşık ve hataya açık ayrıntıların yönetilmesinden tasarruf sağlar. Visual Studio; Python sınıfları, birim testleri, Azure web yapılandırması, HTML ve hatta Django uygulamaları gibi dosyalar için şablonların yanı sıra web, Azure, veri bilimi, konsol ve diğer proje türleri için şablonlar sağlar.

[![Visual Studio'de Python proje ve öğe Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Daha fazla bilgi için:

- Docs: [Python projelerini yönetme](managing-python-projects-in-visual-studio.md)
- Docs: [Öğe şablonları başvurusu](python-item-templates.md)
- Docs: [Python proje şablonları](managing-python-projects-in-visual-studio.md#project-templates)
- Docs: [C++ ve Python ile çalışma](working-with-c-cpp-python-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [Project ve öğe şablonları](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Genel Visual Studio özellik belgeleri: [Belgelerde çözümler ve Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Tam özellikli hata ayıklama

Bu Visual Studio güçlü hata ayıklayıcısıdır. Özellikle Python için Python/C++ Visual Studio mod hata ayıklama, Linux üzerinde uzaktan hata ayıklama, Etkileşimli pencere içinde hata ayıklama ve Python birim testlerinde hata ayıklama özellikleri vardır. 

![Visual Studio özel durum açılan pencereyi gösteren Python için hata ayıklayıcısı](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
2019'Visual Studio içinde, bir proje dosyası olmadan kodu çalıştırabilir ve Visual Studio ayıkabilirsiniz. Örnek [için bkz. Hızlı Başlangıç: Python kodunu bir klasörde açma](quickstart-05-python-visual-studio-open-folder.md) ve çalıştırma.
::: moniker-end

Daha fazla bilgi için:

- Docs: [Python'da hata ayıklama](debugging-python-in-visual-studio.md)
- Docs: [Python/C++ karma mod hata ayıklaması](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Docs: [Linux'ta uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- Genel Visual Studio özellik belgeleri: [Visual Studio Debugger'ın özellik turu](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Kapsamlı raporlama ile profil oluşturma araçları

Profil oluşturma, sürenin uygulamanız içinde nasıl harcanıyor olduğunu inceler. Visual Studio CPython tabanlı yorumlayıcılarla profil oluşturmayı destekler ve farklı profil oluşturma çalıştırmaları arasındaki performansı karşılaştırma olanağını içerir.

[![Visual Studio Python projesi için profil oluşturma sonuçlarını oluşturma](media/profiling-results.png)](media/profiling-results.png#lightbox)

Daha fazla bilgi için:

- Docs: [Python profil oluşturma araçları](profiling-python-code-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [Profil Oluşturma Özelliği Turu.](../profiling/profiling-feature-tour.md) (Tüm Visual Studio profil oluşturma özellikleri Python'da kullanılamaz).

## <a name="unit-testing-tools"></a>Birim testi araçları

Test Gezgini'nde testleri keşfedin, çalıştırın Visual Studio **yönetin** ve birim testlerinde kolayca hata ayıklayabilirsiniz.

![Visual Studio'da Python birim testinde hata ayıklama](media/unit-test-debugging.png)

Daha fazla bilgi için:

- Docs: [Python için birim testi araçları](unit-testing-python-in-visual-studio.md)
- genel Visual Studio özelliği belgeleri: [birim testi kodunuz](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Python için Azure SDK

Python için azure kitaplıkları Windows, Mac OS X ve Linux uygulamalarından azure hizmetlerini kullanmayı basitleştirir. Bunları Azure kaynakları oluşturmak ve yönetmek için, ayrıca Azure hizmetlerine bağlanmak için de kullanabilirsiniz. 

Daha fazla bilgi için bkz. [Python Için Azure SDK](/azure/python/) ve [Python için Azure kitaplıkları](/azure/python/python-sdk-azure-overview) .

## <a name="questions-and-answers"></a>Sorular ve cevaplar

**Ç. Python desteği Mac için Visual Studio ile kullanılabilir mi?**

A. Şu anda değil, ancak [geliştirici Community](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html)isteği oylayabilirsiniz. [Mac için Visual Studio](/visualstudio/mac/) belgeleri, desteklediği geliştirmenin geçerli türlerini tanımlar. bu sırada, Windows, Mac ve Linux üzerinde Visual Studio Code, [kullanılabilir uzantılar aracılığıyla Python ile iyi şekilde](https://code.visualstudio.com/docs/languages/python)çalışacaktır.

**Ç. Python ile Kullanıcı arabirimi oluşturmak için ne kullanabilirim?**

A. bu alandaki ana teklif, ( [resmi bağlama) pyside (resmi bağlama)](https://wiki.qt.io/PySide) olarak bilinen Python için bağlamaları (ayrıca bkz. [pyside indirmeleri](https://download.qt.io/official_releases/pyside/.)) ve [pyqt](https://wiki.python.org/moin/PyQt)' [Project](https://www.qt.io/qt-for-application-development/)dir. mevcut olduğunda, Visual Studio 'de Python desteği, uı geliştirmesi için herhangi bir belirli araç içermez.

**Ç. Bir Python projesi tek başına yürütülebilir bir dosya oluşturabilir mi?**

A. python genellikle kodun, Visual Studio ve web sunucuları gibi uygun bir Python özellikli ortamda isteğe bağlı olarak çalıştırıldığı yorumlanan bir dildir. Visual Studio kendisi, bir tek başına yürütülebilir dosya oluşturma, aslında katıştırılmış Python yorumlayıcı içeren bir program anlamına gelir. Ancak, Python topluluğu farklı şekilde sağlanmış olduğundan, [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)adresinde açıklandığı şekilde yürütülebilir dosyalar oluşturma anlamına gelir. Cpyıthon Ayrıca, [cpıthon 'un eklenebilir ZIP dosyası kullanılarak](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)blog gönderisine göre yerel bir uygulama içine katıştırılmakta da desteklenir.

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Özellik desteği

Python özellikleri, [yükleme kılavuzunda](installing-python-support-in-visual-studio.md)açıklandığı gibi Visual Studio aşağıdaki sürümlerine yüklenebilir:

- [Visual Studio 2019 (tüm sürümler)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (tüm sürümler)
- Visual Studio 2015 (tüm sürümler)
- Visual Studio 2013 Community sürümü
- Visual Studio 2013 Web için Express, güncelleştirme 2 veya üzeri
- Visual Studio 2013 Masaüstü için Express, güncelleştirme 2 veya üzeri
- Visual Studio 2013 (Pro edition veya üzeri)
- Visual Studio 2012 (Pro edition veya üzeri)
- Visual Studio 2010 SP1 (Pro edition veya üzeri; .net 4,5 gerekir)

Visual Studio 2015 ve önceki sürümleri [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/)adresinde bulunabilir.

> [!Important]
> Özellikler yalnızca Visual Studio en son sürümü için tam olarak desteklenir ve sürdürülür. Özellikler eski sürümlerde mevcuttur ancak etkin bir şekilde korunmaz.

|          Python desteği          |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Birden çok yorumlayıcıları yönetme   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Popüler yorumlayıcıları otomatik algıla | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Özel yorumlayıcılar ekleme      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Sanal ortamlar       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         PIP/kolay yüklemesi         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

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
|        Otomatik tamamlama         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        İmza yardımı        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Hızlı bilgi          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Nesne tarayıcısı/sınıf görünümü   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Gezinti çubuğu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Tanıma Git       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          sayfasına gidin          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Tüm Başvuruları Bul      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Otomatik girintileme       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
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

|               Masaüstü               |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Konsol/Windows uygulaması     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IronPython WPF (XAML tasarımcısı ile) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      IronPython Windows Forms       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Django web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Bottle web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Flask web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Genel web projesi | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü |       2013 Web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Web sitesine dağıtma   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Web rolüne dağıt   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Çalışan rolüne dağıt  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Azure öykünücüsü 'nde Çalıştır  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Uzaktan hata ayıklama    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Sunucu Gezgini Ekle | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Docgo şablonları           |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü |       2013 Web       |      2013 Pro +       | 2012 Pro + | 2010 SP1 Pro + |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Hata Ayıklama               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Otomatik tamamlama             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| CSS ve JavaScript için otomatik tamamlanma | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Hata Ayıklama                  |   2017 +   |   2015   | 2013 Comm | 2013 Masaüstü | 2013 Web | 2013 Pro + | 2012 Pro + | 2010 SP1 Pro + |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Hata Ayıklama                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Proje olmadan hata ayıklama         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Hata ayıklama - düzenlemeye ekleme        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Karma mod hata ayıklama             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Uzaktan hata ayıklama (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
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

1. Visual Studio 2012 için Git desteği, Visual Studio Araçları Market'te bulunan Git uzantısı [için Visual Studio mevcuttur.](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit)

1. Azure Web Sitesine dağıtım için [.NET 2.1 - Visual Studio 2010 SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids)için Azure SDK gerekir. Sonraki sürümler 2010 Visual Studio desteklemez.

1. Azure Web Rolü ve Çalışan Rolü desteği için [.NET 2.3 - VS 2012 veya](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) sonraki bir sürümü için Azure SDK gerekir.

1. Azure Web Rolü ve Çalışan Rolü desteği için [.NET 2.3 - VS 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) veya sonraki bir sürümü için Azure SDK gerekir.

1. Visual Studio 2013 Django şablon düzenleyicisinde Güncelleştirme 2 yükleyerek çözülen bazı bilinen sorunlar var.

1. Daha Windows 8 veya sonraki bir zaman gerektirir. Visual Studio 2013 Web için Express'te  İşleme Ekle iletişim kutusu yok, ancak Azure Web Sitesi uzaktan hata ayıklama işlemi, içinde Hata Ayıklayıcıyı Ekle **(Python)** komutu kullanılarak **Sunucu Gezgini.** Uzaktan hata ayıklama için [.NET 2.3 için Azure SDK - Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) veya sonraki bir sürümü gerekir.

1. Daha Windows 8 veya sonraki bir zaman gerektirir. .NET [2.3](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) için Azure SDK Sunucu Gezgini veya sonraki bir sürümü gerektirirken Hata Ayıklayıcı **(Python)** Visual Studio 2013 komutu. 

1. Daha Windows 8 veya sonraki bir zaman gerektirir.
::: moniker-end
