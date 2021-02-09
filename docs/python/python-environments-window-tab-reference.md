---
title: Python ortamları penceresi başvurusu
description: Visual Studio 'da Python ortamları penceresinde görüntülenen sekmelerin her biri hakkında ayrıntılar.
ms.date: 03/18/2019
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d00f8cc05e4a2a2ce1e947207997cc2e46d9d9f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912373"
---
# <a name="python-environments-window-tabs-reference"></a>Python ortamları pencere sekmeleri başvurusu

**Python ortamları** penceresini açmak için:

-   >  **Diğer Windows**  >  **Python ortamlarını** görüntüle menü komutunu seçin.
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
| **Bu ortamı yeni projeler için varsayılan yapın** | Etkin ortamı, Visual Studio 'Nun (2017 sürüm 15,5 ve önceki sürümleri) IntelliSense veritabanını yüklerken hızlı bir şekilde yanıt vermeyen hale gelmesine neden olabilecek şekilde ayarlar. Birçok pakete sahip ortamlar, daha uzun bir süre boyunca yanıt vermeyebilir. |
| **Dağıtıcısının Web sitesini ziyaret edin** | Python dağıtımı tarafından belirtilen URL 'ye bir tarayıcı açar. Python 3. x, örneğin, python.org öğesine gider. |
| **Etkileşimli pencereyi aç** | Visual Studio içinde bu ortam için [etkileşimli (REPL) pencereyi](python-interactive-repl-in-visual-studio.md) açar ve tüm [başlatma betikleri (aşağıya bakın)](#startup-scripts)uygulayın. |
| **Etkileşimli betikleri keşfet** | Bkz. [Başlangıç betikleri](#startup-scripts). |
| **IPython etkileşimli modunu kullanma** | Ayarlandığında, varsayılan olarak, IPython ile **etkileşimli** pencereyi açar. Bu, `name?` Yardım ve kabuk komutlarının yanı sıra satır içi çizimleri ve genişletilmiş IPython söz dizimini sağlar `!command` . Bu seçenek, ek paketler gerektirdiğinden bir Anaconda dağıtımı kullanılırken önerilir. Daha fazla bilgi için bkz. [etkileşimli pencerede IPython kullanma](interactive-repl-ipython.md). |
| **PowerShell 'de aç** | Bir PowerShell komut penceresinde yorumlayıcı başlatır. |
| (Klasör ve program bağlantıları) | Ortamın yükleme klasörüne, *python.exe* yorumlayıcıya ve *pythonw.exe* Yorumlayıcısına hızlı erişim sağlar. İlk kez Windows Gezgini 'nde açılır, ikinci iki bir konsol penceresi açar. |

### <a name="startup-scripts"></a>Başlangıç betikleri

Günlük iş akışınızda etkileşimli pencereleri kullanırken, muhtemelen düzenli olarak kullandığınız yardımcı işlevleri geliştirirsiniz. Örneğin, Excel 'de bir DataFrame açan bir işlev oluşturabilir ve sonra bu kodu **etkileşimli** pencerede her zaman kullanılabilir olacak şekilde bir başlangıç betiği olarak kaydedebilirsiniz.

Başlangıç betikleri, içeri aktarmalar, işlev tanımları ve başka bir şey gibi **etkileşimli** pencerenin otomatik olarak yüklediği ve çalıştırdığı kodu içerir. Bu komut dosyalarına iki şekilde başvurulur:

1. Bir ortam yüklediğinizde, Visual Studio sürümü *\<version> \\ \<environment>* &lt; &gt; Visual Studio sürümü olan (2017 veya 2019 gibi) ve &lt; ortam &gt; ortamın adıyla eşleşen Studio \ Python betikleri için bir klasör oluşturur. **Etkileşimli betikleri keşfet** komutuyla, ortama özgü klasöre kolayca gidebilirsiniz. Bu ortam için **etkileşimli** pencereyi başlattığınızda, *Bu dosya her* şeyi alfabetik sırada bulmuştur ve çalıştırır.

1.  **Araçlar**  >  **Seçenekler**  >  **Python**  >  **etkileşimli Windows** sekmesi içindeki betikler denetimi (bkz. [etkileşimli Windows seçenekleri](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)), tüm ortamlarda yüklenen ve çalıştırılan başlatma betikleri için ek bir klasör belirtmeye yöneliktir. Ancak, bu özellik şu anda çalışmıyor.

## <a name="configure-tab"></a>Sekmeyi Yapılandır

Varsa, **Yapılandır** sekmesi aşağıdaki tabloda açıklandığı gibi ayrıntılar içerir. Bu sekme yoksa, Visual Studio 'Nun tüm ayrıntıları otomatik olarak yönetmediği anlamına gelir.

::: moniker range="vs-2017"
![Python ortamları Yapılandırma sekmesi](media/environments/environments-configure-tab.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Python ortamları Yapılandırma sekmesi](media/environments/environments-configure-tab-2019.png)
::: moniker-end

| Alan | Açıklama |
| --- | --- |
| **Açıklama** | Ortama verilecek ad. |
| **Ön ek yolu** | Yorumlayıcının taban klasör konumu. Bu değeri doldurarak ve **Otomatik Algıla**'ya tıkladığınızda, Visual Studio sizin için diğer alanları doldurmaya çalışır. |
| **Yorumlayıcı yolu** | Yorumlayıcı yürütülebilir dosyasının yolu, genellikle önek yolu ve ardından **python.exe** |
| **Pencereli yorumlayıcı** | Konsol dışı yürütülebilirin yolu, genellikle önek yolu ve ardından **pythonw.exe**. |
| **Kitaplık yolu**<br/>(varsa) | Standart kitaplığın kökünü belirtir, ancak Visual Studio yorumlayıcıdan daha doğru bir yol talep edebiliyor ise bu değer yok sayılabilir. |
| **Dil sürümü** | Açılır menüden seçilidir. |
| **Mimari** | Normalde algılanan ve otomatik olarak doldurulmuş, aksi takdirde **32-bit** veya **64 bit** belirtir. |
| **PATH ortam değişkeni** | Yorumlayıcının arama yollarını bulmak için kullandığı ortam değişkeni. Visual Studio, Python başlatıldığında projenin arama yollarını içermesi için değişkenin değerini değiştirir. Genellikle bu özellik **PYTHONPATH** olarak ayarlanmalıdır, ancak bazı yorumlayıcılar farklı bir değer kullanır. |

## <a name="packages-tab"></a>Paketler sekmesi

*Ayrıca önceki sürümlerde "PIP" olarak etiketlenir.*

Ortamda yüklü olan paketleri, Visual Studio 2017 sürüm 15,7 ve sonrasındaki Conda ortamları için PIP ( **Packages (PyPI)** sekmesini) veya Conda ( **Packages (Conda)** sekmesini kullanarak yönetir. Bu sekmede, bağımlılıkları da dahil olmak üzere yeni paketleri arayıp yükleyebilirsiniz.

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

Paketleri dosya sisteminin korunan bir alanında bulunan *C:\Program Files\anacondad3\lib* gibi bir ortama yüklerken, Visual Studio 'nun `pip install` paket alt klasörleri oluşturmasına izin vermek için yükseltilmiş olarak çalışması gerekir. Yükseltme gerektiğinde, Visual Studio istemi görüntüler, **Bu ortama yönelik paketleri yüklemek, güncelleştirmek veya kaldırmak Için yönetici ayrıcalıkları** gerekebilir:

![Paket yüklemesi için yükseltme istemi](media/environments/environments-pip-elevate.png)

**Şimdi Yükselt** , tek bir işlem için PIP 'ye yönetim ayrıcalıkları verir ve aynı zamanda herhangi bir işletim sistemi için izin ister. **Yönetici ayrıcalıkları olmadan devam et** seçeneği, paketi yüklemeye çalışır, ancak hata gibi çıktıyı içeren klasörler oluşturmaya çalışırken PIP başarısız olur: **' C:\Program Files\anaconda3\lib\site-packages\png.exe ': izin reddedildi.**

**Paketleri yükleme veya kaldırma sırasında her zaman Yükselt** seçeneğinin belirlenmesi, iletişim kutusunun söz konusu ortamda görüntülenmesini önler. İletişim kutusunun yeniden görünmesini sağlamak için, **Araçlar**  >  **Seçenekler**  >  **Python**  >  **genel** ' e gidin ve düğmeyi seçin, **tüm kalıcı gizli iletişimleri sıfırlayın**.

Aynı **Seçenekler** sekmesinde, tüm ortamların iletişim kutusunu gizlemek Için **her zaman PIP 'yi yönetici olarak çalıştır** ' ı da seçebilirsiniz. Bkz. [Seçenekler-Genel sekmesi](python-support-options-and-settings-in-visual-studio.md#general-options).

### <a name="security-restrictions-with-older-versions-of-python"></a>Python 'un eski sürümleriyle güvenlik kısıtlamaları

Python 2,6, 3,1 ve 3,2 kullanılırken, Visual Studio, **yeni güvenlik kısıtlamaları nedeniyle uyarı gösterir. Bu, Python 'un bu sürümünde internet 'ten yükleme çalışmayabilir**:

![Python 'un eski sürümüyle birlikte PIP yüklemesi kısıtlamaları hakkında ileti](media/environments/environments-old-version-restriction.png)

Uyarının nedeni bu Python 'un eski sürümleriyle, `pip install` pypi.org paket kaynağından paketleri indirmek için gerekli olan aktarım güvenliği katmanı (TLS) 1,2 için destek içermez. Özel Python yapıları, TLS 1,2 ' i destekleyebilir ve bu durumda `pip install` çalışmayabilir.

[Bootstrap.pypa.io](https://bootstrap.pypa.io/)adresinden bir paket için uygun *get-pip.py* indirmek ve [pypi.org](https://pypi.org/)'den bir paketi el ile indirmek ve ardından paketi o yerel kopyadan yüklemek mümkün olabilir.

Ancak, öneri yalnızca Python 2,7 veya 3.3 + sürümüne yükseltilmesinin yanı, uyarının görünmemelidir.

::: moniker range="vs-2017"
## <a name="intellisense-tab"></a>IntelliSense sekmesi

IntelliSense tamamlanma veritabanının geçerli durumunu gösterir:

![Python ortamları IntelliSense sekmesi](media/environments/environments-intellisense-tab.png)

- Visual Studio 2017 sürüm 15,5 ve önceki sürümlerde, IntelliSense, bu kitaplık için derlenen bir veritabanına bağlıdır. Bir kitaplık yüklendiğinde veritabanının oluşturulması arka planda yapılır, ancak bir süre zaman alabilir ve kod yazmaya başladığınızda tamamlanmamış olabilir.
- Visual Studio 2017 sürüm 15,6 ve üzeri, varsayılan olarak veritabanına bağımlı olmayan tamamlamalar sağlamak için daha hızlı bir yöntem kullanır. Bu nedenle sekmenin **IntelliSense [veritabanı devre dışı]** olarak etiketlenir. **Araç** seçeneklerini temizleyerek veritabanını etkinleştirebilirsiniz  >    >  **Python**  >  **deneysel**  >  **ortamlar için yeni stil IntelliSense kullanın**.

Visual Studio yeni bir ortam algıladığında (veya bir tane eklediğinizde), kitaplık kaynak dosyalarını çözümleyerek otomatik olarak veritabanını derlemeye başlar. Bu işlem, nelerin yüklü olduğuna bağlı olarak bir dakikadan bir saate veya daha fazlasına kadar zaman alabilir. (Örneğin, Anaconda, birçok kitaplığı ile birlikte gelir ve veritabanını derlemek biraz zaman alır.) Tamamlandıktan sonra ayrıntılı IntelliSense alırsınız ve daha fazla kitaplık yükleyene kadar veritabanını yeniden yenilemeniz gerekmez (DB 'yi **Yenile** düğmesi ile).

Derlenmeyen verilerin kitaplıkları bir **!**; ile işaretlenir ortamın veritabanı tamamlanmadıysa, **!** ana ortam listesinde bunun yanında da görünür.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için requirements.txt kullanma](managing-required-packages-with-requirements-txt.md)
- [Arama yolları](search-paths.md)
