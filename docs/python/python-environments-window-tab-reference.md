---
title: Python ortamları pencere başvurusu
description: Uygulamanın Python Ortamları penceresinde görünen sekmelerin her biri hakkında Visual Studio.
ms.date: 03/18/2019
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ec08fbc30f6a03929e778361c08b03281d997d1b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726795"
---
# <a name="python-environments-window-tabs-reference"></a>Python Ortamları pencere sekmeleri başvurusu

Python Ortamları **penceresini açmak** için:

- Diğer Öğeleri  >  **Görüntüle'Windows**  >  **Python Ortamları menü** komutunu seçin.
- Çözüm Gezgini'da **bir** projenin Python Ortamları **düğümüne** sağ tıklayın ve Tüm **Python Ortamlarını Görüntüle'yi seçin.**

Python Ortamları penceresini **yeterince geniş** genişlettiysanız, bu seçenekler sekme olarak gösterilir ve bu sekmelerle çalışmanız daha kullanışlı olabilir. Netlik sağlamak için bu makaledeki sekmeler genişletilmiş görünümde gösterilir.

::: moniker range="vs-2017"
![Python Ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Genel Bakış sekmesi

Ortam için temel bilgiler ve komutlar sağlar:

::: moniker range="vs-2017"
![Python Ortamlara genel bakış sekmesi](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamlara genel bakış sekmesi](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Komut | Açıklama |
| --- | --- |
| **Bu ortamı yeni projeler için varsayılan hale** | Etkin ortamı ayarlar; bu da Visual Studio (2017 sürüm 15.5 ve önceki sürümler) IntelliSense veritabanını yüklerken kısa bir süre yanıt vermeyebilirsiniz. Çok sayıda paketi olan ortamlar daha uzun süre yanıt vermeyebilirsiniz. |
| **Dağıtımcının web sitesini ziyaret edin** | Python dağıtımı tarafından sağlanan URL'ye bir tarayıcı açar. Örneğin Python 3.x, python.org. |
| **Etkileşimli pencereyi açma** | Bu ortam [için etkileşimli (REPL)](python-interactive-repl-in-visual-studio.md) penceresini Visual Studio tüm başlangıç betiklerini [uygulayarak (aşağıya bakın)](#startup-scripts). |
| **Etkileşimli betikleri keşfetme** | Bkz. [başlangıç betikleri.](#startup-scripts) |
| **IPython etkileşimli modunu kullanma** | Ayar olduğunda, varsayılan **olarak** IPython ile Etkileşimli penceresini açar. Bu, satır içi çizimlerin yanı sıra yardım ve kabuk komutları için görüntüleme gibi genişletilmiş IPython `name?` söz `!command` dizimlerini de sağlar. Bu seçenek, ek paketler gerektirdiği için Anaconda dağıtımı kullanılırken önerilir. Daha fazla bilgi için [bkz. IPython'un Etkileşimli penceresi.](interactive-repl-ipython.md) |
| **PowerShell'de aç** | Yorumlayıcıyı bir PowerShell komut penceresinde başlatır. |
| (Klasör ve program bağlantıları) | Ortamın yükleme klasörüne,python.exeyorumlayıcıya vepythonw.exe *sağlar.*  İlki Gezgin Windows de açılır, ikincisi ise bir konsol penceresi açar. |

### <a name="startup-scripts"></a>Başlangıç betikleri

Günlük iş akışında etkileşimli pencereler kullansanız da düzenli olarak kullanabileceğiniz yardımcı işlevler geliştirebilirsiniz. Örneğin, bir DataFrame'i Excel açan bir işlev oluşturabilir ve ardından etkileşimli pencerede her zaman kullanılabilir olacak şekilde bu kodu başlangıç betiği **olarak kaydedebilirsiniz.**

Başlangıç betikleri, **Etkileşimli pencerenin içeri aktarmalar,** işlev tanımları ve diğer her şey dahil olmak üzere otomatik olarak yük devredilir ve çalıştırılır. Bu tür betiklere iki şekilde başvurabilirsiniz:

1. Bir ortam Visual Studio, sürümün Visual Studio sürümü (2017 veya 2019 gibi) olduğu ve ortamın ortamın adıyla eş olduğu *Belgeler\Visual Studio \<version> \Python \\ \<environment> Betikleri* &lt; klasörü &gt; &lt; &gt; oluşturur. Etkileşimli betikleri keşfedin komutuyla ortama özgü **klasöre kolayca ulaşabilirsiniz.** Bu ortam için **Etkileşimli** pencereyi başlatarak burada bulunan *.py* dosyalarını alfabetik sırada yükler ve çalıştırır.

1. Araçlar **Seçenekleri** Python Interactive Windows sekmesindeki Betikler denetimi (bkz. Etkileşimli pencere seçenekleri), tüm ortamlarda yüklenen ve çalıştırilen başlangıç betikleri için ek bir  >    >    >   klasör belirtmek için tasarlanmıştır. [](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options) Ancak bu özellik şu anda çalışmıyor.

## <a name="configure-tab"></a>Yapılandırma sekmesi

Varsa, Yapılandır **sekmesi** aşağıdaki tabloda açıklandığı gibi ayrıntıları içerir. Bu sekme yoksa, tüm ayrıntıları Visual Studio otomatik olarak yönetebilirsiniz.

::: moniker range="vs-2017"
![Python Ortamları yapılandırma sekmesi](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python Ortamları yapılandırma sekmesi](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Alan | Açıklama |
| --- | --- |
| **Açıklama** | Ortama verilen ad. |
| **Ön ek yolu** | Yorumlayıcının temel klasör konumu. Bu değeri doldurarak ve Otomatik **Algıla'Visual Studio** diğer alanları sizin için doldurmaya çalışır. |
| **Yorumlayıcı yolu** | Yorumlayıcı yürütülebilir dosyasının yolu, genellikle ön ek yolu ve **ardından** python.exe |
| **Pencereli yorumlayıcı** | Konsol dışı yürütülebilir dosyanın yolu, genellikle ön ek yolu ve **ardından** pythonw.exe. |
| **Kitaplık yolu**<br/>(varsa) | Standart kitaplığın kökünü belirtir, ancak yorumlayıcıdan daha doğru Visual Studio yol isteğinde Visual Studio bu değer yoksayılabilir. |
| **Dil sürümü** | Açılan menüden seçilir. |
| **Mimari** | Normalde otomatik olarak algılanır ve doldurulur, aksi takdirde **32 bit veya** **64 bit belirtir.** |
| **Yol ortam değişkeni** | Yorumlayıcının arama yollarını bulmak için kullandığı ortam değişkeni. Visual Studio Python'a başlayarak değişkenin değerini projenin arama yollarını içerdiği şekilde değiştirir. Genellikle bu özellik PYTHONPATH olarak **ayarlanır,** ancak bazı yorumlayıcılar farklı bir değer kullanır. |

## <a name="packages-tab"></a>Paketler sekmesi

*Önceki sürümlerde de "pip" olarak etiketlenmiş.*

Visual Studio 2017 sürüm 15.7 ve sonraki sürümlerde conda ortamları için pip (Paketler **(PyPI)** sekmesi) veya **conda (Conda)** sekmesini kullanarak ortamda yüklü paketleri yönetir. Bu sekmede ayrıca bağımlılıkları dahil olmak üzere yeni paketleri arayabilir ve yükleyebilirsiniz.

Zaten yüklü paketler, paketi güncelleştirmek (yukarı ok) ve paketi kaldırmak (daire içinde X) için denetimlerle birlikte görünür:

![Python ortamları paketleri sekmesi](media/environments/environments-pip-tab-controls.png)

Arama terimi girerek hem yüklü paketler hem de PyPI'den yüklenecek paketler listesi filtre olur.

::: moniker range="vs-2017"
!["num" araması içeren Python ortamları paketleri sekmesi](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
!["num" araması içeren Python ortamları paketleri sekmesi](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Yukarıdaki görüntüde de gördüğünüz gibi, arama sonuçları arama terimiyle eşan bir dizi paket gösterir; Ancak, listede ilk girdi, pip install'ı doğrudan çalıştırmak **için bir \<name> komuttır.** Paketler **(Conda) sekmesindeysiniz,** bunun yerine **conda \<name> yüklemesi görüntülenir:**

::: moniker range="vs-2017"
![Conda yükleme komutunu gösteren Conda paketleri sekmesi](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Conda yükleme komutunu gösteren Conda paketleri sekmesi](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

Her iki durumda da, paketin adının ardından arama kutusuna bağımsız değişkenler ekleyerek yükleme özelleştirebilirsiniz. Bağımsız değişkenleri dahil etmek için arama sonuçlarında **pip install** veya **conda install** ve ardından arama kutusunun içeriği görüntülenir:

::: moniker range="vs-2017"
![Pip ve conda yükleme komutlarının bağımsız değişkenlerini kullanma](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Pip ve conda yükleme komutlarının bağımsız değişkenlerini kullanma](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Paket yüklemek, dosya sistemi üzerinde ortamın *Lib* klasöründe alt klasörler oluşturur. Örneğin, *c:\Python36'da* Python 3.6 yüklüyse paketler *c:\Python36\Lib* içinde yüklenir; *c:\Program Files\Anaconda3 dizininde Anaconda3* yüklüyse paketler *c:\Program Files\Anaconda3\Lib* dizinine yüklenir. Conda ortamları için paketler o ortamın klasörüne yüklenir.

### <a name="grant-administrator-privileges-for-package-install"></a>Paket yüklemesi için yönetici ayrıcalıkları ver

Paketleri *c:\Program Files\Anaconda3\Lib* gibi dosya sisteminin korumalı bir alanında bulunan bir ortama yüklerken, Visual Studio'nin paket alt klasörleri oluşturmasına izin vermek için yükseltilmiş olarak `pip install` çalışması gerekir. Yükseltme gerektiğinde, Visual Studio, bu ortam için paketleri yüklemek, güncelleştirmek veya kaldırmak için Yönetici ayrıcalıkları **gerekebilir:**

![Paket yüklemesi için yükseltme istemi](media/environments/environments-pip-elevate.png)

**Artık Yükselt,** pip'e tek bir işlem için yönetici ayrıcalıkları verir ve izinler için tüm işletim sistemi istemlerine de tabi olur. Yönetici **ayrıcalıkları** olmadan devam edin'i seçmek paketi yükleme girişiminde bulunur ancak pip şu hata gibi bir çıkışla klasör oluşturma sırasında başarısız **oluyor: 'C:\Program Files\Anaconda3\Lib\site-packages\png.py':** İzin reddedildi.

Paketleri **yüklerken veya kaldıran her zaman yükselt'i** seçmek söz konusu ortam için iletişim kutusunun görünmesini önler. İletişim kutusunun yeniden görünmesini sağlamak için, **Araçlar**  >  **Seçenekler**  >  **Python**  >  **genel** ' e gidin ve düğmeyi seçin, **tüm kalıcı gizli iletişimleri sıfırlayın**.

Aynı **Seçenekler** sekmesinde, tüm ortamların iletişim kutusunu gizlemek Için **her zaman PIP 'yi yönetici olarak çalıştır** ' ı da seçebilirsiniz. Bkz. [Seçenekler-Genel sekmesi](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Python 'un eski sürümleriyle güvenlik kısıtlamaları

python 2,6, 3,1 ve 3,2 kullanılırken Visual Studio, **yeni güvenlik kısıtlamaları nedeniyle, python 'un bu sürümünde internet 'ten yükleme çalışmayabilir**:

![Python 'un eski sürümüyle birlikte PIP yüklemesi kısıtlamaları hakkında ileti](media/environments/environments-old-version-restriction.png)

Uyarının nedeni bu Python 'un eski sürümleriyle, `pip install` pypi.org paket kaynağından paketleri indirmek için gerekli olan aktarım güvenliği katmanı (TLS) 1,2 için destek içermez. Özel Python yapıları, TLS 1,2 ' i destekleyebilir ve bu durumda `pip install` çalışmayabilir.

[Bootstrap.pypa.io](https://bootstrap.pypa.io/)adresinden bir paket için uygun *get-pip.py* indirmek ve [pypi.org](https://pypi.org/)'den bir paketi el ile indirmek ve ardından paketi o yerel kopyadan yüklemek mümkün olabilir.

Ancak, öneri yalnızca Python 2,7 veya 3.3 + sürümüne yükseltilmesinin yanı, uyarının görünmemelidir.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>IntelliSense sekmesi

IntelliSense tamamlanma veritabanının geçerli durumunu gösterir:

![Python ortamları IntelliSense sekmesi](media/environments/environments-intellisense-tab.png)

- Visual Studio 2017 sürüm 15,5 ve önceki sürümlerde, ıntellisense, bu kitaplık için derlenen bir veritabanına bağlıdır. Bir kitaplık yüklendiğinde veritabanının oluşturulması arka planda yapılır, ancak bir süre zaman alabilir ve kod yazmaya başladığınızda tamamlanmamış olabilir.
- Visual Studio 2017 sürüm 15,6 ve sonraki sürümleri, varsayılan olarak veritabanına bağımlı olmayan tamamlamalar sağlamak için daha hızlı bir yöntem kullanır. Bu nedenle sekmenin **IntelliSense [veritabanı devre dışı]** olarak etiketlenir. **Araç** seçeneklerini temizleyerek veritabanını etkinleştirebilirsiniz  >    >  **Python**  >  **deneysel**  >  **ortamlar için yeni stil IntelliSense kullanın**.

Visual Studio yeni bir ortam algıladığında (veya bir tane eklediğinizde), kitaplık kaynak dosyalarını çözümleyerek otomatik olarak veritabanını derlemeye başlar. Bu işlem, nelerin yüklü olduğuna bağlı olarak bir dakikadan bir saate veya daha fazlasına kadar zaman alabilir. (Örneğin, Anaconda, birçok kitaplığı ile birlikte gelir ve veritabanını derlemek biraz zaman alır.) Tamamlandıktan sonra ayrıntılı IntelliSense alırsınız ve daha fazla kitaplık yükleyene kadar veritabanını yeniden yenilemeniz gerekmez (DB 'yi **Yenile** düğmesi ile).

Derlenmeyen verilerin kitaplıkları bir **!**; ile işaretlenir ortamın veritabanı tamamlanmadıysa, **!** ana ortam listesinde bunun yanında da görünür.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
