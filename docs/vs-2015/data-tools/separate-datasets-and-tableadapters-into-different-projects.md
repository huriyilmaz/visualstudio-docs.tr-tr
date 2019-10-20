---
title: Veri kümelerini ve TableAdapters farklı projelere ayır | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f6ec76e79cc1c4759cbe05d8bdcacc1297b655b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655427"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Veri kümeleri ile TableAdapter’ları farklı projelere ayırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Türü belirtilmiş veri kümeleri, [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) ve DataSet sınıflarının ayrı projelere üretilebilmeleri için geliştirilmiştir. Bu, uygulama katmanlarını hızlıca ayırmanızı ve n katmanlı veri uygulamaları oluşturmanıza olanak sağlar.

 Aşağıdaki yordamda, oluşturulan `TableAdapter` kodunu içeren projeden ayrı bir projede veri kümesi kodu oluşturmak için Veri Kümesi Tasarımcısı kullanma işlemi açıklanmaktadır.

## <a name="separatedatasets-and-tableadapters"></a>Separatedataset ve TableAdapters
 Veri kümesi kodunu `TableAdapter` koddan ayırdığınızda, veri kümesi kodunu içeren proje geçerli çözümde bulunmalıdır. Bu proje geçerli çözümde bulunmuyorsa, **Özellikler** penceresindeki **veri kümesi proje** listesinde kullanılamaz.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Veri kümesini farklı bir projeye ayırmak için

1. Bir veri kümesi (. xsd dosyası) içeren bir çözüm açın.

   > [!NOTE]
   > Çözüm, veri kümesi kodunuzu ayırmak istediğiniz projeyi içermiyorsa, projeyi oluşturun veya var olan bir projeyi çözüme ekleyin.

2. **Veri kümesi Tasarımcısı**veri kümesini açmak için **Çözüm Gezgini** bir türü belirtilmiş veri kümesi dosyasına (. xsd dosyası) çift tıklayın.

3. **Veri kümesi Tasarımcısı**boş bir alan seçin.

4. **Özellikler** penceresinde **veri kümesi proje** düğümünü bulun.

5. **Veri kümesi proje** listesinde, veri kümesi kodunu oluşturmak istediğiniz projenin adını seçin.

    Veri kümesi kodu oluşturmak istediğiniz projeyi seçtikten sonra, **veri kümesi dosyası** özelliği varsayılan bir dosya adı ile doldurulur. Gerekirse bu adı değiştirebilirsiniz. Ayrıca, veri kümesi kodunu belirli bir dizine oluşturmak istiyorsanız **Proje klasörü** özelliğini bir klasörün adı olarak ayarlayabilirsiniz.

   > [!NOTE]
   > Veri kümelerini ve TableAdapters ayırabilirsiniz ( **veri kümesi proje** özelliğini ayarlayarak), projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

6. Veri kümesini kaydedin.

    Veri kümesi kodu, **veri kümesi proje** özelliğindeki seçili projede oluşturulur ve **TableAdapter** kodu geçerli projede oluşturulur.

   Varsayılan olarak, veri kümesini ve `TableAdapter` kodunu ayırdıktan sonra sonuç, her projedeki ayrı bir sınıf dosyasıdır. Özgün projenin `TableAdapter` kodu içeren DatasetName. Designer. vb (veya DatasetName.Designer.cs) adlı bir dosyası vardır. **DataSet projesi** özelliğinde belirtilen proje, dataset kodunu Içeren DataSetName. DataSet. Designer. vb (veya DatasetName.DataSet.Designer.cs) adlı bir dosyaya sahiptir.

> [!NOTE]
> Oluşturulan sınıf dosyasını görüntülemek için veri kümesini veya `TableAdapter` projeyi seçin. Ardından, **Çözüm Gezgini**, **tüm dosyaları göster** ' i seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md) [Izlenecek yol: n katmanlı veri uygulaması oluşturma](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md) [Visual Studio 'da verilere erişme](../data-tools/accessing-data-in-visual-studio.md) [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
