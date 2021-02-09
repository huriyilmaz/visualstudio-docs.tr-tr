---
title: NamedRange denetimi
description: NamedRange denetiminin benzersiz bir ada sahip, olayları açığa çıkaran ve verilere bağlanabilen bir Aralık olduğunu öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 74eb3467c4cfbba5a2cb411a1f0ad439b1a7620b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926631"
---
# <a name="namedrange-control"></a>NamedRange denetimi
  <xref:Microsoft.Office.Tools.Excel.NamedRange>Denetim, benzersiz bir ada sahip, olayları ortaya çıkaran ve verilere bağlanabilen bir aralıktır. Daha fazla bilgi için bkz. [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Denetim oluşturma
 <xref:Microsoft.Office.Tools.Excel.NamedRange>Tasarım zamanında Microsoft Office Excel çalışma sayfasına veya belge düzeyi projelerde çalışma zamanında denetim ekleyebilirsiniz.

 <xref:Microsoft.Office.Tools.Excel.NamedRange>Bir çalışma sayfasına BIR VSTO eklentisinin çalışma zamanında denetim ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

> [!NOTE]
> Varsayılan olarak, çalışma sayfası kapatıldığında dinamik olarak oluşturulan adlandırılmış aralıklar çalışma sayfasında konak denetimleri olarak kalıcı olmaz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

 <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimler yalnızca belirli sayfalardaki aralıklardan oluşabilir. <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimlerin tüm sayfalara uygulanan göreli adları olamaz ve bir çalışma kitabındaki iki veya daha fazla çalışma sayfasını kapsayan aralıklardan oluşamaz (3-b Aralık).

## <a name="bind-data-to-the-control"></a>Verileri denetime bağlama
 Adlandırılmış bir Aralık, çok sayıda hücre içerdiğinden karmaşık veri bağlama için iyi bir aday olarak görünebilir; Ancak, bir Aralık yalnızca bir veri kümesinden belirli bir sütunla kolayca eşleştirilemez bir hücre koleksiyonudur. Bu nedenle, <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimler yalnızca basit veri bağlamayı destekler. <xref:Microsoft.Office.Tools.Excel.ListObject>Denetim karmaşık veri bağlama için kullanılabilir. Daha fazla bilgi için bkz. [ListObject denetimi](../vsto/listobject-control.md).

 <xref:Microsoft.Office.Tools.Excel.NamedRange>Denetim, özellikleri kullanılarak bir veri kaynağına bağlanabilir <xref:System.Windows.Forms.Control.DataBindings%2A> . Denetimin varsayılan veri bağlama özelliği <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> .

 Bağlantılı veri kümesindeki veriler herhangi bir mekanizmaya göre güncelleştirilirse, <xref:Microsoft.Office.Tools.Excel.NamedRange> Denetim değişiklikleri yansıtır.

## <a name="formatting"></a>Biçimlendirme
 Bir denetime uygulanabilen biçimlendirme <xref:Microsoft.Office.Interop.Excel.Range> , bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetime uygulanabilir. Bu, kenarlıkları, yazı tiplerini, sayı biçimlerini ve stilleri içerir.

## <a name="rename-the-control"></a>Denetimi yeniden adlandırma
 <xref:Microsoft.Office.Tools.Excel.NamedRange> **Araç kutusundan** çalışma sayfanıza bir denetim eklediğinizde, Visual Studio otomatik olarak denetim için bir ad oluşturur. **Özellikler** penceresinde adı değiştirebilirsiniz.

## <a name="events"></a>Ekinlikler
 Denetim için aşağıdaki olaylar mevcuttur <xref:Microsoft.Office.Tools.Excel.NamedRange> :

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [İzlenecek yol: NamedRange denetimi olaylarına karşı programlama](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
