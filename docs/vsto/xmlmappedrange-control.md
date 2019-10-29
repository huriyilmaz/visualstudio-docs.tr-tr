---
title: XmlMappedRange denetimi
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
ms.openlocfilehash: 01417d9c08491edc882f7f758bb36e6184500e52
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985367"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange denetimi
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetimi, yalnızca tekrarsız bir şema öğesi Microsoft Office Excel içindeki bir hücreyle eşlendiğinde oluşturulan bir aralıktır. Örneğin, bir şema öğesinin `maxOccurs` özniteliği 1 ' e eşitse. Visual Studio XML eşlenmiş aralığı oluşturduktan sonra, Excel nesne modelinde geçiş yapmak zorunda kalmadan doğrudan buna karşı programlama yapabilirsiniz. Excel içindeki bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetimini, öğe eşleme kaldırıldığında silebilirsiniz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Verileri denetime bağlama
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetim tek bir veri alanına bağlamayı destekler (basit veri bağlama). <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi karmaşık veri bağlamasını destekler ve yinelenen bir şema öğesi bir hücreyle eşlendiğinde otomatik olarak oluşturulur. Daha fazla bilgi için bkz. [ListObject denetimi](../vsto/listobject-control.md).

 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetimi, <xref:System.Windows.Forms.Control.DataBindings%2A> özelliğini kullanarak bir veri kaynağına bağlanır. Çalışma sayfası hücresine bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> eklendiğinde, Visual Studio otomatik olarak eşlenmiş hücrelerdeki verilerden bir veri kümesi oluşturur ve denetimi bu veri kümesine bağlar. <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> varsayılan veri bağlama özelliği <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.

 Bağlantılı veri kümesindeki veriler herhangi bir mekanizma aracılığıyla güncelleştirilirse, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetimi değişiklikleri yansıtır.

## <a name="formatting"></a>Biçimlendirme
 Aynı biçimlendirmeyi bir <xref:Microsoft.Office.Interop.Excel.Range>uygulayabileceğiniz bir <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetimine uygulayabilirsiniz. Buna kenarlık, yazı tipi, sayı biçimi ve stil dahildir.

## <a name="events"></a>Olaylar
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> denetimi için kullanılabilen olaylar şunlardır:

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
