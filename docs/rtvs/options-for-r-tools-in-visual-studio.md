---
title: R araçları seçenekleri
description: R dili ve ilişkili özellikler için Visual Studio seçeneklerine yönelik başvuru.
ms.date: 12/04/2017
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: ed2ee29fb7a0a832dd3076cbd47a7f9cd1414d96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939480"
---
# <a name="r-tools-for-visual-studio-options"></a>Visual Studio için R Araçları seçenekleri

Ayarlar **r araçları**  >  **Seçenekler** menüsüyle veya **Araçlar**  >  **seçenekleri** aracılığıyla veya **r araçları**' na kaydırılırken erişilir:

  ![R araçları için Seçenekler iletişim kutusu](media/options-dialog.png)

R 'ye özgü seçeneklere ve ayarlara aşağıdaki yöntemler kullanılarak erişilir. Bu bölümlerin tümünün görünmesi için **Seçenekler** iletişim kutusunun altındaki **tüm ayarları göster** kutusunu seçmeniz gerekir.

- Kod biçimlendirme seçenekleri (bkz. [Düzenleyici seçenekleri](editing-r-code-in-visual-studio.md#editor-options): **Araçlar**  >  **Seçenekler** menüsü, sonra **metin düzenleyici**  >  **R**  >  **biçimlendirme** seçimi
- [Linter seçenekleri (bkz.](linting-r-code.md)): **Araçlar**  >  **Seçenekler** menüsü, sonra **metin düzenleyici**  >  **R**  >  **Lint** 'i seçme
- Gelişmiş Düzenleyici seçenekleri ([Bu makalede açıklanan](#text-editor--r--advanced-options)): **Araçlar**  >  **Seçenekler** menüsünde, **metin düzenleyici**  >  **R**  >  **Gelişmiş** ' i seçin
- Davranış seçenekleri ([Bu makalede açıklanan](#r-tools--advanced-options)): **r araçları**  >  **Seçenekler** menüsü veya **Araçlar**  >  **Seçenekler**, ardından **r araçları**' na kaydırın.

**R araçları**  >  **veri bilimi ayarları** komutu aynı zamanda Visual Studio 'daki birçok farklı ayarı da etkiler. Bu komut, sonraki bölümde açıklanmaktadır.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>R araçları > Veri Bilimi Ayarları

**R araçları > veri bilimi ayarları** menü öğesi, VISUAL Studio IDE 'yi veri bilimcilerinin ihtiyaçları için en iyi duruma getirilmiş bir düzen ile yapılandırır. Özellikle, bu seçenek [etkileşimli](interactive-repl-for-r-in-visual-studio.md), [değişken Gezgini](variable-explorer.md)ve [çalışma alanları](r-workspaces-in-visual-studio.md) pencerelerini açar:

![Visual Studio 'da veri bilimcisi pencere düzeni](media/installation-data-scientist-layout-result.png)

Daha sonra diğer Visual Studio ayarlarına daha sonra dönmek için, önce **Araçlar**  >  **içeri ve dışarı aktarma ayarları** komutunu kullanın, **Seçili ortam ayarlarını dışarı aktar**' ı seçin ve bir dosya adı belirtin. Bu ayarları geri yüklemek için aynı komutu kullanın ve **Seçili ortam ayarlarını Içeri aktar**' ı seçin. Ayrıca, veri bilimconu mizanpajını değiştirirseniz ve daha sonra **veri bilimi ayarları** komutunu kullanmak yerine daha sonra üzerine dönmek isterseniz aynı komutları kullanabilirsiniz.

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

### <a name="help"></a>Yardım

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| F1 web tarayıcısı | `Internal` | **CTRL** F1 kullanarak bir terimi ararken yardım 'ın nasıl görüntüleneceğini denetler + . Olarak ayarlandığında `Internal` , yardım, Visual Studio 'daki bir araç penceresi içinde işlenir. Olarak ayarlandığında `External` , yardım varsayılan Web tarayıcınızda görüntülenir. |
| F1 Web Araması dizesi | `R site:stackoverflow.com` |  + Düzenleyicideki bir terim üzerinde CTRL **F1** tuşuna bastığınızda arama koşullarının arama altyapısına nasıl geçtiğini denetler. Varsayılan olarak dize, `R site:stackoverflow.com` `R` Arama teriminizi ekler. , Arama `site:stackoverflow.com` altyapısına, bu, etki alanı içindeki sayfalara aramanın kapsamını belirten bir yönergedir `stackoverflow.com` . |
| R Yardım tarayıcısı | `Automatic` | R belgelerini **F1**, **?**, veya **??** kullanarak ararken yardım 'ın nasıl görüntüleneceğini denetler. Olarak ayarlandığında `Automatic` , uygun pencerede yardım işler. Örneğin, HTML Yardımı bir Visual Studio araç penceresi içinde görünür, ancak PDF 'Ler varsayılan PDF programınızda görüntülenir. Olarak ayarlandığında `External` , yardım varsayılan Web tarayıcınızda işlenir. |

### <a name="history"></a>Geçmiş

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Geçmişi her zaman Kaydet | `True` | RTVS 'nin komut geçmişinizi bir öğesine yazıp yazmadığını denetler *.* Çalışma dizininizde her ne zaman bir proje kapatıldığında RHistory dosyası. Sihirbazdan çıkmadan önce projenizi kaydetmeseniz bile geçmiş kaydedilir. |
| Arama filtresini Sıfırla | `True` | Geçmiş penceresinin komut geçmişinizi yalnızca R Geçmiş iletişim kutusunda filtre terimiyle alt dize ile eşleşen komutları gösterecek şekilde filtreleyemeyeceğini belirler. Bu ayar, yeni bir komut çalıştırdığınız veya yeni bir projeye geçiş yaptığınızda geçmiş arama filtreinizin sıfırlanıp sıfırlanmayacağını belirler. Bu, farklı yükü tetikler *. RHistory* dosyası. Varsayılan ayar, `True` filtre kümesi ile bir komut çalıştırdığınızda beklenmedik şekilde en aza indirir ve az önce çalıştırdığınız komutun geçmişte gösterilmediğini merak ettiniz. |
| Çok satırlı seçim kullan | `True` | Tek bir tıklama geçmişi içinde çok satırlı bir deyimin seçip seçmeyeceğinizi belirtir. Ayrıca, satırlarda değil, etkileşimli pencerelerin deyimlerini izleyerek yukarı/aşağı ok gezintisini de mümkün. |

### <a name="html"></a>HTML

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| HTML sayfaları tarayıcısı | `External` | Bir `ggvis` çizim veya bir uygulama gibi içeriğin nerede işleneceğini belirler `shiny` . `Internal` HTML çıkışını Visual Studio 'daki bir araç penceresi içinde gösterir; `External` HTML çıkışını varsayılan tarayıcınızda görüntüler. |

### <a name="logging"></a>Günlüğe Kaydetme

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Olayları günlüğe kaydet | `Normal` | RTVS tanılaması için kullanılan günlüğün ayrıntı düzeyini denetler. Varsayılan ayarı, `Normal` dizininizde bir günlük dosyası oluşturur `TEMP` . Olarak ayarlandığında `Traffic` , rtvs, tüm komutları ve oturumlarınızda yanıtları günlüğe kaydeder. Bu günlük dosyaları hiçbir şekilde makinenizi bırakmaz, ancak RTVS 'de sorunları tanılamak için faydalı olabilir. |

### <a name="markdown"></a>Markdown

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Markaşağı Önizleme tarayıcısı | `External` | Rmarkin HTML çıktısının görüntülendiğini belirler. `Internal` Visual Studio 'da bir araç penceresi içinde Rmarkeshtml belgesi gösterir; `External` varsayılan tarayıcınızı kullanarak Rmarkaşağı HTML görüntüler. |

### <a name="r-engine"></a>R altyapısı

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Kod sayfası | `(OS Default)` | R için kod sayfasını (yerel ayar) ayarlar. Varsayılan olarak, işletim sisteminin temel alınan yerel ayarını kullanır. |
| CRAN yansıtması | `(Use .Rprofile)` | Paket yüklemeleri için varsayılan CRAN yansıtmasını ayarlar. Varsayılan ayar, `Use .Rprofile` CRAN yansıtma ayarlarını sizin için varsayılan ayardır *. RProfile* dosyası. |

### <a name="workspace"></a>Çalışma alanı

| Seçenek | Varsayılan değer | Description |
| --- | --- | --- |
| Proje açıldığında çalışma alanını yükle | `No` | İçin ayarı `Yes` , oturum verilerinin içinden yüklenmesini sağlar *. Proje açıldığında RData* dosyası genel ortama. |
| Sıfırlama sırasında çalışma alanını kaydetmek için sor | `Yes` | `No`Etkileşimli penceredeki Sıfırla düğmesine tıkladığınızda çalışma alanınızı kaydetme istemini devre dışı bırakmak için ayarı. |
| Proje kapandığında çalışma alanını Kaydet | `No` | İçin ayarı `Yes` , genel ortamın öğesine kaydedilmesini sağlar *. Proje kapatıldığında RData* dosyası. |
| Çalışma alanlarını değiştirmeden önce onay iletişim kutusunu göster | `Yes` | İçin ayarı `No` , farklı çalışma alanları arasında geçiş yaparken kullanıcıya onay sorulmasını devre dışı bırakır. Bkz. [çalışma alanları arasında geçiş](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Makine yük göstergesini göster | `False` | Durum çubuğundaki CPU/bellek/ağ yükü göstergesinin görünürlüğünü denetler. Gösterge ağ trafiği oluşturduğundan, bunu `False` uzak tarifeli senaryolarda tutmak yararlı olur. Bu seçeneğin değiştirilmesi, Visual Studio 'Yu yeniden başlatmanızı gerektirir. |
