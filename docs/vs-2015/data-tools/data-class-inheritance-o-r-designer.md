---
title: Veri sınıfı devralma (O-R Designer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e7dfc2b1137b30a03425f663d70e12c528dad39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657406"
---
# <a name="data-class-inheritance-or-designer"></a>Veri sınıfı devralma (O/R Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diğer nesneler gibi, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sınıflar devralma kullanabilir ve diğer sınıflardan türetilebilir. Kodda, bir sınıfın diğerinden devraldığını bildirerek nesneler arasındaki devralma ilişkilerini belirtebilirsiniz. Bir veritabanında, devralma ilişkileri çeşitli yollarla oluşturulur. [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ), Genellikle ilişkisel sistemlerde uygulanan tek tablo devralma kavramını destekler.

 Tek tablo Devralmada, hem temel hem de türetilmiş sınıfların sütunlarını içeren tek bir veritabanı tablosu vardır. İlişkisel veriler ile, bir Ayrıştırıcı sütunu, belirli bir kaydın hangi sınıfa ait olduğunu belirleyen değeri içerir. Örneğin, bir şirket tarafından görevli herkesi içeren bir kişiler tablosu düşünün. Bazı kişiler çalışanlar ve bazı kişiler yöneticilerdir. Kişiler tablosu, Yöneticiler için 1 değeri ve çalışanlar için 2 değeri olan Type adlı bir sütun içerir. Tür sütunu ayrıştırıcı sütunudur. Bu senaryoda, çalışanların bir alt sınıfını oluşturabilir ve sınıfı yalnızca 2 tür değerine sahip kayıtlarla doldurabilirsiniz.

 Kullanarak varlık sınıflarında devralmayı yapılandırdığınızda [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , devralma verilerini içeren tek tabloyu tasarımcıya iki kez sürükleyin: devralma hiyerarşisindeki her sınıf için bir kez. Tabloları tasarımcıya ekledikten sonra, **nesne ilişkisel Tasarımcısı** araç kutusundan devralma öğesiyle bağlayın ve ardından **Özellikler** penceresinde dört devralma özelliğini ayarlayın.

## <a name="inheritance-properties"></a>Devralma özellikleri
 Aşağıdaki tabloda devralma özellikleri ve açıklamaları listelenmektedir:

|Özellik|Açıklama|
|--------------|-----------------|
|Ayrıştırıcı özelliği|Geçerli kaydın hangi sınıfa ait olduğunu belirleyen özelliği (sütunla eşleştirilir).|
|Temel sınıf ayrıştırıcı değeri|Bir kaydın temel sınıf olduğunu belirleyen değer (ayrıştırıcı özelliği olarak belirlenen sütunda).|
|Türetilmiş sınıf ayrıştırıcı değeri|Bir kaydın türetilmiş sınıfa ait olduğunu belirleyen değer (ayrıştırıcı özelliği olarak belirlenmiş özellikte).|
|Devralma varsayılanı|**Ayrıştırıcı özelliği** olarak belirtilen özellikte değer, **taban sınıf ayrıştırıcı değeri** veya **türetilmiş sınıf ayrıştırıcı değeri**ile eşleşmediği zaman doldurulmalıdır.|

 Devralma kullanan ve ilişkisel verilere karşılık gelen bir nesne modeli oluşturmak biraz kafa karıştırıcı olabilir. Bu konuda, devralmayı yapılandırmak için gerekli olan temel kavramlar ve tek tek özellikler hakkında bilgi verilmektedir. Aşağıdaki konularda, ile devralmayı yapılandırma hakkında daha net bir açıklama sağlanmaktadır [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

|Konu|Description|
|-----------|-----------------|
|[Nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Kullanarak tek tablo devralma kullanan varlık sınıflarının nasıl yapılandırılacağını açıklar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .|
|[İzlenecek Yol: Tek Tablo Devralma Kullanarak LINQ to SQL Sınıfı Oluşturma (O/R Tasarımcısı)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Kullanılarak tek tablo devralma kullanan varlık sınıflarının nasıl yapılandırılacağı hakkında adım adım yönergeler sağlar [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [izlenecek yol: LINQ to SQL sınıfları oluşturma (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [Izlenecek yol: tek Tablo Devralma kullanarak LINQ to SQL sınıfları oluşturma (o/r Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [Başlarken](https://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)
