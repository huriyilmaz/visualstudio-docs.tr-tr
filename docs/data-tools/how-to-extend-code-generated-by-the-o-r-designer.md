---
title: 'Nasıl kullanılır: O-R Tasarımcısı Tarafından Oluşturulan Kodu Genişletme'
description: Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) tarafından oluşturulan kodu genişletmeyi gözden geçirme. Varlık sınıfına kod ekleyin. DataContext'e kod ekleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7bc1c926108efb6223788caa695bdb4028645252
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631304"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Nasıl kullanılır: O/R Tasarımcısı tarafından oluşturulan kodu genişletme
O/R Tasarımcısı **tarafından oluşturulan kod,** varlık sınıflarında ve tasarımcı yüzeyindeki diğer nesnelerde değişiklikler yapılırken yeniden oluşturulur. Bu kod yeniden oluşturma nedeniyle, tasarımcı kodu yeniden üretirken oluşturulan koda ekley istediğiniz kodun üzerine yazılır. **O/R Tasarımcısı,** üzerine yazılmadan kod ek oluşturabilirsiniz kısmi sınıf dosyaları oluşturma olanağı sağlar. **O/R** Tasarımcısı tarafından oluşturulan koda kendi kodunuzu eklemenin bir örneği, bu sınıflara (varlık) LINQ to SQL doğrulama eklemektir. Daha fazla bilgi için [bkz. Nasıl kullanılır: Varlık sınıflarında doğrulama ekleme.](../data-tools/how-to-add-validation-to-entity-classes.md)

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Varlık sınıfına kod ekleme

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Kısmi bir sınıf oluşturmak ve varlık sınıfına kod eklemek için

1. **O/R** Tasarımcısı'nda LINQ to SQL Classes dosyasını (**.dbml** dosyası) açın veya yeni bir oluşturun. (Çözüm Gezgini veya **Veritabanı Gezgini** **.)** 

2. **O/R Tasarımcısı'nda,** doğrulama eklemek istediğiniz sınıfa sağ tıklayın ve ardından Kodu **Görüntüle'ye tıklayın.**

     Kod Düzenleyicisi, seçilen varlık sınıfı için kısmi bir sınıfla açılır.

3. Kodunuzu varlık sınıfı için kısmi sınıf bildirimine ekleyin.

## <a name="add-code-to-a-datacontext"></a>DataContext'e kod ekleme

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Kısmi bir sınıf oluşturmak ve DataContext'e kod eklemek için

1. **O/R** Tasarımcısı'nda LINQ to SQL Classes dosyasını (**.dbml** dosyası) açın veya yeni bir oluşturun. (Çözüm Gezgini veya **Veritabanı Gezgini** **.)** 

2. **O/R Tasarımcısı'nda** tasarımcıda boş bir alana sağ tıklayın ve ardından Kodu Görüntüle'ye **tıklayın.**

     Kod Düzenleyicisi DataContext için kısmi bir sınıfla açılır.

3. Kodunuzu DataContext için kısmi sınıf bildirimine ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Adım adım kılavuz: LINQ to SQL sınıfları oluşturma (O-R Tasarımcısı)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ - SQL](/dotnet/framework/data/adonet/sql/linq/index)
