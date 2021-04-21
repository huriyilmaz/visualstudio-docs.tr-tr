---
title: 'İzlenecek yol: Word Eylemler bölmesindeki denetimlere veri bağlama'
description: Microsoft Word 'de bir eylemler bölmesindeki denetimlere veri bağlama. Denetimler SQL Server veritabanındaki tablolar arasında bir ana/ayrıntı ilişkisi gösterir.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d94891520695117c7a395f81feda81e52f909fe6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824503"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>İzlenecek yol: Word Eylemler bölmesindeki denetimlere veri bağlama
  Bu izlenecek yol, Word 'de bir eylemler bölmesindeki denetimlere veri bağlamayı gösterir. Denetimler SQL Server veritabanındaki tablolar arasında bir ana/ayrıntı ilişkisi gösterir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Verilere bağlanan Windows Forms denetimleriyle bir eylemler bölmesi oluşturma.

- Denetimlerde verileri göstermek için ana/ayrıntı ilişkisi kullanma.

- Uygulama açıldığında Eylemler bölmesini göster.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Northwind SQL Server örnek veritabanıyla bir sunucuya erişim.

- SQL Server veritabanına okuma ve yazma izinleri.

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Word belgesi projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Word eylemlerimi Adlandır bölmesiyle** bir Word belgesi projesi oluşturun. Sihirbazda **Yeni belge oluştur**' u seçin.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio, tasarımcıda yeni Word belgesini açar ve **Çözüm Gezgini** Için **My Word Actions Pane** projesini ekler.

## <a name="add-controls-to-the-actions-pane"></a>Eylemler bölmesine denetim ekleme
 Bu izlenecek yol için, veri bağlantılı Windows Forms denetimleri içeren bir eylemler bölmesi denetimine ihtiyacınız vardır. Projeye bir veri kaynağı ekleyin ve ardından **veri kaynakları** penceresinden denetimleri Eylemler bölmesi denetimine sürükleyin.

### <a name="to-add-an-actions-pane-control"></a>Eylemler bölmesi denetimi eklemek için

1. **Çözüm Gezgini**' de **My Word Actions Pane** projesini seçin.

2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

3. **Yeni öğe Ekle** iletişim kutusunda, **Eylemler bölmesi denetimi**' ni seçin, **ActionsControl** olarak adlandırın ve ardından **Ekle**' ye tıklayın.

### <a name="to-add-a-data-source-to-the-project"></a>Projeye bir veri kaynağı eklemek için

1. **Veri kaynakları** penceresi görünür değilse, menü çubuğunda,   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçerek bunu görüntüleyin.

   > [!NOTE]
   > **Veri kaynaklarını göster** yoksa, Word belgesine tıklayın ve sonra yeniden kontrol edin.

2. **Veri kaynağı Yapılandırma Sihirbazı 'nı** başlatmak Için **Yeni veri kaynağı Ekle** ' ye tıklayın.

3. **Veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

4. Northwind örnek SQL Server veritabanına yönelik bir veri bağlantısı seçin veya **Yeni bağlantı** düğmesini kullanarak yeni bir bağlantı ekleyin.

5. **İleri**’ye tıklayın.

6. Seçildiğinde bağlantıyı kaydetme seçeneğini temizleyin ve ardından **İleri**' ye tıklayın.

7. **Veritabanı nesneleri** penceresinde **Tablolar** düğümünü genişletin.

8. **Üreticiler** ve **Ürünler** tablolarının yanındaki onay kutusunu işaretleyin.

9. **Finish (Son)** düğmesine tıklayın.

   Sihirbaz, **tedarikçiler** tablosu ve **Ürünler** tablosunu **veri kaynakları** penceresine ekler. Ayrıca, projenize **Çözüm Gezgini** görünür bir veri kümesi de ekler.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Eylemler bölmesi denetimine veriye dayalı Windows Forms denetimleri eklemek için

1. **Veri kaynakları** penceresinde **Üreticiler** tablosunu genişletin.

2. **Şirket adı** düğümündeki açılan oka tıklayın ve **ComboBox**' ı seçin.

3. **CompanyName** **veri kaynakları** penceresinden eylemler bölmesi denetimine sürükleyin.

     <xref:System.Windows.Forms.ComboBox>Eylemler bölmesi denetiminde bir denetim oluşturulur. Aynı zamanda, bir <xref:System.Windows.Forms.BindingSource> adlandırılmış `SuppliersBindingSource` , bir tablo bağdaştırıcısı ve bir, bileşeni, <xref:System.Data.DataSet> bileşen tepsisinde projeye eklenir.

4. `SuppliersBindingNavigator` **Bileşen** tepsisinde öğesini seçin ve **Sil**'e basın. `SuppliersBindingNavigator`Bu izlenecek yolda kullanamazsınız.

    > [!NOTE]
    > Öğesinin silinmesi, `SuppliersBindingNavigator` kendisi için oluşturulan tüm kodu kaldırmaz. Bu kodu kaldırabilirsiniz.

5. Birleşik giriş kutusunu etiketin altında olacak şekilde taşıyın ve **size** özelliğini **171, 21** olarak değiştirin.

6. **Veri kaynakları** penceresinde, **Üreticiler** tablosunun bir alt öğesi olan **Ürünler** tablosunu genişletin.

7. **ProductName** düğümündeki açılan oka tıklayın ve **ListBox**' ı seçin.

8. **ProductName** öğesini eylemler bölmesi denetimine sürükleyin.

     <xref:System.Windows.Forms.ListBox>Eylemler bölmesi denetiminde bir denetim oluşturulur. Aynı zamanda, <xref:System.Windows.Forms.BindingSource> `ProductBindingSource` bileşen tepsisinde projeye adlandırılmış ve bir tablo bağdaştırıcısı eklenir.

9. Liste kutusunu etiketin altında olacak şekilde taşıyın ve **size** özelliğini **171, 95** olarak değiştirin.

10. <xref:System.Windows.Forms.Button> **Araç kutusundan** bir öğesini eylemler bölmesi denetimine sürükleyin ve liste kutusunun altına yerleştirin.

11. Öğesine sağ tıklayın <xref:System.Windows.Forms.Button> , kısayol menüsünde **Özellikler** ' e tıklayın ve aşağıdaki özellikleri değiştirin.

    |Özellik|Değer|
    |--------------|-----------|
    |**Ad**|**Ekle**|
    |**Metin**|**Ekle**|

12. Kullanıcı denetimini denetimlere sığacak şekilde yeniden boyutlandırın.

## <a name="set-up-the-data-source"></a>Veri kaynağını ayarlama
 Veri kaynağını ayarlamak için, <xref:System.Windows.Forms.UserControl.Load> Eylemler bölmesi denetiminin olayına kodu ekleyerek, denetimi içindeki verilerle doldurup, <xref:System.Data.DataTable> her bir <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> denetimin ve özelliklerini ayarlayın.

### <a name="to-load-the-control-with-data"></a>Denetimi verilerle yükleme

1. <xref:System.Windows.Forms.UserControl.Load>Sınıfının olay işleyicisinde `ActionsControl` aşağıdaki kodu ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet1":::

2. C# ' ta olay işleyicisini olaya bağlamanız gerekir <xref:System.Windows.Forms.UserControl.Load> . `ActionsControl`Çağrısından sonra bu kodu oluşturucuya yerleştirebilirsiniz `InitializeComponent` . Olay işleyicilerinin nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet33":::

### <a name="to-set-data-binding-properties-of-the-controls"></a>Denetimlerin veri bağlama özelliklerini ayarlamak için

1. Denetimi seçin `CompanyNameComboBox` .

2. **Özellikler** penceresinde **DataSource** özelliğinin sağındaki düğmesine tıklayın ve **suppliersBindingSource**' yi seçin.

3. **DisplayMember** özelliğinin sağ tarafındaki düğmeye tıklayın ve **CompanyName**' i seçin.

4. **DataBindings** özelliğini genişletin, **metin** özelliğinin sağ tarafındaki düğmeye tıklayın ve **hiçbiri**' ni seçin.

5. Denetimi seçin `ProductNameListBox` .

6. **Özellikler** penceresinde **DataSource** özelliğinin sağ tarafındaki düğmeye tıklayın ve **productsBindingSource**' u seçin.

7. **DisplayMember** özelliğinin sağ tarafındaki düğmeye tıklayın ve **ProductName**' i seçin.

8. **DataBindings** özelliğini genişletin, **SelectedValue** özelliğinin sağ tarafındaki düğmeye tıklayın ve **hiçbiri**' ni seçin.

## <a name="add-a-method-to-insert-data-into-a-table"></a>Tabloya veri eklemek için bir yöntem ekleme
 Sonraki görev, bağlantılı denetimlerden verileri okumaktır ve Word belgenizdeki bir tabloyu doldurur. İlk olarak, tablodaki başlıkları biçimlendirmek için bir yordam oluşturun ve sonra `AddData` bir Word tablosu oluşturmak ve biçimlendirmek için yöntemini ekleyin.

### <a name="to-format-the-table-headings"></a>Tablo başlıklarını biçimlendirmek için

1. `ActionsControl`Sınıfında, tablonun başlıklarını biçimlendirmek için bir yöntem oluşturun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet2":::

### <a name="to-create-the-table"></a>Tablo oluşturmak için

1. `ActionsControl`Sınıfında, zaten mevcut değilse tablo oluşturacak bir yöntem yazın ve Eylemler bölmesinden tabloya veri ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet3":::

### <a name="to-insert-text-into-a-word-table"></a>Bir Word tablosuna metin eklemek için

1. <xref:System.Windows.Forms.Control.Click> **Ekle** düğmesinin olay işleyicisine aşağıdaki kodu ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet4":::

2. C# ' de, düğme olayı için bir olay işleyicisi oluşturmanız gerekir <xref:System.Windows.Forms.Control.Click> .  Bu kodu, <xref:System.Windows.Forms.UserControl.Load> sınıfının olay işleyicisine yerleştirebilirsiniz `ActionsControl` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet5":::

## <a name="show-the-actions-pane"></a>Eylemler bölmesini göster
 Eylemler bölmesi denetim eklendikten sonra görünür hale gelir.

### <a name="to-show-the-actions-pane"></a>Eylemler bölmesini göstermek için

1. **Çözüm Gezgini**' de, **ThisDocument. vb** veya **ThisDocument. cs**' ye sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.

2. Aşağıdaki örneğe benzer şekilde görünmesi için sınıfın en üstünde denetimin yeni bir örneğini oluşturun `ThisDocument` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet6":::

3. <xref:Microsoft.Office.Tools.Word.Document.Startup> `ThisDocument` Aşağıdaki örneğe benzer şekilde görünmesi için olay işleyicisine kod ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet7":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık belge açıldığında eylemler bölmesinin göründüğünü doğrulamak için belgenizi test edebilirsiniz. Eylemler bölmesindeki denetimlerde ana/ayrıntı ilişkisini test edin ve **Ekle** düğmesine tıklandığında verilerin bir Word tablosunda doldurulduğundan emin olun.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Eylemler bölmesinin görünür olduğunu onaylayın.

3. Birleşik giriş kutusunda bir şirket seçin ve **Ürünler** liste kutusundaki öğelerin değiştiğini doğrulayın.

4. Bir ürün seçin, Eylemler bölmesinde **Ekle** ' ye tıklayın ve ürün ayrıntılarının Word 'deki tabloya eklendiğini doğrulayın.

5. Çeşitli şirketlerin ek ürünlerini ekleyin.

## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuzda, Word 'de bir eylemler bölmesindeki denetimlere veri bağlamanın temelleri gösterilmektedir. Daha sonra gelebilecek bazı görevler şunlardır:

- Excel 'de denetimlere veri bağlama. Daha fazla bilgi için bkz. [Izlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

- Projeyi dağıtma. Daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
