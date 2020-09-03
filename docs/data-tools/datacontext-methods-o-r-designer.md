---
title: DataContext yöntemleri (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b8b9d322ea9c805b7fc1ce55dbf93b72b29958af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586711"
---
# <a name="datacontext-methods-or-designer"></a>DataContext Metotları (O/R Tasarımcısı)

<xref:System.Data.Linq.DataContext> Yöntemler ( [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)bağlamında), <xref:System.Data.Linq.DataContext> bir veritabanındaki saklı yordamları ve işlevleri çalıştıran sınıfın yöntemleridir.

Sınıfı, bir <xref:System.Data.Linq.DataContext> [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] SQL Server veritabanı ile [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Bu veritabanıyla eşlenen varlık sınıfları arasında bir iletken görevi gören bir sınıftır. <xref:System.Data.Linq.DataContext>Sınıfı, bağlantı dizesi bilgilerini ve veritabanına bağlanma ve veritabanındaki verileri düzenleme yöntemlerini içerir. Varsayılan olarak, <xref:System.Data.Linq.DataContext> sınıfı, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veri sınıflarından güncelleştirilmiş verileri gönderen Yöntem gibi çağırabilmeniz gereken birkaç yöntem içerir [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] . Ayrıca, <xref:System.Data.Linq.DataContext> saklı yordamlar ve işlevlerle eşlenen ek yöntemler de oluşturabilirsiniz. Diğer bir deyişle, bu özel yöntemleri çağırmak, yöntemin eşlendiği veritabanında saklı yordamı veya işlevi çalıştırır <xref:System.Data.Linq.DataContext> . <xref:System.Data.Linq.DataContext>Herhangi bir sınıfı genişletmek için yöntemler ekleyeceğiniz gibi sınıfa yeni yöntemler ekleyebilirsiniz. Bununla birlikte, <xref:System.Data.Linq.DataContext> **O/R tasarımcısının**bağlamındaki yöntemlerle ilgili tartışmalarda bu, <xref:System.Data.Linq.DataContext> ele alınan saklı yordamlar ve işlevlerle eşlenen yöntemlerdir.

## <a name="methods-pane"></a>Yöntemler bölmesi

<xref:System.Data.Linq.DataContext>saklı yordamlar ve işlevlerle eşlenen Yöntemler **O/R tasarımcısının** **Yöntemler** bölmesinde görüntülenir. **Yöntemler** bölmesi, **varlıklar** bölmesinin (ana tasarım yüzeyi) yanındaki bölmesidir. **Yöntemler** bölmesinde <xref:System.Data.Linq.DataContext> , **O/R Tasarımcısı**kullanılarak oluşturduğunuz tüm yöntemler listelenir. Varsayılan olarak, **Yöntemler** bölmesi boştur; Yöntemler oluşturmak **Server Explorer** ve **Database Explorer** yöntemler bölmesini doldurmak için Sunucu Gezgini veya veritabanı Gezgini içindeki saklı yordamları veya Işlevleri **O/R tasarımcısına** sürükleyin <xref:System.Data.Linq.DataContext> . **Methods** Daha fazla bilgi için bkz. [nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> **O/R tasarımcısına** sağ tıklayıp Yöntemler bölmesini **Gizle** veya **Yöntemler bölmesini göster**' e tıklayarak Yöntemler bölmesini açıp kapatın veya **CTRL** + **1**klavye kısayolunu kullanın.

## <a name="two-types-of-datacontext-methods"></a>İki tür DataContext yöntemi

DataContext yöntemleri, veritabanındaki saklı yordamlar ve işlevlerle eşlenen yöntemlerdir. **O/R tasarımcısının** **Yöntemler** bölmesinde DataContext yöntemleri oluşturabilir ve ekleyebilirsiniz. İki farklı yöntem türü vardır <xref:System.Data.Linq.DataContext> ; bir veya daha fazla sonuç kümesi döndüren ve olmayanlar:

- <xref:System.Data.Linq.DataContext> bir veya daha fazla sonuç kümesi döndüren yöntemler:

   <xref:System.Data.Linq.DataContext>Uygulamanız yalnızca veritabanında saklı yordamları ve işlevleri çalıştırmak ve sonuçları döndürmek için ihtiyaç duyduğunda, bu tür bir yöntem oluşturun. Daha fazla bilgi için bkz [. nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. LINQ. ISingleResult \<T> , ve <xref:System.Data.Linq.IMultipleResults> .

- <xref:System.Data.Linq.DataContext> Sonuç kümesi döndürmeyen Yöntemler: belirli bir varlık sınıfı için ekleme, güncelleştirme ve silme gibi.

   <xref:System.Data.Linq.DataContext>Uygulamanız, [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] değiştirilen verileri bir varlık sınıfı ve veritabanı arasında kaydetmek için varsayılan davranışı kullanmak yerine saklı yordamları çalıştırmak gerektiğinde bu tür bir yöntem oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>DataContext yöntemlerinin dönüş türleri

**Sunucu Gezgini** veya **veritabanı Gezgini** içindeki saklı yordamları ve Işlevleri **O/R tasarımcısına**sürüklediğinizde, oluşturulan metodun dönüş türü, <xref:System.Data.Linq.DataContext> öğeyi nereye bıraktığınızda olduğuna göre farklılık gösterir. Öğelerin doğrudan mevcut bir varlık sınıfına düşürülme, <xref:System.Data.Linq.DataContext> varlık sınıfının dönüş türüyle bir yöntem oluşturur; öğeleri **O/R tasarımcısının** boş bir alanına bırakmak (her iki bölmede) <xref:System.Data.Linq.DataContext> otomatik olarak üretilen bir tür döndüren bir yöntem oluşturur. Otomatik olarak oluşturulan türün saklı yordam veya işlev adı ve özellikleriyle eşleşen adı vardır ve bu, saklı yordam veya işlev tarafından döndürülen alanlarla eşlenir.

> [!NOTE]
> Bir yöntemin dönüş türünü <xref:System.Data.Linq.DataContext> Yöntemler bölmesine ekledikten sonra değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için <xref:System.Data.Linq.DataContext> , bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Veritabanından O/R Designer yüzeyine sürüklediğiniz nesneler, veritabanındaki nesnelerin adına göre otomatik olarak adlandırılır. Aynı nesneyi birden çok kez sürüklerseniz, adları farklılaştırır yeni adın sonuna bir sayı eklenir. Veritabanı nesne adları boşluk veya Visual Basic veya C# ' de desteklenmeyen karakterler içerdiğinde, boşluk veya geçersiz karakter alt çizgiyle değiştirilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Saklı yordamlar](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
