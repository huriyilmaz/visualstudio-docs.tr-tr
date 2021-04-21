---
title: 'Nasıl yapılır: içerik denetimlerini kullanarak belge parçalarını koruma'
description: Visual Studio 'Yu, içerik denetimlerini kullanarak bir Microsoft Word belgesinin parçalarını korumak için nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc333871d4f371530db84a0c4f07ab891db2a937
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825478"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Nasıl yapılır: içerik denetimlerini kullanarak belge parçalarını koruma
  Belgenin bir bölümünü koruduğunuzda, kullanıcıların belgenin o bölümündeki içeriği değiştirmesini veya silmesini engelleyebilirsiniz. İçerik denetimlerini kullanarak Microsoft Office Word belgesinin parçalarını koruyabileceğiniz çeşitli yollar vardır:

- Bir içerik denetimini koruyabilirsiniz.

- Bir belgenin içerik denetiminde olmayan bir bölümünü koruyabilirsiniz.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a> İçerik denetimini koruma
 Tasarım zamanında veya çalışma zamanında, belge düzeyindeki bir projede denetimin özelliklerini ayarlayarak kullanıcıların bir içerik denetimini düzenlemesini veya silmesini engelleyebilirsiniz.

 Ayrıca, bir VSTO eklenti projesi kullanarak çalışma zamanında belgeye eklediğiniz içerik denetimlerini de koruyabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md).

### <a name="to-protect-a-content-control-at-design-time"></a>Tasarım zamanında bir içerik denetimini korumak için

1. Tasarımcıda barındırılan belge içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , korumak istediğiniz içerik denetimini seçin.

2. **Özellikler** penceresinde, aşağıdaki özelliklerden birini veya her ikisini birden ayarlayın:

    - Kullanıcıların denetimi düzenlemesini engellemek için, **LockContents** ' i **true** olarak ayarlayın.

    - Kullanıcıların denetimi silmesini engellemek için **LockContentControl** öğesini **true** olarak ayarlayın.

3. **Tamam**'a tıklayın.

### <a name="to-protect-a-content-control-at-run-time"></a>Çalışma zamanında bir içerik denetimini korumak için

1. Kullanıcıların denetimi `LockContents` düzenlemesini engellemek için içerik denetiminin özelliğini **true** olarak ayarlayın ve `LockContentControl` kullanıcıların denetimi silmesini engellemek için özelliği **true** olarak ayarlayın.

     Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> belge düzeyindeki bir projede iki farklı nesnenin ve özelliklerinin kullanımını gösterir. Bu kodu çalıştırmak için `ThisDocument` projenizdeki sınıfa kodu ekleyin ve `AddProtectedContentControls` `ThisDocument_Startup` olay işleyicisinden yöntemi çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet2":::

     Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> VSTO eklenti projesindeki iki farklı nesnenin ve özelliklerinin kullanımını gösterir <xref:Microsoft.Office.Tools.Word.RichTextContentControl> . Bu kodu çalıştırmak için `ThisAddIn` projenizdeki sınıfa kodu ekleyin ve `AddProtectedContentControls` `ThisAddIn_Startup` olay işleyicisinden yöntemi çağırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet14":::

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Bir içerik denetiminde olmayan bir belgenin parçasını koruma
 Kullanıcıların bir belgeyi bir alanı içine yerleştirerek değiştirmesini engelleyebilirsiniz <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Bu, aşağıdaki senaryolarda yararlı olur:

- İçerik denetimleri içermeyen bir alanı korumak istiyorsunuz.

- Zaten içerik denetimleri içeren bir alanı korumak istiyorsunuz, ancak korumak istediğiniz metin veya diğer öğeler içerik denetimlerinde değil.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.GroupContentControl>Katıştırılmış içerik denetimleri içeren bir oluşturursanız, katıştırılmış içerik denetimleri otomatik olarak korunmaz. Kullanıcıların katıştırılmış içerik denetimini düzenlemesini engellemek için denetimin **LockContents** özelliğini kullanın.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Tasarım zamanında bir belgenin alanını korumak için

1. Tasarımcıda barındırılan belgede [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , korumak istediğiniz alanı seçin.

2. Şeritte **Geliştirici** sekmesine tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. **Denetimler** grubunda, **Grup** açılan düğmesine tıklayın ve ardından **Grup**' a tıklayın.

     <xref:Microsoft.Office.Tools.Word.GroupContentControl>Korumalı bölgeyi içeren bir, projenizdeki sınıfında otomatik olarak oluşturulur `ThisDocument` . Tasarım zamanında grup denetimini temsil eden bir kenarlık görünür, ancak çalışma zamanında görünür bir kenarlık yoktur.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Çalışma zamanında bir belgenin alanını korumak için

1. Program aracılığıyla korumak istediğiniz alanı seçin ve ardından <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> bir oluşturmak için yöntemini çağırın <xref:Microsoft.Office.Tools.Word.GroupContentControl> .

     Belge düzeyi projesi için aşağıdaki kod örneği belgedeki ilk paragrafa metin ekler, ilk paragrafı seçer ve ardından bir başlatır <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Bu kodu çalıştırmak için `ThisDocument` projenizdeki sınıfa kodu ekleyin ve `ProtectFirstParagraph` `ThisDocument_Startup` olay işleyicisinden yöntemi çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet1":::

     Bir VSTO eklenti projesi için aşağıdaki kod örneği, etkin belgedeki ilk paragrafa metin ekler, ilk paragrafı seçer ve ardından bir başlatır <xref:Microsoft.Office.Tools.Word.GroupContentControl> . Bu kodu çalıştırmak için `ThisAddIn` projenizdeki sınıfa kodu ekleyin ve `ProtectFirstParagraph` `ThisAddIn_Startup` olay işleyicisinden yöntemi çağırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet15":::

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [İçerik denetimleri](../vsto/content-controls.md)
- [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
