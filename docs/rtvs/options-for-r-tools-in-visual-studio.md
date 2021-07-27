---
title: R araçları seçenekleri
description: R dili ve ilişkili Visual Studio seçenekleri için başvuru.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: fc46d7ed1e369d31a9d0675f0595073f51f28d17
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2021
ms.locfileid: "114679791"
---
# <a name="r-tools-for-visual-studio-options"></a>Visual Studio için R Araçları seçenekleri

Ayarlar R Araçları Seçenekleri **menüsünden veya** Araçlar Seçenekleri aracılığıyla ve  >   R   >  **Araçları'ne** kaydırarak **erişebilirsiniz:**

  ![R Araçları için Seçenekler iletişim kutusu](media/options-dialog.png)

R'ye özgü seçeneklere ve ayarlara aşağıdaki yöntemler kullanılarak erişilir. Bu bölümlerin **hepsi için** Seçenekler iletişim  kutusunun en altındaki Tüm ayarları göster kutusunu seçmeniz gerekir.

- Kod biçimlendirme seçenekleri [(bkz. Düzenleyici seçenekleri:](editing-r-code-in-visual-studio.md#editor-options) **Araçlar**  >  **Seçenekler** menüsü ve ardından Metin Düzenleyicisi R   >  **Biçimlendirmesi'ni**  >  **seçin**
- Lint seçenekleri (bkz. [Lint):](linting-r-code.md) **Araçlar**  >  **Seçenekler** menüsü ve ardından **Metin** Düzenleyici R  >    >  **Lint'i seçin**
- Gelişmiş düzenleyici seçenekleri ([bu makalede açıklanmıştır):](#text-editor--r--advanced-options) **Araçlar**  >  **Seçenekler** menüsü ve ardından Metin Düzenleyici   >  **R Gelişmiş'i**  >  **seçin**
- Davranış seçenekleri ([bu makalede açıklanmıştır):](#r-tools--advanced-options) **R Araçları**  >  **Seçenekleri** menüsü veya Araçlar **Seçenekleri'ne**  >  **gidin** ve **R Araçları'ne kaydırın.**

**R Araçları Veri** Bilimi Ayarlar komutu, genel olarak R Tools Veri  >   Bilimi Visual Studio etkiler. Bu komut sonraki bölümde açıklanmıştır.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>R Araçları > Veri Bilimi Ayarlar

R **Tools > Data Science Ayarlar** menü öğesi, Visual Studio IDE'yi veri bilimcilerinin ihtiyaçlarına en iyi duruma getirilmiş bir düzen ile yapılandırıyor. Özel olarak, bu seçenek [Etkileşimli](interactive-repl-for-r-in-visual-studio.md), [Değişken Gezgini](variable-explorer.md)ve Çalışma [Alanları pencerelerini](r-workspaces-in-visual-studio.md) açar:

![Veri bilimcisi pencere düzeni Visual Studio](media/installation-data-scientist-layout-result.png)

Daha sonra diğer Visual Studio geri dönmek için önce Araçlar İçeri ve Dışarı Aktarma Ayarlar komutunu kullanın, Seçili ortam ayarlarını dışarı aktar'ı seçin ve  >   bir dosya adı belirtin.  Bu ayarları geri yüklemek için aynı komutu kullanın ve Seçili ortam ayarlarını **içeri aktar'ı seçin.** Veri bilimcisi düzenini değiştirir ve veri bilimi komutlarını doğrudan kullanmak yerine daha sonra buna geri dönmek için de **aynı Ayarlar** kullanabilirsiniz.

## <a name="text-editor--r--advanced-options"></a>R > Gelişmiş > Metin Düzenleyici

Bu seçenekler, R için biçimlendirme, IntelliSense, satır çizgisi oluşturma, girintileme ve söz dizimi denetimi davranışını kontrol edin.

![R metin düzenleyicisi gelişmiş seçenekleri için Seçenekler iletişim kutusu](media/options-dialog-advanced-text-editor.png)

Söz konusu davranışı kontrol etmek için her seçenek ya on ya da off olarak ayarlanır. Her seçeneğin neleri etkilediği hakkında ayrıntılı bilgi için iletişim kutusunun altındaki yardım bölmesine bakın. Bölmeyi daha büyük hale etmek için bu yardım bölmesinin üst kısmından yukarı sürükleyebilirsiniz.

![R metin düzenleyicisi gelişmiş seçenekler iletişim kutusunda genişletilmiş yardım bölmesi](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>R Araçları > Gelişmiş seçenekler

**R Araçları Seçenekler**  >  **menü** komutu, R **seçeneklerinin** Seçenekler iletişim kutusunu açar:

  ![R Araçları için Seçenekler iletişim kutusu](media/options-dialog.png)

Aşağıdaki bölümlerde bu sayfada kullanılabilen farklı seçenekler açıklanmaktadır.

### <a name="debugging"></a>Hata Ayıklama

Bu seçenekler, değerlerin izleme ve [Değişken Gezgini](variable-explorer.md) ve hata ayıklayıcısı pencerelerinde nasıl işlen olduğunu kontrol eder (bkz. [R kodunda hata ayıklama).](debugging-r-in-visual-studio.md)

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Etkin bağlamaları değerlendirme | `True` | olduğunda, `True` değişkenleri ve özellikleri incelerken her zaman en güncel değeri görmelerini sağlar. Risk, ifadelerin değerlendirilmesi, uygulanma durumuna bağlı olarak yan etkilere neden olabilir. |
| Nokta ön ekli değişkenleri gösterme | `False` | Ön ekli değişkenlerin göster olup `.` olmadığını belirtir. |

### <a name="grid-view"></a>Izgara görünümü

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Dinamik değerlendirme | `False` | Varsayılan olarak işlev, büyük veri kümeleriyle önemli miktarda bellek tüketen bir veri çerçevesi olarak `View(<expression>)` verilerin anlık görüntüsünü alır. Bu seçeneğin olarak ayarlenmesi, yalnızca görüntülenen verileri getirmek için `True` kılavuz yenilendiğinde ifadenin değerlendirilecek olduğu anlamına gelir. Ancak, ifade verileri de değiştirirse dplyr pip ifadeleri için uygun olmayacaktır. |

### <a name="help"></a>Help

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| F1 Web tarayıcısı | `Internal` | **Ctrl** F1 kullanarak bir terim ararken yardımın nasıl + **görüntüleniyor olduğunu kontrol eder.** olarak `Internal` ayarlanırsa, yardım bir araç penceresinde oluşturulur ve Visual Studio. olarak `External` ayarlendiğinde, yardım varsayılan web tarayıcınızda görünür. |
| F1 Web Araması Dizesi | `R site:stackoverflow.com` | Düzenleyicide bir terimde **Ctrl** + **F1** tuşlarına basabilirsiniz. Varsayılan olarak dize, `R site:stackoverflow.com` arama teriminize `R` eklenen dizesidir. `site:stackoverflow.com`, arama altyapısına, arama kapsamını etki alanı içindeki sayfaların kapsamına almalarını söyleyen bir `stackoverflow.com` yönergedir. |
| R Yardım Browser | `Automatic` | R belgelerinde **F1**, **?** veya ?? kullanarak arama kullanırken yardımın nasıl görüntüleniyor **olduğunu kontrol eder.** olarak `Automatic` ayarlanırsa, yardım uygun pencerede işler. Örneğin, HTML yardımı bir Visual Studio penceresinde görünürken PDF'ler varsayılan PDF programınız içinde görünür. olarak `External` ayarlanırsa, yardım varsayılan web tarayıcınızda işlenir. |

### <a name="history"></a>Geçmiş

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Geçmişi her zaman kaydet | `True` | RTVS'nin komut geçmişinizi bir 'a yazıp yazmay olmadığını kontrol *eder. Proje her kapatılan* çalışma dizininize RHistory dosyası. Çıkıştan önce projenizi kaydetmenize rağmen geçmişi kaydetmeniz gerekir. |
| Arama filtresini sıfırlama | `True` | Geçmiş penceresinin komut geçmişinizi yalnızca alt dizenin komut satırı iletişim kutusundaki filtre terimiyle eşan komutları gösterecek şekilde filtreleye R Geçmiş belirler. Bu ayar, yeni bir komut her çalıştırsanız Geçmiş arama filtrenizi sıfırlamayı veya farklı bir 'nin yükünü tetikleyen yeni bir projeye geçmeyi *belirler. RHistory* dosyası. Varsayılan ayarı, filtre kümesiyle bir komut çalıştırarak sürprizi en aza indirger ve az önce çalıştırdınız komutun Neden Geçmiş'te göstere `True` olmadığını merak ediyorsanız. |
| Çok satırlı seçimi kullanma | `True` | Geçmiş'te tek tıklamayla çok satırlı bir deyim seçip seçey tıklamay seçeneklerden biri olup olmadığını belirtir. Ayrıca Etkileşimli gezinti bölmesinde satırlar yerine deyimlere Windows yukarı/aşağı ok gezintisi sağlar. |

### <a name="html"></a>HTML

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| HTML Sayfaları tarayıcısı | `External` | Çizim veya uygulama gibi içeriğin `ggvis` nerede `shiny` işleneceklerini belirler. `Internal`bir araç penceresi içinde HTML çıkışını Visual Studio; `External`varsayılan tarayıcınızda HTML çıktısını görüntüler. |

### <a name="logging"></a>Günlüğe Kaydetme

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Günlük olayları | `Normal` | RTVS tanılaması için kullanılan günlük kaydının ayrıntılılık düzeyini kontrol eder. varsayılan `Normal` ayarı, dizininize bir günlük dosyası `TEMP` oluşturur. olarak `Traffic` ayarlanırsa RTVS, oturumda tüm komutları ve yanıtları günlüğe kaydeder. Bu günlük dosyaları makinenizi asla bırakmaz, ancak RTVS'deki sorunları tanılamak için yararlı olabilir. |

### <a name="markdown"></a>Markdown

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Markaşağı Önizleme tarayıcısı | `External` | Rmarkin HTML çıktısının görüntülendiğini belirler. `Internal`Visual Studio; bir araç penceresi içinde Rmarkeshtml belgesi gösterir; `External`varsayılan tarayıcınızı kullanarak Rmarkaşağı HTML görüntüler. |

### <a name="r-engine"></a>R altyapısı

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Kod sayfası | `(OS Default)` | R için kod sayfasını (yerel ayar) ayarlar. Varsayılan olarak, işletim sisteminin temel alınan yerel ayarını kullanır. |
| CRAN yansıtması | `(Use .Rprofile)` | Paket yüklemeleri için varsayılan CRAN yansıtmasını ayarlar. Varsayılan ayar, `Use .Rprofile` CRAN yansıtma ayarlarını sizin için varsayılan ayardır *. RProfile* dosyası. |

### <a name="workspace"></a>Çalışma alanı

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Proje açıldığında çalışma alanını yükle | `No` | İçin ayarı `Yes` , oturum verilerinin içinden yüklenmesini sağlar *. Proje açıldığında RData* dosyası genel ortama. |
| Sıfırlama sırasında çalışma alanını kaydetmek için sor | `Yes` | `No`Etkileşimli penceredeki Sıfırla düğmesine tıkladığınızda çalışma alanınızı kaydetme istemini devre dışı bırakmak için ayarı. |
| Proje kapandığında çalışma alanını Kaydet | `No` | İçin ayarı `Yes` , genel ortamın öğesine kaydedilmesini sağlar *. Proje kapatıldığında RData* dosyası. |
| Çalışma alanlarını değiştirmeden önce onay iletişim kutusunu göster | `Yes` | İçin ayarı `No` , farklı çalışma alanları arasında geçiş yaparken kullanıcıya onay sorulmasını devre dışı bırakır. Bkz. [çalışma alanları arasında geçiş](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Makine yük göstergesini göster | `False` | Durum çubuğundaki CPU/bellek/ağ yükü göstergesinin görünürlüğünü denetler. Gösterge ağ trafiği oluşturduğundan, bunu `False` uzak tarifeli senaryolarda tutmak yararlı olur. Bu seçeneğin değiştirilmesi Visual Studio yeniden başlatmanızı gerektirir. |
