---
title: Python desteğini yükler
description: seçenekler ve yükleme konumları dahil Visual Studio 2017, 2015, 2013, 2012 ve 2010 Visual Studio için Python Araçları (ptv) yükleme.
ms.date: 12/11/2021
ms.custom: devdivchpfy22
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: c3d53db62b1ba48013a7b0f03c8d0369c7e7feeb
ms.sourcegitcommit: 04fb8ba0f7ea73ba17baa88f10563c8600e7fd7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "135121788"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Windows üzerinde Visual Studio Python desteği nasıl yüklenir

Visual Studio (Visual Studio için Python Araçları veya ptv olarak da bilinir) için Python desteğini yüklemek için, Visual Studio sürümünüzle eşleşen bölümdeki yönergeleri izleyin:
:::moniker range=">=vs-2022"

-[Visual Studio 2022](#visual-studio-2022)
:::moniker-end
:::moniker range="vs-2019"

- [Visual Studio 2019](#visual-studio-2019)
:::moniker-end
:::moniker range="<=vs-2017"

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 ve önceki sürümler](#visual-studio-2013-and-earlier)
:::moniker-end

Yükleme adımlarını tamamladıktan sonra Python desteğini hızlıca test etmek için, **alt** i ve girerek **Python etkileşimli** penceresini açın +  `2+2` . Çıktısını görmüyorsanız `4` , adımlarınızı yeniden denetleyin.

> [!Tip]
> Python iş yükü; şablonları, giriş şablonu seçeneklerini bulmaya ve proje ve dosya oluşturmaya yönelik grafik kullanıcı arabirimi sağlayan yararlı Cookiecutter uzantısını içerir. Ayrıntılar için bkz. [Cookiecutter kullanma](using-python-cookiecutter-templates.md).

> [!Note]
> Python desteği şu anda Mac için Visual Studio değildir, ancak Visual Studio Code aracılığıyla Mac ve Linux 'ta kullanılabilir. [Sorular ve yanıtlar](overview-of-python-tools-for-visual-studio.md#questions-and-answers)bölümüne bakın.

:::moniker range=">=vs-2022"

## <a name="visual-studio-2022"></a>Visual Studio 2022

:::moniker-end
:::Moniker range="vs-2019"

## <a name="visual-studio-2019"></a>Visual Studio 2019

:::moniker-end
:::moniker range="vs-2017"

## <a name="visual-studio-2017"></a>Visual Studio 2017

:::moniker-end

1. en son Visual Studio yükleyiciyi indirin ve çalıştırın. Visual Studio zaten yüklüyse, Visual Studio Yükleyicisi çalıştırın, **değiştir** seçeneğini belirleyin (bkz. [Visual Studio değiştirme](../install/modify-visual-studio.md)) ve adım 2 ' ye gidin.

    :::moniker range=">=vs-2022"
  
   >[!div class="nextstepaction"]
   > [Visual Studio 2022 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=17)

    >[!Tip]
    > Community sürümü bireysel geliştiriciler, ders öğrenimi, akademik araştırmalar ve açık kaynak geliştirme içindir. diğer kullanıcılar için [Visual Studio 2022 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=17) veya [Visual Studio 2022 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=17)

    :::moniker-end
    :::moniker range="vs-2019"

   >[!div class="nextstepaction"]
   > [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Community sürümü bireysel geliştiriciler, ders öğrenimi, akademik araştırmalar ve açık kaynak geliştirme içindir. diğer kullanımlar için [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) veya [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)' yi yükler.

    :::moniker-end
    :::moniker range="vs-2017"

   >[!div class="nextstepaction"]
   > [Visual Studio 2017 community 'yi yükler](https://my.visualstudio.com/Downloads?q=Visual-Studio-2017)
    :::moniker-end

1. Visual Studio yükleyici, belirli geliştirme alanlarında ilgili seçenek grupları olan iş yüklerinin bir listesini sağlar. Python için **Python geliştirme** iş yükünü seçin.

   İsteğe bağlı: veri bilimi ile çalışıyorsanız, **veri bilimi ve analitik uygulamalar** iş yükünü de göz önünde bulundurun. Bu iş yükü Python, R ve F # dilleri için destek içerir. Daha fazla bilgi için bkz. [veri bilimi ve analitik uygulamalar iş yükü](data-science-and-analytical-applications-workload.md).

   ![Visual Studio yükleyicisinde Python geliştirme iş yükü](media/installation-python-workload.png).

1. Yükleyicinin sağ tarafında isterseniz diğer seçenekler ' i seçin. Varsayılan seçenekleri kabul etmek için bu adımı atlayın.
   :::moniker range=">=vs-2022"

   ![Visual Studio 2022 yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options-2022.png)

   :::moniker-end

   :::moniker range="vs-2019"

   ![Visual Studio 2019 yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options-2019.png)

   :::moniker-end

   :::moniker range="vs-2017"

   ![Visual Studio 2017 yükleyicisinde Python geliştirme seçenekleri](media/installation-python-options.png)

   :::moniker-end

 | Seçenek | Açıklama |
   | --- | --- |
| Python dağıtımları | Birlikte çalışmayı planladığınız Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32-bit ve 64-bit çeşitleri gibi kullanılabilir seçeneklerin herhangi bir birleşimini seçin. Her biri dağıtımın yorumlayıcı, çalışma zamanı ve kitaplıklarını içerir. Anaconda, özellikle de önceden yüklenmiş çok sayıda paketi içeren açık bir veri bilimi platformudur. (dağıtım eklemek veya kaldırmak için dilediğiniz zaman Visual Studio yükleyiciye dönebilirsiniz.) **Note**: Visual Studio yükleyicisinin dışında bir dağıtım yüklediyseniz, eşdeğer seçeneği burada denetlemeniz gerekmez. Visual Studio, var olan Python yüklemelerini otomatik olarak algılar. Bkz. [Python ortamları penceresi](managing-python-environments-in-visual-studio.md#the-python-environments-window). ayrıca, Python 'un daha yeni bir sürümü yükleyicide gösterilenden daha fazla kullanılabilir ise, bu sürümü ayrı olarak yükleyebilir ve Visual Studio algılayacaktır. |
| **Cookiecutter şablonu desteği** | Şablonları, giriş şablonu seçeneklerini bulmaya ve proje ve dosya oluşturmaya yönelik Cookiecutter grafik kullanıcı arabirimini yükleyerek. Bkz. [Cookiecutter uzantısını kullanma](using-python-cookiecutter-templates.md). |
| **Python web desteği** | HTML, CSS ve JavaScript Düzenle desteği dahil web geliştirme araçları 'nı, şişe, Flask ve Docgo çerçevelerini kullanan projelere yönelik şablonlarla birlikte kurar. Bkz. [Python web projesi şablonları](python-web-application-project-templates.md). |
| **Python yerel geliştirme araçları** | Python için yerel uzantılar geliştirmek üzere C++ derleyicisini ve diğer gerekli bileşenleri yükleyerek. Bkz. [Python Için C++ uzantısı oluşturma](working-with-c-cpp-python-in-visual-studio.md). Ayrıca, tam C++ desteği için C++ iş yüküne **sahip masaüstü geliştirmeyi** de yükler. |

Yükleme sonrasında, yükleyici Visual Studio değiştirme, başlatma, onarma veya kaldırma seçeneklerini sağlar. Visual Studio güncelleştirmeler yüklü bileşenler için kullanılabilir olduğunda **değiştir** düğmesi **güncelleştir** olarak değişir. ( **Değiştir** seçeneği daha sonra açılan menüden kullanılabilir.) ayrıca, Windows **başlat** menüsünden "Visual Studio" arayarak Visual Studio ve yükleyiciyi de başlatabilirsiniz.

:::moniker range=">=vs-2022"

   ![yükleyiciden Visual Studio başlatma, değiştirme, değiştirme veya kaldırma-2022](media/installation-vs-launch-2022.png)

:::moniker-end
:::moniker range="vs-2019"

   ![yükleyiciden Visual Studio başlatma, değiştirme, değiştirme veya kaldırma-2019](media/installation-vs-launch.png)

:::moniker-end
:::moniker range="vs-2017"
  > [!Note]
> Python ve veri bilimi iş yükleri yalnızca Visual Studio 2017 sürüm 15,2 ve üzeri sürümlerle kullanılabilir.
:::moniker-end

### <a name="troubleshooting"></a>Sorun giderme

Visual Studio Python 'u yüklerken veya çalıştırırken sorunları onarmak için aşağıdaki adımları deneyin:

- Aynı hatanın, Python CLı kullanarak oluşup oluşmadığını belirleme, diğer bir deyişle, bir komut isteminden *python.exe* çalıştırma.
- Visual Studio yükleyicisinde [**onar**](../install/repair-visual-studio.md) seçeneğini kullanın.
- Windows & **Ayarlar**  >  **uygulamalar** aracılığıyla Python 'u onarın veya yeniden yükleyin.

**Örnek hata**: etkileşimli işlem başlatılamadı: System. ComponentModel. Win32Exception (0x80004005): Microsoft.PythonTools.REPL.PythonInteractiveEvaluator.d__43. MoveNext () konumunda bilinmeyen hata (0xc0000135).

:::moniker range="<=vs-2017"

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Visual Studio yükleyicisini **denetim masası > programlar ve özellikler**' i seçerek çalıştırın **Microsoft Visual Studio 2015** ' i seçin ve ardından **değiştirin**.

1. Yükleyicide **Değiştir**' i seçin.

1. **programlama dillerini** > **Visual Studio için Python Araçları** ve ardından **ileri**' yi seçin:

   ![Visual Studio 2015 yükleyicisinde ptv seçeneği](media/installation-vs2015.png)

1. Visual Studio kurulum tamamlandıktan sonra, [tercih ettiğiniz bir Python yorumlayıcı kurun](installing-python-interpreters.md). Visual Studio 2015 yalnızca Python 3,5 ve öncesini destekler; sonraki sürümler **desteklenmeyen python sürümü 3,6** gibi bir ileti oluşturur. zaten bir yorumlayıcı yüklüyse ve Visual Studio otomatik olarak algılamazsa, bkz. [var olan bir ortamı el ile](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)saptama.

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 ve önceki sürümler

1. Visual Studio sürümünüze uygun Visual Studio için Python Araçları sürümünü yükler:

    - Visual Studio 2013: [Visual Studio 2013 için ptv 2.2.2](https://github.com/Microsoft/PTVS/releases/v2.2.2). Visual Studio 2013 **dosya**  >  **yeni Project** iletişim kutusu size bu işlem için bir kısayol sağlar.
    - Visual Studio 2010 ve 2012: [Visual Studio 2010 ve 2012 için ptelevizyon2.1.1](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Seçtiğiniz bir Python yorumlayıcı yükler](installing-python-interpreters.md).
zaten bir yorumlayıcı yüklüyse ve Visual Studio otomatik olarak algılamazsa, bkz. [var olan bir ortamı el ile](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)saptama.

:::moniker-end

## <a name="install-locations"></a>Konum yüklemeleri

:::moniker range=">=vs-2022"

Varsayılan olarak, Python desteği bir bilgisayardaki tüm kullanıcılar için yüklenir.

Visual Studio 2022 için Python iş yükü *% ProgramFiles% \ Microsoft Visual Studio \\<VS_version>\\*<VS_edition>2022 Common7\IDE\Extensions\Microsoft\Python ve VS_version VS_edition &lt; , &gt; &lt; &gt; Community veya Enterprise.

:::moniker-end
:::moniker range="<=vs-2019"

Varsayılan olarak, Python desteği bir bilgisayardaki tüm kullanıcılar için yüklenir.

Visual Studio 2019 ve Visual Studio 2017 için Python iş yükü *% ProgramFiles (x86)% \ Microsoft Visual Studio \\<VS_version>\\*<VS_edition>&lt; &gt; 2017 2019 Common7\IDE\Extensions\Microsoft\Python ve VS_version &lt; &gt; Community, Professional veya Enterprise.

:::moniker-end

:::moniker range="<=vs-2017"

Visual Studio 2015 ve önceki sürümlerde, yükleme yolları aşağıdaki gibidir:

- 32 bit:
  - yol: *% Program Files (x86)% \ Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\ Visual Studio için Python Araçları \\<PTVS_ver>*
  - Yolun kayıt konumu: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver> \ınstalldir**
- 64 bit:
  - yol: *% Program Files% \ Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\ Visual Studio için Python Araçları \\<PTVS_ver>*
  - Yolun kayıt konumu: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver> \ınstalldir**

Konum:

- &lt;VS_ver &gt; :
  - Visual Studio 2015 için 14,0
  - Visual Studio 2013 için 12.0
  - Visual Studio 2012 için 11.0
  - Visual Studio 2010 için 10.0
- &lt;PTVS_ver &gt; 2.2.2, 2.1.1, 2.0, 1.5, 1.1 veya 1.0 gibi bir sürüm numarasıdır.

### <a name="user-specific-installations-15-and-earlier"></a>Kullanıcıya özgü yüklemeler (1.5 ve önceki sürümler)

Visual Studio için Python Araçları kullanıcı için izin verilen 1.5 ve daha önceki bir sürüm yüklemesi var; bu durumda yükleme yolu *%LocalAppData%\Microsoft\VisualStudio \\<VS_ver>\Extensions\Microsoft\Visual Studio için Python Araçları \\<PTVS_ver>* yoludur VS_ver &lt; &gt; &lt; ve PTVS_ver &gt; yukarıdakiyle aynıdır.

:::moniker-end
