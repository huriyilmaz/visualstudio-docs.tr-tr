---
title: LINQ to SQL araçları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 470cfabd54fa5f2b92001a635477c60d45fac538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651511"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Visual Studio'daki LINQ to SQL Araçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL, Microsoft tarafından yayınlanan ilk nesne ilişkisel eşleme teknolojisidir. Temel senaryolarda iyi çalışmaktadır ve Visual Studio 'da desteklenmeye devam eder, ancak artık etkin geliştirme aşamasındadır. Zaten kullanmakta olan eski bir uygulamayı sürdürirken veya SQL Server kullanan ve çok tablo eşleştirmesi gerektirmeyen basit uygulamalarda LINQ to SQL kullanın. Genel olarak, yeni uygulamalar, nesne ilişkisel bir Eşleyici katmanı gerektiğinde Entity Framework kullanmalıdır.

 Visual Studio 'da, kullanarak SQL tablolarını temsil eden LINQ to SQL sınıflar oluşturursunuz [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 , [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Tasarım yüzeyinde iki ayrı alana sahiptir: sol taraftaki varlıklar bölmesi ve sağ taraftaki Yöntemler bölmesi. Varlıklar bölmesi, varlık sınıflarını, ilişkilerini ve devralma hiyerarşilerini görüntüleyen ana tasarım yüzeyidir. Yöntemler bölmesi, <xref:System.Data.Linq.DataContext> saklı yordamlar ve işlevlerle eşlenmiş yöntemleri görüntüleyen tasarım yüzeyidir.

 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ), Bir veritabanındaki nesneleri temel alan [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) varlık sınıfları ve ilişkilendirmeleri (ilişkiler) oluşturmak için görsel tasarım yüzeyi sağlar. Diğer bir deyişle, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] bir veritabanındaki nesnelerle eşleşen bir uygulamada nesne modeli oluşturmak için kullanılır. Ayrıca <xref:System.Data.Linq.DataContext> , varlık sınıfları ve veritabanı arasında veri göndermek ve almak için kullanılan bir kesin türü oluşturur. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Ayrıca, depolanan yordamları ve işlevleri <xref:System.Data.Linq.DataContext> veri döndürme ve varlık sınıflarını doldurma yöntemlerine eşlemek için de işlevsellik sağlar. Son olarak, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] varlık sınıfları arasındaki devralma ilişkilerini tasarlama yeteneği sağlar.

## <a name="opening-the-or-designer"></a>O/R tasarımcısını açma
 Projenize LINQ to SQL bir varlık modeli eklemek için **proje &#124; yeni öğe Ekle** ' yi seçin ve ardından proje öğeleri listesinden  **LINQ to SQL sınıflar** ' ı seçin:

 ![LINQ to SQL sınıfları](../data-tools/media/raddata-linq-to-sql-classes.png "radveri LINQ to SQL sınıfları")

 Visual Studio bir. dbml dosyası oluşturur ve bunu çözümünüze ekler. Bu, XML eşleme dosyası ve ilgili kod dosyalarıdır.

 ![Çözüm Gezgini LINQ to SQL sınıfları](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "Çözüm Gezgini içindeki radveri LINQ to SQL sınıfları")

 . Dbml dosyasını seçtiğinizde, Visual Studio modeli görsel olarak oluşturmanıza olanak sağlayan O/R tasarımcı yüzeyini gösterir. Aşağıdaki çizimde, Northwind Customers ve Orders tablolarının Sunucu Gezgini sürüklenmesi sonrasında tasarımcı gösterilmektedir. Tablolar arasındaki ilişkiyi aklınızda edin.

 ![LINQ to SQL Tasarımcısı](../data-tools/media/raddata-linq-to-sql-designer.png "radveri LINQ to SQL Tasarımcısı")

> [!IMPORTANT]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Yalnızca 1:1 eşleme ilişkilerini desteklediğinden basit bir nesne ilişkisel eşleştiricisidir. Diğer bir deyişle, bir varlık sınıfı bir veritabanı tablosu veya görünümüyle yalnızca 1:1 eşleme ilişkisine sahip olabilir. Bir varlık sınıfını birleştirilmiş bir tabloya eşleme gibi karmaşık eşleme desteklenmez; karmaşık eşleme için Entity Framework kullanın. Ayrıca, tasarımcı tek yönlü bir kod Oluşturucu olur. Bu, yalnızca tasarımcı yüzeyine yaptığınız değişikliklerin kod dosyasında yansıtıldığı anlamına gelir. Kod dosyasında el ile yapılan değişiklikler ' de yansıtılmaz [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Tasarımcı kaydedildiğinde ve kod yeniden oluşturulduğunda kod dosyasında el ile yaptığınız tüm değişiklikler üzerine yazılır. Kullanıcı kodu ekleme ve tarafından oluşturulan sınıfları genişletme hakkında daha fazla bilgi için [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] bkz. [nasıl yapılır: O/R Tasarımcısı tarafından oluşturulan kodu genişletme](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>DataContext oluşturma ve yapılandırma
 Bir projeye **LINQ to SQL Classes** öğesi ekledikten ve öğesini açtıktan sonra [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] boş tasarım yüzeyi, yapılandırmaya yönelik boş bir <xref:System.Data.Linq.DataContext> hazırlık gösterir. , <xref:System.Data.Linq.DataContext> tasarım yüzeyine sürüklenen ilk öğe tarafından belirtilen bağlantı bilgileriyle yapılandırılır. Bu nedenle, <xref:System.Data.Linq.DataContext> tasarım yüzeyine bırakılan ilk öğeden bağlantı bilgileri kullanılarak yapılandırılır. Sınıf hakkında daha fazla bilgi için <xref:System.Data.Linq.DataContext> bkz. [DataContext metotları (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Veritabanı tabloları ve görünümleri ile eşlenen varlık sınıfları oluşturma
 Veritabanı tablolarını ve görünümlerini **Sunucu Gezgini** / **veritabanı Gezgini** üzerine sürükleyerek tablolar ve görünümlere eşlenmiş varlık sınıfları oluşturabilirsiniz [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Önceki bölümde gösterildiği gibi,, <xref:System.Data.Linq.DataContext> tasarım yüzeyine sürüklenen ilk öğe tarafından sağlanmış olan bağlantı bilgileriyle yapılandırılır. Farklı bir bağlantı kullanan sonraki bir öğe öğesine eklenirse, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] bağlantısını değiştirebilirsiniz <xref:System.Data.Linq.DataContext> . Daha fazla bilgi için bkz. [nasıl yapılır: tablolar ve görünümler ile eşlenmiş LINQ to SQL sınıfları oluşturma (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Saklı yordamları ve Işlevleri çağıran DataContext yöntemleri oluşturma
 <xref:System.Data.Linq.DataContext>Saklı yordamları ve işlevleri çağıran ve **Sunucu Gezgini** / **veritabanı Gezgini** ' den üzerine sürükleyerek Yöntemler oluşturabilirsiniz [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Saklı yordamlar ve işlevler [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , öğesinin as yöntemlerine eklenir <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> **Sunucu Gezgini**veritabanı Gezgini içindeki saklı yordamları ve işlevleri / **Database Explorer** üzerine sürüklediğinizde [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , oluşturulan metodun dönüş türü, <xref:System.Data.Linq.DataContext> öğeyi nereye bıraktığınızda olduğuna göre farklılık gösterir. Daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Varlık sınıfları ve veritabanı arasında veri kaydetmek için saklı yordamları kullanmak üzere DataContext yapılandırma
 Daha önce belirtildiği gibi, <xref:System.Data.Linq.DataContext> saklı yordamları ve işlevleri çağıran Yöntemler oluşturabilirsiniz. Ayrıca, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] ekleme, güncelleştirme ve silme işlemleri gerçekleştiren varsayılan çalışma zamanı davranışı için kullanılabilecek saklı yordamları da atayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Devralma ve O/R Tasarımcısı
 Diğer nesneler gibi, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sınıflar devralma kullanabilir ve diğer sınıflardan türetilebilir. Bir veritabanında, devralma ilişkileri çeşitli yollarla oluşturulur. , [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Genellikle ilişkisel sistemlerde uygulanan tek tablo devralma kavramını destekler. Daha fazla bilgi için, bkz. [nasıl yapılır: O/R tasarımcısını kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>LINQ to SQL Sorguları
 Tarafından oluşturulan varlık sınıfları [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] [LINQ (dil Ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)ile kullanılmak üzere tasarlanmıştır. Daha fazla bilgi için bkz. [nasıl yapılır: bilgi sorgulama](https://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Oluşturulan DataContext ve varlık sınıfı kodunu farklı ad alanlarına ayırma
 , [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Üzerinde **bağlam ad alanı** ve **varlık ad alanı** özellikleri sağlar <xref:System.Data.Linq.DataContext> . Bu özellikler, hangi ad alanının <xref:System.Data.Linq.DataContext> ve varlık sınıfı kodunun oluşturulduğunu belirlenir. Varsayılan olarak, bu özellikler boştur ve <xref:System.Data.Linq.DataContext> ve varlık sınıfları uygulamanın ad alanında oluşturulur. Kodu, uygulamanın ad alanından başka bir ad alanı içinde oluşturmak için, **bağlam ad alanına** ve/veya **varlık ad alanı** özelliklerine bir değer girin.

## <a name="in-this-section"></a>Bu bölümde
 [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) Yöntemlerin ne <xref:System.Data.Linq.DataContext> olduğunu ve nasıl oluşturulacağını açıklar.

 [Veri sınıfı devralma (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md) Tek tablo devralma kavramı ve içinde nasıl uygulandığı açıklanmaktadır [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Nasıl yapılır: tablolar ve görünümler ile eşlenmiş LINQ to SQL sınıfları oluşturma (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) Bir veritabanındaki tablolarla ve görünümlerle eşlenmiş varlık sınıflarının nasıl oluşturulacağını açıklar.

 [Nasıl yapılır: LINQ to SQL sınıfları arasında ilişkilendirme (ilişki) oluşturma (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) Varlık sınıfları arasında bir ilişkinin nasıl oluşturulacağını açıklar [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] .

 [Nasıl yapılır: saklı yordamlar ve işlevlerle eşlenen DataContext yöntemleri oluşturma (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) <xref:System.Data.Linq.DataContext> Çağrıldığında saklı yordamları veya işlevleri çalıştıran yöntemlerin nasıl oluşturulduğunu açıklar.

 [Nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) ' Nin <xref:System.Data.Linq.DataContext> varlık sınıflarından verileri bir veritabanına geri kaydederken saklı yordamları kullanmak üzere nasıl yapılandırılacağını açıklar.

 [Nasıl yapılır: DataContext metodunun dönüş türünü değiştirme (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) Bir yöntemin dönüş türünün bir <xref:System.Data.Linq.DataContext> varlık sınıfı türü olarak veya O/R Tasarımcısı tarafından oluşturulan otomatik oluşturulmuş bir tür olarak nasıl ayarlanacağını açıklar.

 [Nasıl yapılır: varlık sınıflarına doğrulama ekleme](../data-tools/how-to-add-validation-to-entity-classes.md) Özellik değişiklikleri ve varlık sınıfı güncelleştirmeleri sırasında kodun eklenmesini etkinleştiren kısmi yöntemlerin nasıl oluşturulacağını açıklar.

 [Nasıl yapılır: plurselleştirmeyi açma ve kapatma (O/R Tasarımcısı)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) Öğesine eklenen sınıfların otomatik olarak yeniden adlandırılmasının nasıl açılacağını ve devre dışı aktarılacağını açıklar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Nasıl yapılır: O/R tasarımcısını kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) İle tek tablo devralma kullanılarak varlık sınıflarının nasıl yapılandırılacağını açıklar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Nasıl yapılır: O/R Tasarımcısı tarafından oluşturulan kodu genişletme](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) O/R tasarımcısında nesnelerdeki değişiklikler kodu yeniden oluştururken, üzerine yazılmayacak kodun nasıl ve nereye ekleneceğini açıklar.

 [Izlenecek yol: tek tablo devralma (O/R Designer) kullanarak LINQ to SQL sınıfları oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) İle tek tablo devralma kullanılarak varlık sınıflarını yapılandırmaya yönelik adım adım yönergeler sağlar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Izlenecek yol: varlık sınıflarının INSERT, Update ve DELETE davranışını özelleştirme](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) <xref:System.Data.Linq.DataContext> Varlık sınıflarından verileri bir veritabanına geri kaydederken saklı yordamları kullanacak şekilde yapılandırmak için adım adım yönergeler sağlar.

## <a name="reference-content"></a>Başvuru içeriği
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Ayrıca Bkz.
 [.Net Için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md) [sık sorulan sorular](https://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Visual Studio 'da verilere erişme](../data-tools/accessing-data-in-visual-studio.md)
