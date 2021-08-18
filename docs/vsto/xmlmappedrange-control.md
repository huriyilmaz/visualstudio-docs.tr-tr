---
title: XmlMappedRange denetimi
description: XmlMappedRange denetimi, yalnızca yinelenen olmayan bir şema öğesi, yinelenen bir şema öğesi Microsoft Excel.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 173120009b6d295f04c467900e1918361cb5900e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045937"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange denetimi
  Denetim, yalnızca yinelenen olmayan bir şema öğesi bir şema öğesi <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Microsoft Office Excel. Örneğin, bir şema `maxOccurs` öğesinin özniteliği 1'e eşit olduğunda. Bu Visual Studio XML eşlenen aralığını oluşturduğunda, nesne modelini çapraz geçiş yapmak zorunda kalmadan doğrudan Excel programlaabilirsiniz. Bir denetimi yalnızca öğe <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> eşlemesi Excel içinde silebilirsiniz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Denetime veri bağlama
 Denetim, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> tek bir veri alanına bağlamayı destekler (basit veri bağlama). Denetim <xref:Microsoft.Office.Tools.Excel.ListObject> karmaşık veri bağlamayı destekler ve yinelenen şema öğesi bir hücreye eşlenirken otomatik olarak oluşturulur. Daha fazla bilgi için bkz. [ListObject denetimi.](../vsto/listobject-control.md)

 Denetimin <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> özelliği kullanılarak bir veri kaynağına bağlı <xref:System.Windows.Forms.Control.DataBindings%2A> olması. Çalışma sayfası hücresine bir ek Visual Studio, eşlenen hücrelerde veri kümesinden otomatik olarak bir veri kümesi üretir ve denetimi bu veri <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kümesine bağlar. varsayılan veri bağlama <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> özelliğidir.

 Bağlı veri kümesinde yer alan veriler herhangi bir mekanizma aracılığıyla <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> güncelleştirilirse denetim değişiklikleri yansıtıyor.

## <a name="formatting"></a>Biçimlendirme
 Aynı biçimlendirmeyi bir denetime <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> uygulayan bir denetimine <xref:Microsoft.Office.Interop.Excel.Range> uygulayabilirsiniz. Buna kenarlıklar, yazı tipleri, sayı biçimi ve stiller dahildir.

## <a name="events"></a>Ekinlikler
 Denetim için kullanılabilen <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> olaylar:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş Excel kullanarak otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Nasıl yapılır: Çalışma sayfalarına XMLMappedRange denetimleri ekleme](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Nasıl ekleyebilirsiniz: Şemaları çalışma sayfalarıyla eşleme Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
