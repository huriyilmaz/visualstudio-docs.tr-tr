---
title: 'Nasıl kullanılır: Windows form denetimleri Office ekleme'
description: Belge düzeyindeki projelerde word Windows tasarım zamanında Microsoft Office Excel ve Microsoft Office Form denetimleri ekleme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 11d5efde772a85681f21fc8b08586f014d96978d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026284"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Nasıl kullanılır: Windows Formlar denetimleri Office ekleme
  Belge düzeyi projelerinde Windows word Microsoft Office Excel Microsoft Office belgelerine form denetimleri ekleyebilirsiniz. Çalışma zamanında, belge düzeyi özelleştirmelerde ve diğer eklentilerde VSTO ekleyebilirsiniz. Örneğin, kullanıcıların seçenekler <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> listesinden seçim yapmak için çalışma sayfanıza bir denetim ekleyebilirsiniz.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Bu konuda aşağıdaki görevler açıklanmıştır:

- [Tasarım zamanında denetim ekleme](#designtime)

- [Belge düzeyindeki projelerde çalışma zamanında denetimler ekleme](#runtimedoclevel)

- [Eklentilerde çalışma zamanında VSTO ekleme](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> Tasarım zamanında denetim ekleme
 Tasarım zamanında belge düzeyi Windows form denetimleri eklemenin çeşitli yolları vardır.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Formlar Windows belgeye sürüklemek için

1. Belgenin tasarımcıda görünür Excel için Visual Studio çalışma kitabı projesini veya Word Belgesi projesini oluşturun veya açın. Proje oluşturma hakkında daha fazla bilgi için [bkz. Nasıl Office: Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

2. Araç **Kutusunun Ortak** **Denetimler sekmesinde,** eklemek istediğiniz denetime tıklayın ve belgeye sürükleyin.

    > [!NOTE]
    > Denetim çubuğundan bir denetim Excel Formül Çubuğunda **=EMBED("WinForms.Control.Host","")** **ifadesinin yer alır.** Bu metin gereklidir ve silinmemelidir.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Belge üzerinde Windows Forms denetimi çizmek için

1. Belgenin tasarımcıda görünür Excel için Visual Studio çalışma kitabı projesini veya Word Belgesi projesini oluşturun veya açın. Proje oluşturma hakkında daha fazla bilgi için [bkz. Nasıl Office: Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

2. Araç **Kutusunun Ortak** **Denetimler sekmesinde,** eklemek istediğiniz denetime tıklayın.

3. Belgede, denetimin sol üst köşesinin yer almak istediğiniz yere tıklayın ve denetimin sağ alt köşesinin yer almak istediğiniz yere sürükleyin.

     Denetim, belirtilen konum ve boyuta sahip belgeye eklenir.

    > [!NOTE]
    > Denetim çubuğundan bir denetim Excel Formül Çubuğunda **=EMBED("WinForms.Control.Host","")** **ifadesinin yer alır.** Bu metin gereklidir ve silinmemelidir.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Denetime tek Windows Formlar denetimi eklemek için

1. Belgenin tasarımcıda görünür Excel için Visual Studio çalışma kitabı projesini veya Word Belgesi projesini oluşturun veya açın. Proje oluşturma hakkında daha fazla bilgi için [bkz. Nasıl Office: Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

2. Araç **Kutusunun Ortak** **Denetimler sekmesinde,** eklemek istediğiniz denetime tıklayın

3. Belgelerden biri, denetimin eklenmek istediğiniz yere tıklayın.

     Denetim, belgeye varsayılan boyutla eklenir.

    > [!NOTE]
    > Denetim çubuğundan bir denetim Excel Formül Çubuğunda **=EMBED("WinForms.Control.Host","")** **ifadesinin yer alır.** Bu metin gereklidir ve silinmemelidir.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Denetime çift Windows Formlar denetimi eklemek için

1. Belgenin tasarımcıda görünür Excel için Visual Studio çalışma kitabı projesini veya Word Belgesi projesini oluşturun veya açın. Proje oluşturma hakkında daha fazla bilgi için [bkz. Nasıl Office: Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

2. Araç **Kutusunun Ortak** **Denetimler sekmesinde,** eklemek istediğiniz denetime çift tıklayın.

     Denetim, belgenin merkezine veya etkin bölmeye eklenir.

    > [!NOTE]
    > Denetim çubuğundan bir denetim Excel Formül Çubuğunda **=EMBED("WinForms.Control.Host","")** **ifadesinin yer alır.** Bu metin gereklidir ve silinmemelidir.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Enter tuşuna Windows form denetimi eklemek için

1. Belgenin tasarımcıda görünür Excel için Visual Studio çalışma kitabı projesini veya Word Belgesi projesini oluşturun veya açın. Proje oluşturma hakkında bilgi için, [bkz. How to: Create Office Projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

2. Araç **Kutusunun Ortak** Denetimler **sekmesinde,** eklemek istediğiniz denetime tıklayın ve **Enter tuşuna** basın.

     Denetim, belgenin merkezine veya etkin bölmeye eklenir.

    > [!NOTE]
    > Denetim çubuğundan bir denetim Excel Formül Çubuğunda **=EMBED("WinForms.Control.Host","")** **ifadesinin yer alır.** Bu metin gereklidir ve silinmemelidir.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> Belge düzeyindeki projelerde çalışma zamanında denetimler ekleme
 Çalışma zamanında bir belgeye program Windows Form denetimleri ekleyebilirsiniz. Word'de sınıfının <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> özelliğinin yöntemlerini `ThisDocument` kullanın. Bu Excel n sınıfının <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> özelliğinin `Sheet` *yöntemlerini* kullanın. Her yöntemin, denetimin konumunu farklı yollarla belirtmenize olanak sağlayan birkaç aşırı yüklemesi vardır.

 Çalışma zamanında Windows Formlar denetimi eklerken, belge kapatılan denetim belgede kalıcı olmaz. Belge bir sonraki açıldığında denetimi yeniden oluşturabilirsiniz. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Çalışma zamanında Windows Formlar denetimi eklemek için

1. Add adına sahip bir yöntem kullanın (burada denetim sınıfı, eklemek istediğiniz Windows Forms denetimi sınıf \<*control class*> adıdır,  <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> örneğin).

     Aşağıdaki kod örneğinde, C5 hücresine belge düzeyi projesinde <xref:Microsoft.Office.Tools.Excel.Controls.Button> **C5** hücresine bir ekleme adımları `Sheet1` Excel.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet4":::

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a>Eklentilerde çalışma zamanında VSTO ekleme
 Formlar denetimlerini Windows açık herhangi bir belgeye çalışma zamanında program aracılığıyla ekleyebilirsiniz. İlk olarak, açık bir belgeyi veya çalışma sayfasını temel alan bir konak öğesi oluşturun. Ardından Word'de yeni konak <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> öğesinin özelliğinin yöntemlerini kullanın. Bu Excel, yeni konak <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> öğesinin özelliğinin yöntemlerini kullanın. Her yöntemin, denetimin konumunu farklı yollarla belirtmenize olanak sağlayan birkaç aşırı yüklemesi vardır.

 Çalışma zamanında Windows Formlar denetimi eklerken, belge kapatılan denetim belgede kalıcı olmaz. Belge bir sonraki açıldığında denetimi yeniden oluşturabilirsiniz. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 Eklenti projelerinde konak öğeleri VSTO daha fazla bilgi için bkz. Çalışma zamanında VSTO Eklentilerinde Word belgelerini ve Excel çalışma [kitaplarını genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Çalışma zamanında Windows Formlar denetimi eklemek için

1. Add adına sahip bir yöntem kullanın (burada denetim sınıfı, eklemek istediğiniz Windows Forms denetimi sınıf \<*control class*> adıdır,  <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> örneğin).

    > [!NOTE]
    > Veya VSTO'yi hedef alan eklenti projelerinde, Add methods'a erişmeden önceMicrosoft.Office.Tools.Excel.v4.0.Utilities.dllveyaMicrosoft.Office.Tools.Word.v4.0.Utilities.dllderlemeye bir başvuru [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] eklemeniz   \<*control class*> gerekir.

     Aşağıdaki kod örneği, Word VSTO Eklentisini kullanarak etkin belgenin ilk <xref:Microsoft.Office.Tools.Word.Controls.Button> paragrafı için bir eklemeyi gösterir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet7":::

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Belgelerde form Office genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Nasıl olur: Çalışma sayfası hücrelerinde denetimleri yeniden boyutlandırma](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
