---
title: Veri sınıfı devralma (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7172c868780aec61de8688614fbb93627dc23bf5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462401"
---
# <a name="data-class-inheritance-or-designer"></a>Veri sınıfı devralma (O/R Tasarımcısı)

Diğer nesneler gibi LINQ to SQL sınıflar devralma kullanabilir ve diğer sınıflardan türetilebilir. Kodda, bir sınıfın diğerinden devraldığını bildirerek nesneler arasındaki devralma ilişkilerini belirtebilirsiniz. Bir veritabanında, devralma ilişkileri çeşitli yollarla oluşturulur. **Nesne ilişkisel Tasarımcısı** (**O/R Designer**), genellikle ilişkisel sistemlerde uygulanan tek tablo devralma kavramını destekler.

Tek tablo Devralmada, hem temel hem de türetilmiş sınıfların sütunlarını içeren tek bir veritabanı tablosu vardır. İlişkisel veriler ile, bir Ayrıştırıcı sütunu, belirli bir kaydın hangi sınıfa ait olduğunu belirleyen değeri içerir. Örneğin, `Persons` bir şirket tarafından görevli herkesi içeren bir tablo düşünün. Bazı kişiler çalışanlar ve bazı kişiler yöneticilerdir. `Persons`Tablo, `Type` Yöneticiler için 1 değeri ve çalışanlar için 2 değeri olan adlı bir sütun içerir. `Type`Sütun, ayrıştırıcı sütunudur. Bu senaryoda, çalışanların bir alt sınıfını oluşturabilir ve sınıfı yalnızca 2 değerine sahip kayıtlarla doldurabilirsiniz `Type` .

Kullanarak varlık sınıflarında devralmayı yapılandırdığınızda [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , devralma verilerini içeren tek tabloyu tasarımcıya iki kez sürükleyin: devralma hiyerarşisindeki her sınıf için bir kez. Tabloları tasarımcıya ekledikten sonra, **nesne ilişkisel Tasarımcısı** araç kutusundan devralma öğesiyle bağlayın ve ardından **Özellikler** penceresinde dört devralma özelliğini ayarlayın.

## <a name="inheritance-properties"></a>Devralma özellikleri

Aşağıdaki tabloda devralma özellikleri ve açıklamaları listelenmektedir:

|Özellik|Açıklama|
|--------------|-----------------|
|**Ayrıştırıcı özelliği**|Geçerli kaydın hangi sınıfa ait olduğunu belirleyen özelliği (sütunla eşleştirilir).|
|**Temel sınıf ayrıştırıcı değeri**|Bir kaydın temel sınıf olduğunu belirleyen değer ( **ayrıştırıcı özelliği**olarak belirlenen sütunda).|
|**Türetilmiş sınıf ayrıştırıcı değeri**|Bir kaydın türetilmiş sınıfa ait olduğunu belirleyen değer ( **ayrıştırıcı özelliği**olarak belirlenmiş özellikte).|
|**Devralma varsayılanı**|Bir **ayrıştırıcı özelliği** olarak belirtilen özellikte değer, **taban sınıf ayrıştırıcı değeri** veya **türetilmiş sınıf ayrıştırıcı değeri**ile eşleşmezse doldurulan sınıf.|

Devralma kullanan ve ilişkisel verilere karşılık gelen bir nesne modeli oluşturmak biraz kafa karıştırıcı olabilir. Bu konuda, devralmayı yapılandırmak için gerekli olan temel kavramlar ve tek tek özellikler hakkında bilgi verilmektedir. Aşağıdaki konularda, **O/R Tasarımcısı**ile devralmayı yapılandırma hakkında daha net bir açıklama sağlanmaktadır.

|Konu başlığı|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|**O/R tasarımcısını**kullanarak tek tablo devralma kullanan varlık sınıflarının nasıl yapılandırılacağını açıklar.|
|[İzlenecek yol: tek tablo devralma (O/R Designer) kullanarak LINQ to SQL sınıfları oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|**O/R tasarımcısını**kullanarak tek tablo devralma kullanan varlık sınıflarının nasıl yapılandırılacağı hakkında adım adım yönergeler sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [İzlenecek yol: tek tablo devralma (O/R Designer) kullanarak LINQ to SQL sınıfları oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Kullanmaya başlama](/dotnet/framework/data/adonet/sql/linq/getting-started)