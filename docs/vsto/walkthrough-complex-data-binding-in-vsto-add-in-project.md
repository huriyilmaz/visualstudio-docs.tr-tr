---
title: 'İzlenecek yol: VSTO eklenti projesinde karmaşık veri bağlama'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99caf87000ea9df9260e8926eee4c7136bc9b848
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985488"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>İzlenecek yol: VSTO eklenti projesinde karmaşık veri bağlama
  VSTO eklenti projelerinde verileri konak denetimlerine ve Windows Forms denetimlerine bağlayabilirsiniz. Bu izlenecek yol, Microsoft Office Excel çalışma sayfasına nasıl denetim ekleneceğini ve çalışma zamanında denetimleri verilere nasıl bağlayacağınızı gösterir.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- <xref:Microsoft.Office.Tools.Excel.ListObject>Çalışma zamanında çalışma sayfasına denetim ekleme.

- Denetimi bir <xref:System.Windows.Forms.BindingSource> veri kümesinin örneğine bağlayan bir oluşturma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Örnek veritabanının eklendiği SQL Server 2005 veya SQL Server 2005 Express 'in çalışan bir örneğine erişim `AdventureWorksLT` . `AdventureWorksLT`Veritabanını [SQL Server örnekleri GitHub deposundan](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)indirebilirsiniz. Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak bir veritabanı eklemek için bkz. [nasıl yapılır: veritabanı iliştirme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırını kullanarak bir veritabanı eklemek için, bkz. [nasıl yapılır: SQL Server Express veritabanı dosyası iliştirme](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma
 İlk adım bir Excel VSTO eklenti projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Visual Basic veya C# kullanarak **bir veritabanından çalışma sayfası doldurma**adlı BIR Excel VSTO eklentisi projesi oluşturun.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio, `ThisAddIn.vb` veya `ThisAddIn.cs` dosyasını açar ve **çalışma sayfalarını bir veritabanı** projesinden **Çözüm Gezgini**doldurma ekler.

## <a name="create-a-data-source"></a>Veri kaynağı oluşturma
 Projenize türü belirtilmiş bir veri kümesi eklemek için **veri kaynakları** penceresini kullanın.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Projeye türü belirtilmiş bir veri kümesi eklemek için

1. **Veri kaynakları** penceresi görünür değilse, menü çubuğunda, **View**  >  **diğer Windows**  >  **veri kaynaklarını**görüntüle ' yi seçerek bunu görüntüleyin.

2. **Veri kaynağı Yapılandırma Sihirbazı 'nı**başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veritabanı**' na ve ardından **İleri**' ye tıklayın.

4. Veritabanına var olan bir bağlantınız varsa `AdventureWorksLT` , bu bağlantıyı seçin ve **İleri**' ye tıklayın.

    Aksi takdirde, **Yeni bağlantı**' ya tıklayın ve yeni bağlantıyı oluşturmak Için **bağlantı ekle** iletişim kutusunu kullanın. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

5. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

6. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** ' ı genişletin ve adres ' i **(SalesLT)** seçin.

7. **Son**'a tıklayın.

    *AdventureWorksLTDataSet. xsd* dosyası **Çözüm Gezgini**eklenir. Bu dosya aşağıdaki öğeleri tanımlar:

   - Adında bir türü belirtilmiş veri kümesi `AdventureWorksLTDataSet` . Bu veri kümesi AdventureWorksLT veritabanındaki **Address (SalesLT)** tablosunun içeriğini temsil eder.

   - Adında bir TableAdapter `AddressTableAdapter` . Bu TableAdapter, içindeki verileri okumak ve yazmak için kullanılabilir `AdventureWorksLTDataSet` . Daha fazla bilgi için bkz. [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Bu iki nesneyi daha sonra Bu izlenecek yolda kullanacaksınız.

## <a name="create-controls-and-bind-controls-to-data"></a>Denetim oluşturma ve verilere denetim bağlama
 Bu izlenecek yol için <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim, Kullanıcı çalışma kitabını açtığında seçtiğiniz tablodaki tüm verileri görüntüler. Liste nesnesi, <xref:System.Windows.Forms.BindingSource> denetimi veritabanına bağlamak için bir kullanır.

 Verilere yönelik bağlama denetimleri hakkında daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Liste nesnesini, veri kümesini ve tablo bağdaştırıcısını eklemek için

1. `ThisAddIn`Sınıfında, `Address` veri kümesinin tablosunu göstermek için aşağıdaki denetimleri bildirin `AdventureWorksLTDataSet` .

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. `ThisAddIn_Startup`Yönteminde, veri kümesini başlatmak ve veri kümesini veri kümesindeki bilgilerle doldurmanız için aşağıdaki kodu ekleyin `AdventureWorksLTDataSet` .

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. `ThisAddIn_Startup` yöntemine aşağıdaki kodu ekleyin. Bu, çalışma sayfasını genişleten bir konak öğesi oluşturur. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. Bir Aralık oluşturun ve denetimi ekleyin <xref:Microsoft.Office.Tools.Excel.ListObject> .

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. ' İ kullanarak liste nesnesini bağlayın `AdventureWorksLTDataSet` <xref:System.Windows.Forms.BindingSource> . Liste nesnesine bağlamak istediğiniz sütunların adlarını geçirin.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Eklentiyi test etme
 Excel 'i açtığınızda <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim, veri `Address` kümesinin tablosundaki verileri görüntüler `AdventureWorksLTDataSet` .

### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisini test etmek için

- **F5**tuşuna basın.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Çalışma sayfasında adlı bir denetim `addressListObject` oluşturulur. Aynı zamanda, adlı ve adlı bir veri kümesi nesnesi `adventureWorksLTDataSet` <xref:System.Windows.Forms.BindingSource> `addressBindingSource` projeye eklenir. , <xref:Microsoft.Office.Tools.Excel.ListObject> ' A bağlanır ve <xref:System.Windows.Forms.BindingSource> veri kümesi nesnesine bağlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: çalışma sayfasındaki veritabanı kayıtlarını kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [İzlenecek yol: belge düzeyi projede basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [İzlenecek yol: belge düzeyi projede karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Office çözümlerinde yerel veritabanı dosyalarını kullanma genel bakış](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Office çözümlerinde yerel veritabanı dosyalarını kullanma genel bakış](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)
