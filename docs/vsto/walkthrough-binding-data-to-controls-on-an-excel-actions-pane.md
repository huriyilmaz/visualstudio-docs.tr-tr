---
title: 'İzlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama'
description: Microsoft Excel 'de bir eylemler bölmesindeki denetimlere veri bağlama. Denetimler SQL Server veritabanındaki tablolar arasında bir ana/ayrıntı ilişkisi gösterir.
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
ms.openlocfilehash: 377c3405211c91712f8754131d8379c3dae7e820
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824555"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>İzlenecek yol: Excel eylemler bölmesindeki denetimlere veri bağlama
  Bu izlenecek yol, Excel Microsoft Office bir eylemler bölmesindeki denetimlere veri bağlamayı gösterir. Denetimler SQL Server veritabanındaki tablolar arasında bir ana/ayrıntı ilişkisi gösterir.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma sayfasına denetimler ekleme.

- Eylemler bölmesi denetimi oluşturma.

- Eylemler bölmesi denetimine veriye dayalı Windows Forms denetimleri ekleme.

- Uygulama açıldığında eylemler bölmesi gösteriliyor.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Northwind SQL Server örnek veritabanıyla bir sunucuya erişim.

- SQL Server veritabanına okuma ve yazma izinleri.

## <a name="create-the-project"></a>Proje oluşturma
 İlk adım bir Excel çalışma kitabı projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Excel eylemlerimi Adlandır bölmesiyle** bir Excel çalışma kitabı projesi oluşturun. Sihirbazda **Yeni belge oluştur**' u seçin. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **Çözüm Gezgini** Için **Excel eylemler bölmesi** projesini ekler.

## <a name="add-a-new-data-source-to-the-project"></a>Projeye yeni bir veri kaynağı ekleyin

### <a name="to-add-a-new-data-source-to-the-project"></a>Projeye yeni bir veri kaynağı eklemek için

1. **Veri kaynakları** penceresi görünür değilse, menü çubuğunda,   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçerek bunu görüntüleyin.

2. **Veri kaynağı Yapılandırma Sihirbazı 'nı** başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

4. Northwind örnek SQL Server veritabanına yönelik bir veri bağlantısı seçin veya **Yeni bağlantı** düğmesini kullanarak yeni bir bağlantı ekleyin.

5. **İleri**’ye tıklayın.

6. Seçildiğinde bağlantıyı kaydetme seçeneğini temizleyin ve ardından **İleri**' ye tıklayın.

7. **Veritabanı nesneleri** penceresinde **Tablolar** düğümünü genişletin.

8. **Üreticiler** tablosunun yanındaki onay kutusunu işaretleyin.

9. **Products** tablosunu genişletin ve **ProductName**, **SupplierID**, **quantityPerUnit** ve **BirimFiyat**' ı seçin.

10. **Finish (Son)** düğmesine tıklayın.

    Sihirbaz, **tedarikçiler** tablosu ve **Ürünler** tablosunu **veri kaynakları** penceresine ekler. Ayrıca, projenize **Çözüm Gezgini** görünür bir veri kümesi de ekler.

## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme
 Sonra, <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> ilk çalışma sayfasına bir denetim ve denetim ekleyin.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>NamedRange denetimi ve ListObject denetimi eklemek için

1. **Excel eylemlerim Pane.xlsx** çalışma kitabının, Visual Studio tasarımcısında görüntülenen ' de açık olduğunu doğrulayın `Sheet1` .

2. **Veri kaynakları** penceresinde **Üreticiler** tablosunu genişletin.

3. **Şirket adı** düğümündeki açılan oka tıklayın ve ardından **NamedRange**' e tıklayın.

4. **Şirket adı** ' nı **veri kaynakları** penceresinden **a2** hücresine sürükleyin `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Adlı bir denetim `CompanyNameNamedRange` oluşturulur ve metin \<CompanyName> **a2** hücresinde görüntülenir. Aynı zamanda, bir <xref:System.Windows.Forms.BindingSource> adlandırılmış `suppliersBindingSource` , bir tablo bağdaştırıcısı ve bir <xref:System.Data.DataSet> projeye eklenir. Denetim öğesine bağlanır <xref:System.Windows.Forms.BindingSource> , bu da <xref:System.Data.DataSet> örneğe bağlanır.

5. **Veri kaynakları** penceresinde, **Üreticiler** tablosunun altındaki sütunları aşağı kaydırın. Listenin en altında **Products** tablosu vardır; Bu, **tedarikçiler** tablosunun bir alt öğesi olduğundan burada yer alabilir. **Üreticiler** tablosuyla aynı düzeyde değil, bu **Ürünler** tablosunu seçin ve ardından görüntülenen aşağı açılan oka tıklayın.

6. Açılan listede **ListObject** ' e tıklayın ve ardından **Ürünler** tablosunu **a6** hücresine sürükleyin `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.ListObject>A6 hücresinde adlı bir denetim `ProductNameListObject` oluşturulur.  Aynı zamanda, bir <xref:System.Windows.Forms.BindingSource> adlandırılmış `productsBindingSource` ve bir tablo bağdaştırıcısı projeye eklenir. Denetim öğesine bağlanır <xref:System.Windows.Forms.BindingSource> , bu da <xref:System.Data.DataSet> örneğe bağlanır.

7. Yalnızca C# için bileşen tepsisinde **suppliersBindingSource** ' ı seçin ve **değiştiriciler** özelliğini **Özellikler** penceresinde **iç** olarak değiştirin.

## <a name="add-controls-to-the-actions-pane"></a>Eylemler bölmesine denetim ekleme
 Sonra, bir açılan kutu içeren bir eylemler bölmesi denetimine ihtiyacınız vardır.

### <a name="to-add-an-actions-pane-control"></a>Eylemler bölmesi denetimi eklemek için

1. **Çözüm Gezgini** Içinde **Excel eylemler bölmesi** projesini seçin.

2. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

3. **Yeni öğe Ekle** Iletişim kutusunda **Eylemler bölmesi denetimi**' ni seçin, **eylem eylemi**' ni adlandırın ve **Ekle**' ye tıklayın.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Eylemler bölmesi denetimine veriye dayalı Windows Forms denetimleri eklemek için

1. **Araç kutusunun** **ortak denetimler** sekmelerinden, <xref:System.Windows.Forms.ComboBox> Eylemler bölmesi denetimine bir denetim sürükleyin.

2. **Boyut** özelliğini **171, 21** olarak değiştirin.

3. Kullanıcı denetimini açılan kutuya sığacak şekilde yeniden boyutlandırın.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Eylemler bölmesindeki denetimi veriye bağlama
 Bu bölümde, veri kaynağını <xref:System.Windows.Forms.ComboBox> çalışma sayfasındaki denetimle aynı veri kaynağına ayarlayacaksınız <xref:Microsoft.Office.Tools.Excel.NamedRange> .

### <a name="to-set-data-binding-properties-of-the-control"></a>Denetimin veri bağlama özelliklerini ayarlamak için

1. Eylemler bölmesi denetimine sağ tıklayın ve sonra **kodu görüntüle**' ye tıklayın.

2. <xref:System.Windows.Forms.UserControl.Load>Eylemler bölmesi denetiminin olayına aşağıdaki kodu ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet1":::

3. C# ' de, için bir olay işleyicisi oluşturmanız gerekir `ActionsControl` . Bu kodu `ActionsControl` oluşturucuya yerleştirebilirsiniz. Olay işleyicileri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet2":::

## <a name="show-the-actions-pane"></a>Eylemler bölmesini göster
 Çalışma zamanında denetim eklenene kadar eylemler bölmesi görünür değildir.

#### <a name="to-show-the-actions-pane"></a>Eylemler bölmesini göstermek için

1. **Çözüm Gezgini**, *ThisWorkbook. vb* veya *ThisWorkbook. cs* öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. Sınıfında kullanıcı denetiminin yeni bir örneğini oluşturun `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet3":::

3. <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>Olay işleyicisinde `ThisWorkbook` , denetimi eylemler bölmesine ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet4":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık belge açıldığında eylemler bölmesinin açıldığını ve denetimlerin Master/Detail ilişkisine sahip olduğunu doğrulamak için belgenizi test edebilirsiniz.

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

2. Eylemler bölmesinin görünür olduğunu onaylayın.

3. Liste kutusunda bir şirket seçin. Şirket adının <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimde listelendiğini ve ürün ayrıntılarının denetimde listelendiğinden emin olun <xref:Microsoft.Office.Tools.Excel.ListObject> .

4. Şirket adının ve ürün ayrıntılarının uygun şekilde değiştiğini doğrulamak için çeşitli şirketler ' i seçin.

## <a name="next-steps"></a>Sonraki Adımlar
 Daha sonra gelebilecek bazı görevler şunlardır:

- Word 'de denetimlere veri bağlama. Daha fazla bilgi için bkz. [Izlenecek yol: Word Eylemler bölmesindeki denetimlere veri bağlama](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

- Projeyi dağıtma. Daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md)
- [Nasıl yapılır: eylemler bölmelerinde denetim yerleşimini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
