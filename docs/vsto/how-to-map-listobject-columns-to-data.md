---
title: 'Nasıl kullanılır: ListObject sütunlarını veriyle eşleme'
description: SetDataBinding yöntemini çağırarak ListObject içinde görünmesini istediğiniz sütunları nasıl eşleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e611ebd51428b91311dade00b42095ba0501d276b2dfe91f7a407593894348fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394660"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Nasıl kullanılır: ListObject sütunlarını veriyle eşleme
  Bir denetimi bir 'a bağlayabilirsiniz. Bir listede yer alan tüm sütunları görüntülemek istemeyebilirsiniz veya verilere bağlı olan belirli <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Data.DataTable> sütunlarız olabilir. yöntemini çağırarak içinde görünmesini istediğiniz sütunları <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> eşlayabilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Sütunları eşleme

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Bir veri tabloyu bir listede sütunlara eşlemek için

1. sınıf <xref:System.Data.DataTable> düzeyinde oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet16":::

2. Sınıfın (belge düzeyi projesinde) veya sınıfın olay işleyicisinde örnek sütunlar ve veriler `Startup` `Sheet1` ekleyin `ThisAddIn` (VSTO Projesinde).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet17":::

3. yöntemini <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> çağırarak sütun adlarını görünmeleri gereken sırayla iletir. Liste nesnesi yeni oluşturulan nesnesine bağlı olur, ancak liste nesnesinde sütunların sırası, içinde görünme <xref:System.Data.DataTable> sıralarından farklı <xref:System.Data.DataTable> olur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet18":::

## <a name="specify-unmapped-columns"></a>Eşlenmemiş sütunları belirtme
 Sütunları bir ile eşlerken, boş bir dizeyi geçerek belirli sütunların <xref:System.Data.DataTable> verilere bağlı olmadığını da belirtebilirsiniz. Daha sonra denetime verilere bağlı değil yeni bir sütun <xref:Microsoft.Office.Tools.Excel.ListObject> eklenir.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>ListObject sütunlarını eşlerken eşlenmemiş bir sütun belirtmek için

1. yöntemini <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> çağırarak sütun adlarını görünmeleri gereken sırayla iletir. Eşlenmemiş bir sütunun ekli olduğu yeri belirtmek için boş bir dize kullanın; bu durumda, başlık sütunu ile soyadı sütunu arasında.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb" id="Snippet19":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu kod örneğinde, bu kodun göründüğü <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasında adlı bir var olan var olan bir `list1` varsayalım.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl kullanılır: ListObject denetimlerini verilerle doldurma](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Genişletilmiş Excel kullanarak otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject denetimi](../vsto/listobject-control.md)
