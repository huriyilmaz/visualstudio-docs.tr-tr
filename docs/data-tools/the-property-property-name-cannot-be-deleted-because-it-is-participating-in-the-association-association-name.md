---
title: Özellik, ilişkiye katıldığından silinemiyor
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e1890535fb008c8e8be6ee9dea0eda3ab3844da6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648140"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>@No__t_0property ad &gt; özelliği, Association &lt;association adına katıldığından silinemiyor &gt;

Seçilen özellik, hata iletisinde belirtilen sınıflar arasındaki ilişki için **Ilişkilendirme özelliği** olarak ayarlanır. Özellikler, veri sınıfları arasında bir ilişkiye katılılarsa silinemez.

İstenen özelliğin başarıyla silinmesini sağlamak için **Association özelliğini** Data sınıfının farklı bir özelliğine ayarlayın.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. **O/R tasarımcısında** , hata iletisinde belirtilen veri sınıflarını bağlayan ilişki satırını seçin.

2. **Ilişkilendirme düzenleyici** iletişim kutusunu açmak için satıra çift tıklayın.

3. Özelliği **Ilişkilendirme özelliklerinden**kaldırın.

4. Özelliği silmeyi yeniden deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)