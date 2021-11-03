---
title: 'Adım adım kılavuz: Sunucu üzerinde bir çalışma kitabından önbelleğe alınmış verileri alma'
description: ServerDocument sınıfını kullanarak veri kümelerini kullanmaya başlamadan Microsoft Excel bir veri kümesinden Excel nasıl alasınız?
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 77b6006b54da383a763ea1dbd93d078a40a88aaf
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131126993"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>Adım adım kılavuz: Sunucu üzerinde bir çalışma kitabından önbelleğe alınmış verileri alma
  Bu kılavuzda, sınıfını kullanmaya başlamadan bir Microsoft Office Excel çalışma kitabında önbelleğe alınmış bir veri kümesinden Excel nasıl alın <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> açıklanır.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- *AdventureWorksLT* veritabanından veri içeren bir veri kümesi tanımlama.

- Bir çalışma kitabı projesinde ve konsol uygulaması Excel veri kümesi örnekleri oluşturma.

- Çalışma kitabındaki veri kümesine bağlı bir oluşturma ve çalışma kitabı açıldığında <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> verilerle doldurmak.

- Çalışma kitabındaki veri kümelerini veri önbelleğine ekleme.

- Önbelleğe alınmış veri kümesinden konsol uygulamasındaki veri kümesine veri okuma, Excel.

  Bu kılavuz, kodu geliştirme bilgisayarınızda çalıştırmış olduğunu varsaysa da, bu izlenecek yol tarafından belirtilen kod, yüklü yüklü Excel kullanılabilir.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- AdventureWorksLT örnek veritabanının Microsoft SQL Server veya Microsoft SQL Server Express örnek veritabanına erişim. AdventureWorksLT veritabanını CodePlex web [sitesinden indirebilirsiniz.](/sql/samples/adventureworks-install-configure) Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak veritabanı eklemek için [bkz. Nasıl kullanılır: Veritabanı ekleme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırı kullanarak veritabanı eklemek için bkz. [Nasıl kullanılır:](/previous-versions/sql/)Veritabanı dosyasını SQL Server Express.

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Veri kümesi tanımlayan bir sınıf kitaplığı projesi oluşturma
 Aynı veri kümesini bir Excel çalışma kitabı projesinde ve konsol uygulamasında kullanmak için, veri kümesini bu projelerin her ikisi tarafından da başvurulan ayrı bir derlemede tanımlamanız gerekir. Bu kılavuz için, veri kümesi bir sınıf kitaplığı projesinde tanımlayın.

### <a name="create-the-class-library-project"></a>Sınıf kitaplığı projesini oluşturma

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** ardından Yeni'ye **Project.**

3. Şablonlar bölmesinde, Visual **C#** veya Visual Basic **genişletin** ve ardından **Windows.**

4. Proje şablonları listesinde Sınıf **Kitaplığı'ı seçin.**

5. Ad **kutusuna** **AdventureWorksDataSet yazın.**

6. **Gözat'a** tıklayın, *%UserProfile%\Belgelerim* (Windows XP ve önceki sürümler için) veya *%UserProfile%\Documents* (Windows Vista için) klasörüne gidin ve ardından Klasör Seç'e **tıklayın.**

7. Yeni **Project** iletişim kutusunda Çözüm için **dizin oluştur onay kutusunun seçili** olduğundan emin olun.

8. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**AdventureWorksDataSet projesini**  Çözüm Gezgini *class1.cs veya Class1.vb* *kod* dosyasını açar.

9. Bu **Çözüm Gezgini** *Class1.cs veya Class1.vb'ye* sağ *tıklayın* ve ardından Sil'e **tıklayın.** Bu kılavuz için bu dosyaya ihtiyacınız yok.

## <a name="define-a-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde veri kümesi tanımlama
 SQL Server 2005 için AdventureWorksLT veritabanından veri içeren türü SQL Server tanımlayın. Bu kılavuzun ilerleyen adımlarında, bu veri kümesine bir Excel çalışma kitabı projesinden ve konsol uygulaması projesinden başvuracağız.

 Veri kümesi, AdventureWorksLT *veritabanının* Product tablosunda yer alan verileri temsil eden türü belirli bir veri kümesidir. Türü yazilen veri kümeleri hakkında daha fazla bilgi için [bkz.](../data-tools/dataset-tools-in-visual-studio.md)Visual Studio.

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde türe bağlı bir veri kümesi tanımlama

1. Bu **Çözüm Gezgini** **AdventureWorksDataSet projesine** tıklayın.

2. Veri **Kaynakları penceresi görünmüyorsa,** menü çubuğunda Diğer Kaynakları Görüntüle'Windows   >    >  **görüntüleniyor.**

3. Veri **Kaynağı Yapılandırma Sihirbazı'nı başlatmak** için Yeni Veri Kaynağı **Ekle'yi seçin.**

4. Veritabanı **'ne** ve ardından Sonraki'ye **tıklayın.**

5. AdventureWorksLT veritabanına mevcut bir bağlantınız varsa bu bağlantıyı seçin ve Ardından'ya **tıklayın.**

    Aksi takdirde, **Yeni Bağlantı'ya** tıklayın **ve yeni bağlantıyı** oluşturmak için Bağlantı Ekle iletişim kutusunu kullanın. Daha fazla bilgi için [bkz. Yeni bağlantı ekleme.](../data-tools/add-new-connections.md)

6. Bağlantı **Dizesini Uygulama Yapılandırma Dosyasına Kaydet sayfasında, Sonraki** 'ye **tıklayın.**

7. Veritabanı **Nesnelerinizi Seçin sayfasında Tablolar'ı** genişletin ve **Ürün** **(SalesLT) öğesini seçin.**

8. **Finish (Son)** düğmesine tıklayın.

    *AdventureWorksLTDataSet.xsd* dosyası **AdventureWorksDataSet projesine** eklenir. Bu dosya aşağıdaki öğeleri tanımlar:

   - adlı türüne göre bir veri `AdventureWorksLTDataSet` kümesi. Bu veri kümesi, AdventureWorksLT veritabanındaki Product tablosu içeriğini temsil eder.

   - adlı bir TableAdapter. `ProductTableAdapter` Bu TableAdapter, içinde veri okumak ve yazmak için `AdventureWorksLTDataSet` kullanılabilir. Daha fazla bilgi için bkz. [TableAdapter'a genel bakış.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

     Bu adım adım kılavuzda bu nesnelerin ikisini de kullanacağız.

9. Içinde **Çözüm Gezgini** **AdventureWorksDataSet'e sağ tıklayın ve Derleme'ye** **tıklayın.**

     Projenin hatasız olarak derlemesini doğrulayın.

## <a name="create-an-excel-workbook-project"></a>Çalışma kitabı Excel oluşturma
 Verilere Excel için bir çalışma kitabı projesi oluşturun. Bu kılavuzda daha sonra verileri görüntüleyen bir oluşturacak ve çalışma kitabındaki veri önbelleğine veri kümesi <xref:Microsoft.Office.Tools.Excel.ListObject> örneği eklenecektir.

### <a name="create-the-excel-workbook-project"></a>Excel çalışma kitabı projesini oluşturma

1. Bu **Çözüm Gezgini** **AdventureWorksDataSet** çözümüne sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından Yeni Çalışma **Project.**

2. Şablonlar bölmesinde Visual **C#** veya **Visual Basic'ı** genişletin ve ardından **Office/SharePoint.**

3. Genişletilmiş **Office/SharePoint** altında, Office **düğümünü** seçin.

4. Proje şablonları listesinde Excel **2010** Çalışma Kitabı'Excel **projesini** seçin.

5. Ad **kutusuna** **AdventureWorksReport yazın.** Konumu değiştirmeyin.

6. **Tamam**'a tıklayın.

     Office için Visual Studio Araçları Project **Sihirbazı** açılır.

7. Yeni belge **oluştur'u seçin ve** Tamam'a **tıklayın.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Tasarımcıda **AdventureWorksReport** çalışma kitabını açar ve **AdventureWorksReport** projesini **Çözüm Gezgini.**

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Veri kümesi çalışma kitabı projesinde veri Excel ekleme
 Veri kümelerini çalışma kitabınızda görüntüley Excel önce çalışma kitabı projesinde veri Excel eklemeniz gerekir.

1. Bu **Çözüm Gezgini** **AdventureWorksReport** projesinin altında *Sheet1.cs veya Sheet1.vb'ye* çift tıklayın. 

     Çalışma kitabı tasarımcıda açılır.

2. Veri menüsünde **Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

     Veri **Kaynağı Yapılandırma Sihirbazı** açılır.

3. **Nesne'ye** ve ardından Sonraki **'ye tıklayın.**

4. Bağlamak **istediğiniz Nesneyi Seçin sayfasında Başvuru** Ekle'ye **tıklayın.**

5. Projeler sekmesinde **AdventureWorksDataSet'e ve ardından** Tamam'a **tıklayın.** 

6. **AdventureWorksDataSet** **derlemenin AdventureWorksDataSet** ad alanı altında **AdventureWorksLTDataSet'e** ve ardından Son'a **tıklayın.**

     Veri **Kaynakları** penceresi açılır ve **AdventureWorksLTDataSet** veri kaynakları listesine eklenir.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Veri kümesi örneğine bağlı bir ListObject oluşturma
 Çalışma kitabında veri kümesi görüntülemek için veri <xref:Microsoft.Office.Tools.Excel.ListObject> kümesi örneğine bağlı bir oluşturun. Verilere denetimler bağlama hakkında daha fazla bilgi için [bkz. Veri bağlama çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

1. Veri Kaynakları **penceresinde** **AdventureWorksDataSet altındaki AdventureWorksLTDataSet** **düğümünü genişletin.**

2. Ürün **düğümünü** seçin, görüntülenen açılan oka tıklayın ve açılan listeden **ListObject** öğesini seçin.

     Açılan ok görünmüyorsa çalışma kitabının tasarımcıda açık olduğunu onaylayın.

3. Product tablosu **A1** hücresine sürükleyin.

     Çalışma <xref:Microsoft.Office.Tools.Excel.ListObject> sayfasında `productListObject` A1 hücresinde başlayarak adlı bir denetim oluşturulur. Aynı zamanda, ve adlı bir veri `adventureWorksLTDataSet` kümesi <xref:System.Windows.Forms.BindingSource> nesnesi projeye `productBindingSource` eklenir. <xref:Microsoft.Office.Tools.Excel.ListObject>, veri kümesi <xref:System.Windows.Forms.BindingSource> nesnesine bağlı olan nesnesine bağlı olur.

## <a name="add-the-dataset-to-the-data-cache"></a>Veri kümesi veri önbelleğine ekleme
 Çalışma kitabı projesinin Excel çalışma kitabı projesinin dışındaki kodun çalışma kitabındaki veri kümesine erişmesini sağlamak için veri kümesine veri önbelleğini eklemeniz gerekir. Veri önbelleği hakkında daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md) ve [Önbellek verileri](../vsto/caching-data.md).

1. Tasarımcıda **AdventureWorksLTDataSet**' e tıklayın.

2. **Özellikler** penceresinde **değiştiriciler** özelliğini **Public** olarak ayarlayın.

3. **CacheInDocument** özelliğini **true** olarak ayarlayın.

## <a name="initialize-the-dataset-in-the-workbook"></a>Çalışma kitabındaki veri kümesini başlatma
 Konsol uygulamasını kullanarak önbelleğe alınmış veri kümesinden verileri almak için önce önbelleğe alınmış veri kümesini verilerle doldurmanız gerekir.

1. **Çözüm Gezgini**, *Sheet1. cs* veya *Sayfa1. vb* dosyasını sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

2. `Sheet1_Startup`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod, `ProductTableAdapter` Şu anda boşsa, verileri önbelleğe alınmış veri kümesini dolduracak şekilde, **AdventureWorksDataSet** projesinde tanımlanan sınıfının bir örneğini kullanır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb" id="Snippet8":::

## <a name="checkpoint"></a>Checkpoint
 Excel çalışma kitabı projesi oluşturup çalıştırarak, hatasız bir şekilde derlendiğinden ve çalıştığından emin olun. Bu işlem, önbelleğe alınmış veri kümesini de doldurur ve verileri çalışma kitabına kaydeder.

### <a name="build-and-run-the-project"></a>Projeyi derleyin ve çalıştırın

1. **Çözüm Gezgini**, **AdventureWorksReport** projesine sağ tıklayın, **Hata Ayıkla**' yı seçin ve ardından **Yeni örnek Başlat**' ı tıklatın.

     Proje oluşturulur ve çalışma kitabı Excel açılır. Aşağıdakileri doğrulayın:

    - <xref:Microsoft.Office.Tools.Excel.ListObject>Veriler ile doldurulur.

    - Öğesinin ilk satırı için **ListPrice** sütunundaki değer <xref:Microsoft.Office.Tools.Excel.ListObject> 1431,5 ' dir. Bu izlenecek yolda daha sonra, **ListPrice** sütunundaki değerleri değiştirmek için bir konsol uygulaması kullanacaksınız.

2. Çalışma kitabını kaydedin. Dosya adını veya çalışma kitabının konumunu değiştirmeyin.

3. Excel kapatın.

## <a name="create-a-console-application-project"></a>Konsol uygulaması projesi oluşturma
 Çalışma kitabındaki önbelleğe alınmış veri kümesindeki verileri değiştirmek için kullanılacak bir konsol uygulaması projesi oluşturun.

1. **Çözüm Gezgini**, **AdventureWorksDataSet** çözümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **yeni Project**' ye tıklayın.

2. **Project türleri** bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Windows**' ye tıklayın.

3. **Şablonlar** bölmesinde **konsol uygulaması**' nı seçin.

4. **Ad** kutusuna **DataReader** yazın. Konumu değiştirmeyin.

5. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**DataReader** projesini **Çözüm Gezgini** ekler ve *program. cs* veya *Module1. vb* kod dosyasını açar.

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Konsol uygulamasını kullanarak önbelleğe alınmış veri kümesinden verileri alma
 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Verileri yerel bir nesneye okumak için konsol uygulamasındaki sınıfını kullanın `AdventureWorksLTDataSet` . Yerel veri kümesinin, önbelleğe alınmış veri kümesindeki verilerle başlatıldığını onaylamak için, uygulama yerel veri kümesindeki satır sayısını görüntüler.

### <a name="retrieve-data-from-the-cached-dataset"></a>Önbelleğe alınmış veri kümesinden verileri alma

1. **Çözüm Gezgini**, **DataReader** projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

2. **.Net** sekmesinde, **Microsoft. VisualStudio. Tools. Applications. ServerDocument** öğesini seçin.

3. **Tamam**'a tıklayın.

4. **Çözüm Gezgini**, **DataReader** projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

5. **Projeler** sekmesinde, **AdventureWorksDataSet**' i seçin ve **Tamam**' ı tıklatın.

6. Kod düzenleyicisinde *program. cs* veya *Module1. vb* dosyasını açın.

7. aşağıdaki **using** (C# için) veya **ımports** (for Visual Basic) deyimlerini kod dosyasının en üstüne ekleyin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet1":::

8. `Main` yöntemine aşağıdaki kodu ekleyin. Bu kod aşağıdaki nesneleri bildirir:

   - `AdventureWorksLTDataSet` **AdventureWorksDataSet** projesinde tanımlanan türün örneği.

   - **AdventureWorksReport** projesinin Build klasöründeki AdventureWorksReport çalışma kitabının yolu.

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Çalışma kitabındaki veri önbelleğine erişmek için kullanılacak nesne.

     > [!NOTE]
     > Aşağıdaki kod, çalışma kitabının *.xlsx* uzantısı kullanılarak kaydedildiğini varsayar. Projenizdeki çalışma kitabının farklı bir uzantısı varsa, yolu gereken şekilde değiştirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet10":::

9. `Main`Önceki adımda eklediğiniz koddan sonra yöntemine aşağıdaki kodu ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Çalışma kitabındaki önbelleğe alınmış veri kümesine erişmek için sınıfının özelliğini kullanır.

   - Önbelleğe alınmış veri kümesindeki verileri yerel veri kümesine okur.

   - Verilerin olduğunu doğrulamak için yerel veri kümesindeki satır sayısını görüntüler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet11":::

10. **Yapı** menüsünde, **derleme DataReader**' ı tıklatın.

## <a name="test-the-project"></a>Projeyi test etme
 Konsol uygulamasını çalıştırdığınızda, yerel veri kümesindeki satır sayısını görüntüler.

### <a name="test-the-workbook"></a>Çalışma kitabını test etme

1. **Çözüm Gezgini**, **DataReader** projesine sağ tıklayın, **Hata Ayıkla**' nın üzerine gelin ve ardından **Yeni örnek Başlat**' a tıklayın.

     Uygulamanın, yerel veri kümesinin 295 satırı olduğunu rapor ettiğini doğrulayın.

2. Uygulamayı kapatmak için **ENTER** tuşuna basın.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan önbelleğe alınmış verilerle çalışma hakkında daha fazla bilgi edinebilirsiniz:

- Excel başlatmadan önbelleğe alınmış veri kümesindeki verileri değiştirme. Daha fazla bilgi için bkz. [Izlenecek yol: bir sunucudaki çalışma kitabındaki önbelleğe alınmış verileri değiştirme](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: sunucudaki çalışma kitabına veri ekleme](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [İzlenecek yol: sunucudaki çalışma kitabında bulunan önbelleğe alınmış verileri değiştirme](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
