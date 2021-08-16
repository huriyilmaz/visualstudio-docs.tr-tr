---
title: Kod Ölçümleri penceresi
ms.date: 12/12/2017
description: Kod ölçümleri analiz verilerini görüntülemeyi, filtrelemeyi, yeniden düzenlemeyi Visual Studio dışarı aktarmayı öğrenin. Kod ölçümü sonuçlarına göre iş öğeleri oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: d68f8b43e675aa3e07b392ca8e0dfa77232245b0d8e652ee6570cd3869350e5c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121405389"
---
# <a name="use-the-code-metrics-results-window"></a>Kod Ölçümleri Sonuçları penceresini kullanma

Kod **Ölçümleri Sonuçları** penceresi, kod ölçümleri analizi tarafından oluşturulan verileri görüntüler. Kod ölçümleri veri değerleri hakkında daha fazla bilgi için [bkz. Kod ölçümleri değerleri.](../code-quality/code-metrics-values.md)

## <a name="display-code-metrics-results"></a>Kod ölçümleri sonuçlarını görüntüleme

Kod **Ölçümleri Sonuçları penceresi,** kod ölçümleri sonuçları üretmeniz sırasında otomatik olarak görüntülenir. Ayrıca, pencereyi herhangi bir zamanda görüntüebilirsiniz.

Aşağıdaki menü dizilerinden birini kullanarak Kod Ölçümleri Sonuçları penceresini görüntüebilirsiniz:

- Çözümle **menüsünde** Kod Ölçümleri **Windows**  >  **seçeneğini belirleyin.**

- Görünüm menüsünde **Kod** Ölçümleri **Sonuçları'Windows**  >  **Diğer Seçenekler'i seçin.**

Sonuç **içerilse** bile Kod Ölçümleri Sonuçları penceresi açılır.

### <a name="to-view-code-metrics-details"></a>Kod ölçümleri ayrıntılarını görüntülemek için

Kod ölçümleri sonuçları oluşturulmuşsa Hiyerarşi sütunundaki **ağacı genişletin.**

## <a name="filter-code-metrics-results"></a>Kod ölçümleri sonuçlarını filtreleme

En üstte yer alan araç çubuğunu kullanarak **Kod Ölçümleri Sonuçları** penceresinde görüntülenen sonuçları filtreleyebilirsiniz. Örneğin, yalnızca bakım dizini 65'in altında olan sonuçları görmek istiyor olabilir.

Filtre  açılan kutusu, sonuç sütunlarının adlarını içerir. Bir filtre tanımlandığı zaman, girintileme ile birlikte listenin en altına eklenir. Liste, tanımlanan son 10 filtreyi içerebilir.

### <a name="to-filter-the-code-metrics-results"></a>Kod ölçümleri sonuçlarını filtrelemek için

1. Filtre **listesinden** sütun adını seçin.

2. Minimum **'da** görüntülenecek minimum değeri yazın.

3. Maksimum **'a** görüntülenecek maksimum değeri yazın.

4. Filtre **Uygula düğmesine** tıklayın.

5. Sonuç ayrıntılarını görmek için hiyerarşi ağacını genişletin.

## <a name="add-remove-and-rearrange-data-columns"></a>Veri sütunlarını ekleme, kaldırma ve yeniden düzenleme

Kod Ölçümleri Sonuçları penceresinden sonuç sütunları **ekleyebilir veya kaldırabilirsiniz.** Ayrıca sonuç sütunlarını istediğiniz sırada görünecek şekilde yeniden düzenleyebilirsiniz.

### <a name="add-or-remove-a-column"></a>Sütun ekleme veya kaldırma

1. Sütun **Ekle/Kaldır düğmesine tıklayın** veya herhangi bir sütun başlığına sağ tıklayın ve ardından Sütun **Ekle/Kaldır'a tıklayın.**

1. Sütun **Ekle/Kaldır iletişim kutusunda,** eklemek veya kaldırmak istediğiniz sütunun onay kutusunu seçin veya temizleyin ve ardından Tamam'ı **seçin.**

### <a name="rearrange-columns"></a>Sütunları yeniden düzenleme

1. Sütun **Ekle/Kaldır düğmesine** tıklayın.

1. Sütun **Ekle/Kaldır iletişim** kutusunda, taşımak istediğiniz sütunu seçin ve sonra yukarı oku veya aşağı oku seçin.

1. Sütun istediğiniz konuma geldiğinde Tamam'ı **seçin.**

## <a name="copy-data-to-the-clipboard-or-excel"></a>Panoya veya panoya veri Excel

Her veri sütunlarının adı ve değeri için bir satır içeren bir metin dizesi olarak seçili bir kod ölçümü satırı seçerek panoya kopyalayabilirsiniz. Ayrıca tüm kod ölçümleri **sonuçlarını bir Microsoft Excel** elektronik tablosuna dışarı aktararak Seçimi Aç'a Excel tıklayabilirsiniz.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Kod ölçümü sonuçlarını temel alan bir iş öğesi oluşturma

Kod Ölçümü [Azure Boards](/azure/devops/boards/index?view=vsts&preserve-view=true) sonuçları temel alan bir iş öğesi **oluşturabilirsiniz.** İş öğesi oluşturulduğunda, Visual Studio otomatik olarak Başlık alanına bir başlık **ve** Geçmiş sekmesinin altındaki kod ölçümleri **verilerine bir başlık** girer.

İş öğeleri hakkında daha Azure Boards için bkz. [İş öğeleri.](/azure/devops/boards/work-items/index?view=vsts&preserve-view=true)

### <a name="to-create-a-work-item-based-on-a-result"></a>Bir sonucu temel alan bir iş öğesi oluşturmak için

1. Sonuça sağ tıklayın.

2. İş **Öğesi Oluştur'a** gelin ve ardından oluşturmak istediğiniz iş öğesi türüne tıklayın (**Hata,** **Görev** vb.).

3. Tüm gerekli alanları doldurarak iş öğesi formunu doldurun.

4. Dosya **menüsünde,** iş öğesini **kaydetmek için Hepsini** Kaydet'e tıklayın.

### <a name="to-create-a-bug-based-on-a-result"></a>Bir sonucu temel alan bir hata oluşturmak için

1. Sonucu seçerek seçin.

2. İş **Öğesi Oluştur düğmesine** tıklayın.

3. Tüm gerekli alanları doldurarak iş öğesi formunu doldurun.

4. Dosya **menüsünde,** iş öğesini **kaydetmek için Hepsini** Kaydet'e tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod ölçümleri değerleri](../code-quality/code-metrics-values.md)
- [Nasıl kullanılır: Kod ölçümleri verileri oluşturma](../code-quality/how-to-generate-code-metrics-data.md)
