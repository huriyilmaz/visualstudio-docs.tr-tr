---
title: 'Nasıl yapılır: LINQ to SQL sınıfları arasında ilişki (ilişki) oluşturma (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c2f6f6f65410336eacf72967c8360a56e8fa5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610009"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Nasıl yapılır: LINQ to SQL sınıfları arasında ilişkilendirme (ilişki) oluşturma (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 varlık sınıfları arasındaki ilişkilendirmeler, bir veritabanındaki tablolar arasındaki ilişkilerle benzerdir. **Ilişki düzenleyici** iletişim kutusunu kullanarak varlık sınıfları arasında ilişkiler oluşturabilirsiniz.

 İlişki oluşturmak için **Ilişkilendirme düzenleyici** iletişim kutusunu kullandığınızda bir üst sınıf ve alt sınıf seçmelisiniz. Ana sınıf, birincil anahtarı içeren varlık sınıfıdır; alt sınıf, yabancı anahtarı içeren varlık sınıfıdır. Örneğin, Northwind Customers ve Orders tablolarıyla eşlenen varlık sınıfları oluşturulduysa, müşteri sınıfı üst sınıf olur ve Order sınıfı alt sınıf olur.

> [!NOTE]
> Tabloları **Sunucu Gezgini** /**Veritabanı Gezgini** [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) üzerine sürüklediğinizde, ilişkilendirmeler veritabanındaki mevcut yabancı anahtar ilişkilerine göre otomatik olarak oluşturulur.

 Bir ilişki oluşturduktan sonra, O/R tasarımcısında ilişkilendirmeyi seçtiğinizde, **Özellikler** penceresinde bazı yapılandırılabilir özellikler vardır. (İlişkilendirme ilişkili sınıflar arasındaki satırdır.) Aşağıdaki tabloda bir ilişkinin özelliklerine ilişkin açıklamalar verilmiştir.

|Özellik|Açıklama|
|--------------|-----------------|
|**İte**|İlişkilendirmenin bire çok veya bire bir olduğunu denetler.|
|**Alt özellik**|Üst öğede, ilişkilendirmenin yabancı anahtar tarafındaki alt kayıtlara yönelik bir koleksiyon veya başvuru olan bir özellik oluşturulup oluşturulmayacağını belirtir. Örneğin, müşteri ve sipariş arasındaki ilişkilendirmede, **alt özelliği** **true**olarak ayarlanırsa, ana sınıfta Orders adlı bir özellik oluşturulur.|
|**Parent özelliği**|İlişkili üst sınıfa başvuran alt sınıftaki özellik. Örneğin, müşteri ve sipariş arasındaki ilişkilendirmede, sipariş sınıfında bir sipariş için ilişkili müşteriye başvuran müşteri adlı bir özellik oluşturulur.|
|**Katılım özellikleri**|İlişki özelliklerini görüntüler ve **Ilişkilendirme düzenleyici** iletişim kutusunu yeniden açan **üç nokta** düğmesini (...) sağlar.|
|**Eşi**|Yabancı hedef sütunlarının benzersizlik kısıtlaması olup olmadığını belirtir.|

### <a name="to-create-an-association-between-entity-classes"></a>Varlık sınıfları arasında bir ilişkilendirme oluşturmak için

1. İlişkilendirmedeki üst sınıfı temsil eden varlık sınıfına sağ tıklayın, **Ekle**' nin üzerine gelin ve **ilişkilendirme**' ye tıklayın.

2. **Ilişkilendirme düzenleyici** iletişim kutusunda doğru **üst sınıfın** seçildiğini doğrulayın.

3. Birleşik giriş kutusunda **alt sınıfı** seçin.

4. Sınıflarla ilişkili **Ilişkilendirme özelliklerini** seçin. Genellikle, bu, veritabanında tanımlanan yabancı anahtar ilişkisiyle eşlenir. Örneğin, müşteriler ve siparişler ilişkisinde, her bir sınıf için **Ilişki özellikleri** CustomerID ' dir.

5. İlişkilendirmeyi oluşturmak için **Tamam** ' ı tıklatın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [izlenecek yol: LINQ to SQL sınıfları oluşturma (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [DataContext yöntemleri (o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [nasıl yapılır: birincil anahtarları temsil etme](https://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)
