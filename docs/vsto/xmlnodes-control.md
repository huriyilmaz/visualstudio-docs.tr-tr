---
title: XMLNodes denetimi
description: XMLNodes denetimi yalnızca yinelenen bir şema öğesi bir belgeye eşlenmiş olduğunda Microsoft Word öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726079"
---
# <a name="xmlnodes-control"></a>XMLNodes denetimi
  **Önemli** Microsoft Word ile ilgili bu konu başlığı altında açıklanan bilgiler, Microsoft tarafından Ocak 2010'dan önce Microsoft tarafından lisanslanmıştır ve Birleşik Devletler ve bölgeleri dışında bulunan veya Microsoft tarafından 2010'dan önce microsoft tarafından lisanslanmıştır ve Microsoft Word ürünleri üzerinde çalıştırılan programları kullanan veya geliştiren kişiler ve kuruluşların kullanımı için özel olarak Microsoft Word. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler'daki veya Microsoft Word Microsoft tarafından 10 Ocak 2010'dan sonra lisansa alınan ve üzerinde çalışan programları kullanan veya geliştiren kişiler veya kuruluşlar tarafından okunamayabilirsiniz veya kullanılmayabilirsiniz; bu ürünler, ilgili tarihten önce lisanslı olan veya satın alınan ve satın alınan ve satın alınan ürünlerle aynı davranışa Birleşik Devletler.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Denetim, <xref:Microsoft.Office.Tools.Word.XMLNodes> olayları ortaya çıkaran eşlenmiş XML düğümü nesneleri koleksiyonudur. Denetim yalnızca yinelenen bir şema öğesi word belgesinde bir Microsoft Office <xref:Microsoft.Office.Tools.Word.XMLNodes> oluşturulur. Yinelenen öğe alt öğeler içeriyorsa, alt öğelerin her biri de bir denetim olarak <xref:Microsoft.Office.Tools.Word.XMLNodes> oluşturulur.

 Bu Visual Studio XML düğümleri koleksiyonunu oluşturduğunda, Word nesne modelini çapraz geçiş yapmak zorunda kalmadan doğrudan denetime karşı program kurabilirsiniz. Denetim <xref:Microsoft.Office.Tools.Word.XMLNodes> yalnızca öğe eşlemesi belgeden kaldırılarak silinebilir.

> [!NOTE]
> Denetimin bir alt öğesine özelliği <xref:Microsoft.Office.Tools.Word.XMLNodes> aracılığıyla <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> erişersiniz, denetim yerine <xref:Microsoft.Office.Interop.Word.XMLNode> bir nesnesi <xref:Microsoft.Office.Tools.Word.XMLNode> döndürür. Daha fazla bilgi için [bkz. Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

## <a name="bind-data-to-the-control"></a>Denetime veri bağlama
 Denetim, <xref:Microsoft.Office.Tools.Word.XMLNodes> veri bağlamayı desteklemez. Bunun nedeni <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimin karmaşık veri bağlama özelliklerine sahip değildir ve basit veri bağlaması yinelenen verileri temsil etme özelliğine sahip değildir.

## <a name="formatting"></a>Biçimlendirme
 Belge içindeki metne uygulana tüm biçimlendirmeler bir denetime <xref:Microsoft.Office.Tools.Word.XMLNodes> uygulanabilir.

## <a name="events"></a>Ekinlikler
 Denetim için kullanılabilen <xref:Microsoft.Office.Tools.Word.XMLNodes> olaylar:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Olayları karşılaştırma
 Kullanıcı imlecini belirli bir denetimin bağlamı içinde hareket ettiğinde bir olayı <xref:Microsoft.Office.Tools.Word.XMLNodes> yakalar. Örneğin, adlı bir alt denetimi olan ve adlı iki alt denetimi olan <xref:Microsoft.Office.Tools.Word.XMLNodes> ve aşağıdaki gibi bir `Customer` <xref:Microsoft.Office.Tools.Word.XMLNodes> `Company` `Company` <xref:Microsoft.Office.Tools.Word.XMLNodes> `CompanyName` `CompanyRegion` denetime sahip olabilir:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 İmleç düğüme her taşındığında eylemler bölmesinde bir denetim göstermek istemeniz, imlecin içine yerleştirilip yerleştirilip yerleştiril olmadığı veya her ikisi de bağlamında olduğu `Company` `CompanyName` için önemli `CompanyRegion` `Company` değildir. Bu durumda, durumunda kodunuzu <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `Company` yazabilirsiniz.

 Çoğu durumda, imleç bir <xref:Microsoft.Office.Tools.Word.XMLNodes> denetime girdiği zaman hem <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> hem de olayları ortaya <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> çıkar. Aşağıdaki tabloda bu olaylar arasındaki farklar yer alır.

|Olay seçme|ContextEnter olayı|
|------------------|------------------------|
|İmleç koleksiyonun düğümlerinden birinin içine yerleştiril olduğunda <xref:Microsoft.Office.Tools.Word.XMLNodes> gerçekleşir.|İmleç, düğümün bağlamı dışındaki bir alandan koleksiyonun düğümlerinden veya alt düğümlerinden birinin <xref:Microsoft.Office.Tools.Word.XMLNodes> içine yerleştirilsin. Başka bir deyişle, yalnızca bağlam değiştinde ve birden çok iç içe denetim için <xref:Microsoft.Office.Tools.Word.XMLNodes> yükseltildi.|

 Örneğin, imleci dışından içine `Customer` taşıyarak , ve olayları harekete `CompanyName` <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `Customer` `Company` `CompanyName` geçerek. Daha sonra imleci 'den 'e taşımanız durumunda, bağlam hem hem de için aynı olduğu için yalnızca `CompanyName` `CompanyRegion` olayı ortaya <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `CompanyRegion` `Company` `Customer` çıkar. Belgenize birden `Company` çok düğüm ekleyebilirsiniz. İmleci bir düğümden başka bir düğümüne taşımanız durumunda bağlam `CompanyName` `Company` `CompanyName` `Company` aynıdır, bu nedenle yalnızca <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> olay ortaya çıkar.

 Olayla olay arasında <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> aynı farklar <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> vardır.

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode denetimi](../vsto/xmlnode-control.md)
- [Nasıl kullanılır: Word belgelerine XMLNodes denetimleri ekleme](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Nasıl kullanılır: Şemaları Visual Studio içindeki Word belgeleriyle eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
