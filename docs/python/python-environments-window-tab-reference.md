---
title: Python ortamları penceresi başvurusu
description: Visual Studio 'de Python ortamları penceresinde görüntülenen sekmelerin her biri hakkında ayrıntılar.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140381"
---
# <a name="python-environments-window-tabs-reference"></a>Python ortamları pencere sekmeleri başvurusu

**Python ortamları** penceresini açmak için:

-   >  **diğer Windows**  >  **Python ortamlarını** görüntüle menü komutunu seçin.
- **Çözüm Gezgini** bir proje Için **Python ortamları** düğümüne sağ tıklayın ve **Tüm Python ortamlarını görüntüle**' yi seçin.

**Python ortamları** penceresini yeterince genişletebilirsiniz, bu seçenekler sekme olarak gösterilir ve bunlarla daha uygun olabilecek şekilde çalışabilirsiniz. Açıklık açısından, bu makaledeki sekmeler genişletilmiş görünümde gösterilmiştir.

::: moniker range="vs-2017"
![Python ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları penceresi genişletilmiş görünümü](media/environments/environments-expanded-view-2019.png)
::: moniker-end

## <a name="overview-tab"></a>Genel Bakış sekmesi

Ortam için temel bilgileri ve komutları sağlar:

::: moniker range="vs-2017"
![Python ortamlarına Genel Bakış sekmesi](media/environments/environments-overview-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamlarına Genel Bakış sekmesi](media/environments/environments-overview-tab-2019.png)
::: moniker-end

| Komut | Açıklama |
| --- | --- |
| **Bu ortamı yeni projeler için varsayılan yapın** | Visual Studio (2017 sürüm 15,5 ve önceki sürümleri), ıntellisense veritabanını yüklerken hızlı bir şekilde yanıt vermemeye başlamasına neden olabilen etkin ortamı ayarlar. Birçok pakete sahip ortamlar, daha uzun bir süre boyunca yanıt vermeyebilir. |
| **Dağıtıcısının Web sitesini ziyaret edin** | Python dağıtımı tarafından belirtilen URL 'ye bir tarayıcı açar. Python 3. x, örneğin, python.org öğesine gider. |
| **Etkileşimli pencereyi aç** | Visual Studio içinde bu ortamın [etkileşimli (REPL) penceresini](python-interactive-repl-in-visual-studio.md) açar ve tüm [başlatma betikleri (aşağıya bakın)](#startup-scripts)uygulayın. |
| **Etkileşimli betikleri keşfet** | Bkz. [Başlangıç betikleri](#startup-scripts). |
| **IPython etkileşimli modunu kullanma** | Ayarlandığında, varsayılan olarak, IPython ile **etkileşimli** pencereyi açar. Bu, `name?` Yardım ve kabuk komutlarının yanı sıra satır içi çizimleri ve genişletilmiş IPython söz dizimini sağlar `!command` . Bu seçenek, ek paketler gerektirdiğinden bir Anaconda dağıtımı kullanılırken önerilir. Daha fazla bilgi için bkz. [etkileşimli pencerede IPython kullanma](interactive-repl-ipython.md). |
| **PowerShell 'de aç** | Bir PowerShell komut penceresinde yorumlayıcı başlatır. |
| (Klasör ve program bağlantıları) | Ortamın yükleme klasörüne, *python.exe* yorumlayıcıya ve *pythonw.exe* Yorumlayıcısına hızlı erişim sağlar. ilki Windows Explorer 'da açılır, ikinci iki konsol penceresi açar. |

### <a name="startup-scripts"></a>Başlangıç betikleri

Günlük iş akışınızda etkileşimli pencereleri kullanırken, muhtemelen düzenli olarak kullandığınız yardımcı işlevleri geliştirirsiniz. örneğin, Excel bir veri çerçevesini açan bir işlev oluşturabilir ve ardından bu kodu **etkileşimli** pencerede her zaman kullanılabilir olacak şekilde bir başlangıç betiği olarak kaydedebilirsiniz.

Başlangıç betikleri, içeri aktarmalar, işlev tanımları ve başka bir şey gibi **etkileşimli** pencerenin otomatik olarak yüklediği ve çalıştırdığı kodu içerir. Bu komut dosyalarına iki şekilde başvurulur:

1. bir ortam yüklediğinizde Visual Studio, sürümünün *\<version> \\ \<environment>* &lt; &gt; Visual Studio sürümü (2017 veya 2019 gibi) olduğu ve &lt; ortamın &gt; ortam adıyla eşleştiği bir klasör belgeler \ Visual Studio \python betikleri oluşturur. **Etkileşimli betikleri keşfet** komutuyla, ortama özgü klasöre kolayca gidebilirsiniz. Bu ortam için **etkileşimli** pencereyi başlattığınızda, *Bu dosya her* şeyi alfabetik sırada bulmuştur ve çalıştırır.

1.  **araçlar**  >  **seçenekler**  >  **Python**  >  **etkileşimli Windows** sekmesindeki betikler denetimi (bkz. [etkileşimli Windows seçenekleri](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)), tüm ortamlarda yüklenen ve çalıştırılan başlatma betikleri için ek bir klasör belirtmek üzere tasarlanmıştır. Ancak, bu özellik şu anda çalışmıyor.

## <a name="configure-tab"></a>Sekmeyi Yapılandır

Varsa, **Yapılandır** sekmesi aşağıdaki tabloda açıklandığı gibi ayrıntılar içerir. bu sekme yoksa, Visual Studio tüm ayrıntıları otomatik olarak yönetiyor demektir.

::: moniker range="vs-2017"
![Python ortamları Yapılandırma sekmesi](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları Yapılandırma sekmesi](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Alan | Açıklama |
| --- | --- |
| **Açıklama** | Ortama verilecek ad. |
| **Ön ek yolu** | Yorumlayıcının taban klasör konumu. bu değeri doldurup **otomatik algıla**' ya tıklayarak, diğer alanları sizin için doldurmaya çalışır Visual Studio. |
| **Yorumlayıcı yolu** | Yorumlayıcı yürütülebilir dosyasının yolu, genellikle önek yolu ve ardından **python.exe** |
| **Pencereli yorumlayıcı** | Konsol dışı yürütülebilirin yolu, genellikle önek yolu ve ardından **pythonw.exe**. |
| **Kitaplık yolu**<br/>(varsa) | standart kitaplığın kökünü belirtir, ancak Visual Studio yorumlayıcıdan daha doğru bir yol isteyebiliyor olması durumunda bu değer yok sayılabilir. |
| **Dil sürümü** | Açılır menüden seçilidir. |
| **Mimari** | Normalde algılanan ve otomatik olarak doldurulmuş, aksi takdirde **32-bit** veya **64 bit** belirtir. |
| **PATH ortam değişkeni** | Yorumlayıcının arama yollarını bulmak için kullandığı ortam değişkeni. Visual Studio, Python başlatıldığında projenin arama yollarını içermesi için değişkenin değerini değiştirir. Genellikle bu özellik **PYTHONPATH** olarak ayarlanmalıdır, ancak bazı yorumlayıcılar farklı bir değer kullanır. |

## <a name="packages-tab"></a>Paketler sekmesi

*Ayrıca önceki sürümlerde "PIP" olarak etiketlenir.*

Visual Studio 2017 sürüm 15,7 ve üzeri sürümlerde bulunan conda ortamları için pıp ( **packages (pypi)** sekmesi) veya conda ( **packages (conda)** sekmesini kullanarak ortamda yüklü olan paketleri yönetir. Bu sekmede, bağımlılıkları da dahil olmak üzere yeni paketleri arayıp yükleyebilirsiniz.

Zaten yüklü olan paketler, güncelleştirme (bir yukarı ok) ve yüklemeyi kaldırma (bir daire içinde X) denetimleriyle birlikte görüntülenir:

![Python ortamları paketleri sekmesi](media/environments/environments-pip-tab-controls.png)

Bir arama terimi girilmesi, yüklü paketlerin listesinin yanı sıra Pypı 'den yüklenebilen paketleri de filtreliyor.

::: moniker range="vs-2017"
!["Num" üzerinde arama içeren Python ortamları paketleri sekmesi](media/environments/environments-pip-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
!["Num" üzerinde arama içeren Python ortamları paketleri sekmesi](media/environments/environments-pip-tab-2019.png)
::: moniker-end

Yukarıdaki görüntüde görebileceğiniz gibi, arama sonuçları arama terimiyle eşleşen bir dizi paket gösterir; Ancak listedeki ilk giriş, doğrudan **PIP yüklemeyi \<name>** çalıştırmak için bir komuttur. **Paketler (Conda)** sekmesi kullanıyorsanız, bunun yerine **Conda install \<name>**:

::: moniker range="vs-2017"
![Conda install komutunu gösteren Conda paketleri sekmesi](media/environments/environments-conda-tab-install.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Conda install komutunu gösteren Conda paketleri sekmesi](media/environments/environments-conda-tab-install-2019.png)
::: moniker-end

Her iki durumda da, paketin adından sonra arama kutusuna bağımsız değişkenler ekleyerek yüklemeyi özelleştirebilirsiniz. Bağımsız değişkenleri dahil ettiğinizde, arama sonuçları **PIP install** veya **Conda install** öğesini ve ardından arama kutusunun içeriğini gösterir:

::: moniker range="vs-2017"
![PIP ve Conda Install komutlarında bağımsız değişkenleri kullanma](media/environments/environments-pip-tab-arguments.png)
::: moniker-end
::: moniker range=">=vs-2019"
![PIP ve Conda Install komutlarında bağımsız değişkenleri kullanma](media/environments/environments-pip-tab-arguments-2019.png)
::: moniker-end

Bir paket yükleme, dosya sistemindeki ortamın *lib* klasörü içinde alt klasörler oluşturur. Örneğin, *c:\Python36* içinde Python 3,6 yüklüyse, paketler *c:\Python36\Lib*'ye yüklenir; *C:\Program Files\anacondad3* ' te Anaconda3 yüklüyse, paketler *C:\Program Files\anacondad3\lib dizinine* yüklenir. Conda ortamları için, paketler bu ortamın klasörüne yüklenir.

### <a name="grant-administrator-privileges-for-package-install"></a>Paket yüklemesi için yönetici ayrıcalıkları verme

paketleri dosya sisteminin korunan bir alanında bulunan *c:\Program files\anacondad3\lib* gibi bir ortama yüklerken, `pip install` paket alt klasörleri oluşturmasına izin vermek için Visual Studio yükseltilmiş olarak çalıştırılmalıdır. yükseltme gerektiğinde Visual Studio, **bu ortama yönelik paketleri yüklemek, güncelleştirmek veya kaldırmak için yönetici ayrıcalıkları** gerekebilir:

![Paket yüklemesi için yükseltme istemi](media/environments/environments-pip-elevate.png)

**Şimdi Yükselt** , tek bir işlem için PIP 'ye yönetim ayrıcalıkları verir ve aynı zamanda herhangi bir işletim sistemi için izin ister. **Yönetici ayrıcalıkları olmadan devam et** seçeneği, paketi yüklemeye çalışır, ancak hata gibi çıktıyı içeren klasörler oluşturmaya çalışırken PIP başarısız olur: **' C:\Program Files\anaconda3\lib\site-packages\png.exe ': izin reddedildi.**

**Paketleri yükleme veya kaldırma sırasında her zaman Yükselt** seçeneğinin belirlenmesi, iletişim kutusunun söz konusu ortamda görüntülenmesini önler. İletişim kutusunun yeniden görünmesini için Araçlar Seçenekleri Python Genel'e gidin ve düğmesini seçerek Kalıcı olarak  >    >    >   **gizlenen tüm iletişim kutularını sıfırlayın.**

Aynı Seçenekler **sekmesinde, tüm** ortamlar için iletişim kutusunu **gizlemesi için Her** zaman pip'i yönetici olarak çalıştır'ı da seçebilirsiniz. Bkz. [Seçenekler - Genel sekmesi.](python-support-options-and-settings-in-visual-studio.md#general-options)

### <a name="security-restrictions-with-older-versions-of-python"></a>Python'ın eski sürümleriyle ilgili güvenlik kısıtlamaları

Python 2.6, 3.1 ve 3.2 kullanırken Visual Studio, yeni güvenlik kısıtlamaları nedeniyle internetten yükleme python'ın bu sürümünde çalışmayabilirsiniz uyarıyı **gösterir:**

![Python'ın eski sürümüyle ilgili pip yükleme kısıtlamalarıyla ilgili ileti](media/environments/environments-old-version-restriction.png)

Bu uyarının nedeni, Python'ın bu eski sürümlerinde paket kaynağından paket indirmek için gerekli olan Aktarım Güvenlik Katmanı `pip install` (TLS) 1.2 için destek içerme pypi.org. Özel Python derlemeleri TLS 1.2'yi destekleyene kadar devam `pip install` ediyor olabilir.

bir paket için uygun  [get-pip.py'ı bootstrap.pypa.io'dan](https://bootstrap.pypa.io/)el ile [indirmek, pypi.org'den](https://pypi.org/)el ile indirmek ve ardından paketi bu yerel kopyadan yüklemek mümkün olabilir.

Ancak öneri yalnızca Python 2.7 veya 3.3+ sürümüne yükseltmektir. Bu durumda uyarı görünmez.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>IntelliSense sekmesi

IntelliSense tamamlama veritabanının geçerli durumunu gösterir:

![Python Ortamları IntelliSense sekmesi](media/environments/environments-intellisense-tab.png)

- 2017 Visual Studio 15.5 ve önceki sürümlerde IntelliSense tamamlamaları, bu kitaplık için derlenmiş bir veritabanına bağlıdır. Veritabanı oluşturma işlemi bir kitaplık yüklenirken arka planda yapılır, ancak biraz zaman alır ve kod yazmaya başlanırken tamamlanmadı olabilir.
- Visual Studio 2017 sürüm 15.6 ve sonrası varsayılan olarak veritabanına bağımlı olan tamamlamalar sağlamak için daha hızlı bir yöntem kullanır. Bu nedenle sekme **IntelliSense [veritabanı devre dışı] olarak etiketlenmiş.** Ortamlar için Araçlar Seçenekleri Python Deneysel Yeni stil  >    >    >    >  **IntelliSense kullan seçeneğini temizerek veritabanını etkinleştirebilirsiniz.**

Yeni Visual Studio algılayan bir ortam algılasanız (veya bir ortam eklerken), kitaplık kaynak dosyalarını analiz ederek veritabanını otomatik olarak derlemeye başlar. Bu işlem, yüklü olan işleme bağlı olarak bir dakika ile bir saat veya daha fazla zaman alır. (Örneğin Anaconda birçok kitaplıkla birlikte gelir ve veritabanını derlemek biraz zaman alır.) Tamamlandıktan sonra ayrıntılı IntelliSense alırsınız ve daha fazla kitaplık  yükleyene kadar veritabanını yeniden yenilemeniz (Db'yi Yenile düğmesiyle) ihtiyacınız olmayacaktır.

Verilerin derlenmiş olduğu kitaplıklar ! ;  bir ortamın veritabanı tam değilse, **bir !** , ana ortam listesinde yanında da görünür.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Python ortamlarını Visual Studio](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar requirements.txt kullanım](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
