---
title: 'Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme'
description: bir Microsoft Excel çalışma kitabındaki NamedRange denetimlerini programlı olarak yeniden boyutlandırmak için Visual Studio nasıl kullanabileceğinizi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 33f07b0dd91654216e1465223a04bc5e1ab21300e1fdd6a2f3f70a0fde6bc218
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384164"
---
# <a name="how-to-resize-namedrange-controls"></a>Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme
  bir denetimin boyutunu bir <xref:Microsoft.Office.Tools.Excel.NamedRange> Microsoft Office Excel belgesine eklediğinizde ayarlayabilirsiniz; ancak, daha sonra yeniden boyutlandırmak isteyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Belge düzeyi projelerinde, tasarım zamanında veya çalışma zamanında adlandırılmış bir aralığı yeniden boyutlandırabilirsiniz. ayrıca, uygulama düzeyinde VSTO eklentilerinde adlandırılmış aralıkları çalışma zamanında yeniden boyutlandırabilirsiniz.

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında NamedRange denetimlerini yeniden boyutlandır](#designtime)

- [Belge düzeyindeki bir projede, çalışma zamanında NamedRange denetimlerini yeniden boyutlandırma](#runtimedoclevel)

- [VSTO eklentisi projesindeki NamedRange denetimlerini çalışma zamanında yeniden boyutlandır](#runtimeaddin)

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

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>VSTO eklentisi projesindeki NamedRange denetimlerini çalışma zamanında yeniden boyutlandır
 <xref:Microsoft.Office.Tools.Excel.NamedRange>Çalışma zamanında herhangi bir açık çalışma sayfasında bir denetimi yeniden boyutlandırabilirsiniz. <xref:Microsoft.Office.Tools.Excel.NamedRange>VSTO eklentisi kullanarak çalışma sayfasına denetim ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: NamedRange denetimleri çalışma sayfalarına ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

### <a name="to-resize-a-named-range-programmatically"></a>Adlandırılmış bir aralığı programlı olarak yeniden boyutlandırmak için

1. <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** hücresinde bir denetim oluşturun `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet10":::

2. Adlandırılmış aralığı **B1** hücresini içerecek şekilde yeniden boyutlandırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet11":::

## <a name="see-also"></a>Ayrıca bkz.
- [Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerde genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office belgelerdeki denetimler](../vsto/controls-on-office-documents.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Nasıl yapılır: yer Işareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)
- [Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-listobject-controls.md)
