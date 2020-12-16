---
title: XmlMappedRange denetimi
description: XmlMappedRange denetiminin, yalnızca tekrarsız bir şema öğesi Microsoft Excel 'deki bir hücreyle eşlendiğinde oluşturulan bir Aralık olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3b3fd140787d44cdd8364ce77d5292dfcd83f54
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525900"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange denetimi
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Denetim, yalnızca tekrarsız bir şema öğesi Microsoft Office Excel içindeki bir hücreyle eşlendiğinde oluşturulan bir aralıktır. Örneğin, `maxOccurs` bir şema öğesinin özniteliği 1 ' e eşitse. Visual Studio XML eşlenmiş aralığı oluşturduktan sonra, Excel nesne modelinde geçiş yapmak zorunda kalmadan doğrudan buna karşı programlama yapabilirsiniz. <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Excel içindeki bir denetimi, öğe eşleme kaldırıldığında silebilirsiniz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Verileri denetime bağlama
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Denetim, tek bir veri alanına bağlamayı destekler (basit veri bağlama). <xref:Microsoft.Office.Tools.Excel.ListObject>Denetim karmaşık veri bağlamasını destekler ve yinelenen bir şema öğesi bir hücreyle eşlendiğinde otomatik olarak oluşturulur. Daha fazla bilgi için bkz. [ListObject denetimi](../vsto/listobject-control.md).

 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Denetim, özelliğini kullanarak bir veri kaynağına bağlanır <xref:System.Windows.Forms.Control.DataBindings%2A> . Bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> çalışma sayfası hücresine eklendiğinde, Visual Studio otomatik olarak eşlenmiş hücrelerdeki verilerden bir veri kümesi oluşturur ve bu veri kümesine denetimi bağlar. Öğesinin varsayılan veri bağlama özelliği <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> .

 Bağlantılı veri kümesindeki veriler herhangi bir mekanizma aracılığıyla güncelleştirilirse, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Denetim değişiklikleri yansıtır.

## <a name="formatting"></a>Biçimlendirme
 Aynı biçimlendirmeyi <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> öğesine uygulayabileceğiniz bir denetime uygulayabilirsiniz <xref:Microsoft.Office.Interop.Excel.Range> . Buna kenarlık, yazı tipi, sayı biçimi ve stil dahildir.

## <a name="events"></a>Ekinlikler
 Denetim için kullanılabilen olaylar <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> şunlardır:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Nasıl yapılır: çalışma sayfalarına XMLMappedRange denetimleri ekleme](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Nasıl yapılır: şemaları Visual Studio içindeki çalışma sayfalarına eşleme](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
