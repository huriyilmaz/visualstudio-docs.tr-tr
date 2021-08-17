---
title: Özellik ilişkilendirmeye katıyor
description: özelliği ilişkilendirmeye katıldığı için silinemiyor. Bu Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) iletisiyle ilgili bilgileri görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: dc732273719484b7f2f3eaf26a39a8ff518ee3dc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067013"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Özellik &lt; özellik &gt; adı, ilişkilendirme ilişkilendirme adına katıldığı için &lt; silinemiyor&gt;

Seçilen özellik, hata **iletisinde belirtilen** sınıflar arasındaki ilişkilendirme için İlişki özelliği olarak ayarlanır. Özellikler, veri sınıfları arasında bir ilişkilendirmeye katıldıklarında silinemez.

İstenen **özelliğin başarıyla** silinmesini sağlamak için association Özelliğini veri sınıfının farklı bir özelliğine ayarlayın.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Hata iletisinde belirtilen **veri sınıflarını bağlayan O/R** Tasarımcısı'nda ilişkilendirme çizgisini seçin.

2. İlişki Düzenleyicisi iletişim kutusunu açmak için **satıra çift** tıklayın.

3. özelliğini İlişki **Özellikleri'nin 'den kaldırın.**

4. Özelliğini silmeyi yeniden deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)