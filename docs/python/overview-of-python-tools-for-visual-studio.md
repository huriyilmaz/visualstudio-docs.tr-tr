---
title: Windows'da Visual Studio'da Python desteği
titleSuffix: ''
description: Visual Studio'daki Python özelliklerinin özeti, windows'daki en iyi Python IDE 'si (Visual Studio için Python Tools, PTVS olarak da bilinir).
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a913fa6abdcf59a64d8514f17656b8f8531d476d
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302793"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Windows'da Visual Studio'da Python ile çalışma

Python güvenilir, esnek, öğrenmesi kolay, tüm işletim sistemlerinde kullanımı ücretsiz ve hem güçlü bir geliştirici topluluğu hem de birçok ücretsiz kütüphane tarafından desteklenen popüler bir programlama dilidir. Python, web uygulamaları, web hizmetleri, masaüstü uygulamaları, komut dosyası oluşturma ve bilimsel bilgi işlem dahil olmak üzere tüm geliştirme yöntemlerini destekler ve birçok üniversite, bilim adamı, gündelik geliştiriciler ve profesyonel geliştiriciler tarafından kullanılır. [Yeni Başlayanlar için](https://www.python.org/about/gettingstarted/) [python.org](https://www.python.org) ve Python dil hakkında daha fazla bilgi edinebilirsiniz.

Visual Studio, Windows'da güçlü bir Python IDE'dir. Visual Studio, Python Geliştirme ve **Veri Bilimi** iş yükleri (Visual Studio 2017 ve sonrası) ve Visual Studio uzantısı için ücretsiz Python Tools (Visual Studio 2015 ve öncesi) aracılığıyla **Python** dili için [açık kaynak](https://github.com/Microsoft/ptvs) desteği sağlar.

Python şu anda Visual Studio for Mac'te desteklenmez, ancak Visual Studio Code aracılığıyla Mac ve Linux'ta kullanılabilir [(soru ve cevaplara](#questions-and-answers)bakın).

Başlamak için:

- Python iş yükünü ayarlamak için [yükleme yönergelerini](installing-python-support-in-visual-studio.md) izleyin.
- Bu makaledeki bölümler aracılığıyla Visual Studio'nun Python yeteneklerine aşina olun.
::: moniker range="vs-2017"
- Bir proje oluşturmak için Quickstarts bir veya daha fazla gidin. Emin değilseniz, [Flask ile bir web uygulaması oluşturun ile](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)başlayın.
::: moniker-end
::: moniker range=">=vs-2019"
- Bir proje oluşturmak için Quickstarts bir veya daha fazla gidin. Emin değilseniz, Quickstart ile [başlayın: Python kodunu bir klasörde açın ve çalıştırın](quickstart-05-python-visual-studio-open-folder.md) veya [Flask ile bir web uygulaması oluşturun.](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)
::: moniker-end
- Tam bir uç-uç deneyim için Visual Studio öğretici [Python ile Çalışma](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) izleyin.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio Python sürüm 2.7'nin yanı sıra 3.5'ten 3.7'ye kadar olan sürümleri destekler. Python'un diğer sürümlerinde yazılan kodu yeniden kullanmak için Visual Studio'yu kullanmak mümkün olsa da, bu sürümler resmi olarak desteklenmez ve IntelliSense ve hata ayıklama gibi özellikler çalışmayabilir. Python sürüm 3.8 desteği hala geliştirilmekte, destek hakkında belirli ayrıntılar [GitHub bu](https://github.com/microsoft/PTVS/issues/5822)izleme sorunu görülebilir.
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Birden fazla yorumlayıcı için destek

Visual Studio'nun **Python Ortamları** penceresi (aşağıda geniş ve genişletilmiş bir görünümde gösterilmiştir) tüm küresel Python ortamlarınızı, conda ortamlarınızı ve sanal ortamlarınızı yönetmek için tek bir yer sağlar. Visual Studio, Python'un yüklemelerini standart konumlardaki yüklemeleri otomatik olarak algılar ve özel yüklemeleri yapılandırmanızı sağlar. Her ortamda paketleri kolayca yönetebilir, bu ortam için etkileşimli bir pencere açabilir ve ortam klasörlerine erişebilirsiniz.

::: moniker range="vs-2017"
![Python Ortamları penceresinin genişletilmiş görünümü](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamları penceresinin genişletilmiş görünümü](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Python'u Visual Studio bağlamında etkileşimli olarak çalıştırmak için **Etkileşimli Aç komutunu** kullanın. Seçili ortamın klasöründe ayrı bir komut penceresi açmak için **PowerShell'de Aç** komutunu kullanın. Bu komut penceresinden herhangi bir python komut dosyası çalıştırabilirsiniz.

Daha fazla bilgi için:

- [Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Python Ortamları başvurusu](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Zengin düzenleme, IntelliSense ve kod anlama

Visual Studio, sözdizimi boyama, tüm kod ve kitaplıklar arasında otomatik olarak tam, kod biçimlendirme, imza yardımı, yeniden düzenleme, linting ve tür ipuçları nı içeren birinci sınıf bir Python düzenleyicisi sağlar. Visual Studio ayrıca sınıf görünümü, **Tanıya Git,** **Tüm Referansları Bul**ve kod parçacıkları gibi benzersiz özellikler de sağlar. [Etkileşimli pencereyle](#interactive-window) doğrudan tümleştirme, zaten bir dosyaya kaydedilmiş olan Python kodunu hızla geliştirmenize yardımcı olur.

![Visual Studio'da Python kodu için kod tamamlama](media/code-editing-completions-simple.png)

Daha fazla bilgi için:

- Dokümanlar: [Python kodunu edit](editing-python-code-in-visual-studio.md)
- Dokümanlar: [Kodu biçimlendir](formatting-python-code.md)
- Dokümanlar: [Refactor kodu](refactoring-python-code.md)
- Dokümanlar: [Linter kullanın](linting-python-code.md)
- Genel Visual Studio özellik dokümanları: [Kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Etkileşimli pencere

Visual Studio tarafından bilinen her Python ortamı için, ayrı bir komut istemi kullanmak yerine, doğrudan Visual Studio içinde bir Python yorumlayıcısı için aynı etkileşimli (REPL) ortamı kolayca açabilirsiniz. Ortamlar arasında da kolayca geçiş yapabilirsiniz. (Ayrı bir komut istemi açmak için **Python Ortamları** penceresinde istediğiniz ortamı seçin ve ardından [birden çok yorumlayıcı için Destek](#support-for-multiple-interpreters)altında daha önce açıklandığı gibi **PowerShell'de Aç** komutunu seçin.)

![Visual Studio'da Python etkileşimli pencere](media/interactive-window.png)

Visual Studio ayrıca Python kod düzenleyicisi ile **Etkileşimli** pencere arasında sıkı tümleştirme sağlar. **Ctrl**+**Enter** klavye kısayolu, düzenleyicideki geçerli kod satırını (veya kod bloğunu) **etkileşimli** pencereye gönderir ve bir sonraki satıra (veya bloka) geçer. **Ctrl**+**Enter,** hata ayıklayıcıyı çalıştırmak zorunda kalmadan kodda kolayca adım atmanızı sağlar. Ayrıca, seçili kodu **etkileşimli** pencereye aynı tuş vuruşuyla gönderebilir ve **Etkileşimli** pencereden düzenleyiciye kolayca kod yapıştırabilirsiniz. Bu özellikler birlikte, **Etkileşimli** penceredeki bir kod kesiminin ayrıntılarını çözmenize ve sonuçları düzenleyicideki bir dosyaya kolayca kaydetmenize olanak sağlar.

Visual Studio ayrıca, satır satır çizimleri, .NET ve Windows Presentation Foundation (WPF) dahil olmak üzere REPL'de IPython/Jupyter'ı destekler.

Daha fazla bilgi için:

- [Etkileşimli pencere](python-interactive-repl-in-visual-studio.md)
- [Görsel Stüdyo'da IPython](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Proje sistemi ve proje ve madde şablonları

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019, Python kodu içeren bir klasör açmayı ve Visual Studio proje ve çözüm dosyaları oluşturmadan bu kodu çalıştırmayı destekler. Daha fazla bilgi için [Bkz. Quickstart: Python kodunu bir klasörde açın ve çalıştırın.](quickstart-05-python-visual-studio-open-folder.md) Ancak, bu bölümde açıklandığı gibi, bir proje dosyası kullanmanın yararları vardır.
::: moniker-end

Visual Studio, zaman içinde büyüdükçe bir projenin karmaşıklığını yönetmenize yardımcı olur. *Visual Studio projesi* bir klasör yapısından çok daha fazlasıdır: farklı dosyaların nasıl kullanıldığı ve birbirleriyle nasıl ilişkili oldukları hakkında bir anlayış içerir. Visual Studio, uygulama kodunu, test kodunu, web sayfalarını, JavaScript'i, komut dosyalarını oluşturmanızı ve daha sonra dosyaya uygun özellikleri etkinleştirmenizi sağlamanıza yardımcı olur. Ayrıca Visual Studio çözümü, Python projesi ve C++ uzantıprojesi gibi birçok ilgili projeyi yönetmenize yardımcı olur.

![Python ve C++ projelerini içeren bir Visual Studio çözümü](media/projects-solution-explorer-two-projects.png)

Proje ve madde şablonları, farklı proje ve dosya türlerini ayarlama işlemini otomatikleştirerek değerli zaman ları kurtarır ve karmaşık ve hataya açık ayrıntıları yönetmeniz için sizi rahatlatur. Visual Studio, Web, Azure, veri bilimi, konsol ve diğer proje türleri için şablonların yanı sıra Python sınıfları, birim testleri, Azure web yapılandırması, HTML ve hatta Django uygulamaları gibi dosyalar için şablonlar sağlar.

[![Visual Studio'da Python proje ve öğe şablonları](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Daha fazla bilgi için:

- Dokümanlar: [Python projelerini yönetin](managing-python-projects-in-visual-studio.md)
- Dokümanlar: [Öğe şablonları başvurusu](python-item-templates.md)
- Dokümanlar: [Python proje şablonları](managing-python-projects-in-visual-studio.md#project-templates)
- Dokümanlar: [C++ ve Python ile çalışın](working-with-c-cpp-python-in-visual-studio.md)
- Genel Görsel Stüdyo özellik dokümanları: [Proje ve öğe şablonları](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Genel Görsel Stüdyo özelliği dokümanlar: [Çözümleri ve Visual Studio projeler](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Tam özellikli hata ayıklama

Visual Studio'nun güçlü yanlarından biri güçlü hata ayıklamadır. Özellikle Python için Visual Studio, Python/C++ karışık mod hata ayıklama, Linux'ta uzaktan hata ayıklama, **Etkileşimli** pencere içinde hata ayıklama ve Python birim testlerini hata ayıklama içerir.

![Python için Visual Studio hata ayıklama bir özel durum açılır pencere gösteren](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
Visual Studio 2019'da Visual Studio proje dosyasına sahip olmadan kodu çalıştırıp hata ayıklayabilirsiniz. Bkz. Hızlı Başlangıç: Bir klasörde örneğin [Python kodunu açın ve çalıştırın.](quickstart-05-python-visual-studio-open-folder.md)
::: moniker-end

Daha fazla bilgi için:

- Dokümanlar: [Hata Ayıklama Python](debugging-python-in-visual-studio.md)
- Dokümanlar: [Python/C++ karışık mod hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Dokümanlar: [Linux'ta uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- Genel Görsel Studio özellik dokümanlar: [Visual Studio Debugger Özellik tur](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Kapsamlı raporlama ile profil oluşturma araçları

Profil oluşturma, uygulamanızda zamanın nasıl harcandırıldığını inceler. Visual Studio, CPython tabanlı yorumlayıcılarla profil oluşturmayı destekler ve performansı farklı profil oluşturma çalıştırmaları arasında karşılaştırma olanağı içerir.

[![Python projesi için Visual Studio profilleyici sonuçları](media/profiling-results.png)](media/profiling-results.png#lightbox)

Daha fazla bilgi için:

- Dokümanlar: [Python profil oluşturma araçları](profiling-python-code-in-visual-studio.md)
- Genel Görsel Studio özelliği docs: [Profil Özelliği Tur](../profiling/profiling-feature-tour.md). (Tüm Visual Studio profil oluşturma özellikleri Python için kullanılamaz).

## <a name="unit-testing-tools"></a>Birim test araçları

Visual Studio **Test Explorer'da**testleri keşfedin, çalıştırın ve yönetin ve birim testlerini kolayca hata ayıkla.

![Visual Studio'da Python birim testini hata ayıklama](media/unit-test-debugging.png)

Daha fazla bilgi için:

- Dokümanlar: [Python için birim test araçları](unit-testing-python-in-visual-studio.md)
- Genel Görsel Stüdyo özelliği dokümanları: [Birim kodutest edin.](../test/unit-test-your-code.md)

## <a name="azure-sdk-for-python"></a>Python için Azure SDK

Python için Azure kitaplıkları, Windows, Mac OS X ve Linux uygulamalarından Azure hizmetlerini tüketen leri basitleştirir. Bunları Azure kaynakları oluşturmak ve yönetmek ve Azure hizmetlerine bağlanmak için kullanabilirsiniz. 

Daha fazla bilgi için [Python için Azure SDK](/azure/python/) ve [Python için Azure kitaplıklarına](/azure/python/python-sdk-azure-overview) bakın.

## <a name="questions-and-answers"></a>Sorular ve cevaplar

**S. Python desteği Visual Studio for Mac ile kullanılabilir mi?**

A. Şu anda değil, ancak [Geliştirici Topluluğu'ndaki](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html)isteği oylayabilirsiniz. Mac belgeleri [için Visual Studio,](/visualstudio/mac/) desteklediği geçerli geliştirme türlerini tanımlar. Bu arada, Windows, Mac ve Linux Visual Studio Code [mevcut uzantıları aracılığıyla Python ile iyi çalışır.](https://code.visualstudio.com/docs/languages/python)

**S. Python ile UI oluşturmak için ne kullanabilirim?**

A. Bu alanda ana sunan [Qt Projesi](https://www.qt.io/qt-for-application-development/), [Python pyside (resmi bağlama) (ayrıca](https://wiki.qt.io/PySide) [PySide indirme](https://download.qt.io/official_releases/pyside/.)bakınız) ve [PyQt](https://wiki.python.org/moin/PyQt)olarak bilinen ciltler ile. Şu anda Visual Studio'daki Python desteği, UI geliştirme için belirli araçlar içermez.

**S. Bir Python projesi tek başına yürütülebilir bir proje üretebilir mi?**

A. Python genellikle visual studio ve web sunucuları gibi uygun bir Python özellikli ortamda kod isteğe bağlı olarak çalıştırılan yorumlanmış bir dildir. Visual Studio kendisi şu anda tek başına yürütülebilir oluşturmak için araçlar sağlamaz, hangi aslında gömülü bir Python yorumlayıcısı ile bir program anlamına gelir. Ancak, Python topluluğu [StackOverflow'da](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)açıklandığı gibi yürütülebilir araçlar oluşturmak için farklı araçlar sağladı. CPython da yerel bir uygulama içinde gömülü olmayı destekler, blog yazısı açıklandığı gibi, [CPython's embedddable zip dosyasını kullanarak](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/).

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Özellik desteği

Python [özellikleri, yükleme kılavuzunda](installing-python-support-in-visual-studio.md)açıklandığı gibi Visual Studio'nun aşağıdaki sürümlerinde yüklenebilir:

- [Visual Studio 2019 (tüm sürümler)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (tüm sürümler)
- Visual Studio 2015 (tüm sürümler)
- Visual Studio 2013 Topluluk Sürümü
- Web için Visual Studio 2013 Express, Update 2 veya üzeri
- Masaüstü için Visual Studio 2013 Express, Update 2 veya üzeri
- Visual Studio 2013 (Pro sürümü veya üstü)
- Visual Studio 2012 (Pro baskı veya üstü)
- Visual Studio 2010 SP1 (Pro baskı veya üzeri; .NET 4.5 gerekli)

Visual Studio 2015 ve daha önce [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/)mevcuttur.

> [!Important]
> Özellikler, Visual Studio'nun yalnızca en son sürümü için tam olarak desteklenir ve korunur. Özellikler eski sürümlerde kullanılabilir, ancak etkin olarak korunmuyor.

|          Python desteği          |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Birden çok yorumlayıcıyı yönetme   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Popüler tercümanları otomatik olarak algılama | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Özel tercümanlar ekleme      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Sanal Ortamlar       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Pip/Kolay Yükleme         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Proje sistemi         |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar | 2013 Web | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Varolan koddan yeni proje | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Tüm dosyaları göster         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Kaynak denetimi         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Git ile tümleştirme         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Düzenleme            |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Sözdizimi vurgulama      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Otomatik tamamlama         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        İmza yardımı        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Hızlı bilgi          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Nesne tarayıcı/sınıf görünümü   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Gezinti çubuğu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Tanıma Git       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Gezinme          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Tüm Başvuruları Bul      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Otomatik girintisi       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Kod biçimlendirme        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refactor - yeniden adlandırma       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refactor - özü yöntemi   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refactor - ekle/kaldırma alma | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Etkileşimli pencere     |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Etkileşimli pencere     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Satır çizgisi grafikleri olan IPython | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Masaüstü               |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Konsol/Windows uygulaması     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IronPython WPF (XAML tasarımcısı ile) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      IronPython Windows Formları       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Django web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Şişe web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Flask web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Genel web projesi | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar |       2013 Web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Web sitesine dağıt   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Web rolüne dağıtma   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| İşçi rolüne dağıtma  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Azure emülatörde çalıştırın  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Uzaktan hata ayıklama    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Sunucu Gezgini Ekle | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Django şablonları           |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar |       2013 Web       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Hata ayıklama               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Otomatik tamamlama             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| CSS ve JavaScript için otomatik tamamlama | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Hata ayıklama                  |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Hata ayıklama                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Proje olmadan hata ayıklama         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Hata ayıklama - düzenlemeye iliştirme        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Karışık mod hata ayıklama             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Uzaktan hata ayıklama (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Hata Ayıklama Etkileşimli pencere           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profil oluşturma |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profil oluşturma | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Test      |   2017+   |   2015   | 2013 Comm | 2013 Masaüstü Bilgisayar | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Test gezgini | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Testi çalıştır    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Hata ayıklama testi   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Visual Studio için Git desteği 2012 Git uzantısı için Visual Studio Tools mevcuttur, [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit)mevcuttur.

1. Azure Web Sitesine Dağıtım [için .NET 2.1 - Visual Studio 2010 SP1 için Azure SDK](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids)gerekir. Sonraki sürümler Visual Studio 2010'u desteklemez.

1. Azure Web Rolü ve Çalışan Rolü desteği [için .NET 2.3 - VS 2012](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) veya sonrası için Azure SDK'sı gerektirir.

1. Azure Web Rolü ve Çalışan Rolü desteği [için .NET 2.3 - VS 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) veya sonraki düzey ler için Azure SDK'sı gerektirir.

1. Visual Studio 2013'teki Django şablon düzenleyicisinde Güncelleme 2'yi yükleyerek çözülen bazı bilinen sorunlar vardır.

1. Windows 8 veya daha sonra gerektirir. Visual Studio 2013 Web için Express'te **İşleme Ekle** iletişim kutusu yoktur, ancak Azure Web Sitesi uzaktan hata ayıklama, **Server Explorer'daki** **Hata Ayıklama (Python)** komutunu kullanarak hala mümkündür. Uzaktan hata ayıklama [için .NET 2.3 - Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) veya sonrası için Azure SDK'sı gerektirir.

1. Windows 8 veya daha sonra gerektirir. **Sunucu Gezgini'nde** **Hata Ayıklayıcı (Python)** komutunu [ekle ,NET 2.3 için Azure SDK gerektirir - Visual Studio 2013](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) veya sonraki.

1. Windows 8 veya daha sonra gerektirir.
::: moniker-end
