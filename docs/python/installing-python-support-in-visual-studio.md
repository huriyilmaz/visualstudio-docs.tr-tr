---
title: Python desteğini yükler
description: seçenekler ve yükleme konumları dahil Visual Studio 2017, 2015, 2013, 2012 ve 2010 Visual Studio için Python Araçları (ptv) yükleme.
ms.date: 03/13/2019
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: fd132d88541ecb4500c373d7714c9f9604ee0197
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968676"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Windows üzerinde Visual Studio Python desteği nasıl yüklenir

Visual Studio (Visual Studio için Python Araçları veya ptv olarak da bilinir) için Python desteğini yüklemek için, Visual Studio sürümünüzle eşleşen bölümdeki yönergeleri izleyin:

- [Visual Studio 2017 ve Visual Studio 2019](#visual-studio-2017-and-2019)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 ve önceki sürümler](#visual-studio-2013-and-earlier)

Yükleme adımlarını tamamladıktan sonra Python desteğini hızlıca test etmek için, **alt** i ve girerek **Python etkileşimli** penceresini açın +  `2+2` . Çıktısını görmüyorsanız `4` , adımlarınızı yeniden denetleyin.

> [!Tip]
> Python iş yükü; şablonları, giriş şablonu seçeneklerini bulmaya ve proje ve dosya oluşturmaya yönelik grafik kullanıcı arabirimi sağlayan yararlı Cookiecutter uzantısını içerir. Ayrıntılar için bkz. [Cookiecutter kullanma](using-python-cookiecutter-templates.md).

> [!Note]
> Python desteği şu anda Mac için Visual Studio, ancak Mac ve Linux 'ta Visual Studio Code üzerinden kullanılabilir. [Sorular ve yanıtlar](overview-of-python-tools-for-visual-studio.md#questions-and-answers)bölümüne bakın.

<a name="visual-studio-2017-and-2019"></a>
## <a name="visual-studio-2019-and-visual-studio-2017"></a>Visual Studio 2019 ve Visual Studio 2017

1. en son Visual Studio yükleyiciyi indirin ve çalıştırın. Visual Studio zaten yüklüyse, Visual Studio Yükleyicisi çalıştırın, **değiştir** seçeneğini belirleyin (bkz. [Visual Studio değiştirme](../install/modify-visual-studio.md)) ve adım 2 ' ye gidin.

    > [!div class="nextstepaction"]
    > [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Community sürümü bireysel geliştiriciler, ders öğrenimi, akademik araştırmalar ve açık kaynak geliştirme içindir. diğer kullanımlar için [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) veya [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)' yi yükler.

1. Yükleyici, belirli bir geliştirme alanı için ilgili seçeneklerin grupları olan iş yüklerinin bir listesini sunar. Python için **Python geliştirme** iş yükünü seçin.

    ![Visual Studio yükleyicisinde Python geliştirme iş yükü](media/installation-python-workload.png)

    ::: moniker range="vs-2017"
    İsteğe bağlı: veri bilimi ile çalışıyorsanız, **veri bilimi ve analitik uygulamalar** iş yükünü de göz önünde bulundurun. Bu iş yükü Python, R ve F # dilleri için destek içerir. Daha fazla bilgi için bkz. [veri bilimi ve analitik uygulamalar iş yükü](data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Python ve veri bilimi iş yükleri yalnızca Visual Studio 2017 sürüm 15,2 ve üzeri sürümlerle kullanılabilir.

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    İsteğe bağlı: veri bilimi ile çalışıyorsanız, **veri bilimi ve analitik uygulamalar** iş yükünü de göz önünde bulundurun. Bu iş yükü Python ve F # dilleri için destek içerir. Daha fazla bilgi için bkz. [veri bilimi ve analitik uygulamalar iş yükü](data-science-and-analytical-applications-workload.md).
    ::: moniker-end

1. Yükleyicinin sağ tarafında, istenirse ek seçenekler ' i seçin. Varsayılan seçenekleri kabul etmek için bu adımı atlayın.

    ::: moniker range="vs-2017"
    ![Visual Studio yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    ![Visual Studio 2019 yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options-2019.png)
    ::: moniker-end

    ::: moniker range="<=vs-2017"
    | Seçenek | Açıklama |
    | --- | --- |
    | Python dağıtımları | Birlikte çalışmayı planladığınız Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32-bit ve 64-bit çeşitleri gibi kullanılabilir seçeneklerin herhangi bir birleşimini seçin. Her biri dağıtımın yorumlayıcı, çalışma zamanı ve kitaplıklarını içerir. Anaconda, özellikle de önceden yüklenmiş çok sayıda paketi içeren açık bir veri bilimi platformudur. (dağıtım eklemek veya kaldırmak için dilediğiniz zaman Visual Studio yükleyiciye dönebilirsiniz.)  **Note**: Visual Studio yükleyicisinin dışında bir dağıtım yüklediyseniz, eşdeğer seçeneği burada denetlemeniz gerekmez. Visual Studio, var olan Python yüklemelerini otomatik olarak algılar. Bkz. [Python ortamları penceresi](managing-python-environments-in-visual-studio.md#the-python-environments-window). ayrıca, Python 'un daha yeni bir sürümü yükleyicide gösterilenden daha fazla kullanılabilir ise, bu sürümü ayrı olarak yükleyebilir ve Visual Studio algılayacaktır. |
    | **Cookiecutter şablonu desteği** | Şablonları, giriş şablonu seçeneklerini bulmaya ve proje ve dosya oluşturmaya yönelik Cookiecutter grafik kullanıcı arabirimini yükleyerek. Bkz. [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md). |
    | **Python web desteği** | HTML, CSS ve JavaScript Düzenle desteği dahil web geliştirme araçları 'nı, şişe, Flask ve Docgo çerçevelerini kullanan projelere yönelik şablonlarla birlikte kurar. Bkz. [Python web projesi şablonları](python-web-application-project-templates.md). |
    | **Python IoT desteği** | Python kullanarak ıot Core geliştirmesini Windows destekler. |
    | **Python yerel geliştirme araçları** | Python için yerel uzantılar geliştirmek üzere C++ derleyicisini ve diğer gerekli bileşenleri yükleyerek. Bkz. [Python Için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md). Ayrıca, tam C++ desteği için C++ iş yüküne **sahip masaüstü geliştirmeyi** de yükler. |

    ::: moniker-end

    ::: moniker range=">=vs-2019"
    | Seçenek | Açıklama |
    | --- | --- |
    | Python dağıtımları | Birlikte çalışmayı planladığınız Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32-bit ve 64-bit çeşitleri gibi kullanılabilir seçeneklerin herhangi bir birleşimini seçin. Her biri dağıtımın yorumlayıcı, çalışma zamanı ve kitaplıklarını içerir. Anaconda, özellikle de önceden yüklenmiş çok sayıda paketi içeren açık bir veri bilimi platformudur. (dağıtım eklemek veya kaldırmak için dilediğiniz zaman Visual Studio yükleyiciye dönebilirsiniz.)  **Note**: Visual Studio yükleyicisinin dışında bir dağıtım yüklediyseniz, eşdeğer seçeneği burada denetlemeniz gerekmez. Visual Studio, var olan Python yüklemelerini otomatik olarak algılar. Bkz. [Python ortamları penceresi](managing-python-environments-in-visual-studio.md#the-python-environments-window). ayrıca, Python 'un daha yeni bir sürümü yükleyicide gösterilenden daha fazla kullanılabilir ise, bu sürümü ayrı olarak yükleyebilir ve Visual Studio algılayacaktır. |
    | **Cookiecutter şablonu desteği** | Şablonları, giriş şablonu seçeneklerini bulmaya ve proje ve dosya oluşturmaya yönelik Cookiecutter grafik kullanıcı arabirimini yükleyerek. Bkz. [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md). |
    | **Python web desteği** | HTML, CSS ve JavaScript Düzenle desteği dahil web geliştirme araçları 'nı, şişe, Flask ve Docgo çerçevelerini kullanan projelere yönelik şablonlarla birlikte kurar. Bkz. [Python web projesi şablonları](python-web-application-project-templates.md). |
    | **Python yerel geliştirme araçları** | Python için yerel uzantılar geliştirmek üzere C++ derleyicisini ve diğer gerekli bileşenleri yükleyerek. Bkz. [Python Için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md). Ayrıca, tam C++ desteği için C++ iş yüküne **sahip masaüstü geliştirmeyi** de yükler. |
    ::: moniker-end

1. Yükleme sonrasında, yükleyici Visual Studio değiştirme, başlatma, onarma veya kaldırma seçeneklerini sağlar. Visual Studio güncelleştirmeler yüklü bileşenler için kullanılabilir olduğunda **değiştir** düğmesi **güncelleştir** olarak değişir. ( **Değiştir** seçeneği daha sonra açılan menüden kullanılabilir.) ayrıca, Windows **başlat** menüsünden "Visual Studio" arayarak Visual Studio ve yükleyiciyi de başlatabilirsiniz.

    ![yükleyiciden Visual Studio başlatma, değiştirme, değiştirme veya kaldırma](media/installation-vs-launch.png)

### <a name="troubleshooting"></a>Sorun giderme

Visual Studio 'de Python yükleme veya çalıştırma sorunlarıyla karşılaşırsanız şunları deneyin:

- Aynı hatanın, Python CLı kullanarak oluşup oluşmadığını belirleme, diğer bir deyişle, bir komut isteminden *python.exe* çalıştırma.
- Visual Studio yükleyicisinde [**onar**](../install/repair-visual-studio.md) seçeneğini kullanın.
- Windows & **Ayarlar**  >  **uygulamalar** aracılığıyla Python 'u onarın veya yeniden yükleyin.

**Örnek hata**: etkileşimli işlem başlatılamadı: System. ComponentModel. Win32Exception (0x80004005): Microsoft.PythonTools.REPL.PythonInteractiveEvaluator.d__43. MoveNext () konumunda bilinmeyen hata (0xc0000135).

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Visual Studio yükleyicisini **denetim masası > programlar ve özellikler**' i seçerek çalıştırın **Microsoft Visual Studio 2015** ' i seçin ve ardından **değiştirin**.

1. Yükleyicide **Değiştir**' i seçin.

1. **programlama dillerini**  >  **Visual Studio için Python Araçları** ve ardından **ileri**' yi seçin:

    ![Visual Studio 2015 yükleyicisinde ptv seçeneği](media/installation-vs2015.png)

1. Visual Studio kurulum tamamlandıktan sonra, [tercih ettiğiniz bir Python yorumlayıcı kurun](installing-python-interpreters.md). Visual Studio 2015 yalnızca Python 3,5 ve öncesini destekler; sonraki sürümler **Desteklenmeyen Python sürüm 3,6**) gibi bir ileti oluşturur. zaten bir yorumlayıcı yüklüyse ve Visual Studio otomatik olarak algılamazsa, bkz. [var olan bir ortamı el ile](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)saptama.

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 ve önceki sürümler

1. Visual Studio sürümünüze uygun Visual Studio için Python Araçları sürümünü yükler:

    - Visual Studio 2013: [Visual Studio 2013 için ptv 2.2.2](https://github.com/Microsoft/PTVS/releases/v2.2.2). Visual Studio 2013 **dosya**  >  **yeni Project** iletişim kutusu size bu işlem için bir kısayol sağlar.
    - Visual Studio 2010 ve 2012: [Visual Studio 2010 ve 2012 için ptelevizyon2.1.1](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Seçtiğiniz bir Python yorumlayıcı yükler](installing-python-interpreters.md). zaten bir yorumlayıcı yüklüyse ve Visual Studio otomatik olarak algılamazsa, bkz. [var olan bir ortamı el ile](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)saptama.

## <a name="install-locations"></a>Yükleme konumları

Varsayılan olarak, bir bilgisayarda tüm kullanıcılar için Python desteği yüklenir.

Visual Studio 2019 ve Visual Studio 2017 için Python iş yükü *%ProgramFiles(x86)%\Microsoft Visual Studio<VS_version><VS_edition>\\ \\ Common7\IDE\Extensions\Microsoft\Python'a* yüklenir; burada &lt; VS_version &gt; 2019 veya 2017 ve &lt; VS_edition &gt; Community, Professional veya Enterprise.

2015 Visual Studio önceki sürümler için yükleme yolları aşağıdaki gibidir:

- 32 bit:
  - Yol: *%Program Files(x86)%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Visual Studio için Python Araçları \\<PTVS_ver>*
  - Yolun kayıt defteri konumu: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64 bit:
  - Yol: *%Program Files%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Visual Studio için Python Araçları \\<PTVS_ver>*
  - Yolun kayıt defteri konumu: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

burada:

- &lt;&gt;VS_ver:
  - Visual Studio 2015 için 14.0
  - Visual Studio 2013 için 12.0
  - Visual Studio 2012 için 11.0
  - Visual Studio 2010 için 10.0
- &lt;PTVS_ver &gt; 2.2.2, 2.1.1, 2.0, 1.5, 1.1 veya 1.0 gibi bir sürüm numarasıdır.

### <a name="user-specific-installations-15-and-earlier"></a>Kullanıcıya özgü yüklemeler (1.5 ve önceki sürümler)

Visual Studio için Python Araçları yalnızca geçerli kullanıcı için 1.5 ve önceki bir sürümün yüklenmesine izin verildi; bu durumda yükleme yolu *%LocalAppData%\Microsoft\VisualStudio \\<VS_ver>\Extensions\Microsoft\Visual Studio için Python Araçları \\<PTVS_ver>'dir* VS_ver &lt; ve &gt; &lt; PTVS_ver &gt;, yukarıda açıklananla aynıdır.
