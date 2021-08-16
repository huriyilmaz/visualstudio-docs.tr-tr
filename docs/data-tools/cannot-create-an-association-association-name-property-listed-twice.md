---
title: Özellik iki kez listelendi
description: Bir ilişki oluşturma özelliği iki kez listelenmiş. bu Visual Studio Nesne İlişkisel Tasarımcısı (O/R Designer) iletisiyle ilgili bilgileri görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 391d24219063d2c1973361260a36b14d7a30a09e6d00a73476867d15c777130a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380734"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>İlişki &lt; ilişkilendirme adı oluşturulamıyor &gt; -özellik iki kez listelendi

İlişki oluşturulamıyor \<association name> . Aynı özellik birden çok kez listeleniyor: \<property name> .

İlişkilendirmeler, **Ilişki düzenleyici** iletişim kutusunda seçilen **ilişkilendirme özellikleri** tarafından tanımlanır. Özellikler, ilişkilendirmedeki her sınıf için yalnızca bir kez listelenebilir.

İletideki özelliği, üst veya alt sınıfın **Ilişkilendirme özelliklerinde** birden çok kez görünüyor.

## <a name="to-resolve-this-condition"></a>Bu durumu çözümlemek için

- İletiyi inceleyin ve iletide belirtilen özelliği aklınızda edin.

- İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.

- **Ilişki özelliklerini** inceleyin ve yinelenen girdileri kaldırın.

- **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio araçlar LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [nasıl yapılır: LINQ to SQL sınıfları arasında ilişki oluşturma (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
