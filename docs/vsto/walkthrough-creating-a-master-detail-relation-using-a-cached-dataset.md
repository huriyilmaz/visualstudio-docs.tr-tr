---
title: Önbelleğe alınmış veri kümesini kullanarak ana ayrıntı ilişkisi oluşturma
description: Çalışma sayfasında ana/ayrıntı ilişkisi oluşturma ve çözümün çevrimdışı kullanılabilmesi için verileri önbelleğe alma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c4d8d32ea4abfd7b81e6e86bc8d1affa32d1c3b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059874"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>İzlenecek yol: önbelleğe alınmış bir veri kümesini kullanarak ana ayrıntı ilişkisi oluşturma
  Bu izlenecek yol, bir çalışma sayfasında ana/ayrıntı ilişkisi oluşturmayı ve çözümün çevrimdışı kullanılabilmesi için verileri önbelleğe almayı gösterir.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Çalışma sayfasına denetimler ekleme.

- Bir çalışma sayfasında önbelleğe alınacak bir veri kümesi ayarlayın.

- Kayıtlar arasında gezinmeyi etkinleştirmek için kod ekleyin.

- Projenizi test edin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Northwind SQL Server örnek veritabanına erişim. Veritabanı geliştirme bilgisayarınızda veya bir sunucuda olabilir.

- SQL Server veritabanına okuma ve yazma izinleri.

## <a name="create-a-new-project"></a>Yeni proje oluşturma
 bu adımda, bir Excel çalışma kitabı projesi oluşturacaksınız.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Visual Basic veya C# kullanarak **ana ayrıntım** adlı Excel bir çalışma kitabı projesi oluşturun. **Yeni belge oluştur** ' un seçili olduğundan emin olun. daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

   Visual Studio yeni Excel çalışma kitabını tasarımcıda açar ve **asıl ayrıntı** projesini **Çözüm Gezgini** ekler.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma
 Projenize türü belirtilmiş bir veri kümesi eklemek için **veri kaynakları** penceresini kullanın.

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **veri kaynakları** penceresi görünür değilse, menü çubuğunda,   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçerek bunu görüntüleyin.

2. **Veri kaynağı Yapılandırma Sihirbazı 'nı** başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

4. Northwind örnek SQL Server veritabanına yönelik bir veri bağlantısı seçin veya **yeni bağlantı** düğmesini kullanarak yeni bir bağlantı ekleyin.

5. Bir bağlantı seçtikten veya oluşturduktan sonra **İleri**' ye tıklayın.

6. Seçildiğinde bağlantıyı kaydetme seçeneğini temizleyin ve ardından **İleri**' ye tıklayın.

7. **Veritabanı nesneleri** penceresinde **Tablolar** düğümünü genişletin.

8. **Siparişler** tablosu ve **sipariş ayrıntıları** tablosunu seçin.

9. **Finish (Son)** düğmesine tıklayın.

   Sihirbaz, **veri kaynakları** penceresine iki tablo ekler. Ayrıca, projenize **Çözüm Gezgini** görünür bir veri kümesi de ekler.

## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme
 Bu adımda, ilk çalışma sayfasına adlandırılmış bir Aralık, liste nesnesi ve iki düğme ekleyeceksiniz. İlk olarak, adlandırılmış aralığı ve liste nesnesini **veri kaynakları** penceresinden, otomatik olarak veri kaynağına bağlanacak şekilde ekleyin. Sonra, **araç kutusundan** düğmeleri ekleyin.

### <a name="to-add-a-named-range-and-a-list-object"></a>Adlandırılmış bir Aralık ve bir liste nesnesi eklemek için

1. **Master-Detail.xlsx** çalışma kitabının, **Sheet1** görüntülenirken Visual Studio tasarımcısında açık olduğunu doğrulayın.

2. **Veri kaynakları** penceresini açın ve **siparişler** düğümünü genişletin.

3. **OrderID** sütununu seçin ve ardından görüntülenen aşağı açılan oka tıklayın.

4. Açılan listede **NamedRange** ' e tıklayın ve ardından **OrderID** sütununu **a2** hücresine sürükleyin.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Adlandırılmış bir denetim `OrderIDNamedRange` , **a2** hücresinde oluşturulur. Aynı zamanda, <xref:System.Windows.Forms.BindingSource> adlandırılmış `OrdersBindingSource` , bir tablo bağdaştırıcısı ve <xref:System.Data.DataSet> projeye bir örnek eklenir. Denetim öğesine bağlanır <xref:System.Windows.Forms.BindingSource> , bu da <xref:System.Data.DataSet> örneğe bağlanır.

5. **Siparişler** tablosunun altındaki sütunları aşağı kaydırın. Listenin en altında **sipariş ayrıntıları** tablosu bulunur; burada, **siparişler** tablosunun bir alt öğesi olduğu için burada yer verilmiştir. **Orders** tablosuyla aynı düzeyde değil, bu **sipariş ayrıntıları** tablosunu seçin ve ardından görüntülenen aşağı açılan oka tıklayın.

6. Açılan listede **ListObject** ' e tıklayın ve ardından **OrderDetails** tablosunu **a6** hücresine sürükleyin.

7. <xref:Microsoft.Office.Tools.Excel.ListObject> **Order_DetailsListObject** adlı bir denetim, **a6** hücresinde oluşturulur ve öğesine bağlanır <xref:System.Windows.Forms.BindingSource> .

### <a name="to-add-two-buttons"></a>İki düğme eklemek için

1. **Araç kutusunun** **ortak denetimler** sekmesinden, <xref:System.Windows.Forms.Button> çalışma sayfasının **a3** hücresine bir denetim ekleyin.

    Bu düğme adlandırılır `Button1` .

2. <xref:System.Windows.Forms.Button>Çalışma sayfasının **B3** hücresine başka bir denetim ekleyin.

    Bu düğme adlandırılır `Button2` .

   Sonra, veri kümesini belgede önbelleğe alınacak şekilde işaretleyin.

## <a name="cache-the-dataset"></a>Veri kümesini önbelleğe alma
 Veri kümesini ortak hale getirerek ve **CacheInDocument** özelliğini ayarlayarak veri kümesini belgede önbelleğe alınacak şekilde işaretleyin.

### <a name="to-cache-the-dataset"></a>Veri kümesini önbelleğe almak için

1. Bileşen tepsisinde **NorthwindDataSet** ' i seçin.

2. **Özellikler** penceresinde, **değiştiriciler** özelliğini **Public** olarak değiştirin.

    Önbelleğe alma etkinleştirilmeden önce veri kümelerinin ortak olması gerekir.

3. **CacheInDocument** özelliğini **true** olarak değiştirin.

   Sonraki adım düğmelere metin eklemektir ve C# ' ta olay işleyicilerini bağlamak için kod ekler.

## <a name="initialize-the-controls"></a>Denetimleri Başlat
 Olay sırasında düğme metnini ayarlayın ve olay işleyicileri ekleyin <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> .

### <a name="to-initialize-the-data-and-the-controls"></a>Verileri ve denetimleri başlatmak için

1. **Çözüm Gezgini**, **Sheet1. vb** veya **Sayfa1. cs**' ye sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.

2. `Sheet1_Startup`Düğme metnini ayarlamak için yöntemine aşağıdaki kodu ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet15":::

3. Yalnızca C# için, yöntemine düğme tıklama olayları için olay işleyicileri ekleyin `Sheet1_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet16":::

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Kayıtlar arasında kaydırmayı etkinleştirmek için kod ekleme
 <xref:System.Windows.Forms.Control.Click>Kayıtlar arasında gezinmek için her düğmenin olay işleyicisine kod ekleyin.

### <a name="to-scroll-through-the-records"></a>Kayıtlar arasında gezinmek için

1. Olayı için bir olay işleyicisi ekleyin <xref:System.Windows.Forms.Control.Click> `Button1` ve kayıtlar arasında geriye gitmek için aşağıdaki kodu ekleyin:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet17":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet17":::

2. Olayı için bir olay işleyicisi ekleyin <xref:System.Windows.Forms.Control.Click> `Button2` ve kayıtlar arasında ilerlemek için aşağıdaki kodu ekleyin:

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs" id="Snippet18":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık, verilerin beklendiği gibi göründüğünden ve çözümü çevrimdışı olarak kullanabilmeniz için çalışma kitabınızı test edebilirsiniz.

### <a name="to-test-the-data-caching"></a>Verilerin önbelleğe alınmasını test etmek için

1. **F5** tuşuna basın.

2. Adlandırılmış aralığın ve liste nesnesinin veri kaynağından alınan verilerle doldurulduğunu doğrulayın.

3. Düğmelere tıklayarak bazı kayıtlardan ilerleyin.

4. Çalışma kitabını kaydedin ve sonra Visual Studio çalışma kitabını kapatın.

5. Veritabanına bağlantıyı devre dışı bırakın. veritabanı bir sunucuda bulunuyorsa ağ kablosunu bilgisayarınızdan çıkarın veya veritabanı geliştirme bilgisayarınızda ise SQL Server hizmeti 'ni durdurun.

6. Excel açın ve sonra *\bin* dizininden **Master-Detail.xlsx** *açın (C# ' deki Visual Basic* veya *\Master-Detail\bin\debug* ).

7. Çalışma sayfasının, bağlantısı kesildiğinde normal şekilde çalıştığını görmek için bazı kayıtlardan ilerleyin.

8. Veritabanına yeniden bağlanın. veritabanı bir sunucuda bulunuyorsa bilgisayarınızı ağa yeniden Bağlan veya veritabanı geliştirme bilgisayarınızda ise SQL Server hizmeti 'ni başlatın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yol, bir çalışma sayfasında ana/ayrıntı veri ilişkisi oluşturma ve bir veri kümesini önbelleğe alma temellerini gösterir. Daha sonra gelebilecek bazı görevler şunlardır:

- Çözümü dağıtın. daha fazla bilgi için bkz. [Office çözüm dağıtma](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office çözümlerinde veri](../vsto/data-in-office-solutions.md)
- [Önbellek verileri](../vsto/caching-data.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
