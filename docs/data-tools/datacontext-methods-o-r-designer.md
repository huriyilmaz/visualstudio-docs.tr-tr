---
title: DataContext Yöntemleri (O-R Tasarımcısı)
description: Veri koruma araçları bağlamında DataContext LINQ to SQL anlama Visual Studio. Bu yöntemler, saklı yordamları ve işlevleri bir veritabanında çalıştırabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 892005ee4f88b1ffc4cd456a2e4ccbfe3e0ee50b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037011"
---
# <a name="datacontext-methods-or-designer"></a>DataContext Metotları (O/R Tasarımcısı)

<xref:System.Data.Linq.DataContext>yöntemleri (LINQ to SQL [Araçları bağlamında Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)), bir veritabanında saklı yordamları ve işlevleri çalıştıran <xref:System.Data.Linq.DataContext> sınıfının yöntemleridir.

sınıfı, bir veritabanı ile bu veritabanıyla eşlenen varlık sınıfları SQL Server bir bağlantı <xref:System.Data.Linq.DataContext> [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] olarak hareket [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] eder. sınıfı, bağlantı dizesi bilgilerini ve bir veritabanına bağlanma <xref:System.Data.Linq.DataContext> ve veritabanındaki verileri manipüle etmeye ilişkin yöntemleri içerir. Varsayılan olarak, sınıfı sınıflardan veritabanına güncelleştirilmiş veri gönderen yöntemi gibi <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağırabilirsiniz [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] çeşitli yöntemler içerir. Saklı yordamlara ve <xref:System.Data.Linq.DataContext> işlevlere eşlene ek yöntemler de oluşturabilirsiniz. Başka bir deyişle, bu özel yöntemleri çağırma yöntemin eşlenmiş olduğu veritabanında saklı yordamı <xref:System.Data.Linq.DataContext> veya işlevi çalıştırır. Sınıfına, herhangi bir sınıfı <xref:System.Data.Linq.DataContext> genişletmek için yöntemler ekley istediğiniz gibi yeni yöntemler ebilirsiniz. Ancak, O/R Tasarımcısı bağlamında yöntemlerle ilgili tartışmalarda, tartışılan saklı yordamlar ve işlevlerle <xref:System.Data.Linq.DataContext>  <xref:System.Data.Linq.DataContext> eşlene yöntemlerdir.

## <a name="methods-pane"></a>Yöntemler bölmesi

<xref:System.Data.Linq.DataContext>saklı yordamlar ve işlevlerle eşlendi yöntemleri, **O/R** **Tasarımcısı'nın** Yöntemler bölmesinde görüntülenir. Yöntemler **bölmesi,** Varlıklar bölmesinin (ana tasarım **yüzeyi)** yan tarafındaki bölmedir. Yöntemler **bölmesi,** <xref:System.Data.Linq.DataContext> **O/R** Tasarımcısını kullanarak oluşturduğunuz tüm yöntemleri listeler. Varsayılan olarak Yöntemler **bölmesi boştur;** saklı yordamları veya işlevleri **Sunucu Gezgini** veya **Veritabanı Gezgini** oluşturmak ve Yöntemler bölmesini doldurmak için **O/R** <xref:System.Data.Linq.DataContext> **Tasarımcısı'na** sürükleyin. Daha fazla bilgi için, [bkz. How to: Create DataContext methodsapped to stored procedures and functions (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Yöntemler bölmesini açmak ve kapatmak için **O/R** Tasarımcısı'na  sağ tıklayın ve ardından Yöntemler Bölmesini Gizle'ye veya Yöntemler Bölmesini Göster'e tıklayın ya da **CTRL 1** klavye + **kısayolunu kullanın.**

## <a name="two-types-of-datacontext-methods"></a>İki tür DataContext yöntemi

DataContext yöntemleri, veritabanındaki saklı yordamlara ve işlevlere eşilen yöntemlerdir. DataContext yöntemlerini O/R **Tasarımcısı'nın** Yöntemler bölmesinde **oluşturabilir ve ekleyebilirsiniz.** İki farklı yöntem türü vardır: bir veya daha fazla sonuç kümesi dönüşenler <xref:System.Data.Linq.DataContext> ve bunu yapmayanlar:

- <xref:System.Data.Linq.DataContext> bir veya daha fazla sonuç kümesi dönüşen yöntemler:

   Yalnızca uygulamanın veritabanında saklı yordamları ve işlevleri çalıştırması ve sonuçları iade etmek <xref:System.Data.Linq.DataContext> için ihtiyacı olduğunda bu tür bir yöntem oluşturun. Daha fazla bilgi için bkz. Nasıl kullanılır: Saklı yordamlara ve işlevlere [eşlenmiş DataContext yöntemleri oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult \<T> ve <xref:System.Data.Linq.IMultipleResults> .

- <xref:System.Data.Linq.DataContext> belirli bir varlık sınıfı için Eklemeler, Güncelleştirmeler ve Silmeler gibi sonuç kümelerini geri dönmeyen yöntemler.

   Bir varlık sınıfı ile veritabanı arasında değiştirilen verileri kaydetmeye ilişkin varsayılan davranışı kullanmak yerine, uygulamanıza saklı yordamlar çalıştırmak zorunda olduğunda <xref:System.Data.Linq.DataContext> bu tür bir yöntem [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] oluşturun. Daha fazla bilgi için bkz. Nasıl kullanılır: Güncelleştirmeleri, eklemeleri ve silmeleri gerçekleştirmek için [saklı yordamları atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>DataContext Yöntemlerinin Dönüş Türleri

Saklı yordamları ve **işlevleri Sunucu Gezgini** veya  Veritabanı Gezgini **O/R Tasarımcısı'na** sürüklerken, oluşturulan yöntemin dönüş türü, öğeyi bıraktırmanıza bağlı olarak <xref:System.Data.Linq.DataContext> farklılık gösterir. Öğeleri doğrudan mevcut bir varlık sınıfına bırakmak varlık sınıfının dönüş türüyle bir yöntem <xref:System.Data.Linq.DataContext> oluşturur; **öğeleri O/R Tasarımcısı'nın** boş bir alanına bırakmak (iki bölmede de) otomatik olarak oluşturulan bir tür döndüren <xref:System.Data.Linq.DataContext> bir yöntem oluşturur. Otomatik olarak oluşturulan tür saklı yordam veya saklı yordam veya işlev tarafından döndürülen alanlarla eşleşen işlev adı ve özelliklerine sahiptir.

> [!NOTE]
> Bir yöntemi yöntemler bölmesine <xref:System.Data.Linq.DataContext> ekledikten sonra dönüş türünü değiştirebilirsiniz. Bir yöntemin dönüş türünü incelemek veya değiştirmek için, yöntemi seçin ve Özellikler penceresinde <xref:System.Data.Linq.DataContext> **Dönüş** Türü **özelliğini** inceler. Daha fazla bilgi için, bkz. How to: Change the return [type of a DataContext method (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Veritabanından O/R Tasarımcısı yüzeyine sürüklenen nesneler, veritabanındaki nesnelerin adına göre otomatik olarak adlandırılmıştır. Aynı nesneyi birden çok kez sürüklersanız, adları ayırt etmek için yeni adın sonuna bir sayı eklenir. Veritabanı nesne adları boşluk içerdiğinde veya Visual Basic veya C# içinde desteklenmiyorsa, boşluk veya geçersiz karakter bir alt çizgiyle değiştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Saklı yordamlar](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Nasıl yapılır: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [adım adım kılavuz: LINQ to SQL sınıfları oluşturma (O-R Tasarımcısı)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
