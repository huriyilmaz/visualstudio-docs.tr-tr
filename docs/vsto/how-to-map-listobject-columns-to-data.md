---
title: 'Nasıl yapılır: ListObject sütunlarını verilerle eşleme'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cffd9f009d193f5ed687560b4f13940273fd82ad
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985894"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Nasıl yapılır: ListObject sütunlarını verilerle eşleme
  Bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimini <xref:System.Data.DataTable>bağladığınızda, tüm sütunları bir listede göstermek istemeyebilirsiniz veya verilere bağlı olmayan belirli sütunlara sahip olabilirsiniz. <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> yöntemini çağırdığınızda <xref:Microsoft.Office.Tools.Excel.ListObject> görünmesini istediğiniz sütunları eşleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Harita sütunları

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Bir veri tablosunu bir listedeki sütunlarla eşlemek için

1. Sınıf düzeyinde <xref:System.Data.DataTable> oluşturun.

     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]

2. `Sheet1` sınıfının (belge düzeyi projesinde) veya `ThisAddIn` sınıfında (VSTO eklenti projesinde) `Startup` olay işleyicisine örnek sütun ve veri ekleyin.

     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]

3. <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> yöntemi çağırın ve sütun adlarını görünmesi gereken sırada geçirin. Liste nesnesi yeni oluşturulan <xref:System.Data.DataTable>bağlanacak, ancak liste nesnesindeki sütunların sırası <xref:System.Data.DataTable>göründükleri sırada farklı olacaktır.

     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]

## <a name="specify-unmapped-columns"></a>Eşlenmemiş sütunları belirt
 Sütunları bir <xref:System.Data.DataTable>eşleştirdiğinizde, belirli sütunların boş bir dizeye geçerek veriye bağlanmamalıdır de belirtebilirsiniz. Daha sonra <xref:Microsoft.Office.Tools.Excel.ListObject> denetimine, verilere bağlanmamış yeni bir sütun eklenir.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>ListObject sütunlarını eşlerken eşlenmemiş bir sütun belirtmek için

1. <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> yöntemi çağırın ve sütun adlarını görünmesi gereken sırada geçirin. Eşlenmemiş bir sütunun eklendiğini göstermek için boş bir dize kullanın; Bu durumda, başlık sütunu ve soyadı sütunu arasında.

     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]

## <a name="compile-the-code"></a>Kodu derle
 Bu kod örneği, bu kodun göründüğü çalışma sayfasında `list1` adında mevcut bir <xref:Microsoft.Office.Tools.Excel.ListObject> olduğunu varsayar.

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl yapılır: ListObject denetimlerini verilerle Doldur](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject denetimi](../vsto/listobject-control.md)
