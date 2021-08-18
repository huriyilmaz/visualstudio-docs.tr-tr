---
title: Nesneler farklı bağlantı kullanıyor
description: Tasarımcıya eklemekte olduğunuz nesneler tasarımcıdan farklı bir veri bağlantısı kullanır. bu Visual Studio O/R Designer iletisi hakkındaki bilgileri görüntüleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a93906f50fb332b05c7894c80d581d49d3f3be22
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052583"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Tasarımcıya eklemekte olduğunuz nesneler tasarımcıdan farklı bir veri bağlantısı kullanır

Tasarımcıya eklemekte olduğunuz nesneler, tasarımcının kullanmakta olduğundan farklı bir veri bağlantısı kullanır. Tasarımcı tarafından kullanılan bağlantıyı değiştirmek istiyor musunuz?

öğeleri **Nesne İlişkisel Tasarımcısı** eklediğinizde (**O/R Designer**), tüm öğeler paylaşılan bir veri bağlantısı kullanır. (Tasarım yüzeyi, <xref:System.Data.Linq.DataContext> yüzeyde tüm nesneler için tek bir bağlantı kullanan öğesini temsil eder.) Tasarımcıya, tasarımcı tarafından kullanılmakta olan veri bağlantısından farklı bir veri bağlantısı kullanan bir nesne eklerseniz, bu ileti görünür. Bu hatayı çözmek için var olan bağlantıyı korumayı seçebilirsiniz. Bu seçimi yaparsanız, seçilen nesne eklenmez. Alternatif olarak, nesneyi eklemeyi ve <xref:System.Data.Linq.DataContext> Yeni bağlantıyla bağlantıyı sıfırlamayı seçebilirsiniz.

## <a name="connection-options"></a>Bağlantı seçenekleri

- Mevcut bağlantıyı seçilen nesne tarafından kullanılan bağlantıyla değiştirmek için **Evet**' e tıklayın.

   Seçilen nesne **O/R tasarımcısına** eklenir ve *DataContext. Connection* yeni bağlantı olarak ayarlanır.

   > [!NOTE]
   > **Evet**' e tıklarsanız, **O/R tasarımcısında** tüm varlık sınıfları yeni bağlantıyla eşleştirilir.

- Mevcut bağlantıyı kullanmaya devam etmek ve seçili nesneyi eklemeyi iptal etmek için **Hayır**'a tıklayın.

   Eylem iptal edildi. *DataContext. Connection* mevcut bağlantı olarak ayarlanmış durumda kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio araçlar LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
