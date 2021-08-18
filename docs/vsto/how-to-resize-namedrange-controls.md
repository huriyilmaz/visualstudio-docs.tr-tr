---
title: 'Nasıl olur: NamedRange denetimlerini yeniden boyutlandırma'
description: Visual Studio çalışma kitabındaki NamedRange denetimlerini program aracılığıyla yeniden boyutlandırmak için Microsoft Excel öğrenin.
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
ms.openlocfilehash: 6f30671c883c06834e9c00fadd81760b123ae9f4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115232"
---
# <a name="how-to-resize-namedrange-controls"></a>Nasıl olur: NamedRange denetimlerini yeniden boyutlandırma
  Denetimi bir belgeye eklerken boyutunu Microsoft Office Excel ancak daha sonra yeniden <xref:Microsoft.Office.Tools.Excel.NamedRange> boyutlandırmak da iyi olabilir.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Adlandırılmış bir aralığı tasarım zamanında veya çalışma zamanında belge düzeyindeki projelerde yeniden boyutlandırabilirsiniz. Ayrıca, uygulama düzeyindeki çalışma zamanında adlandırılmış aralıkları yeniden boyutlandırabilir ve VSTO boyutlandırabilirsiniz.

 Bu konuda aşağıdaki görevler açıklanmıştır:

- [NamedRange denetimlerini tasarım zamanında yeniden boyutlandırma](#designtime)

- [Belge düzeyi projesinde çalışma zamanında NamedRange denetimlerini yeniden boyutlandırma](#runtimedoclevel)

- [VSTO Eklenti projesinde NamedRange denetimlerini çalışma zamanında yeniden boyutlandırma](#runtimeaddin)

## <a name="resize-namedrange-controls-at-design-time"></a><a name="designtime"></a> NamedRange denetimlerini tasarım zamanında yeniden boyutlandırma
 Adlandırılmış aralığı, Adı Tanımla iletişim kutusunda boyutunu yeniden **tanımlayarak yeniden boyutlandırabilirsiniz.**

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Ad Tanımla iletişim kutusunu kullanarak adlandırılmış bir aralığı yeniden boyutlandırmak için

1. Bir denetime sağ <xref:Microsoft.Office.Tools.Excel.NamedRange> tıklayın.

2. Kısayol **menüsünde Adlandırılmış Aralıkları** Yönet'e tıklayın.

     Ad **Tanımla** iletişim kutusu görüntülenir.

3. Yeniden boyutlandırmak istediğiniz adlandırılmış aralığı seçin.

4. Başvurular **kutusunu** temizleyin.

5. Adlandırılmış aralığın boyutunu tanımlamak için kullanmak istediğiniz hücreleri seçin.

6. **Tamam**'a tıklayın.

## <a name="resize-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyindeki projede çalışma zamanında NamedRange denetimlerini yeniden boyutlandırma
 özelliğini kullanarak adlandırılmış bir aralığı program aracılığıyla yeniden <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> boyutlandırabilirsiniz.

> [!NOTE]
> Özellikler **penceresinde,** özelliği <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> salt okunur olarak işaretlenir.

### <a name="to-resize-a-named-range-programmatically"></a>Adlandırılmış bir aralığı program aracılığıyla yeniden boyutlandırmak için

1. hücresi <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** üzerinde bir denetim `Sheet1` oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet4":::

2. Adlandırılmış aralığı B1 hücresini içerecek **şekilde yeniden boyutlandırabilirsiniz.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet5":::

## <a name="resize-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>VSTO Add-in projesinde Çalışma zamanında NamedRange denetimlerini yeniden boyutlandırma
 Çalışma zamanında herhangi bir <xref:Microsoft.Office.Tools.Excel.NamedRange> açık çalışma sayfasında denetimi yeniden boyutlandırabilirsiniz. VSTO Eklentisini kullanarak çalışma sayfasına denetim ekleme hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Excel.NamedRange> bkz. Nasıl ekleyebilirsiniz: [NamedRange denetimlerini çalışma sayfalarına ekleme.](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

### <a name="to-resize-a-named-range-programmatically"></a>Adlandırılmış bir aralığı program aracılığıyla yeniden boyutlandırmak için

1. hücresi <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** üzerinde bir denetim `Sheet1` oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet10":::

2. Adlandırılmış aralığı B1 hücresini içerecek **şekilde yeniden boyutlandırabilirsiniz.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet11":::

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma zamanında Word Excel ve VSTO çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Genişletilmiş Excel kullanarak nesneleri otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange denetimi](../vsto/namedrange-control.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Nasıl olur: Yer İşareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)
- [Nasıl olur: ListObject denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-listobject-controls.md)
