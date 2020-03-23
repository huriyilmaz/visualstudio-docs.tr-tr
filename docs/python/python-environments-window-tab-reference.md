---
title: Python ortamları pencere başvurusu
description: Visual Studio'daki Python Ortamları penceresinde görünen sekmelerin her birinin ayrıntıları.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 578f73aabfb8b5a4c8336c8611f634b8947c8885
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302772"
---
# <a name="python-environments-window-tabs-reference"></a>Python Ortamları pencere sekmeleri başvurusu

**Python Ortamları** penceresini açmak için:

- **Diğer Windows** > **Python Ortamlarını** **Görüntüle** > menüsü komutunu seçin.
- **Solution Explorer'daki** bir proje için **Python Ortamları** düğümüne sağ tıklayın ve **Tüm Python Ortamlarını Görüntüle'yi**seçin.

**Python Ortamları** penceresini yeterince genişletirseniz, bu seçenekler, çalışmak için daha uygun bulabileceğiniz sekmeler olarak gösterilir. Netlik için, bu makaledeki sekmeler genişletilmiş görünümde gösterilir.

::: moniker range="vs-2017"
![Python Ortamları penceresi genişletilmiş görünüm](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamları penceresi genişletilmiş görünüm](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Genel Bakış sekmesi

Ortam için temel bilgi ve komutlar sağlar:

::: moniker range="vs-2017"
![Python Ortamları genel bakış sekmesi](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamları genel bakış sekmesi](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Komut | Açıklama |
| --- | --- |
| **Bu ortamı yeni projeler için varsayılan hale getirme** | Visual Studio'nun (2017 sürüm 15.5 ve daha önce) IntelliSense veritabanını yüklerken kısa bir süre yanıt vermemesine neden olabilecek etkin ortamı ayarlar. Birçok paketin olduğu ortamlar daha uzun süre yanıt vermiyor olabilir. |
| **Distribütörün web sitesini ziyaret edin** | Python dağıtımı tarafından sağlanan URL'ye bir tarayıcı açar. Örneğin Python 3.x python.org gider. |
| **Etkileşimli pencereyi aç** | Visual Studio içindeki bu ortam için [etkileşimli (REPL) penceresini](python-interactive-repl-in-visual-studio.md) açar ve başlangıç komut dosyalarını uygular [(aşağıya bakın)](#startup-scripts). |
| **Etkileşimli komut dosyalarını keşfedin** | [Başlangıç komut dosyalarını](#startup-scripts)görün. |
| **IPython etkileşimli modunu kullanma** | Ayarlandığında, varsayılan olarak IPython ile **Etkileşimli** pencereyi açar. Bu, satır ara çizimlerinin yanı sıra yardım ve `name?` `!command` kabuk komutlarını görüntülemek gibi genişletilmiş IPython sözdizimini de sağlar. Bu seçenek, ekstra paketler gerektirdiği için Anaconda dağıtımı kullanırken önerilir. Daha fazla bilgi için [Etkileşimli pencerede IPython'u kullanın'](interactive-repl-ipython.md)a bakın. |
| **PowerShell'de açık** | Bir PowerShell komut penceresinde tercüman ı başlatır. |
| (Klasör ve program bağlantıları) | Ortamın yükleme klasörüne, *python.exe* yorumlayıcısına ve *pythonw.exe* yorumlayıcısına hızlı erişim sağlar. İlki Windows Gezgini'nde açılır, ikincisi bir konsol penceresi açar. |

### <a name="startup-scripts"></a>Başlangıç komut dosyaları

Günlük iş akışınızda etkileşimli pencereler kullandığınızda, büyük olasılıkla düzenli olarak kullandığınız yardımcı işlevleri geliştirirsiniz. Örneğin, Excel'de bir DataFrame açan bir işlev oluşturabilir ve ardından bu kodu **etkileşimli** pencerede her zaman kullanılabilsin diye başlangıç komut dosyası olarak kaydedebilirsiniz.

Başlangıç komut **dosyaları, etkileşimli** pencerenin içe aktarımlar, işlev tanımları ve kelimenin tam anlamıyla başka bir şey de dahil olmak üzere otomatik olarak yükleyip çalıştığı kod içerir. Bu tür komut dosyaları iki şekilde başvurulan:

1. Bir ortam yüklediğinizde, Visual Studio, Visual Studio sürümünün&gt; Visual Studio sürümünün (2017 veya 2019 gibi) olduğu &lt;&gt; &lt;ve ortamın ortamın adıyla eşleştiği>*belgeler\Visual Studio \<sürümü>\Python Scripts\\\<ortamı* klasörü oluşturur. **Etkileşimli komut dosyalarını keşfet** komutuyla ortama özel klasöre kolayca gidebilirsiniz. Bu ortam için **Etkileşimli** pencereyi başlattığınızda, alfabetik sırada bulunan ne olursa olsun *.py* dosyaları yükler ve çalışır.

1.  >  **Araçlar** > **Seçenekleri** > **Python****Interactive Windows** sekmesinde Komut **Dosyaları** denetimi [(bkz. Etkileşimli windows seçenekleri)](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)tüm ortamlarda yüklenen ve çalıştırılan başlangıç komut dosyaları için ek bir klasör belirtmek için tasarlanmıştır. Ancak, bu özellik şu anda çalışmıyor.

## <a name="configure-tab"></a>Yapılandırma sekmesi

Varsa, **Yapılandırma** sekmesi aşağıdaki tabloda açıklandığı gibi ayrıntıları içerir. Bu sekme yoksa, Visual Studio tüm ayrıntıları otomatik olarak yönetiyor demektir.

::: moniker range="vs-2017"
![Python Ortamları yapılandırma sekmesi](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamları yapılandırma sekmesi](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Alan | Açıklama |
| --- | --- |
| **Açıklama** | Çevreye vermek için isim. |
| **Önek yolu** | Yorumlayıcının temel klasör konumu. Bu değeri doldurarak ve **Otomatik Algıla'yı**tıklatarak Visual Studio sizin için diğer alanları doldurmaya çalışır. |
| **Tercüman yolu** | Yorumlayıcıya giden yol çalıştırılabilir, genellikle **python.exe** tarafından izlenen önek yolu |
| **Pencereli tercüman** | Konsol olmayan yürütülebilir giden yol, genellikle **pythonw.exe**tarafından izlenen önek yolu . |
| **Kütüphane yolu**<br/>(varsa) | Standart kitaplığın kökünü belirtir, ancak Visual Studio yorumlayıcıdan daha doğru bir yol isteyebiliyorsa bu değer yoksayılabilir. |
| **Dil sürümü** | Açılır menüden seçilir. |
| **Mimari** | Normalde algılanan ve otomatik olarak doldurulmuş, aksi takdirde **32-bit** veya **64-bit**belirtir. |
| **Yol ortamı değişkeni** | Yorumlayıcının arama yollarını bulmak için kullandığı ortam değişkeni. Visual Studio Python'u başlatırken değişkenin değerini değiştirin ve böylece projenin arama yollarını içerir. Genellikle bu özellik **PYTHONPATH**olarak ayarlanmalıdır, ancak bazı yorumlayıcılar farklı bir değer kullanır. |

## <a name="packages-tab"></a>Paketler sekmesi

*Ayrıca önceki sürümlerde "pip" olarak etiketlenmiştir.*

Visual Studio 2017 sürüm 15.7 ve sonraki sürümdeki conda ortamları için pip **(Paketler (PyPI)** sekmesi veya conda **(Paketler (Conda)** sekmesi) kullanarak ortama yüklenen paketleri yönetir. Bu sekmede, bağımlılıkları da dahil olmak üzere yeni paketleri arayabilir ve yükleyebilirsiniz.

Zaten yüklenmiş paketler paketi güncelleştirmek (yukarı ok) ve kaldırma (dairedeki X) denetimleriyle görünür:

![Python ortamları paketleri sekmesi](media/environments/environments-pip-tab-controls.png)

Arama terimi girilmesi, yüklü paketlerin listesini ve PyPI'den yüklenebilecek paketleri filtreler.

::: moniker range="vs-2017"
![Python ortamları "num" üzerinde bir arama ile paketler sekmesi](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları "num" üzerinde bir arama ile paketler sekmesi](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Yukarıdaki resimde de görebileceğiniz gibi, arama sonuçları arama terimiyle eşleşen bir dizi paket gösterir; listedeki ilk giriş, ancak, **doğrudan pip yüklemek \<adı>** çalıştırmak için bir komuttur. **Paketler (Conda)** sekmesindeyseniz, bunun yerine **conda \<yükleme adını>** görürsünüz:

::: moniker range="vs-2017"
![Conda yükleme komutunu gösteren Conda paketleri sekmesi](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Conda yükleme komutunu gösteren Conda paketleri sekmesi](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

Her iki durumda da, paketin adından sonra arama kutusuna bağımsız değişkenler ekleyerek yüklemeyi özelleştirebilirsiniz. Bağımsız değişkenler eklediğinizde, arama sonuçları **pip yükleme** veya **conda yükleme** ve ardından arama kutusunun içeriğini gösterir:

::: moniker range="vs-2017"
![Pip ve conda yükleme komutlarında bağımsız değişkenleri kullanma](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Pip ve conda yükleme komutlarında bağımsız değişkenleri kullanma](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Bir paketin yüklenmesi, dosya sisteminde ortamın *Lib* klasöründe alt klasörler oluşturur. Örneğin, python 3.6 yüklü yse *c:\Python36*, paketleri *c yüklü:\Python36\Lib;* Eğer Anaconda3 yüklü varsa *c:\Program Files\Anaconda3* sonra paketleri *c yüklü:\Program Files\Anaconda3\Lib*. Conda ortamları için paketler bu ortamın klasörüne yüklenir.

### <a name="grant-administrator-privileges-for-package-install"></a>Paket yükleme için yönetici ayrıcalıkları tanıyın

*C:\Program Files\Anaconda3\Lib*gibi dosya sisteminin korunan bir alanında bulunan bir ortama paketleri yüklerken, `pip install` Visual Studio paket alt klasörleri oluşturmak için yüksek çalışması gerekir. Yükseklik gerektiğinde, Visual Studio istemi görüntüler, **Yönetici ayrıcalıkları yüklemek için gerekli olabilir, bu ortam için paketleri güncellemek veya kaldırmak:**

![Paket kurulumu için yükseklik istemi](media/environments/environments-pip-elevate.png)

**Yükseltme şimdi** tek bir işlem için pip için idari ayrıcalıklar verir, ayrıca izinler için herhangi bir işletim sistemi istemleri tabidir. Yönetici **ayrıcalıkları olmadan devam** seçeneğini seçmek paketi yüklemeye çalışır, ancak hata gibi çıktısı olan klasörler oluşturmaya çalışırken pip başarısız **olur: 'C:\Program Files\Anaconda3\Lib\site-packages\png.py': İzin reddedildi.**

Paketleri **yüklerken veya kaldırırken Her Zaman yükselt'i** seçmek, söz konusu ortam için iletişim kutusunun görünmesini engeller. İletişim kutusunu yeniden görünmesini sağlamak için **Araçlar** > **Seçenekleri** > **Python** > **General'e** gidin ve düğmeyi seçin, tüm kalıcı olarak gizlenmiş **iletişim günlüklerini sıfırla.**

Aynı **Seçenekler** sekmesinde, tüm ortamlar için iletişimi bastırmak için **her zaman pip'i yönetici olarak çalıştır'ı** da seçebilirsiniz. [Bkz. Seçenekler - Genel sekmesi](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Python'un eski sürümleriyle güvenlik kısıtlamaları

Python 2.6, 3.1 ve 3.2 kullanırken, Visual Studio uyarı gösterir, **Yeni güvenlik kısıtlamaları nedeniyle, internetten yükleme Python bu sürümü üzerinde çalışmayabilir:**

![Python'un eski sürümüyle pip yükleme kısıtlamaları hakkında ileti](media/environments/environments-old-version-restriction.png)

Uyarının nedeni, Python'un bu eski `pip install` sürümlerinde, paket kaynağından paketleri indirmek için gerekli olan Transport Security Layer (TLS) 1.2 için destek içermemesidir, pypi.org. Özel Python oluşturur TLS 1.2'yi `pip install` destekleyebilir, bu durumda işe yarayabilir.

[Bootstrap.pypa.io](https://bootstrap.pypa.io/)bir paket için uygun *get-pip.py* indirmek, [pypi.org'dan](https://pypi.org/)bir paketi el ile indirmek ve paketi bu yerel kopyadan yüklemek mümkün olabilir.

Ancak öneri, python 2.7 veya 3.3+'a yükseltme yapmaktır, bu durumda uyarı görünmez.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>IntelliSense sekmesi

IntelliSense tamamlama veritabanının geçerli durumunu gösterir:

![Python Ortamları IntelliSense sekmesi](media/environments/environments-intellisense-tab.png)

- Visual Studio 2017 sürüm 15.5 ve önceki sürümde, IntelliSense tamamlamaları bu kitaplık için derlenmiş bir veritabanına bağlıdır. Veritabanı oluşturma bir kitaplık yüklü olduğunda arka planda yapılır, ancak biraz zaman alabilir ve kod yazmaya başladığınızda tamamlanmış olmayabilir.
- Visual Studio 2017 sürüm 15.6 ve daha sonra varsayılan olarak veritabanına bağlı olmayan tamamlamalar sağlamak için daha hızlı bir yöntem kullanır. Bu nedenle sekme **IntelliSense [veritabanı devre dışı]** olarak etiketlenir. Araçlar **Tools** > **Seçenekleri** > **Python** > **Deneysel** > **Ortamlar için yeni stil IntelliSense kullanarak**veritabanını etkinleştirebilirsiniz.

Visual Studio yeni bir ortam algıladığında (veya bir ortam eklediğinizde), kitaplık kaynak dosyalarını çözümleyerek veritabanını otomatik olarak derlemeye başlar. Bu işlem, yüklenenlere bağlı olarak bir dakikadan bir saate kadar sürebilir. (Anaconda, örneğin, birçok kütüphane ile birlikte gelir ve veritabanı derlemek için biraz zaman alır.) Tamamlandıktan sonra ayrıntılı IntelliSense alırsınız ve daha fazla kitaplık yükleyene kadar veritabanını yeniden yenilemeniz gerekmez **(DB Yenile** düğmesiyle).

Verilerin derlenmediği kitaplıklar bir **!** ile işaretlenir; bir ortamın veritabanı tamamlanmamışsa, bir **!** ana ortam listesinde yanında da görünür.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanın](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
