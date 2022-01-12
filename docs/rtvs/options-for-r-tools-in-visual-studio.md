---
title: R araçları seçenekleri
description: R dili ve ilişkili özellikler için Visual Studio ' deki seçeneklere yönelik başvuru.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: f3476df66a9ddd11ef7cb7229db8b1f7f15a1a3b
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135750833"
---
# <a name="r-tools-for-visual-studio-options"></a>Visual Studio için R Araçları seçenekleri

Ayarlar, **r araçları**  >  **seçenekleri** menüsüyle veya **araçlar**  >  **seçenekleri** aracılığıyla veya **r araçları**' na kaydırarak erişilir:

  ![R araçları için Seçenekler iletişim kutusu](media/options-dialog.png)

R 'ye özgü seçeneklere ve ayarlara aşağıdaki yöntemler kullanılarak erişilir. Bu bölümlerin tümünün görünmesi için **Seçenekler** iletişim kutusunun altındaki **tüm ayarları göster** kutusunu seçmeniz gerekir.

- Kod biçimlendirme seçenekleri (bkz. [Düzenleyici seçenekleri](editing-r-code-in-visual-studio.md#editor-options): **Araçlar**  >  **Seçenekler** menüsü, sonra **metin düzenleyici**  >  **R**  >  **biçimlendirme** seçimi
- [Linter seçenekleri (bkz.](linting-r-code.md)): **Araçlar**  >  **Seçenekler** menüsü, sonra **metin düzenleyici**  >  **R**  >  **Lint** 'i seçme
- Gelişmiş Düzenleyici seçenekleri ([Bu makalede açıklanan](#text-editor--r--advanced-options)): **Araçlar**  >  **Seçenekler** menüsünde, **metin düzenleyici**  >  **R**  >  **Gelişmiş** ' i seçin
- Davranış seçenekleri ([Bu makalede açıklanan](#r-tools--advanced-options)): **r araçları**  >  **Seçenekler** menüsü veya **Araçlar**  >  **Seçenekler**, ardından **r araçları**' na kaydırın.

**R araçları**  >  **Veri Bilimi Ayarları** komutu ayrıca Visual Studio genel ' de birçok farklı ayarı etkiler. Bu komut, sonraki bölümde açıklanmaktadır.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>R araçları > Veri Bilimi Ayarları

**R araçları > Veri Bilimi Ayarları** menü öğesi, veri bilimcilerinin ihtiyaçları için optimize edilmiş bir düzen ile Visual Studio ıde 'yi yapılandırır. Özellikle, bu seçenek [etkileşimli](interactive-repl-for-r-in-visual-studio.md), [değişken Gezgini](variable-explorer.md)ve [çalışma alanları](r-workspaces-in-visual-studio.md) pencerelerini açar:

![Visual Studio veri bilimcisi pencere düzeni](media/installation-data-scientist-layout-result.png)

daha sonra diğer Visual Studio ayarlarına dönmek için, önce **araçlar**  >  **içeri aktar ve dışarı aktar Ayarlar** komutunu kullanın, **seçili ortam ayarlarını dışarı aktar**' ı seçin ve bir dosya adı belirtin. Bu ayarları geri yüklemek için aynı komutu kullanın ve **Seçili ortam ayarlarını Içeri aktar**' ı seçin. ayrıca, veri bilimconu mizanpajını değiştirirseniz ve daha sonra **Veri Bilimi Ayarları** komutunu kullanmak yerine daha sonra üzerine dönmek isterseniz aynı komutları kullanabilirsiniz.

## <a name="text-editor--r--advanced-options"></a>> R > gelişmiş seçenekleri için metin Düzenleyicisi

Bu seçenekler, R için biçimlendirme, IntelliSense, ana hat, girintileme ve söz dizimi denetimi davranışlarını denetler.

![R metin Düzenleyicisi gelişmiş seçenekleri için Seçenekler iletişim kutusu](media/options-dialog-advanced-text-editor.png)

Her seçenek, söz konusu davranışı denetlemek için açık veya kapalı olarak ayarlanır. Her bir seçeneğin etkilediği Ayrıntılar için iletişim kutusunun altındaki yardım bölmesine bakın. Bölmeyi daha büyük hale getirmek için Yardım bölmesinin en üstünü sürükleyebileceğinizi unutmayın.

![R metin Düzenleyicisi Gelişmiş Seçenekler iletişim kutusunda Genişletilmiş Yardım Bölmesi](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>R araçları > Gelişmiş Seçenekler

**R araçları**  >  **seçenekleri** menü komutu, r seçenekleri için **Seçenekler** iletişim kutusunu açar:

  ![R araçları için Seçenekler iletişim kutusu](media/options-dialog.png)

Aşağıdaki bölümlerde bu sayfada kullanılabilen farklı seçenekler açıklanır.

### <a name="debugging"></a>Hata Ayıklama

Bu seçenekler, [değişken Gezgini](variable-explorer.md) ve Izleme ve Yereller gibi hata ayıklayıcı pencerelerinde değerlerin nasıl işlendiğini denetler (bkz. [Debug R Code](debugging-r-in-visual-studio.md)).

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Etkin bağlamaları değerlendir | `True` | Ne zaman `True` , değişkenlerin ve özelliklerin incelenirken en güncel değeri her zaman görmenizi sağlar. Riskin nasıl uygulandığına bağlı olarak, ifadeleri değerlendirmek yan etkilere neden olabilir. |
| Nokta ön ekli değişkenleri göster | `False` | Ön eki eklenen değişkenlerin gösterilip `.` gösterilmeyeceğini belirtir. |

### <a name="grid-view"></a>Izgara görünümü

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Dinamik değerlendirme | `False` | Varsayılan olarak, `View(<expression>)` işlevi veri çerçevesi olarak verilerin anlık görüntüsünü alır ve bu da büyük veri kümeleriyle önemli miktarda bellek tüketebilir. Bu seçeneğin ayarlanması, `True` kılavuz yalnızca görüntülenen verileri getirmek üzere yenilendiğinde ifadenin değerlendirileceği anlamına gelir. Ancak, ifade verileri değiştirirse, dplyr PIP ifadelerine uygun olmayan değişiklikler de değişir. |

### <a name="help"></a>Help

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| F1 web tarayıcısı | `Internal` | **CTRL** F1 kullanarak bir terimi ararken yardım 'ın nasıl görüntüleneceğini denetler + . Olarak ayarlandığında `Internal` , yardım Visual Studio içindeki bir araç penceresinde işlenir. Olarak ayarlandığında `External` , yardım varsayılan Web tarayıcınızda görüntülenir. |
| F1 Web Araması dizesi | `R site:stackoverflow.com` |  + Düzenleyicideki bir terim üzerinde CTRL **F1** tuşuna bastığınızda arama koşullarının arama altyapısına nasıl geçtiğini denetler. Varsayılan olarak dize, `R site:stackoverflow.com` `R` Arama teriminizi ekler. , Arama `site:stackoverflow.com` altyapısına, bu, etki alanı içindeki sayfalara aramanın kapsamını belirten bir yönergedir `stackoverflow.com` . |
| R Yardım tarayıcısı | `Automatic` | R belgelerini **F1**, **?**, veya **??** kullanarak ararken yardım 'ın nasıl görüntüleneceğini denetler. Olarak ayarlandığında `Automatic` , uygun pencerede yardım işler. örneğin, HTML yardımı bir Visual Studio araç penceresi içinde görünür, ancak pdf 'ler varsayılan pdf programınızda görüntülenir. Olarak ayarlandığında `External` , yardım varsayılan Web tarayıcınızda işlenir. |

### <a name="history"></a>Geçmiş

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Geçmişi her zaman Kaydet | `True` | RTVS 'nin komut geçmişinizi bir öğesine yazıp yazmadığını denetler *.* Çalışma dizininizde her ne zaman bir proje kapatıldığında RHistory dosyası. Sihirbazdan çıkmadan önce projenizi kaydetmeseniz bile geçmiş kaydedilir. |
| Arama filtresini Sıfırla | `True` | Geçmiş penceresinin komut geçmişinizi yalnızca R Geçmiş iletişim kutusunda filtre terimiyle alt dize ile eşleşen komutları gösterecek şekilde filtreleyemeyeceğini belirler. Bu ayar, yeni bir komut çalıştırdığınız veya yeni bir projeye geçiş yaptığınızda geçmiş arama filtreinizin sıfırlanıp sıfırlanmayacağını belirler. Bu, farklı yükü tetikler *. RHistory* dosyası. Varsayılan ayar, `True` filtre kümesi ile bir komut çalıştırdığınızda beklenmedik şekilde en aza indirir ve az önce çalıştırdığınız komutun geçmişte gösterilmediğini merak ettiniz. |
| Çok satırlı seçim kullan | `True` | Tek bir tıklama geçmişi içinde çok satırlı bir deyimin seçip seçmeyeceğinizi belirtir. ayrıca, etkileşimli Windows satırlar yerine deyimlere göre yukarı/aşağı ok gezintisini de mümkün. |

### <a name="html"></a>HTML

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| HTML sayfaları tarayıcısı | `External` | Bir `ggvis` çizim veya bir uygulama gibi içeriğin nerede işleneceğini belirler `shiny` . `Internal`html çıkışını Visual Studio bir araç penceresi içinde gösterir; `External` html çıkışını varsayılan tarayıcınızda görüntüler. |

### <a name="logging"></a>Günlüğe Kaydetme

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Olayları günlüğe kaydet | `Normal` | RTVS tanılaması için kullanılan günlüğün ayrıntı düzeyini denetler. Varsayılan ayarı, `Normal` dizininizde bir günlük dosyası oluşturur `TEMP` . Olarak ayarlandığında `Traffic` , rtvs, tüm komutları ve oturumlarınızda yanıtları günlüğe kaydeder. Bu günlük dosyaları hiçbir şekilde makinenizi bırakmaz, ancak RTVS 'de sorunları tanılamak için faydalı olabilir. |

### <a name="markdown"></a>Markdown

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Markdown önizleme tarayıcısı | `External` | RMarkdown HTML çıkışının nerede görüntülendiğinden belirler. `Internal`bir araç penceresindeki RMarkdown HTML belgesini Visual Studio; varsayılan tarayıcınızı `External` kullanarak RMarkdown HTML'yi görüntüler. |

### <a name="r-engine"></a>R Altyapısı

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Kod sayfası | `(OS Default)` | R için kod sayfasını (yerel ayar) ayarlar. Varsayılan olarak işletim sisteminin temel alınan yerel ayarlarını kullanır. |
| CRAN Mirror | `(Use .Rprofile)` | Paket yüklemeleri için varsayılan CRAN yansıtmasını ayarlar. varsayılan `Use .Rprofile` ayarı, içinde CRAN Mirror ayarlarını *kullanır. RProfile* dosyası. |

### <a name="workspace"></a>Çalışma alanı

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Proje açıldığında çalışma alanını yükleme | `No` | ayarı, `Yes` oturum verilerini 'den yüklemeye olanak *sağlar. Proje* açıldığında genel ortama RData dosyası. |
| Sıfırlamada çalışma alanını kaydetme istemi | `Yes` | olarak `No` ayarı, Etkileşimli Pencere'de Sıfırla düğmesine tıklarsanız çalışma alanınızı kaydetme istemini devre dışı bırakır. |
| Proje kapanıyorken çalışma alanını kaydetme | `No` | olarak `Yes` ayarı, genel ortamın 'a kaydedilene olanak *sağlar. Proje* kapatılan RData dosyası. |
| Çalışma alanlarını değiştirmeden önce onay iletişim kutusunu göster | `Yes` | ayarı, `No` farklı çalışma alanları arasında geçiş sırasında kullanıcıdan onay istemini devre dışı bırakır. Bkz. [Çalışma alanları arasında geçiş](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Makine yükü göstergesini göster | `False` | Durum çubuğunda CPU/Bellek/Ağ yükü göstergesinin görünürlüğünü kontrol eder. Gösterge ağ trafiğine neden olduğundan, bunu uzak tarifeli `False` senaryolarda tutmak yararlı olur. Bu seçeneği değiştirmek için yeniden başlatmanız Visual Studio. |
