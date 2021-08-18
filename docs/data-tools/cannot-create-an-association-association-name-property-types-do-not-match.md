---
title: Özellik türleri eşle değil
description: İlişki oluşturulamaz - özellik türleri eşliğiz. Bu Visual Studio Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) iletisiyle ilgili bilgileri görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f752757aadf67529f915340434735e89bf7375da
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081886"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>İlişki ilişkilendirme adı &lt; oluşturulamaz &gt; - özellik türleri eşle

İlişki oluşturulamaz \<association name> - özellik türleri eşliğiz. Özelliklerin eşleşen türleri yok: \<property names> .

İlişkiler, İlişki Düzenleyici iletişim **kutusunda seçili** İlişki Özellikleri **tarafından** tanımlanır. İlişkinin her tarafındaki özellikler aynı veri türünde olması gerekir.

İletide listelenen özellikler aynı veri türlerine sahip değildir.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. İletiyi inceler ve iletide çağrılan özellikleri not alın.

2. İletişim **kutusunu** açmak için Tamam'a tıklayın.

3. İlişki **özellikleri'ne** tıklayın ve aynı veri türünün özelliklerini seçin.

4. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Nasıl kullanılır: LINQ to SQL sınıfları (O/R Tasarımcısı) arasında ilişki oluşturma](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)