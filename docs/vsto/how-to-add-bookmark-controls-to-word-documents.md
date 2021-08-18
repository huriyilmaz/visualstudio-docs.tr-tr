---
title: 'Nasıl kullanılır: Word belgelerine Yer İşareti denetimleri ekleme'
description: Belge düzeyindeki projelerde, projenizin tasarım zamanında veya çalışma zamanında belgeye Yer İşareti denetimleri ekleyebilirsiniz.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: edc861a203b211feb1018cf26cadd6ad996f0164
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100289"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Nasıl kullanılır: Word belgelerine Yer İşareti denetimleri ekleme
  Belge düzeyindeki projelerde, <xref:Microsoft.Office.Tools.Word.Bookmark> projenizin tasarım zamanında veya çalışma zamanında belgeye denetimler ekleyebilirsiniz. Bu VSTO projelerinde, çalışma zamanında herhangi <xref:Microsoft.Office.Tools.Word.Bookmark> bir açık belgeye denetim ekleyebilirsiniz.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Bu konuda aşağıdaki görevler açıklanmıştır:

- [Tasarım zamanında Yer İşareti denetimleri ekleme](#designtime)

- [Belge düzeyi projesinde çalışma zamanında Yer İşareti denetimleri ekleme](#runtimedoclevel)

- [VSTO Add-in projesine çalışma zamanında Yer İşareti denetimleri ekleme](#runtimeaddin)

  Denetimler hakkında daha fazla <xref:Microsoft.Office.Tools.Word.Bookmark> bilgi için bkz. [Yer işareti denetimi.](../vsto/bookmark-control.md)

## <a name="add-bookmark-controls-at-design-time"></a><a name="designtime"></a> Tasarım Zamanında Yer İşareti denetimleri ekleme
 Tasarım zamanında belge düzeyi <xref:Microsoft.Office.Tools.Word.Bookmark> projesinde belgeye denetim eklemenin birkaç yolu vardır:

- Visual Studio **Araç Kutusundan**.

   Denetimi Araç <xref:Microsoft.Office.Tools.Word.Bookmark> Kutusundan **belgenize** sürükleyebilirsiniz. Belgenize form formları denetimleri eklemek için  Zaten Araç Kutusunu kullanıyorsanız Windows tercih edebilirsiniz.

- Word'den.

   Denetimi <xref:Microsoft.Office.Tools.Word.Bookmark> belgenize, yerel yer işaretini eklerken olduğu gibi ekleyebilirsiniz. Bu şekilde eklemenin avantajı, denetiminizi oluşturduktan sonra bu denetimin adını ve soyadınızı belirterek oluşturmanızdır.

- Veri **Kaynakları penceresinden.**

   Denetimi Veri <xref:Microsoft.Office.Tools.Word.Bookmark> Kaynakları penceresinden belgenize **sürükleyebilirsiniz.** Bu, denetimi verilere aynı anda bağlamak istediğiniz zaman kullanışlıdır. Konak denetimi, Veri Kaynakları penceresinden bir Windows Form denetimi eklemek için olduğu gibi eklemek için **de kullanılır.** Daha fazla bilgi için [bkz. Veri bağlama ve Windows Forms.](/dotnet/framework/winforms/data-binding-and-windows-forms)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Araç Kutusundan bir belgeye Yer İşareti denetimi eklemek için

1. Araç Kutusunu **açın ve** Word **Denetimleri sekmesine** tıklayın.

2. Bir denetimi <xref:Microsoft.Office.Tools.Word.Bookmark> belgeye sürükleyin.

     Yer **İşareti Ekle** iletişim kutusu görüntülenir.

3. Yer işaretine eklemek istediğiniz metni veya diğer öğeleri seçin.

4. **Tamam**'a tıklayın.

     Varsayılan yer işareti adını tutmak istemiyorsanız, Özellikler penceresinde adı **değiştirebilirsiniz.**

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Word'de bir belgeye Yer İşareti denetimi eklemek için

1. Tasarımcıda barındırılan belgede imleci yer işaretini eklemek istediğiniz yere yerleştirin veya yer işaretinin içine eklemesini [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] istediğiniz metni seçin.

2. Şeridin  Ekle sekmesindeki Bağlantılar **grubunda** Yer İşareti **düğmesine** tıklayın.

3. Yer **İşareti** iletişim kutusunda yeni yer işaretinin adını yazın ve Ekle'ye **tıklayın.**

## <a name="add-bookmark-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Belge düzeyi projesinde çalışma zamanında Yer İşareti denetimleri ekleme
 Projeniz içinde sınıfının özelliğinin yöntemlerini kullanarak çalışma zamanında belgenize <xref:Microsoft.Office.Tools.Word.Bookmark> program <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> aracılığıyla `ThisDocument` denetimler ekleyebilirsiniz. Aşağıdaki yollarla denetim eklemek için kullanabileceğiniz iki yöntem <xref:Microsoft.Office.Tools.Word.Bookmark> aşırı yüklemesi vardır:

- Belirtilen <xref:Microsoft.Office.Tools.Word.Bookmark> aralıkta bir ekleyin.

- Belgeye <xref:Microsoft.Office.Tools.Word.Bookmark> yerel bir yer işaretini temel alan bir ekleyin (başka bir ifadeyle). <xref:Microsoft.Office.Interop.Word.Bookmark>

  Belge <xref:Microsoft.Office.Tools.Word.Bookmark> kapatıldığında, dinamik olarak oluşturulan denetimler belgede kalıcı olmaz. Ancak, belgede <xref:Microsoft.Office.Interop.Word.Bookmark> bir yerel kalır. Belge bir sonraki <xref:Microsoft.Office.Tools.Word.Bookmark> açıldığında yerel bir yer işaretini temel alan bir yeniden oluşturabilirsiniz. Daha fazla bilgi için [bkz. Çalışma zamanında Office belgelerine denetim ekleme.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Bir belgeye program aracılığıyla Yer İşareti denetimi eklemek için

1. Projenizin `ThisDocument_Startup` olay işleyicisinde, denetimi belgenin ilk paragrafa <xref:Microsoft.Office.Tools.Word.Bookmark> eklemek için aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet1":::

    > [!NOTE]
    > Var olan bir denetimi <xref:Microsoft.Office.Tools.Word.Bookmark> oluşturmak için yöntemini kullanın ve var olan <xref:Microsoft.Office.Interop.Word.Bookmark> <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> 'i <xref:Microsoft.Office.Interop.Word.Bookmark> iletir.

## <a name="add-bookmark-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>VSTO Add-in projesine çalışma zamanında Yer İşareti denetimleri ekleme
 Çalışma zamanında açık olan herhangi bir belgeye program aracılığıyla denetimler eklemek için VSTO <xref:Microsoft.Office.Tools.Word.Bookmark> ekleyebilirsiniz. Bunu yapmak için, açık bir belgeyi temel alan bir konak öğesi üretin ve ardından bu konak <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> öğesinin özelliğinin yöntemlerini kullanın. Aşağıdaki yollarla denetim eklemek için kullanabileceğiniz iki yöntem <xref:Microsoft.Office.Tools.Word.Bookmark> aşırı yüklemesi vardır:

- Belirtilen <xref:Microsoft.Office.Tools.Word.Bookmark> aralıkta bir ekleyin.

- Belgeye <xref:Microsoft.Office.Tools.Word.Bookmark> yerel bir yer işaretini temel alan bir ekleyin (başka bir ifadeyle). <xref:Microsoft.Office.Interop.Word.Bookmark>

  Belge <xref:Microsoft.Office.Tools.Word.Bookmark> kapatıldığında, dinamik olarak oluşturulan denetimler belgede kalıcı olmaz. Ancak, belgede <xref:Microsoft.Office.Interop.Word.Bookmark> bir yerel kalır. Belge bir sonraki <xref:Microsoft.Office.Tools.Word.Bookmark> açıldığında yerel bir yer işaretini temel alan bir yeniden oluşturabilirsiniz. Daha fazla bilgi için [bkz. Dinamik denetimleri belgelerde Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

  Eklenti projelerinde konak öğeleri VSTO daha fazla bilgi için bkz. Çalışma zamanında VSTO Eklentilerinde Word belgelerini ve Excel çalışma [kitaplarını genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Belirtilen aralıkta Yer İşareti denetimi eklemek için

1. yöntemini <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> kullanın ve eklemek <xref:Microsoft.Office.Interop.Word.Range> istediğiniz yere <xref:Microsoft.Office.Tools.Word.Bookmark> iletir.

     Aşağıdaki kod örneği, etkin belgenin <xref:Microsoft.Office.Tools.Word.Bookmark> başına yeni bir ekler. Bu örneği kullanmak için Word VSTO `ThisAddIn_Startup` Add-in projesinde olay işleyiciden kodu çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet4":::

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Yerel Bir Yer İşareti denetimine dayalı bir Yer İşareti denetimi eklemek için

1. yöntemini <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> kullanın ve yeni için temel <xref:Microsoft.Office.Interop.Word.Bookmark> olarak kullanmak istediğiniz mevcut 'i iletir. <xref:Microsoft.Office.Tools.Word.Bookmark>

     Aşağıdaki kod örneği, etkin <xref:Microsoft.Office.Tools.Word.Bookmark> belgede birinciyi temel alan <xref:Microsoft.Office.Interop.Word.Bookmark> yeni bir oluşturur. Bu örneği kullanmak için Word VSTO `ThisAddIn_Startup` Add-in projesinde olay işleyiciden kodu çalıştırın.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet5":::

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Nasıl olur: Yer İşareti denetimlerini yeniden boyutlandırma](../vsto/how-to-resize-bookmark-controls.md)
