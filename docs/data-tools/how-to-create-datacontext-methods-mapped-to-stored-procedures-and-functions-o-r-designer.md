---
title: DataContext metotlarını sprocs ve işlevlerle eşleyin (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ba4a53e81578a7b72c697e52fec923d8ecc1ecce
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586490"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)

Saklı yordamları ve işlevleri de <xref:System.Data.Linq.DataContext> yöntemler olarak **O/R tasarımcısına** ekleyebilirsiniz. Yöntemi çağırmak ve gerekli parametreleri geçirmek, veritabanında saklı yordamı veya işlevi çalıştırır ve <xref:System.Data.Linq.DataContext> yönteminin dönüş türündeki verileri döndürür. <xref:System.Data.Linq.DataContext> yöntemleriyle ilgili ayrıntılı bilgi için bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Ayrıca, değişiklikler varlık sınıflarından veritabanına kaydedildiğinde ekleme, güncelleştirme ve silme işlemleri gerçekleştiren varsayılan [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] çalışma zamanı davranışını geçersiz kılmak için saklı yordamları da kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: güncelleştirme, ekleme ve silme (O/R Tasarımcısı) gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>DataContext yöntemleri oluşturma

Saklı yordamları veya işlevleri <strong>Sunucu Gezgini veya * * veritabanı Gezgini</strong> ' den **O/R tasarımcısına**sürükleyerek <xref:System.Data.Linq.DataContext> Yöntemler oluşturabilirsiniz.

> [!NOTE]
> Oluşturulan <xref:System.Data.Linq.DataContext> yönteminin dönüş türü, saklı yordamı veya işlevi **O/R tasarımcısında**nerede bıraktığınızda olduğuna bağlı olarak farklılık gösterir. Öğeleri doğrudan mevcut bir varlık sınıfına bırakmak, varlık sınıfının dönüş türüyle <xref:System.Data.Linq.DataContext> bir yöntem oluşturur. **O/R tasarımcısının** boş bir alanına öğe bırakma, otomatik olarak oluşturulan bir tür döndüren <xref:System.Data.Linq.DataContext> yöntemi oluşturur. **Yöntem bölmesine eklendikten** sonra bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türünü değiştirebilirsiniz. Bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türünü incelemek veya değiştirmek için, bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Otomatik olarak oluşturulan türleri döndüren DataContext yöntemleri oluşturmak için

1. **Sunucu Gezgini** veya **veritabanı Gezgini**' de, çalışmakta olduğunuz veritabanının **saklı yordamlar** düğümünü genişletin.

2. İstenen saklı yordamı bulun ve **u/R tasarımcısının**boş bir alanına sürükleyin.

     <xref:System.Data.Linq.DataContext> yöntemi otomatik olarak oluşturulan bir dönüş türüyle oluşturulur ve **Yöntemler** bölmesinde görünür.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Bir varlık sınıfının dönüş türüne sahip DataContext yöntemleri oluşturmak için

1. **Sunucu Gezgini** veya **veritabanı Gezgini**' de, çalışmakta olduğunuz veritabanının **saklı yordamlar** düğümünü genişletin.

2. İstenen saklı yordamı bulun ve **o/R tasarımcısında**mevcut bir varlık sınıfının üzerine sürükleyin.

     <xref:System.Data.Linq.DataContext> yöntemi, seçilen varlık sınıfının dönüş türüyle oluşturulur ve **Yöntemler** bölmesinde görünür.

> [!NOTE]
> Mevcut <xref:System.Data.Linq.DataContext> yöntemlerinin dönüş türünü değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Basic LINQ 'e giriş](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [C# üzerinde LINQ](/dotnet/csharp/linq/linq-in-csharp)
