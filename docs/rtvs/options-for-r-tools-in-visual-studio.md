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
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c7c2cb57dc96d7bb0df09248eb7a877820e50521
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409675"
---
# <a name="r-tools-for-visual-studio-options"></a>Visual Studio için R Araçları seçenekleri

Ayarlar **r araçları** > **seçenekleri** menüsüyle veya **Araçlar** > **Seçenekler** aracılığıyla veya **R araçları**' na kaydırılırken erişilir:

  ![R araçları için Seçenekler iletişim kutusu](media/options-dialog.png)

R 'ye özgü seçeneklere ve ayarlara aşağıdaki yöntemler kullanılarak erişilir. Bu bölümlerin tümünün görünmesi için **Seçenekler** iletişim kutusunun altındaki **tüm ayarları göster** kutusunu seçmeniz gerekir.

- Kod biçimlendirme seçenekleri (bkz. [Düzenleyici seçenekleri](editing-r-code-in-visual-studio.md#editor-options): **Araçlar** > **Seçenekler** menüsü, sonra **metin düzenleyici** > **R** > **biçimlendirme**
- [Linter seçenekleri (bkz.](linting-r-code.md)): **Araçlar** > **Seçenekler** menüsü, sonra **metin düzenleyici** > **R** > **Lint**
- Gelişmiş Düzenleyici seçenekleri ([Bu makalede açıklanan](#text-editor--r--advanced-options)): **Araçlar** > **Seçenekler** menüsü, sonra **metin düzenleyici** > **R** > **Gelişmiş**
- Davranış seçenekleri ([Bu makalede açıklanan](#r-tools--advanced-options)): **r araçları** > **seçenekleri** menüsü veya **Araçlar** > **Seçenekler**ve ardından **R araçları**' na kaydırın.

**R araçları** > **veri bilimi ayarları** komutu aynı zamanda Visual Studio 'daki birçok farklı ayarı da etkiler. Bu komut, sonraki bölümde açıklanmaktadır.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>R araçları > Veri Bilimi Ayarları

**R araçları > veri bilimi ayarları** menü öğesi, VISUAL Studio IDE 'yi veri bilimcilerinin ihtiyaçları için en iyi duruma getirilmiş bir düzen ile yapılandırır. Özellikle, bu seçenek [etkileşimli](interactive-repl-for-r-in-visual-studio.md), [değişken Gezgini](variable-explorer.md)ve [çalışma alanları](r-workspaces-in-visual-studio.md) pencerelerini açar:

![Visual Studio 'da veri bilimcisi pencere düzeni](media/installation-data-scientist-layout-result.png)

Daha sonra diğer Visual Studio ayarlarına dönmek için, önce **ayarları Içeri aktar ve dışarı aktar** **komutunu > ,** **Seçili ortam ayarlarını dışarı aktar**' ı seçin ve bir dosya adı belirtin. Bu ayarları geri yüklemek için aynı komutu kullanın ve **Seçili ortam ayarlarını Içeri aktar**' ı seçin. Ayrıca, veri bilimconu mizanpajını değiştirirseniz ve daha sonra **veri bilimi ayarları** komutunu kullanmak yerine daha sonra üzerine dönmek isterseniz aynı komutları kullanabilirsiniz.

## <a name="text-editor--r--advanced-options"></a>> R > Gelişmiş seçenekleri için metin Düzenleyicisi

Bu seçenekler, R için biçimlendirme, IntelliSense, ana hat, girintileme ve söz dizimi denetimi davranışlarını denetler.

![R metin Düzenleyicisi gelişmiş seçenekleri için Seçenekler iletişim kutusu](media/options-dialog-advanced-text-editor.png)

Her seçenek, söz konusu davranışı denetlemek için açık veya kapalı olarak ayarlanır. Her bir seçeneğin etkilediği Ayrıntılar için iletişim kutusunun altındaki yardım bölmesine bakın. Bölmeyi daha büyük hale getirmek için Yardım bölmesinin en üstünü sürükleyebileceğinizi unutmayın.

![R metin Düzenleyicisi Gelişmiş Seçenekler iletişim kutusunda Genişletilmiş Yardım Bölmesi](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>R araçları > Gelişmiş Seçenekler

**R araçları** > **seçenekleri** menü komutu, r seçenekleri için **Seçenekler** iletişim kutusunu açar:

  ![R araçları için Seçenekler iletişim kutusu](media/options-dialog.png)

Aşağıdaki bölümlerde bu sayfada kullanılabilen farklı seçenekler açıklanır.

### <a name="debugging"></a>Hata ayıklama

Bu seçenekler, [değişken Gezgini](variable-explorer.md) ve Izleme ve Yereller gibi hata ayıklayıcı pencerelerinde değerlerin nasıl işlendiğini denetler (bkz. [Debug R Code](debugging-r-in-visual-studio.md)).

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Etkin bağlamaları değerlendir | `True` | `True`, değişkenlerin ve özelliklerin incelenirken en güncel değeri her zaman görmenizi sağlar. Riskin nasıl uygulandığına bağlı olarak, ifadeleri değerlendirmek yan etkilere neden olabilir. |
| Nokta ön ekli değişkenleri göster | `False` | `.` ön eki eklenmiş değişkenlerin gösterilip gösterilmeyeceğini belirtir. |

### <a name="grid-view"></a>Izgara görünümü

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Dinamik değerlendirme | `False` | Varsayılan olarak `View(<expression>)` işlevi, verilerin bir anlık görüntüsünü veri çerçevesi olarak alır ve bu da büyük veri kümeleriyle önemli miktarda bellek tüketebilir. Bu seçeneğin `True` ayarlanması, kılavuz yalnızca görüntülenen verileri getirmek üzere yenilendiğinde ifadenin değerlendirileceği anlamına gelir. Ancak, ifade verileri değiştirirse, dplyr PIP ifadelerine uygun olmayan değişiklikler de değişir. |

### <a name="help"></a>Yardım

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| F1 web tarayıcısı | `Internal` | **Ctrl**+**F1**kullanarak bir terimi ararken yardım 'ın nasıl görüntüleneceğini denetler. `Internal`olarak ayarlandığında, yardım, Visual Studio 'daki bir araç penceresi içinde işlenir. `External`olarak ayarlandığında, yardım varsayılan Web tarayıcınızda görüntülenir. |
| F1 Web Araması dizesi | `R site:stackoverflow.com` | Düzenleyicideki bir terim üzerinde **Ctrl**+**F1** tuşlarına bastığınızda arama koşullarının arama altyapısına nasıl geçtiğini denetler. Varsayılan olarak dize, arama teriminizi `R` ekler `R site:stackoverflow.com`. `site:stackoverflow.com`, arama motoruna, aramanın `stackoverflow.com` etki alanındaki sayfalara kapsamını nasıl göndereceğini söyleyen bir yönergedir. |
| R Yardım tarayıcısı | `Automatic` | R belgelerini **F1**, **?** , veya **??** kullanarak ararken yardım 'ın nasıl görüntüleneceğini denetler. `Automatic`olarak ayarlandığında, ilgili pencerede yardım işler. Örneğin, HTML Yardımı bir Visual Studio araç penceresi içinde görünür, ancak PDF 'Ler varsayılan PDF programınızda görüntülenir. `External`olarak ayarlandığında, yardım varsayılan Web tarayıcınızda işlenir. |

### <a name="history"></a>Geçmiş

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Geçmişi her zaman Kaydet | `True` | RTVS 'nin komut geçmişinizi bir öğesine yazıp yazmadığını denetler *.* Çalışma dizininizde her ne zaman bir proje kapatıldığında RHistory dosyası. Sihirbazdan çıkmadan önce projenizi kaydetmeseniz bile geçmiş kaydedilir. |
| Arama filtresini Sıfırla | `True` | Geçmiş penceresinin komut geçmişinizi yalnızca R Geçmiş iletişim kutusunda filtre terimiyle alt dize ile eşleşen komutları gösterecek şekilde filtreleyemeyeceğini belirler. Bu ayar, yeni bir komut çalıştırdığınız veya yeni bir projeye geçiş yaptığınızda geçmiş arama filtreinizin sıfırlanıp sıfırlanmayacağını belirler. Bu, farklı yükü tetikler *. RHistory* dosyası. Filtre kümesi ile bir komut çalıştırdığınızda `True` varsayılan ayarı aniden en aza indirir ve az önce çalıştırdığınız komutun geçmişte gösterilmediğini merak ettiniz. |
| Çok satırlı seçim kullan | `True` | Tek bir tıklama geçmişi içinde çok satırlı bir deyimin seçip seçmeyeceğinizi belirtir. Ayrıca, satırlarda değil, etkileşimli pencerelerin deyimlerini izleyerek yukarı/aşağı ok gezintisini de mümkün. |

### <a name="html"></a>HTML

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| HTML sayfaları tarayıcısı | `External` | `ggvis` çizimi gibi içeriğin veya `shiny` uygulamasının nerede işleneceğini belirler. `Internal`, HTML çıkışını Visual Studio 'daki bir araç penceresi içinde gösterir; `External` HTML çıkışını varsayılan tarayıcınızda görüntüler. |

### <a name="logging"></a>Günlüğe kaydetme

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Olayları günlüğe kaydet | `Normal` | RTVS tanılaması için kullanılan günlüğün ayrıntı düzeyini denetler. `Normal` varsayılan ayarı `TEMP` dizininizde bir günlük dosyası oluşturur. `Traffic`olarak ayarlandığında, RTVS, tüm komutları ve oturumlarınızda yanıtları günlüğe kaydeder. Bu günlük dosyaları hiçbir şekilde makinenizi bırakmaz, ancak RTVS 'de sorunları tanılamak için faydalı olabilir. |

### <a name="markdown"></a>Markdown

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Markaşağı Önizleme tarayıcısı | `External` | Rmarkin HTML çıktısının görüntülendiğini belirler. `Internal`, Rmarkaşağı HTML belgesini Visual Studio 'daki bir araç penceresi içinde gösterir; `External` varsayılan tarayıcınızı kullanarak Rmarkaşağı HTML 'yi görüntüler. |

### <a name="r-engine"></a>R altyapısı

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Kod sayfası | `(OS Default)` | R için kod sayfasını (yerel ayar) ayarlar. Varsayılan olarak, işletim sisteminin temel alınan yerel ayarını kullanır. |
| CRAN yansıtması | `(Use .Rprofile)` | Paket yüklemeleri için varsayılan CRAN yansıtmasını ayarlar. `Use .Rprofile` varsayılan ayarı, içindeki CRAN yansıtma ayarlarını duyar *. RProfile* dosyası. |

### <a name="workspace"></a>Çalışma alanı

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Proje açıldığında çalışma alanını yükle | `No` | `Yes` ayarı, oturum verilerinin içinden yüklenmesini sağlar *. Proje açıldığında RData* dosyası genel ortama. |
| Sıfırlama sırasında çalışma alanını kaydetmek için sor | `Yes` | `No` ayarı, etkileşimli penceredeki Sıfırla düğmesine tıkladığınızda çalışma alanınızın kaydedilmesini istemeden devre dışı bırakır. |
| Proje kapandığında çalışma alanını Kaydet | `No` | `Yes` ayarı, genel ortamın öğesine kaydedilmesini sağlar *. Proje kapatıldığında RData* dosyası. |
| Çalışma alanlarını değiştirmeden önce onay iletişim kutusunu göster | `Yes` | `No` ayarı, farklı çalışma alanları arasında geçiş yaparken kullanıcıya onay sorulmasını devre dışı bırakır. Bkz. [çalışma alanları arasında geçiş](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Makine yük göstergesini göster | `False` | Durum çubuğundaki CPU/bellek/ağ yükü göstergesinin görünürlüğünü denetler. Gösterge ağ trafiği oluşturduğundan bu `False` uzak ölçümlü senaryolarda tutmanız yararlı olur. Bu seçeneğin değiştirilmesi, Visual Studio 'Yu yeniden başlatmanızı gerektirir. |
