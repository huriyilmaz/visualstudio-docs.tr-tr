---
title: Kod ölçümleri verileriyle çalışma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645701"
---
# <a name="working-with-code-metrics-data"></a>Kod Ölçüm Verileri ile çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Kod ölçümleri sonuçları** penceresinde, kod ölçüm Analizi tarafından oluşturulan veriler görüntülenir. Kod ölçümleri veri değerleri hakkında daha fazla bilgi için bkz. [kod ölçüm değerleri](../code-quality/code-metrics-values.md).

 Bu konu aşağıdaki bölümleri içermektedir:

- [Kod ölçümleri sonuçları penceresi](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [Kod ölçümleri sonuçlarını görüntüleme](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [Kod ölçümleri sonuçlarını filtreleme](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [Veri sütunları ekleme, kaldırma ve yeniden düzenleme](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [Verileri panoya veya Excel 'e kopyalama](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [Kod ölçümü sonuçlarına göre Iş öğesi oluşturma](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="BKMK_CodeMetricsResultsWindow"></a>Kod ölçümleri sonuçları penceresi
 **Kod ölçümleri sonuçları** penceresinde, hesaplanmış sonuçları görüntüleyen en üstteki ve sütunlardaki bir araç çubuğu bulunur.

|Sütunuyla|Açıklama|
|------------|-----------------|
|**Hiyerarşi**|**Hiyerarşi** sütunu, istediğiniz ayrıntı düzeyini görmek için genişletebileceğiniz veya daraltabileceğiniz kod hiyerarşisinin ağaç görünümünü içerir. Kalan sütunlar, hesaplanan sonuçları gösterir. Sonuç sütunlarını istediğiniz gibi gizleyebilir veya düzenleyebilirsiniz.|
|**Bakım**|**Bakımsıma** sütunu, sayısal sonuca ek olarak bir simge içerir. Yeşil bir simge görece yüksek oranda bakım derecesini gösterir. Sarı bir simge, ileri düzey bakım derecesini belirtir. Kırmızı bir simge, düşük bakım ve olası bir sorun noktası olduğunu gösterir. Bu renk göstergeleri, FxCop kuralı AvoidUnmaintainableCode tarafından kullanılan önem kategorilerine karşılık gelir. Bu kural, bakım dizini 10 ' dan düşükse bir hata tetikler, dizin 10 ile 20 arasındaysa bir uyarı ve Dizin 20 ' den fazlaysa bir hata ya da uyarı değildir. Bakımı dizini üç ölçüden oluşur: döngüsel karmaşıklık, kod satırı ve hesaplama karmaşıklığı. Değerleri birimlerde ifade edilmez.|

## <a name="BKMK_DisplayingCodeMetricsResults"></a>Kod ölçümleri sonuçlarını görüntüleme
 Kod ölçümleri sonuçları penceresi, kod ölçümleri sonuçları oluştururken otomatik olarak görüntülenir. Ayrıca, pencereyi istediğiniz zaman da görüntüleyebilirsiniz.

#### <a name="to-display-the-code-metrics-results-window"></a>Kod ölçümleri sonuçları penceresini göstermek için

- **Çözümle** menüsünde **Windows** ' a ve ardından **Kod ölçümleri sonuçları**' na tıklayın.

     \- veya-

- **Görünüm** menüsünde **diğer pencereler** ' in üzerine gelin ve ardından **Kod ölçümleri sonuçları**' na tıklayın.

     Kod ölçümleri sonuçları penceresi hiç sonuç içermediğinde bile görüntülenir.

#### <a name="to-view-code-metrics-details"></a>Kod ölçümleri ayrıntılarını görüntülemek için

- Kod ölçümleri sonuçları oluşturulduysa, **hiyerarşi** sütunundaki ağacı genişletin.

## <a name="BKMK_FilteringCodeMetricsResults"></a>Kod ölçümleri sonuçlarını filtreleme
 Üstteki araç çubuğunu kullanarak, **Kod ölçümleri sonuçları** penceresinde görüntülenen sonuçlara filtre uygulayabilirsiniz. Örneğin, yalnızca 65 altındaki bakım dizinine sahip sonuçları görmek isteyebilirsiniz.

 **Filtre** açılan kutusu, sonuçlar sütunlarının adlarını içerir. Bir filtre tanımlandığında, listenin sonuna girintileme ile birlikte eklenir. Liste, tanımlanan son on filtreyi içerebilir.

#### <a name="to-filter-the-code-metrics-results"></a>Kod ölçümleri sonuçlarını filtrelemek için

1. **Filtre** listesinden sütun adını seçin.

2. **En**az, görüntülenecek en düşük değeri yazın.

3. **En**fazla, görüntülenecek en büyük değeri yazın.

4. **Filtre Uygula** düğmesine tıklayın.

5. Sonuç ayrıntılarını görmek için hiyerarşi ağacını genişletin.

## <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Veri sütunları ekleme, kaldırma ve yeniden düzenleme
 **Kod ölçümleri sonuçları** penceresinden sonuç sütunları ekleyebilir veya kaldırabilirsiniz. Ayrıca, sonuçlar sütunlarını istediğiniz sırada görünecek şekilde yeniden düzenleyebilirsiniz.

#### <a name="to-remove-a-column"></a>Bir sütunu kaldırmak için

1. **Sütun Ekle/Kaldır** düğmesine tıklayın.

     \- veya-

     Herhangi bir sütun başlığına sağ tıklayın ve ardından **sütun Ekle/Kaldır**' a tıklayın.

2. **Sütunları Ekle/Kaldır** iletişim kutusunda, kaldırmak istediğiniz sütunun onay kutusunu temizleyin ve ardından **Tamam**' a tıklayın.

#### <a name="to-add-a-previously-removed-column"></a>Daha önce kaldırılan bir sütun eklemek için

1. **Sütun Ekle/Kaldır** düğmesine tıklayın.

     \- veya-

     Herhangi bir sütun başlığına sağ tıklayın ve ardından **sütun Ekle/Kaldır**' a tıklayın.

2. **Sütun Ekle/Kaldır** iletişim kutusunda, eklemek istediğiniz sütunun onay kutusunu seçin ve ardından **Tamam**' a tıklayın.

#### <a name="to-rearrange-columns"></a>Sütunları yeniden düzenlemek için

1. **Sütun Ekle/Kaldır** düğmesine tıklayın.

     \- veya-

     Herhangi bir sütun başlığına sağ tıklayın ve ardından **sütun Ekle/Kaldır**' a tıklayın.

2. **Sütun Ekle/Kaldır** iletişim kutusunda, taşımak istediğiniz sütunu seçin ve ardından yukarı oka veya aşağı oka tıklayın.

3. Sütun istediğiniz yere konumlandırıldığında, **Tamam**' a tıklayın.

## <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Verileri panoya veya Excel 'e kopyalama
 Seçilen bir kod Ölçüm verisi satırını, her bir veri sütununun adı ve değeri için bir satır içeren bir metin dizesi olarak Pano 'ya seçip kopyalayabilirsiniz. Ayrıca, tüm kod ölçümleri sonuçlarının bir Excel elektronik tablosuna aktarılması için **Microsoft Excel 'de listeyi aç** ' a tıklayabilirsiniz.

## <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Kod ölçümü sonuçlarına göre Iş öğesi oluşturma
 **Kod ölçümü sonuçları** penceresindeki sonuçlara dayalı bir [!INCLUDE[esprfound](../includes/esprfound-md.md)] iş öğesi oluşturabilirsiniz. İş öğesi oluşturulduğunda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **başlık** alanına otomatik olarak bir başlık girer ve **geçmiş** sekmesinin altındaki kod ölçümleri verilerini otomatik olarak girer.

 İş öğeleri oluşturma hakkında daha fazla bilgi için bkz. [iş öğesi &#91;yeniden yönlendirilen&#93;oluşturma](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).

#### <a name="to-create-a-work-item-based-on-a-result"></a>Bir sonuca göre iş öğesi oluşturmak için

1. Sonuca sağ tıklayın.

2. **Iş öğesi oluştur**' un üzerine gelin ve sonra oluşturmak istediğiniz iş öğesi türüne (**hata**, **görev**vb.) tıklayın.

3. Tüm gerekli alanları doldurarak iş öğesi formunu doldurun.

4. **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayarak iş öğesini kaydedin.

#### <a name="to-create-a-bug-based-on-a-result"></a>Bir sonuca dayalı bir hata oluşturmak için

1. Seçmek için sonuca tıklayın.

2. **Iş öğesi oluştur** düğmesine tıklayın.

3. Tüm gerekli alanları doldurarak iş öğesi formunu doldurun.

4. **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayarak iş öğesini kaydedin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilen kod](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [nasıl yapılır: kod ölçüm verileri oluşturma](../code-quality/how-to-generate-code-metrics-data.md) karmaşıklık ve bakım
