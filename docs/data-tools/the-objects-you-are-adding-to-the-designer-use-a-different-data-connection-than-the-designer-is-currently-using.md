---
title: Nesneler farklı bağlantı kullanır
description: Tasarımcıya eklemekte olduğunu nesneler tasarımcıdan farklı bir veri bağlantısı kullanır. Bu çalışma Visual Studio O/R Tasarımcısı iletisiyle ilgili bilgileri görüntüleme.
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
ms.openlocfilehash: c4ac9e9426d782c32a4cd75fb73a29f2839edf35ba8f94b8bd8708cc3223a622
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346784"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Tasarımcıya eklemekte olduğunu nesneler tasarımcıdan farklı bir veri bağlantısı kullanır

Tasarımcıya eklemekte olduğu nesneler, tasarımcının şu anda kullanmakta olduğu veri bağlantısından farklı bir veri bağlantısı kullanır. Tasarımcı tarafından kullanılan bağlantıyı değiştirmek istiyor musunuz?

Öğeleri Nesne İlişkisel Tasarımcısı **(** **O/R Tasarımcısı) eklerken,** tüm öğeler paylaşılan bir veri bağlantısı kullanır. (Tasarım yüzeyi, yüzeydeki <xref:System.Data.Linq.DataContext> tüm nesneler için tek bir bağlantı kullanan 'yi temsil eder.) Tasarımcı tarafından şu anda kullanılan veri bağlantısından farklı bir veri bağlantısı kullanan bir nesneyi tasarımcıya eklersiniz, bu ileti görüntülenir. Bu hatayı çözmek için mevcut bağlantıyı sürdürmeyi seçebilirsiniz. Bu seçimi yaptıysanız, seçilen nesne eklenmez. Alternatif olarak, nesnesini ekleyebilir ve bağlantıyı yeni <xref:System.Data.Linq.DataContext> bağlantıyla sıfırlayabilirsiniz.

## <a name="connection-options"></a>Bağlantı seçenekleri

- Mevcut bağlantıyı seçilen nesne tarafından kullanılan bağlantıyla değiştirmek için Evet'e **tıklayın.**

   Seçilen nesne **O/R Tasarımcısı'na eklenir** ve *DataContext.Connection* yeni bağlantı olarak ayarlanır.

   > [!NOTE]
   > **Evet'e** tıklarsanız, **O/R** Tasarımcısı'nda tüm varlık sınıfları yeni bağlantıyla eşlenmiş olur.

- Mevcut bağlantıyı kullanmaya devam etmek ve seçilen nesneyi eklemeyi iptal etmek için Hayır'a **tıklayın.**

   Eylem iptal edilir. *DataContext.Connection,* mevcut bağlantı olarak ayarlanmış olarak kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
