---
title: 'Nasıl yapılır: Word belgelerine Içerik denetimleri ekleme'
description: Belge düzeyi Word projelerinde, tasarım zamanında veya çalışma zamanında projenizdeki belgeye içerik denetimleri ekleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a902e85f8c53aa7a3d1ebe3b6480a7c68fa60601
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827909"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Nasıl yapılır: Word belgelerine Içerik denetimleri ekleme
  Belge düzeyi Word projelerinde, tasarım zamanında veya çalışma zamanında projenizdeki belgeye içerik denetimleri ekleyebilirsiniz. Word VSTO eklenti projelerinde, çalışma zamanında herhangi bir açık belgeye içerik denetimleri ekleyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında içerik denetimleri ekleme](#designtime)

- [Belge düzeyindeki bir projede çalışma zamanında içerik denetimleri ekleme](#runtimedoclevel)

- [VSTO eklenti projesindeki çalışma zamanında içerik denetimleri ekleme](#runtimeaddin)

  İçerik denetimleri hakkında daha fazla bilgi için bkz. [içerik denetimleri](../vsto/content-controls.md).

## <a name="add-content-controls-at-design-time"></a><a name="designtime"></a> Tasarım zamanında Içerik denetimleri ekleme
 Belge düzeyindeki bir projede belgeye tasarım zamanında içerik denetimleri eklemenin birkaç yolu vardır:

- **Araç kutusunun** **Word denetimleri** sekmesinden bir içerik denetimi ekleyin.

- Word 'de yerel içerik denetimi ekleyeceğiniz şekilde belgenize bir içerik denetimi ekleyin.

- **Veri kaynakları** penceresinden bir içerik denetimini belgenize sürükleyin. Bu, Denetim oluşturulduğunda denetimi verilere bağlamak istediğinizde yararlıdır. Daha fazla bilgi için bkz. [nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md) ve [nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Araç kutusunu kullanarak bir belgeye içerik denetimi eklemek için

1. Tasarımcıda barındırılan belgede [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , içerik denetimini eklemek istediğiniz yere imleci koyun veya içerik denetiminin değiştirilmesini istediğiniz metni seçin.

2. **Araç kutusunu** açın ve **Word denetimleri** sekmesine tıklayın.

3. Denetimi aşağıdaki yollarla ekleyin:

    - **Araç kutusunda** bir içerik denetimine çift tıklayın.

         veya

    - **Araç kutusunda** bir içerik denetimine tıklayın ve ardından **ENTER** tuşuna basın.

         veya

    - **Araç kutusundan** bir içerik denetimini belgeye sürükleyin. İçerik denetimi, fare işaretçisinin konumunda değil belgedeki geçerli seçime eklenir.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.GroupContentControl> **Araç kutusunu** kullanarak bir ekleyemezsiniz. Yalnızca bir <xref:Microsoft.Office.Tools.Word.GroupContentControl> kelime veya çalışma zamanında ekleyebilirsiniz.

> [!NOTE]
> Visual Studio, araç kutusunda onay kutusu içerik denetimi sağlamaz. Belgeye bir onay kutusu içerik denetimi eklemek için <xref:Microsoft.Office.Tools.Word.ContentControl> Program aracılığıyla bir nesne oluşturmanız gerekir. Daha fazla bilgi için bkz. [içerik denetimleri](../vsto/content-controls.md).

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Word 'de belgeye içerik denetimi eklemek için

1. Tasarımcıda barındırılan belgede [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , içerik denetimini eklemek istediğiniz yere imleci koyun veya içerik denetiminin değiştirilmesini istediğiniz metni seçin.

2. Şeritte **Geliştirici** sekmesine tıklayın.

    > [!NOTE]
    > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. **Denetimler** grubunda, eklemek istediğiniz içerik denetimi simgesine tıklayın.

## <a name="add-content-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyindeki bir projede çalışma zamanında içerik denetimleri ekleme
 Projenizdeki sınıf özelliğinin yöntemlerini kullanarak çalışma zamanında belgenize programlı bir şekilde içerik denetimleri ekleyebilirsiniz <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> `ThisDocument` . Her yöntemin, aşağıdaki yollarla bir içerik denetimi eklemek için kullanabileceğiniz üç aşırı yüklemesi vardır:

- Geçerli seçime bir denetim ekleyin.

- Belirtilen aralığa bir denetim ekleyin.

- Belgedeki yerel içerik denetimini temel alan bir denetim ekleyin.

  Belge kapatıldığında dinamik olarak oluşturulan içerik denetimleri belgede kalıcı olmaz. Ancak, yerel içerik denetimi belgede kalır. Belgenin bir sonraki açılışında yerel içerik denetimine dayalı bir içerik denetimini yeniden oluşturabilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

> [!NOTE]
> Word 2010 projesindeki bir belgeye onay kutusu içerik denetimi eklemek için bir nesnesi oluşturmanız gerekir <xref:Microsoft.Office.Tools.Word.ContentControl> . Daha fazla bilgi için bkz. [içerik denetimleri](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Geçerli seçime bir içerik denetimi eklemek için

1. Adında bir <xref:Microsoft.Office.Tools.Word.ControlCollection> yöntemi kullanın `Add` \<*control class*> ( *Denetim sınıfı* , eklemek istediğiniz içerik denetiminin sınıf adıdır <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) ve yeni denetimin adı için tek bir parametreye sahiptir.

     Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> belgenin başlangıcına yeni bir eklemek için yöntemini kullanır <xref:Microsoft.Office.Tools.Word.RichTextContentControl> . Bu kodu çalıştırmak için `ThisDocument` projenizdeki sınıfa kodu ekleyin ve `AddRichTextControlAtSelection` `ThisDocument_Startup` olay işleyicisinden yöntemi çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet700":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet700":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Belirli bir aralığa içerik denetimi eklemek için

1. Adında bir <xref:Microsoft.Office.Tools.Word.ControlCollection> yöntemi kullanın `Add` \<*control class*> (burada *Denetim sınıfı* , eklemek istediğiniz içerik denetim sınıfının adıdır, gibi <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) ve bir <xref:Microsoft.Office.Interop.Word.Range> parametresi vardır.

     Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> belgenin başlangıcına yeni bir eklemek için yöntemini kullanır <xref:Microsoft.Office.Tools.Word.RichTextContentControl> . Bu kodu çalıştırmak için `ThisDocument` projenizdeki sınıfa kodu ekleyin ve `AddRichTextControlAtRange` `ThisDocument_Startup` olay işleyicisinden yöntemi çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet701":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet701":::

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Yerel içerik denetimini temel alan bir içerik denetimi eklemek için

1. Adında bir <xref:Microsoft.Office.Tools.Word.ControlCollection> yöntemi kullanın `Add` \<*control class*> (burada *Denetim sınıfı* , eklemek istediğiniz içerik denetim sınıfının adıdır, gibi <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) ve bir `Microsoft.Office.Interop.Word.ContentControl` parametresi vardır.

     Aşağıdaki kod örneği, belgesinde bulunan <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> her yerel zengin metin denetimine yeni bir oluşturmak için yöntemini kullanır. Bu kodu çalıştırmak için `ThisDocument` projenizdeki sınıfa kodu ekleyin ve `CreateRichTextControlsFromNativeControls` `ThisDocument_Startup` olay işleyicisinden yöntemi çağırın.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet702":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet702":::

## <a name="add-content-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> VSTO eklenti projesindeki çalışma zamanında içerik denetimleri ekleme
 Bir VSTO eklentisi kullanarak çalışma zamanında herhangi bir açık belgeye programlama yoluyla içerik denetimleri ekleyebilirsiniz. Bunu yapmak için, açık bir <xref:Microsoft.Office.Tools.Word.Document> belgeyi temel alan bir konak öğesi oluşturun ve ardından <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> Bu konak öğesinin özelliğinin yöntemlerini kullanın. Her yöntemin, aşağıdaki yollarla bir içerik denetimi eklemek için kullanabileceğiniz üç aşırı yüklemesi vardır:

- Geçerli seçime bir denetim ekleyin.

- Belirtilen aralığa bir denetim ekleyin.

- Belgedeki yerel içerik denetimini temel alan bir denetim ekleyin.

  Belge kapatıldığında dinamik olarak oluşturulan içerik denetimleri belgede kalıcı olmaz. Ancak, yerel içerik denetimi belgede kalır. Belgenin bir sonraki açılışında yerel içerik denetimine dayalı bir içerik denetimini yeniden oluşturabilirsiniz. Daha fazla bilgi için bkz. [Dinamik denetimleri Office belgelerinde kalıcı hale](../vsto/persisting-dynamic-controls-in-office-documents.md)getirme.

  VSTO eklenti projelerinde konak öğeleri oluşturma hakkında daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

> [!NOTE]
> Bir belgeye onay kutusu içerik denetimi eklemek için bir nesnesi oluşturmanız gerekir <xref:Microsoft.Office.Tools.Word.ContentControl> . Daha fazla bilgi için bkz. [içerik denetimleri](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Geçerli seçime bir içerik denetimi eklemek için

1. Adında bir <xref:Microsoft.Office.Tools.Word.ControlCollection> yöntemi kullanın `Add` \<*control class*> ( *Denetim sınıfı* , eklemek istediğiniz içerik denetiminin sınıf adıdır <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) ve yeni denetimin adı için tek bir parametreye sahiptir.

     Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> etkin belgenin başlangıcına yeni bir eklemek için yöntemini kullanır <xref:Microsoft.Office.Tools.Word.RichTextContentControl> . Bu kodu çalıştırmak için `ThisAddIn` projenizdeki sınıfa kodu ekleyin ve `AddRichTextControlAtSelection` `ThisAddIn_Startup` olay işleyicisinden yöntemi çağırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet1":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Belirli bir aralığa içerik denetimi eklemek için

1. Adında bir <xref:Microsoft.Office.Tools.Word.ControlCollection> yöntemi kullanın `Add` \<*control class*> (burada *Denetim sınıfı* , eklemek istediğiniz içerik denetim sınıfının adıdır, gibi <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) ve bir <xref:Microsoft.Office.Interop.Word.Range> parametresi vardır.

     Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> etkin belgenin başlangıcına yeni bir eklemek için yöntemini kullanır <xref:Microsoft.Office.Tools.Word.RichTextContentControl> . Bu kodu çalıştırmak için `ThisAddIn` projenizdeki sınıfa kodu ekleyin ve `AddRichTextControlAtRange` `ThisAddIn_Startup` olay işleyicisinden yöntemi çağırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet2":::

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Yerel içerik denetimini temel alan bir içerik denetimi eklemek için

1. Adında bir <xref:Microsoft.Office.Tools.Word.ControlCollection> yöntemi kullanın `Add` \<*control class*> (burada *Denetim sınıfı* , eklemek istediğiniz içerik denetim sınıfının adıdır, gibi <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) ve bir `Microsoft.Office.Interop.Word.ContentControl` parametresi vardır.

     Aşağıdaki kod örneği, belge <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> açıldıktan sonra bir belgedeki her yerel zengin metin denetimine yeni bir oluşturmak için yöntemini kullanır. Bu kodu çalıştırmak için `ThisAddIn` projenizdeki sınıfa kodu ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet3":::

     C# için olay işleyicisini olaya de eklemeniz gerekir `Application_DocumentOpen` <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
