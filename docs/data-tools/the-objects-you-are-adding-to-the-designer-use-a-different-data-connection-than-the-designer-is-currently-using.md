---
title: Tasarımcıya eklenen nesneler farklı bir veri bağlantısı kullanır
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 915860c2559335f37869f5c6009f7a38dde6abcd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72640838"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Tasarımcıya eklemekte olduğunuz nesneler tasarımcıdan farklı bir veri bağlantısı kullanır

Tasarımcıya eklemekte olduğunuz nesneler, tasarımcının kullanmakta olduğundan farklı bir veri bağlantısı kullanır. Tasarımcı tarafından kullanılan bağlantıyı değiştirmek istiyor musunuz?

Öğeleri **nesne ilişkisel Tasarımcısı** eklediğinizde (**O/R Designer**), tüm öğeler paylaşılan bir veri bağlantısı kullanır. (Tasarım yüzeyi, yüzeyde tüm nesneler için tek bir bağlantı kullanan <xref:System.Data.Linq.DataContext> temsil eder.) Tasarımcıya, tasarımcı tarafından kullanılmakta olan veri bağlantısından farklı bir veri bağlantısı kullanan bir nesne eklerseniz, bu ileti görünür. Bu hatayı çözmek için var olan bağlantıyı korumayı seçebilirsiniz. Bu seçimi yaparsanız, seçilen nesne eklenmez. Alternatif olarak, nesneyi eklemeyi ve yeni bağlantıya <xref:System.Data.Linq.DataContext> bağlantıyı sıfırlamayı seçebilirsiniz.

## <a name="connection-options"></a>Bağlantı seçenekleri

- Mevcut bağlantıyı seçilen nesne tarafından kullanılan bağlantıyla değiştirmek için **Evet**' e tıklayın.

   Seçilen nesne **O/R tasarımcısına**eklenir ve *DataContext. Connection* yeni bağlantı olarak ayarlanır.

   > [!NOTE]
   > **Evet**' e tıklarsanız, **O/R tasarımcısında** tüm varlık sınıfları yeni bağlantıyla eşleştirilir.

- Mevcut bağlantıyı kullanmaya devam etmek ve seçili nesneyi eklemeyi iptal etmek için **Hayır**'a tıklayın.

   Eylem iptal edildi. *DataContext. Connection* mevcut bağlantı olarak ayarlanmış durumda kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
