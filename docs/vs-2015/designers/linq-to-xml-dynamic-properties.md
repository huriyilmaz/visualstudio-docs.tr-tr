---
title: Dinamik özellikleri LINQ to XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ff0b31512711b8888b05fcfde191c8cb5c47d99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664258"
---
# <a name="linq-to-xml-dynamic-properties"></a>LINQ to XML Dinamik Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölüm LINQ to XML içindeki dinamik özelliklerle ilgili başvuru bilgileri sağlar. Özellikle, bu özellikler <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> ad alanındaki ve sınıfları tarafından gösterilir <xref:System.Xml.Linq> .

 [LINQ to XML Ile WPF veri bağlamaya genel bakış](../designers/wpf-data-binding-with-linq-to-xml-overview.md)konusunda açıklandığı gibi, dinamik özelliklerin her biri aynı sınıftaki standart ortak bir özellik veya yönteme eşdeğerdir. Bu standart Üyeler çoğu amaçla kullanılmalıdır; dinamik özellikler, LINQ to XML veri bağlama senaryoları için özel olarak sağlanır. Bu sınıfların standart üyeleri hakkında daha fazla bilgi için bkz <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> . ve başvuru konuları.

 Çözümlenme değerlerine göre, bu bölümdeki dinamik özellikler iki kategoriye ayrılır:

- `Value` <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> Tek bir değere çözümlenenler ve sınıflardaki özellikler gibi basit olanlar.

- Dizin Oluşturucu türü olarak çözümlenilen [öğesi](../designers/elements-xelement-dynamic-property.md) ve [alt](../designers/descendants-xelement-dynamic-property.md) öğeler özellikleri gibi dizinli değerler <xref:System.Xml.Linq.XElement> . Dizin Oluşturucu türlerinin istenen değere veya koleksiyona çözümlenmesi için, bir genişletilmiş ad parametresi geçirilmesi gerekir.

  Türünde dizinli bir değer döndüren tüm dinamik özellikler, <xref:System.Collections.Generic.IEnumerable%601> ertelenmiş yürütmeyi kullanır. Ertelenmiş yürütme hakkında daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="in-this-section"></a>Bu Bölümde

|Konu|Açıklama|
|-----------|-----------------|
|[XAttribute Sınıfı Dinamik Özellikleri](../designers/xattribute-class-dynamic-properties.md)|Sınıfı tarafından kullanıma sunulan dinamik özelliklerle ilgili ayrıntıları sağlar <xref:System.Xml.Linq.XAttribute> .|
|[XElement sınıfı dinamik özellikleri](../designers/xelement-class-dynamic-properties.md)|Sınıfı tarafından kullanıma sunulan dinamik özelliklerle ilgili ayrıntıları sağlar <xref:System.Xml.Linq.XElement> .|

## <a name="reference"></a>Başvuru
 <xref:System.Xml.Linq>

 <xref:System.Xml.Linq.XElement?displayProperty=fullName>

 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Ayrıca Bkz.
 [LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md) WPF veri bağlama ile WPF veri bağlama [LINQ to XML genel bakış](../designers/wpf-data-binding-with-linq-to-xml-overview.md) [LINQ Sorgularına Giriş (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)
