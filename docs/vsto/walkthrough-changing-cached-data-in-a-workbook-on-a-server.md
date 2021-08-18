---
title: 'Adım adım kılavuz: Sunucu üzerinde bir çalışma kitabındaki önbelleğe alınmış verileri değiştirme'
description: ServerDocument sınıfını kullanarak Microsoft Excel çalışma kitabında önbelleğe alınmış bir veri Excel değiştirmeyi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], changing server data
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
ms.openlocfilehash: a98370ee84f914b5f556276a6d83d7713246d615
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032101"
---
# <a name="walkthrough-change-cached-data-in-a-workbook-on-a-server"></a>Adım adım kılavuz: Sunucu üzerinde bir çalışma kitabındaki önbelleğe alınmış verileri değiştirme
  Bu kılavuzda, sınıfını kullanarak veri kümelerini başlatmadan Microsoft Office Excel bir Excel veri kümesinde nasıl değişiklik <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> göstereceğiz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- AdventureWorksLT veritabanından veri içeren bir veri kümesi tanımlama.

- Bir çalışma kitabı projesinde ve konsol uygulaması Excel veri kümesi örnekleri oluşturma.

- Çalışma kitabındaki veri kümesine bağlı bir oluşturma ve çalışma kitabı açıldığında <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> verilerle doldurmak.

- Çalışma kitabındaki veri kümelerini veri önbelleğine ekleme.

- Konsol uygulamasında kod çalıştırarak önbelleğe alınmış veri kümesinde bir veri sütununu değiştirme, Excel.

  Bu kılavuz, kodu geliştirme bilgisayarınızda çalıştırmış olduğunu varsaysa da, bu izlenecek yol tarafından belirtilen kod, yüklü yüklü Excel kullanılabilir.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [bkz. IDE'Visual Studio kişiselleştirme.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- AdventureWorksLT örnek veritabanının Microsoft SQL Server veya Microsoft SQL Server Express örneğine erişim. AdventureWorksLT veritabanını SQL Server Samples [GitHub indirebilirsiniz.](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak veritabanı eklemek için [bkz. Nasıl kullanılır: Veritabanı ekleme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırı kullanarak veritabanı eklemek için bkz. [Nasıl kullanılır:](/previous-versions/sql/)Veritabanı dosyasını SQL Server Express.

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Veri kümesi tanımlayan bir sınıf kitaplığı projesi oluşturma
 Aynı veri kümesini bir Excel çalışma kitabı projesinde ve konsol uygulamasında kullanmak için, veri kümesini bu projelerin her ikisi tarafından da başvurulan ayrı bir derlemede tanımlamanız gerekir. Bu kılavuz için bir sınıf kitaplığı projesinde veri kümesi tanımlayın.

### <a name="to-create-the-class-library-project"></a>Sınıf kitaplığı projesini oluşturmak için

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** ardından Dosya'ya **Project.**

3. Şablonlar bölmesinde, Visual **C#** veya Visual Basic **genişletin** ve ardından **Windows.**

4. Proje şablonları listesinde Sınıf **Kitaplığı'ı seçin.**

5. Ad **kutusuna** **AdventureWorksDataSet yazın.**

6. **Gözat'a** tıklayın, *%UserProfile%\Belgelerim* (Windows XP ve önceki sürümler için) veya *%UserProfile%\Documents* (Windows Vista için) klasörüne gidin ve Klasör Seç'e **tıklayın.**

7. Yeni **Project** iletişim kutusunda Çözüm için **dizin oluştur onay kutusunun seçili** olduğundan emin olun.

8. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**AdventureWorksDataSet projesini**  Çözüm Gezgini **class1.cs veya Class1.vb** **kod** dosyasını açar.

9. Bu **Çözüm Gezgini** **Class1.cs veya Class1.vb'ye** sağ **tıklayın** ve ardından Sil'e **tıklayın.** Bu kılavuz için bu dosyaya ihtiyacınız yok.

## <a name="define-a-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde veri kümesi tanımlama
 SQL Server 2005 için AdventureWorksLT veritabanından veri içeren türü SQL Server tanımlayın. Bu kılavuzun devamlarında, bu veri kümesine bir Excel çalışma kitabı projesinden ve konsol uygulaması projesinden başvuracağız.

 Veri kümesi, AdventureWorksLT *veritabanının* Product tablosunda yer alan verileri temsil eden türü belirli bir veri kümesidir. Türü yazilen veri kümeleri hakkında daha fazla bilgi için [bkz.](../data-tools/dataset-tools-in-visual-studio.md)Visual Studio.

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde türü belirli bir veri kümesi tanımlamak için

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

9. Bu **Çözüm Gezgini** **AdventureWorksDataSet'e sağ tıklayın ve Derleme'ye** **tıklayın.**

     Projenin hatasız olarak derlemesini doğrulayın.

## <a name="create-an-excel-workbook-project"></a>Çalışma kitabı Excel oluşturma
 Verilere Excel için bir çalışma kitabı projesi oluşturun. Bu kılavuzda daha sonra verileri görüntüleyen bir oluşturacak ve çalışma kitabındaki veri önbelleğine veri kümesi <xref:Microsoft.Office.Tools.Excel.ListObject> örneği eklenecektir.

### <a name="to-create-the-excel-workbook-project"></a>Excel çalışma kitabı projesini oluşturmak için

1. Bu **Çözüm Gezgini** **AdventureWorksDataSet** çözümüne sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından Yeni Çalışma **Project.**

2. Şablonlar bölmesinde, Visual **C#** veya Visual Basic **genişletin** ve sonra da **Office.**

3. Genişletilmiş **Office** **2010 düğümünü** seçin.

4. Proje şablonları listesinde Çalışma Kitabı projesini Excel seçin.

5. Ad **kutusuna** **AdventureWorksReport yazın.** Konumu değiştirmeyin.

6. **Tamam**'a tıklayın.

     Office için Visual Studio Araçları Project **Sihirbazı** açılır.

7. Yeni belge **oluştur'u seçin ve** Tamam'a **tıklayın.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**AdventureWorksReport çalışma kitabını** tasarımcıda açar ve **AdventureWorksReport** projesini **Çözüm Gezgini.**

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Çalışma kitabı projesinde veri Excel ekleme
 Veri kümelerini çalışma kitabınızda görüntüley Excel önce çalışma kitabı projesinde veri Excel eklemeniz gerekir.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Veri kümelerini çalışma kitabı projesinde veri kaynaklarına Excel için

1. Bu **Çözüm Gezgini** **AdventureWorksReport** projesinin altında **Sheet1.cs veya Sheet1.vb'ye** çift tıklayın. 

     Çalışma kitabı tasarımcıda açılır.

2. Veri menüsünde **Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

     Veri **Kaynağı Yapılandırma Sihirbazı** açılır.

3. **Nesne'ye** ve ardından Sonraki **'ye tıklayın.**

4. Bağlamak **istediğiniz Nesneyi Seçin sayfasında Başvuru Ekle'ye** **tıklayın.**

5. Projeler sekmesinde **AdventureWorksDataSet'e ve ardından** Tamam'a **tıklayın.** 

6. **AdventureWorksDataSet** **derlemenin AdventureWorksDataSet** ad alanı altında **AdventureWorksLTDataSet'e** ve ardından Son'a **tıklayın.**

     Veri **Kaynakları** penceresi açılır ve **AdventureWorksLTDataSet** veri kaynakları listesine eklenir.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Veri kümesi örneğine bağlı bir ListObject oluşturma
 Çalışma kitabında veri kümesi görüntülemek için veri <xref:Microsoft.Office.Tools.Excel.ListObject> kümesi örneğine bağlı bir oluşturun. Verilere denetimler bağlama hakkında daha fazla bilgi için [bkz. Veri bağlama çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Veri kümesi örneğine bağlı bir ListObject oluşturmak için

1. Veri Kaynakları **penceresinde** **AdventureWorksDataSet altındaki AdventureWorksLTDataSet** **düğümünü genişletin.**

2. Ürün **düğümünü** seçin, görüntülenen açılan oka tıklayın ve açılan listeden **ListObject** öğesini seçin.

     Açılan ok görünmüyorsa çalışma kitabının tasarımcıda açık olduğunu onaylayın.

3. Product **tabloyu** A1 hücresine sürükleyin.

     Çalışma <xref:Microsoft.Office.Tools.Excel.ListObject> sayfasında `productListObject` A1 hücresinde başlayarak adlı bir denetim oluşturulur. Aynı zamanda, ve adlı bir veri `adventureWorksLTDataSet` kümesi <xref:System.Windows.Forms.BindingSource> nesnesi projeye `productBindingSource` eklenir. <xref:Microsoft.Office.Tools.Excel.ListObject>, veri kümesi <xref:System.Windows.Forms.BindingSource> nesnesine bağlı olan nesnesine bağlı olur.

## <a name="add-the-dataset-to-the-data-cache"></a>Veri kümesi veri önbelleğine ekleme
 çalışma kitabındaki veri kümesine erişmek üzere Excel çalışma kitabı projesinin dışındaki kodu etkinleştirmek için veri kümesini veri önbelleğine eklemeniz gerekir. Veri önbelleği hakkında daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerde önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md) ve [Önbellek verileri](../vsto/caching-data.md).

### <a name="to-add-the-dataset-to-the-data-cache"></a>Veri kümesini veri önbelleğine eklemek için

1. Tasarımcıda **AdventureWorksLTDataSet**' e tıklayın.

2. **Özellikler** penceresinde **değiştiriciler** özelliğini **Public** olarak ayarlayın.

3. **CacheInDocument** özelliğini **true** olarak ayarlayın.

## <a name="initialize-the-dataset-in-the-workbook"></a>Çalışma kitabındaki veri kümesini başlatma
 Konsol uygulamasını kullanarak önbelleğe alınmış veri kümesinden verileri almak için önce önbelleğe alınmış veri kümesini verilerle doldurmanız gerekir.

### <a name="to-initialize-the-dataset-in-the-workbook"></a>Çalışma kitabında veri kümesini başlatmak için

1. **Çözüm Gezgini**, **Sheet1. cs** veya **Sayfa1. vb** dosyasını sağ tıklayın ve **kodu görüntüle**' ye tıklayın.

2. `Sheet1_Startup`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod, `ProductTableAdapter` Şu anda boşsa, verileri önbelleğe alınmış veri kümesini dolduracak şekilde, **AdventureWorksDataSet** projesinde tanımlanan sınıfının bir örneğini kullanır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb" id="Snippet8":::

## <a name="checkpoint"></a>Checkpoint
 Excel çalışma kitabı projesi oluşturup çalıştırarak, hatasız bir şekilde derlendiğinden ve çalıştığından emin olun. Bu işlem, önbelleğe alınmış veri kümesini de doldurur ve verileri çalışma kitabına kaydeder.

### <a name="to-build-and-run-the-project"></a>Projeyi derleyip çalıştırmak için

1. **Çözüm Gezgini**, **AdventureWorksReport** projesine sağ tıklayın, **Hata Ayıkla**' yı seçin ve ardından **Yeni örnek Başlat**' ı tıklatın.

     Proje oluşturulur ve çalışma kitabı Excel açılır. Aşağıdakileri doğrulayın:

    - <xref:Microsoft.Office.Tools.Excel.ListObject>Veriler ile doldurulur.

    - Öğesinin ilk satırı için **ListPrice** sütunundaki değer <xref:Microsoft.Office.Tools.Excel.ListObject> 1431,5 ' dir. Bu izlenecek yolda daha sonra, **ListPrice** sütunundaki değerleri değiştirmek için bir konsol uygulaması kullanacaksınız.

2. Çalışma kitabını kaydedin. Dosya adını veya çalışma kitabının konumunu değiştirmeyin.

3. Excel kapatın.

## <a name="create-a-console-application-project"></a>Konsol uygulaması projesi oluşturma
 Çalışma kitabındaki önbelleğe alınmış veri kümesindeki verileri değiştirmek için kullanılacak bir konsol uygulaması projesi oluşturun.

### <a name="to-create-the-console-application-project"></a>Konsol uygulaması projesi oluşturmak için

1. **Çözüm Gezgini**, **AdventureWorksDataSet** çözümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **yeni Project**' ye tıklayın.

2. **Project türleri** bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Windows**' ye tıklayın.

3. **Şablonlar** bölmesinde **konsol uygulaması**' nı seçin.

4. **Ad** kutusuna **DataWriter** yazın. Konumu değiştirmeyin.

5. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**DataWriter** projesini **Çözüm Gezgini** ekler ve **program. cs** veya **Module1. vb** kod dosyasını açar.

## <a name="change-data-in-the-cached-dataset-by-using-the-console-application"></a>Konsol uygulamasını kullanarak önbelleğe alınmış veri kümesindeki verileri değiştirme
 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Verileri yerel bir nesne içine okumak `AdventureWorksLTDataSet` , bu verileri değiştirmek ve sonra önbelleğe alınmış veri kümesine geri kaydetmek için konsol uygulamasındaki sınıfını kullanın.

### <a name="to-change-data-in-the-cached-dataset"></a>Önbelleğe alınmış veri kümesindeki verileri değiştirmek için

1. **Çözüm Gezgini**, **DataWriter** projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

2. **.Net** sekmesinde, **Microsoft. VisualStudio. Tools. Applications**' ı seçin.

3. **Tamam**'a tıklayın.

4. **Çözüm Gezgini**, **DataWriter** projesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

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
     > Aşağıdaki kod, *.xlsx* dosya uzantısına sahip bir çalışma kitabı kullandığınızı varsayar. Projenizdeki çalışma kitabının farklı bir dosya uzantısı varsa, yolu gereken şekilde değiştirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet6":::

9. `Main`Önceki adımda eklediğiniz koddan sonra yöntemine aşağıdaki kodu ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Çalışma kitabındaki önbelleğe alınmış veri kümesine erişmek için sınıfının özelliğini kullanır.

   - Önbelleğe alınmış veri kümesindeki verileri yerel veri kümesine okur.

   - `ListPrice`Veri kümesinin ürün tablosundaki her ürünün değerini değiştirir.

   - Çalışma kitabındaki önbelleğe alınmış veri kümesine değişiklikleri kaydeder.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet7":::

10. **Çözüm Gezgini**, **DataWriter** projesine sağ tıklayın, **Hata Ayıkla**' nın üzerine gelin ve ardından **Yeni örnek Başlat**' a tıklayın.

     Konsol uygulaması, önbelleğe alınmış veri kümesini yerel veri kümesine okurken iletileri görüntüler, yerel veri kümesindeki ürün fiyatlarını değiştirir ve yeni değerleri önbelleğe alınmış veri kümesine kaydeder. Uygulamayı kapatmak için **ENTER** tuşuna basın.

## <a name="test-the-workbook"></a>Çalışma kitabını test etme
 Çalışma kitabını açtığınızda, <xref:Microsoft.Office.Tools.Excel.ListObject> artık `ListPrice` önbelleğe alınmış veri kümesindeki verilerin sütununda yaptığınız değişiklikleri görüntüler.

### <a name="to-test-the-workbook"></a>Çalışma kitabını test etmek için

1. hala açıksa, Visual Studio tasarımcısında AdventureWorksReport çalışma kitabını kapatın.

2. **AdventureWorksReport** projesinin Build klasöründeki AdventureWorksReport çalışma kitabını açın. Varsayılan olarak, derleme klasörü aşağıdaki konumlardan birinde bulunur:

    - *%userprofıle%\my Documents\AdventureWorksReport\bin\Debug* (Windows XP ve önceki sürümleri için)

    - *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* (Windows Vista için)

3. Öğesinin ilk satırı için **ListPrice** sütunundaki değerin <xref:Microsoft.Office.Tools.Excel.ListObject> artık 1574,65 olduğunu doğrulayın.

4. Çalışma kitabını kapatın.

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: sunucudaki çalışma kitabına veri ekleme](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
