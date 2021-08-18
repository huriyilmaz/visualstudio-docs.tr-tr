---
title: Ayrı projeler kullanma hatası
description: Uygulama katmanlarını hızlıca ayırabilmeniz ve N katmanlı veri uygulamaları oluşturabilmeniz için veri kümelerini ve TableAdapters farklı projelere nasıl ayıracağınızı öğrenin.
ms.date: 11/04/2016
ms.topic: how-to
ms.custom: SEO-VS-2020
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 335f6d1ab4a7dba28609a267e6a6ce950cb607ff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161837"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Veri kümeleri ile TableAdapter’ları farklı projelere ayırma
Türü belirtilmiş veri kümeleri, [TableAdapters](create-and-configure-tableadapters.md) ve DataSet sınıflarının ayrı projelere üretilebilmeleri için geliştirilmiştir. Bu, uygulama katmanlarını hızlıca ayırmanızı ve n katmanlı veri uygulamaları oluşturmanıza olanak sağlar.

Aşağıdaki yordamda, oluşturulan TableAdapter kodunu içeren projeden ayrı bir projede veri kümesi kodu oluşturmak için **veri kümesi Tasarımcısı** kullanma işlemi açıklanmaktadır.

## <a name="separate-datasets-and-tableadapters"></a>Ayrı veri kümeleri ve TableAdapters
Veri kümesi kodunu TableAdapter kodundan ayırdığınızda, veri kümesi kodunu içeren proje geçerli çözümde bulunmalıdır. bu proje geçerli çözümde bulunmuyorsa, **özellikler** penceresindeki **veri kümesi Project** listesinde kullanılamaz.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Veri kümesini farklı bir projeye ayırmak için

1. Bir veri kümesi (*. xsd* dosyası) içeren bir çözüm açın.

    > [!NOTE]
    > Çözüm, veri kümesi kodunuzu ayırmak istediğiniz projeyi içermiyorsa, projeyi oluşturun veya var olan bir projeyi çözüme ekleyin.

2. **Veri kümesi Tasarımcısı** veri kümesini açmak için **Çözüm Gezgini** bir türü belirtilmiş veri kümesi dosyasına ( *. xsd* dosyası) çift tıklayın.

3. **Veri kümesi Tasarımcısı** boş bir alan seçin.

4. **özellikler** penceresinde, **veri kümesi Project** düğümünü bulun.

5. **veri kümesi Project** listesinde, veri kümesi kodunu oluşturmak istediğiniz projenin adını seçin.

     Veri kümesi kodu oluşturmak istediğiniz projeyi seçtikten sonra, **veri kümesi dosyası** özelliği varsayılan bir dosya adı ile doldurulur. Gerekirse bu adı değiştirebilirsiniz. ayrıca, veri kümesi kodunu belirli bir dizine oluşturmak isterseniz, **Project folder** özelliğini bir klasörün adı olarak ayarlayabilirsiniz.

    > [!NOTE]
    > veri kümelerini ve TableAdapters ayırabilirsiniz ( **dataset Project** özelliğini ayarlayarak), projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut kısmi veri kümesi sınıflarının veri kümesi projesine el ile taşınması gerekir.

6. Veri kümesini kaydedin.

     veri kümesi kodu, **veri kümesi Project** özelliğindeki seçili projede oluşturulur ve **TableAdapter** kodu geçerli projede oluşturulur.

Varsayılan olarak, veri kümesini ve TableAdapter kodunu ayırdıktan sonra sonuç, her projedeki ayrı bir sınıf dosyasıdır. Özgün projenin, TableAdapter kodunu içeren *DataSetName. Designer. vb* (veya *DataSetName. Designer. cs*) adlı bir dosyası vardır. **dataset Project** özelliğinde belirtilen proje, dataset kodunu içeren *datasetname. dataset. designer. vb* (veya *datasetname. dataset. designer. cs*) adlı bir dosyaya sahiptir.

> [!NOTE]
> Oluşturulan sınıf dosyasını görüntülemek için DataSet veya TableAdapter projesini seçin. Ardından, **Çözüm Gezgini**, **tüm dosyaları göster**' i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md)
- [İzlenecek yol: N katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)
