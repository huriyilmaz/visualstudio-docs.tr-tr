---
title: LINQ to SQL sınıfları arasındaki ilişkiler (O/R Tasarımcısı)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fb81cf17de86a11d2373f6a545b3efc78e65ada9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586477"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Nasıl yapılır: LINQ to SQL sınıfları arasında ilişki oluşturma (O/R Designer)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] varlık sınıfları arasındaki ilişkilendirmeler, bir veritabanındaki tablolar arasındaki ilişkilerle benzerdir. **Ilişki düzenleyici** iletişim kutusunu kullanarak varlık sınıfları arasında ilişkiler oluşturabilirsiniz.

İlişki oluşturmak için **Ilişkilendirme düzenleyici** iletişim kutusunu kullandığınızda bir üst sınıf ve alt sınıf seçmelisiniz. Ana sınıf, birincil anahtarı içeren varlık sınıfıdır; alt sınıf, yabancı anahtarı içeren varlık sınıfıdır. Örneğin, `Northwind Customers` ve `Orders` tabloları ile eşlenen varlık sınıfları oluşturulduysa, `Customer` sınıfı üst sınıf olur ve `Order` sınıfı alt sınıf olur.

> [!NOTE]
> Tabloları **Sunucu Gezgini** veya **veritabanı Gezgini** **nesne ilişkisel Tasarımcısı** (**O/R Designer**) üzerine sürüklediğinizde, ilişkilendirmeler veritabanındaki mevcut yabancı anahtar ilişkilerine göre otomatik olarak oluşturulur.

## <a name="association-properties"></a>İlişkilendirme özellikleri
Bir ilişki oluşturduktan sonra, **O/R tasarımcısında**ilişkilendirmeyi seçtiğinizde, **Özellikler** penceresinde bazı yapılandırılabilir özellikler vardır. (İlişkilendirme ilişkili sınıflar arasındaki satırdır.) Aşağıdaki tabloda bir ilişkinin özelliklerine ilişkin açıklamalar verilmiştir.

|Özellik|Açıklama|
|--------------|-----------------|
|**İte**|İlişkilendirmenin bire çok veya bire bir olduğunu denetler.|
|**Alt özellik**|Üst öğede, ilişkilendirmenin yabancı anahtar tarafındaki alt kayıtlara yönelik bir koleksiyon veya başvuru olan bir özellik oluşturulup oluşturulmayacağını belirtir. Örneğin, `Customer` ve `Order`arasındaki ilişkilendirmede, **alt özelliği** **true**olarak ayarlanırsa, ana sınıfta `Orders` adlı bir özellik oluşturulur.|
|**Parent özelliği**|İlişkili üst sınıfa başvuran alt sınıftaki özellik. Örneğin, `Customer` ve `Order`arasındaki ilişkide, `Order` sınıfında bir sipariş için ilişkili müşteriye başvuran `Customer` adlı bir özellik oluşturulur.|
|**Katılım özellikleri**|İlişki özelliklerini görüntüler ve **Ilişkilendirme düzenleyici** iletişim kutusunu yeniden açan **üç nokta** düğmesini (...) sağlar.|
|**Eşi**|Yabancı hedef sütunlarının benzersizlik kısıtlaması olup olmadığını belirtir.|

## <a name="to-create-an-association-between-entity-classes"></a>Varlık sınıfları arasında bir ilişkilendirme oluşturmak için

1. İlişkilendirmedeki üst sınıfı temsil eden varlık sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve **ilişkilendirme**' ye tıklayın.

2. **Ilişkilendirme düzenleyici** iletişim kutusunda doğru **üst sınıfın** seçildiğini doğrulayın.

3. Birleşik giriş kutusunda **alt sınıfı** seçin.

4. Sınıflarla ilişkili **Ilişkilendirme özelliklerini** seçin. Genellikle, bu, veritabanında tanımlanan yabancı anahtar ilişkisiyle eşlenir. Örneğin, `Customers` ve `Orders` ilişkilendirmesinde, **Ilişkilendirme özellikleri** her bir sınıf için `CustomerID`.

5. İlişkilendirmeyi oluşturmak için **Tamam** ' ı tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [İzlenecek yol: LINQ to SQL sınıfları oluşturma](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: birincil anahtarları temsil etme](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
