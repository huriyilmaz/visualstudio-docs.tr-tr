---
title: Eylemler bölmesine genel bakış
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 82bf3ac9515effaa1053a011085849f0afea67f5
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986307"
---
# <a name="actions-pane-overview"></a>Eylemler bölmesine genel bakış
  Bir eylemler bölmesi, belirli bir Microsoft Office Word belgesine veya Microsoft Office Excel çalışma kitabına eklenen özelleştirilebilir bir **belge eylemleri** görev bölmesidir. Eylemler bölmesi Office görev bölmesinin içinde, Excel 'deki **XML kaynağı** görev bölmesi veya Word 'deki **Stiller ve biçimlendirme** görev bölmesi gibi diğer yerleşik görev bölmeleri ile birlikte barındırılır. Eylemler bölmesi Kullanıcı arabirimini tasarlamak için Windows Forms denetimleri veya WPF denetimleri kullanabilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Yalnızca Word veya Excel için belge düzeyi özelleştirmesindeki bir eylemler bölmesi oluşturabilirsiniz. Bir VSTO eklentisi içinde bir eylemler bölmesi oluşturamazsınız. Daha fazla bilgi için bkz. [Office uygulaması ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Eylemler bölmesi özel görev bölmeleriyle farklılık gösterir. Özel görev bölmeleri, belirli bir belge değil uygulamayla ilişkilendirilir. Bazı Microsoft Office uygulamaları için VSTO eklentilerinde özel görev bölmeleri oluşturabilirsiniz. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="display-the-actions-pane"></a>Eylemler bölmesini görüntüleme
 Eylemler bölmesi <xref:Microsoft.Office.Tools.ActionsPane> sınıfı tarafından temsil edilir. Belge düzeyinde bir proje oluşturduğunuzda, bu sınıfın bir örneği, projenizdeki `ThisWorkbook` (Excel için) veya `ThisDocument` (Word için) sınıfının `ActionsPane` alanı kullanılarak kodunuzda kullanılabilir. Eylemler bölmesini göstermek için `ActionsPane` alanının <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> özelliğine bir Windows Forms denetimi ekleyin. Aşağıdaki kod örneği, eylemler bölmesine `actions` adlı bir denetim ekler.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 Eylemler bölmesi, açıkça bir denetim eklediğiniz anda çalışma zamanında görünür hale gelir. Eylemler bölmesi görüntülendikten sonra, kullanıcı eylemlerine yanıt olarak denetimleri dinamik olarak ekleyebilir veya kaldırabilirsiniz. Genellikle, Eylemler bölmesini Kullanıcı belgeyi ilk açtığında eylemler bölmesinin görünür olması için `ThisDocument` veya `ThisWorkbook` `Startup` olay işleyicisine göstermek üzere kodu eklersiniz. Ancak, Eylemler bölmesini yalnızca bir kullanıcının belgedeki eylemine yanıt olarak göstermek isteyebilirsiniz. Örneğin, kodu belgedeki bir denetimin `Click` olayına ekleyebilirsiniz.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Eylemler bölmesine birden çok denetim ekleme
 Eylemler bölmesine birden çok denetim eklediğinizde, denetimleri bir kullanıcı denetiminde gruplandırmalı ve ardından Kullanıcı denetimini <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> özelliğine eklemelisiniz. Bu işlem aşağıdaki adımları içerir:

1. Projenize bir **Eylemler bölmesi denetimi** veya **Kullanıcı denetim** öğesi ekleyerek eylemler BÖLMESININ Kullanıcı arabirimini (UI) oluşturun. Bu öğelerin her ikisi de özel bir Windows Forms <xref:System.Windows.Forms.UserControl> sınıfı içerir. **Eylemler bölmesi denetimi** ve **Kullanıcı denetimi** öğeleri eşdeğerdir; Tek fark kendi adıdır.

2. Tasarımcıyı kullanarak veya kod yazarak <xref:System.Windows.Forms.UserControl> Windows Forms denetimleri ekleyin.

   > [!NOTE]
   > Ayrıca, Windows Forms <xref:System.Windows.Forms.UserControl>bir WPF <xref:System.Windows.Controls.UserControl> ekleyerek, eylemler bölmesine WPF denetimleri ekleyebilirsiniz. Daha fazla bilgi için bkz. [Office ÇÖZÜMLERINDE WPF denetimlerini kullanma](../vsto/using-wpf-controls-in-office-solutions.md).

3. Projenizdeki `ThisWorkbook` (Excel için) veya `ThisDocument` (Word için) sınıfının `ActionsPane` alanında bulunan denetimlere özel kullanıcı denetimi örneği ekleyin.

   Bu işlemi daha ayrıntılı olarak gösteren örnekler için bkz. [nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

## <a name="hide-the-actions-pane"></a>Eylemler bölmesini gizle
 <xref:Microsoft.Office.Tools.ActionsPane> sınıfında bir <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> yöntemi ve bir <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> özelliği olsa da, <xref:Microsoft.Office.Tools.ActionsPane> sınıfının herhangi bir üyesini kullanarak Eylemler bölmesini kullanıcı arabiriminden kaldıramazsınız. <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> yöntemi çağrılması veya <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> özelliğini **false** olarak ayarlamak yalnızca eylemler bölmesindeki denetimleri gizler; görev bölmesini gizlemez.

 Çözümünüzde görev bölmesini gizlemek için birkaç seçeneğiniz vardır:

- Word için, belge eylemleri görev bölmesini temsil eden <xref:Microsoft.Office.Interop.Word.TaskPane> nesnesinin <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> özelliğini **false**olarak ayarlayın. Aşağıdaki kod örneği, projenizdeki `ThisDocument` sınıfından çalıştırılmak üzere tasarlanmıştır.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- Excel için, <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> nesnesinin <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> özelliğini **false**olarak ayarlayın. Aşağıdaki kod örneği, projenizdeki `ThisWorkbook` sınıfından çalıştırılmak üzere tasarlanmıştır.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- Word veya Excel için, görev bölmesini temsil eden komut çubuğunun <xref:Microsoft.Office.Core.CommandBar.Visible%2A> özelliğini **yanlış**olarak ayarlayabilirsiniz. Aşağıdaki kod örneği, projenizdeki `ThisDocument` veya `ThisWorkbook` sınıfından çalıştırılmak üzere tasarlanmıştır.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Belge açıldığında Eylemler bölmesini temizle
 Eylemler bölmesi görünür durumdayken bir Kullanıcı belgeyi kaydettiğinde, Eylemler bölmesi her açıldığında görünür ve eylemler bölmesi herhangi bir denetim içerip içermediğini belirtir. Ne zaman göründüğünü denetlemek isterseniz, Eylemler bölmesinin belge açıldığında görünür olmamasını sağlamak için `ThisDocument` veya `ThisWorkbook` `Startup` olay işleyicisinde `ActionsPane` alanının <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> yöntemini çağırın.

### <a name="determine-when-the-actions-pane-is-closed"></a>Eylemler bölmesinin ne zaman kapatıldığını belirleme
 Eylemler bölmesi kapatıldığında harekete geçirilen bir olay yoktur. <xref:Microsoft.Office.Tools.ActionsPane> sınıfı <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> olayına sahip olsa da, Son Kullanıcı Eylemler bölmesini kapattığında bu olay oluşturulmaz. Bunun yerine, bu olay, Eylemler bölmesindeki denetimler <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> yöntemi çağırarak veya <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> özelliği **false**olarak ayarlanarak tetiklenir.

 Kullanıcı Eylemler bölmesini kapattığında, uygulamanın kullanıcı arabiriminde (UI) aşağıdaki yordamlardan birini gerçekleştirerek Kullanıcı onu yeniden görüntüleyebilir.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Word veya Excel Kullanıcı arabirimini kullanarak Eylemler bölmesini görüntüleme

1. Şeritte **Görünüm** sekmesine tıklayın.

2. **Göster/Gizle** grubunda, **belge eylemleri** iki durumlu düğmesine tıklayın.

## <a name="program-actions-pane-events"></a>Program eylemleri bölmesi olayları
 Eylemler bölmesine birden çok kullanıcı denetimi ekleyebilir ve ardından Kullanıcı denetimlerini göstererek ve gizleyerek belgedeki olaylara yanıt vermek için kod yazabilirsiniz. XML şema öğelerini belgenize eşlediğinizde, ekleme noktası XML öğelerinden birinin içinde olduğunda, Eylemler bölmesinde belirli kullanıcı denetimlerini gösterebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: şemaları Visual Studio Içindeki Word belgeleriyle eşleştirme](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) ve [nasıl yapılır: şemaları Visual Studio Içindeki çalışma sayfalarına eşleme](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 Ayrıca, konak denetimi, uygulama veya belge olayları dahil olmak üzere herhangi bir nesnenin olaylarına yanıt vermek için kod yazabilirsiniz. Daha fazla bilgi için bkz. [Walkthrough: bir NamedRange denetimindeki olaylara karşı](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)programlama.

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Eylemler bölmesindeki denetimlere veri bağlama
 Eylemler bölmesindeki denetimler Windows Forms denetimlerle aynı veri bağlama özelliklerine sahiptir. Denetimleri veri kümeleri, türü belirtilmiş veri kümeleri ve XML gibi veri kaynaklarına bağlayabilirsiniz. Daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Eylemler bölmesi ve belgedeki denetimlerde denetimleri aynı veri kümesine bağlayabilirsiniz. Örneğin, Eylemler bölmesindeki denetimler ve çalışma sayfasındaki denetimler arasında bir ana/ayrıntı ilişkisi oluşturabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

## <a name="validate-data-in-actions-pane-controls"></a>Eylemler bölmesi denetimlerinde verileri doğrulama
 Eylemler bölmesindeki bir denetimin <xref:System.Windows.Forms.Control.Validating> olay işleyicisinde bir ileti kutusu görüntülediğinizde, odak denetimden ileti kutusuna taşınışında olay ikinci kez ortaya çıkabilir. Bu sorunu engellemek için, herhangi bir doğrulama hata iletisini göstermek üzere bir <xref:System.Windows.Forms.ErrorProvider> denetimi kullanın.

## <a name="user-control-stacking-order"></a>Kullanıcı Denetimi yığınlama sırası
 Birden çok kullanıcı denetimi kullanıyorsanız, Eylemler bölmesindeki Kullanıcı Denetimlerini dikey veya yatay yerleştirilmiş olsun doğru bir şekilde yığmak için kod yazabilirsiniz. <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> özelliğinin <xref:Microsoft.Office.Tools.StackStyle> sabit listesini kullanarak, Eylemler bölmesinde kullanıcı denetimlerinin yığınlama sırasını ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> özelliği aşağıdaki <xref:Microsoft.Office.Tools.StackStyle> numaralandırma değerlerini alabilir.

|Yığınlama stili|Tanım|
|--------------------|----------------|
|FromBottom|Eylemler bölmesinin alt kısmından oluşan yığın.|
|FromLeft|Eylemler bölmesinin sol tarafındaki yığın.|
|FromRight|Eylemler bölmesinin sağ tarafındaki yığın.|
|FromTop|Eylemler bölmesinin en üstünden oluşan yığın.|
|Yok.|Yığın sıralaması tanımlı değil; sıra, geliştirici tarafından denetlenir.|

 Aşağıdaki kod, <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> özelliğini, Eylemler bölmesinin en üstünden kullanıcı denetimlerini yığmak üzere ayarlar.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Tutturucu denetimleri
 Kullanıcı, çalışma zamanında eylemler bölmesini yeniden boyutlandırırsa, denetimler Eylemler bölmesi ile yeniden boyutlandırılabilir. Denetimleri eylemler bölmesine bağlamak için bir Windows Forms denetiminin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini kullanabilirsiniz. Ayrıca, Windows Forms denetimlerini aynı şekilde Kullanıcı denetimine de bağlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimleri bağlama](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Eylemler bölmesini yeniden boyutlandır
 <xref:Microsoft.Office.Tools.ActionsPane> görev bölmesine katıştırıldığından, bir <xref:Microsoft.Office.Tools.ActionsPane> boyutunu doğrudan değiştiremezsiniz. Ancak, görev bölmesini temsil eden <xref:Microsoft.Office.Core.CommandBar> <xref:Microsoft.Office.Core.CommandBar.Width%2A> özelliğini ayarlayarak görev bölmesinin genişliğini programlı bir şekilde değiştirebilirsiniz. Görev bölmesinin yüksekliğini yatay olarak yuvalanmışsa veya kaydırılabiliyorsa değiştirebilirsiniz.

 Kullanıcı, ihtiyaçlarına en uygun görev bölmesi boyutunu seçebildiğinden, görev bölmesini programlı olarak yeniden boyutlandırma önerilmez. Ancak, görev bölmesinin genişliğini yeniden boyutlandırmanız gerekiyorsa, bu görevi gerçekleştirmek için aşağıdaki kodu kullanabilirsiniz.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Eylemler bölmesini yeniden Konumlandır
 Görev bölmesinde katıştırıldığından <xref:Microsoft.Office.Tools.ActionsPane> doğrudan yeniden konumlandırabilirsiniz. Ancak, görev bölmesini temsil eden <xref:Microsoft.Office.Core.CommandBar> <xref:Microsoft.Office.Core.CommandBar.Position%2A> özelliğini ayarlayarak görev bölmesini programlı bir şekilde taşıyabilirsiniz.

 Kullanıcının kendi ihtiyaçlarına en uygun ekranda görev bölmesi konumunu seçebilmesi gerektiğinden, görev bölmesini programlı bir şekilde yeniden konumlandırma önerilmez. Ancak, görev bölmesini belirli bir konuma taşımanız gerekiyorsa, bu görevi gerçekleştirmek için aşağıdaki kodu kullanabilirsiniz.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Son kullanıcılar, görev bölmesini dilediğiniz zaman el ile yeniden konumlandırabilirler. Görev bölmesinin programlama yoluyla gösterdiğiniz konuma yerleştirilmiş olarak kalmasını sağlamanın bir yolu yoktur. Ancak, yönlendirme değişikliklerini denetleyebilir ve Eylemler bölmesindeki denetimlerin doğru yönde yığıltığınızdan emin olabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 <xref:Microsoft.Office.Tools.ActionsPane> nesnesi görev bölmesine katıştırıldığından <xref:Microsoft.Office.Tools.ActionsPane> <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> ve <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> özelliklerinin ayarlanması konumunu değiştirmez.

 Görev bölmesi yerleştirilmemişse, görev bölmesini temsil eden <xref:Microsoft.Office.Core.CommandBar> <xref:Microsoft.Office.Core.CommandBar.Top%2A> ve <xref:Microsoft.Office.Core.CommandBar.Left%2A> özelliklerini ayarlayabilirsiniz. Aşağıdaki kod, yerleştirilmemiş bir görev bölmesini belgenin sol üst köşesine kaydırır.

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde WPF denetimlerini kullanma](../vsto/using-wpf-controls-in-office-solutions.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md)
- [Nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [İzlenecek yol: Word Eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [İzlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
