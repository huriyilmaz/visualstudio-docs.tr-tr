---
title: Çalışma zamanında Office belgelerine denetim ekleme
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- host controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- user controls [Office development in Visual Studio], adding at run time
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], adding at run time
- helper methods [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 44bf1de5d550a264a63ba7293fe1bdc0c9630aee
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986329"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Çalışma zamanında Office belgelerine denetim ekleme
  Çalışma zamanında bir Microsoft Office Word belgesine ve Microsoft Office Excel çalışma kitabına denetimler ekleyebilirsiniz. Onları çalışma zamanında da kaldırabilirsiniz. Çalışma zamanında eklediğiniz veya kaldırdığınız denetimlere *Dinamik denetimler*denir.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Bu konuda aşağıdakiler açıklanmaktadır:

- [Denetimleri denetim koleksiyonları kullanarak çalışma zamanında yönetin](#ControlsCollection).

- [Belgelere konak denetimleri ekleyin](#HostControls).

- [Belgelere Windows Forms denetimleri ekleyin](#WindowsForms).

## <a name="ControlsCollection"></a>Denetim koleksiyonlarını kullanarak çalışma zamanında denetimleri yönetme
 Çalışma zamanında denetimleri eklemek, almak veya kaldırmak için <xref:Microsoft.Office.Tools.Excel.ControlCollection> ve <xref:Microsoft.Office.Tools.Word.ControlCollection> nesneleri için yardımcı yöntemleri kullanın.

 Bu nesnelere erişme şekli, geliştirmekte olduğunuz projenin türüne bağlıdır:

- Excel için belge düzeyi projesinde, `Sheet1`, `Sheet2`ve `Sheet3` sınıflarının <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> özelliğini kullanın. Bu sınıflar hakkında daha fazla bilgi için bkz. [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

- Word için belge düzeyi projesinde, `ThisDocument` sınıfının <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> özelliğini kullanın. Bu sınıf hakkında daha fazla bilgi için bkz. [belge konak öğesi](../vsto/document-host-item.md).

- Excel veya Word için VSTO eklentisi projesinde, çalışma zamanında oluşturduğunuz bir <xref:Microsoft.Office.Tools.Excel.Worksheet> veya <xref:Microsoft.Office.Tools.Word.Document> `Controls` özelliğini kullanın. Çalışma zamanında bu nesneleri oluşturma hakkında daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="add-controls"></a>Denetim Ekle
 <xref:Microsoft.Office.Tools.Excel.ControlCollection> ve <xref:Microsoft.Office.Tools.Word.ControlCollection> türleri, belgelere ve çalışma sayfalarına konak denetimleri ve ortak Windows Forms denetimleri eklemek için kullanabileceğiniz yardımcı yöntemleri içerir. Her yöntem adı `Add`*Control sınıfına*sahiptir; burada *Denetim sınıfı* , eklemek istediğiniz denetimin sınıf adıdır. Örneğin, belgenize <xref:Microsoft.Office.Tools.Excel.NamedRange> bir denetim eklemek için <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> yöntemini kullanın.

 Aşağıdaki kod örneği, Excel için belge düzeyindeki bir projede `Sheet1` bir <xref:Microsoft.Office.Tools.Excel.NamedRange> ekler.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]

### <a name="access-and-delete-controls"></a>Erişim ve silme denetimleri
 Tasarım zamanında eklediğiniz denetimler de dahil olmak üzere, belgenizdeki tüm denetimleri yinelemek için bir <xref:Microsoft.Office.Tools.Excel.Worksheet> veya <xref:Microsoft.Office.Tools.Word.Document> `Controls` özelliğini kullanabilirsiniz. Tasarım zamanında eklediğiniz denetimlere de *Statik denetimler*denir.

 Denetimin `Delete` yöntemini çağırarak veya her bir denetim koleksiyonunun `Remove` yöntemini çağırarak dinamik denetimleri kaldırabilirsiniz. Aşağıdaki kod örneği, Excel için belge düzeyindeki bir projede `Sheet1` bir <xref:Microsoft.Office.Tools.Excel.NamedRange> kaldırmak için <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> yöntemini kullanır.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]

 Çalışma zamanında statik denetimleri kaldıramazsınız. Statik bir denetimi kaldırmak için `Delete` veya `Remove` yöntemini kullanmayı denerseniz, bir <xref:Microsoft.Office.Tools.CannotRemoveControlException> oluşturulur.

> [!NOTE]
> Belgenin `Shutdown` olay işleyicisindeki denetimleri program aracılığıyla kaldırmayın. `Shutdown` olayı ortaya çıktığında belgenin UI öğeleri artık kullanılamaz. Belge kapanmadan önce denetimleri kaldırmak istiyorsanız, <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> veya Word için <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> veya <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose>ya da Excel için <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> gibi başka bir olay için kodunuzu olay işleyicisine ekleyin.

## <a name="HostControls"></a>Belgelere konak denetimleri ekleme

Belgelere program aracılığıyla ana bilgisayar denetimleri eklediğinizde, denetimi benzersiz bir şekilde tanımlayan bir ad sağlamalısınız ve denetimin belgede nereye ekleneceğini belirtmeniz gerekir. Belirli yönergeler için aşağıdaki konulara bakın:

- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Nasıl yapılır: Word belgelerine Içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Nasıl yapılır: Word belgelerine yer Işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Konak denetimleri hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

Bir belge kaydedilip kapatıldığında, dinamik olarak oluşturulan tüm konak denetimlerinin olaylarıyla bağlantısı kesilir ve veri bağlama işlevlerini kaybeder. Belge yeniden açıldığında konak denetimlerini yeniden oluşturmak için çözümünüze kod ekleyebilirsiniz. Daha fazla bilgi için bkz. [Dinamik denetimleri Office belgelerinde kalıcı hale](../vsto/persisting-dynamic-controls-in-office-documents.md)getirme.

> [!NOTE]
> Şu denetimler belgelere program aracılığıyla eklenemediği için, aşağıdaki konak denetimleri için yardımcı yöntemler sağlanmaz: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode>ve <xref:Microsoft.Office.Tools.Word.XMLNodes>.

## <a name="WindowsForms"></a>Belgelere Windows Forms denetimleri ekleme
 Bir belgeye program aracılığıyla bir Windows Forms denetimi eklediğinizde, denetimin konumunu ve denetimi benzersiz bir şekilde tanımlayan bir adı sağlamanız gerekir. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] her denetim için yardımcı yöntemler sağlar. Bu yöntemler, denetimin konumu için bir Aralık veya belirli koordinatları geçirebilmeniz için aşırı yüklenmiştir.

 Bir belge kaydedilip kapatıldığında, dinamik olarak oluşturulan Windows Forms denetimleri belgeden kaldırılır. Belge yeniden açıldığında denetimleri yeniden oluşturmak için çözümünüze kod ekleyebilirsiniz. VSTO eklentisini kullanarak dinamik Windows Forms denetimleri oluşturursanız, denetimlerin ActiveX sarmalayıcıları belgede bırakılır. Daha fazla bilgi için bkz. [Dinamik denetimleri Office belgelerinde kalıcı hale](../vsto/persisting-dynamic-controls-in-office-documents.md)getirme.

> [!NOTE]
> Windows Forms denetimleri, korumalı belgelere program aracılığıyla eklenemez. Bir Word belgesi veya Excel çalışma sayfasını program aracılığıyla bir denetim eklemek üzere kaldırırsanız, belge kapatıldığında denetimin ActiveX sarmalayıcısı kaldırmak için ek kod yazmalısınız. Denetimin ActiveX sarmalayıcısı, korumalı belgelerden otomatik olarak silinmez.

### <a name="add-custom-controls"></a>Özel denetim ekleme
 Özel Kullanıcı denetimi gibi kullanılabilir yardımcı yöntemler tarafından desteklenmeyen bir <xref:System.Windows.Forms.Control> eklemek istiyorsanız aşağıdaki yöntemleri kullanın:

- Excel için, bir <xref:Microsoft.Office.Tools.Excel.ControlCollection> nesnesinin <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> yöntemlerinden birini kullanın.

- Word için, bir <xref:Microsoft.Office.Tools.Word.ControlCollection> nesnesinin <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> yöntemlerinden birini kullanın.

  Denetimi eklemek için <xref:System.Windows.Forms.Control>, denetim için bir konum ve denetimi benzersiz bir şekilde tanımlayan bir ad `AddControl` yöntemine geçirin. `AddControl` yöntemi, denetimin çalışma sayfası veya belgeyle nasıl etkileşime gireceğini tanımlayan bir nesne döndürür. `AddControl` yöntemi bir <xref:Microsoft.Office.Tools.Excel.ControlSite> (Excel için) veya <xref:Microsoft.Office.Tools.Word.ControlSite> nesnesi (Word için) döndürür.

  Aşağıdaki kod örneği, belge düzeyindeki bir Excel projesindeki çalışma sayfasına dinamik olarak özel kullanıcı denetimi eklemek için <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> yönteminin nasıl kullanılacağını gösterir. Bu örnekte, Kullanıcı denetimi `UserControl1`olarak adlandırılır ve <xref:Microsoft.Office.Interop.Excel.Range> `range1`olarak adlandırılır. Bu örneği kullanmak için, bunu projedeki bir `Sheet`*n* sınıfından çalıştırın.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]

### <a name="use-members-of-custom-controls"></a>Özel denetimlerin üyelerini kullanma
 Bir çalışma sayfasına veya belgeye denetim eklemek için `AddControl` yöntemlerinden birini kullandıktan sonra, artık iki farklı denetim nesneniz vardır:

- Özel denetimi temsil eden <xref:System.Windows.Forms.Control>.

- Çalışma sayfasına veya belgeye eklendikten sonra denetimi temsil eden `ControlSite`, `OLEObject`veya `OLEControl` nesnesi.

  Birçok özellik ve yöntem bu denetimler arasında paylaşılır. Bu üyelere uygun denetim aracılığıyla erişmeniz önemlidir:

- Yalnızca özel denetime ait üyelere erişmek için <xref:System.Windows.Forms.Control>kullanın.

- Denetimler tarafından paylaşılan üyelere erişmek için `ControlSite`, `OLEObject`veya `OLEControl` nesnesini kullanın.

  <xref:System.Windows.Forms.Control>paylaşılan bir üyeye eriştiğinizde, uyarı veya bildirim olmadan başarısız olabilir ya da geçersiz sonuçlar üretebilir. Gerekli Yöntem veya özellik kullanılamadığından, her zaman `ControlSite`, `OLEObject`veya `OLEControl` nesnesinin yöntemlerini veya özelliklerini kullanın; yalnızca <xref:System.Windows.Forms.Control>başvurmanız gerekir.

  Örneğin, hem <xref:Microsoft.Office.Tools.Excel.ControlSite> sınıfı hem de <xref:System.Windows.Forms.Control> sınıfı bir `Top` özelliğine sahiptir. Denetimin üst ve belgenin üst arasındaki mesafeyi almak veya ayarlamak için, <xref:System.Windows.Forms.Control><xref:System.Windows.Forms.Control.Top%2A> özelliğini değil <xref:Microsoft.Office.Tools.Excel.ControlSite><xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> özelliğini kullanın.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#3)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.
- [Office belgelerindeki denetimler](../vsto/controls-on-office-documents.md)
- [Office belgelerinde dinamik denetimleri kalıcı hale getirme](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Nasıl yapılır: Word belgelerine yer Işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Office belgelerindeki Windows Forms denetimlerine genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
