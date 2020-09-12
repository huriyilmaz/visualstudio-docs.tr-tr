---
title: Nesneler farklı bağlantı kullanıyor
description: Tasarımcıya eklenen nesneler farklı bir veri bağlantısı kullanır
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5b2ae4975f2848379403a0df1258640c32ccd58f
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036229"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Tasarımcıya eklemekte olduğunuz nesneler tasarımcıdan farklı bir veri bağlantısı kullanır

Tasarımcıya eklemekte olduğunuz nesneler, tasarımcının kullanmakta olduğundan farklı bir veri bağlantısı kullanır. Tasarımcı tarafından kullanılan bağlantıyı değiştirmek istiyor musunuz?

Öğeleri **nesne ilişkisel Tasarımcısı** eklediğinizde (**O/R Designer**), tüm öğeler paylaşılan bir veri bağlantısı kullanır. (Tasarım yüzeyi, <xref:System.Data.Linq.DataContext> yüzeyde tüm nesneler için tek bir bağlantı kullanan öğesini temsil eder.) Tasarımcıya, tasarımcı tarafından kullanılmakta olan veri bağlantısından farklı bir veri bağlantısı kullanan bir nesne eklerseniz, bu ileti görünür. Bu hatayı çözmek için var olan bağlantıyı korumayı seçebilirsiniz. Bu seçimi yaparsanız, seçilen nesne eklenmez. Alternatif olarak, nesneyi eklemeyi ve <xref:System.Data.Linq.DataContext> Yeni bağlantıyla bağlantıyı sıfırlamayı seçebilirsiniz.

## <a name="connection-options"></a>Bağlantı seçenekleri

- Mevcut bağlantıyı seçilen nesne tarafından kullanılan bağlantıyla değiştirmek için **Evet**' e tıklayın.

   Seçilen nesne **O/R tasarımcısına**eklenir ve *DataContext. Connection* yeni bağlantı olarak ayarlanır.

   > [!NOTE]
   > **Evet**' e tıklarsanız, **O/R tasarımcısında** tüm varlık sınıfları yeni bağlantıyla eşleştirilir.

- Mevcut bağlantıyı kullanmaya devam etmek ve seçili nesneyi eklemeyi iptal etmek için **Hayır**'a tıklayın.

   Eylem iptal edildi. *DataContext. Connection* mevcut bağlantı olarak ayarlanmış durumda kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
