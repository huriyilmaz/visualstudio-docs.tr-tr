---
title: 'Nasıl yapılır: tablolar ve görünümlerle eşlenen LINQ to SQL sınıfları oluşturma (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a63e81abcae508487afa40d0778c0f9e9b9caf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665921"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Nasıl yapılır: Tablolar ve görünümler ile eşlenen LINQ to SQL sınıfları oluşturma (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Veritabanı tablolarıyla ve görünümleriyle eşlenmiş LINQ to SQL sınıflarına *varlık sınıfları*denir. Varlık sınıfı bir kayıtla eşlenir, ancak bir varlık sınıfının bireysel özellikleri bir kaydı oluşturan ayrı sütunlara eşlenir. **Sunucu Gezgini** / **veritabanı Gezgini** tabloları veya görünümleri [Visual Studio 'daki LINQ to SQL araçlarına](../data-tools/linq-to-sql-tools-in-visual-studio2.md)sürükleyerek veritabanı tablolarını veya görünümlerini temel alan varlık sınıfları oluşturun. , [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Sınıfları oluşturur ve belirli [! Etkinleştirilecek öznitelikleri LINQ to SQL [! LINQ to SQL işlevselliği (öğesinin veri iletişimi ve düzenlenme özellikleri <xref:System.Data.Linq.DataContext> ). [! Hakkında ayrıntılı bilgi için Sınıfları LINQ to SQL, bkz. [LINQ to SQL nesne modeli](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Yalnızca 1:1 eşleme ilişkilerini desteklediğinden basit bir nesne ilişkisel eşleştiricisidir. Diğer bir deyişle, bir varlık sınıfı bir veritabanı tablosu veya görünümüyle yalnızca 1:1 eşleme ilişkisine sahip olabilir. Bir varlık sınıfını birden çok tabloya eşleme gibi karmaşık eşleme desteklenmez. Ancak, bir varlık sınıfını birden çok ilişkili tabloyu birleştiren bir görünümle eşleyebilirsiniz.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı tabloları veya görünümleriyle eşlenmiş LINQ to SQL sınıfları oluşturma
 Sunucu Gezgini veritabanı Gezgini tabloları veya görünümleri **Server Explorer** / **Database Explorer** , [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] <xref:System.Data.Linq.DataContext> güncelleştirme yapmak için kullanılan yöntemlerin yanı sıra varlık sınıfları oluşturur.

 Varsayılan olarak, [! LINQ to SQL Runtime, güncelleştirilebilir bir varlık sınıfından değişiklikleri veritabanına kaydetmek için mantık oluşturur. Bu mantık, tablonun şemasını temel alır (sütun tanımları ve birincil anahtar bilgileri). Bu davranışı istemiyorsanız, varsayılan [! yerine ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için saklı yordamları kullanmak üzere bir varlık sınıfı yapılandırabilirsiniz. Çalışma zamanı davranışı LINQ to SQL. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Veritabanı tabloları veya görünümleriyle eşlenmiş LINQ to SQL sınıfları oluşturmak için

1. **Sunucu** / **veritabanı Gezgini**' de **Tablolar** veya **Görünümler** ' i genişletin ve uygulamanızda kullanmak istediğiniz veritabanı tablosu veya görünümünü bulun.

2. Tabloyu veya görünümü üzerine sürükleyin [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

     Bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görüntülenir. Varlık sınıfı, seçili tablodaki veya görünümdeki sütunlarla eşlenen özelliklere sahiptir.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Bir nesne veri kaynağı oluşturma ve verileri bir formda görüntüleme
 Kullanarak varlık sınıfları oluşturduktan sonra [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , bir nesne veri kaynağı oluşturabilir ve [veri kaynakları penceresini](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) varlık sınıflarıyla doldurabilirsiniz.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL varlık sınıflarına dayalı bir nesne veri kaynağı oluşturmak için

1. Projeyi derlemek için **Oluştur** menüsünde **çözüm oluştur** ' a tıklayın.

2. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

3. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

4. **Veri kaynağı türü seçin** sayfasında **nesne** ' ye tıklayın ve ardından **İleri**' ye tıklayın.

5. Düğümleri genişletin ve sınıfınızı bulun ve seçin.

    > [!NOTE]
    > **Müşteri** sınıfı kullanılabilir değilse, Sihirbazı iptal edin, projeyi derleyin ve Sihirbazı yeniden çalıştırın.

6. Veri kaynağını oluşturmak ve **veri kaynakları** penceresine **Müşteri** varlık sınıfını eklemek için **son** ' a tıklayın.

7. Öğeleri **veri kaynakları** penceresinden bir form üzerine sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki LINQ to SQL Araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [DataContext Metotları (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: Saklı yordamlarla eşlenen DataContext metotları oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL Nesne Modeli](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [İzlenecek yol: varlık sınıflarına doğrulama ekleme](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Nasıl yapılır: LINQ to SQL sınıfları arasında ilişkilendirme (ilişki) oluşturma (O/R Tasarımcısı)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)