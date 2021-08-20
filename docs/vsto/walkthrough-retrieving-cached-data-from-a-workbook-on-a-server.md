---
title: 'Adım adım kılavuz: Sunucu üzerinde bir çalışma kitabından önbelleğe alınmış verileri alma'
description: ServerDocument sınıfını kullanarak veri kümelerini başlatmadan Microsoft Excel bir veri kümesinden Excel nasıl alasınız?
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
ms.openlocfilehash: e2a84857f6ad3e58430538e2656b31869f9a4bbe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155427"
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

- AdventureWorksLT örnek veritabanının Microsoft SQL Server veya Microsoft SQL Server Express örnek veritabanına erişim. AdventureWorksLT veritabanını CodePlex web [sitesinden indirebilirsiniz.](https://archive.codeplex.com/?p=SqlServerSamples) Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak veritabanı eklemek için [bkz. Nasıl kullanılır: Veritabanı ekleme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırı kullanarak veritabanı eklemek için bkz. [Nasıl kullanılır:](/previous-versions/sql/)Veritabanı dosyasını SQL Server Express.

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Veri kümesi tanımlayan bir sınıf kitaplığı projesi oluşturma
 Aynı veri kümesini bir Excel çalışma kitabı projesinde ve konsol uygulamasında kullanmak için, veri kümesini bu projelerin her ikisi tarafından da başvurulan ayrı bir derlemede tanımlamanız gerekir. Bu kılavuz için bir sınıf kitaplığı projesinde veri kümesi tanımlayın.

### <a name="create-the-class-library-project"></a>Sınıf kitaplığı projesini oluşturma

1. 'i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] başlatma.

2. Dosya menüsünde **Yeni'nin** üzerine **gelin ve** ardından Dosya'ya **Project.**

3. Şablonlar bölmesinde, Visual **C#** veya Visual Basic **genişletin** ve ardından **Windows.**

4. Proje şablonları listesinde Sınıf **Kitaplığı'ı seçin.**

5. Ad **kutusuna** **AdventureWorksDataSet yazın.**

6. **Gözat'a** tıklayın, *%UserProfile%\Belgelerim* (Windows XP ve önceki sürümler için) veya *%UserProfile%\Documents* (Windows Vista için) klasörüne gidin ve Klasör Seç'e **tıklayın.**

7. Yeni **Project** iletişim kutusunda Çözüm için **dizin oluştur onay kutusunun seçili** olduğundan emin olun.

8. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**AdventureWorksDataSet projesini**  Çözüm Gezgini *class1.cs veya Class1.vb* *kod* dosyasını açar.

9. Bu **Çözüm Gezgini** *Class1.cs veya Class1.vb'ye* sağ *tıklayın* ve ardından Sil'e **tıklayın.** Bu kılavuz için bu dosyaya ihtiyacınız yok.

## <a name="define-a-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde veri kümesi tanımlama
 SQL Server 2005 için AdventureWorksLT veritabanından veri içeren türü SQL Server tanımlayın. Bu kılavuzun devamlarında, bu veri kümesine bir Excel çalışma kitabı projesinden ve konsol uygulaması projesinden başvuracağız.

 Veri kümesi, AdventureWorksLT *veritabanının* Product tablosunda yer alan verileri temsil eden türü belirli bir veri kümesidir. Türü türüne sahip veri kümeleri hakkında daha fazla bilgi için [bkz.](../data-tools/dataset-tools-in-visual-studio.md)Visual Studio.

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

9. Bu **Çözüm Gezgini** **AdventureWorksDataSet'e sağ tıklayın ve Derleme'ye** **tıklayın.**

     Projenin hatasız olarak derlemesini doğrulayın.

## <a name="create-an-excel-workbook-project"></a>Çalışma kitabı Excel oluşturma
 Verilere Excel için bir çalışma kitabı projesi oluşturun. Bu kılavuzda daha sonra verileri görüntüleyen bir oluşturacak ve çalışma kitabındaki veri önbelleğine veri kümesi <xref:Microsoft.Office.Tools.Excel.ListObject> örneği eklenecektir.

### <a name="create-the-excel-workbook-project"></a>Çalışma kitabı Excel oluşturma

1. Bu **Çözüm Gezgini** **AdventureWorksDataSet** çözümüne sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından Yeni Çalışma **Project.**

2. Şablonlar bölmesinde Visual **C#** veya **Visual Basic'ı** genişletin ve sonra **Office/SharePoint.**

3. Genişletilmiş **Office/SharePoint** altında, **Office düğümünü** seçin.

4. Proje şablonları listesinde, Excel **2010** Çalışma Kitabı'Excel **2013 Çalışma Kitabı projesini** seçin.

5. Ad **kutusuna** **AdventureWorksReport yazın.** Konumu değiştirmeyin.

6. **Tamam**'a tıklayın.

     Office için Visual Studio Araçları Project **Sihirbazı** açılır.

7. Yeni belge **oluştur seçeneğinin seçili olduğundan** emin olun ve Tamam'a **tıklayın.**

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**AdventureWorksReport çalışma kitabını** tasarımcıda açar ve **AdventureWorksReport** projesini **Çözüm Gezgini.**

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Veri kümesi çalışma kitabı projesinde veri Excel ekleme
 Veri kümelerini çalışma kitabınızda Excel önce çalışma kitabı projesinde veri Excel eklemeniz gerekir.

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

3. Product **tabloyu** A1 hücresine sürükleyin.

     Çalışma <xref:Microsoft.Office.Tools.Excel.ListObject> sayfasında `productListObject` A1 hücresinde başlayarak adlı bir denetim oluşturulur. Aynı zamanda, ve adlı bir veri `adventureWorksLTDataSet` kümesi <xref:System.Windows.Forms.BindingSource> nesnesi projeye `productBindingSource` eklenir. <xref:Microsoft.Office.Tools.Excel.ListObject>, veri kümesi <xref:System.Windows.Forms.BindingSource> nesnesine bağlı olan nesnesine bağlı olur.

## <a name="add-the-dataset-to-the-data-cache"></a>Veri kümesi veri önbelleğine ekleme
 Çalışma kitabı projesinin Excel çalışma kitabı projesinin dışındaki kodun çalışma kitabındaki veri kümesine erişmesini sağlamak için veri kümesine veri önbelleğini eklemeniz gerekir. Veri önbelleği hakkında daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler ve](../vsto/cached-data-in-document-level-customizations.md) [Önbellek verileri.](../vsto/caching-data.md)

1. Tasarımcıda **adventureWorksLTDataSet'e tıklayın.**

2. Özellikler **penceresinde** Değiştiriciler **özelliğini Genel** olarak **ayarlayın.**

3. **CacheInDocument özelliğini** True olarak **ayarlayın.**

## <a name="initialize-the-dataset-in-the-workbook"></a>Çalışma kitabında veri kümesi başlatma
 Konsol uygulamasını kullanarak önbelleğe alınmış veri kümesinden verileri aldan önce önbelleğe alınan veri kümesine verilerle doldurmak gerekir.

1. Bu **Çözüm Gezgini,** *Sheet1.cs veya Sheet1.vb* dosyasına sağ *tıklayın* ve Kodu **Görüntüle'ye tıklayın.**

2. Olay `Sheet1_Startup` işleyicisini aşağıdaki kodla değiştirin. Bu kod, önbelleğe alınmış veri kümesi şu anda boşsa verilerle doldurmak için `ProductTableAdapter` **AdventureWorksDataSet** projesinde tanımlanan sınıfının bir örneğini kullanır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb" id="Snippet8":::

## <a name="checkpoint"></a>Checkpoint
 Derlemesini ve hatasız Excel emin olmak için Excel çalışma kitabı projesini derle ve çalıştır. Bu işlem ayrıca önbelleğe alınan veri kümesini doldurur ve verileri çalışma kitabına kaydeder.

### <a name="build-and-run-the-project"></a>Projeyi derleme ve çalıştırma

1. Bu **Çözüm Gezgini** **AdventureWorksReport** projesine sağ tıklayın, Hata Ayıkla'yı **seçin** ve ardından Yeni örneği **başlat'a tıklayın.**

     Proje yerleşiktir ve çalışma kitabı Excel. Aşağıdakileri doğrulayın:

    - <xref:Microsoft.Office.Tools.Excel.ListObject>verilerle doldurur.

    - ListPrice **sütunundaki ilk** satırın değeri <xref:Microsoft.Office.Tools.Excel.ListObject> 1431,5'tir. Bu kılavuzda daha sonra **ListPrice** sütunundaki değerleri değiştirmek için bir konsol uygulaması kullanacağız.

2. Çalışma kitabını kaydedin. Dosya adını veya çalışma kitabının konumunu değiştirmeyin.

3. Excel.

## <a name="create-a-console-application-project"></a>Konsol uygulaması projesi oluşturma
 Çalışma kitabındaki önbelleğe alınmış veri kümesinde verileri değiştirmek için kullanmak üzere bir konsol uygulaması projesi oluşturun.

1. Bu **Çözüm Gezgini** **AdventureWorksDataSet** çözümüne sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından Yeni Çalışma **Project.**

2. Project **Türleri** **bölmesinde, Visual C#** veya **Visual Basic** genişletin ve ardından **Windows.**

3. Şablonlar **bölmesinde Konsol** Uygulaması'nu **seçin.**

4. Ad **kutusuna** **DataReader yazın.** Konumu değiştirmeyin.

5. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**DataReader projesini**  Çözüm Gezgini program.cs veya *Module1.vb kod* dosyasını açar. 

## <a name="retrieve-data-from-the-cached-dataset-by-using-the-console-application"></a>Konsol uygulamasını kullanarak önbelleğe alınmış veri kümesinden veri alma
 Verileri <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> yerel bir nesneye okumak için konsol uygulamasındaki sınıfını `AdventureWorksLTDataSet` kullanın. Uygulama, yerel veri kümesinde önbelleğe alınan veri kümesinden alınan verilerle başlatılmış olduğunu doğrulamak için yerel veri kümesinde satır sayısını görüntüler.

### <a name="retrieve-data-from-the-cached-dataset"></a>Önbelleğe alınan veri kümesinden veri alma

1. Bu **Çözüm Gezgini** **DataReader** projesine sağ tıklayın ve Başvuru Ekle'ye **tıklayın.**

2. **.NET sekmesinde** **Microsoft.VisualStudio.Tools.Applications.ServerDocument öğesini seçin.**

3. **Tamam**'a tıklayın.

4. Bu **Çözüm Gezgini** **DataReader** projesine sağ tıklayın ve Başvuru Ekle'ye **tıklayın.**

5. Projeler sekmesinde **AdventureWorksDataSet öğesini seçin ve** Tamam'a **tıklayın.** 

6. *Program.cs veya* *Module1.vb dosyasını* kod düzenleyicisinde açın.

7. Aşağıdaki using  (C#) veya **Imports** (for Visual Basic) deyimini kod dosyasının en üstüne ekleyin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet1":::

8. `Main` yöntemine aşağıdaki kodu ekleyin. Bu kod aşağıdaki nesneleri bildirer:

   - `AdventureWorksLTDataSet` **AdventureWorksDataSet** projesinde tanımlanan türün bir örneği.

   - AdventureWorksReport projesinin derleme klasöründeki **AdventureWorksReport çalışma kitabının** yolu.

   - Çalışma <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> kitabındaki veri önbelleğine erişmek için kullanabileceğiniz nesne.

     > [!NOTE]
     > Aşağıdaki kod, çalışma kitabının çalışma kitabı uzantısı kullanılarak *.xlsx* varsayıyor. Projenizin çalışma kitabı farklı bir uzantıya sahipse, yolu gereken şekilde değiştirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet10":::

9. Aşağıdaki kodu `Main` yöntemine, önceki adımda ekley istediğiniz kodun ardından ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Çalışma <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> kitabındaki önbelleğe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> alınmış veri kümesine erişmek için sınıfının özelliğini kullanır.

   - Önbelleğe alınan veri kümesinden yerel veri kümesine verileri okur.

   - Veriye sahip olduğunu onaylamak için yerel veri kümesinde satır sayısını görüntüler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet11":::

10. Build **(Derleme) menüsünde** Build **DataReader (Derleme VerileriOkuma) seçeneğine tıklayın.**

## <a name="test-the-project"></a>Projeyi test etme
 Konsol uygulamasını çalıştırarak yerel veri kümesinde satır sayısını görüntüler.

### <a name="test-the-workbook"></a>Çalışma kitabını test etmek

1. Bu **Çözüm Gezgini** **DataReader** projesine sağ tıklayın, Hata Ayıkla'nın üzerine **gelin** ve ardından Yeni örneği **başlat'a tıklayın.**

     Uygulamanın yerel veri kümesine 295 satır olduğunu rapor çalıştığını doğrulayın.

2. Uygulamayı kapatmak için **Enter** tuşuna basın.

## <a name="next-steps"></a>Sonraki adımlar
 Önbelleğe alınmış verilerle çalışma hakkında daha fazla bilgi edinmek için şu konulardan bilgi veebilirsiniz:

- Önbelleğe alınmış bir veri kümesinde verileri, veri kümesine başlamadan Excel. Daha fazla bilgi için [bkz. Adım adım: Sunucusundaki bir çalışma kitabındaki önbelleğe alınmış verileri değiştirme.](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: Sunucu üzerinde bir çalışma kitabına veri ekleme](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)
- [Adım adım kılavuz: Sunucu üzerinde bir çalışma kitabındaki önbelleğe alınmış verileri değiştirme](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
