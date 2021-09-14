---
title: Nesneler farklı bağlantı kullanır
description: Tasarımcıya eklemekte olduğunu nesneler tasarımcıdan farklı bir veri bağlantısı kullanır. O/R Tasarımcısı Visual Studio ilgili bilgileri görüntüleme.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631166"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>Tasarımcıya eklemekte olduğunuz nesneler tasarımcıdan farklı bir veri bağlantısı kullanır

Tasarımcıya eklemekte olduğunu nesneler, tasarımcının şu anda kullanmakta olduğu veri bağlantısından farklı bir veri bağlantısı kullanır. Tasarımcı tarafından kullanılan bağlantıyı değiştirmek istiyor musunuz?

Nesne İlişkisel Tasarımcısı  **(O/R Tasarımcısı) öğeleri eklerken,** tüm öğeler tek bir paylaşılan veri bağlantısı kullanır. (Tasarım yüzeyi, yüzeydeki <xref:System.Data.Linq.DataContext> tüm nesneler için tek bir bağlantı kullanan 'yi temsil eder.) Tasarımcı tarafından şu anda kullanılan veri bağlantısından farklı bir veri bağlantısı kullanan tasarımcıya bir nesnesi eklersiniz, bu ileti görüntülenir. Bu hatayı çözmek için mevcut bağlantıyı sürdürmeyi seçebilirsiniz. Bu seçimi yaptıysanız, seçilen nesne eklenmez. Alternatif olarak, nesnesini ekleyebilir ve bağlantıyı yeni <xref:System.Data.Linq.DataContext> bağlantıyla sıfırlayabilirsiniz.

## <a name="connection-options"></a>Bağlantı seçenekleri

- Mevcut bağlantıyı seçilen nesne tarafından kullanılan bağlantıyla değiştirmek için Evet'e **tıklayın.**

   Seçilen nesne **O/R Tasarımcısı'na eklenir** ve *DataContext.Connection* yeni bağlantı olarak ayarlanır.

   > [!NOTE]
   > **Evet'e** tıklarsanız, **O/R** Tasarımcısı'nda tüm varlık sınıfları yeni bağlantıyla eşlenmiş olur.

- Mevcut bağlantıyı kullanmaya devam etmek ve seçilen nesneyi eklemeyi iptal etmek için Hayır'a **tıklayın.**

   Eylem iptal edilir. *DataContext.Connection,* mevcut bağlantı olarak ayarlanmış olarak kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
