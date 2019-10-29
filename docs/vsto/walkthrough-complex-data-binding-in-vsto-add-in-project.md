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
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985488"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>İzlenecek yol: VSTO eklenti projesinde karmaşık veri bağlama
  VSTO eklenti projelerinde verileri konak denetimlerine ve Windows Forms denetimlerine bağlayabilirsiniz. Bu izlenecek yol, Microsoft Office Excel çalışma sayfasına nasıl denetim ekleneceğini ve çalışma zamanında denetimleri verilere nasıl bağlayacağınızı gösterir.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma zamanında çalışma sayfasına <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi ekleme.

- Denetimi bir veri kümesinin örneğine bağlayan <xref:System.Windows.Forms.BindingSource> oluşturma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- `AdventureWorksLT` örnek veritabanının eklendiği SQL Server 2005 veya SQL Server 2005 Express 'in çalışan bir örneğine erişim. `AdventureWorksLT` veritabanını [SQL Server örnekleri GitHub deposundan](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)indirebilirsiniz. Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak bir veritabanı eklemek için bkz. [nasıl yapılır: veritabanı iliştirme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırını kullanarak bir veritabanı eklemek için, bkz. [nasıl yapılır: SQL Server Express veritabanı dosyası iliştirme](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma
 İlk adım bir Excel VSTO eklenti projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Visual Basic veya C#kullanarak **bir veritabanından çalışma sayfası doldurma**adlı bir Excel VSTO eklentisi projesi oluşturun.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio `ThisAddIn.vb` veya `ThisAddIn.cs` dosyasını açar ve **çalışma sayfalarını bir veritabanı** projesinden **Çözüm Gezgini**ekler.

## <a name="create-a-data-source"></a>Veri kaynağı oluşturma
 Projenize türü belirtilmiş bir veri kümesi eklemek için **veri kaynakları** penceresini kullanın.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Projeye türü belirtilmiş bir veri kümesi eklemek için

1. **Veri kaynakları** penceresi görünür değilse, menü çubuğunda, **diğer Windows** > **veri kaynaklarını** **görüntüle** > ' yi seçerek görüntüleyin.

2. **Veri kaynağı Yapılandırma Sihirbazı 'nı**başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veritabanı**' na ve ardından **İleri**' ye tıklayın.

4. `AdventureWorksLT` veritabanıyla bağlantı varsa, bu bağlantıyı seçin ve **İleri**' ye tıklayın.

    Aksi takdirde, **Yeni bağlantı**' ya tıklayın ve yeni bağlantıyı oluşturmak Için **bağlantı ekle** iletişim kutusunu kullanın. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

5. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

6. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** ' ı genişletin ve adres ' i **(SalesLT)** seçin.

7. **Son**'a tıklayın.

    *AdventureWorksLTDataSet. xsd* dosyası **Çözüm Gezgini**eklenir. Bu dosya aşağıdaki öğeleri tanımlar:

   - `AdventureWorksLTDataSet`adlı türü belirtilmiş bir veri kümesi. Bu veri kümesi AdventureWorksLT veritabanındaki **Address (SalesLT)** tablosunun içeriğini temsil eder.

   - `AddressTableAdapter`adlı bir TableAdapter. Bu TableAdapter, `AdventureWorksLTDataSet`veri okumak ve yazmak için kullanılabilir. Daha fazla bilgi için bkz. [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Bu iki nesneyi daha sonra Bu izlenecek yolda kullanacaksınız.

## <a name="create-controls-and-bind-controls-to-data"></a>Denetim oluşturma ve verilere denetim bağlama
 Bu izlenecek yol için, <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi kullanıcı çalışma kitabını açtığında seçtiğiniz tablodaki tüm verileri görüntüler. Liste nesnesi, denetimi veritabanına bağlamak için bir <xref:System.Windows.Forms.BindingSource> kullanır.

 Verilere yönelik bağlama denetimleri hakkında daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Liste nesnesini, veri kümesini ve tablo bağdaştırıcısını eklemek için

1. `ThisAddIn` sınıfında, `AdventureWorksLTDataSet` veri kümesinin `Address` tablosunu göstermek için aşağıdaki denetimleri bildirin.

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. `ThisAddIn_Startup` yönteminde, veri kümesini başlatmak ve veri kümesini `AdventureWorksLTDataSet` veri kümesindeki bilgilerle doldurmanız için aşağıdaki kodu ekleyin.

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. `ThisAddIn_Startup` yöntemine aşağıdaki kodu ekleyin. Bu, çalışma sayfasını genişleten bir konak öğesi oluşturur. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. Aralık oluşturun ve <xref:Microsoft.Office.Tools.Excel.ListObject> denetimini ekleyin.

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. Liste nesnesini <xref:System.Windows.Forms.BindingSource>kullanarak `AdventureWorksLTDataSet` bağlayın. Liste nesnesine bağlamak istediğiniz sütunların adlarını geçirin.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Eklentiyi test etme
 Excel 'i açtığınızda <xref:Microsoft.Office.Tools.Excel.ListObject> denetim, verileri `AdventureWorksLTDataSet` veri kümesinin `Address` tablosundan görüntüler.

### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisini test etmek için

- **F5**tuşuna basın.

     Çalışma sayfasında `addressListObject` adlı bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi oluşturulur. Aynı zamanda, `adventureWorksLTDataSet` adlı bir veri kümesi nesnesi ve `addressBindingSource` adlı bir <xref:System.Windows.Forms.BindingSource> projeye eklenir. <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:System.Windows.Forms.BindingSource>bağlanır, bu da DataSet nesnesine bağlanır.

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
