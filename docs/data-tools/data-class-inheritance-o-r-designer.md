---
title: Veri sınıfı devralma (O-R Tasarımcısı)
description: Bir veri sınıfı aracı olan Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) içinde veri LINQ to SQL devralma ile Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 82c1c07ec9fb7e19a2d4e126358d124d88c79ff1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154920"
---
# <a name="data-class-inheritance-or-designer"></a>Veri sınıfı devralma (O/R Tasarımcısı)

Diğer nesneler gibi, LINQ to SQL sınıfları devralma kullanabilir ve diğer sınıflardan türetilen. Kodda, bir sınıfın başka bir sınıftan devralınıyor olduğunu bildirerek nesneler arasındaki devralma ilişkilerini belirtebilirsiniz. Bir veritabanında devralma ilişkileri çeşitli yollarla oluşturulur. Bu **Nesne İlişkisel Tasarımcısı** **(O/R Tasarımcısı)** genellikle ilişkisel sistemlerde uygulanan tek tablolu devralma kavramını destekler.

Tek tablo devralmada, hem temel hem de türetilmiş sınıflar için sütunlar içeren tek bir veritabanı tablosu vardır. İlişkisel verilerde, bir ayrımcı sütun belirli bir kaydın hangi sınıfa ait olduğunu belirleyen değeri içerir. Örneğin, bir şirket `Persons` tarafından çalışan herkesi içeren bir tablo düşünün. Bazı kişiler çalışan, bazıları ise yöneticidir. Tablo, `Persons` yöneticiler için `Type` 1, çalışanlar için ise 2 değerine sahip olan adlı bir sütun içerir. `Type`sütun, ayrımcı sütuntur. Bu senaryoda, çalışanların bir alt sınıfını oluşturabilir ve sınıfı yalnızca 2 değerine sahip `Type` kayıtlarla doldurmak için kullanabilirsiniz.

kullanarak varlık sınıflarında devralmayı yapılandırıldığında, devralma verilerini içeren tek tabloyu tasarımcıya iki kez sürükleyin: devralma hiyerarşisinde her sınıf [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] için bir kez. Tabloları tasarımcıya ekledikten sonra, bunları Nesne İlişkisel Tasarımcısı araç  kutusundan bir Devralma öğesiyle bağ açın ve ardından Özellikler penceresinde dört devralma **özelliği** ayarlayın.

## <a name="inheritance-properties"></a>Devralma özellikleri

Aşağıdaki tabloda devralma özellikleri ve açıklamaları listelemiştir:

|Özellik|Açıklama|
|--------------|-----------------|
|**Discriminator Özelliği**|Geçerli kaydın hangi sınıfa ait olduğunu belirleyen özelliği (sütunla eşlenmiş).|
|**Temel Sınıf Ayırıcı Değeri**|Bir kaydın temel sınıftan olduğunu belirleyen değer **(Discriminator Özelliği** olarak belirlenen sütunda).|
|**Türetilmiş Sınıf Ayrımı Değeri**|Bir kaydın türetilmiş sınıftan olduğunu belirleyen değer **(Discriminator Özelliği** olarak belirlenen özellikte).|
|**Devralma Varsayılanı**|**Discriminator** Özelliği olarak belirlenen özellikte değer Temel Sınıf Ayrımı Değeri  veya Türetilmiş Sınıf Ayrımı Değeri ile eşleşmezse **doldurulan sınıf.**|

Devralma kullanan ve ilişkisel verilere karşılık gelen bir nesne modeli oluşturmak biraz kafa karıştırıcı olabilir. Bu konu, devralmayı yapılandırmak için gereken temel kavramlar ve tek tek özellikler hakkında bilgi sağlar. Aşağıdaki konular, **O/R** Tasarımcısı ile devralmayı yapılandırma hakkında daha net bir açıklama sağlar.

|Konu|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|O/R Tasarımcısı kullanılarak tek tablo devralma kullanan varlık sınıflarını **yapılandırmayı açıklar.**|
|[adım adım kılavuz: LINQ to SQL devralma (O/R Tasarımcısı) kullanarak tek tablo sınıflarını oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|**O/R** Tasarımcısı kullanarak tek tablo devralma kullanan varlık sınıflarını yapılandırmaya ilişkin adım adım yönergeler sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [adım adım kılavuz: LINQ to SQL sınıfları oluşturma (O-R Tasarımcısı)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [adım adım kılavuz: LINQ to SQL devralma (O/R Tasarımcısı) kullanarak tek tablo sınıflarını oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Başlarken](/dotnet/framework/data/adonet/sql/linq/getting-started)
