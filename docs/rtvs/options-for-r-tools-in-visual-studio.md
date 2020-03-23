---
title: R araçları seçenekleri
description: R dili ve ilişkili özellikler için Visual Studio'daki seçenekler için başvuru.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302709"
---
# <a name="r-tools-for-visual-studio-options"></a>Visual Studio seçenekleri için R Araçları

Ayarlara **R Araçları** > **Seçenekleri** menüsünden veya **Araçlar** > **Seçenekleri'nden** ve **R Tools'a**kaydırma yoluyla erişilir:

  ![R Araçları için seçenekler iletişim kutusu](media/options-dialog.png)

R'ye özgü seçeneklere ve ayarlara aşağıdaki yöntemler kullanılarak erişilir. Tüm bu bölümlerin görünmesi için **Seçenekler** iletişim kutusunun altındaki **tüm ayarları göster** kutusunu seçmeniz gerekir.

- Kod biçimlendirme seçenekleri (bkz. [Editör seçenekleri](editing-r-code-in-visual-studio.md#editor-options): **Araçlar** > **Seçenekleri** menüsü, ardından Metin**Düzenleyicisi** >  **Text Editor** > R**Biçimlendirme'yi** seçin
- Linter seçenekleri [(bkz. Linting):](linting-r-code.md) **Araçlar** > **Seçenekleri** menüsü, ardından **Metin Düzenleyicisi** > **R** > **Lint'i** seçin
- Gelişmiş düzenleyici seçenekleri ([bu makalede açıklanan](#text-editor--r--advanced-options)): **Araçlar** > **Seçenekleri** menüsü, sonra **Metin Düzenleyicisi** > **R** > **Advanced** seçin
- Davranışsal seçenekler[(bu makalede açıklanan):](#r-tools--advanced-options) **R Araçları** > **Seçenekleri** menüsü veya **Araçlar** > **Seçenekleri,** sonra **R Tools'a**kaydırın.

**R Tools** > **Veri Bilimi Ayarları** komutu, Visual Studio'daki genel olarak birçok farklı ayarı da etkiler. Bu komut sonraki bölümde açıklanmıştır.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>Veri Bilimi Ayarları> R Araçları

**R Tools > Veri Bilimi Ayarları** menü öğesi Visual Studio IDE'yi veri bilimcilerin ihtiyaçlarına göre optimize edilmiş bir düzenle yapılandırır. Özellikle, bu seçenek [Etkileşimli,](interactive-repl-for-r-in-visual-studio.md) [Değişken Gezgin](variable-explorer.md)ve Çalışma [Alanları](r-workspaces-in-visual-studio.md) pencerelerini açar:

![Visual Studio'da veri bilimci pencere düzeni](media/installation-data-scientist-layout-result.png)

Daha sonra diğer Visual Studio ayarlarına dönmek için önce **Araçlar** > **İçe Ve Dışa Aktar Ayarlarını** komutunu kullanın, **seçili ortam ayarlarını dışa**aktar'ı seçin ve bir dosya adı belirtin. Bu ayarları geri yüklemek için aynı komutu kullanın ve **seçili ortam ayarlarını içe aktar'ı**seçin. Veri bilimcisi düzenini değiştirmek ve doğrudan **Veri Bilimi Ayarları** komutunu kullanmak yerine daha sonra dönmek istiyorsanız, aynı komutları da kullanabilirsiniz.

## <a name="text-editor--r--advanced-options"></a>Metin Editörü > R > Gelişmiş seçenekler

Bu seçenekler biçimlendirme, IntelliSense, anahat oluşturma, girintisi ve R için sözdizimi denetimi davranışını denetler.

![R metin düzenleyicisi gelişmiş seçenekleri için seçenekler iletişim kutusu](media/options-dialog-advanced-text-editor.png)

Her seçenek, söz konusu davranışı denetlemek için aç Veya kapalı olarak ayarlanır. Her seçeneğin neleri etkilediğine ilişkin ayrıntılar için iletişim kutusunun altındaki yardım bölmesine bakın. Bölmeyi büyütmek için bu yardım bölmesinin üst kısmını sürükleyebileceğinizi unutmayın.

![R metin düzenleyicisi gelişmiş seçenekler iletişim kutusunda genişletilmiş yardım bölmesi](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>Gelişmiş seçenekler > R Araçları

**R Araçları** > **Seçenekleri** menüsü komutu **Seçenekler** iletişim kutusunu R seçeneklerine açar:

  ![R Araçları için seçenekler iletişim kutusu](media/options-dialog.png)

Aşağıdaki bölümlerde bu sayfada bulunan farklı seçenekler açıklayınız.

### <a name="debugging"></a>Hata ayıklama

Bu [seçenekler, Değişken Gezgini'nde](variable-explorer.md) ve Watch ve Locals gibi hata ayıklayıcı pencerelerinde değerlerin nasıl işleneceğini denetler (bkz. [Hata Ayıklama R kodu).](debugging-r-in-visual-studio.md)

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Etkin bağlamaları değerlendirme | `True` | Değişkenleri `True`ve özellikleri incelerken her zaman en güncel değeri görmenizi sağlar. Risk, ifadelerin değerlendirilmesinin nasıl uygulandığına bağlı olarak yan etkilere yol açabileceğidir. |
| Nokta önceden belirlenmiş değişkenleri göster | `False` | Önceden belirlenmiş değişkenlerin gösterip `.` gösterilmediğini belirtir. |

### <a name="grid-view"></a>Izgara görünümü

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Dinamik değerlendirme | `False` | Varsayılan olarak, `View(<expression>)` işlev büyük veri kümeleri ile önemli bellek tüketebilir bir veri çerçevesi olarak veri anlık alır. Bu seçeneğin `True` ayarlanması, Kılavuz yalnızca görüntülenen verileri almak için yenilendiğinde ifadenin değerlendirildiği anlamına gelir. Ancak, ifade değişirse, dplyr pip ifadeleri için uygun olmayan veriler de değişir. |

### <a name="help"></a>Yardım

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| F1 Web tarayıcısı | `Internal` | **Ctrl**+**F1**kullanarak bir terim ararken yardımın nasıl görüntüleneceğini denetler. `Internal`Ayarlandığınızda, yardım Visual Studio'daki bir araç penceresi içinde işlenir. Varsayılan web `External`tarayıcınızda yardım olarak ayarlandığında görünür. |
| F1 Web Arama Dizesi | `R site:stackoverflow.com` | Editördeki bir terimde **Ctrl**+**F1** tuşuna bastığınızda arama terimlerinin arama motorunuza nasıl geçirildiğini denetler. Varsayılan olarak dize, arama `R` teriminize ekleyen dizedir. `R site:stackoverflow.com` Arama `site:stackoverflow.com` motoruna, aramayı `stackoverflow.com` etki alanındaki sayfalara kapsamını söyleyen bir yönergedir. |
| R Yardım Tarayıcısı | `Automatic` | **F1**, **? ,** veya **??** kullanarak R belgelerinde arama yaparken yardımın nasıl görüntüleneceğini denetler. `Automatic`Ayarlandığında, uygun pencerede işler yardım. Örneğin, HTML yardımı Visual Studio araç penceresinde görünürken, PDF'ler varsayılan PDF programınızda görünür. `External`Ayarlandığında, yardım varsayılan web tarayıcınızda işlenir. |

### <a name="history"></a>Geçmiş

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Her zaman geçmişi kaydet | `True` | RTVS'nin komut geçmişinizi bir 'e yazıp yazmadığını *denetler. *Proje kapatıldığında çalışma dizininizdeki RHistory dosyası. Projenizi çıkmadan önce kaydetmeseniz bile geçmişi kaydetmek gerçekleşir. |
| Arama filtresini sıfırla | `True` | Geçmiş penceresinin yalnızca R Geçmişi iletişim kutusundaki filtre terimiyle eşleşen alt dize komutlarını göstermek için komut geçmişinize filtre uygulayıp filtrelemeyeceğini belirler. Bu ayar, yeni bir komut çalıştırdığınızda geçmiş arama filtrenizi sıfırlayıp sıfırlamayacağınızı veya farklı bir projenin yükünü tetikleyen yeni bir projeye geçiş yapıp yapmayı belirler. * RHistory* dosyası. Varsayılan ayar, `True` filtre kümesi olan bir komutu çalıştırdığınızda sürprizi en aza indirir ve çalıştırdığınız komutun Neden Tarih'te görünmediğini merak edeyim. |
| Çok satırlı seçimi kullanma | `True` | Tek bir tıklamayla Tarihçe'de çok satırlı bir deyim seçip seçemeyeceğiniz belirtilir. Ayrıca, Etkileşimli Windows'da satıryerine ifadelere göre yukarı/aşağı ok gezintisi sağlar. |

### <a name="html"></a>HTML

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| HTML Sayfaları tarayıcısı | `External` | `ggvis` Çizim veya `shiny` uygulama gibi içeriğin nerede işlenmeli olduğunu belirler. `Internal`Visual Studio'da bir araç penceresi içinde HTML çıktısını gösterir; `External` varsayılan tarayıcınızda HTML çıktısını görüntüler. |

### <a name="logging"></a>Günlüğe kaydetme

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Günlük olayları | `Normal` | RTVS tanılama için kullanılan günlük ayrıntılılığını denetler. Varsayılan ayar, `Normal` dizininizde `TEMP` bir günlük dosyası oluşturur. `Traffic`Ayarlandığında, RTVS oturumunuzdaki tüm komutları ve yanıtları kaydeder. Bu günlük dosyaları makinenizden asla ayrılmaz, ancak RTVS'deki sorunları tanılamanız için yararlı olabilir. |

### <a name="markdown"></a>Markdown

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Markdown önizleme tarayıcısı | `External` | RMarkdown HTML çıktının nerede görüntüleneceğini belirler. `Internal`Visual Studio'daki bir araç penceresinde RMarkdown HTML belgesini gösterir; `External` varsayılan tarayıcınızı kullanarak RMarkdown HTML görüntüler. |

### <a name="r-engine"></a>R Motoru

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Kod sayfası | `(OS Default)` | R için kod sayfasını (yerel ayar) ayarlar. Varsayılan olarak, işletim sisteminin temel yerel sini kullanır. |
| CRAN Ayna | `(Use .Rprofile)` | Paket yüklemeleri için varsayılan CRAN aynasını ayarlar. Varsayılan ayar, `Use .Rprofile` cran ayna ayarlarına saygı *gösterir. RProfile* dosyası. |

### <a name="workspace"></a>Çalışma alanı

| Seçenek | Varsayılan değer | Açıklama |
| --- | --- | --- |
| Proje açıldığında çalışma alanını yükleme | `No` | Oturum `Yes` verilerinin 'den yüklenmesine olanak sağlayacak *ayar. Proje* açıldığında Küresel ortama RData dosyası. |
| Sıfırlamada çalışma alanını kaydetmek için komut istemi | `Yes` | Etkileşimli `No` Pencere'deki Sıfırla düğmesini tıklattığınızda çalışma alanınızı kaydetmenizi isteyen devre dışı bırakışlar ayarlayın. |
| Proje kapandığında çalışma alanından tasarruf edin | `No` | Küresel `Yes` ortamın ' a kaydedilmesini sağlayacak *ayarı. *Proje kapatıldığında RData dosyası. |
| Çalışma alanlarını değiştirmeden önce onay iletişim kutusunu göster | `Yes` | Farklı `No` çalışma alanları arasında geçiş yaparken kullanıcıdan onay istenmesini isteyen devre dışı kalım ayarlaması. Bkz. [Çalışma Alanları Arasında Geçiş](r-workspaces-in-visual-studio.md#switch-between-workspaces) |
| Makine yük göstergesini göster | `False` | Durum çubuğundaki CPU/Bellek/Ağ yük göstergesinin görünürlüğünü denetler. Gösterge ağ trafiğine maruz kaldığından, bunu `False` uzak ölçülü senaryolarda tutmak yararlıdır. Bu seçeneği değiştirmek için Visual Studio'yı yeniden başlatmanız gerekmektedir. |
