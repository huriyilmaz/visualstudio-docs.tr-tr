---
title: Çalışma zamanında Office denetimler ekleme
description: Microsoft Office Word belgesine denetimler Microsoft Office Excel çalışma zamanında nasıl ekleyebilirsiniz?
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2b6f8fdd05bde0714abc90f8c18e6217708deb6313871e41e8600acecf40af10
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440909"
---
# <a name="add-controls-to-office-documents-at-run-time"></a>Çalışma zamanında Office denetimler ekleme
  Çalışma zamanında bir Word belgesine Microsoft Office ve Microsoft Office Excel çalışma kitabına denetimler ekleyebilirsiniz. Bunları çalışma zamanında da kaldırabilirsiniz. Çalışma zamanında eklemeniz veya kaldırmanız için dinamik *denetimler adı verilen denetimler.*

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 Bu konuda aşağıdakiler açıklanmıştır:

- [Denetim koleksiyonlarını kullanarak çalışma zamanında denetimleri yönetin.](#ControlsCollection)

- [Belgelere konak denetimleri ekleyin.](#HostControls)

- [Belgelere Windows Form denetimleri ekleyin.](#WindowsForms)

## <a name="manage-controls-at-run-time-by-using-control-collections"></a><a name="ControlsCollection"></a> Denetim koleksiyonlarını kullanarak çalışma zamanında denetimleri yönetme
 Çalışma zamanında denetim eklemek, almak veya kaldırmak için ve nesnelerinin yardımcı <xref:Microsoft.Office.Tools.Excel.ControlCollection> yöntemlerini <xref:Microsoft.Office.Tools.Word.ControlCollection> kullanın.

 Bu nesnelere erişme yolunuz, geliştirmekte olduğunu projenin türüne bağlıdır:

- Bir belge düzeyi projesinde Excel , <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> ve sınıflarının `Sheet1` özelliğini `Sheet2` `Sheet3` kullanın. Bu sınıflar hakkında daha fazla bilgi için bkz. [Çalışma sayfası konak öğesi.](../vsto/worksheet-host-item.md)

- Word için belge düzeyi projesinde sınıfının <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> özelliğini `ThisDocument` kullanın. Bu sınıf hakkında daha fazla bilgi için [bkz. Belge konak öğesi.](../vsto/document-host-item.md)

- VSTO word için bir eklenti Excel çalışma zamanında bir veya `Controls` özelliğini <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> kullanın. Bu nesneleri çalışma zamanında oluşturma hakkında daha fazla bilgi için bkz. Çalışma zamanında Word Excel ve VSTO çalışma [kitaplarını genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

### <a name="add-controls"></a>Denetim ekleme
 ve türleri, belgelere ve çalışma sayfalarına konak denetimleri ve yaygın Windows Formlar denetimleri eklemek için <xref:Microsoft.Office.Tools.Excel.ControlCollection> <xref:Microsoft.Office.Tools.Word.ControlCollection> kullanabileceğiniz yardımcı yöntemleri içerir. Her yöntem adı biçim `Add` *denetim sınıfına* *sahip, burada* denetim sınıfı eklemek istediğiniz denetimin sınıf adıdır. Örneğin, belgenize <xref:Microsoft.Office.Tools.Excel.NamedRange> denetim eklemek için yöntemini <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A> kullanın.

 Aşağıdaki kod örneği, bir belge düzeyi projesinde için bir <xref:Microsoft.Office.Tools.Excel.NamedRange> `Sheet1` ekler Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#3)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#3)]
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb" id="Snippet3":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs" id="Snippet3":::


### <a name="access-and-delete-controls"></a>Erişim ve silme denetimleri
 Tasarım zamanında eklenen denetimler de dahil olmak üzere belgenizin tüm denetimlerini yeniden kullanmak için veya `Controls` <xref:Microsoft.Office.Tools.Excel.Worksheet> özelliğini <xref:Microsoft.Office.Tools.Word.Document> kullanabilirsiniz. Tasarım zamanında ekley istediğiniz denetimler statik *denetimler olarak da adlandırılan denetimlerdir.*

 Denetimin yöntemini çağırarak veya her denetim koleksiyonunun yöntemini `Delete` `Remove` çağırarak dinamik denetimleri kaldırabilirsiniz. Aşağıdaki kod örneği, bir belge düzeyi projesinde bir 'den kaldırmak için <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> <xref:Microsoft.Office.Tools.Excel.NamedRange> yöntemini `Sheet1` Excel.

 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb#4)]
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs#4)]
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/ThisWorkbook.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/ThisWorkbook.cs" id="Snippet4":::


 Çalışma zamanında statik denetimleri kaldıramazsiniz. Statik bir denetimi kaldırmak `Delete` için veya yöntemini kullanmayı `Remove` <xref:Microsoft.Office.Tools.CannotRemoveControlException> denersanız, bir olur.

> [!NOTE]
> Belgenin olay işleyicisinde program aracılığıyla `Shutdown` denetimleri kaldırabilirsiniz. Olay ortaya çıkarken belgenin kullanıcı arabirimi öğeleri `Shutdown` artık kullanılamaz. Belge kapanmadan önce denetimleri kaldırmak için kodunuzu Word veya veya için ya da gibi başka bir olay için olay işleyicisine ekleyin veya <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose> <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> Excel.

## <a name="add-host-controls-to-documents"></a><a name="HostControls"></a> Belgelere konak denetimleri ekleme

Belgelere program aracılığıyla konak denetimleri eklerken, denetimi benzersiz olarak tanımlayan bir ad sağlamalı ve belgeye denetimin ek nereye ek gerektiğini belirtmeniz gerekir. Belirli yönergeler için aşağıdaki konulara bakın:

- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)

- [Nasıl kullanılır: Word belgelerine İçerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Nasıl kullanılır: Word belgelerine Yer İşareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

Konak denetimleri hakkında daha fazla bilgi için bkz. [Konak öğeleri ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

Bir belge kaydedildiğinde ve kapatıldığında, dinamik olarak oluşturulan tüm konak denetimlerinin olaylarının bağlantısı kesilir ve veri bağlama işlevlerini kaybederler. Belge yeniden açılırken konak denetimlerini yeniden oluşturmak için çözümünüze kod ekleyebilirsiniz. Daha fazla bilgi için [bkz. Dinamik denetimleri belgelerde Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

> [!NOTE]
> Yardımcı yöntemler aşağıdaki konak denetimleri için sağlanmaz çünkü bu denetimler belgelere program aracılığıyla ek olamaz: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> , <xref:Microsoft.Office.Tools.Word.XMLNode> ve <xref:Microsoft.Office.Tools.Word.XMLNodes> .

## <a name="add-windows-forms-controls-to-documents"></a><a name="WindowsForms"></a>Belgelere Windows Form denetimleri ekleme
 Bir belgeye program aracılığıyla Windows Forms denetimi eklerken, denetimin konumunu ve denetimi benzersiz olarak tanımlayan bir ad sağlanız gerekir. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] her denetim için yardımcı yöntemler sağlar. Bu yöntemler aşırı yüklenmiştir, böylece denetimin konumu için bir aralık veya belirli koordinatlar geçebilirsiniz.

 Bir belge kaydedilebilir ve kapatıldığında, tüm dinamik olarak Windows Forms denetimleri belgeden kaldırılır. Belge yeniden açılırken denetimleri yeniden oluşturmak için çözümünüze kod ekleyebilirsiniz. VSTO Eklenti kullanarak dinamik Windows Forms denetimleri oluşturursanız, ActiveX sarmalayıcıları belgede sol taraftadır. Daha fazla bilgi için [bkz. Dinamik denetimleri belgelerde Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

> [!NOTE]
> Windows Form denetimleri, korumalı belgelere program aracılığıyla ek olamaz. Program aracılığıyla bir Word belgesinin korumasını kaldırırsanız veya denetim eklemek için Excel çalışma sayfasını kaldırırsanız, belge kapatılan denetimin ActiveX sarmalayıcısını kaldırmak için ek kod yazmanız gerekir. Denetimin ActiveX sarmalayıcı korumalı belgelerden otomatik olarak silinmez.

### <a name="add-custom-controls"></a>Özel denetim ekleme
 Özel kullanıcı denetimi gibi kullanılabilir yardımcı yöntemler tarafından desteklenen bir eklemek için <xref:System.Windows.Forms.Control> aşağıdaki yöntemleri kullanın:

- Daha Excel için bir nesnenin <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> yöntemlerinden birini <xref:Microsoft.Office.Tools.Excel.ControlCollection> kullanın.

- Word için bir nesnenin <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> yöntemlerinden birini <xref:Microsoft.Office.Tools.Word.ControlCollection> kullanın.

  Denetimi eklemek için , denetimin bir konumunu ve yöntemine denetimi <xref:System.Windows.Forms.Control> benzersiz olarak tanımlayan bir ad `AddControl` girin. yöntemi, `AddControl` denetimin çalışma sayfası veya belgeyle nasıl etkileşim kura olduğunu tanımlayan bir nesnesi döndürür. yöntemi `AddControl` bir <xref:Microsoft.Office.Tools.Excel.ControlSite> (Excel) veya bir <xref:Microsoft.Office.Tools.Word.ControlSite> nesnesi (Word için) döndürür.

  Aşağıdaki kod örneği, belge düzeyinde bir çalışma sayfasındaki çalışma sayfasına dinamik olarak özel kullanıcı denetimi eklemek için yönteminin <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> nasıl Excel gösterir. Bu örnekte, kullanıcı denetimi olarak ve `UserControl1` olarak <xref:Microsoft.Office.Interop.Excel.Range> `range1` adlandırılmıştır. Bu örneği kullanmak için projesinde `Sheet` *n* sınıfından çalıştırın.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet2":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet2":::

### <a name="use-members-of-custom-controls"></a>Özel denetimlerin üyelerini kullanma
 Çalışma sayfasına veya belgeye denetim eklemek için yöntemlerden birini kullandıktan `AddControl` sonra artık iki farklı denetim nesnesine sahipsiniz:

- Özel <xref:System.Windows.Forms.Control> denetimi temsil eden .

- Çalışma `ControlSite` `OLEObject` sayfasına veya `OLEControl` belgeye eklendikten sonra denetimi temsil eden , veya nesnesi.

  Bu denetimler arasında birçok özellik ve yöntem paylaşılır. Bu üyelere uygun denetim aracılığıyla erişmeniz önemlidir:

- Yalnızca özel denetime ait üyelere erişmek için <xref:System.Windows.Forms.Control> kullanın.

- Denetimler tarafından paylaşılan üyelere erişmek için `ControlSite` , veya `OLEObject` nesnesini `OLEControl` kullanın.

  paylaşılan bir üyeye 'den erişerseniz, uyarı veya bildirim olmadan başarısız olabilir <xref:System.Windows.Forms.Control> veya geçersiz sonuçlar üretebilir. Gereken yöntem veya özellik kullanılabilir değilse, her zaman , veya nesnesinin yöntemlerini veya özelliklerini kullanın; yalnızca o `ControlSite` `OLEObject` zaman ' a `OLEControl` <xref:System.Windows.Forms.Control> başvurabilirsiniz.

  Örneğin, hem sınıfının <xref:Microsoft.Office.Tools.Excel.ControlSite> hem de sınıfının bir özelliği <xref:System.Windows.Forms.Control> `Top` vardır. Denetimin üst ve belgenin üst değeri arasındaki mesafeyi almak veya ayarlamak için özelliğini değil <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> <xref:Microsoft.Office.Tools.Excel.ControlSite> , özelliğini <xref:System.Windows.Forms.Control.Top%2A> <xref:System.Windows.Forms.Control> kullanın.

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet3":::
  :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet3":::

## <a name="see-also"></a>Ayrıca bkz.
- [Belgelerde Office denetimler](../vsto/controls-on-office-documents.md)
- [Belgelerde dinamik Office kalıcılığı](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına Grafik denetimleri ekleme](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Nasıl kullanılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Nasıl kullanılır: Word belgelerine Yer İşareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Windows Belgelerde form Office genel bakış](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Nasıl Windows: Windows Form denetimleri ekleme Office ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
