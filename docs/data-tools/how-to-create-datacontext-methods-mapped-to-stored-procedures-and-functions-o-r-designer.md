---
title: DataContext metotlarını sprocs ve işlevlerle eşleyin (O-R Designer)
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0c1545313ba6852765bc86d57f2149b4481e5f57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282143"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)

Saklı yordamları ve işlevleri Yöntem olarak **O/R tasarımcısına** ekleyebilirsiniz <xref:System.Data.Linq.DataContext> . Yöntemi çağırmak ve gerekli parametreleri geçirmek, veritabanında saklı yordamı veya işlevi çalıştırır ve yöntemin dönüş türündeki verileri döndürür <xref:System.Data.Linq.DataContext> . Yöntemler hakkında ayrıntılı bilgi için <xref:System.Data.Linq.DataContext> bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Ayrıca [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] , değişiklikler varlık sınıflarından veritabanına kaydedildiğinde ekleme, güncelleştirme ve silme işlemleri gerçekleştiren varsayılan çalışma zamanı davranışını geçersiz kılmak için saklı yordamları kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>DataContext yöntemleri oluşturma

<xref:System.Data.Linq.DataContext>Saklı yordamları veya işlevleri <strong>Sunucu Gezgini veya * * veritabanı Gezgini</strong> ' dan **O/R tasarımcısına**sürükleyerek Yöntemler oluşturabilirsiniz.

> [!NOTE]
> Oluşturulan metodun dönüş türü, <xref:System.Data.Linq.DataContext> saklı yordamı veya Işlevi **O/R tasarımcısında**nerede bıraktığınızda olduğuna bağlı olarak farklılık gösterir. Öğelerin doğrudan mevcut bir varlık sınıfına düşürülme, <xref:System.Data.Linq.DataContext> varlık sınıfının dönüş türüyle bir yöntem oluşturur. **O/R tasarımcısının** boş bir alanına öğe bırakma, <xref:System.Data.Linq.DataContext> otomatik olarak oluşturulan bir tür döndüren bir yöntem oluşturur. Bir yöntemin dönüş türünü, <xref:System.Data.Linq.DataContext> **Yöntemler** bölmesine eklendikten sonra değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için <xref:System.Data.Linq.DataContext> , bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Otomatik olarak oluşturulan türleri döndüren DataContext yöntemleri oluşturmak için

1. **Sunucu Gezgini** veya **veritabanı Gezgini**' de, çalışmakta olduğunuz veritabanının **saklı yordamlar** düğümünü genişletin.

2. İstenen saklı yordamı bulun ve **u/R tasarımcısının**boş bir alanına sürükleyin.

     <xref:System.Data.Linq.DataContext>Yöntemi otomatik olarak oluşturulan bir dönüş türüyle oluşturulur ve **Yöntemler** bölmesinde görünür.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Bir varlık sınıfının dönüş türüne sahip DataContext yöntemleri oluşturmak için

1. **Sunucu Gezgini** veya **veritabanı Gezgini**' de, çalışmakta olduğunuz veritabanının **saklı yordamlar** düğümünü genişletin.

2. İstenen saklı yordamı bulun ve **o/R tasarımcısında**mevcut bir varlık sınıfının üzerine sürükleyin.

     <xref:System.Data.Linq.DataContext>Yöntemi, seçilen varlık sınıfının dönüş türüyle oluşturulur ve **Yöntemler** bölmesinde görünür.

> [!NOTE]
> Mevcut yöntemlerin dönüş türünü değiştirme hakkında daha fazla bilgi için <xref:System.Data.Linq.DataContext> bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Basic'de LINQ'e Giriş](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [C# üzerinde LINQ](/dotnet/csharp/linq/linq-in-csharp)
