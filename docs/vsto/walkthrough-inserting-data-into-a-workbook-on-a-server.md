---
title: 'İzlenecek yol: sunucudaki çalışma kitabına veri ekleme'
description: ServerDocument sınıfını kullanarak Excel başlatmadan Microsoft Excel çalışma kitabında önbelleğe alınan bir veri kümesine veri eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
- workbooks [Office development in Visual Studio], inserting data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 376c0c4a51fa6d4514af403322956f60bfe9fad3
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127890"
---
# <a name="walkthrough-insert-data-into-a-workbook-on-a-server"></a>İzlenecek yol: sunucudaki çalışma kitabına veri ekleme
  bu izlenecek yol, sınıfını kullanarak Excel başlatmadan Microsoft Office Excel çalışma kitabında önbelleğe alınan bir veri kümesine veri eklemeyi gösterir <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> .

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- AdventureWorksLT veritabanından veri içeren bir veri kümesi tanımlama.

- Excel çalışma kitabı projesinde ve konsol uygulaması projesinde veri kümesinin örneklerini oluşturma.

- <xref:Microsoft.Office.Tools.Excel.ListObject>Çalışma kitabındaki veri kümesine bağlanan bir oluşturma.

- Çalışma kitabındaki veri kümesini veri önbelleğine ekleme.

- Excel başlatmadan, konsol uygulamasındaki kodu çalıştırarak önbelleğe alınmış veri kümesine veri ekleme.

  bu izlenecek yol, geliştirme bilgisayarınızda kodu çalıştırdığınız varsayılmaktadır, ancak bu izlenecek yol tarafından gösterilen kod Excel yüklü olmayan bir sunucuda kullanılabilir.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- AdventureWorksLT örnek veritabanının eklendiği Microsoft SQL Server veya Microsoft SQL Server Express çalışan bir örneğine erişim. AdventureWorksLT veritabanını [CodePlex Web sitesinden](/sql/samples/adventureworks-install-configure)indirebilirsiniz. Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak bir veritabanı eklemek için bkz. [nasıl yapılır: veritabanı iliştirme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırını kullanarak bir veritabanı eklemek için, bkz. [nasıl yapılır: SQL Server Express veritabanı dosyası iliştirme](/previous-versions/sql/).

## <a name="create-a-class-library-project-that-defines-a-dataset"></a>Veri kümesini tanımlayan bir sınıf kitaplığı projesi oluşturma
 aynı veri kümesini bir Excel çalışma kitabı projesinde ve bir konsol uygulamasında kullanmak için, veri kümesini bu projelerin her ikisi tarafından başvurulan ayrı bir derlemede tanımlamanız gerekir. Bu izlenecek yol için bir sınıf kitaplığı projesinde veri kümesini tanımlayın.

### <a name="to-create-the-class-library-project"></a>Sınıf kitaplığı projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Project**' ye tıklayın.

3. şablonlar bölmesinde, **Visual C#** veya **Visual Basic** öğesini genişletin ve ardından **Windows**' e tıklayın.

4. Proje şablonları listesinde, **sınıf kitaplığı**' nı seçin.

5. **Ad** kutusuna **AdventureWorksDataSet** yazın.

6. **araştır**' a tıklayın, *%userprofıle%\my belgelerinize* (Windows XP ve önceki sürümler) veya *%userprofile%\documents* (Windows Vista için) klasörüne gidin ve ardından **klasör seç**' e tıklayın.

7. **yeni Project** iletişim kutusunda, **çözüm için dizin oluştur** onay kutusunun seçili olmadığından emin olun.

8. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Çözüm Gezgini** Için bir **AdventureWorksDataSet** projesi ekler ve **Class1. cs** veya **Class1. vb** kod dosyasını açar.

9. **Çözüm Gezgini**, **Class1. cs** veya **Class1. vb** öğesine sağ tıklayın ve ardından **Sil**' e tıklayın. Bu izlenecek yol için bu dosyaya ihtiyacınız yoktur.

## <a name="define-a-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde bir veri kümesi tanımlama
 SQL Server 2005 için AdventureWorksLT veritabanından veri içeren bir türü belirtilmiş veri kümesi tanımlayın. bu izlenecek yolda daha sonra, bu veri kümesine bir Excel çalışma kitabı projesinden ve konsol uygulaması projesinden başvurabileceksiniz.

 Veri kümesi, AdventureWorksLT veritabanının Product tablosundaki verileri temsil eden *türsüz bir veri* kümesidir. Türü belirtilmiş veri kümeleri hakkında daha fazla bilgi için bkz. [Visual Studio veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md).

### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Sınıf kitaplığı projesinde türü belirtilmiş bir veri kümesini tanımlamak için

1. **Çözüm Gezgini**' de, **AdventureWorksDataSet** projesine tıklayın.

2. **veri kaynakları** penceresi görünür değilse, menü çubuğunda,   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçerek bunu görüntüleyin.

3. **Veri kaynağı Yapılandırma Sihirbazı 'nı** başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

4. **Veritabanı**' na ve ardından **İleri**' ye tıklayın.

5. AdventureWorksLT veritabanına mevcut bir bağlantınız varsa, bu bağlantıyı seçin ve **İleri**' ye tıklayın.

    Aksi takdirde, **Yeni bağlantı**' ya tıklayın ve yeni bağlantıyı oluşturmak Için **bağlantı ekle** iletişim kutusunu kullanın. daha fazla bilgi için bkz. [nasıl yapılır: veritabanındaki verileri Bağlan](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md).

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
 veri arabirimi için bir Excel çalışma kitabı projesi oluşturun. Bu kılavuzda daha sonra, verileri görüntüleyen bir oluşturacak <xref:Microsoft.Office.Tools.Excel.ListObject> ve veri kümesinin bir örneğini çalışma kitabındaki veri önbelleğine ekleyeceksiniz.

### <a name="to-create-the-excel-workbook-project"></a>Excel çalışma kitabı projesi oluşturmak için

1. **Çözüm Gezgini**, **AdventureWorksDataSet** çözümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **yeni Project**' ye tıklayın.

2. şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' yı genişletin.

3. genişletilmiş **Office/SharePoint** düğümü altında **Office eklentileri** düğümünü seçin.

4. proje şablonları listesinde **Excel 2010 çalışma** kitabını veya **Excel 2013 çalışma kitabı** projesini seçin.

5. **Ad** kutusuna **AdventureWorksReport** yazın. Konumu değiştirmeyin.

6. **Tamam**'a tıklayın.

     **Office için Visual Studio Araçları Project sihirbazı** açılır.

7. **Yeni bir belge oluştur** ' un seçili olduğundan emin olun ve **Tamam**' ı tıklatın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]tasarımcıda **AdventureWorksReport** çalışma kitabını açar ve **Çözüm Gezgini** **AdventureWorksReport** projesini ekler.

## <a name="add-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Excel çalışma kitabı projesindeki veri kaynaklarına veri kümesini ekleme
 veri kümesini Excel çalışma kitabında görüntüleyebilmeniz için önce, önce Excel çalışma kitabı projesindeki veri kaynaklarına veri kümesini eklemeniz gerekir.

### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>veri kümesini Excel çalışma kitabı projesindeki veri kaynaklarına eklemek için

1. **Çözüm Gezgini**, **AdventureWorksReport** projesi altında **Sheet1. cs** veya **Sayfa1. vb** ' ye çift tıklayın.

     Çalışma kitabı tasarımcıda açılır.

2. **Veri** menüsünde **Yeni veri kaynağı Ekle**' ye tıklayın.

     **Veri kaynağı Yapılandırma Sihirbazı** açılır.

3. **Nesne**' ye ve ardından **İleri**' ye tıklayın.

4. **Bağlamak Istediğiniz nesneyi seçin** sayfasında, **Başvuru Ekle**' ye tıklayın.

5. **Projeler** sekmesinde, **AdventureWorksDataSet** ' e ve ardından **Tamam**' a tıklayın.

6. **AdventureWorksDataSet** derlemesinin **AdventureWorksDataSet** ad alanı altında, **AdventureWorksLTDataSet** ' e ve ardından **son**' a tıklayın.

     **Veri kaynakları** penceresi açılır ve **AdventureWorksLTDataSet** veri kaynakları listesine eklenir.

## <a name="create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Veri kümesinin örneğine bağlanan bir ListObject oluşturma
 Çalışma kitabında veri kümesini göstermek için bir <xref:Microsoft.Office.Tools.Excel.ListObject> veri kümesinin örneğine bağlanan bir oluşturun. verilere yönelik bağlama denetimleri hakkında daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Veri kümesinin bir örneğine bağlanan bir ListObject oluşturmak için

1. **Veri kaynakları** penceresinde, **AdventureWorksDataSet** altındaki **AdventureWorksLTDataSet** düğümünü genişletin.

2. **Ürün** düğümünü seçin, görüntülenen aşağı açılan oka tıklayın ve açılan listeden **ListObject** ' i seçin.

     Aşağı açılan ok görünmezse, çalışma kitabının tasarımcıda açık olduğunu onaylayın.

3. **Ürün** tablosunu a1 hücresine sürükleyin.

     <xref:Microsoft.Office.Tools.Excel.ListObject> `productListObject` Çalışma sayfasında A1 hücresinden başlayarak adlı bir denetim oluşturulur. Aynı zamanda, adlı ve adlı bir veri kümesi nesnesi `adventureWorksLTDataSet` <xref:System.Windows.Forms.BindingSource> `productBindingSource` projeye eklenir. , <xref:Microsoft.Office.Tools.Excel.ListObject> ' A bağlanır ve <xref:System.Windows.Forms.BindingSource> veri kümesi nesnesine bağlanır.

## <a name="add-the-dataset-to-the-data-cache"></a>Veri kümesi veri önbelleğine ekleme
 Çalışma kitabı projesinin Excel çalışma kitabındaki veri kümesine erişmesini sağlamak için veri kümesine veri önbelleğini eklemeniz gerekir. Veri önbelleği hakkında daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerde önbelleğe alınmış veriler ve](../vsto/cached-data-in-document-level-customizations.md) [Önbellek verileri.](../vsto/caching-data.md)

### <a name="to-add-the-dataset-to-the-data-cache"></a>Veri kümesi veri önbelleğine eklemek için

1. Tasarımcıda **adventureWorksLTDataSet'e tıklayın.**

2. Özellikler **penceresinde** Değiştiriciler **özelliğini Genel** olarak **ayarlayın.**

3. **CacheInDocument özelliğini** True olarak **ayarlayın.**

## <a name="checkpoint"></a>Checkpoint
 Derlemesini ve hatasız Excel emin olmak için Excel çalışma kitabı projesini derle ve çalıştır.

### <a name="to-build-and-run-the-project"></a>Projeyi derleyip çalıştırmak için

1. Bu **Çözüm Gezgini** **AdventureWorksReport** projesine sağ tıklayın, Hata Ayıkla'yı **seçin** ve ardından Yeni örneği **başlat'a tıklayın.**

     Proje yerleşiktir ve çalışma kitabı Excel. <xref:Microsoft.Office.Tools.Excel.ListObject> **Sayfa1'de** boştur çünkü `adventureWorksLTDataSet` veri önbelleğinde nesne henüz veriye sahip değildir. Sonraki bölümde, nesneyi verilerle doldurmak için bir konsol `adventureWorksLTDataSet` uygulaması kullansınız.

2. Excel. Değişiklikleri kaydetme.

## <a name="create-a-console-application-project"></a>Konsol uygulaması projesi oluşturma
 Çalışma kitabındaki önbelleğe alınmış veri kümesine veri eklemek için kullanmak üzere bir konsol uygulaması projesi oluşturun.

### <a name="to-create-the-console-application-project"></a>Konsol uygulaması projesini oluşturmak için

1. Bu **Çözüm Gezgini** **AdventureWorksDataSet** çözümüne sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından Yeni Çalışma **Project.**

2. Project **Türleri** **bölmesinde, Visual C#** veya **Visual Basic** genişletin ve ardından **Windows'a tıklayın.**

3. Şablonlar **bölmesinde Konsol** Uygulaması'nu **seçin.**

4. Ad **kutusuna** **DataWriter yazın.** Konumu değiştirmeyin.

5. **Tamam**'a tıklayın.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] DataWriter **projesini** **Çözüm Gezgini** **program.cs veya** **Module1.vb kod** dosyasını açar.

## <a name="add-data-to-the-cached-dataset-by-using-the-console-application"></a>Konsol uygulamasını kullanarak önbelleğe alınmış veri kümesine veri ekleme
 Çalışma <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> kitabındaki önbelleğe alınmış veri kümelerini verilerle doldurmak için konsol uygulamasındaki sınıfını kullanın.

### <a name="to-add-data-to-the-cached-dataset"></a>Önbelleğe alınan veri kümesine veri eklemek için

1. Bu **Çözüm Gezgini** **DataWriter** projesine sağ tıklayın ve Başvuru Ekle'ye **tıklayın.**

2. **.NET sekmesinde** **Microsoft.VisualStudio.Tools.Applications.ServerDocument öğesini seçin.**

3. **Tamam**'a tıklayın.

4. Bu **Çözüm Gezgini** **DataWriter** projesine sağ tıklayın ve Başvuru Ekle'ye **tıklayın.**

5. Projeler sekmesinde **AdventureWorksDataSet öğesini seçin ve** Tamam'a **tıklayın.** 

6. Kod *Düzenleyicisi'nde Program.cs* *veya Module1.vb* dosyasını açın.

7. Aşağıdaki using  (C#) veya **Imports** (for Visual Basic) deyimini kod dosyasının en üstüne ekleyin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet1":::

8. `Main` yöntemine aşağıdaki kodu ekleyin. Bu kod aşağıdaki nesneleri bildirer:

   - `AdventureWorksLTDataSet` `ProductTableAdapter` **AdventureWorksDataSet** projesinde tanımlanan ve türlerinin örnekleri.

   - AdventureWorksReport projesinin derleme klasöründeki **AdventureWorksReport çalışma kitabının** yolu.

   - Çalışma <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> kitabındaki veri önbelleğine erişmek için kullanabileceğiniz nesne.

     > [!NOTE]
     > Aşağıdaki kod, dosya uzantısını içeren bir çalışma kitabı *.xlsx* varsayır. Projenizin çalışma kitabı farklı bir dosya uzantısına sahipse, yolu gereken şekilde değiştirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet3":::

9. Aşağıdaki kodu `Main` yöntemine, önceki adımda ekley istediğiniz kodun ardından ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Tablo bağdaştırıcısını kullanarak türüne göre türü doğru olan veri kümesi nesnesini doldurur.

   - Çalışma <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> kitabındaki önbelleğe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> alınmış veri kümesine erişmek için sınıfının özelliğini kullanır.

   - Önbelleğe <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> alınmış veri kümelerini yerel türü yerel veri kümesinden gelen verilerle doldurmak için yöntemini kullanır.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb" id="Snippet4":::

10. Bu **Çözüm Gezgini** **DataWriter** projesine sağ tıklayın, Hata Ayıkla'nın üzerine **gelin** ve ardından Yeni örneği **başlat'a tıklayın.**

     Proje yerleşiktir ve konsol uygulaması yerel veri kümesi doldurulan ve uygulama verileri çalışma kitabındaki önbelleğe alınmış veri kümesine kaydeden birkaç durum mesajı görüntüler. Uygulamayı kapatmak için **Enter** tuşuna basın.

## <a name="test-the-workbook"></a>Çalışma kitabını test etmek
 Çalışma kitabını açsanız, konsol uygulaması kullanılarak önbelleğe alınan <xref:Microsoft.Office.Tools.Excel.ListObject> veri kümesine eklenen veriler görüntülenir.

### <a name="to-test-the-workbook"></a>Çalışma kitabını test etmek için

1. Hala açıksa, Visual Studio tasarımcıda AdventureWorksReport çalışma kitabını kapatın.

2. Bu Dosya Gezgini AdventureWorksReport projesinin derleme klasöründeki **AdventureWorksReport çalışma kitabını** açın. Varsayılan olarak, derleme klasörü aşağıdaki konumlardan biri içindedir:

    - *%UserProfile%\Belgelerim\AdventureWorksReport\bin\Debug* (Windows XP ve önceki sürümler için)

    - *%UserProfile%\Documents\AdventureWorksReport\bin\Debug* (Windows Vista için)

3. çalışma kitabını <xref:Microsoft.Office.Tools.Excel.ListObject> açtıktan sonra verilerle doldurulduğundan emin olun.

## <a name="next-steps"></a>Sonraki adımlar

Önbelleğe alınmış verilerle çalışma hakkında daha fazla bilgi edinmek için şu konulardan bilgi edinmek için:

- Önbelleğe alınmış bir veri kümesinde verileri, veri kümesine başlamadan Excel. Daha fazla bilgi için [bkz. Adım adım kılavuz: Sunucusundaki bir çalışma kitabındaki önbelleğe alınmış verileri değiştirme.](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: Sunucu üzerinde bir çalışma kitabındaki önbelleğe alınmış verileri değiştirme](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)
