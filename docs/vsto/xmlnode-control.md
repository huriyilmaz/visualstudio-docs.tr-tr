---
title: XMLNode denetimi
description: XMLNode denetiminin olayları açığa çıkaran ve verilere bağlanabilen eşlenmiş bir XML düğümü nesnesi olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ffd8fd0aa1b6d969a610f411caef11d09f47e3e73340ff82b3cab3fe5538cf22
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440649"
---
# <a name="xmlnode-control"></a>XMLNode denetimi
  **Önemli** bu konu başlığı altında Microsoft Word, microsoft, Microsoft Word 'den özel XML ile ilgili belirli işlevlerin bir uygulamasını kaldırdıkları zaman, Birleşik Devletler ve bölgeleri dışında bulunan Microsoft Word veya 2010 microsoft tarafından lisanslanan ürünlerin ve kuruluşların kullanımı ve kullanımı için özel olarak sunulur. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler veya şirket içinde çalışan ya da şirket içinde çalışan veya Microsoft tarafından lisanslanan Microsoft Word, 10 ocak 2010 ' den sonra lisanslı ürünleri kullanan bireyler veya kuruluşlar tarafından okunamaz veya kullanılmıyor olabilir. Bu ürünler, bu tarihten önce lisanslanan ürünlerle aynı veya satın alınmadan ve Birleşik Devletler dışında kullanılmak üzere lisanslanmaz.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNode>Denetim, olayları ortaya çıkaran ve verilere bağlanabilen eşlenmiş BIR XML node nesnesidir. <xref:Microsoft.Office.Tools.Word.XMLNode>denetim, yalnızca tekrarsız bir şema öğesi Microsoft Office bir Word belgesiyle eşlendiğinde oluşturulur. Visual Studio XML düğümünü oluşturduktan sonra, Word nesne modelinde geçiş yapmak zorunda kalmadan doğrudan buna karşı programlama yapabilirsiniz.

 <xref:Microsoft.Office.Tools.Word.XMLNode>Denetim yalnızca Word 'deki öğe eşlemesini kaldırarak silinebilir.

## <a name="bind-data-to-the-control"></a>Verileri denetime bağlama
 Bir <xref:Microsoft.Office.Tools.Word.XMLNode> Denetim basit veri bağlamayı destekler. XML düğümü, özelliğini kullanarak bir veri kaynağına bağlanmalıdır <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> . Bağlantılı veri kümesindeki veriler güncelleştirilirse <xref:Microsoft.Office.Tools.Word.XMLNode> Denetim, değişiklikleri yansıtır.

## <a name="formatting"></a>Biçimlendirme
 Bir nesneye uygulanabilen biçimlendirme <xref:Microsoft.Office.Interop.Word.XMLNode> , bir <xref:Microsoft.Office.Tools.Word.XMLNode> denetime uygulanabilir. Buna yazı tipleri, alt çizgi stilleri ve karakter stilleri dahildir.

## <a name="events"></a>Ekinlikler
 Denetim için aşağıdaki olaylar mevcuttur <xref:Microsoft.Office.Tools.Word.XMLNode> :

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Olayları Karşılaştır
 Kullanıcı imlecini belirli bir denetim bağlamının içine taşıdıkça bir olay yakalayabilirsiniz <xref:Microsoft.Office.Tools.Word.XMLNode> . Örneğin, adında <xref:Microsoft.Office.Tools.Word.XMLNode> bir alt denetimi olan adlı bir denetiminiz olabilir `Customer` <xref:Microsoft.Office.Tools.Word.XMLNode> `Company` ve `Company` <xref:Microsoft.Office.Tools.Word.XMLNode> `CompanyName` aşağıdaki gibi iki alt denetime sahiptir `CompanyRegion` :

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 İmleç düğümüne her taşındığında Eylemler bölmesinde bir denetim göstermek istiyorsanız `Company` , imlece yerleştirilmiş `CompanyName` ya da `CompanyRegion` her ikisi de bağlamı içinde olduklarından bağımsız değildir `Company` . Bu durumda, kodunuzun <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> olayında yazabilirsiniz `Company` .

 Çoğu durumda, imleç bir denetim girdiğinde hem hem <xref:Microsoft.Office.Tools.Word.XMLNode> de <xref:Microsoft.Office.Tools.Word.XMLNode.Select> <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> olayları tetiklenir. Aşağıdaki tabloda bu olaylar arasındaki farklar gösterilmektedir.

|Olay Seç|ContextEnter olayı|
|------------------|------------------------|
|İmleç bir içinde yerleştirildiğinde oluşur <xref:Microsoft.Office.Tools.Word.XMLNode> .|İmleç, <xref:Microsoft.Office.Tools.Word.XMLNode> düğüm bağlamı dışındaki bir alandan bir veya alt düğümlerinden birinin içine yerleştirildiğinde gerçekleşir. Diğer bir deyişle, yalnızca bağlam değiştiğinde oluşturulur.|

 Örneğin, imleci içine içinden taşıdığınızda,, `Customer` `CompanyName` <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> ve için olayı `Customer` `Company` `CompanyName` tetiklenir. Daha sonra imleci `CompanyName` ' den ' e taşırsanız `CompanyRegion` , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> hala hem hem de `CompanyRegion` bağlamı dahilinde olduğunuz için yalnızca olay oluşturulur `Company` `Customer` .

 Olay ve olay arasında aynı farklar vardır <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> .

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNodes denetimi](../vsto/xmlnodes-control.md)
- [Nasıl yapılır: Word belgelerine XMLNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Nasıl yapılır: Visual Studio içindeki Word belgeleriyle şemaları eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
