---
title: Çalışma zamanında Office belgelerine denetim ekleme
description: Çalışma zamanında bir Microsoft Office Word belgesine ve Microsoft Office Excel çalışma kitabına nasıl denetim ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e971556605a120b4ef475f434390c6dcf7b17938
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844848"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Çalışma zamanında Office belgelerine denetim ekleme
  Çalışma zamanında bir Microsoft Office Word belgesine ve Microsoft Office Excel çalışma kitabına denetimler ekleyebilirsiniz. Onları çalışma zamanında da kaldırabilirsiniz. Çalışma zamanında eklediğiniz veya kaldırdığınız denetimlere *Dinamik denetimler* denir.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Bu konuda aşağıdakiler açıklanmaktadır:

- [Denetimleri denetim koleksiyonları kullanarak çalışma zamanında yönetin](#ControlsCollection).

- [Belgelere konak denetimleri ekleyin](#HostControls).

- [Belgelere Windows Forms denetimleri ekleyin](#WindowsForms).

## <a name="manage-controls-at-run-time-by-using-control-collections"></a><a name="ControlsCollection"></a> Denetim koleksiyonlarını kullanarak çalışma zamanında denetimleri yönetme
 Çalışma zamanında denetimleri eklemek, almak veya kaldırmak için, ve nesnelerinin yardımcı yöntemlerini kullanın <xref:Microsoft.Office.Tools.Excel.ControlCollection> <xref:Microsoft.Office.Tools.Word.ControlCollection> .

 Bu nesnelere erişme şekli, geliştirmekte olduğunuz projenin türüne bağlıdır:

- Excel için belge düzeyi projesinde <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> `Sheet1` ,, `Sheet2` ve sınıflarının özelliğini kullanın `Sheet3` . Bu sınıflar hakkında daha fazla bilgi için bkz. [çalışma sayfası konak öğesi](../vsto/worksheet-host-item.md).

- Word için belge düzeyi projesinde, <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> sınıfının özelliğini kullanın `ThisDocument` . Bu sınıf hakkında daha fazla bilgi için bkz. [belge konak öğesi](../vsto/document-host-item.md).

- Excel veya Word için VSTO eklentisi projesinde, `Controls` çalışma zamanında oluşturduğunuz bir veya öğesinin özelliğini kullanın <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> . Çalışma zamanında bu nesneleri oluşturma hakkında daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="add-controls"></a>Denetim Ekle
 <xref:Microsoft.Office.Tools.Excel.ControlCollection>Ve <xref:Microsoft.Office.Tools.Word.ControlCollection> türleri, belgelere ve çalışma sayfalarına konak denetimleri ve ortak Windows Forms denetimleri eklemek için kullanabileceğiniz yardımcı yöntemleri içerir. Her yöntem adı, denetim sınıfının, `Add` eklemek istediğiniz denetimin *control class* sınıf adı olduğu biçim *denetim sınıfına* sahiptir. Örneğin, belgenize bir denetim eklemek için <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> yöntemini kullanın.

 Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Excel.NamedRange> `Sheet1` Excel için belge düzeyi projesine öğesine ekler.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]

### <a name="access-and-delete-controls"></a>Erişim ve silme denetimleri
 `Controls` <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> Tasarım zamanında eklediğiniz denetimler de dahil olmak üzere, belgenizdeki tüm denetimleri yinelemek için veya özelliğini kullanabilirsiniz. Tasarım zamanında eklediğiniz denetimlere de *Statik denetimler* denir.

 `Delete`Denetimin yöntemini çağırarak veya `Remove` her bir denetim koleksiyonunun yöntemini çağırarak dinamik denetimleri kaldırabilirsiniz. Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> `Sheet1` Excel için belge düzeyindeki bir projede öğesinden kaldırmak için yöntemini kullanır.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]

 Çalışma zamanında statik denetimleri kaldıramazsınız. `Delete` `Remove` Statik bir denetimi kaldırmak için veya yöntemini kullanmayı denerseniz, bir <xref:Microsoft.Office.Tools.CannotRemoveControlException> oluşturulur.

> [!NOTE]
> `Shutdown`Belgenin olay işleyicisindeki denetimleri program aracılığıyla kaldırmayın. Olay ortaya çıktığında, belgenin Kullanıcı arabirimi öğeleri artık kullanılamaz `Shutdown` . Belge kapanmadan önce denetimleri kaldırmak istiyorsanız, kodunuzu, veya Word gibi başka bir olay için olay işleyicisine ekleyin; örneğin, ya da <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose> <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> Excel için.

## <a name="add-host-controls-to-documents"></a><a name="HostControls"></a> Belgelere konak denetimleri ekleme

Belgelere program aracılığıyla ana bilgisayar denetimleri eklediğinizde, denetimi benzersiz bir şekilde tanımlayan bir ad sağlamalısınız ve denetimin belgede nereye ekleneceğini belirtmeniz gerekir. Belirli yönergeler için aşağıdaki konulara bakın:

- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Nasıl yapılır: çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Nasıl yapılır: Word belgelerine Içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Nasıl yapılır: Word belgelerine yer Işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Konak denetimleri hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

Bir belge kaydedilip kapatıldığında, dinamik olarak oluşturulan tüm konak denetimlerinin olaylarıyla bağlantısı kesilir ve veri bağlama işlevlerini kaybeder. Belge yeniden açıldığında konak denetimlerini yeniden oluşturmak için çözümünüze kod ekleyebilirsiniz. Daha fazla bilgi için bkz. [Dinamik denetimleri Office belgelerinde kalıcı hale](../vsto/persisting-dynamic-controls-in-office-documents.md)getirme.

> [!NOTE]
> Aşağıdaki konak denetimleri için yardımcı yöntemler sağlanmaz, çünkü bu denetimler belgelere program aracılığıyla eklenemez: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , <xref:Microsoft.Office.Tools.Word.XMLNode> , ve <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="add-windows-forms-controls-to-documents"></a><a name="WindowsForms"></a> Belgelere Windows Forms denetimleri ekleme
 Bir belgeye program aracılığıyla bir Windows Forms denetimi eklediğinizde, denetimin konumunu ve denetimi benzersiz bir şekilde tanımlayan bir adı sağlamanız gerekir. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Her denetim için yardımcı yöntemler sağlar. Bu yöntemler, denetimin konumu için bir Aralık veya belirli koordinatları geçirebilmeniz için aşırı yüklenmiştir.

 Bir belge kaydedilip kapatıldığında, dinamik olarak oluşturulan Windows Forms denetimleri belgeden kaldırılır. Belge yeniden açıldığında denetimleri yeniden oluşturmak için çözümünüze kod ekleyebilirsiniz. VSTO eklentisini kullanarak dinamik Windows Forms denetimleri oluşturursanız, denetimlerin ActiveX sarmalayıcıları belgede bırakılır. Daha fazla bilgi için bkz. [Dinamik denetimleri Office belgelerinde kalıcı hale](../vsto/persisting-dynamic-controls-in-office-documents.md)getirme.

> [!NOTE]
> Windows Forms denetimleri, korumalı belgelere program aracılığıyla eklenemez. Bir Word belgesi veya Excel çalışma sayfasını program aracılığıyla bir denetim eklemek üzere kaldırırsanız, belge kapatıldığında denetimin ActiveX sarmalayıcısı kaldırmak için ek kod yazmalısınız. Denetimin ActiveX sarmalayıcısı, korumalı belgelerden otomatik olarak silinmez.

### <a name="add-custom-controls"></a>Özel denetim ekleme
 <xref:System.Windows.Forms.Control>Özel Kullanıcı denetimi gibi kullanılabilir yardımcı yöntemler tarafından desteklenmeyen bir eklemek istiyorsanız, aşağıdaki yöntemleri kullanın:

- Excel için, <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> bir nesnenin yöntemlerinden birini kullanın <xref:Microsoft.Office.Tools.Excel.ControlCollection> .

- Word için, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> bir nesnenin yöntemlerinden birini kullanın <xref:Microsoft.Office.Tools.Word.ControlCollection> .

  Denetimi eklemek için, denetimi <xref:System.Windows.Forms.Control> için bir konum ve denetimi benzersiz bir şekilde tanımlayan bir ad olarak `AddControl` yöntemini geçirin. `AddControl`Yöntemi, denetimin çalışma sayfası veya belge ile nasıl etkileşime gireceğini tanımlayan bir nesne döndürür. `AddControl`Yöntemi bir <xref:Microsoft.Office.Tools.Excel.ControlSite> (Excel için) veya bir <xref:Microsoft.Office.Tools.Word.ControlSite> nesnesi (Word için) döndürür.

  Aşağıdaki kod örneği, bir <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> belge düzeyi Excel projesindeki çalışma sayfasına dinamik olarak özel kullanıcı denetimi eklemek için yönteminin nasıl kullanılacağını gösterir. Bu örnekte, Kullanıcı denetimi adı ve olarak adlandırılır `UserControl1` <xref:Microsoft.Office.Interop.Excel.Range> `range1` . Bu örneği kullanmak için, bunu `Sheet` projedeki *n* sınıfından çalıştırın.

  [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#2)]
  [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#2)]

### <a name="use-members-of-custom-controls"></a>Özel denetimlerin üyelerini kullanma
 `AddControl`Çalışma sayfasına veya belgeye denetim eklemek için yöntemlerden birini kullandıktan sonra, artık iki farklı denetim nesneniz vardır:

- <xref:System.Windows.Forms.Control>Özel denetimi temsil eder.

- `ControlSite` `OLEObject` `OLEControl` Çalışma sayfasına veya belgeye eklendikten sonra denetimi temsil eden, veya nesnesi.

  Birçok özellik ve yöntem bu denetimler arasında paylaşılır. Bu üyelere uygun denetim aracılığıyla erişmeniz önemlidir:

- Yalnızca özel denetime ait üyelere erişmek için öğesini kullanın <xref:System.Windows.Forms.Control> .

- Denetimler tarafından paylaşılan üyelere erişmek için, `ControlSite` `OLEObject` veya `OLEControl` nesnesini kullanın.

  İçinden paylaşılan bir üyeye eriştiğinizde, <xref:System.Windows.Forms.Control> uyarı veya bildirim olmadan başarısız olabilir ya da geçersiz sonuçlar üretebilir. `ControlSite`Gerekli Yöntem veya özellik kullanılamadığından her zaman,, veya nesnesinin yöntemlerini veya özelliklerini kullanın `OLEObject` `OLEControl` ; yalnızca öğesine başvurmanız gerekir <xref:System.Windows.Forms.Control> .

  Örneğin, hem <xref:Microsoft.Office.Tools.Excel.ControlSite> sınıf hem de <xref:System.Windows.Forms.Control> sınıfın bir `Top` özelliği vardır. Denetimin üst ve belgenin üst arasındaki mesafeyi almak veya ayarlamak için öğesinin özelliğini <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> değil öğesinin özelliğini kullanın <xref:Microsoft.Office.Tools.Excel.ControlSite> <xref:System.Windows.Forms.Control.Top%2A> <xref:System.Windows.Forms.Control> .

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
