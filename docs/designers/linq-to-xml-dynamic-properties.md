---
title: LINQ to XML Dinamik Özellikleri
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5993639a1bd6db1b814615bc75c1a57b64212185
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635258"
---
# <a name="linq-to-xml-dynamic-properties"></a>LINQ to XML dinamik özellikleri

Bu bölüm LINQ to XML içindeki dinamik özelliklerle ilgili başvuru bilgileri sağlar. Özellikle, bu özellikler <xref:System.Xml.Linq> ad alanındaki <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıfları tarafından gösterilir.

[LINQ to XML Ile WPF veri bağlamaya genel bakış](../designers/wpf-data-binding-with-linq-to-xml-overview.md)konusunda açıklandığı gibi, dinamik özelliklerin her biri aynı sınıftaki standart ortak bir özellik veya yönteme eşdeğerdir. Bu standart Üyeler çoğu amaçla kullanılmalıdır; dinamik özellikler, LINQ to XML veri bağlama senaryoları için özel olarak sağlanır. Bu sınıfların standart üyeleri hakkında daha fazla bilgi için, <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> başvuru konularına bakın.

Çözümlenme değerlerine göre, bu bölümdeki dinamik özellikler iki kategoriye ayrılır:

- Tek bir değere çözüm veren <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıflarında `Value` özellikleri gibi basit olanlar.

- Dizin Oluşturucu türünde çözümlenilen <xref:System.Xml.Linq.XElement> [öğeleri](../designers/elements-xelement-dynamic-property.md) ve [alt](../designers/descendants-xelement-dynamic-property.md) öğeler gibi dizinli değerler. Dizin Oluşturucu türlerinin istenen değere veya koleksiyona çözümlenmesi için, bir genişletilmiş ad parametresi geçirilmesi gerekir.

@No__t_0 türünde dizinli bir değer döndüren tüm dinamik özellikler ertelenmiş yürütmeyi kullanır. Ertelenmiş yürütme hakkında daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="reference"></a>Başvuru

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML ile WPF verilerini bağlama](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [LINQ to XML genel bakış ile WPF veri bağlama](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [LINQ Sorgularına Giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
