---
title: DataContext yöntemleri (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0e81f2337931f565e0068a852bf9b8284350690c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648535"
---
# <a name="datacontext-methods-or-designer"></a>DataContext Metotları (O/R Tasarımcısı)

<xref:System.Data.Linq.DataContext> Yöntemleri ( [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)bağlamında), bir veritabanındaki saklı yordamları ve işlevleri çalıştıran <xref:System.Data.Linq.DataContext> sınıfının yöntemlerdir.

@No__t_0 sınıfı, bir SQL Server veritabanı ile bu veritabanıyla eşlenen [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] varlık sınıfları arasında bir iletken görevi gören bir [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sınıfıdır. @No__t_0 sınıfı, bağlantı dizesi bilgilerini ve veritabanına bağlanma ve veritabanındaki verileri düzenleme yöntemlerini içerir. Varsayılan olarak <xref:System.Data.Linq.DataContext> sınıfı, [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sınıflardan veritabanına güncelleştirilmiş verileri gönderen <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yöntemi gibi çağırabilmeniz için çeşitli yöntemler içerir. Ayrıca, saklı yordamlar ve işlevlerle eşlenen ek <xref:System.Data.Linq.DataContext> yöntemler de oluşturabilirsiniz. Diğer bir deyişle, bu özel yöntemleri çağırmak, <xref:System.Data.Linq.DataContext> yönteminin eşlendiği veritabanında saklı yordamı veya işlevi çalıştırır. Herhangi bir sınıfı genişletmek için yöntemler ekleyeceğiniz gibi <xref:System.Data.Linq.DataContext> sınıfına yeni yöntemler ekleyebilirsiniz. Bununla birlikte, **O/R tasarımcısının**bağlamındaki <xref:System.Data.Linq.DataContext> yöntemleriyle ilgili tartışmalarda bu, ele alınan saklı yordamlar ve işlevlerle eşlenen <xref:System.Data.Linq.DataContext> yöntemlerdir.

## <a name="methods-pane"></a>Yöntemler bölmesi

saklı yordamlar ve işlevlerle eşlenen <xref:System.Data.Linq.DataContext> Yöntemler, **O/R tasarımcısının** **Yöntemler** bölmesinde görüntülenir. **Yöntemler** bölmesi, **varlıklar** bölmesinin (ana tasarım yüzeyi) yanındaki bölmesidir. **Yöntemler** bölmesi, **O/R tasarımcısını**kullanarak oluşturduğunuz tüm <xref:System.Data.Linq.DataContext> yöntemlerini listeler. Varsayılan olarak, **Yöntemler** bölmesi boştur; <xref:System.Data.Linq.DataContext> Yöntemler oluşturmak ve **Yöntemler** bölmesini doldurmak için **Sunucu Gezgini** veya **veritabanı Gezgini** içindeki saklı yordamları veya işlevleri **O/R tasarımcısına** sürükleyin. Daha fazla bilgi için bkz. [nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> **O/R tasarımcısına** sağ tıklayıp Yöntemler bölmesini **Gizle** veya **Yöntemler bölmesini göster**' e tıklayarak ve **CTRL** +**1**klavye kısayolunu kullanarak Yöntemler bölmesini açın ve kapatın.

## <a name="two-types-of-datacontext-methods"></a>İki tür DataContext yöntemi

DataContext yöntemleri, veritabanındaki saklı yordamlar ve işlevlerle eşlenen yöntemlerdir. **O/R tasarımcısının** **Yöntemler** bölmesinde DataContext yöntemleri oluşturabilir ve ekleyebilirsiniz. @No__t_0 yöntemlerinin iki farklı türü vardır; bir veya daha fazla sonuç kümesi döndürenler ve olmayanlar:

- bir veya daha fazla sonuç kümesi döndüren <xref:System.Data.Linq.DataContext> Yöntemler:

   Uygulamanız yalnızca veritabanında saklı yordamları ve işlevleri çalıştırmak ve sonuçları döndürmek için ihtiyaç duyduğunda, bu tür bir <xref:System.Data.Linq.DataContext> yöntemi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: saklı yordamlar ve işlevler (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. LINQ. ISingleResult \<T > ve <xref:System.Data.Linq.IMultipleResults> Ile eşlenmiş DataContext yöntemleri oluşturma.

- Sonuç kümesi döndürmeyen <xref:System.Data.Linq.DataContext> Yöntemler: belirli bir varlık sınıfı için ekleme, güncelleştirme ve silme gibi.

   Uygulamanız, değiştirilen verileri bir varlık sınıfı ve veritabanı arasında kaydetmek için varsayılan [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] davranışını kullanmak yerine, saklı yordamları çalıştırmak zorunda olduğunda bu tür bir <xref:System.Data.Linq.DataContext> yöntemi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>DataContext yöntemlerinin dönüş türleri

**Sunucu Gezgini** veya **veritabanı Gezgini** içindeki saklı yordamları ve Işlevleri **O/R tasarımcısına**sürüklediğinizde, oluşturulan <xref:System.Data.Linq.DataContext> yönteminin dönüş türü, öğeyi nereye bıraktığınızda olduğuna göre farklılık gösterir. Öğeleri doğrudan mevcut bir varlık sınıfına bırakmak, varlık sınıfının dönüş türüyle <xref:System.Data.Linq.DataContext> yöntemi oluşturur; öğeleri **O/R tasarımcısının** boş bir alanına bırakmak (her bölmede) otomatik olarak oluşturulan bir tür döndüren <xref:System.Data.Linq.DataContext> yöntemi oluşturur. Otomatik olarak oluşturulan türün saklı yordam veya işlev adı ve özellikleriyle eşleşen adı vardır ve bu, saklı yordam veya işlev tarafından döndürülen alanlarla eşlenir.

> [!NOTE]
> @No__t_0 yönteminin dönüş türünü Yöntemler bölmesine ekledikten sonra değiştirebilirsiniz. Bir <xref:System.Data.Linq.DataContext> yönteminin dönüş türünü incelemek veya değiştirmek için, bunu seçin ve **Özellikler** penceresinde **dönüş türü** özelliğini inceleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Veritabanından O/R Designer yüzeyine sürüklediğiniz nesneler, veritabanındaki nesnelerin adına göre otomatik olarak adlandırılır. Aynı nesneyi birden çok kez sürüklerseniz, adları farklılaştırır yeni adın sonuna bir sayı eklenir. Veritabanı nesne adları boşluk veya Visual Basic veya C#içinde desteklenmeyen karakterler içerdiğinde, boşluk veya geçersiz karakter alt çizgiyle değiştirilmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Saklı yordamlar](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)