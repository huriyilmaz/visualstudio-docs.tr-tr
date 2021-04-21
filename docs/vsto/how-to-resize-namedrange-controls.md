---
title: 'Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme'
description: Visual Studio 'Yu kullanarak bir Microsoft Excel çalışma kitabındaki NamedRange denetimlerini programlı olarak yeniden boyutlandırma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3b70b34de222c35903a4f08b95d9efe8d8f896d9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826466"
---
# <a name="how-to-resize-namedrange-controls"></a>Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme
  Bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimin boyutunu Microsoft Office Excel belgesine eklediğinizde ayarlayabilirsiniz; ancak, daha sonra yeniden boyutlandırmak isteyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Belge düzeyi projelerinde, tasarım zamanında veya çalışma zamanında adlandırılmış bir aralığı yeniden boyutlandırabilirsiniz. Ayrıca, uygulama düzeyi VSTO Eklentilerindeki çalışma zamanında adlandırılmış aralıkları yeniden boyutlandırabilirsiniz.

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında NamedRange denetimlerini yeniden boyutlandır](#designtime)

- [Belge düzeyindeki bir projede, çalışma zamanında NamedRange denetimlerini yeniden boyutlandırma](#runtimedoclevel)

- [VSTO eklenti projesindeki NamedRange denetimlerini çalışma zamanında yeniden boyutlandırma](#runtimeaddin)

## <a name="resize-namedrange-controls-at-design-time"></a><a name="designtime"></a> Tasarım zamanında NamedRange denetimlerini yeniden boyutlandır
 **Adı tanımla** iletişim kutusunda boyutunu tekrar tanımlayarak adlandırılmış bir aralığı yeniden boyutlandırabilirsiniz.

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Adlandırılmış bir aralığı adı tanımla iletişim kutusunu kullanarak yeniden boyutlandırmak için

1. Bir denetime sağ tıklayın <xref:Microsoft.Office.Tools.Excel.NamedRange> .

2. Kısayol menüsünde **adlandırılmış aralıkları Yönet** ' e tıklayın.

     **Ad tanımla** iletişim kutusu görüntülenir.

3. Yeniden boyutlandırmak istediğiniz adlandırılmış aralığı seçin.

4. **Başvuruda** bulunan kutusunun işaretini kaldırın.

5. Adlandırılmış aralığın boyutunu tanımlamak için kullanmak istediğiniz hücreleri seçin.

6. **Tamam**'a tıklayın.

## <a name="resize-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyindeki bir projede, çalışma zamanında NamedRange denetimlerini yeniden boyutlandırma
 Özelliği kullanarak adlandırılmış bir aralığı programlı şekilde yeniden boyutlandırabilirsiniz <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> .

> [!NOTE]
> **Özellikler** penceresinde, <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> özelliği salt okunurdur olarak işaretlenir.

### <a name="to-resize-a-named-range-programmatically"></a>Adlandırılmış bir aralığı programlı olarak yeniden boyutlandırmak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** hücresinde bir denetim oluşturun `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet4":::

2. Adlandırılmış aralığı **B1** hücresini içerecek şekilde yeniden boyutlandırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet5":::

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> VSTO eklenti projesindeki NamedRange denetimlerini çalışma zamanında yeniden boyutlandırma
 <xref:Microsoft.Office.Tools.Excel.NamedRange>Çalışma zamanında herhangi bir açık çalışma sayfasında bir denetimi yeniden boyutlandırabilirsiniz. <xref:Microsoft.Office.Tools.Excel.NamedRange>VSTO eklentisini kullanarak çalışma sayfasına denetim ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: NamedRange denetimleri çalışma sayfalarına ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

### <a name="to-resize-a-named-range-programmatically"></a>Adlandırılmış bir aralığı programlı olarak yeniden boyutlandırmak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** hücresinde bir denetim oluşturun `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet10":::

2. Adlandırılmış aralığı **B1** hücresini içerecek şekilde yeniden boyutlandırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet11":::

## <a name="see-also"></a>Ayrıca bkz.
- [VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Nasıl yapılır: yer Işareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)
- [Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-listobject-controls.md)
