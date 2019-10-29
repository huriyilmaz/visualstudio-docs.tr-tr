---
title: 'Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fdebceb7ed6357542877bf13522425f7c013da73
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985747"
---
# <a name="how-to-resize-listobject-controls"></a>Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma
  Bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimin boyutunu, bir Microsoft Office Excel çalışma kitabına eklediğinizde ayarlarsınız; Ancak, daha sonra yeniden boyutlandırmak isteyebilirsiniz. Örneğin, iki sütunlu bir listeyi üç sütun olarak değiştirmek isteyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Tasarım zamanında <xref:Microsoft.Office.Tools.Excel.ListObject> denetimleri veya belge düzeyi projelerde çalışma zamanında yeniden boyutlandırabilirsiniz. Bir VSTO eklenti projesindeki <xref:Microsoft.Office.Tools.Excel.ListObject> denetimlerini çalışma zamanında yeniden boyutlandırabilirsiniz.

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında ListObject denetimlerini yeniden boyutlandır](#designtime)

- [Belge düzeyindeki bir projede, çalışma zamanında ListObject denetimlerini yeniden boyutlandırma](#runtimedoclevel)

- [VSTO eklenti projesindeki ListObject denetimlerini çalışma zamanında yeniden boyutlandırma](#runtimeaddin)

  <xref:Microsoft.Office.Tools.Excel.ListObject> denetimleri hakkında daha fazla bilgi için bkz. [ListObject denetimi](../vsto/listobject-control.md).

## <a name="designtime"></a>Tasarım zamanında ListObject denetimini yeniden boyutlandırma
 Bir listeyi yeniden boyutlandırmak için, boyutlandırma tutamaçlarından birini tıklatabilir ve sürükleyebilirsiniz ya da **Listeyi yeniden boyutlandır** iletişim kutusunda boyutunu yeniden tanımlayabilirsiniz.

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Listeyi yeniden boyutlandır iletişim kutusunu kullanarak bir listeyi yeniden boyutlandırmak için

1. <xref:Microsoft.Office.Tools.Excel.ListObject> tablosundaki herhangi bir yere tıklayın. Şeritteki **tablo araçları** > **Tasarım** sekmesi görüntülenir.

2. Özellikler bölümünde, **tabloyu yeniden boyutlandır**' ı tıklatın.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Tablonuz için yeni veri aralığını seçin.

4. **Tamam**'a tıklayın.

## <a name="runtimedoclevel"></a>Belge düzeyindeki bir projede bir ListObject denetimini çalışma zamanında yeniden boyutlandırma
 Bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimini çalışma zamanında <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> metodunu kullanarak yeniden boyutlandırabilirsiniz. <xref:Microsoft.Office.Tools.Excel.ListObject> denetimini çalışma sayfasındaki yeni bir konuma taşımak için bu yöntemi kullanamazsınız. Üst bilgiler aynı satırda kalmalıdır ve yeniden boyutlandırılmış <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi özgün liste nesnesiyle çakışmalıdır. Yeniden boyutlandırılan <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi bir başlık satırı ve en az bir veri satırı içermelidir.

### <a name="to-resize-a-list-object-programmatically"></a>Bir liste nesnesini programlı olarak yeniden boyutlandırmak için

1. `Sheet1`hücresinde **a1** ile **B3** arası bir denetim <xref:Microsoft.Office.Tools.Excel.ListObject> oluşturun.

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. Listeyi, **a1** ile **C5**arasındaki hücreleri içerecek şekilde yeniden boyutlandırın.

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="runtimeaddin"></a>VSTO eklenti projesindeki bir ListObject 'i çalışma zamanında yeniden boyutlandırma
 Çalışma zamanında herhangi bir açık çalışma sayfasında <xref:Microsoft.Office.Tools.Excel.ListObject> denetimini yeniden boyutlandırabilirsiniz. VSTO eklentisini kullanarak çalışma sayfasına <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: ListObject denetimlerini çalışma sayfalarına ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Bir liste nesnesini programlı olarak yeniden boyutlandırmak için

1. `Sheet1`hücresinde **a1** ile **B3** arası bir denetim <xref:Microsoft.Office.Tools.Excel.ListObject> oluşturun.

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. Listeyi, **a1** ile **C5**arasındaki hücreleri içerecek şekilde yeniden boyutlandırın.

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject denetimi](../vsto/listobject-control.md)
- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Nasıl yapılır: yer Işareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)
- [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)
