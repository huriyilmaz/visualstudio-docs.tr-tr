---
title: Python desteğini yükleme
description: seçenekler ve yükleme konumları dahil olmak üzere Visual Studio 2017, 2015, 2013, 2012 ve 2010'da Visual Studio için Python Araçları (PTVS) yükleme.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 51c6224b0987443f73c353761588b6450a0a067e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060784"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Visual Studio'da Python desteğini Windows

Visual Studio (Visual Studio için Python Araçları veya PTVS olarak da bilinir) için Python desteğini yüklemek için, Visual Studio sürümünüzle eşleşen bölümdeki yönergeleri izleyin:

- [Visual Studio 2017 ve Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 ve önceki sürümler](#visual-studio-2013-and-earlier)

Yükleme adımlarını takip ettikten sonra Python desteğini hızlıca test etmek için Alt I tuşuna basarak **ve girerek** **Python** + **Etkileşimli** penceresini `2+2` açın. çıktısını görmüyorsanız, `4` adımlarınızı yeniden işaretleyin.

> [!Tip]
> Python iş yükü, şablonları, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için grafik kullanıcı arabirimi sağlayan yararlı Cookiecutter uzantısını içerir. Ayrıntılar için [bkz. Cookiecutter kullanma.](using-python-cookiecutter-templates.md)

> [!Note]
> Python desteği şu anda şu anda Mac için Visual Studio mac ve Linux'ta kullanılabilir ve Visual Studio Code. Soru [ve cevaplara bakın.](overview-of-python-tools-for-visual-studio.md#questions-and-answers)

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 ve Visual Studio 2017

1. En son yükleme yükleyicisini indirin ve Visual Studio çalıştırın. Zaten yüklü Visual Studio, Visual Studio Yükleyicisi seçeneğini belirleyin [(bkz.](../install/modify-visual-studio.md)Visual Studio değiştirme) ve 2. adıma gidin. 

    > [!div class="nextstepaction"]
    > [2019 Visual Studio'i Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Bu Community bireysel geliştiricilere, sınıf öğrenimine, akademik araştırmalara ve açık kaynak geliştirmeye göre tasarlanmıştır. Diğer kullanımlar için, [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) [veya Visual Studio 2019 Enterprise.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

1. Yükleyici, belirli geliştirme alanları için ilgili seçeneklerin grupları olan iş yüklerinin listesini sunar. Python için Python geliştirme **iş yükünü** seçin.

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    İsteğe bağlı: Veri bilimiyle çalışıyorsanız Veri bilimi ve analitik uygulamalar **iş yükünü de göz önünde bulundurabilirsiniz.** Bu iş yükü Python, R ve F# dilleri için destek içerir. Daha fazla bilgi için [bkz. Veri bilimi ve analitik uygulamalar iş yükü.](data-science-and-analytical-applications-workload.md)

    > [!Note]
    > Python ve Veri Bilimi iş yükleri yalnızca 2017 Visual Studio 15.2 ve sonraki sürümlerle kullanılabilir.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    İsteğe bağlı: Veri bilimiyle çalışıyorsanız Veri bilimi ve analitik uygulamalar **iş yükünü de göz önünde bulundurabilirsiniz.** Bu iş yükü Python ve F# dilleri için destek içerir. Daha fazla bilgi için [bkz. Veri bilimi ve analitik uygulamalar iş yükü.](data-science-and-analytical-applications-workload.md)
    ::: moniker-end

1. Yükleyicinin sağ tarafında, istenirse ek seçenekler belirleyin. Varsayılan seçenekleri kabul etmek için bu adımı atlayabilirsiniz.

    ::: moniker range="vs-2017"
    ![Visual Studio yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Visual Studio 2019 yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Seçenek | Açıklama |
    | --- | --- |
    | Python dağıtımları | Birlikte çalışmak istediğiniz Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32 bit ve 64 bit varyantları gibi kullanılabilir seçeneklerin herhangi bir bileşimini seçin. Her biri dağıtımın yorumlayıcı, çalışma zamanı ve kitaplıklarını içerir. Anaconda, özellikle de çok çeşitli önceden yüklenmiş paketleri içeren bir açık veri bilimi platformudur. (Dağıtımları eklemek veya kaldırmak Visual Studio yükleyiciye geri dönabilirsiniz.)  **Not:** Dağıtım yükleyicisi dışında bir dağıtım Visual Studio, burada eşdeğer seçeneği denetlemeye gerek yoktur. Visual Studio Python yüklemelerini otomatik olarak algılar. Bkz. [Python Ortamları penceresi.](managing-python-environments-in-visual-studio.md#the-python-environments-window) Ayrıca, python'ın yükleyicide gösterilenden daha yeni bir sürümü varsa, bu sürümü ayrı olarak yükleyebilirsiniz ve Visual Studio algılarsınız. |
    | **Cookiecutter şablon desteği** | Şablonları, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için Cookiecutter grafik kullanıcı arabirimini yükleme. Bkz. [Cookiecutter uzantısını kullanma.](using-python-cookiecutter-templates.md) |
    | **Python web desteği** | Bottle, Flask ve Django çerçevelerini kullanan projelere yönelik şablonların yanı sıra HTML, CSS ve JavaScript düzenleme desteği de dahil olmak üzere web geliştirme araçlarını yüklür. Bkz. [Python web projesi şablonları.](python-web-application-project-templates.md) |
    | **Python IoT desteği** | Python Windows IoT Core geliştirmeyi destekler. |
    | **Python yerel geliştirme araçları** | Python için yerel uzantılar geliştirmek için C++ derleyicisi ve diğer gerekli bileşenleri yüklenir. Bkz. [Python için C++ uzantısı oluşturma.](working-with-c-cpp-python-in-visual-studio.md) Ayrıca tam C++ **desteği için C++ ile** Masaüstü geliştirme iş yükünü yükleyin. |

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Seçenek | Açıklama |
    | --- | --- |
    | Python dağıtımları | Birlikte çalışmak istediğiniz Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32 bit ve 64 bit varyantları gibi kullanılabilir seçeneklerin herhangi bir bileşimini seçin. Her biri dağıtımın yorumlayıcı, çalışma zamanı ve kitaplıklarını içerir. Anaconda, özellikle de çok çeşitli önceden yüklenmiş paketleri içeren bir açık veri bilimi platformudur. (Dağıtımları eklemek veya kaldırmak Visual Studio yükleyiciye geri dönabilirsiniz.)  **Not:** Dağıtım yükleyicisi dışında bir dağıtım Visual Studio, burada eşdeğer seçeneği denetlemeye gerek yoktur. Visual Studio Python yüklemelerini otomatik olarak algılar. Bkz. [Python Ortamları penceresi.](managing-python-environments-in-visual-studio.md#the-python-environments-window) Ayrıca, python'ın yükleyicide gösterilenden daha yeni bir sürümü varsa, bu sürümü ayrı olarak yükleyebilirsiniz ve Visual Studio algılarsınız. |
    | **Cookiecutter şablon desteği** | Şablonları, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için Cookiecutter grafik kullanıcı arabirimini yükleme. Bkz. [Cookiecutter uzantısını kullanma.](using-python-cookiecutter-templates.md) |
    | **Python web desteği** | Bottle, Flask ve Django çerçevelerini kullanan projelere yönelik şablonların yanı sıra HTML, CSS ve JavaScript düzenleme desteği de dahil olmak üzere web geliştirme araçlarını yüklür. Bkz. [Python web projesi şablonları.](python-web-application-project-templates.md) |
    | **Python yerel geliştirme araçları** | Python için yerel uzantılar geliştirmek için C++ derleyicisi ve diğer gerekli bileşenleri yüklenir. Bkz. [Python için C++ uzantısı oluşturma.](working-with-c-cpp-python-in-visual-studio.md) Ayrıca tam C++ **desteği için C++ ile** Masaüstü geliştirme iş yükünü yükleyin. |
    ::: moniker-end

1. Yüklemeden sonra yükleyici, yükleme sırasında değişiklik, başlatma, onarma veya kaldırma Visual Studio. Değiştir **düğmesi,** yüklü **tüm bileşenler** için Visual Studio güncelleştirmeler kullanılabilir olduğunda Güncelleştir olarak değişir. (Değiştir  seçeneği daha sonra açılan menüden kullanılabilir.) Ayrıca , "Visual Studio" üzerinde arama Windows başlat **menüsünden** yükleyiciyi Visual Studio.

    ![Yükleme yüklemesini başlatma, değiştirme, değiştirme Visual Studio kaldırma](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Sorun giderme

Python'u Visual Studio yükleme veya çalıştırma sorunlarıyla karşılaşırsanız şunları deneyin:

- Aynı hatanın Python CLI kullanılarak mı oluştuğu, yani komut isteminden *python.exe* çalıştırarak mı oluştuğuna karar verir.
- Visual Studio [](../install/repair-visual-studio.md) yükleyicisinde Onar seçeneğini kullanın.
- Windows'daki Ayarlar   >  **Apps & Python'ı** onarın veya Windows.

**Örnek hata:** Etkileşimli işlem başlatılamadı: System.ComponentModel.Win32Exception (0x80004005): Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext() içinde bilinmeyen hata (0xc0000135) .

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Visual Studio **2015'i** **ve ardından Değiştir'i** Denetim Masası > Programlar ve Özellikler'i seçerek Microsoft Visual Studio yükleyicisini **çalıştırın.**

1. Yükleyicide Değiştir'i **seçin.**

1. Programlama **Dilleri'Visual Studio için Python Araçları**  >  **ve** ardından Sonraki:

    ![Visual Studio 2015 yükleyicisinde PTVS seçeneği](media/installation-vs2015.png)

1. Bu Visual Studio tamamlandıktan [sonra, tercih ettiyniz bir Python yorumlayıcı yükleyin.](installing-python-interpreters.md) Visual Studio 2015 yalnızca Python 3.5 ve önceki sürümleri destekler; sonraki sürümler Desteklenmeyen **Python sürüm 3.6 gibi bir ileti üretir.** Zaten yüklü bir yorumlayıcınız varsa ve Visual Studio otomatik olarak algılamazsa bkz. [Mevcut bir ortamı el ile tanımlama.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 ve önceki sürümler

1. Visual Studio sürümünüz için uygun Visual Studio için Python Araçları sürümünü Visual Studio:

    - Visual Studio 2013: Visual Studio 2013 için [PTVS 2.2.2.](https://github.com/Microsoft/PTVS/releases/v2.2.2) Yeni **Dosya**  >  **Project** iletişim Visual Studio 2013 bu işlem için bir kısayol sağlar.
    - Visual Studio 2010 ve 2012: [Visual Studio 2010 ve 2012 için PTVS 2.1.1](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Tercihen bir Python yorumlayıcı yükleyin.](installing-python-interpreters.md) Zaten yüklü bir yorumlayıcınız varsa ve Visual Studio otomatik olarak algılamazsa bkz. [Mevcut bir ortamı el ile tanımlama.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

## <a name="install-locations"></a>Konum yüklemeleri

Varsayılan olarak, Python desteği bir bilgisayardaki tüm kullanıcılar için yüklenir.

Visual Studio 2019 ve Visual Studio 2017 için Python iş yükü *% ProgramFiles (x86)% \ Microsoft Visual Studio \\<VS_version>\\*<VS_edition>2017 2019 Common7\IDE\Extensions\Microsoft\Python ve VS_version VS_edition &lt; &gt; &lt; &gt; , Community veya Professional.

Visual Studio 2015 ve önceki sürümlerde, yükleme yolları aşağıdaki gibidir:

- 32 bit:
  - yol: *% Program Files (x86)% \ Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\ Visual Studio için Python Araçları \\<PTVS_ver>*
  - Yolun kayıt konumu: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver> \ınstalldir**
- 64 bit:
  - yol: *% Program Files% \ Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\ Visual Studio için Python Araçları \\<PTVS_ver>*
  - Yolun kayıt konumu: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver> \ınstalldir**

burada:

- &lt;VS_ver &gt; :
  - Visual Studio 2015 için 14,0
  - Visual Studio 2013 için 12,0
  - Visual Studio 2012 için 11,0
  - Visual Studio 2010 için 10,0
- &lt;PTVS_ver, &gt; 2.2.2, 2.1.1, 2,0, 1,5, 1,1 veya 1,0 gibi bir sürüm numarasıdır.

### <a name="user-specific-installations-15-and-earlier"></a>Kullanıcıya özgü yüklemeler (1,5 ve önceki sürümler)

yalnızca geçerli kullanıcı için Visual Studio için Python Araçları 1,5 ve önceki sürümlere izin verilir; bu durumda yükleme yolu *%localappdata%\microsoft\visualstudio \\<VS_ver> \extensions\microsoft\ Visual Studio için Python Araçları \\<PTVS_ver>VS_ver* &lt; &gt; ve &lt; PTVS_ver &gt; yukarıda açıklanan şekilde aynıdır.
