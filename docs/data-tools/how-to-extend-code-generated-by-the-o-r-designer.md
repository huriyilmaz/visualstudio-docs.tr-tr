---
title: 'Nasıl yapılır: O-R Tasarımcısı tarafından oluşturulan kodu genişletme'
description: Nesne İlişkisel Tasarımcısı (O/R Designer) tarafından oluşturulan kodun nasıl genişletileceğini inceleyin. Bir varlık sınıfına kod ekleyin. DataContext 'e kod ekleyin.
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
ms.openlocfilehash: dac89dae2f54c32e6fb4e2bd40d3ee231e4847e3914bd0e577e489beb214e5f0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264356"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Nasıl yapılır: O/R Tasarımcısı tarafından oluşturulan kodu genişletme
**O/R Tasarımcısı** tarafından oluşturulan kod, varlık sınıflarında ve tasarımcı yüzeyinde diğer nesnelerde değişiklik yapıldığında yeniden oluşturulur. Bu kod yeniden oluşturma nedeniyle, tasarımcı kodu yeniden oluştururken oluşturulan koda eklediğiniz tüm kodlar genellikle üzerine yazılır. **O/R Tasarımcısı** , üzerine yazılmayan kod ekleyebileceğiniz kısmi sınıf dosyaları oluşturma yeteneği sağlar. kendi kodunuzu **O/R tasarımcısı** tarafından oluşturulan koda eklemenin bir örneği, LINQ to SQL (varlık) sınıflarına veri doğrulaması ekliyor. Daha fazla bilgi için bkz. [nasıl yapılır: varlık sınıflarına doğrulama ekleme](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Bir varlık sınıfına kod ekleme

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Kısmi bir sınıf oluşturmak ve bir varlık sınıfına kod eklemek için

1. **O/R tasarımcısında** yeni bir LINQ to SQL Classes dosyası (**. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** veya **veritabanı Gezgini** **. dbml** dosyasını çift tıklatın.)

2. **O/R tasarımcısında**, doğrulama eklemek istediğiniz sınıfa sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

     Kod Düzenleyicisi seçili varlık sınıfı için kısmi bir sınıf ile açılır.

3. Varlık sınıfı için kısmi sınıf bildiriminde kodunuzu ekleyin.

## <a name="add-code-to-a-datacontext"></a>DataContext 'e kod ekleme

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Kısmi bir sınıf oluşturmak ve DataContext 'e kod eklemek için

1. **O/R tasarımcısında** yeni bir LINQ to SQL Classes dosyası (**. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** veya **veritabanı Gezgini** **. dbml** dosyasını çift tıklatın.)

2. **O/R tasarımcısında**, tasarımcıda boş bir alana sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     Kod Düzenleyicisi DataContext için kısmi bir sınıf ile açılır.

3. DataContext için kısmi sınıf bildiriminde kodunuzu ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio araçlar LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [izlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ - SQL](/dotnet/framework/data/adonet/sql/linq/index)
