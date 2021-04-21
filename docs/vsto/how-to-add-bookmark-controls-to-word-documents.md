---
title: 'Nasıl yapılır: Word belgelerine yer Işareti denetimleri ekleme'
description: Belge düzeyi projelerde, tasarım zamanında veya çalışma zamanında projenizdeki belgeye Bookmark denetimleri ekleyebileceğinizi öğrenin.
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0a5520582db9919417b1c70d773355901ac0b0a5
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826609"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Nasıl yapılır: Word belgelerine yer Işareti denetimleri ekleme
  Belge düzeyi projelerde, <xref:Microsoft.Office.Tools.Word.Bookmark> tasarım zamanında veya çalışma zamanında projenizdeki belgeye denetim ekleyebilirsiniz. VSTO eklenti projelerinde, <xref:Microsoft.Office.Tools.Word.Bookmark> çalışma zamanında herhangi bir açık belgeye denetimler ekleyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Bu konuda aşağıdaki görevler açıklanmaktadır:

- [Tasarım zamanında Bookmark denetimleri ekleme](#designtime)

- [Belge düzeyindeki bir projede çalışma zamanında yer Işareti denetimleri ekleme](#runtimedoclevel)

- [VSTO eklenti projesindeki çalışma zamanında yer Işareti denetimleri ekleme](#runtimeaddin)

  Denetimler hakkında daha fazla bilgi için <xref:Microsoft.Office.Tools.Word.Bookmark> bkz. [Bookmark Control](../vsto/bookmark-control.md).

## <a name="add-bookmark-controls-at-design-time"></a><a name="designtime"></a> Tasarım zamanında Bookmark denetimleri ekleme
 Belge <xref:Microsoft.Office.Tools.Word.Bookmark> düzeyindeki bir projede belgeye tasarım zamanında denetim eklemenin birkaç yolu vardır:

- Visual Studio **araç kutusundan**.

   <xref:Microsoft.Office.Tools.Word.Bookmark>Denetimi **araç kutusundan** belgenize sürükleyebilirsiniz. Belgenize Windows Forms denetimleri eklemek için **araç kutusunu** zaten kullanıyorsanız, bu yolu tercih edebilirsiniz.

- Word içinden.

   <xref:Microsoft.Office.Tools.Word.Bookmark>Yerel yer işaretini ekleyeceğiniz şekilde belgenize denetim ekleyebilirsiniz. Bu şekilde eklemenin avantajı, denetiminizi oluşturduğunuz sırada bir kez ad olarak belirleyebilirsiniz.

- **Veri kaynakları** penceresinden.

   <xref:Microsoft.Office.Tools.Word.Bookmark> **Veri kaynakları** penceresinden denetimi belgenize sürükleyebilirsiniz. Bu, denetimi verilere aynı anda bağlamak istediğinizde yararlıdır. Konak denetimini, **veri kaynakları** penceresinden bir Windows form denetimi ekleyeceğiniz şekilde ekleyebilirsiniz. Daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Araç kutusu 'ndan bir belgeye bir yer Işareti denetimi eklemek için

1. **Araç kutusunu** açın ve **Word denetimleri** sekmesine tıklayın.

2. Belgeye bir <xref:Microsoft.Office.Tools.Word.Bookmark> Denetim sürükleyin.

     **Yer Işareti Ekle** iletişim kutusu görünür.

3. Yer işaretine eklemek istediğiniz metni veya diğer öğeleri seçin.

4. **Tamam**'a tıklayın.

     Varsayılan yer işaretinin adını korumak istemiyorsanız, adı **Özellikler** penceresinde değiştirebilirsiniz.

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Word 'de belgeye bir yer Işareti denetimi eklemek için

1. Tasarımcıda barındırılan belgede [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , yer işaretini eklemek istediğiniz yere yerleştirin veya yer işaretinin kapsamasını istediğiniz metni seçin.

2. Şeridin **Ekle** sekmesinde, **Bağlantılar** grubunda **yer işareti** düğmesine tıklayın.

3. **Yer işareti** iletişim kutusunda yeni yer işaretinin adını yazın ve **Ekle**' ye tıklayın.

## <a name="add-bookmark-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyindeki bir projede çalışma zamanında yer Işareti denetimleri ekleme
 <xref:Microsoft.Office.Tools.Word.Bookmark>Projenizdeki sınıf özelliğinin yöntemlerini kullanarak çalışma zamanında belgenize programlı bir şekilde denetim ekleyebilirsiniz <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> `ThisDocument` . Aşağıdaki yollarla bir denetim eklemek için kullanabileceğiniz iki yöntem aşırı yüklemesi vardır <xref:Microsoft.Office.Tools.Word.Bookmark> :

- Belirtilen bir <xref:Microsoft.Office.Tools.Word.Bookmark> aralığa ekleyin.

- <xref:Microsoft.Office.Tools.Word.Bookmark>Belgedeki yerel bir yer işaretine (yani, a) dayalı bir ekleyin <xref:Microsoft.Office.Interop.Word.Bookmark> .

  Belge kapatıldığında dinamik olarak oluşturulan <xref:Microsoft.Office.Tools.Word.Bookmark> denetimler belgede kalıcı olmaz. Ancak, yerel bir <xref:Microsoft.Office.Interop.Word.Bookmark> belgede kalır. Belgenin bir sonraki açılışında <xref:Microsoft.Office.Tools.Word.Bookmark> yerel bir yer işaretine dayalı bir oluştur işlemi yapabilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Belgeye programlı bir Bookmark denetimi eklemek için

1. `ThisDocument_Startup`Projenizdeki olay işleyicisinde, <xref:Microsoft.Office.Tools.Word.Bookmark> denetimi belgedeki ilk paragrafa eklemek için aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet1":::

    > [!NOTE]
    > <xref:Microsoft.Office.Tools.Word.Bookmark>Varolan bir denetimi oluşturmak istiyorsanız, <xref:Microsoft.Office.Interop.Word.Bookmark> <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> yöntemini kullanın ve var olan öğesini geçirin <xref:Microsoft.Office.Interop.Word.Bookmark> .

## <a name="add-bookmark-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> VSTO eklenti projesindeki çalışma zamanında yer Işareti denetimleri ekleme
 <xref:Microsoft.Office.Tools.Word.Bookmark>VSTO eklentisini kullanarak çalışma zamanında herhangi bir açık belgeye program aracılığıyla denetimler ekleyebilirsiniz. Bunu yapmak için, açık bir <xref:Microsoft.Office.Tools.Word.Document> belgeyi temel alan bir konak öğesi oluşturun ve ardından <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> Bu konak öğesinin özelliğinin yöntemlerini kullanın. Aşağıdaki yollarla bir denetim eklemek için kullanabileceğiniz iki yöntem aşırı yüklemesi vardır <xref:Microsoft.Office.Tools.Word.Bookmark> :

- Belirtilen bir <xref:Microsoft.Office.Tools.Word.Bookmark> aralığa ekleyin.

- <xref:Microsoft.Office.Tools.Word.Bookmark>Belgedeki yerel bir yer işaretine (yani, a) dayalı bir ekleyin <xref:Microsoft.Office.Interop.Word.Bookmark> .

  Belge kapatıldığında dinamik olarak oluşturulan <xref:Microsoft.Office.Tools.Word.Bookmark> denetimler belgede kalıcı olmaz. Ancak, yerel bir <xref:Microsoft.Office.Interop.Word.Bookmark> belgede kalır. Belgenin bir sonraki açılışında <xref:Microsoft.Office.Tools.Word.Bookmark> yerel bir yer işaretine dayalı bir oluştur işlemi yapabilirsiniz. Daha fazla bilgi için bkz. [Dinamik denetimleri Office belgelerinde kalıcı hale](../vsto/persisting-dynamic-controls-in-office-documents.md)getirme.

  VSTO eklenti projelerinde konak öğeleri oluşturma hakkında daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Belirtilen aralığa bir yer Işareti denetimi eklemek için

1. Yöntemini kullanın <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> ve öğesini eklemek istediğiniz yere geçirin <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Tools.Word.Bookmark> .

     Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.Bookmark> etkin belgenin başlangıcına yeni bir ekler. Bu örneği kullanmak için, `ThisAddIn_Startup` olay işleyicisindeki kodu bir Word VSTO eklenti projesinde çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet4":::

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Yerel bir yer Işareti denetimine dayalı bir yer Işareti denetimi eklemek için

1. Yöntemini kullanın <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> ve <xref:Microsoft.Office.Interop.Word.Bookmark> Yeni için temel olarak kullanmak istediğiniz varolan ' ı geçirin <xref:Microsoft.Office.Tools.Word.Bookmark> .

     Aşağıdaki kod örneği, <xref:Microsoft.Office.Tools.Word.Bookmark> etkin belgede ilkini temel alan yeni bir oluşturur <xref:Microsoft.Office.Interop.Word.Bookmark> . Bu örneği kullanmak için, `ThisAddIn_Startup` olay işleyicisindeki kodu bir Word VSTO eklenti projesinde çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet5":::

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Nasıl yapılır: yer Işareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)
