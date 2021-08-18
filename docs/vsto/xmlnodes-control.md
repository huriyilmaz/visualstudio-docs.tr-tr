---
title: XMLNodes denetimi
description: XMLNodes denetiminin yalnızca yinelenen bir şema öğesi Microsoft Word bir belgeyle eşlendiğinde oluşturulduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cad5ca717f5e996fcc32c4806c6ab86afc7cc241
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045911"
---
# <a name="xmlnodes-control"></a>XMLNodes denetimi
  **Önemli** bu konu başlığı altında Microsoft Word, microsoft, Microsoft Word 'den özel XML ile ilgili belirli işlevlerin bir uygulamasını kaldırdıkları zaman, Birleşik Devletler ve bölgeleri dışında bulunan Microsoft Word veya 2010 microsoft tarafından lisanslanan ürünlerin ve kuruluşların kullanımı ve kullanımı için özel olarak sunulur. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler veya şirket içinde çalışan ya da şirket içinde çalışan veya Microsoft tarafından lisanslanan Microsoft Word, 10 ocak 2010 ' den sonra lisanslı ürünleri kullanan bireyler veya kuruluşlar tarafından okunamaz veya kullanılmıyor olabilir. Bu ürünler, bu tarihten önce lisanslanan ürünlerle aynı veya satın alınmadan ve Birleşik Devletler dışında kullanılmak üzere lisanslanmaz.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNodes>Denetim, olayları ortaya çıkaran eşlenmiş BIR XML düğümü nesneleri koleksiyonudur. <xref:Microsoft.Office.Tools.Word.XMLNodes>denetim, yalnızca yinelenen bir şema öğesi Microsoft Office bir Word belgesiyle eşlendiğinde oluşturulur. Yinelenen öğe alt öğeler içeriyorsa, alt öğelerin her biri de bir denetim olarak oluşturulur <xref:Microsoft.Office.Tools.Word.XMLNodes> .

 Visual Studio, XML düğümleri koleksiyonunu oluşturduktan sonra, Word nesne modeline çapraz geçiş yapmak zorunda kalmadan doğrudan denetime karşı programlama yapabilirsiniz. <xref:Microsoft.Office.Tools.Word.XMLNodes>Denetim yalnızca belgeden öğe eşlemesi kaldırılarak silinebilir.

> [!NOTE]
> Özelliği aracılığıyla denetimin bir alt öğesine eriştiğinizde <xref:Microsoft.Office.Tools.Word.XMLNodes> <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> , <xref:Microsoft.Office.Interop.Word.XMLNode> bir denetim yerine bir nesne döndürür <xref:Microsoft.Office.Tools.Word.XMLNode> . Daha fazla bilgi için bkz. [konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Verileri denetime bağlama
 Bir <xref:Microsoft.Office.Tools.Word.XMLNodes> Denetim veri bağlamayı desteklemez. Bunun nedeni, <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimin karmaşık veri bağlama özelliklerine sahip olmaması ve basit veri bağlamasının yinelenen verileri temsil edemez.

## <a name="formatting"></a>Biçimlendirme
 Belge içindeki metne uygulanabilen tüm biçimlendirmeler bir <xref:Microsoft.Office.Tools.Word.XMLNodes> denetime uygulanabilir.

## <a name="events"></a>Ekinlikler
 Denetim için kullanılabilen olaylar <xref:Microsoft.Office.Tools.Word.XMLNodes> şunlardır:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Olayları Karşılaştır
 Kullanıcı imlecini belirli bir denetim bağlamının içine taşıdıkça bir olay yakalayabilirsiniz <xref:Microsoft.Office.Tools.Word.XMLNodes> . Örneğin, adında <xref:Microsoft.Office.Tools.Word.XMLNodes> bir alt denetimi olan adlı bir denetiminiz olabilir `Customer` <xref:Microsoft.Office.Tools.Word.XMLNodes> `Company` ve `Company` <xref:Microsoft.Office.Tools.Word.XMLNodes> `CompanyName` aşağıdaki gibi iki alt denetime sahiptir `CompanyRegion` :

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 İmleç düğümüne her taşındığında Eylemler bölmesinde bir denetim göstermek istiyorsanız `Company` , imlece yerleştirilmiş `CompanyName` ya da `CompanyRegion` her ikisi de bağlamı içinde olduklarından bağımsız değildir `Company` . Bu durumda, kodunuzun <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> olayında yazabilirsiniz `Company` .

 Çoğu durumda, imleç bir denetim girdiğinde hem hem <xref:Microsoft.Office.Tools.Word.XMLNodes> de <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> olayları tetiklenir. Aşağıdaki tabloda bu olaylar arasındaki farklılıklar gösterilmektedir.

|Olay Seç|ContextEnter olayı|
|------------------|------------------------|
|İmleç koleksiyonun düğümlerinden birinin içine yerleştirildiğinde oluşur <xref:Microsoft.Office.Tools.Word.XMLNodes> .|İmleç, <xref:Microsoft.Office.Tools.Word.XMLNodes> düğümün bağlamı dışında bir alandan, koleksiyonun düğümlerin veya alt düğümlerinden birinin içine yerleştirildiğinde oluşur. Diğer bir deyişle, yalnızca bağlam değiştiğinde oluşturulur ve birden çok iç içe denetim için oluşturulabilir <xref:Microsoft.Office.Tools.Word.XMLNodes> .|

 Örneğin, imleci içine içinden taşıdığınızda,, `Customer` `CompanyName` <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> ve için olaylar `Customer` `Company` `CompanyName` oluşturulur. Daha sonra imleci `CompanyName` ' den ' e taşırsanız `CompanyRegion` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `CompanyRegion` bağlamı her ikisi için de aynı olduğu için yalnızca için olay tetiklenir `Company` `Customer` . Belgenizde birden çok düğüme sahip olabilirsiniz `Company` . İmleci `CompanyName` bir düğümden `Company` `CompanyName` başka bir düğüme taşırsanız `Company` , bağlam aynı olur, bu nedenle yalnızca <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> olay tetiklenir.

 Olay ve olay arasında aynı farklar vardır <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> .

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode denetimi](../vsto/xmlnode-control.md)
- [Nasıl yapılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Nasıl yapılır: Visual Studio içindeki Word belgeleriyle şemaları eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
