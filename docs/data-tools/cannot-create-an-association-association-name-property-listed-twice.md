---
title: Özellik iki kez listelendi
description: Bir ilişki oluşturulamıyor-Özellik iki kez listelenmiş
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c496a25b093c88cca68d31bd22ccc6deca9a33a
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743207"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>İlişki &lt; ilişkilendirme adı oluşturulamıyor &gt; -özellik iki kez listelendi

İlişki oluşturulamıyor \<association name> . Aynı özellik birden çok kez listeleniyor: \<property name> .

İlişkilendirmeler, **Ilişki düzenleyici** iletişim kutusunda seçilen **ilişkilendirme özellikleri** tarafından tanımlanır. Özellikler, ilişkilendirmedeki her sınıf için yalnızca bir kez listelenebilir.

İletideki özelliği, üst veya alt sınıfın **Ilişkilendirme özelliklerinde**birden çok kez görünüyor.

## <a name="to-resolve-this-condition"></a>Bu durumu çözümlemek için

- İletiyi inceleyin ve iletide belirtilen özelliği aklınızda edin.

- İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.

- **Ilişki özelliklerini** inceleyin ve yinelenen girdileri kaldırın.

- **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Nasıl yapılır: LINQ to SQL sınıfları arasında ilişki oluşturma (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)