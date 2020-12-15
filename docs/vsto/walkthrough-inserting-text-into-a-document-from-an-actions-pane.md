---
title: 'İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme'
description: Bir Microsoft Word belgesinde bir eylemler bölmesi oluşturun. Eylemler bölmesinin girişi toplayıp belgeyi belgeye gönderdiğini iki denetim içerdiğini öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 44fd876dfad99e1a1320a5e5d743ea8e30dfdb98
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524162"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>İzlenecek yol: Eylemler bölmesinden belgeye metin ekleme
  Bu izlenecek yol, bir Microsoft Office Word belgesinde bir eylemler bölmesinin nasıl oluşturulacağını göstermektedir. Eylemler bölmesi girişi toplayıp metni belgeye gönderen iki denetim içerir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Eylemler bölmesi denetiminde Windows Forms denetimleri kullanarak bir arabirim tasarlayın.

- Uygulama açıldığında Eylemler bölmesini görüntüleyin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Word belgesi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Temel eylemler Bölmesimi** Içeren bir Word belgesi projesi oluşturun. Sihirbazda **Yeni belge oluştur**' u seçin. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Word belgesini açar ve **temel eylemler bölmesi** projesini **Çözüm Gezgini** ekler.

## <a name="add-text-and-bookmarks-to-the-document"></a>Belgeye metin ve yer işaretleri ekleme
 Eylemler bölmesi belgedeki yer işaretlerine metin gönderir. Belgeyi tasarlamak için, temel form oluşturmak üzere bir metin yazın.

### <a name="to-add-text-to-your-document"></a>Belgenize metin eklemek için

1. Word belgenize aşağıdaki metni yazın:

    **21 Mart 2008**

    **Ad**

    **Adres**

    **Bu, Word 'deki temel eylemler bölmesine bir örnektir.**

   <xref:Microsoft.Office.Tools.Word.Bookmark>Belgenize, Visual Studio 'Daki **araç kutusundan** sürükleyerek veya Word 'deki **yer işareti** iletişim kutusunu kullanarak bir denetim ekleyebilirsiniz.

### <a name="to-add-a-bookmark-control-to-your-document"></a>Belgenize bir yer Işareti denetimi eklemek için

1. **Araç kutusunun** **Word denetimleri** sekmesinden <xref:Microsoft.Office.Tools.Word.Bookmark> belgenize bir denetim sürükleyin.

     **Yer Işareti denetimi Ekle** iletişim kutusu görünür.

2. Paragraf işaretini seçmeden bir sözcük **adı** seçin ve **Tamam**' ı tıklatın.

    > [!NOTE]
    > Paragraf işareti, yer işaretinin dışında olmalıdır. Paragraf işaretleri belgede görünmüyorsa, **Araçlar** menüsüne tıklayın, **Microsoft Office Word araçları** ' nın üzerine gelin ve ardından **Seçenekler**' e tıklayın. **Görünüm** sekmesine tıklayın ve **Seçenekler** iletişim kutusunun **Biçimlendirme işaretleri** bölümündeki **paragraf işaretleri** onay kutusunu seçin.

3. **Özellikler** penceresinde, **Bookmark1** öğesinin **Name** özelliğini **ShowName** olarak değiştirin.

4. Paragraf işaretini seçmeden, sözcük **adresini** seçin.

5. Şeridin **Ekle** sekmesinde, **Bağlantılar** grubunda **yer işareti**' ne tıklayın.

6. **Yer işareti** iletişim kutusunda, **yer Işareti adı** kutusuna **showAddress** yazın ve **Ekle**' ye tıklayın.

## <a name="add-controls-to-the-actions-pane"></a>Eylemler bölmesine denetim ekleme
 Eylemler bölmesi arabirimini tasarlamak için projeye bir eylemler bölmesi denetimi ekleyin ve sonra Eylemler bölmesi denetimine Windows Forms denetimleri ekleyin.

### <a name="to-add-an-actions-pane-control"></a>Eylemler bölmesi denetimi eklemek için

1. **Çözüm Gezgini** Içinde **temel eylemler bölmesi** projesini seçin.

2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

3. **Yeni öğe Ekle** iletişim kutusunda, **Eylemler bölmesi denetimi**' ne tıklayın, denetimi **InsertTextControl olarak** adlandırın ve **Ekle**' ye tıklayın.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Eylemler bölmesi denetimine Windows form denetimleri eklemek için

1. Eylemler bölmesi denetimi tasarımcıda görünür değilse, **InsertTextControl** öğesine çift tıklayın.

2. **Araç kutusunun** **ortak denetimler** sekmesinden, bir **etiket** denetimini eylemler bölmesi denetimine sürükleyin.

3. Etiket denetiminin **Text** özelliğini **Name** olarak değiştirin.

4. Eylemler bölmesi denetimine bir **TextBox** denetimi ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**getName**|
    |**Boyut**|**130, 20**|

5. Eylemler bölmesi denetimine ikinci bir **etiket** denetimi ekleyin ve **Text** özelliğini **Address** olarak değiştirin.

6. Eylemler bölmesi denetimine ikinci bir **TextBox** denetimi ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**getAddress**|
    |**Dönüşü kabul eder**|**True**|
    |**Multiline**|**True**|
    |**Boyut**|**130, 40**|

7. Eylemler bölmesi denetimine bir **düğme** denetimi ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**addText**|
    |**Metin**|**Ekle**|

## <a name="add-code-to-insert-text-into-the-document"></a>Belgeye metin eklemek için kod ekleme
 Eylemler bölmesinde metin kutularından metni belgedeki uygun denetimlere ekleyen kodu yazın <xref:Microsoft.Office.Tools.Word.Bookmark> . Bu `Globals` sınıfı, Eylemler bölmesindeki denetimlerden belgedeki denetimlere erişmek için kullanabilirsiniz. Daha fazla bilgi için bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Belgedeki bir yer işaretine Eylemler bölmesinden metin eklemek için

1. <xref:System.Windows.Forms.Control.Click> **AddText** düğmesinin olay işleyicisine aşağıdaki kodu ekleyin.

     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]

2. C# ' de, düğme tıklayı için bir olay işleyicisi eklemeniz gerekir. `InsertTextControl`Çağrısından sonra bu kodu oluşturucuya yerleştirebilirsiniz `InitializeComponent` . Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]

## <a name="add-code-to-show-the-actions-pane"></a>Eylemler bölmesini göstermek için kod ekleme
 Eylemler bölmesini göstermek için, oluşturduğunuz denetimi denetim koleksiyonuna ekleyin.

### <a name="to-show-the-actions-pane"></a>Eylemler bölmesini göstermek için

1. Sınıfında eylemler bölmesi denetiminin yeni bir örneğini oluşturun `ThisDocument` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]

2. Olay işleyicisine aşağıdaki kodu ekleyin <xref:Microsoft.Office.Tools.Word.Document.Startup> `ThisDocument` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]

## <a name="test-the-application"></a>Uygulamayı test etme
 Belge açıldığında eylemler bölmesinin açıldığını ve düğme tıklandığında metin kutularına yazılan metinlerin yer işaretlerine eklendiğini doğrulamak için belgenizi test edin.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Eylemler bölmesinin görünür olduğunu onaylayın.

3. Eylemler bölmesindeki metin kutularına adınızı ve adresinizi yazın ve **Ekle**' ye tıklayın.

## <a name="next-steps"></a>Sonraki adımlar
 Daha sonra gelebilecek bazı görevler şunlardır:

- Excel 'de bir eylemler bölmesi oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Excel çalışma kitaplarına eylemler bölmesi ekleme](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).

- Eylemler bölmesindeki denetimlere veri bağlama. Daha fazla bilgi için bkz. [Izlenecek yol: Word Eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Nasıl yapılır: Excel çalışma kitaplarına eylemler bölmesi ekleme](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Yer işareti denetimi](../vsto/bookmark-control.md)
