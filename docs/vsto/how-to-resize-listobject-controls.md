---
title: 'Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma'
description: bir Microsoft Excel çalışma kitabındaki ListObject denetimlerini programlı bir şekilde yeniden boyutlandırmak için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0dedb2aad7598e1a9a3f97123260580de9a93f34
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099691"
---
# <a name="how-to-resize-listobject-controls"></a>Nasıl yapılır: ListObject denetimlerini yeniden boyutlandırma
  bir denetimin boyutunu bir <xref:Microsoft.Office.Tools.Excel.ListObject> Microsoft Office Excel çalışma kitabına eklediğinizde ayarlarsınız; ancak, daha sonra yeniden boyutlandırmak isteyebilirsiniz. Örneğin, iki sütunlu bir listeyi üç sütun olarak değiştirmek isteyebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 <xref:Microsoft.Office.Tools.Excel.ListObject>Tasarım zamanında veya çalışma zamanında denetimleri belge düzeyi projelerde yeniden boyutlandırabilirsiniz. <xref:Microsoft.Office.Tools.Excel.ListObject>VSTO eklentisi projesindeki denetimleri çalışma zamanında yeniden boyutlandırabilirsiniz.

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında ListObject denetimlerini yeniden boyutlandır](#designtime)

- [Belge düzeyindeki bir projede, çalışma zamanında ListObject denetimlerini yeniden boyutlandırma](#runtimedoclevel)

- [VSTO eklentisi projesindeki ListObject denetimlerini çalışma zamanında yeniden boyutlandırma](#runtimeaddin)

  Denetimler hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Excel.ListObject> bkz. [ListObject denetimi](../vsto/listobject-control.md).

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> Tasarım zamanında ListObject denetimini yeniden boyutlandırma
 Bir listeyi yeniden boyutlandırmak için, boyutlandırma tutamaçlarından birini tıklatabilir ve sürükleyebilirsiniz ya da **Listeyi yeniden boyutlandır** iletişim kutusunda boyutunu yeniden tanımlayabilirsiniz.

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>Listeyi yeniden boyutlandır iletişim kutusunu kullanarak bir listeyi yeniden boyutlandırmak için

1. Tabloda herhangi bir yere tıklayın  <xref:Microsoft.Office.Tools.Excel.ListObject> . Şeritteki **Tablo Araçları**  >  **Tasarım** sekmesi görüntülenir.

2. Özellikler bölümünde, **tabloyu yeniden boyutlandır**' ı tıklatın.

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. Tablonuz için yeni veri aralığını seçin.

4. **Tamam**'a tıklayın.

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyindeki bir projede bir ListObject denetimini çalışma zamanında yeniden boyutlandırma
 <xref:Microsoft.Office.Tools.Excel.ListObject>Yöntemini kullanarak çalışma zamanında bir denetimi yeniden boyutlandırabilirsiniz <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> . Bu yöntemi, <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi çalışma sayfasındaki yeni bir konuma taşımak için kullanamazsınız. Üst bilgiler aynı satırda kalmalıdır ve yeniden boyutlandırılmış <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim özgün liste nesnesiyle çakışmalıdır. Yeniden boyutlandırılmış <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim bir başlık satırı ve en az bir veri satırı içermelidir.

### <a name="to-resize-a-list-object-programmatically"></a>Bir liste nesnesini programlı olarak yeniden boyutlandırmak için

1. <xref:Microsoft.Office.Tools.Excel.ListObject> **A1** hücresini **B3** üzerinden kapsayan bir denetim oluşturun `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet6":::

2. Listeyi, **a1** ile **C5** arasındaki hücreleri içerecek şekilde yeniden boyutlandırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>VSTO eklentisi projesindeki bir ListObject 'i çalışma zamanında yeniden boyutlandırma
 <xref:Microsoft.Office.Tools.Excel.ListObject>Çalışma zamanında herhangi bir açık çalışma sayfasında bir denetimi yeniden boyutlandırabilirsiniz. <xref:Microsoft.Office.Tools.Excel.ListObject>VSTO eklentisi kullanarak çalışma sayfasına denetim ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: ListObject denetimlerini çalışma sayfalarına ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md).

### <a name="to-resize-a-list-object-programmatically"></a>Bir liste nesnesini programlı olarak yeniden boyutlandırmak için

1. <xref:Microsoft.Office.Tools.Excel.ListObject> **A1** hücresini **B3** üzerinden kapsayan bir denetim oluşturun `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet12":::

2. Listeyi, **a1** ile **C5** arasındaki hücreleri içerecek şekilde yeniden boyutlandırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Ayrıca bkz.
- [Word belgelerini ve Excel çalışma kitaplarını çalışma zamanında VSTO eklentilerde genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office belgelerdeki denetimler](../vsto/controls-on-office-documents.md)
- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [genişletilmiş nesneleri kullanarak Excel otomatikleştirin](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject denetimi](../vsto/listobject-control.md)
- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Nasıl yapılır: yer Işareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)
- [Nasıl yapılır: NamedRange denetimlerinin boyutunu değiştirme](../vsto/how-to-resize-namedrange-controls.md)
