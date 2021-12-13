---
title: Python desteğini yükleme
description: seçenekler ve yükleme konumları dahil olmak üzere Visual Studio 2017, 2015, 2013, 2012 ve 2010'da Visual Studio için Python Araçları (PTVS) yükleme.
ms.date: 03/13/2019
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: d8bced39dc9b2aea7678505bd597fd9e1aa6db39
ms.sourcegitcommit: 0f2af2f1a8cf0a481fd8f673accf3aebf2e262c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "134714404"
---
# <a name="how-to-install-python-support-in-visual-studio-on-windows"></a>Visual Studio'da Python desteğini Windows

Visual Studio (Visual Studio için Python Araçları veya PTVS olarak da bilinir) için Python desteğini yüklemek için, Visual Studio sürümünüzle eşleşen bölümdeki yönergeleri izleyin:
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

Yükleme adımlarını takip ettikten sonra Python desteğini hızlıca test etmek için Alt I tuşuna basarak **ve girerek** **Python** + **Etkileşimli** penceresini `2+2` açın. çıktısını görmüyorsanız, `4` adımlarınızı yeniden işaretleyin.

> [!Tip]
> Python iş yükü, şablonları, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için grafik kullanıcı arabirimi sağlayan yararlı Cookiecutter uzantısını içerir. Ayrıntılar için [bkz. Cookiecutter kullanma.](using-python-cookiecutter-templates.md)

> [!Note]
> Python desteği şu anda Mac için Visual Studio' Visual Studio Code. Soru [ve cevaplara bakın.](overview-of-python-tools-for-visual-studio.md#questions-and-answers)

:::moniker range=">=vs-2022"

## <a name="visual-studio-2022"></a>Visual Studio 2022

:::moniker-end
:::Moniker range="vs-2019"

## <a name="visual-studio-2019"></a>Visual Studio 2019

:::moniker-end
:::moniker range="vs-2017"

## <a name="visual-studio-2017"></a>Visual Studio 2017

:::moniker-end

1. En son yükleme yükleyicisini indirip Visual Studio çalıştırın. Zaten yüklü Visual Studio, Visual Studio Yükleyicisi seçeneğini belirleyin (bkz. Visual Studio [değiştirme)](../install/modify-visual-studio.md)ve 2. adıma gidin. 

    :::moniker range=">=vs-2022"
  
   >[!div class="nextstepaction"]
   > [2022 Visual Studio'i Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=17)

    >[!Tip]
    > Bu Community bireysel geliştiricilere, sınıf öğrenimine, akademik araştırmalara ve açık kaynak geliştirmeye özeldir. Diğer kullanıcılar için [2022 Visual Studio 2022 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=17) [veya Visual Studio 2022 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=17)

    :::moniker-end
    :::moniker range="vs-2019"

   >[!div class="nextstepaction"]
   > [2019 Visual Studio'i Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    >[!Tip]
    > Bu Community bireysel geliştiricilere, sınıf öğrenimine, akademik araştırmalara ve açık kaynak geliştirmeye özeldir. Diğer kullanımlar için, [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted) [veya Visual Studio 2019 Enterprise.](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_gettingstarted)

    :::moniker-end
    :::moniker range="vs-2017"

   >[!div class="nextstepaction"]
   > [2017 Visual Studio topluluğu yükleme](https://my.visualstudio.com/Downloads?q=Visual-Studio-2017)
    :::moniker-end

1. Visual Studio yükleyicisi, belirli geliştirme alanları için ilgili seçenek grupları olan iş yüklerinin bir listesini sağlar. Python için Python geliştirme **iş yükünü** seçin.

   İsteğe bağlı: Veri bilimiyle çalışıyorsanız Veri bilimi ve analitik uygulamalar **iş yükünü de göz önünde bulundurabilirsiniz.** Bu iş yükü Python, R ve F# dilleri için destek içerir. Daha fazla bilgi için [bkz. Veri bilimi ve analitik uygulamalar iş yükü.](data-science-and-analytical-applications-workload.md)

   ![Visual Studio yükleyicisinde Python geliştirme iş ](media/installation-python-workload.png) yükü.
    

1. Yükleyicinin sağ tarafında, 80000000000000000000000000000000000000000 Varsayılan seçenekleri kabul etmek için bu adımı atlayabilirsiniz.
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
| Python dağıtımları | Birlikte çalışmak istediğiniz Python 2, Python 3, Miniconda, Anaconda2 ve Anaconda3 dağıtımlarının 32 bit ve 64 bit varyantları gibi kullanılabilir seçeneklerin herhangi bir bileşimini seçin. Her biri dağıtımın yorumlayıcı, çalışma zamanı ve kitaplıklarını içerir. Anaconda, özellikle de çok çeşitli önceden yüklenmiş paketleri içeren bir açık veri bilimi platformudur. (Dağıtımları eklemek veya kaldırmak Visual Studio yükleyiciye geri dönabilirsiniz.) **Not:** Dağıtım yükleyicisi dışında bir dağıtım Visual Studio, burada eşdeğer seçeneği denetlemeye gerek yoktur. Visual Studio Python yüklemelerini otomatik olarak algılar. Bkz. [Python Ortamları penceresi.](managing-python-environments-in-visual-studio.md#the-python-environments-window) Ayrıca, python'ın yükleyicide gösterilenden daha yeni bir sürümü varsa, bu sürümü ayrı olarak yükleyebilirsiniz ve Visual Studio algılarsınız. |
| **Cookiecutter şablon desteği** | Şablonları, giriş şablonu seçeneklerini bulmak ve proje ve dosya oluşturmak için Cookiecutter grafik kullanıcı arabirimini yükleme. Bkz. [Cookiecutter uzantısını kullanma.](using-python-cookiecutter-templates.md) |
| **Python web desteği** | Bottle, Flask ve Django çerçevelerini kullanan projelere yönelik şablonların yanı sıra HTML, CSS ve JavaScript düzenleme desteği de dahil olmak üzere web geliştirme araçlarını yüklür. Bkz. [Python web projesi şablonları.](python-web-application-project-templates.md) |
| **Python yerel geliştirme araçları** | Python için yerel uzantılar geliştirmek için C++ derleyicisi ve diğer gerekli bileşenleri yüklenir. Bkz. [Python için C++ uzantısı oluşturma.](working-with-c-cpp-python-in-visual-studio.md) Ayrıca tam C++ **desteği için C++ ile** Masaüstü geliştirme iş yükünü yükleyin. |

Yüklemeden sonra yükleyici, yükleme sırasında değişiklik, başlatma, onarma veya kaldırma Visual Studio. Değiştir **düğmesi,** herhangi **bir yüklü** bileşen için Visual Studio güncelleştirmeler kullanılabilir olduğunda Güncelleştir olarak değişir. (Değiştir  seçeneği daha sonra açılan menüden kullanılabilir.) Ayrıca , "Visual Studio" üzerinde arama Windows başlat **menüsünden** yükleyiciyi Visual Studio.

:::moniker range=">=vs-2022"

   ![Yükleyici-2022'den Visual Studio başlatma, değiştirme, değiştirme veya kaldırma](media/installation-vs-launch-2022.png)

:::moniker-end
:::moniker range="vs-2019"

   ![Yükleyici-2019'dan Visual Studio başlatma, değiştirme, değiştirme veya kaldırma](media/installation-vs-launch.png)

:::moniker-end
:::moniker range="vs-2017"
  > [!Note]
> Python ve Veri Bilimi iş yükleri yalnızca 2017 Visual Studio 15.2 ve sonraki sürümlerle kullanılabilir.
:::moniker-end

### <a name="troubleshooting"></a>Sorun giderme

Python'u Visual Studio yükleme veya çalıştırma sorunlarını gidermek için aşağıdaki adımları deneyin:

- Aynı hatanın Python CLI kullanılarak mı oluştuğu, yani komut isteminden *python.exe* olup olmadığını belirler.
- Visual Studio [](../install/repair-visual-studio.md) yükleyicisinde Onar seçeneğini kullanın.
- **Windows'daki Ayarlar** Apps  >  **& Python'ı** onarın veya yeniden Windows.

**Örnek hata:** Etkileşimli işlem başlatılamadı: System.ComponentModel.Win32Exception (0x80004005): Microsoft.PythonTools.Repl.PythonInteractiveEvaluator.d__43.MoveNext() içinde bilinmeyen hata (0xc0000135).

:::moniker range="<=vs-2017"

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. **2015** Visual Studio **değiştir'i Denetim Masası >** Programlar ve Özellikler'i seçerek Microsoft Visual Studio yükleyicisini **çalıştırın.**

1. Yükleyicide Değiştir'i **seçin.**

1. Programlama **Dilleri'Visual Studio için Python Araçları** > **ve** ardından Sonraki:

   ![Visual Studio 2015 yükleyicisinde PTVS seçeneği](media/installation-vs2015.png)

1. Yükleme Visual Studio tamamlandıktan [sonra, tercih edin bir Python yorumlayıcı yükleyin.](installing-python-interpreters.md) Visual Studio 2015 yalnızca Python 3.5 ve önceki sürümleri destekler; sonraki sürümler Desteklenmeyen Python sürüm **3.6** gibi bir ileti üretir. Zaten yüklü bir yorumlayıcınız varsa ve Visual Studio otomatik olarak algılamazsa bkz. [Mevcut bir ortamı el ile tanımlama.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 ve önceki sürümler

1. Visual Studio sürümünüz için uygun Visual Studio için Python Araçları sürümünü Visual Studio:

    - Visual Studio 2013: Visual Studio 2013 için [PTVS 2.2.2.](https://github.com/Microsoft/PTVS/releases/v2.2.2) Yeni **Dosya**  >  **Project** iletişim Visual Studio 2013 bu işlem için bir kısayol sağlar.
    - Visual Studio 2010 ve 2012: [Visual Studio 2010 ve 2012 için PTVS 2.1.1](https://github.com/Microsoft/PTVS/releases/v2.1.1)

1. [Tercihen bir Python yorumlayıcı yükleyin.](installing-python-interpreters.md)
Zaten yüklü bir yorumlayıcınız varsa ve Visual Studio otomatik olarak algılamazsa bkz. [Mevcut bir ortamı el ile tanımlama.](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)

:::moniker-end

## <a name="install-locations"></a>Yükleme konumları

:::moniker range=">=vs-2022"

Varsayılan olarak, Python desteği bir bilgisayarda tüm kullanıcılar için yüklenir.

Visual Studio 2022 için Python iş yükü *%ProgramFiles%\Microsoft Visual Studio \\<VS_version><VS_edition>\\ Common7\IDE\Extensions\Microsoft\Python* dizinine yüklenir; burada &lt; VS_version &gt; 2022 ve &lt; VS_edition &gt; Community, Professional veya Enterprise.

:::moniker-end
:::moniker range="<=vs-2019"

Varsayılan olarak, Python desteği bir bilgisayarda tüm kullanıcılar için yüklenir.

Visual Studio 2019 ve Visual Studio 2017 için Python iş yükü *%ProgramFiles(x86)%\Microsoft Visual Studio \\<VS_version>\\<VS_edition>Common7\IDE\Extensions\Microsoft\Python'a* yüklenir; burada &lt; VS_version &gt; 2019 veya 2017 ve &lt; VS_edition &gt; Community, Professional veya Enterprise.

:::moniker-end

:::moniker range="<=vs-2017"

2015 Visual Studio önceki sürümlerde yükleme yolları aşağıdaki gibidir:

- 32 bit:
  - Yol: *%Program Files(x86)%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Visual Studio için Python Araçları \\<PTVS_ver>*
  - Yolun kayıt defteri konumu: **HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\\<VS_ver>\InstallDir**
- 64 bit:
  - Yol: *%Program Files%\Microsoft Visual Studio \<VS_ver> \Common7\IDE\Extensions\Microsoft\Visual Studio için Python Araçları \\<PTVS_ver>*
  - Yolun kayıt defteri konumu: **HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\\<VS_ver>\InstallDir**

Konum:

- &lt;&gt;VS_ver:
  - Visual Studio 2015 için 14.0
  - Visual Studio 2013 için 12,0
  - Visual Studio 2012 için 11,0
  - Visual Studio 2010 için 10,0
- &lt;PTVS_ver, &gt; 2.2.2, 2.1.1, 2,0, 1,5, 1,1 veya 1,0 gibi bir sürüm numarasıdır.

### <a name="user-specific-installations-15-and-earlier"></a>Kullanıcıya özgü yüklemeler (1,5 ve önceki sürümler)

yalnızca geçerli kullanıcı için 1,5 ve daha önceki bir yüklemeye izin verilir; bu durumda yükleme yolu *%localappdata%\microsoft\visualstudio \\<VS_ver> \extensions\microsoft\ Visual Studio için Python Araçları \\<PTVS_ver>* &lt; &gt; ve &lt; VS_ver Visual Studio için Python Araçları PTVS_ver &gt; yukarıda açıklanan şekilde aynıdır.

:::moniker-end
