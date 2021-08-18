---
title: Word belgelerine veya çalışma kitaplarını Excel ekleme
description: Microsoft Office Word belgesine veya Microsoft Excel çalışma kitabına eylemler bölmesi eklemek için öncelikle Windows Forms kullanıcı denetimi oluşturmanız gerektiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e86893fd1ae5ba42ee0f2ed5f8d4bbc6fdad50f8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083563"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Nasıl Yapılır: Word Belgelerine veya Excel Çalışma Kitaplarına Eylemler Bölmesi Ekleme
  Microsoft Office Word belgesine veya Microsoft Excel çalışma kitabına eylemler bölmesi eklemek için ilk olarak Windows Forms kullanıcı denetimi oluşturun. Ardından kullanıcı denetiminizi projenizin <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` (Word) veya alanın `ThisWorkbook.ActionsPane` (Excel) özelliğine ekleyin.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="creating-the-user-control"></a>Kullanıcı Denetimi Oluşturma
 Aşağıdaki yordam, bir Word veya Excel projesinde kullanıcı denetimi oluşturma işlemi gösterir. Ayrıca kullanıcı denetimine, tıkıldığında belgeye veya çalışma kitabına metin yazan bir düğme ekler.

#### <a name="to-create-the-user-control"></a>Kullanıcı denetimi oluşturmak için

1. Word veya Excel düzeyi projenizi Visual Studio.

2. Yeni **Project** Ekle'ye **tıklayın.**

3. Yeni Öğe **Ekle iletişim kutusunda** Eylemler Bölmesi Denetimi'ni **seçin,** **HelloControl** olarak ad girin ve Ekle'ye **tıklayın.**

    > [!NOTE]
    > Alternatif olarak projenize bir **Kullanıcı Denetimi** öğesi ekebilirsiniz. Eylemler Bölmesi Denetimi ve **Kullanıcı Denetimi öğeleri tarafından** oluşturulan sınıflar **işlevsel** olarak eşdeğerdir.

4. Araç **kutusunun Windows Formlar** **sekmesinden bir** **Düğme denetimi sürükleyerek** denetime sürükleyin.

    > [!NOTE]
    > Denetim tasarımcıda görünmüyorsa, denetimin içinde **HelloControl'a** **çift Çözüm Gezgini.**

5. Kodu düğmenin olay <xref:System.Windows.Forms.Control.Click> işleyicisi'ne ekleyin. Aşağıdaki örnekte, bir Word belgesi için Microsoft Office ve gösterir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb" id="Snippet12":::

6. C# içinde, düğme tıklaması için bir olay işleyicisi eklemeniz gerekir. Bu kodu çağrısının ardından `HelloControl` oluşturucuya yer veebilirsiniz. `InitializeComponent`

     Olay işleyicileri oluşturma hakkında daha fazla bilgi için [bkz. Nasıl 2011: Office Projelerinde Olay İşleyicileri Oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet13":::

## <a name="add-the-user-control-to-the-actions-pane"></a>Eylemler bölmesine kullanıcı denetimi ekleme
 Eylemler bölmesini göstermek için, kullanıcı denetimi alanını <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` (Word) veya alanın (word) `ThisWorkbook.ActionsPane` özelliğine Excel.

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Kullanıcı denetimi eylemler bölmesine eklemek için

1. Aşağıdaki kodu veya `ThisDocument` sınıfına `ThisWorkbook` sınıf düzeyi bildirim olarak ekleyin (bu kodu bir yönteme ekleme).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet14":::

2. Sınıfın olay `ThisDocument_Startup` işleyicisi veya sınıfının olay `ThisDocument` `ThisWorkbook_Startup` işleyicisi için aşağıdaki kodu `ThisWorkbook` ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet15":::

## <a name="see-also"></a>Ayrıca bkz.
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Adım adım kılavuz: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Nasıl gösterilir: Eylemler bölmeleri üzerinde denetim düzenini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Adım adım kılavuz: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
