---
title: 'Nasıl kullanılır: İçerik denetimlerini kullanarak belgelerin bölümlerini koruma'
description: İçerik denetimlerini kullanarak bir Visual Studio bölümlerini korumak için Microsoft Word nasıl kullanabileceğinizi öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 49988266ebee5821323ee3a9994312d99033c9f3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633865"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Nasıl kullanılır: İçerik denetimlerini kullanarak belgelerin bölümlerini koruma
  Bir belgenin bir bölümünü korurken, kullanıcıların belgenin o bölümünde içeriği değiştirmesini veya silmesini önlersiniz. İçerik denetimlerini kullanarak bir Word belgesinin Microsoft Office korumanın çeşitli yolları vardır:

- İçerik denetimi koruyabilirsiniz.

- Bir belgenin içerik denetiminde yer alan bir bölümünü koruyabilirsiniz.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a> İçerik denetimi koruma
 Tasarım zamanında veya çalışma zamanında bir belge düzeyi projesinde denetimin özelliklerini ayarleyerek kullanıcıların içerik denetimi düzenlemesini veya silmesini önleyebilirsiniz.

 Ayrıca, çalışma zamanında bir belgeye ekley istediğiniz içerik denetimlerini, VSTO projesini kullanarak koruyabilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Word belgelerine içerik denetimleri ekleme.](../vsto/how-to-add-content-controls-to-word-documents.md)

### <a name="to-protect-a-content-control-at-design-time"></a>İçerik denetimlerini tasarım zamanında korumak için

1. Tasarımcıda barındırılan [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belgede, korumak istediğiniz içerik denetimlerini seçin.

2. Özellikler **penceresinde,** aşağıdaki özelliklerden birini veya ikisini birden ayarlayın:

    - Kullanıcıların denetimi düzenlemesini önlemek için **LockContents'i** True olarak **ayarlayın.**

    - Kullanıcıların denetimi silmesini önlemek için **LockContentControl'ı** True olarak **ayarlayın.**

3. **Tamam**'a tıklayın.

### <a name="to-protect-a-content-control-at-run-time"></a>Çalışma zamanında içerik denetimi korumak için

1. Kullanıcıların `LockContents` denetimi düzenlemesini önlemek için içerik denetimi **özelliğini true,** kullanıcıların denetimi silmesini önlemek için özelliğini `LockContentControl` **true** olarak ayarlayın.

     Aşağıdaki kod örneği, bir belge düzeyi <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> projesinde iki farklı nesne <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ve özelliklerini kullanmayı gösterir. Bu kodu çalıştırmak için, kodu projenizin sınıfına ekleyin ve `ThisDocument` olay `AddProtectedContentControls` işleyiciden yöntemini `ThisDocument_Startup` çağırabilirsiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet2":::

     Aşağıdaki kod örneği, bir eklenti <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> projesinde iki farklı <xref:Microsoft.Office.Tools.Word.RichTextContentControl> nesne ve özelliklerini VSTO gösterir. Bu kodu çalıştırmak için, kodu projenizin sınıfına ekleyin ve `ThisAddIn` olay `AddProtectedContentControls` işleyiciden yöntemini `ThisAddIn_Startup` çağırabilirsiniz.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet14":::

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Belgenin içerik denetiminde yer alan bir bölümünü koruma
 Bir alanına koyarak kullanıcıların bir belgenin bir alanı değiştirmesini önleyebilirsiniz. <xref:Microsoft.Office.Tools.Word.GroupContentControl> Bu, aşağıdaki senaryolarda yararlıdır:

- İçerik denetimleri içermeden bir alanı korumak istediğiniz.

- İçerik denetimleri içeren bir alanı korumak istiyor ancak korumak istediğiniz metin veya diğer öğeler içerik denetimlerde yer alamı değildir.

> [!NOTE]
> Ekli içerik <xref:Microsoft.Office.Tools.Word.GroupContentControl> denetimleri içeren bir oluşturabilirsiniz, ekli içerik denetimleri otomatik olarak korunmaz. Kullanıcıların ekli içerik denetimi düzenlemesini önlemek için **denetimin LockContents** özelliğini kullanın.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Bir belgenin tasarım zamanında bir alanı korumak için

1. Tasarımcıda barındırılan [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belgede, korumak istediğiniz alanı seçin.

2. Şeritte Geliştirici **sekmesine** tıklayın.

    > [!NOTE]
    > Geliştirici **sekmesi** görünmüyorsa, önce bunu göstermeniz gerekir. Daha fazla bilgi için [şeritteki Geliştirici sekmesini gösterme.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

3. Denetimler **grubunda,** Grup açılan **düğmesine** ve ardından Grup'a **tıklayın.**

     Korumalı <xref:Microsoft.Office.Tools.Word.GroupContentControl> bölgeyi içeren bir, projenizin sınıfında `ThisDocument` otomatik olarak oluşturulur. Grup denetimlerini temsil eden kenarlık tasarım zamanında görünür, ancak çalışma zamanında görünür kenarlık yoktur.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Çalışma zamanında belgenin bir alanı korumak için

1. Program aracılığıyla korumak istediğiniz alanı seçin ve ardından yöntemini <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> çağırarak bir <xref:Microsoft.Office.Tools.Word.GroupContentControl> oluşturun.

     Belge düzeyi proje için aşağıdaki kod örneği, belgede ilk paragrafa metin ekler, ilk paragrafı seçer ve ardından bir örneğini <xref:Microsoft.Office.Tools.Word.GroupContentControl> oluşturur. Bu kodu çalıştırmak için, kodu projenizin sınıfına ekleyin ve `ThisDocument` olay `ProtectFirstParagraph` işleyiciden yöntemini `ThisDocument_Startup` çağırabilirsiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet1":::

     VSTO Eklenti projesi için aşağıdaki kod örneği, etkin belgede ilk paragrafa metin ekler, ilk paragrafı seçer ve ardından bir örneğini <xref:Microsoft.Office.Tools.Word.GroupContentControl> oluşturur. Bu kodu çalıştırmak için, kodu projenizin sınıfına ekleyin ve `ThisAddIn` olay `ProtectFirstParagraph` işleyiciden yöntemini `ThisAddIn_Startup` çağırabilirsiniz.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet15":::

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [İçerik denetimleri](../vsto/content-controls.md)
- [Nasıl kullanılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Çalışma zamanında Office için denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
