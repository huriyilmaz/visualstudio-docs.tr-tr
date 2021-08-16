---
title: NamedRange denetimi
description: NamedRange denetiminde benzersiz bir adı olan, olayları ortaya çıkaran ve verilere bağlanan bir aralık olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 002fa5135eb99c671cd00eef76299858a3c8cba4ae1ea80cec46335486fb3d69
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121366023"
---
# <a name="namedrange-control"></a>NamedRange denetimi
  Denetim, <xref:Microsoft.Office.Tools.Excel.NamedRange> benzersiz bir adı olan, olayları ortaya çıkaran ve verilere bağlanan bir aralıktır. Daha fazla bilgi için [bkz. Excel modeline genel bakış.](../vsto/excel-object-model-overview.md)

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Denetimi oluşturma
 Çalışma sayfasına <xref:Microsoft.Office.Tools.Excel.NamedRange> tasarım zamanında Microsoft Office Excel belge düzeyi projelerde çalışma zamanında denetimler ekleyebilirsiniz.

 Çalışma zamanında <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfasına denetimler eklemek için VSTO ekleyebilirsiniz. Daha fazla bilgi için, [bkz. How to: Add NamedRange controls to worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

> [!NOTE]
> Varsayılan olarak, çalışma sayfası kapatıldığında dinamik olarak oluşturulan adlandırılmış aralıklar konak denetimleri olarak çalışma sayfasında kalıcı olmaz. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimler yalnızca belirli sayfalarda yer alan aralıklardan oluşur. <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimler tüm sayfalara uygulanabilecek göreli adlara sahip olamaz ve bir çalışma kitabındaki iki veya daha fazla çalışma sayfasına yayılan aralıklardan (3-B aralıklar) oluşan aralıklardan oluşan olamaz.

## <a name="bind-data-to-the-control"></a>Denetime veri bağlama
 Adlandırılmış aralık, birçok hücreye sahip olduğu için karmaşık veri bağlama için iyi bir aday gibi görünebilir; ancak, aralık yalnızca bir veri kümesinden belirli bir sütuna kolayca eşlenen bir hücre koleksiyonudur. Bu nedenle, <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimler yalnızca basit veri bağlamayı destekler. Denetim, <xref:Microsoft.Office.Tools.Excel.ListObject> karmaşık veri bağlama için kullanılabilir. Daha fazla bilgi için bkz. [ListObject denetimi.](../vsto/listobject-control.md)

 Denetim, <xref:Microsoft.Office.Tools.Excel.NamedRange> özellikleri kullanılarak bir veri kaynağına bağlı <xref:System.Windows.Forms.Control.DataBindings%2A> olabilir. Denetimin varsayılan veri bağlama <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğidir.

 Bağlı veri kümesinde yer alan veriler herhangi bir mekanizma aracılığıyla <xref:Microsoft.Office.Tools.Excel.NamedRange> güncelleştirilirse denetim değişiklikleri yansıtıyor.

## <a name="formatting"></a>Biçimlendirme
 bir denetimine uygulanan <xref:Microsoft.Office.Interop.Excel.Range> biçimlendirme bir denetime <xref:Microsoft.Office.Tools.Excel.NamedRange> uygulanabilir. Buna kenarlıklar, yazı tipleri, sayı biçimleri ve stiller dahildir.

## <a name="rename-the-control"></a>Denetimi yeniden adlandırma
 Çalışma sayfanıza <xref:Microsoft.Office.Tools.Excel.NamedRange> Araç Kutusundan bir denetim **eklerken,** Visual Studio otomatik olarak bir ad üretir. Adı Özellikler penceresinde **değiştirebilirsiniz.**

## <a name="events"></a>Ekinlikler
 Denetim için aşağıdaki olaylar <xref:Microsoft.Office.Tools.Excel.NamedRange> kullanılabilir:

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş Excel kullanarak otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Nasıl olur: NamedRange denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-namedrange-controls.md)
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Adım adım kılavuz: NamedRange denetimi olaylarına karşı programla](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
