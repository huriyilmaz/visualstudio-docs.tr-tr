---
title: Python ortamları penceresi başvurusu
description: Her Visual Studio'da Python ortamları penceresinde görünen sekmeler ayrıntıları.
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409981"
---
# <a name="python-environments-window-tabs-reference"></a>Python ortamları penceresi Sekme Başvurusu

**Python ortamları** penceresini açmak için:

-  > **diğer Windows** > **Python ortamlarını** **görüntüle** menü komutunu seçin.
- **Çözüm Gezgini** bir proje Için **Python ortamları** düğümüne sağ tıklayın ve **Tüm Python ortamlarını görüntüle**' yi seçin.

**Python ortamları** penceresini yeterince genişletebilirsiniz, bu seçenekler sekme olarak gösterilir ve bunlarla daha uygun olabilecek şekilde çalışabilirsiniz. Daha anlaşılır olması için bu makaledeki sekmeleri Genişletilmiş görünümde gösterilir.

::: moniker range="vs-2017"
![Python ortamları penceresi Genişletilmiş Görünümü](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları penceresi Genişletilmiş Görünümü](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Genel Bakış sekmesi

Ortam için temel bilgileri ve komutları sağlar:

::: moniker range="vs-2017"
![Python ortamları genel bakış sekmesi](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları genel bakış sekmesi](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Komut | Açıklama |
| --- | --- |
| **Bu ortamı yeni projeler için varsayılan yapın** | Visual Studio neden olabilecek etkin ortam ayarlar (2017 sürüm 15.5 ve öncesi) IntelliSense veritabanı yüklenirken kısa bir süreliğine duyuracağı olacak. Birçok paketleriyle ortamları daha uzun süre duyuracağı olabilir. |
| **Dağıtıcısının Web sitesini ziyaret edin** | Python dağıtım tarafından sağlanan URL bir tarayıcı açar. Python 3.x, örneğin, için python.org gider. |
| **Etkileşimli pencereyi aç** | Visual Studio içinde bu ortam için [etkileşimli (REPL) pencereyi](python-interactive-repl-in-visual-studio.md) açar ve tüm [başlatma betikleri (aşağıya bakın)](#startup-scripts)uygulayın. |
| **Etkileşimli betikleri keşfet** | Bkz. [Başlangıç betikleri](#startup-scripts). |
| **IPython etkileşimli modunu kullanma** | Ayarlandığında, varsayılan olarak, IPython ile **etkileşimli** pencereyi açar. Bu, satır içi çizimleri ve `name?` gibi genişletilmiş IPython söz dizimini ve kabuk komutlarının yardımını ve `!command` görüntülemesini sağlar. Bir Anaconda dağıtım olarak kullanarak ek paketler gerektirdiğinde bu seçeneği önerilir. Daha fazla bilgi için bkz. [etkileşimli pencerede IPython kullanma](interactive-repl-ipython.md). |
| **PowerShell 'de aç** | Bir PowerShell komut penceresinde yorumlayıcı başlatır. |
| (Klasör ve program bağlantılar) | Ortamın yükleme klasörü, *Python. exe* yorumlayıcı ve *pythonw. exe* yorumlayıcı için hızlı erişim sağlar. Windows Gezgini'nde ilk açılır, sonraki iki konsol penceresi açın. |

### <a name="startup-scripts"></a>Başlatma komut dosyaları

Etkileşimli pencere, gündelik iş akışınızı kullandıkça, büyük olasılıkla düzenli olarak kullandığınız yardımcı işlevleri geliştirin. Örneğin, Excel 'de bir DataFrame açan bir işlev oluşturabilir ve sonra bu kodu **etkileşimli** pencerede her zaman kullanılabilir olacak şekilde bir başlangıç betiği olarak kaydedebilirsiniz.

Başlangıç betikleri, içeri aktarmalar, işlev tanımları ve başka bir şey gibi **etkileşimli** pencerenin otomatik olarak yüklediği ve çalıştırdığı kodu içerir. Bu komut iki yolla başvurulur:

1. Bir ortam yüklediğinizde, Visual Studio, > sürüm &lt;Visual Studio sürümü (2017 veya 2019 gibi) ve&gt; ortamı &lt;ortam adıyla eşleştiği için, Visual Studio *\<sürümü > \Python betikleri\\\<ortamı* oluşturur.&gt; **Etkileşimli betikleri keşfet** komutuyla, ortama özgü klasöre kolayca gidebilirsiniz. Bu ortam için **etkileşimli** pencereyi başlattığınızda, *Bu dosya her* şeyi alfabetik sırada bulmuştur ve çalıştırır.

1. **Araçlar** > **seçeneklerdeki** **betikler** denetimi > **Python** > **etkileşimli Windows** sekmesi (bkz. [etkileşimli Windows seçenekleri](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)), tüm ortamlarda yüklenen ve çalıştırılan başlatma betikleri için ek bir klasör belirtmeye yöneliktir. Ancak, bu özellik şu anda çalışmıyor.

## <a name="configure-tab"></a>Yapılandır sekmesi

Varsa, **Yapılandır** sekmesi aşağıdaki tabloda açıklandığı gibi ayrıntılar içerir. Bu sekme yoksa, Visual Studio otomatik olarak tüm ayrıntıları yönetiyor anlamına gelir.

::: moniker range="vs-2017"
![Python ortamları Yapılandır sekmesi](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları Yapılandır sekmesi](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Alan | Açıklama |
| --- | --- |
| **Açıklama** | Ortamı sağlamak için adı. |
| **Ön ek yolu** | Yorumlayıcı temel klasörün konumu. Bu değeri doldurarak ve **Otomatik Algıla**'ya tıkladığınızda, Visual Studio sizin için diğer alanları doldurmaya çalışır. |
| **Yorumlayıcı yolu** | Yorumlayıcı yürütülebilir dosyasının yolu, genellikle **Python. exe** tarafından izlenen önek yolu |
| **Pencereli yorumlayıcı** | Konsol dışı yürütülebilirin yolu, genellikle önek yolu ve ardından **pythonw. exe**. |
| **Kitaplık yolu**<br/>(varsa) | Standart Kitaplığı'nın kökünü belirtir ancak bu değer, Visual Studio yorumlayıcı istek daha doğru bir yolu erişebiliyorsa yoksayılabilir. |
| **Dil sürümü** | Aşağı açılan menüden seçim. |
| **Mimari** | Normalde algılanan ve otomatik olarak doldurulmuş, aksi takdirde **32-bit** veya **64 bit**belirtir. |
| **PATH ortam değişkeni** | Ortam değişkenini yorumlayıcı arama yollarını bulmak için kullanır. Visual Studio, projenin arama yollarını içeren Python başlatırken değişkenin değerini değiştirir. Genellikle bu özellik **PYTHONPATH**olarak ayarlanmalıdır, ancak bazı yorumlayıcılar farklı bir değer kullanır. |

## <a name="packages-tab"></a>Paketleri sekmesi

*Ayrıca önceki sürümlerde "PIP" olarak etiketlenir.*

Ortamda yüklü olan paketleri, Visual Studio 2017 sürüm 15,7 ve sonrasındaki Conda ortamları için PIP ( **Packages (PyPI)** sekmesini) veya Conda ( **Packages (Conda)** sekmesini kullanarak yönetir. Bu sekmede, bağımlılıkları da dahil olmak üzere yeni paketleri arayıp yükleyebilirsiniz.

Paket zaten yüklü olan paketleri denetimleri (yukarı ok) güncelleştirme ve kaldırma (daire içinde X) ile görünür:

![Python ortamları Paketleri sekmesi](media/environments/environments-pip-tab-controls.png)

Bir arama terimi filtreleri Pypı yüklü paketleri yanı sıra yüklü paketleri listesi giriliyor.

::: moniker range="vs-2017"
![Python ortamları paketleri sekmesinde "num" bir arama özelliğiyle](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları paketleri sekmesinde "num" bir arama özelliğiyle](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Yukarıdaki görüntüde görebileceğiniz gibi, arama sonuçları arama terimiyle eşleşen bir dizi paket gösterir; Ancak listedeki ilk giriş, doğrudan **> \<adı** 'nı çalıştırmak için bir komuttur. **Paketler (Conda)** sekmesi kullanıyorsanız, bunun yerine **Conda install \<name >** ' u görürsünüz:

::: moniker range="vs-2017"
![Yükleme komutunu bir conda gösteren Conda Paketleri sekmesi](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Yükleme komutunu bir conda gösteren Conda Paketleri sekmesi](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

Her iki durumda da, yükleme paket adından sonra arama kutusuna bağımsız değişken ekleyerek özelleştirebilirsiniz. Bağımsız değişkenleri dahil ettiğinizde, arama sonuçları **PIP install** veya **Conda install** öğesini ve ardından arama kutusunun içeriğini gösterir:

::: moniker range="vs-2017"
![Pip ve conda yükleme komutları bağımsız değişkenleri kullanma](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Pip ve conda yükleme komutları bağımsız değişkenleri kullanma](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Bir paket yükleme, dosya sistemindeki ortamın *lib* klasörü içinde alt klasörler oluşturur. Örneğin, *c:\Python36*içinde Python 3,6 yüklüyse, paketler *c:\Python36\Lib*'ye yüklenir; *C:\Program Files\anacondad3* ' te Anaconda3 yüklüyse, paketler *C:\Program Files\anacondad3\lib dizinine*yüklenir. Conda ortamları için, paketler bu ortamın klasörüne yüklenir.

### <a name="grant-administrator-privileges-for-package-install"></a>Yükleme paketi için yönetici ayrıcalıkları verme

Paketleri dosya sisteminin korunan bir alanında bulunan *C:\Program Files\anacondad3\lib*gibi bir ortama yüklerken, Visual Studio 'nun paket alt klasörleri oluşturmasına izin vermek için `pip install` yükseltilmiş olarak çalıştırması gerekir. Yükseltme gerektiğinde, Visual Studio istemi görüntüler, **Bu ortama yönelik paketleri yüklemek, güncelleştirmek veya kaldırmak Için yönetici ayrıcalıkları**gerekebilir:

![Paket yüklemesi için yükseltme istemi](media/environments/environments-pip-elevate.png)

**Şimdi Yükselt** , tek bir işlem için PIP 'ye yönetim ayrıcalıkları verir ve aynı zamanda herhangi bir işletim sistemi için izin ister. **Yönetici ayrıcalıkları olmadan devam et** seçeneği, paketi yüklemeye çalışır, ancak hata gibi çıktıyı içeren klasörler oluşturmaya çalışırken PIP başarısız olur: **' C:\Program Files\anaconda3\lib\site-packages\png.exe ': izin reddedildi.**

**Paketleri yükleme veya kaldırma sırasında her zaman Yükselt** seçeneğinin belirlenmesi, iletişim kutusunun söz konusu ortamda görüntülenmesini önler. İletişim kutusunun yeniden görünmesini sağlamak için **, > ** **araçlar** > **Python** > **genel** ' e gidin ve düğmeyi seçin, **tüm kalıcı gizli iletişim kutularını sıfırlayın**.

Aynı **Seçenekler** sekmesinde, tüm ortamların iletişim kutusunu gizlemek Için **her zaman PIP 'yi yönetici olarak çalıştır** ' ı da seçebilirsiniz. Bkz. [Seçenekler-Genel sekmesi](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Python'ın eski sürümleriyle birlikte güvenlik kısıtlamaları

Python 2,6, 3,1 ve 3,2 kullanılırken, Visual Studio, **yeni güvenlik kısıtlamaları nedeniyle uyarı gösterir. Bu, Python 'un bu sürümünde internet 'ten yükleme çalışmayabilir**:

![Python eski sürümü yükleme kısıtlamaları iletisi pip hakkında](media/environments/environments-old-version-restriction.png)

Uyarının nedeni, Python 'un bu eski sürümleriyle `pip install`, pypi.org paket kaynağından paketleri indirmek için gerekli olan aktarım güvenliği katmanı (TLS) 1,2 için destek içermez. Özel Python yapıları, `pip install` çalışması için TLS 1,2 destekleyebilir.

[Bootstrap.pypa.io](https://bootstrap.pypa.io/)adresinden bir paket için uygun *get-pip.py* indirmek ve [pypi.org](https://pypi.org/)'den bir paketi el ile indirmek ve ardından paketi o yerel kopyadan yüklemek mümkün olabilir.

Ancak yalnızca Python 2.7 veya 3.3 durumu uyarısı görünmez + yükseltmek için önerilir.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>IntelliSense sekmesi

IntelliSense tamamlanma veritabanı geçerli durumunu gösterir:

![Python ortamları IntelliSense sekmesi](media/environments/environments-intellisense-tab.png)

- Visual Studio 2017 sürüm 15,5 ve önceki sürümlerde, IntelliSense, bu kitaplık için derlenen bir veritabanına bağlıdır. Veritabanı oluşturma arka planda gerçekleştirilir, bu kitaplığa yüklendiğinde, ancak biraz zaman alabilir ve kod yazmaya başladığınızda tam olmayabilir.
- Visual Studio 2017 sürüm 15,6 ve üzeri, varsayılan olarak veritabanına bağımlı olmayan tamamlamalar sağlamak için daha hızlı bir yöntem kullanır. Bu nedenle sekmenin **IntelliSense [veritabanı devre dışı]** olarak etiketlenir.  > **Python** > **deneysel** > seçenek **araçları** > **seçeneklerini** temizleyerek veritabanını etkinleştirebilir ve **ortamlar için yeni stil IntelliSense kullanın**

Visual Studio yeni bir ortam algılar (veya bir ekledikten sonra), veritabanı, kitaplık kaynak dosyalarını analiz ederek derlemek otomatik olarak başlar. Bu işlem, herhangi bir yere bir saat veya yüklenenler bağlı olarak daha fazla bilgi için bir dakika sürebilir. (Örneğin, Anaconda, birçok kitaplığı ile birlikte gelir ve veritabanını derlemek biraz zaman alır.) Tamamlandıktan sonra ayrıntılı IntelliSense alırsınız ve daha fazla kitaplık yükleyene kadar veritabanını yeniden yenilemeniz gerekmez (DB 'yi **Yenile** düğmesi ile).

Derlenmeyen verilerin kitaplıkları bir **!** ; ile işaretlenir ortamın veritabanı tamamlanmadıysa, **!** Ayrıca yanında ana ortam listesinde görünür.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements. txt kullanın](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
