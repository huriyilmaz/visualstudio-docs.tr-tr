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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409040"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Windows üzerinde Visual Studio'da Python ile çalışma

Python güvenilir, esnek, öğrenin, tüm işletim sistemlerinde kullanmak için ücretsiz daha kolay ve güçlü Geliştirici topluluğu ve çoğu ücretsiz kitaplıkları tarafından desteklenen yaygın bir programlama dilidir. Python geliştirme, web uygulamaları, web Hizmetleri, Masaüstü uygulamaları, komut dosyası ve bilimsel bilgi işleme dahil olmak üzere tüm yolla destekler ve birçok üniversiteler, uzmanları, sıradan geliştiriciler ve aynı şekilde profesyonel geliştiriciler tarafından kullanılır. [Python.org](https://www.python.org) ve [Yeni başlayanlar için Python](https://www.python.org/about/gettingstarted/)'da dil hakkında daha fazla bilgi edinebilirsiniz.

Visual Studio, Windows üzerinde güçlü bir Python ıde'dir. Visual Studio, **Python geliştirme** ve **veri bilimi** Iş yükleri (Visual Studio 2017 ve üzeri) ve ücretsiz Visual Studio için Python Araçları uzantısı (Visual Studio 2015 ve önceki sürümler) aracılığıyla Python dili için [açık kaynak](https://github.com/Microsoft/ptvs) desteği sağlar.

Python şu anda Mac için Visual Studio desteklenmemektedir, ancak Mac ve Linux 'ta Visual Studio Code aracılığıyla kullanılabilir (bkz. [sorular ve yanıtlar](#questions-and-answers)).

Başlamak için:

- Python iş yükünü ayarlamak için [yükleme yönergelerini](installing-python-support-in-visual-studio.md) izleyin.
- Bu makaledeki bölümler üzerinden Visual Studio Python yeteneklerini tanıyın.
::: moniker range="vs-2017"
- Bir veya daha fazla bir proje oluşturmak için hızlı başlangıç şablonları gidin. Emin değilseniz [Flask ile Web uygulaması oluşturma](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)ile başlayın.
::: moniker-end
::: moniker range=">=vs-2019"
- Bir veya daha fazla bir proje oluşturmak için hızlı başlangıç şablonları gidin. Emin değilseniz, [hızlı başlangıç: bir klasörde Python kodu açın ve çalıştırın](quickstart-05-python-visual-studio-open-folder.md) ya da [Flask ile bir Web uygulaması oluşturun](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- Eksiksiz bir uçtan uca deneyim için [Visual Studio 'Da Python Ile çalışmayı](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) izleyin.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio, Python sürüm 2,7 ' i ve sürüm 3,7 3,5 ' yi de destekler. Python 'un diğer sürümlerinde yazılmış kodu düzenlemek için Visual Studio 'Yu kullanmak mümkün olsa da, bu sürümler resmi olarak desteklenmez ve IntelliSense ve hata ayıklama gibi özellikler çalışmayabilir. Python sürüm 3,8 desteği hala geliştirme aşamasındadır ve bu izleme [sorunu GitHub](https://github.com/microsoft/PTVS/issues/5822)'da görülebilir.
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Birden çok yorumlayıcılarını desteği

Visual Studio 'nun **Python ortamları** penceresi (aşağıda, geniş ve genişletilmiş bir görünümde gösterilmektedir), tüm genel Python ortamlarınızı, Conda ortamlarınızı ve Sanal ortamlarınızı yönetmek için size tek bir yer sunar. Visual Studio otomatik olarak standart konumlarda Python yüklemelerini algılar ve özel yüklemeleri yapılandırmanıza olanak tanır. Her bir ortam ile kolayca paketleri yönetebilir, bu ortam için etkileşimli bir pencere açın ve ortam klasörlere erişim.

::: moniker range="vs-2017"
![Python ortamları penceresinin Genişletilmiş Görünümü](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları penceresinin Genişletilmiş Görünümü](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Visual Studio 'nun bağlamında Python 'ı etkileşimli olarak çalıştırmak için **etkileşimli pencere aç** komutunu kullanın. Seçili ortamın klasöründe ayrı bir komut penceresi açmak için **PowerShell 'de aç** komutunu kullanın. Bu komut penceresinde herhangi bir python betiğini çalıştırabilirsiniz.

Daha fazla bilgi için:

- [Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Python ortamları başvurusu](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Zengin düzenleme, IntelliSense ve kod kavrama

Visual Studio söz dizimi renklendirme, otomatik tamamlama tüm kod ve kitaplıkları arasında kod biçimlendirme, imza Yardımı, yeniden düzenleme, linting ve tür ipuçlarına dahil birinci sınıf bir Python Düzenleyicisi sağlar. Visual Studio Ayrıca sınıf görünümü gibi benzersiz özellikler de sağlar, **Tanıma Git**, **tüm başvuruları bul**ve kod parçacıkları. [Etkileşimli pencereyle](#interactive-window) doğrudan tümleştirme, bir dosyaya zaten kaydedilmiş Python kodunu hızlı bir şekilde geliştirmenize yardımcı olur.

![Visual Studio'da Python kodu için kod tamamlama](media/code-editing-completions-simple.png)

Daha fazla bilgi için:

- Docs: [Python kodunu Düzenle](editing-python-code-in-visual-studio.md)
- Docs: [Biçim kodu](formatting-python-code.md)
- Docs: [kodu yeniden düzenleme](refactoring-python-code.md)
- Docs: [bir lter kullanın](linting-python-code.md)
- Genel Visual Studio özellik belgeleri: [kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Etkileşimli pencere

Bilinen Visual Studio için Python, her ortam için ayrı bir komut isteminde kullanmak yerine Visual Studio içinde doğrudan bir Python yorumlayıcısı için aynı etkileşimli (REPL) ortamı kolayca açabilirsiniz. De ortamlar arasında kolayca geçiş yapabilirsiniz. (Ayrı bir komut istemi açmak için, **Python ortamları** penceresinde istediğiniz ortamı seçin ve daha önce [birden çok Yorumlayıcıiçin destek](#support-for-multiple-interpreters)altında açıklandığı gibi **PowerShell 'de aç** komutunu seçin.)

![Visual Studio'da Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio Ayrıca Python kod Düzenleyicisi ve **etkileşimli** pencere arasında sıkı tümleştirme sağlar. **Ctrl** **+klavye** kısayolunu, düzenleyicide **etkileşimli** pencereye doğru şekilde geçerli kod satırını (veya kod bloğu) gönderir ve ardından sonraki satıra (veya bloğa) gider. **Ctrl**+**ENTER** , hata ayıklayıcıyı çalıştırmak zorunda kalmadan kodu kolayca görmenizi sağlar. Ayrıca, seçilen kodu aynı tuş vuruşu ile **etkileşimli** pencereye gönderebilir ve **etkileşimli** penceredeki kodu kolayca düzenleyiciye yapıştırabilirsiniz. Bu yetenekler birlikte, **etkileşimli** penceredeki bir kod segmenti için ayrıntıları çalışmanıza ve sonuçları düzenleyicide bir dosyaya kolayca kaydetmenizi sağlar.

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

[Visual Studio 'da Python projesi ve öğe şablonlarını ![](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Daha fazla bilgi için:

- Docs: [Python projelerini yönetme](managing-python-projects-in-visual-studio.md)
- Docs: [öğe şablonları başvurusu](python-item-templates.md)
- Docs: [Python proje şablonları](managing-python-projects-in-visual-studio.md#project-templates)
- Docs: [ve Python C++ ile çalışma](working-with-c-cpp-python-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [Proje ve öğe şablonları](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Genel Visual Studio özellik belgeleri: [Visual Studio 'Da çözümler ve projeler](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Tam özellikli hata ayıklama

Visual Studio'nun güçlü, güçlü bir hata ayıklayıcı biridir. Özellikle Python için, Visual Studio Python/C++ karışık mod hata ayıklaması, Linux 'ta uzaktan hata ayıklama, **etkileşimli** pencerede hata ayıklama ve Python birim testlerinde hata ayıklama içerir.

![Bir özel durum açılan gösteren Python için Visual Studio hata ayıklayıcı](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
Visual Studio 2019 ' de, Visual Studio proje dosyası olmadan kodu çalıştırabilir ve hata ayıklaması yapabilirsiniz. Bkz. [hızlı başlangıç: bir örnek için bir klasörde Python kodu açma ve çalıştırma](quickstart-05-python-visual-studio-open-folder.md) .
::: moniker-end

Daha fazla bilgi için:

- Docs: [Python hata ayıkla](debugging-python-in-visual-studio.md)
- Docs: [Python/C++ karışık modda hata ayıklama](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Docs: [Linux 'Ta uzaktan hata ayıklama](debugging-python-code-on-remote-linux-machines.md)
- Genel Visual Studio özellik belgeleri: [Visual Studio hata ayıklayıcısında Özellik turu](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Kapsamlı Raporlama ile profil oluşturma araçları

Profil oluşturma nasıl uygulamanızdaki zaman harcandığını keşfediyor. Visual Studio ile yorumlayıcılarını CPython tabanlı profil oluşturmayı destekler ve performans profil oluşturma farklı çalıştırma arasında karşılaştırma özelliğini içerir.

[Python projesi için Visual Studio Profiler sonuçlarını ![](media/profiling-results.png)](media/profiling-results.png#lightbox)

Daha fazla bilgi için:

- Docs: [Python profil oluşturma araçları](profiling-python-code-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [profil oluşturma özelliği turu](../profiling/profiling-feature-tour.md). (Tüm Visual Studio profil oluşturma özellikleri, Python için mevcuttur).

## <a name="unit-testing-tools"></a>Birim test araçları

Visual Studio **Test Gezgini**'nde testleri bulun, çalıştırın ve yönetin ve birim testlerinde kolayca hata ayıklayın.

![Bir test jednotky Pythonu Visual Studio'da hata ayıklama](media/unit-test-debugging.png)

Daha fazla bilgi için:

- Docs: [Python Için birim testi araçları](unit-testing-python-in-visual-studio.md)
- Genel Visual Studio özellik belgeleri: [birim testi kodunuz](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>Python için Azure SDK

Python için Azure kitaplıkları, Windows, Mac OS X ve Linux uygulamalarından Azure hizmetlerinin tüketilmesini basitleştirir. Bunları Azure kaynakları oluşturmak ve yönetmek için, ayrıca Azure hizmetlerine bağlanmak için de kullanabilirsiniz. 

Daha fazla bilgi için bkz. [Python Için Azure SDK](/azure/python/) ve [Python için Azure kitaplıkları](/azure/python/python-sdk-azure-overview) .

## <a name="questions-and-answers"></a>Sorular ve yanıtlar

**S. Mac için Visual Studio ile Python desteği sağlanıyor mu?**

A. Şu anda değil, ancak [Geliştirici topluluğundaki](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html)isteği oylayabilirsiniz. [Mac için Visual Studio](/visualstudio/mac/) belgeleri, desteklediği geliştirmenin geçerli türlerini tanımlar. Bu sırada, Windows, Mac ve Linux üzerinde Visual Studio Code, [kullanılabilir uzantılar aracılığıyla Python ile iyi şekilde](https://code.visualstudio.com/docs/languages/python)çalışacaktır.

**Soru-cevap ile Kullanıcı arabirimi oluşturmak için ne kullanabilirim?**

A. Bu alandaki ana teklif, bir Python [projesi](https://www.qt.io/qt-for-application-development/)olan ( [resmi bağlama)](https://wiki.qt.io/PySide) (aynı zamanda [Pyside İndirmeleri](https://download.qt.io/official_releases/pyside/.)) ve [PyQt](https://wiki.python.org/moin/PyQt)olarak bilinen Python için bağlamadır. Şu anda, herhangi belirli kullanıcı Arabirimi geliştirme araçları Visual Studio'da Python desteği içermez.

**Soru-cevap, bir Python projesi tek başına yürütülebilir bir dosya oluşturabilir mi?**

A. Python ile isteğe bağlı olarak Visual Studio ve web sunucuları gibi uygun bir Python özellikli ortam kod çalıştırılır, yorumlanan bir dil genellikle var. Visual Studio'nun kendisi, aslında bir programla katıştırılmış bir Python yorumlayıcısı anlamına gelir bir tek başına yürütülebilir oluşturmak için Araçlar şu anda sağlamaz. Ancak, Python topluluğu farklı şekilde sağlanmış olduğundan, [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)adresinde açıklandığı şekilde yürütülebilir dosyalar oluşturma anlamına gelir. Cpyıthon Ayrıca, [cpıthon 'un eklenebilir ZIP dosyası kullanılarak](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)blog gönderisine göre yerel bir uygulama içine katıştırılmakta da desteklenir.

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Özellik desteği

Python özellikleri, [yükleme kılavuzunda](installing-python-support-in-visual-studio.md)açıklandığı şekilde, Visual Studio 'nun aşağıdaki sürümlerine yüklenebilir:

- [Visual Studio 2019 (tüm sürümler)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (tüm sürümler)
- Visual Studio 2015 (tüm sürümler)
- Visual Studio 2013 Community Edition
- Güncelleştirme 2 veya daha yüksek olan Web için Visual Studio 2013 Express
- Güncelleştirme 2 veya üzeri Masaüstü için Visual Studio 2013 Express
- Visual Studio 2013 (Pro sürümü veya üzeri)
- Visual Studio 2012 (Pro sürümü veya üzeri)
- Visual Studio 2010 SP1 (Pro sürümü veya üstü; .NET 4.5 gerekiyor)

Visual Studio 2015 ve önceki sürümleri [VisualStudio.Microsoft.com/vs/Older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/)adresinde bulunabilir.

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
|        Git ile tümleştirme         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

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
|   Web sitesine dağıtma   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>iki</sup> |
|   Web rolü için dağıtma   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>03</sup> |       &#10007;       |
| Çalışan rolü için dağıtma  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>03</sup> |       &#10007;       |
| Azure öykünücüsünde çalıştırın  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>03</sup> |       &#10007;       |
|    Uzaktan hata ayıklama    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>inç</sup> | &#10004;<sup>240</sup> | &#10004;<sup>240</sup> |       &#10007;       |
| Sunucu Gezgini ekleme | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7@@</sup> | &#10004;<sup>7@@</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Django şablonları           |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü |       2013 web       |      2013 pro +       | 2012 pro + | 2010 SP1 Pro + |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Hata Ayıklama               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Otomatik Tamamlama             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>e</sup> | &#10004;<sup>e</sup> | &#10004;  |   &#10004;    |
| CSS ve JavaScript için otomatik tamamlama | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>e</sup> | &#10004;<sup>e</sup> | &#10007;  |   &#10007;    |

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

|     Test      |   2017 +   |   2015   | 2013 iletişim | 2013'ün Masaüstü | 2013 web | 2013 pro + | 2012 pro + | 2010 SP1 Pro + |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Test Gezgini | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Test çalıştırması    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Testte Hata Ayıkla   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. Visual Studio 2012 için git desteği, git uzantısı için Visual Studio Araçları [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit)kullanılabilir.

1. Azure Web sitesine dağıtım, [.net Için Azure SDK 2,1-Visual Studio 2010 SP1](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VS2010SP1AzurePack.2E2.2E1.appids)gerektirir. Sonraki sürümleri, Visual Studio 2010 desteklemez.

1. Azure Web rolü ve çalışan rolü için destek, [.net 2,3-VS 2012 veya üzeri Için Azure SDK](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs11AzurePack.appids) gerektirir.

1. Azure Web rolü ve çalışan rolü için destek, [.net 2,3-VS 2013 veya üzeri Için Azure SDK](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) gerektirir.

1. Django şablonu Düzenleyicisi'nde Visual Studio 2013 güncelleştirme 2'yi yükleme ile çözümlendiği bazı bilinen sorunlar vardır.

1. Windows 8 veya sonraki sürümünü gerektirir. Web için Visual Studio 2013 Express **Işleme Ekle** iletişim kutusuna sahip değil, ancak Azure Web sitesi uzaktan hata ayıklama, **Sunucu Gezgini** **hata ayıklayıcı (Python)** komutu kullanılarak hala mümkün. Uzaktan hata ayıklama, [.net 2,3-Visual Studio 2013 veya üzeri Için Azure SDK](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) gerektirir.

1. Windows 8 veya sonraki sürümünü gerektirir. **Sunucu Gezgini** **hata ayıklayıcı (Python) komutunun eklenmesi** , [.NET 2,3-VISUAL STUDIO 2013 veya üzeri için Azure SDK](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/VWDOrVs2013AzurePack.appids) gerektirir.

1. Windows 8 veya sonraki sürümünü gerektirir.
::: moniker-end
