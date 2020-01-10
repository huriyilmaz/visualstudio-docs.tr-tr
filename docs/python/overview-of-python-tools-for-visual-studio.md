---
title: Windows üzerinde Visual Studio'da Python desteği
titleSuffix: ''
description: Visual Studio, Windows (PTVS Visual Studio için Python araçları olarak da bilinir) üzerinde en iyi Python IDE yapmadan Python özelliklerinin özeti.
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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845664"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Windows üzerinde Visual Studio'da Python ile çalışma

Python güvenilir, esnek, öğrenin, tüm işletim sistemlerinde kullanmak için ücretsiz daha kolay ve güçlü Geliştirici topluluğu ve çoğu ücretsiz kitaplıkları tarafından desteklenen yaygın bir programlama dilidir. Python geliştirme, web uygulamaları, web Hizmetleri, Masaüstü uygulamaları, komut dosyası ve bilimsel bilgi işleme dahil olmak üzere tüm yolla destekler ve birçok üniversiteler, uzmanları, sıradan geliştiriciler ve aynı şekilde profesyonel geliştiriciler tarafından kullanılır. Dili hakkında daha fazla bilgi edinebilirsiniz [python.org](https://www.python.org) ve [yeni başlayanlar için Python](https://www.python.org/about/gettingstarted/).

Visual Studio, Windows üzerinde güçlü bir Python ıde'dir. Visual Studio, **Python geliştirme** ve **veri bilimi** Iş yükleri (Visual Studio 2017 ve üzeri) ve ücretsiz Visual Studio için Python Araçları uzantısı (Visual Studio 2015 ve önceki sürümler) aracılığıyla Python dili için [açık kaynak](https://github.com/Microsoft/ptvs) desteği sağlar.

Python Mac için Visual Studio şu anda desteklenmiyor ancak Mac ve Linux'ta Visual Studio Code ile kullanılabilir (bkz [sorularını ve yanıtlarını](#questions-and-answers)).

Kullanmaya başlamak için:

- İzleyin [yükleme yönergeleri](installing-python-support-in-visual-studio.md) Python iş yükü ayarlanamadı.
- Bu makaledeki bölümler üzerinden Visual Studio Python yeteneklerini tanıyın.
::: moniker range="vs-2017"
- Bir veya daha fazla bir proje oluşturmak için hızlı başlangıç şablonları gidin. Emin değilseniz, başlayan [Flask ile web uygulaması oluşturma](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Bir veya daha fazla bir proje oluşturmak için hızlı başlangıç şablonları gidin. Emin değilseniz, [hızlı başlangıç: bir klasörde Python kodu açın ve çalıştırın](quickstart-05-python-visual-studio-open-folder.md) ya da [Flask ile bir Web uygulaması oluşturun](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- İzleyin [Visual Studio'da Python çalışın](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) baştan sona tam deneyim için öğretici.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio, Python sürüm 2,7 ' i ve sürüm 3,7 3,5 ' yi de destekler. Python 'un diğer sürümlerinde yazılmış kodu düzenlemek için Visual Studio 'Yu kullanmak mümkün olsa da, bu sürümler resmi olarak desteklenmez ve IntelliSense ve hata ayıklama gibi özellikler çalışmayabilir. Python sürüm 3,8 desteği hala geliştirme aşamasındadır ve bu izleme [sorunu GitHub](https://github.com/microsoft/PTVS/issues/5822)'da görülebilir.
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Birden çok yorumlayıcılarını desteği

Visual Studio'nun **Python ortamları** penceresi (aşağıda bir geniş, Genişletilmiş görünümde gösterilen) tek bir yerde tüm genel Python ortamları, conda ortamları ve sanal ortamları yönetmenizi sağlar. Visual Studio otomatik olarak standart konumlarda Python yüklemelerini algılar ve özel yüklemeleri yapılandırmanıza olanak tanır. Her bir ortam ile kolayca paketleri yönetebilir, bu ortam için etkileşimli bir pencere açın ve ortam klasörlere erişim.

::: moniker range="vs-2017"
![Python ortamları penceresinin Genişletilmiş Görünümü](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları penceresinin Genişletilmiş Görünümü](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Kullanım **açık etkileşimli pencere** Python etkileşimli olarak Visual Studio bağlamı içinde çalıştırmak için komutu. Kullanım **PowerShell'de açın** komutu seçili ortam klasöründe bir ayrı bir komut penceresi açın. Bu komut penceresinde herhangi bir python betiğini çalıştırabilirsiniz.

Daha fazla bilgi için:

- [Python ortamları yönetme](managing-python-environments-in-visual-studio.md)
- [Python ortamları başvurusu](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Zengin düzenleme, IntelliSense ve kod kavrama

Visual Studio söz dizimi renklendirme, otomatik tamamlama tüm kod ve kitaplıkları arasında kod biçimlendirme, imza Yardımı, yeniden düzenleme, linting ve tür ipuçlarına dahil birinci sınıf bir Python Düzenleyicisi sağlar. Visual Studio, sınıf görünümü gibi benzersiz özellikleri de sağlar **Tanıma Git**, **tüm başvuruları Bul**ve kod parçacıkları. Doğrudan tümleştirmesiyle [etkileşimli pencere](#interactive-window) , önceden bir dosyaya kaydedilir ve Python kodu hızla geliştirmenize yardımcı olur.

![Visual Studio'da Python kodu için kod tamamlama](media/code-editing-completions-simple.png)

Daha fazla bilgi için:

- Docs: [Python kodunu Düzenle](editing-python-code-in-visual-studio.md)
- Docs: [kod biçimlendirme](formatting-python-code.md)
- Docs: [kodu yeniden düzenleyin](refactoring-python-code.md)
- Docs: [bir lint kullanın](linting-python-code.md)
- Genel Visual Studio özellik belgeleri: [Kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Etkileşimli pencere

Bilinen Visual Studio için Python, her ortam için ayrı bir komut isteminde kullanmak yerine Visual Studio içinde doğrudan bir Python yorumlayıcısı için aynı etkileşimli (REPL) ortamı kolayca açabilirsiniz. De ortamlar arasında kolayca geçiş yapabilirsiniz. (Ayrı bir komut istemi açmak için istenen ortamınızda seçin **Python ortamları** penceresinde seçip **PowerShell'de açın** komutu altında daha önce açıklandığı gibi [desteği birden çok yorumlayıcılar için](#support-for-multiple-interpreters).)

![Visual Studio'da Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio da Python Kod Düzenleyicisi'ni arasında sıkı bir tümleştirme sağlar ve **etkileşimli** penceresi. **Ctrl**+**Enter** klavye kısayolu rahatça gönderdiğini Düzenleyicisi'nde kod (veya kod bloğu) geçerli satırı **etkileşimli** penceresini, sonra da taşır sonraki satır (veya blok). **CTRL**+**Enter** , hata ayıklayıcıyı çalıştırmak zorunda kalmadan kolayca kodu adımlayın sağlar. Seçilen koda da gönderebilirsiniz **etkileşimli** penceresinde aynı tuş vuruşu kaydetme ve kolayca kodunu yapıştırın **etkileşimli** Düzenleyici penceresine. Birlikte, bu özellikler, Ayrıntılar için kod kesiminin kullanıma çalışmanıza olanak sağlar **etkileşimli** penceresi ve sonuçları bir dosyayı düzenleyicide kolayca kaydedin.

Visual Studio, satır içi çizimleri, .NET ve Windows Presentation Foundation (WPF) gibi REPL Ipython/Jupyter da destekler.

Daha fazla bilgi için:

- [Etkileşimli pencere](python-interactive-repl-in-visual-studio.md)
- [Visual Studio 'da IPython](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Proje sistemi ve proje ve öğe şablonları

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019, Python kodu içeren bir klasörün açılmasını destekler ve Visual Studio proje ve çözüm dosyaları oluşturmadan kodu çalıştırır. Daha fazla bilgi için bkz. [hızlı başlangıç: Python kodunu bir klasörde açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md). Ancak, bu bölümde açıklandığı gibi bir proje dosyası kullanmanın avantajları vardır.
::: moniker-end

Visual Studio zamanla büyüdükçe, bir proje karmaşıklığını yönetmenize yardımcı olur. Bir *Visual Studio projesi* bir klasör yapısından çok daha fazla: farklı dosyaların nasıl kullanıldığına ve birbirleriyle nasıl ilişkilendirildiğine ilişkin bilgiler içerir. Visual Studio kodu, web sayfaları, JavaScript, derleme betikleri ve benzeri, ardından dosya uygun özellikler sağlayan test, uygulama kodu ayırt yardımcı olur. Bir Visual Studio çözümü, ayrıca, bir Python proje ve C++ uzantısı projesi gibi birden çok ilgili proje yönetmenize yardımcı olur.

![Hem Python hem de C++ projeleri içeren bir Visual Studio çözümü](media/projects-solution-explorer-two-projects.png)

Proje ve öğe şablonlarını projeleri ve dosyaları farklı türleri ayarlama, değerli zaman tasarrufu sağlar ve karmaşık ve hatalara eğilimli ayrıntılarını yönetmesini oluşturma işlemini otomatik hale getirin. Visual Studio, web, Azure, veri bilimi, konsol ve projeleri, dosyaları Python sınıfları, birim testleri, Azure web yapılandırması, HTML ve hatta Django uygulamaları gibi şablonları yanı sıra diğer türleri için şablonlar sağlar.

[![Visual Studio'da Python proje ve öğe şablonları](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Daha fazla bilgi için:

- Docs: [Yönet Python projeleri](managing-python-projects-in-visual-studio.md)
- Docs: [öğe şablonları başvurusu](python-item-templates.md)
- Docs: [Python proje şablonları](managing-python-projects-in-visual-studio.md#project-templates)
- Docs: [C++ ve Python ile çalışma](working-with-c-cpp-python-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [proje ve öğe şablonları](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Genel Visual Studio özellik belgeleri: [Visual Studio'da projeler ve çözümler](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Tam özellikli hata ayıklama

Visual Studio'nun güçlü, güçlü bir hata ayıklayıcı biridir. Python için Python/C++ karışık hata ayıklama, uzaktan hata ayıklama içinde hata ayıklama Linux'ta mod özellikle, Visual Studio içerir **etkileşimli** penceresi ve Python birim testleri hata ayıklama.

![Bir özel durum açılan gösteren Python için Visual Studio hata ayıklayıcı](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
Visual Studio 2019 ' de, Visual Studio proje dosyası olmadan kodu çalıştırabilir ve hata ayıklaması yapabilirsiniz. Bkz. [hızlı başlangıç: bir örnek için bir klasörde Python kodu açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md) .
::: moniker-end

Daha fazla bilgi için:

- Docs: [Python hata ayıklama](debugging-python-in-visual-studio.md)
- Docs: [Python/C++ karışık mod hata ayıklaması](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Docs: [Linux üzerinde uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- Genel Visual Studio özellik belgeleri: [özelliği Visual Studio hata ayıklayıcı turu](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Kapsamlı Raporlama ile profil oluşturma araçları

Profil oluşturma nasıl uygulamanızdaki zaman harcandığını keşfediyor. Visual Studio ile yorumlayıcılarını CPython tabanlı profil oluşturmayı destekler ve performans profil oluşturma farklı çalıştırma arasında karşılaştırma özelliğini içerir.

[![Python projesi için Visual Studio profil oluşturucu sonuç](media/profiling-results.png)](media/profiling-results.png#lightbox)

Daha fazla bilgi için:

- Docs: [Python profil oluşturma araçları](profiling-python-code-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [profil oluşturma özelliği Turu](../profiling/profiling-feature-tour.md). (Tüm Visual Studio profil oluşturma özellikleri, Python için mevcuttur).

## <a name="unit-testing-tools"></a>Birim test araçları

Bulma, çalıştırmak ve Visual Studio'da testleri yönetmek **Test Gezgini**ve birim testlerini kolayca hata ayıklayın.

![Bir test jednotky Pythonu Visual Studio'da hata ayıklama](media/unit-test-debugging.png)

Daha fazla bilgi için:

- Docs: [birim testi için Python araçları](unit-testing-python-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [birim testi kod](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Python için Azure SDK

Python için Azure kitaplıkları, Windows, Mac OS X ve Linux uygulamalarından Azure hizmetlerinin tüketilmesini basitleştirir. Bunları Azure kaynakları oluşturmak ve yönetmek için, ayrıca Azure hizmetlerine bağlanmak için de kullanabilirsiniz. 

Daha fazla bilgi için bkz. [Python Için Azure SDK](/azure/python/) ve [Python için Azure kitaplıkları](/azure/python/python-sdk-azure-overview) .

## <a name="questions-and-answers"></a>Sorular ve yanıtlar

**S. Mac için Visual Studio ile Python desteği sağlanıyor mu?**

BİR. Şu anda değil, ancak istek en fazla oy verebilirsiniz [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). [Mac için Visual Studio](/visualstudio/mac/) belgeleri destekleyen geliştirme geçerli türlerini tanımlar. Visual Studio Code sırada, Windows, Mac ve Linux'ta [kullanılabilir uzantıları aracılığıyla Python ile de çalışır](https://code.visualstudio.com/docs/languages/python).

**Soru-cevap ile Kullanıcı arabirimi oluşturmak için ne kullanabilirim?**

BİR. Bu alandaki ana tekliftir [Qt proje](https://www.qt.io/qt-for-application-development/), bilinen Python için bağlamaları ile [PySide (resmi bağlama)](https://wiki.qt.io/PySide) (Ayrıca bkz: [PySide indirir](https://download.qt.io/official_releases/pyside/.)) ve [ PyQt](https://wiki.python.org/moin/PyQt). Şu anda, herhangi belirli kullanıcı Arabirimi geliştirme araçları Visual Studio'da Python desteği içermez.

**Soru-cevap, bir Python projesi tek başına yürütülebilir bir dosya oluşturabilir mi?**

BİR. Python ile isteğe bağlı olarak Visual Studio ve web sunucuları gibi uygun bir Python özellikli ortam kod çalıştırılır, yorumlanan bir dil genellikle var. Visual Studio'nun kendisi, aslında bir programla katıştırılmış bir Python yorumlayıcısı anlamına gelir bir tek başına yürütülebilir oluşturmak için Araçlar şu anda sağlamaz. Ancak, yürütülebilir dosyalar üzerinde açıklandığı gibi oluşturmak için farklı yollardan Python topluluk tarafından sağlanan [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython da destekler yerel bir uygulama içinde gömülen blog gönderisi konusunda açıklandığı gibi [kullanarak CPython'ın gömülebilir zip dosyası](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/).

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Özellik desteği

Python özellikleri bölümünde anlatıldığı gibi aşağıdaki Visual Studio sürümlerinde yüklenebilir [Yükleme Kılavuzu](installing-python-support-in-visual-studio.md):

- [Visual Studio 2019 (tüm sürümler)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (tüm sürümler)
- Visual Studio 2015 (tüm sürümler)
- Visual Studio 2013 Community Edition
- Güncelleştirme 2 veya daha yüksek olan Web için Visual Studio 2013 Express
- Güncelleştirme 2 veya üzeri Masaüstü için Visual Studio 2013 Express
- Visual Studio 2013 (Pro sürümü veya üzeri)
- Visual Studio 2012 (Pro sürümü veya üzeri)
- Visual Studio 2010 SP1 (Pro sürümü veya üstü; .NET 4.5 gerekiyor)

Visual Studio 2015 veya önceki kullanılabilir [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Özellikleri tam olarak desteklenen ve yalnızca en son sürümü Visual Studio için korunur. Özellikleri, eski sürümlerinde kullanılabilir, ancak etkin bir şekilde korunmuyor.

|          Python desteği          |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + | 2012 pro + | 2010 SP1 Pro + |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Birden çok yorumlayıcılarını yönetme   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Popüler yorumlayıcılarını otomatik algıla | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Özel yorumlayıcılarını Ekle      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Sanal ortamlar       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         PIP/kolay yükleme         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Proje sistemi         |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + |      2012 pro +       | 2010 SP1 Pro + |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Mevcut koddan yeni proje | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         tüm dosyaları göster         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Kaynak denetimi         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Git tümleştirmesi         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Düzenleme            |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + | 2012 pro + | 2010 SP1 Pro + |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Söz dizimi vurgulama      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Otomatik Tamamlama         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        İmza Yardımı        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Hızlı bilgi          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Nesne tarayıcı/sınıf görünümü   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Gezinti çubuğu        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Tanıma Git       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Tüm Başvuruları Bul      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Otomatik Girinti       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Kod biçimlendirme        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Yeniden düzenleme - yeniden adlandır       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Yeniden düzenleme - extrahovat metodu   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Yeniden düzenleme - içeri aktarma Ekle/Kaldır | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Etkileşimli pencere     |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + | 2012 pro + | 2010 SP1 Pro + |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Etkileşimli pencere     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Ipython ile satır içi grafikleri | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Masaüstü               |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + | 2012 pro + | 2010 SP1 Pro + |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Konsol/Windows uygulaması     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| WPF v Ironpythonu (ile XAML Tasarımcısı) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Windows Forms v Ironpythonu       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + | 2012 pro + | 2010 SP1 Pro + |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Django web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Bottle web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Flask web projesi  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Obecný webový projekt | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü |       2013 web       |      2013 pro +       |      2012 pro +       |    2010 SP1 Pro +     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Web sitesine dağıtma   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Web rolü için dağıtma   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Çalışan rolü için dağıtma  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Azure öykünücüsünde çalıştırın  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Uzaktan hata ayıklama    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Sunucu Gezgini ekleme | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Django şablonları           |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü |       2013 web       |      2013 pro +       | 2012 pro + | 2010 SP1 Pro + |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Hata Ayıklama               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Otomatik Tamamlama             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| CSS ve JavaScript için otomatik tamamlama | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Hata Ayıklama                  |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + | 2012 pro + | 2010 SP1 Pro + |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Hata Ayıklama                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Hata ayıklama olmadan bir proje         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Hata ayıklama - düzenlemeye ekleme        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Karışık mod hata ayıklama             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Uzaktan hata ayıklama (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Hata ayıklama etkileşimli penceresi           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Profil Oluşturma |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + | 2012 pro + | 2010 SP1 Pro + |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Profil Oluşturma | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     {1&gt;Sınama&lt;1}      |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + | 2012 pro + | 2010 SP1 Pro + |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Test Gezgini | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Test çalıştırması    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Testte Hata Ayıkla   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Visual Studio 2012 için git desteği, git uzantısı için Visual Studio Araçları [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit)kullanılabilir.

1. Dağıtım için Azure Web sitesi gerektirir [.NET 2.1 - Visual Studio 2010 SP1 için Azure SDK'sı](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids). Sonraki sürümleri, Visual Studio 2010 desteklemez.

1. Azure Web rolü ve çalışan rolü için destek gerektiren [.NET 2.3 - VS 2012 için Azure SDK'sı](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) veya üzeri.

1. Azure Web rolü ve çalışan rolü için destek gerektiren [.NET 2.3 - VS 2013 için Azure SDK'sı](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) veya üzeri.

1. Django şablonu Düzenleyicisi'nde Visual Studio 2013 güncelleştirme 2'yi yükleme ile çözümlendiği bazı bilinen sorunlar vardır.

1. Windows 8 veya sonraki sürümünü gerektirir. Web için Visual Studio 2013 Express yoksa **iliştirme** iletişim, ancak Azure Web sitesi uzaktan hata ayıklama olmasına rağmen olası kullanarak **hata ayıklayıcısı ekleme (Python)** komutunu **sunucusu Explorer**. Uzaktan hata ayıklama gerektirir [.NET 2.3 - Visual Studio 2013 için Azure SDK'sı](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) veya üzeri.

1. Windows 8 veya sonraki sürümünü gerektirir. **Hata ayıklayıcının (Python)** komutunu **Sunucu Gezgini** gerektirir [.NET 2.3 - Visual Studio 2013 için Azure SDK'sı](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) veya üzeri.

1. Windows 8 veya sonraki sürümünü gerektirir.
::: moniker-end
