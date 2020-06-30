---
title: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2d24ec3a17c9e0824c6b7aaffeaaac02c1c4f76e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546230"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Nasıl Yapılır: Word Belgelerine veya Excel Çalışma Kitaplarına Eylemler Bölmesi Ekleme
  Bir Microsoft Office Word belgesine veya Microsoft Excel çalışma kitabına eylemler bölmesi eklemek için, önce bir Windows Forms Kullanıcı denetimi oluşturun. Daha sonra, Kullanıcı denetimini <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` projenizdeki alan (Word) veya `ThisWorkbook.ActionsPane` alan (Excel) özelliğine ekleyin.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Kullanıcı denetimi oluşturma
 Aşağıdaki yordamda, bir Word veya Excel projesinde kullanıcı denetiminin nasıl oluşturulacağı gösterilmektedir. Ayrıca, tıklatıldığında belgeye veya çalışma kitabına metin yazan Kullanıcı denetimine bir düğme ekler.

#### <a name="to-create-the-user-control"></a>Kullanıcı denetimi oluşturmak için

1. Word veya Excel belge düzeyi projenizi Visual Studio 'da açın.

2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

3. **Yeni öğe Ekle** Iletişim kutusunda **Eylemler bölmesi denetimi**' ni seçin, **Merhaba denetimini**adlandırın ve **Ekle**' ye tıklayın.

    > [!NOTE]
    > Alternatif olarak, projenize bir **Kullanıcı denetim** öğesi ekleyebilirsiniz. **Eylemler bölmesi denetimi** ve **Kullanıcı denetimi** öğeleri tarafından oluşturulan sınıflar, işlevsel olarak eşdeğerdir.

4. **Araç kutusunun** **Windows Forms** sekmesinden denetim üzerine bir **düğme** denetimi sürükleyin.

    > [!NOTE]
    > Denetim tasarımcıda görünmüyorsa, **Çözüm Gezgini**' de **HelloControl** ' a çift tıklayın.

5. <xref:System.Windows.Forms.Control.Click>Düğmenin olay işleyicisine kodu ekleyin. Aşağıdaki örnek bir Microsoft Office Word belgesi için kodu gösterir.

     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]

6. C# ' de, düğme tıklayı için bir olay işleyicisi eklemeniz gerekir. `HelloControl`Çağrısından sonra bu kodu oluşturucuya yerleştirebilirsiniz `InitializeComponent` .

     Olay işleyicilerini oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]

## <a name="add-the-user-control-to-the-actions-pane"></a>Eylemler bölmesine Kullanıcı denetimini ekleme
 Eylemler bölmesini göstermek için, <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` alan (Word) veya `ThisWorkbook.ActionsPane` alan (Excel) özelliğine kullanıcı denetimini ekleyin.

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Eylemler bölmesine Kullanıcı denetimi eklemek için

1. Aşağıdaki kodu `ThisDocument` `ThisWorkbook` bir sınıf düzeyi bildirimi olarak veya sınıfına ekleyin (Bu kodu bir yönteme eklemeyin).

     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]

2. `ThisDocument_Startup`Sınıfının olay işleyicisine `ThisDocument` veya `ThisWorkbook_Startup` sınıfının olay işleyicisine aşağıdaki kodu ekleyin `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]

## <a name="see-also"></a>Ayrıca bkz.
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
