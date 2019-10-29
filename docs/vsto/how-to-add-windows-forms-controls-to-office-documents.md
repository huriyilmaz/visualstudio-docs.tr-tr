---
title: 'Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c4484d07c5cfb77a5fa17460859972bc58b219fc
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986001"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme
  Belge düzeyi projelerinde, tasarım zamanında Excel Microsoft Office ve Microsoft Office Word belgelerine Windows Forms denetimleri ekleyebilirsiniz. Çalışma zamanında, belge düzeyi özelleştirmelerine ve VSTO eklentilerine denetim ekleyebilirsiniz. Örneğin, kullanıcıların bir seçenek listesinden seçim yapabilmesi için çalışma sayfanıza bir <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> denetimi ekleyebilirsiniz.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında denetim ekleme](#designtime)

- [Belge düzeyi projelerde çalışma zamanında denetim ekleme](#runtimedoclevel)

- [VSTO eklentilerinde çalışma zamanında denetim ekleme](#runtimeaddin)

## <a name="designtime"></a>Tasarım zamanında denetim ekleme
 Belge düzeyindeki bir projede belgeye tasarım zamanında Windows Forms denetimleri eklemenin birkaç yolu vardır.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Windows Forms denetimini belgeye sürüklemek için

1. Belge tasarımcıda görünür olması için Visual Studio 'da bir Excel çalışma kitabı projesi veya Word belgesi projesi oluşturun veya açın. Proje oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Araç kutusunun** **ortak denetimler** sekmesinde eklemek istediğiniz denetime tıklayın ve belgeyi belgeye sürükleyin.

    > [!NOTE]
    > Excel 'de bir denetim seçtiğinizde, **Formül çubuğuna** **= embed ("WinForms. Control. Host", "")** görürsünüz. Bu metin gereklidir ve silinmemelidir.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Belgede Windows Forms denetimi çizmek için

1. Belge tasarımcıda görünür olması için Visual Studio 'da bir Excel çalışma kitabı projesi veya Word belgesi projesi oluşturun veya açın. Proje oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Araç kutusunun** **ortak denetimler** sekmesinde, eklemek istediğiniz denetime tıklayın.

3. Belge üzerinde, denetimin sol üst köşesinin bulunmasını istediğiniz yere tıklayın ve denetimin sağ alt köşesinin bulunmasını istediğiniz yere sürükleyin.

     Denetim belgeye belirtilen konum ve boyutla eklenir.

    > [!NOTE]
    > Excel 'de bir denetim seçtiğinizde, **Formül çubuğuna** **= embed ("WinForms. Control. Host", "")** görürsünüz. Bu metin gereklidir ve silinmemelidir.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Denetime tek tıklanarak belgeye Windows Forms denetimi eklemek için

1. Belge tasarımcıda görünür olması için Visual Studio 'da bir Excel çalışma kitabı projesi veya Word belgesi projesi oluşturun veya açın. Proje oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Araç kutusunun** **ortak denetimler** sekmesinde, eklemek istediğiniz denetime tıklayın

3. Bir belge, denetimin eklenmesini istediğiniz yere tıklayın.

     Denetim belgeye varsayılan boyutla eklenir.

    > [!NOTE]
    > Excel 'de bir denetim seçtiğinizde, **Formül çubuğuna** **= embed ("WinForms. Control. Host", "")** görürsünüz. Bu metin gereklidir ve silinmemelidir.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Denetime çift tıklayarak belgeye Windows Forms denetimi eklemek için

1. Belge tasarımcıda görünür olması için Visual Studio 'da bir Excel çalışma kitabı projesi veya Word belgesi projesi oluşturun veya açın. Proje oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Araç kutusunun** **ortak denetimler** sekmesinde, eklemek istediğiniz denetime çift tıklayın.

     Denetim belgeye belge veya etkin bölmesinin merkezinde eklenir.

    > [!NOTE]
    > Excel 'de bir denetim seçtiğinizde, **Formül çubuğuna** **= embed ("WinForms. Control. Host", "")** görürsünüz. Bu metin gereklidir ve silinmemelidir.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>ENTER tuşuna basarak belgeye Windows Forms denetimi eklemek için

1. Belge tasarımcıda görünür olması için Visual Studio 'da bir Excel çalışma kitabı projesi veya Word belgesi projesi oluşturun veya açın. Proje oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. **Araç kutusunun** **ortak denetimler** sekmesinde, eklemek Istediğiniz denetime tıklayın ve **ENTER** tuşuna basın.

     Denetim belgeye belge veya etkin bölmesinin merkezinde eklenir.

    > [!NOTE]
    > Excel 'de bir denetim seçtiğinizde, **Formül çubuğuna** **= embed ("WinForms. Control. Host", "")** görürsünüz. Bu metin gereklidir ve silinmemelidir.

## <a name="runtimedoclevel"></a>Belge düzeyi projelerde çalışma zamanında denetim ekleme
 Çalışma zamanında bir belgeye program aracılığıyla Windows Forms denetimleri ekleyebilirsiniz. Word 'de, `ThisDocument` sınıfının <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> özelliğinin yöntemlerini kullanın. Excel 'de, bir `Sheet`*n* sınıfının <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> özelliğinin yöntemlerini kullanın. Her yöntemde, denetimin konumunu farklı şekillerde belirtmenize imkan tanıyan birkaç aşırı yükleme vardır.

 Çalışma zamanında bir belgeye Windows Forms denetimi eklediğinizde, belge kapatıldığında denetim belgede kalıcı olmaz. Belgeyi bir dahaki sefer açıldığında denetimi yeniden oluşturabilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Çalışma zamanında bir Windows Forms denetimi eklemek için

1. Add\<*Control Class*adlı bir yöntemi kullanın > ( *denetim sınıfı* , <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>gibi eklemek istediğiniz Windows Forms denetiminin sınıf adıdır).

     Aşağıdaki kod örneği, Excel için belge düzeyindeki bir projede **C5** `Sheet1` hücresine nasıl <xref:Microsoft.Office.Tools.Excel.Controls.Button> ekleneceğini gösterir.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="runtimeaddin"></a>VSTO eklentilerinde çalışma zamanında denetim ekleme
 Çalışma zamanında herhangi bir açık belgeye program aracılığıyla Windows Forms denetimleri ekleyebilirsiniz. İlk olarak, açık bir belgeyi veya çalışma sayfasını temel alan bir konak öğesi oluşturun. Ardından, Word 'de yeni konak öğesinin <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> özelliğinin yöntemlerini kullanın. Excel 'de yeni ana bilgisayar öğesinin <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> özelliğinin yöntemlerini kullanın. Her yöntemde, denetimin konumunu farklı şekillerde belirtmenize imkan tanıyan birkaç aşırı yükleme vardır.

 Çalışma zamanında bir belgeye Windows Forms denetimi eklediğinizde, belge kapatıldığında denetim belgede kalıcı olmaz. Belgeyi bir dahaki sefer açıldığında denetimi yeniden oluşturabilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

 VSTO eklenti projelerinde konak öğeleri oluşturma hakkında daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Çalışma zamanında bir Windows Forms denetimi eklemek için

1. Add\<*Control Class*adlı bir yöntemi kullanın > ( *denetim sınıfı* , <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>gibi eklemek istediğiniz Windows Forms denetiminin sınıf adıdır).

    > [!NOTE]
    > [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya üstünü hedefleyen VSTO eklenti projelerinde, Add @no__ erişebilmek için önce *Microsoft. Office. Tools. Excel. v 4.0. Utilities. dll* veya *Microsoft. Office. Tools. Word. v 4.0. Utilities. dll* derlemesine bir başvuru eklemeniz gerekir t_3_ *Denetim sınıfı*> yöntemleri.

     Aşağıdaki kod örneği, bir Word VSTO eklentisi kullanarak etkin belgenin ilk paragrafına bir <xref:Microsoft.Office.Tools.Word.Controls.Button> nasıl ekleneceğini gösterir.

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>Ayrıca bkz.
- [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl yapılır: çalışma sayfası hücreleri içinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
