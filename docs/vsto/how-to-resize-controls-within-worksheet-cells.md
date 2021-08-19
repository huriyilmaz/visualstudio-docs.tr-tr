---
title: 'Nasıl olur: Çalışma sayfası hücrelerinde denetimleri yeniden boyutlandırma'
description: Çalışma sayfası hücrelerinde Visual Studio tasarım zamanında Microsoft Excel çalışma zamanında denetimleri yeniden boyutlandırmak için nasıl kullanabileceğiniz hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d4874215879b0b9e0070b7c108226f6baf4c4296
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147953"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Nasıl olur: Çalışma sayfası hücrelerinde denetimleri yeniden boyutlandırma
  Çalışma sayfasındaki sütunları veya satırları yeniden boyutlandırırsanız, hücre içindeki tüm konak denetimleri yeniden boyutlandırilen hücrenin yüksekliğine veya genişliğine otomatik olarak yeniden boyutlandırılır. Windows Form denetimleri varsayılan olarak otomatik olarak yeniden boyutlandırılmaz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Denetimleri tasarım zamanında eklersiniz, her denetim için konumlandırma seçeneklerini ayarlayabilirsiniz.

 Windows Forms denetimi ekler ve bir aralık bağımsız değişkeni sağlarsanız, aralık içindeki bir hücre yeniden boyutlandırılırken denetim otomatik olarak yeniden boyutlandırılır. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="resize-controls-at-design-time"></a>Tasarım zamanında denetimleri yeniden boyutlandırma

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Denetimlerin tasarım zamanında hücrelerle yeniden boyutlandırılmalarını yapmak için

1. Araç **Kutusundan,** Formlar Windows bir çalışma sayfasına sürükleyin.

2. Denetime sağ tıklayın ve ardından Biçim **Denetimi'ne tıklayın.**

3. Biçim **Denetimi iletişim** kutusunda Özellikler **sekmesine** tıklayın.

4. Nesne **Konumlandırma altında Hücrelerle** taşı **ve boyut seçeneğini belirleyin ve** ardından Tamam'a **tıklayın.**

     Denetimi içeren hücreyi yeniden boyutlandırarak hücreye sığacak şekilde denetim yeniden boyutlandırılır.

## <a name="resize-controls-at-run-time"></a>Çalışma zamanında denetimleri yeniden boyutlandırma
 Çalışma zamanında Windows Formlar denetimi ekler ve denetimin konumu olarak bir iletirsanız, aralığı içeren çalışma sayfası hücresi yeniden boyutlandırılırken denetim otomatik olarak <xref:Microsoft.Office.Interop.Excel.Range> yeniden boyutlandırılır.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Denetimlerin çalışma zamanında hücrelerle yeniden boyutlandırılmalarını yapmak için

1. A1 aralığına bir denetim ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet5":::

     Denetimi içeren hücreyi yeniden boyutlandırarak hücreye sığacak şekilde denetim yeniden boyutlandırılır.

## <a name="reset-control-placement"></a>Denetim yerleştirmeyi sıfırlama
 özelliğini aşağıdaki değerlerden biri olarak ayarerek denetimin yerleşimini `Placement` ve yeniden boyutlandırmayı <xref:Microsoft.Office.Interop.Excel.XlPlacement> sıfırlayabilirsiniz:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Bir denetimin davranışını hücreyle yeniden boyutlandırılmamak veya taşınmamak için değiştirmek için

1. Denetimin yerleştirme özelliğini çağırarak değerini olarak <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> ayarlayın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet6":::

## <a name="see-also"></a>Ayrıca bkz.
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Nasıl Windows: Windows Form denetimleri ekleme Office ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Nasıl olur: Yazdırma sırasında çalışma sayfaları denetimlerini gizleme](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Belgelerde Windows Forms denetimlerinin Office sınırlamaları](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
