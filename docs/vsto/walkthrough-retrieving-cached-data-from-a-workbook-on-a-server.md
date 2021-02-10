---
title: 'İzlenecek yol: sunucudaki çalışma kitabından önbelleğe alınmış verileri alma'
description: ServerDocument sınıfını kullanarak Excel 'i başlatmadan Microsoft Excel çalışma kitabında önbelleğe alınmış bir veri kümesinden verileri nasıl alabileceğinizi öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 818c7c9aa5edeae32859d0b5af6449b513df1c85
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937452"
---
# <a name="walkthrough-retrieve-cached-data-from-a-workbook-on-a-server"></a>İzlenecek yol: sunucudaki çalışma kitabından önbelleğe alınmış verileri alma
  Bu kılavuzda, sınıfını kullanarak Excel 'i başlatmadan Microsoft Office Excel çalışma kitabında önbelleğe alınmış bir veri kümesinden verilerin nasıl alınacağını gösterir <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> .

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- *AdventureWorksLT* veritabanından veri içeren bir veri kümesi tanımlama.

- Excel çalışma kitabı projesinde ve konsol uygulaması projesinde veri kümesinin örneklerini oluşturma.

- <xref:Microsoft.Office.Tools.Excel.ListObject>Çalışma kitabındaki veri kümesine bağlanan bir oluşturma ve <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma kitabı açıldığında verileri ile doldurma.

- Çalışma kitabındaki veri kümesini veri önbelleğine ekleme.

- Önbelleğe alınmış veri kümesinden verileri, Excel 'i başlatmadan konsol uygulamasındaki veri kümesine okuma.

  Bu izlenecek yol, geliştirme bilgisayarınızda kodu çalıştırdığınız varsayılmaktadır, ancak bu izlenecek yol tarafından gösterilen kod, Excel yüklü olmayan bir sunucuda kullanılabilir.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- AdventureWorksLT örnek veritabanının eklendiği Microsoft SQL Server veya Microsoft SQL Server Express çalışan bir örneğine erişim. AdventureWorksLT veritabanını [CodePlex Web sitesinden](https://archive.codeplex.com/?p=SqlServerSamples)indirebilirsiniz. Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak bir veritabanı eklemek için bkz. [nasıl yapılır: veritabanı iliştirme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırını kullanarak bir veritabanı eklemek için, bkz. [nasıl yapılır: SQL Server Express veritabanı dosyası iliştirme](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Veri kümesini tanımlayan bir sınıf kitaplığı projesi oluşturma
 Bir Excel çalışma kitabı projesinde ve bir konsol uygulamasında aynı veri kümesini kullanmak için, veri kümesini bu projelerin her ikisi tarafından başvurulan ayrı bir derlemede tanımlamanız gerekir. Bu izlenecek yol için bir sınıf kitaplığı projesinde veri kümesini tanımlayın.

### <a name="create-the-class-library-project"></a>Sınıf kitaplığı projesi oluşturma

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. Şablonlar bölmesinde, **Visual C#** veya **Visual Basic** öğesini genişletin ve ardından **Windows**' a tıklayın.

4. Proje şablonları listesinde, **sınıf kitaplığı**' nı seçin.

5. **Ad** kutusuna **AdventureWorksDataSet** yazın.

6. **Araştır**' a tıklayın, *%USERPROFILE%\My BELGELERINIZE* (Windows XP ve önceki sürümler için) veya *%UserProfile%\Documents* (Windows Vista Için) klasörüne gidin ve ardından **Klasör Seç**' e tıklayın.

7. **Yeni proje** iletişim kutusunda, **çözüm için dizin oluştur** onay kutusunun seçili olmadığından emin olun.

8. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Çözüm Gezgini** Için bir **AdventureWorksDataSet** projesi ekler ve *Class1.cs* veya *Class1. vb* kod dosyasını açar.

9. **Çözüm Gezgini**' de, *Class1.cs* veya *Class1. vb* öğesine sağ tıklayın ve ardından **Sil**' e tıklayın. Bu izlenecek yol için bu dosyaya ihtiyacınız yoktur.

## <a name="define-a-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde bir veri kümesi tanımlama
 SQL Server 2005 için AdventureWorksLT veritabanından veri içeren bir türü belirtilmiş veri kümesi tanımlayın. Bu izlenecek yolda daha sonra, bu veri kümesine bir Excel çalışma kitabı projesinden ve konsol uygulaması projesinden başvurabileceksiniz.

 Veri kümesi, AdventureWorksLT veritabanının Product tablosundaki verileri temsil eden *türsüz bir veri* kümesidir. Türü belirtilmiş veri kümeleri hakkında daha fazla bilgi için bkz. [Visual Studio 'Da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="define-a-typed-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde bir türü belirtilmiş veri kümesi tanımlama

1. **Çözüm Gezgini**' de, **AdventureWorksDataSet** projesine tıklayın.

2. **Veri kaynakları** penceresi görünür değilse, menü çubuğunda,   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçerek bunu görüntüleyin.

3. **Veri kaynağı Yapılandırma Sihirbazı 'nı** başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

4. **Veritabanı**' na ve ardından **İleri**' ye tıklayın.

5. AdventureWorksLT veritabanına mevcut bir bağlantınız varsa, bu bağlantıyı seçin ve **İleri**' ye tıklayın.

    Aksi takdirde, **Yeni bağlantı**' ya tıklayın ve yeni bağlantıyı oluşturmak Için **bağlantı ekle** iletişim kutusunu kullanın. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** ' ı genişletin ve **ürün (SalesLT)** öğesini seçin.

8. **Finish (Son)** düğmesine tıklayın.

    *AdventureWorksLTDataSet. xsd* dosyası, **AdventureWorksDataSet** projesine eklenir. Bu dosya aşağıdaki öğeleri tanımlar:

   - Adında bir türü belirtilmiş veri kümesi `AdventureWorksLTDataSet` . Bu veri kümesi AdventureWorksLT veritabanındaki ürün tablosunun içeriğini temsil eder.

   - Adında bir TableAdapter `ProductTableAdapter` . Bu TableAdapter, içindeki verileri okumak ve yazmak için kullanılabilir `AdventureWorksLTDataSet` . Daha fazla bilgi için bkz. [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Bu iki nesneyi daha sonra Bu izlenecek yolda kullanacaksınız.

9. **Çözüm Gezgini**, **AdventureWorksDataSet** öğesine sağ tıklayın ve **Oluştur**' a tıklayın.

     Projenin hata olmadan yapılandırıldığını doğrulayın.

## <a name="create-an-excel-workbook-project"></a>Excel çalışma kitabı projesi oluşturma
 Veri arabirimi için bir Excel çalışma kitabı projesi oluşturun. Bu kılavuzda daha sonra, verileri görüntüleyen bir oluşturacak <xref:Microsoft.Office.Tools.Excel.ListObject> ve veri kümesinin bir örneğini çalışma kitabındaki veri önbelleğine ekleyeceksiniz.

### <a name="create-the-excel-workbook-project"></a>Excel çalışma kitabı projesi oluşturma

1. **Çözüm Gezgini**, **AdventureWorksDataSet** çözümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın.

2. Şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' i genişletin.

3. Genişletilmiş **Office/SharePoint** düğümü altında **Office eklentileri** düğümünü seçin.

4. Proje şablonları listesinde, **excel 2010 çalışma** kitabı veya **Excel 2013 çalışma kitabı** projesini seçin.

5. **Ad** kutusuna **AdventureWorksReport** yazın. Konumu değiştirmeyin.

6. **Tamam**'a tıklayın.

     **Office proje sihirbazı Visual Studio Araçları** açılır.

7. **Yeni bir belge oluştur** ' un seçili olduğundan emin olun ve **Tamam**' ı tıklatın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]tasarımcıda **AdventureWorksReport** çalışma kitabını açar ve **Çözüm Gezgini** **AdventureWorksReport** projesini ekler.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Veri kümesini Excel çalışma kitabı projesindeki veri kaynaklarına ekleme
 Veri kümesini Excel çalışma kitabında görüntüleyebilmeniz için önce Excel çalışma kitabı projesindeki veri kaynaklarına veri kümesini eklemeniz gerekir.

1. **Çözüm Gezgini**, **AdventureWorksReport** projesi altındaki *Sheet1.cs* veya *Sheet1. vb* öğesine çift tıklayın.

     Çalışma kitabı tasarımcıda açılır.

2. **Veri** menüsünde **Yeni veri kaynağı Ekle**' ye tıklayın.

     **Veri kaynağı Yapılandırma Sihirbazı** açılır.

3. **Nesne**' ye ve ardından **İleri**' ye tıklayın.

4. **Bağlamak Istediğiniz nesneyi seçin** sayfasında, **Başvuru Ekle**' ye tıklayın.

5. **Projeler** sekmesinde, **AdventureWorksDataSet** ' e ve ardından **Tamam**' a tıklayın.

6. **AdventureWorksDataSet** derlemesinin **AdventureWorksDataSet** ad alanı altında, **AdventureWorksLTDataSet** ' e ve ardından **son**' a tıklayın.

     **Veri kaynakları** penceresi açılır ve **AdventureWorksLTDataSet** veri kaynakları listesine eklenir.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Veri kümesinin örneğine bağlanan bir ListObject oluşturma
 Çalışma kitabında veri kümesini göstermek için bir <xref:Microsoft.Office.Tools.Excel.ListObject> veri kümesinin örneğine bağlanan bir oluşturun. Verilere yönelik bağlama denetimleri hakkında daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

1. **Veri kaynakları** penceresinde, **AdventureWorksDataSet** altındaki **AdventureWorksLTDataSet** düğümünü genişletin.

2. **Ürün** düğümünü seçin, görüntülenen aşağı açılan oka tıklayın ve açılan listeden **ListObject** ' i seçin.

     Aşağı açılan ok görünmezse, çalışma kitabının tasarımcıda açık olduğunu onaylayın.

3. **Ürün** tablosunu a1 hücresine sürükleyin.

     <xref:Microsoft.Office.Tools.Excel.ListObject> `productListObject` Çalışma sayfasında A1 hücresinden başlayarak adlı bir denetim oluşturulur. Aynı zamanda, adlı ve adlı bir veri kümesi nesnesi `adventureWorksLTDataSet` <xref:System.Windows.Forms.BindingSource> `productBindingSource` projeye eklenir. , <xref:Microsoft.Office.Tools.Excel.ListObject> ' A bağlanır ve <xref:System.Windows.Forms.BindingSource> veri kümesi nesnesine bağlanır.

## <a name="add-the-dataset-to-the-data-cache"></a>Veri kümesini veri önbelleğine ekleme
 Excel çalışma kitabı projesi dışındaki kodun çalışma kitabındaki veri kümesine erişmesini sağlamak için veri kümesini veri önbelleğine eklemeniz gerekir. Veri önbelleği hakkında daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md) ve [Önbellek verileri](../vsto/caching-data.md).

1. Tasarımcıda **AdventureWorksLTDataSet**' e tıklayın.

2. **Özellikler** penceresinde **değiştiriciler** özelliğini **Public** olarak ayarlayın.

3. **CacheInDocument** özelliğini **true** olarak ayarlayın.

## <a name="initialize-the-dataset-in-the-workbook"></a>Çalışma kitabındaki veri kümesini başlatma
 Konsol uygulamasını kullanarak önbelleğe alınmış veri kümesinden verileri almak için önce önbelleğe alınmış veri kümesini verilerle doldurmanız gerekir.

1. **Çözüm Gezgini**, *Sheet1.cs* veya *Sheet1. vb* dosyasını sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

2. `Sheet1_Startup`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod, `ProductTableAdapter` Şu anda boşsa, verileri önbelleğe alınmış veri kümesini dolduracak şekilde, **AdventureWorksDataSet** projesinde tanımlanan sınıfının bir örneğini kullanır.

     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]

## <a name="checkpoint"></a>Checkpoint
 Hatasız derlendiğinden ve çalıştığından emin olmak için Excel çalışma kitabı projesini derleyin ve çalıştırın. Bu işlem, önbelleğe alınmış veri kümesini de doldurur ve verileri çalışma kitabına kaydeder.

### <a name="build-and-run-the-project"></a>Projeyi derleyin ve çalıştırın

1. **Çözüm Gezgini**, **AdventureWorksReport** projesine sağ tıklayın, **Hata Ayıkla**' yı seçin ve ardından **Yeni örnek Başlat**' ı tıklatın.

     Proje oluşturulmuştur ve çalışma kitabı Excel 'de açılır. Aşağıdakileri doğrulayın:

    - <xref:Microsoft.Office.Tools.Excel.ListObject>Veriler ile doldurulur.

    - Öğesinin ilk satırı için **ListPrice** sütunundaki değer <xref:Microsoft.Office.Tools.Excel.ListObject> 1431,5 ' dir. Bu izlenecek yolda daha sonra, **ListPrice** sütunundaki değerleri değiştirmek için bir konsol uygulaması kullanacaksınız.

2. Çalışma kitabını kaydedin. Dosya adını veya çalışma kitabının konumunu değiştirmeyin.

3. Excel 'i kapatın.

## <a name="create-a-console-application-project"></a>Konsol uygulaması projesi oluşturma
 Çalışma kitabındaki önbelleğe alınmış veri kümesindeki verileri değiştirmek için kullanılacak bir konsol uygulaması projesi oluşturun.

1. **Çözüm Gezgini**, **AdventureWorksDataSet** çözümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın.

2. **Proje türleri** bölmesinde, **Visual C#** veya **Visual Basic** öğesini genişletin ve ardından **Windows**' a tıklayın.

3. **Şablonlar** bölmesinde **konsol uygulaması**' nı seçin.

4. **Ad** kutusuna **DataReader** yazın. Konumu değiştirmeyin.

5. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Çözüm Gezgini** **DataReader** projesi ekler ve *program.cs* veya *Module1. vb* kod dosyasını açar.

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Konsol uygulamasını kullanarak önbelleğe alınmış veri kümesinden verileri alma
 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Verileri yerel bir nesneye okumak için konsol uygulamasındaki sınıfını kullanın `AdventureWorksLTDataSet` . Yerel veri kümesinin, önbelleğe alınmış veri kümesindeki verilerle başlatıldığını onaylamak için, uygulama yerel veri kümesindeki satır sayısını görüntüler.

### <a name="retrieve-data-from-the-cached-dataset"></a>Önbelleğe alınmış veri kümesinden verileri alma

1. **Çözüm Gezgini**, **DataReader** projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

2. **.Net** sekmesinde, **Microsoft. VisualStudio. Tools. Applications. ServerDocument** öğesini seçin.

3. **Tamam**'a tıklayın.

4. **Çözüm Gezgini**, **DataReader** projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

5. **Projeler** sekmesinde, **AdventureWorksDataSet**' i seçin ve **Tamam**' ı tıklatın.

6. Kod düzenleyicisinde *program.cs* veya *Module1. vb* dosyasını açın.

7. Aşağıdaki **using** (C# için) veya **ımports** (for Visual Basic) deyimlerini kod dosyasının en üstüne ekleyin.

    [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
    [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]

8. `Main` yöntemine aşağıdaki kodu ekleyin. Bu kod aşağıdaki nesneleri bildirir:

   - `AdventureWorksLTDataSet` **AdventureWorksDataSet** projesinde tanımlanan türün örneği.

   - **AdventureWorksReport** projesinin Build klasöründeki AdventureWorksReport çalışma kitabının yolu.

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Çalışma kitabındaki veri önbelleğine erişmek için kullanılacak nesne.

     > [!NOTE]
     > Aşağıdaki kod, çalışma kitabının *. xlsx* uzantısı kullanılarak kaydedildiğini varsayar. Projenizdeki çalışma kitabının farklı bir uzantısı varsa, yolu gereken şekilde değiştirin.

     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]

9. `Main`Önceki adımda eklediğiniz koddan sonra yöntemine aşağıdaki kodu ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Çalışma kitabındaki önbelleğe alınmış veri kümesine erişmek için sınıfının özelliğini kullanır.

   - Önbelleğe alınmış veri kümesindeki verileri yerel veri kümesine okur.

   - Verilerin olduğunu doğrulamak için yerel veri kümesindeki satır sayısını görüntüler.

     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]

10. **Yapı** menüsünde, **derleme DataReader**' ı tıklatın.

## <a name="test-the-project"></a>Projeyi test etme
 Konsol uygulamasını çalıştırdığınızda, yerel veri kümesindeki satır sayısını görüntüler.

### <a name="test-the-workbook"></a>Çalışma kitabını test etme

1. **Çözüm Gezgini**, **DataReader** projesine sağ tıklayın, **Hata Ayıkla**' nın üzerine gelin ve ardından **Yeni örnek Başlat**' a tıklayın.

     Uygulamanın, yerel veri kümesinin 295 satırı olduğunu rapor ettiğini doğrulayın.

2. Uygulamayı kapatmak için **ENTER** tuşuna basın.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan önbelleğe alınmış verilerle çalışma hakkında daha fazla bilgi edinebilirsiniz:

- Excel 'i başlatmadan önbelleğe alınmış veri kümesindeki verileri değiştirme. Daha fazla bilgi için bkz. [Izlenecek yol: bir sunucudaki çalışma kitabındaki önbelleğe alınmış verileri değiştirme](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: sunucudaki çalışma kitabına veri ekleme](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [İzlenecek yol: sunucudaki çalışma kitabında bulunan önbelleğe alınmış verileri değiştirme](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
