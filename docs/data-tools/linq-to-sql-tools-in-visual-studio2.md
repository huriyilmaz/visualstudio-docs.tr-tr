---
title: O/R tasarımcısına genel bakış
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c02dbc42d629385671403de7131b27a449313591
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648291"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Visual Studio 'da LINQ to SQL araçları

LINQ to SQL, Microsoft tarafından yayınlanan ilk nesne ilişkisel eşleme teknolojisidir. Temel senaryolarda iyi çalışmaktadır ve Visual Studio 'da desteklenmeye devam eder, ancak artık etkin geliştirme aşamasındadır. Zaten onu kullanan eski bir uygulamayı sürdürmek veya SQL Server kullanan ve çok tablo eşleştirmesi gerektirmeyen basit uygulamalarda LINQ to SQL kullanın. Genel olarak, yeni uygulamalar, nesne ilişkisel bir Eşleyici katmanı gerektiğinde Entity Framework kullanmalıdır.

Visual Studio 'da, **nesne ilişkisel Tasarımcısı** (**O/R DESIGNER**) kullanarak SQL tablolarını temsil eden LINQ to SQL sınıflar oluşturursunuz.

**O/R tasarımcısının** tasarım yüzeyinde iki ayrı alan vardır: sol taraftaki varlıklar bölmesi ve sağ taraftaki Yöntemler bölmesi. Varlıklar bölmesi, varlık sınıflarını, ilişkilerini ve devralma hiyerarşilerini görüntüleyen ana tasarım yüzeyidir. Yöntemler bölmesi, saklı yordamlar ve işlevlerle eşlenen <xref:System.Data.Linq.DataContext> yöntemlerini görüntüleyen tasarım yüzeyidir.

**O/R Tasarımcısı** , bir veritabanındaki nesneleri temel alan [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) varlık sınıfları ve ilişkilendirmeleri (ilişkiler) oluşturmaya yönelik görsel tasarım yüzeyi sağlar. Diğer bir deyişle, **O/R Tasarımcısı** bir veritabanındaki nesnelerle eşleşen bir uygulamada nesne modeli oluşturur. Ayrıca, varlık sınıfları ve veritabanı arasında veri gönderen ve alan kesin türü belirtilmiş bir <xref:System.Data.Linq.DataContext> oluşturur. **O/R Tasarımcısı** Ayrıca, depolanan yordamları ve işlevleri, verileri döndürme ve varlık sınıflarını doldurma yöntemlerine <xref:System.Data.Linq.DataContext> eşlemek için de işlevsellik sağlar. Son olarak, **O/R Tasarımcısı** varlık sınıfları arasındaki devralma ilişkilerini tasarlama yeteneği sağlar.

## <a name="open-the-or-designer"></a>O/R tasarımcısını açın

Projenize LINQ to SQL bir varlık modeli eklemek için **proje**  > **Yeni öğe Ekle**' yi seçin ve ardından proje öğeleri listesinden **LINQ to SQL sınıflar** ' ı seçin:

![LINQ to SQL sınıfları](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio bir *. dbml* dosyası oluşturur ve bunu çözümünüze ekler. Bu, XML eşleme dosyası ve ilgili kod dosyalarıdır.

![Çözüm Gezgini LINQ to SQL sınıfları](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

*. Dbml* dosyasını seçtiğinizde, Visual Studio modeli görsel olarak oluşturmanıza olanak sağlayan **O/R tasarımcı** yüzeyini gösterir. Aşağıdaki çizimde, Northwind `Customers` sonrasında tasarımcı gösterilmektedir ve `Orders` tabloları **Sunucu Gezgini**sürüklenmiştir. Tablolar arasındaki ilişkiyi aklınızda edin.

![LINQ to SQL Tasarımcısı](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Yalnızca 1:1 eşleme ilişkilerini desteklediği için **O/R Tasarımcısı** basit bir nesne ilişkisel eşleştiricisidir. Diğer bir deyişle, bir varlık sınıfı bir veritabanı tablosu veya görünümüyle yalnızca 1:1 eşleme ilişkisine sahip olabilir. Bir varlık sınıfını birleştirilmiş bir tabloya eşleme gibi karmaşık eşleme desteklenmez; karmaşık eşleme için Entity Framework kullanın. Ayrıca, tasarımcı tek yönlü bir kod Oluşturucu olur. Bu, yalnızca tasarımcı yüzeyine yaptığınız değişikliklerin kod dosyasında yansıtıldığı anlamına gelir. Kod dosyasında el ile yapılan değişiklikler **O/R tasarımcısında**yansıtılmaz. Tasarımcı kaydedildiğinde ve kod yeniden oluşturulduğunda kod dosyasında el ile yaptığınız tüm değişiklikler üzerine yazılır. Kullanıcı kodu ekleme ve **o/r Tasarımcısı**tarafından oluşturulan sınıfları genişletme hakkında bilgi için bkz. [nasıl yapılır: o/r Tasarımcısı tarafından oluşturulan kodu genişletme](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>DataContext oluşturma ve yapılandırma

Bir projeye **LINQ to SQL Classes** öğesi ekledikten ve **O/R tasarımcısını**açtıktan sonra boş tasarım yüzeyi, yapılandırmaya hazırlanma boş bir <xref:System.Data.Linq.DataContext> temsil eder. <xref:System.Data.Linq.DataContext>, tasarım yüzeyine sürüklenen ilk öğe tarafından belirtilen bağlantı bilgileriyle yapılandırılır. Bu nedenle <xref:System.Data.Linq.DataContext>, tasarım yüzeyine bırakılan ilk öğeden bağlantı bilgileri kullanılarak yapılandırılır. @No__t_0 sınıfı hakkında daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Veritabanı tabloları ve görünümleri ile eşlenen varlık sınıfları oluşturma

Veritabanı tablolarını ve görünümlerini **Sunucu Gezgini** veya **veritabanı Gezgini** ' den **O/R tasarımcısına**sürükleyerek tablolara ve görünümlere eşlenmiş varlık sınıfları oluşturabilirsiniz. Önceki bölümde gösterildiği gibi <xref:System.Data.Linq.DataContext>, tasarım yüzeyine sürüklenen ilk öğe tarafından sağlanmış olan bağlantı bilgileriyle yapılandırılır. Farklı bir bağlantı kullanan sonraki bir öğe **O/R tasarımcısına**eklenirse, <xref:System.Data.Linq.DataContext> bağlantısını değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: tablolar ve görünümler ile eşlenmiş LINQ to SQL sınıfları oluşturma (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Saklı yordam ve işlevleri çağıran DataContext yöntemleri oluşturma

Saklı yordam ve işlevleri çağıran, bu dosyaları **Sunucu Gezgini** veya **veritabanı Gezgini** , **O/R tasarımcısına**sürükleyerek <xref:System.Data.Linq.DataContext> Yöntemler oluşturabilirsiniz. Saklı yordamlar ve işlevler, <xref:System.Data.Linq.DataContext> yöntemler olarak **O/R tasarımcısına** eklenir.

> [!NOTE]
> **Sunucu Gezgini** veya **veritabanı Gezgini** içindeki saklı yordamları ve Işlevleri **O/R tasarımcısına**sürüklediğinizde, oluşturulan <xref:System.Data.Linq.DataContext> yönteminin dönüş türü, öğeyi nereye bıraktığınızda olduğuna göre farklılık gösterir. Daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Varlık sınıfları ve veritabanı arasında veri kaydetmek için saklı yordamları kullanmak üzere bir DataContext yapılandırma

Daha önce belirtildiği gibi, saklı yordamları ve işlevleri çağıran <xref:System.Data.Linq.DataContext> Yöntemler oluşturabilirsiniz. Ayrıca, ekleme, güncelleştirme ve silme işlemleri gerçekleştiren varsayılan LINQ to SQL çalışma zamanı davranışı için kullanılan saklı yordamları da atayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Devralma ve O/R Tasarımcısı

Diğer nesneler gibi LINQ to SQL sınıflar devralma kullanabilir ve diğer sınıflardan türetilebilir. Bir veritabanında, devralma ilişkileri çeşitli yollarla oluşturulur. **O/R Tasarımcısı** , genellikle ilişkisel sistemlerde uygulanan tek tablo devralma kavramını destekler. Daha fazla bilgi için, bkz. [nasıl yapılır: O/R tasarımcısını kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL sorguları

**O/R Tasarımcısı** tarafından oluşturulan varlık sınıfları, [dil ile TÜMLEŞIK sorgu (LINQ)](/dotnet/csharp/linq/)ile kullanılmak üzere tasarlanmıştır. Daha fazla bilgi için bkz. [nasıl yapılır: bilgi sorgulama](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oluşturulan DataContext ve varlık sınıfı kodunu farklı ad alanlarına ayırın

**O/R tasarımcısı** <xref:System.Data.Linq.DataContext> **bağlam ad alanı** ve **varlık ad alanı** özellikleri sağlar. Bu özellikler <xref:System.Data.Linq.DataContext> ve varlık sınıfı kodunun hangi ad alanı içinde oluşturulduğunu belirlenir. Varsayılan olarak, bu özellikler boştur ve <xref:System.Data.Linq.DataContext> ve varlık sınıfları uygulamanın ad alanında oluşturulur. Kodu, uygulamanın ad alanından başka bir ad alanı içinde oluşturmak için, **bağlam ad alanına** ve/veya **varlık ad alanı** özelliklerine bir değer girin.

## <a name="reference-content"></a>Başvuru içeriği

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Sık sorulan sorular (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)