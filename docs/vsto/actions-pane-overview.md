---
title: Eylemler bölmesine genel bakış
description: Bir eylemler bölmesinin, belirli bir Microsoft Office Word belgesi veya Excel çalışma kitabına eklenen özelleştirilebilir bir belge eylemleri görev bölmesi olduğunu öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9579de6712b742dde1f9b399ca8a1e4598783679
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896771"
---
# <a name="actions-pane-overview"></a>Eylemler bölmesine genel bakış
  Bir eylemler bölmesi, belirli bir Microsoft Office Word belgesine veya Microsoft Office Excel çalışma kitabına eklenen özelleştirilebilir bir **belge eylemleri** görev bölmesidir. Eylemler bölmesi Office görev bölmesinin içinde, Excel 'deki **XML kaynağı** görev bölmesi veya Word 'deki **Stiller ve biçimlendirme** görev bölmesi gibi diğer yerleşik görev bölmeleri ile birlikte barındırılır. Eylemler bölmesi Kullanıcı arabirimini tasarlamak için Windows Forms denetimleri veya WPF denetimleri kullanabilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Yalnızca Word veya Excel için belge düzeyi özelleştirmesindeki bir eylemler bölmesi oluşturabilirsiniz. Bir VSTO eklentisi içinde bir eylemler bölmesi oluşturamazsınız. Daha fazla bilgi için bkz. [Office uygulaması ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Eylemler bölmesi özel görev bölmeleriyle farklılık gösterir. Özel görev bölmeleri, belirli bir belge değil uygulamayla ilişkilendirilir. Bazı Microsoft Office uygulamaları için VSTO eklentilerinde özel görev bölmeleri oluşturabilirsiniz. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="display-the-actions-pane"></a>Eylemler bölmesini görüntüleme
 Eylemler bölmesi sınıfı tarafından temsil edilir <xref:Microsoft.Office.Tools.ActionsPane> . Belge düzeyinde bir proje oluşturduğunuzda, bu sınıfın bir örneği, `ActionsPane` `ThisWorkbook` projenizdeki (Excel için) veya `ThisDocument` (Word için) sınıfının alanı kullanılarak kodunuzda kullanılabilir. Eylemler bölmesini göstermek için alanın özelliğine bir Windows Forms denetimi ekleyin <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ActionsPane` . Aşağıdaki kod örneği, eylemler bölmesine adlı bir denetim ekler `actions` .

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 Eylemler bölmesi, açıkça bir denetim eklediğiniz anda çalışma zamanında görünür hale gelir. Eylemler bölmesi görüntülendikten sonra, kullanıcı eylemlerine yanıt olarak denetimleri dinamik olarak ekleyebilir veya kaldırabilirsiniz. Genellikle, ' ın olay işleyicisinde Eylemler bölmesini göstermek için kodu eklersiniz, `Startup` `ThisDocument` `ThisWorkbook` böylece Kullanıcı belgeyi ilk açtığında eylemler bölmesi görünür olur. Ancak, Eylemler bölmesini yalnızca bir kullanıcının belgedeki eylemine yanıt olarak göstermek isteyebilirsiniz. Örneğin, kodu `Click` belgedeki bir denetimin olayına ekleyebilirsiniz.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Eylemler bölmesine birden çok denetim ekleme
 Eylemler bölmesine birden çok denetim eklediğinizde, denetimleri bir kullanıcı denetiminde gruplandırmalı ve ardından Kullanıcı denetimini bu <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> özelliğe eklemelisiniz. Bu işlem aşağıdaki adımları içerir:

1. Projenize bir **Eylemler bölmesi denetimi** veya **Kullanıcı denetim** öğesi ekleyerek eylemler BÖLMESININ Kullanıcı arabirimini (UI) oluşturun. Bu öğelerin her ikisi de özel bir Windows Forms <xref:System.Windows.Forms.UserControl> sınıfı içerir. **Eylemler bölmesi denetimi** ve **Kullanıcı denetimi** öğeleri eşdeğerdir; Tek fark kendi adıdır.

2. <xref:System.Windows.Forms.UserControl>Tasarımcı kullanarak veya kod yazarak öğesine Windows Forms denetimleri ekleyin.

   > [!NOTE]
   > Ayrıca, Windows Forms bir WPF ekleyerek, eylemler bölmesine WPF denetimleri ekleyebilirsiniz <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Forms.UserControl> . Daha fazla bilgi için bkz. [Office ÇÖZÜMLERINDE WPF denetimlerini kullanma](../vsto/using-wpf-controls-in-office-solutions.md).

3. `ActionsPane` `ThisWorkbook` Projenizdeki (Excel için) veya `ThisDocument` (Word için) sınıfının alanında bulunan denetimlere özel kullanıcı denetimi örneği ekleyin.

   Bu işlemi daha ayrıntılı olarak gösteren örnekler için bkz. [nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

## <a name="hide-the-actions-pane"></a>Eylemler bölmesini gizle
 <xref:Microsoft.Office.Tools.ActionsPane>Sınıfında bir <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> yöntemi ve bir özelliği olsa da <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> , bir sınıfın herhangi bir üyesini kullanarak Eylemler bölmesini kullanıcı arabiriminden kaldıramazsınız <xref:Microsoft.Office.Tools.ActionsPane> . Yöntemi çağırmak <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> veya <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> özelliği **false** olarak ayarlamak yalnızca eylemler bölmesindeki denetimleri gizler; görev bölmesini gizlemez.

 Çözümünüzde görev bölmesini gizlemek için birkaç seçeneğiniz vardır:

- Word için, <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> <xref:Microsoft.Office.Interop.Word.TaskPane> belge eylemleri görev bölmesini temsil eden nesnenin özelliğini **false** olarak ayarlayın. Aşağıdaki kod örneği, projenizdeki sınıfından çalıştırılmak üzere tasarlanmıştır `ThisDocument` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- Excel için <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> nesnesinin özelliğini **false** olarak ayarlayın. Aşağıdaki kod örneği, projenizdeki sınıfından çalıştırılmak üzere tasarlanmıştır `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- Word veya Excel için, <xref:Microsoft.Office.Core.CommandBar.Visible%2A> görev bölmesini gösteren komut çubuğunun özelliğini **yanlış** olarak ayarlayabilirsiniz. Aşağıdaki kod örneği, `ThisDocument` projenizdeki veya sınıfından çalıştırılmak üzere tasarlanmıştır `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Belge açıldığında Eylemler bölmesini temizle
 Eylemler bölmesi görünür durumdayken bir Kullanıcı belgeyi kaydettiğinde, Eylemler bölmesi her açıldığında görünür ve eylemler bölmesi herhangi bir denetim içerip içermediğini belirtir. Ne zaman göründüğünü denetlemek isterseniz, ' <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> `ActionsPane` `Startup` ın olay işleyicisinde alanın yöntemini çağırın `ThisDocument` ve `ThisWorkbook` belge açıldığında eylemler bölmesinin görünür olmamasını sağlayın.

### <a name="determine-when-the-actions-pane-is-closed"></a>Eylemler bölmesinin ne zaman kapatıldığını belirleme
 Eylemler bölmesi kapatıldığında harekete geçirilen bir olay yoktur. <xref:Microsoft.Office.Tools.ActionsPane>Sınıfında bir olay olsa da <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> , Son Kullanıcı Eylemler bölmesini kapattığında bu olay oluşturulmaz. Bunun yerine, bu olay, Eylemler bölmesindeki denetimler, <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> yöntemi çağırarak veya <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> özelliği **false** olarak ayarlanarak tetiklenir.

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
 <xref:System.Windows.Forms.Control.Validating>Eylemler bölmesindeki bir denetimin olay işleyicisinde bir ileti kutusu görürseniz, odak denetimden ileti kutusuna taşınışında olay ikinci kez ortaya çıkabilir. Bu sorunu engellemek için <xref:System.Windows.Forms.ErrorProvider> doğrulama hata iletilerini göstermek üzere bir denetim kullanın.

## <a name="user-control-stacking-order"></a>Kullanıcı Denetimi yığınlama sırası
 Birden çok kullanıcı denetimi kullanıyorsanız, Eylemler bölmesindeki Kullanıcı Denetimlerini dikey veya yatay yerleştirilmiş olsun doğru bir şekilde yığmak için kod yazabilirsiniz. Özellik numaralandırmasını kullanarak, Eylemler bölmesindeki Kullanıcı denetimlerinin yığınlama sırasını ayarlayabilirsiniz <xref:Microsoft.Office.Tools.StackStyle> <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>Özelliği aşağıdaki <xref:Microsoft.Office.Tools.StackStyle> numaralandırma değerlerini alabilir.

|Yığınlama stili|Tanım|
|--------------------|----------------|
|FromBottom|Eylemler bölmesinin alt kısmından oluşan yığın.|
|FromLeft|Eylemler bölmesinin sol tarafındaki yığın.|
|FromRight|Eylemler bölmesinin sağ tarafındaki yığın.|
|FromTop|Eylemler bölmesinin en üstünden oluşan yığın.|
|Yok|Yığın sıralaması tanımlı değil; sıra, geliştirici tarafından denetlenir.|

 Aşağıdaki kod, <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> Kullanıcı denetimlerini eylemler bölmesinin en üstünden yığmak için özelliğini ayarlar.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Tutturucu denetimleri
 Kullanıcı, çalışma zamanında eylemler bölmesini yeniden boyutlandırırsa, denetimler Eylemler bölmesi ile yeniden boyutlandırılabilir. <xref:System.Windows.Forms.Control.Anchor%2A>Denetimleri eylemler bölmesine bağlamak için bir Windows Forms denetiminin özelliğini kullanabilirsiniz. Ayrıca, Windows Forms denetimlerini aynı şekilde Kullanıcı denetimine de bağlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetimleri bağlama](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Eylemler bölmesini yeniden boyutlandır
 <xref:Microsoft.Office.Tools.ActionsPane>Görev bölmesinde gömülü olduğundan, bir öğesinin boyutunu doğrudan değiştiremezsiniz <xref:Microsoft.Office.Tools.ActionsPane> . Ancak <xref:Microsoft.Office.Core.CommandBar.Width%2A> görev bölmesini temsil eden öğesinin özelliğini ayarlayarak görev bölmesinin genişliğini programlı bir şekilde değiştirebilirsiniz <xref:Microsoft.Office.Core.CommandBar> . Görev bölmesinin yüksekliğini yatay olarak yuvalanmışsa veya kaydırılabiliyorsa değiştirebilirsiniz.

 Kullanıcı, ihtiyaçlarına en uygun görev bölmesi boyutunu seçebildiğinden, görev bölmesini programlı olarak yeniden boyutlandırma önerilmez. Ancak, görev bölmesinin genişliğini yeniden boyutlandırmanız gerekiyorsa, bu görevi gerçekleştirmek için aşağıdaki kodu kullanabilirsiniz.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Eylemler bölmesini yeniden Konumlandır
 Görev bölmesinde katıştırıldığından, doğrudan yeniden konumlandırılamaz <xref:Microsoft.Office.Tools.ActionsPane> . Bununla birlikte, görev bölmesini <xref:Microsoft.Office.Core.CommandBar.Position%2A> temsil eden öğesinin özelliğini ayarlayarak görev bölmesini programlı bir şekilde taşıyabilirsiniz <xref:Microsoft.Office.Core.CommandBar> .

 Kullanıcının kendi ihtiyaçlarına en uygun ekranda görev bölmesi konumunu seçebilmesi gerektiğinden, görev bölmesini programlı bir şekilde yeniden konumlandırma önerilmez. Ancak, görev bölmesini belirli bir konuma taşımanız gerekiyorsa, bu görevi gerçekleştirmek için aşağıdaki kodu kullanabilirsiniz.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Son kullanıcılar, görev bölmesini dilediğiniz zaman el ile yeniden konumlandırabilirler. Görev bölmesinin programlama yoluyla gösterdiğiniz konuma yerleştirilmiş olarak kalmasını sağlamanın bir yolu yoktur. Ancak, yönlendirme değişikliklerini denetleyebilir ve Eylemler bölmesindeki denetimlerin doğru yönde yığıltığınızdan emin olabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 <xref:Microsoft.Office.Tools.ActionsPane.Top%2A>Nesnesinin ve özelliklerinin ayarlanması, <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> <xref:Microsoft.Office.Tools.ActionsPane> <xref:Microsoft.Office.Tools.ActionsPane> nesne görev bölmesine katıştırıldığından konumunu değiştirmez.

 Görev bölmesi yerleştirilmemişse, <xref:Microsoft.Office.Core.CommandBar.Top%2A> <xref:Microsoft.Office.Core.CommandBar.Left%2A> <xref:Microsoft.Office.Core.CommandBar> görev bölmesini temsil eden öğesinin ve özelliklerini ayarlayabilirsiniz. Aşağıdaki kod, yerleştirilmemiş bir görev bölmesini belgenin sol üst köşesine kaydırır.

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
