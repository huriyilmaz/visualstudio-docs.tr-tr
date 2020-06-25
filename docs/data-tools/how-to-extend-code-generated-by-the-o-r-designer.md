---
title: 'Nasıl yapılır: O-R Tasarımcısı tarafından oluşturulan kodu genişletme'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b4c0ac8cff82250169171e1d842e64a34a4523ac
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282117"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Nasıl yapılır: O/R Tasarımcısı tarafından oluşturulan kodu genişletme
**O/R Tasarımcısı** tarafından oluşturulan kod, varlık sınıflarında ve tasarımcı yüzeyinde diğer nesnelerde değişiklik yapıldığında yeniden oluşturulur. Bu kod yeniden oluşturma nedeniyle, tasarımcı kodu yeniden oluştururken oluşturulan koda eklediğiniz tüm kodlar genellikle üzerine yazılır. **O/R Tasarımcısı** , üzerine yazılmayan kod ekleyebileceğiniz kısmi sınıf dosyaları oluşturma yeteneği sağlar. Kendi kodunuzu **O/R Tasarımcısı** tarafından oluşturulan koda eklemenin bir örneği, LINQ to SQL (varlık) sınıflarına veri doğrulaması ekliyor. Daha fazla bilgi için bkz. [nasıl yapılır: varlık sınıflarına doğrulama ekleme](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Bir varlık sınıfına kod ekleme

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Kısmi bir sınıf oluşturmak ve bir varlık sınıfına kod eklemek için

1. **O/R tasarımcısında**yeni bir LINQ to SQL Classes dosyası (**. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** veya **veritabanı Gezgini** **. dbml** dosyasını çift tıklatın.)

2. **O/R tasarımcısında**, doğrulama eklemek istediğiniz sınıfa sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

     Kod Düzenleyicisi seçili varlık sınıfı için kısmi bir sınıf ile açılır.

3. Varlık sınıfı için kısmi sınıf bildiriminde kodunuzu ekleyin.

## <a name="add-code-to-a-datacontext"></a>DataContext 'e kod ekleme

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Kısmi bir sınıf oluşturmak ve DataContext 'e kod eklemek için

1. **O/R tasarımcısında**yeni bir LINQ to SQL Classes dosyası (**. dbml** dosyası) açın veya oluşturun. ( **Çözüm Gezgini** veya **veritabanı Gezgini** **. dbml** dosyasını çift tıklatın.)

2. **O/R tasarımcısında**, tasarımcıda boş bir alana sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     Kod Düzenleyicisi DataContext için kısmi bir sınıf ile açılır.

3. DataContext için kısmi sınıf bildiriminde kodunuzu ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
