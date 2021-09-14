---
title: 'Adım adım kılavuz: Eklenti projesinde VSTO karmaşık veri bağlama'
description: Çalışma zamanında bir çalışma sayfasına denetim Microsoft Excel ve denetimleri verilere bağlamayı öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8f9a554d485abf329a5f3a2933f306035cefa27c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726099"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Adım adım kılavuz: Eklenti projesinde VSTO karmaşık veri bağlama
  Eklenti projelerinde verileri konak denetimlerine Windows Forms VSTO bağlanabilirsiniz. Bu kılavuz, çalışma zamanında bir çalışma sayfasına Microsoft Office Excel ve denetimleri verilere bağlamayı gösterir.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma zamanında <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasına denetim ekleme.

- Denetimi <xref:System.Windows.Forms.BindingSource> bir veri kümesi örneğine bağlayan bir oluşturma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Örnek veritabanının bağlı olduğu SQL Server 2005 veya SQL Server 2005 Express çalıştıran `AdventureWorksLT` bir örneğine erişim. veritabanını SQL Server `AdventureWorksLT` [Samples GitHub indirebilirsiniz.](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak veritabanı eklemek için [bkz. Nasıl kullanılır: Veritabanı ekleme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırı kullanarak veritabanı eklemek için bkz. [Nasıl kullanılır:](/previous-versions/sql/)Veritabanı dosyasını SQL Server Express.

## <a name="create-a-new-project"></a>Yeni proje oluşturma
 İlk adım, bir eklenti Excel VSTO oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. Excel VSTO veya C# kullanarak Bir Veritabanındaki Çalışma Sayfalarını Doldurmak adına sahip bir Visual Basic projesi oluşturun.

     Daha fazla bilgi için, [bkz. How to: Create Office Projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     Visual Studio veya dosyasını açar ve Bir Veritabanı projesinde Yer Alan Çalışma `ThisAddIn.vb` `ThisAddIn.cs` **Sayfaları'Çözüm Gezgini.** 

## <a name="create-a-data-source"></a>Veri kaynağı oluşturma
 Projenize **türü** türüne göre bir veri kümesi eklemek için Veri Kaynakları penceresini kullanın.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Projeye türü türüne göre bir veri kümesi eklemek için

1. Veri **Kaynakları penceresi görünmüyorsa,** menü çubuğunda Diğer Kaynakları Görüntüle'Windows   >    >  **görüntüleniyor.**

2. Veri **Kaynağı Yapılandırma Sihirbazı'nı başlatmak** için Yeni Veri Kaynağı **Ekle'yi seçin.**

3. Veritabanı **'ne** ve ardından Sonraki'ye **tıklayın.**

4. Veritabanıyla mevcut bir bağlantınız varsa `AdventureWorksLT` bu bağlantıyı seçin ve Ardından'ya **tıklayın.**

    Aksi takdirde, **Yeni Bağlantı'ya** tıklayın **ve yeni bağlantıyı** oluşturmak için Bağlantı Ekle iletişim kutusunu kullanın. Daha fazla bilgi için [bkz. Yeni bağlantı ekleme.](../data-tools/add-new-connections.md)

5. Bağlantı **Dizesini Uygulama Yapılandırma Dosyasına Kaydet sayfasında, Sonraki** 'ye **tıklayın.**

6. Veritabanı **Nesnelerinizi Seçin sayfasında Tablolar'ı** genişletin ve **Adres** **(SalesLT) öğesini seçin.**

7. **Finish (Son)** düğmesine tıklayın.

    *AdventureWorksLTDataSet.xsd* dosyası **Çözüm Gezgini.** Bu dosya aşağıdaki öğeleri tanımlar:

   - adlı türüne göre bir veri `AdventureWorksLTDataSet` kümesi. Bu veri kümesi, **AdventureWorksLT veritabanındaki Address (SalesLT)** tablosu içeriğini temsil eder.

   - adlı bir TableAdapter. `AddressTableAdapter` Bu TableAdapter, içinde veri okumak ve yazmak için `AdventureWorksLTDataSet` kullanılabilir. Daha fazla bilgi için bkz. [TableAdapter'a genel bakış.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

     Bu adım adım kılavuzda bu nesnelerin ikisini de kullanacağız.

## <a name="create-controls-and-bind-controls-to-data"></a>Denetim oluşturma ve verilere denetim bağlama
 Bu kılavuzda denetim, kullanıcı çalışma kitabını açtığı anda seçtiğiniz <xref:Microsoft.Office.Tools.Excel.ListObject> tablodaki tüm verileri görüntüler. List nesnesi denetimi <xref:System.Windows.Forms.BindingSource> veritabanına bağlamak için kullanır.

 Verilere denetimler bağlama hakkında daha fazla bilgi için [bkz. Veri bağlama çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Liste nesnesini, veri kümesi ve tablo bağdaştırıcısını eklemek için

1. sınıfında, `ThisAddIn` veri kümesi tablosu görüntülemek için aşağıdaki denetimleri `Address` `AdventureWorksLTDataSet` bildirin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet1":::

2. yönteminde, veri kümesi başlatmak ve veri kümesine veri kümesinden bilgiler eklemek `ThisAddIn_Startup` için aşağıdaki `AdventureWorksLTDataSet` kodu ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet2":::

3. `ThisAddIn_Startup` yöntemine aşağıdaki kodu ekleyin. Bu, çalışma sayfasını genişleten bir konak öğesi üretir. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet3":::

4. Bir aralık oluşturun ve denetimi <xref:Microsoft.Office.Tools.Excel.ListObject> ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet4":::

5. kullanarak list nesnesini `AdventureWorksLTDataSet` nesnesine <xref:System.Windows.Forms.BindingSource> bağlayın. List nesnesine bağlamak istediğiniz sütunların adlarını iletir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet5":::

## <a name="test-the-add-in"></a>Eklentiyi Test Etmek
 Veri kümelerini <xref:Microsoft.Office.Tools.Excel.ListObject> Excel, denetim veri kümesi `Address` tablosundan `AdventureWorksLTDataSet` verileri görüntüler.

### <a name="to-test-the-vsto-add-in"></a>Eklentiyi VSTO için

- **F5 tuşuna basın.**

     Çalışma <xref:Microsoft.Office.Tools.Excel.ListObject> sayfasında adlı bir denetim `addressListObject` oluşturulur. Aynı zamanda, ve adlı bir veri `adventureWorksLTDataSet` kümesi <xref:System.Windows.Forms.BindingSource> nesnesi projeye `addressBindingSource` eklenir. <xref:Microsoft.Office.Tools.Excel.ListObject>, veri kümesi <xref:System.Windows.Forms.BindingSource> nesnesine bağlı olan nesnesine bağlı olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Office verileri](../vsto/data-in-office-solutions.md)
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Nasıl kullanılır: Çalışma sayfalarını veritabanındaki verilerle doldurmak](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl kullanılır: Belgeleri bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl kullanılır: Belgeleri hizmet verileriyle doldurmak](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl kullanılır: Çalışma sayfasındaki veritabanı kayıtları arasında kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Adım adım kılavuz: Belge düzeyi projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Adım adım kılavuz: Belge düzeyi projesinde karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Yerel veritabanı dosyalarını farklı çözümlerde Office genel bakış](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Yerel veritabanı dosyalarını farklı çözümlerde Office genel bakış](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)
