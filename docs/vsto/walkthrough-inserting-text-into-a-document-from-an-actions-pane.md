---
title: 'Adım adım kılavuz: Eylemler bölmesinden belgeye metin ekleme'
description: Yeni bir belgede eylemler Microsoft Word oluşturun. Eylemler bölmesinde girişi toplayan ve sonra belgeye metin gönderen iki denetim olduğunu öğrenin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 071f447e8f32d53feef912b6c804af27fe69aa1e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725544"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Adım adım kılavuz: Eylemler bölmesinden belgeye metin ekleme
  Bu kılavuzda, Word belgesinde eylemler bölmesinin nasıl Microsoft Office gösterilir. Eylemler bölmesi, girişi toplayan ve sonra belgeye metin göndermek için iki denetim içerir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Eylemler bölmesi denetiminde Windows Forms denetimlerini kullanarak arabirim tasarlar.

- Uygulama açıldığında eylemler bölmesini görüntüleyin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Word Belgesi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. Temel Eylemlerim Bölmesi adıyla **bir Word Belgesi projesi oluşturun.** Sihirbazda Yeni belge **oluştur'a tıklayın.** Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     Visual Studio yeni Word belgesini tasarımcıda açar ve Temel Eylemlerim Bölmesi **projesini** **Çözüm Gezgini.**

## <a name="add-text-and-bookmarks-to-the-document"></a>Belgeye metin ve yer işaretleri ekleme
 Eylemler bölmesi belgede yer işaretlerine metin gönderir. Belgeyi tasarlamak için bazı metinler yazarak temel bir form oluşturun.

### <a name="to-add-text-to-your-document"></a>Belgenize metin eklemek için

1. Word belgenize aşağıdaki metni yazın:

    **21 Mart 2008**

    **Ad**

    **Adres**

    **Bu, Word'de temel eylemler bölmesine bir örnektir.**

   Belgenize, belgenizin Araç Kutusundan sürükleyerek veya Word'Visual Studio Yer İşareti <xref:Microsoft.Office.Tools.Word.Bookmark> **iletişim** kutusunu kullanarak bir denetim ekleyebilirsiniz. 

### <a name="to-add-a-bookmark-control-to-your-document"></a>Belgenize Yer İşareti denetimi eklemek için

1. Araç **Kutusunun Sözcük Denetimleri** **sekmesinden,** bir denetimi <xref:Microsoft.Office.Tools.Word.Bookmark> belgenize sürükleyin.

     Yer **İşareti Denetimi Ekle** iletişim kutusu görüntülenir.

2. Paragraf işaretini **seçmeden** Ad sözcüğüne tıklayın ve Tamam'a **tıklayın.**

    > [!NOTE]
    > Paragraf işaretinin yer işaretinin dışında olması gerekir. Belgede paragraf işaretleri görünmüyorsa Araçlar menüsüne tıklayın, **Word** **Araçları'nın** üzerine gelin Microsoft Office seçenekler'e **tıklayın.** Görünüm **sekmesine** tıklayın ve Seçenekler **iletişim kutusunun** Biçimlendirme işaretleri **bölümünde Paragraf** işaretleri **onay** kutusunu seçin.

3. Özellikler penceresinde **Bookmark1'in** **Name** özelliğini **showName olarak değiştirin.** 

4. Paragraf işaretini **seçmeden** Adres sözcüklerini seçin.

5. Şeridin **Ekle** sekmesindeki Bağlantılar grubunda Yer **İşareti'ne** **tıklayın.**

6. Yer **İşareti** iletişim kutusunda Yer İşareti **Adı kutusuna showAddress** **yazın ve** Ekle'ye **tıklayın.**

## <a name="add-controls-to-the-actions-pane"></a>Eylemler bölmesine denetimler ekleme
 Eylemler bölmesi arabirimini tasarlamak için projeye bir eylemler bölmesi denetimi ekleyin ve Windows Forms denetimlerini eylemler bölmesi denetimine ekleyin.

### <a name="to-add-an-actions-pane-control"></a>Eylemler bölmesi denetimi eklemek için

1. içinde **Temel Eylemlerim Bölmesi** projesini **Çözüm Gezgini.**

2. Yeni **Project** **Ekle'ye tıklayın.**

3. Yeni Öğe **Ekle iletişim kutusunda** Eylemler Bölmesi Denetimi'ne tıklayın, denetimi **InsertTextControl** olarak ve Ekle'ye **tıklayın.** 

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Eylemler bölmesi Windows Form denetimleri eklemek için

1. Eylemler bölmesi denetimi tasarımcıda görünmüyorsa **InsertTextControl'e çift tıklayın.**

2. Araç **Kutusunun Ortak** Denetimler **sekmesinden bir** **Etiket denetimi** sürükleyerek eylemler bölmesi denetimine sürükleyin.

3. Etiket **denetiminde Text** özelliğini Name olarak **değiştirme.**

4. Eylemler **bölmesi denetimine** bir Metin Kutusu denetimi ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**getName**|
    |**Boyut**|**130, 20**|

5. Eylemler bölmesi **denetimine** ikinci bir Etiket denetimi ekleyin ve Text özelliğini **Address** olarak **değiştirebilirsiniz.**

6. Eylemler bölmesi **denetimine ikinci** bir Metin Kutusu denetimi ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**getAddress**|
    |**Dönüş Kabul Eder**|**True**|
    |**Multiline**|**True**|
    |**Boyut**|**130, 40**|

7. Eylemler **bölmesi** denetimine bir Düğme denetimi ekleyin ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**addText**|
    |**Metin**|**Ekle**|

## <a name="add-code-to-insert-text-into-the-document"></a>Belgeye metin eklemek için kod ekleme
 Eylemler bölmesinde, metin kutularından belgede uygun denetimlere metin ekli <xref:Microsoft.Office.Tools.Word.Bookmark> kod yazın. Eylemler bölmesindeki `Globals` denetimlerden belge üzerinde denetimlere erişmek için sınıfını kullanabilirsiniz. Daha fazla bilgi için [bkz. Office projelerinde nesnelere genel erişim.](../vsto/global-access-to-objects-in-office-projects.md)

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Eylemler bölmesinden belgede yer işaretine metin eklemek için

1. AddText düğmesinin <xref:System.Windows.Forms.Control.Click> olay işleyicisi için **aşağıdaki kodu** ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb" id="Snippet8":::

2. C# içinde, düğme tıklaması için bir olay işleyicisi eklemeniz gerekir. Bu kodu çağrısının ardından `InsertTextControl` oluşturucuya yer veebilirsiniz. `InitializeComponent` Olay işleyicileri oluşturma hakkında daha fazla bilgi için [bkz. Nasıl oluşturulur: Office projelerinde olay işleyicileri oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet9":::

## <a name="add-code-to-show-the-actions-pane"></a>Eylemler bölmesini göstermek için kod ekleme
 Eylemler bölmesini göstermek için, oluşturduğunuz denetimi denetim koleksiyonuna ekleyin.

### <a name="to-show-the-actions-pane"></a>Eylemler bölmesini göstermek için

1. sınıfında eylemler bölmesi denetimi için yeni bir örnek `ThisDocument` oluşturun.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet10":::

2. Aşağıdaki kodu olay <xref:Microsoft.Office.Tools.Word.Document.Startup> işleyicisi'ne `ThisDocument` ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet11":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Belge açıldığında eylemler bölmesinin açıldığından ve düğmeye tıkıldığında metin kutularına yazılmış metnin yer işaretlerine ekli olduğunu doğrulamak için belgenizi test edin.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. Eylemler bölmesinin görünür olduğunu onaylayın.

3. Eylemler bölmesindeki metin kutularına adınız ve adresinizi yazın ve Ekle'ye **tıklayın.**

## <a name="next-steps"></a>Sonraki adımlar
 Bir sonraki görevlerden bazıları:

- Excel'da bir eylemler bölmesi oluşturun. Daha fazla bilgi için [bkz. Nasıl musunuz: Çalışma kitaplarını Excel bölmesi ekleme.](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))

- Eylemler bölmesindeki denetimlere veri bağlama. Daha fazla bilgi için [bkz. Adım adım: Word eylemleri bölmesindeki denetimlere veri bağlama.](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Nasıl kullanılır: Word belgelerine veya çalışma kitaplarını Excel bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Nasıl Excel: Çalışma kitaplarını Excel ekleme](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Nasıl gösterilir: Eylemler bölmeleri üzerinde denetim düzenini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Yer işareti denetimi](../vsto/bookmark-control.md)
