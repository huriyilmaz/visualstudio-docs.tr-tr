---
title: 'Nasıl yapılır: ListObject denetimlerini verilerle Doldur'
description: Belgenize hızlı bir şekilde veri eklemek için veri bağlamayı kullanın. Ayrıca, verilerin görüntülenmesini sağlamak, ancak artık veri kaynağına bağlanmaması için liste nesnesinin bağlantısını kesebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 601550aa2a93b88cdd6f6b61643a8d4943be5ca1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100068"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Nasıl yapılır: ListObject denetimlerini verilerle Doldur
  Belgenize hızlı bir şekilde veri eklemek için veri bağlamayı kullanabilirsiniz. Verileri bir liste nesnesine bağladıktan sonra, verileri görüntüleyecek ancak artık veri kaynağına bağlanmadığından, liste nesnesinin bağlantısını kesebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

### <a name="to-bind-data-to-a-listobject-control"></a>ListObject denetimine veri bağlamak için

1. <xref:System.Data.DataTable>Sınıf düzeyinde oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet20":::

2. `Startup` `Sheet1` Sınıfın (belge düzeyi projesinde) veya `ThisAddIn` sınıfında (uygulama düzeyi projesinde) olay işleyicisine örnek sütun ve veri ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet21":::

3. Yöntemi çağırın <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> ve sütun adlarını görünmesi gereken sırada geçirin. Liste nesnesindeki sütunların sırası, içinde göründükleri sırayla farklılık gösterebilir <xref:System.Data.DataTable> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet22":::

### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>ListObject denetiminin veri kaynağıyla bağlantısını kesmek için

1. Yöntemini çağırın <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> `List1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb" id="Snippet23":::

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği, <xref:Microsoft.Office.Tools.Excel.ListObject> `list1` Bu kodun göründüğü çalışma sayfasında var olan bir ada sahip olduğunuzu varsayar.

## <a name="see-also"></a>Ayrıca bkz.
- [Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerde genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerdeki denetimler](../vsto/controls-on-office-documents.md)
- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl yapılır: ListObject sütunlarını verilerle eşleme](../vsto/how-to-map-listobject-columns-to-data.md)
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject denetimi](../vsto/listobject-control.md)
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md)
