---
title: Özellik, ilişkiye katıldığından silinemiyor
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3e7a5063846e05fd55880e1727dd829c2db0c3a5
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281402"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Özellik &lt; özelliği adı, &gt; ilişkilendirme ilişkilendirme adına katıldığından silinemiyor &lt;&gt;

Seçilen özellik, hata iletisinde belirtilen sınıflar arasındaki ilişki için **Ilişkilendirme özelliği** olarak ayarlanır. Özellikler, veri sınıfları arasında bir ilişkiye katılılarsa silinemez.

İstenen özelliğin başarıyla silinmesini sağlamak için **Association özelliğini** Data sınıfının farklı bir özelliğine ayarlayın.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. **O/R tasarımcısında** , hata iletisinde belirtilen veri sınıflarını bağlayan ilişki satırını seçin.

2. **Ilişkilendirme düzenleyici** iletişim kutusunu açmak için satıra çift tıklayın.

3. Özelliği **Ilişkilendirme özelliklerinden**kaldırın.

4. Özelliği silmeyi yeniden deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)