---
title: XMLNode denetimi
description: XMLNode denetiminde olayları ortaya çıkaran ve verilere bağlanabilecek eşlenmiş bir XML düğümü nesnesi olduğunu öğrenin.
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
ms.openlocfilehash: 8b3c67526ac00f9cc7266f6bb93992505d3b70ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068281"
---
# <a name="xmlnode-control"></a>XMLNode denetimi
  **Önemli** Microsoft Word ile ilgili bu konu başlığı altında açıklanan bilgiler, Microsoft tarafından Microsoft Word Birleşik Devletler Ocak 2010'dan önce Microsoft tarafından lisanslanmıştır ve Ocak 2010'dan önce Microsoft tarafından lisanslanmıştır ve özel XML ile ilgili belirli bir işlevselliğin uygulamasını kaldıran veya üzerinde çalışan programları kullanan veya geliştiren kişiler ve kuruluşların kullanımı için özel olarak Microsoft Word. Microsoft Word ile ilgili bu bilgiler, Birleşik Devletler'daki veya Birleşik Devletler'daki veya Microsoft tarafından 10 Ocak 2010'dan sonra lisansları alınan Microsoft Word ürünleri üzerinde çalışan programları kullanan veya geliştiren kişiler veya kuruluşlar tarafından okunamayabilirsiniz veya kullanılamaz; bu ürünler, o tarihten önce lisansa sahip olan veya satın alınan ve satın alınan ve satın alınan ürünlerle aynı şekilde davranmaz Birleşik Devletler.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Denetim, <xref:Microsoft.Office.Tools.Word.XMLNode> olayları ortaya çıkaran ve verilere bağlanabilecek eşlenmiş bir XML düğümü nesnesidir. Denetim yalnızca yinelenen olmayan bir şema öğesi Word belgesinde bir Microsoft Office <xref:Microsoft.Office.Tools.Word.XMLNode> oluşturulur. Bu Visual Studio XML düğümünü oluşturduğunda, Word nesne modelini çapraz geçiş yapmak zorunda kalmadan doğrudan buna karşı programlayabilirsiniz.

 Denetim <xref:Microsoft.Office.Tools.Word.XMLNode> yalnızca Word'de öğe eşlemesi kaldırılarak silinebilir.

## <a name="bind-data-to-the-control"></a>Denetime veri bağlama
 Denetim, <xref:Microsoft.Office.Tools.Word.XMLNode> basit veri bağlamayı destekler. XML düğümü, özelliği kullanılarak bir veri kaynağına <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> bağlanmalıdır. Bağlı veri kümesinde veriler güncelleştirildiğinde denetim <xref:Microsoft.Office.Tools.Word.XMLNode> değişiklikleri yansıtıyor.

## <a name="formatting"></a>Biçimlendirme
 Bir nesneye uygulanan <xref:Microsoft.Office.Interop.Word.XMLNode> biçimlendirme bir denetime <xref:Microsoft.Office.Tools.Word.XMLNode> uygulanabilir. Bu yazı tiplerini, alt çizgi stillerini ve karakter stillerini içerir.

## <a name="events"></a>Ekinlikler
 Denetim için aşağıdaki olaylar <xref:Microsoft.Office.Tools.Word.XMLNode> kullanılabilir:

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Olayları karşılaştırma
 Kullanıcı imlecini belirli bir denetimin bağlamının içinde hareket ettiğinde bir olayı <xref:Microsoft.Office.Tools.Word.XMLNode> yakalar. Örneğin, adlı bir alt denetimi olan ve adlı iki alt denetimi olan <xref:Microsoft.Office.Tools.Word.XMLNode> ve aşağıdaki gibi adlı bir `Customer` <xref:Microsoft.Office.Tools.Word.XMLNode> `Company` `Company` <xref:Microsoft.Office.Tools.Word.XMLNode> `CompanyName` `CompanyRegion` denetime sahip olabilir:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 İmleç düğüme her taşındığında eylemler bölmesinde bir denetim göstermek istemeniz, imlecin içine yerleştirilip yerleştirilip yerleştirilmalarının ya da her ikisinin de bağlamı içinde olması `Company` `CompanyName` fark `CompanyRegion` `Company` etmez. Bu durumda, durumunda kodunuzu <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> `Company` yazabilirsiniz.

 Çoğu durumda, imleç bir <xref:Microsoft.Office.Tools.Word.XMLNode> denetime girdiği zaman hem <xref:Microsoft.Office.Tools.Word.XMLNode.Select> hem de olayları ortaya <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> çıkar. Aşağıdaki tabloda bu olaylar arasındaki farklar yer alır.

|Olay'ı seçin|ContextEnter Olayı|
|------------------|------------------------|
|İmleç bir içine yerleştirilirken <xref:Microsoft.Office.Tools.Word.XMLNode> gerçekleşir.|İmleç, düğümün bağlamı dışındaki bir alandan bir veya onun alt düğümlerinin <xref:Microsoft.Office.Tools.Word.XMLNode> içine yerleştirilirken gerçekleşir. Başka bir deyişle, yalnızca bağlam değiştiklerde bu yükseltildi.|

 Örneğin, imleci dışından içine `Customer` taşıyarak , ve için olay harekete `CompanyName` <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> `Customer` `Company` `CompanyName` geçerek. İmleci 'den 'e taşımanız durumunda, hem hem de bağlamında hala yer asanız bile yalnızca `CompanyName` `CompanyRegion` olayı ortaya <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> `CompanyRegion` `Company` `Customer` çıkar.

 Olay ve olay arasında aynı <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> farklar <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> vardır.

## <a name="see-also"></a>Ayrıca bkz.
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNodes denetimi](../vsto/xmlnodes-control.md)
- [Nasıl kullanılır: Word belgelerine XMLNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Nasıl kullanılır: Şemaları Visual Studio içindeki Word belgeleriyle eşleme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
