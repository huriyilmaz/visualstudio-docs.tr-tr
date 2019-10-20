---
title: LINQ to SQL sınıfları tablolarda/görünümlerde eşleme (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7a06d162a9f439690753f23f74ab9923c3201716
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641959"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Nasıl yapılır: tablolar ve görünümler ile eşlenmiş LINQ to SQL sınıfları oluşturma (O/R Designer)

veritabanı tablolarıyla ve görünümleriyle eşlenmiş [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sınıflarına *varlık sınıfları*denir. Varlık sınıfı bir kayıtla eşlenir, ancak bir varlık sınıfının bireysel özellikleri bir kaydı oluşturan ayrı sütunlara eşlenir. **Sunucu Gezgini** veya **veritabanı Gezgini** tabloları veya görünümleri [Visual Studio 'daki LINQ to SQL araçlarına](../data-tools/linq-to-sql-tools-in-visual-studio2.md)sürükleyerek veritabanı tablolarını veya görünümlerini temel alan varlık sınıfları oluşturun. **O/R Tasarımcısı** sınıfları oluşturur ve [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] işlevselliğini etkinleştirmek için belirli [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] özniteliklerini uygular (<xref:System.Data.Linq.DataContext> veri iletişim ve düzenlenme özellikleri). @No__t_0 sınıfları hakkında ayrıntılı bilgi için bkz. [LINQ to SQL nesne modeli](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> Yalnızca 1:1 eşleme ilişkilerini desteklediği için **O/R Tasarımcısı** basit bir nesne ilişkisel eşleştiricisidir. Diğer bir deyişle, bir varlık sınıfı bir veritabanı tablosu veya görünümüyle yalnızca 1:1 eşleme ilişkisine sahip olabilir. Bir varlık sınıfını birden çok tabloya eşleme gibi karmaşık eşleme desteklenmez. Ancak, bir varlık sınıfını birden çok ilişkili tabloyu birleştiren bir görünümle eşleyebilirsiniz.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı tabloları veya görünümleriyle eşlenmiş LINQ to SQL sınıfları oluşturma

**Sunucu Gezgini** veya **veritabanı Gezgini** içindeki tabloları ya da görünümleri **O/R tasarımcısına** sürüklemek, güncelleştirme gerçekleştirmek için kullanılan <xref:System.Data.Linq.DataContext> yöntemlerine ek olarak varlık sınıfları oluşturur.

@No__t_0 çalışma zamanı, varsayılan olarak, güncelleştirilebilir bir varlık sınıfından değişiklikleri veritabanına geri kaydetmek için mantık oluşturur. Bu mantık, tablonun şemasını temel alır (sütun tanımları ve birincil anahtar bilgileri). Bu davranışı istemiyorsanız, varsayılan [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] çalışma zamanı davranışı yerine ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek üzere saklı yordamları kullanmak için bir varlık sınıfı yapılandırabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı tabloları veya görünümleriyle eşlenmiş LINQ to SQL sınıfları oluşturmak için

1. **Sunucu** veya **veritabanı Gezgini**' de, **Tablolar** veya **Görünümler** ' i genişletin ve uygulamanızda kullanmak istediğiniz veritabanı tablosu veya görünümünü bulun.

2. Tabloyu veya görünümü **O/R tasarımcısına**sürükleyin.

     Bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görüntülenir. Varlık sınıfı, seçili tablodaki veya görünümdeki sütunlarla eşlenen özelliklere sahiptir.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Bir nesne veri kaynağı oluşturma ve verileri bir formda görüntüleme

**O/R tasarımcısını**kullanarak varlık sınıfları oluşturduktan sonra, bir nesne veri kaynağı oluşturabilir ve [veri kaynakları penceresini](add-new-data-sources.md#data-sources-window) varlık sınıflarıyla doldurabilirsiniz.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL varlık sınıflarına dayalı bir nesne veri kaynağı oluşturmak için

1. Projeyi derlemek için **Oluştur** menüsünde **çözüm oluştur** ' a tıklayın.

2. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

4. **Veri kaynağı türü seçin** sayfasında **nesne** ' ye tıklayın ve ardından **İleri**' ye tıklayın.

5. Düğümleri genişletin ve sınıfınızı bulun ve seçin.

    > [!NOTE]
    > **Müşteri** sınıfı kullanılabilir değilse, Sihirbazı iptal edin, projeyi derleyin ve Sihirbazı yeniden çalıştırın.

6. Veri kaynağını oluşturmak ve **veri kaynakları** penceresine **Müşteri** varlık sınıfını eklemek için **son** ' a tıklayın.

7. Öğeleri **veri kaynakları** penceresinden bir form üzerine sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL nesne modeli](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Nasıl yapılır: LINQ to SQL sınıfları arasında ilişkilendirme (ilişki) oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
