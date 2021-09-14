---
title: Veri LINQ to SQL tablolara/görünümlere eşleme (O-R Tasarımcısı)
description: LINQ to SQL (O/R Tasarımcısı) içinde Nesne İlişkisel Tasarımcısı varlık sınıfları (tablolar ve görünümlere eşlenen sınıflar) oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 58e6951aee44abaa4a628f39b40bae3a009f8843
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631311"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Nasıl yapılır: Tablolar ve görünümler ile eşlenen LINQ to SQL sınıfları oluşturma (O/R Tasarımcısı)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]veritabanı tablolarına ve görünümlerine eşlenen sınıflara varlık sınıfları *adı verilmektedir.* Varlık sınıfı bir kayıtla eşlerken, varlık sınıfının tek tek özellikleri bir kaydın tek tek sütunlarıyla eşler. Veritabanı tablolarını veya görünümlerini temel alan varlık sınıfları oluşturmak için  Sunucu Gezgini **veya Veritabanı Gezgini'deki** LINQ to SQL [araçlarına Visual Studio.](../data-tools/linq-to-sql-tools-in-visual-studio2.md) **O/R Tasarımcısı** sınıfları üretir ve işlevselliği etkinleştirmek için belirli öznitelikleri [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] uygular [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] (veri iletişimi ve düzenleme <xref:System.Data.Linq.DataContext> özellikleri). Sınıflar hakkında ayrıntılı [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] bilgi için [bkz. LINQ to SQL modeli.](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)

> [!NOTE]
> **O/R Tasarımcısı yalnızca** 1:1 eşleme ilişkilerini desteklediği için basit bir nesne ilişkisel eşleyicidir. Başka bir deyişle, varlık sınıfı bir veritabanı tablosu veya görünümü ile yalnızca 1:1 eşleme ilişkisine sahip olabilir. Varlık sınıfını birden çok tabloyla eşleme gibi karmaşık eşleme desteklenmiyor. Ancak, bir varlık sınıfını birden çok ilişkili tabloyla bire bir görünüme eşebilirsiniz.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı LINQ to SQL görünümlere eşlenmiş veritabanı sınıfları oluşturma

Tabloları veya görünümleri **Sunucu Gezgini** veya **Veritabanı Gezgini** **O/R Tasarımcısı'na** sürüklemek, güncelleştirmeleri gerçekleştirmek için kullanılan yöntemlere ek olarak <xref:System.Data.Linq.DataContext> varlık sınıfları oluşturur.

Varsayılan olarak, [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] çalışma zamanı, ekleyebilirsiniz varlık sınıfındaki değişiklikleri veritabanına geri kaydetmek için mantık oluşturur. Bu mantık, tablonun şemasını (sütun tanımları ve birincil anahtar bilgileri) temel alır. Bu davranışı istemiyorsanız, varsayılan çalışma zamanı davranışını kullanmak yerine ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için saklı yordamları kullanmak üzere bir varlık [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sınıfı yapılandırabilirsiniz. Daha fazla bilgi için bkz. Nasıl kullanılır: Güncelleştirmeleri, eklemeleri ve silmeleri gerçekleştirmek için [saklı yordamları atama (O/R Tasarımcısı)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı LINQ to SQL görünümlerine eşlenmiş bir sınıf oluşturmak için

1. Sunucu **veya** **Veritabanı Gezgini'da** Tablolar **veya** **Görünümler'i** genişletin ve uygulamanıza eklemek istediğiniz veritabanı tablosu veya görünümünü bulun.

2. Tabloyu veya görünümü **O/R Tasarımcısı'na sürükleyin.**

     Bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görünür. Varlık sınıfı, seçili tablo veya görünümde sütunlara eşlene özelliklere sahiptir.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Nesne veri kaynağı oluşturma ve verileri formda görüntüleme

**O/R** Tasarımcısını kullanarak varlık sınıfları oluşturduk sonra, bir nesne veri kaynağı oluşturabilir ve Veri Kaynakları penceresini [varlık](add-new-data-sources.md#data-sources-window) sınıfları ile doldurmak için.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Varlık sınıflarını temel alan bir nesne LINQ to SQL oluşturmak için

1. Projenizi **derlemek** için Derleme **menüsünde Çözümü Derleme'ye** tıklayın.

2. Veri Kaynakları **penceresini açmak için** Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

3. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

4. Veri **Kaynağı** Türü **Seçin sayfasında Nesne'ye ve** ardından Sonraki 'ye **tıklayın.**

5. Düğümleri genişletin ve sınıfını bulup seçin.

    > [!NOTE]
    > Customer **sınıfı** kullanılamıyorsa, sihirbazı iptal edin, projeyi derlemeyi ve sihirbazı yeniden çalıştırın.

6. Veri **kaynağını** oluşturmak ve Müşteri varlık sınıfını Veri Kaynakları **penceresine** eklemek için **Son'a** tıklayın.

7. Veri Kaynakları **penceresindeki öğeleri** bir forma sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Adım adım kılavuz: LINQ to SQL sınıfları oluşturma (O-R Tasarımcısı)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL nesne modeli](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Nasıl yapılır: LINQ to SQL sınıfları arasında ilişkilendirme (ilişki) oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
