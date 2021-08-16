---
title: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme
description: bir Microsoft Office Word belgesine veya Microsoft Excel çalışma kitabına eylemler bölmesi eklemek için, önce bir Windows Forms kullanıcı denetimi oluşturmanız gerektiğini öğrenin.
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
ms.openlocfilehash: a30853d0d685f4b916993b5784cc1158304115385442e7ceb4709f8c17a4e739
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424222"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Nasıl Yapılır: Word Belgelerine veya Excel Çalışma Kitaplarına Eylemler Bölmesi Ekleme
  bir Microsoft Office Word belgesine veya Microsoft Excel çalışma kitabına eylemler bölmesi eklemek için, önce bir Windows Forms kullanıcı denetimi oluşturun. sonra, kullanıcı denetimini <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` projenizdeki alan (kelime) veya `ThisWorkbook.ActionsPane` alan (Excel) özelliğine ekleyin.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Kullanıcı denetimi oluşturma
 aşağıdaki yordamda, bir kelime veya Excel projesinde kullanıcı denetiminin nasıl oluşturulacağı gösterilmektedir. Ayrıca, tıklatıldığında belgeye veya çalışma kitabına metin yazan Kullanıcı denetimine bir düğme ekler.

#### <a name="to-create-the-user-control"></a>Kullanıcı denetimi oluşturmak için

1. Word 'ü veya Excel belge düzeyi projenizi Visual Studio açın.

2. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

3. **Yeni öğe Ekle** Iletişim kutusunda **Eylemler bölmesi denetimi**' ni seçin, **Merhaba denetimini** adlandırın ve **Ekle**' ye tıklayın.

    > [!NOTE]
    > Alternatif olarak, projenize bir **Kullanıcı denetim** öğesi ekleyebilirsiniz. **Eylemler bölmesi denetimi** ve **Kullanıcı denetimi** öğeleri tarafından oluşturulan sınıflar, işlevsel olarak eşdeğerdir.

4. **araç kutusunun** **Windows Forms** sekmesinden denetim üzerine bir **düğme** denetimi sürükleyin.

    > [!NOTE]
    > Denetim tasarımcıda görünmüyorsa, **Çözüm Gezgini**' de **HelloControl** ' a çift tıklayın.

5. <xref:System.Windows.Forms.Control.Click>Düğmenin olay işleyicisine kodu ekleyin. aşağıdaki örnek bir Microsoft Office Word belgesi için kodu gösterir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb" id="Snippet12":::

6. C# ' de, düğme tıklayı için bir olay işleyicisi eklemeniz gerekir. `HelloControl`Çağrısından sonra bu kodu oluşturucuya yerleştirebilirsiniz `InitializeComponent` .

     olay işleyicilerini oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: olay işleyicileri oluşturma Office projelerinde](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet13":::

## <a name="add-the-user-control-to-the-actions-pane"></a>Eylemler bölmesine Kullanıcı denetimini ekleme
 Eylemler bölmesini göstermek için, <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` alan (Word) veya alan (Excel) özelliğine kullanıcı denetimini ekleyin `ThisWorkbook.ActionsPane` .

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Eylemler bölmesine Kullanıcı denetimi eklemek için

1. Aşağıdaki kodu `ThisDocument` `ThisWorkbook` bir sınıf düzeyi bildirimi olarak veya sınıfına ekleyin (Bu kodu bir yönteme eklemeyin).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet14":::

2. `ThisDocument_Startup`Sınıfının olay işleyicisine `ThisDocument` veya `ThisWorkbook_Startup` sınıfının olay işleyicisine aşağıdaki kodu ekleyin `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet15":::

## <a name="see-also"></a>Ayrıca bkz.
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
