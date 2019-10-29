---
title: 'İzlenecek yol: VSTO eklenti projesinde basit veri bağlama'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bcfb150cc0b97b72fd0f6eac02f59ae1db3e9ca6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985399"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>İzlenecek yol: VSTO eklenti projesinde basit veri bağlama

VSTO eklenti projelerinde verileri konak denetimlerine ve Windows Forms denetimlerine bağlayabilirsiniz. Bu izlenecek yol, Microsoft Office bir Word belgesine nasıl denetim ekleneceğini ve çalışma zamanında denetimleri verilere nasıl bağlayacağınızı gösterir.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma zamanında bir belgeye <xref:Microsoft.Office.Tools.Word.ContentControl> ekleme.

- Denetimi bir veri kümesinin örneğine bağlayan <xref:System.Windows.Forms.BindingSource> oluşturma.

- Kullanıcının kayıtlarda gezinmelerini ve denetimde görüntülemesini sağlama.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- `AdventureWorksLT` örnek veritabanının eklendiği SQL Server 2005 veya SQL Server 2005 Express 'in çalışan bir örneğine erişim. `AdventureWorksLT` veritabanını [SQL Server örnekleri GitHub deposundan](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)indirebilirsiniz. Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak bir veritabanı eklemek için bkz. [nasıl yapılır: veritabanı iliştirme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırını kullanarak bir veritabanı eklemek için, bkz. [nasıl yapılır: SQL Server Express veritabanı dosyası iliştirme](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

İlk adım, bir Word VSTO eklenti projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Visual Basic veya C#kullanarak **bir veritabanından belge doldurma**adlı bir Word VSTO eklentisi projesi oluşturun.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio, *ThisAddIn. vb* veya *ThisAddIn.cs* dosyasını açar ve **belgeyi bir veritabanı projesinden doldurma** **Çözüm Gezgini**ekler.

2. Projeniz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]hedefliyorsa, *Microsoft. Office. Tools. Word. v 4.0. Utilities. dll* derlemesine bir başvuru ekleyin. Bu izlenecek yolda daha sonra belgeye Windows Forms denetimleri eklemek için bu başvuru gerekir.

## <a name="create-a-data-source"></a>Veri kaynağı oluşturma

Projenize türü belirtilmiş bir veri kümesi eklemek için **veri kaynakları** penceresini kullanın.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Projeye türü belirtilmiş bir veri kümesi eklemek için

1. **Veri kaynakları** penceresi görünür değilse, menü çubuğunda, **diğer Windows** > **veri kaynaklarını** **görüntüle** > ' yi seçerek görüntüleyin.

2. **Veri kaynağı Yapılandırma Sihirbazı 'nı**başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veritabanı**' na ve ardından **İleri**' ye tıklayın.

4. `AdventureWorksLT` veritabanıyla bağlantı varsa, bu bağlantıyı seçin ve **İleri**' ye tıklayın.

    Aksi takdirde, **Yeni bağlantı**' ya tıklayın ve yeni bağlantıyı oluşturmak Için **bağlantı ekle** iletişim kutusunu kullanın. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

5. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

6. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** ' ı genişletin ve müşteri ' yi **(SalesLT)** seçin.

7. **Son**'a tıklayın.

    *AdventureWorksLTDataSet. xsd* dosyası **Çözüm Gezgini**eklenir. Bu dosya aşağıdaki öğeleri tanımlar:

   - `AdventureWorksLTDataSet`adlı türü belirtilmiş bir veri kümesi. Bu veri kümesi AdventureWorksLT veritabanındaki **Customer (SalesLT)** tablosunun içeriğini temsil eder.

   - `CustomerTableAdapter`adlı bir TableAdapter. Bu TableAdapter, `AdventureWorksLTDataSet`veri okumak ve yazmak için kullanılabilir. Daha fazla bilgi için bkz. [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Bu iki nesneyi daha sonra Bu izlenecek yolda kullanacaksınız.

## <a name="create-controls-and-binding-controls-to-data"></a>Verilere denetimler oluşturma ve denetimleri bağlama

Bu izlenecek yolda veritabanı kayıtlarını görüntüleme arabirimi temel ve belge içinde oluşturulur. Bir <xref:Microsoft.Office.Tools.Word.ContentControl> her seferinde tek bir veritabanı kaydını görüntüler ve iki <xref:Microsoft.Office.Tools.Word.Controls.Button> denetimi kayıtlarda ileri ve geri kaydıramanıza imkan tanır. İçerik denetimi, veritabanına bağlanmak için bir <xref:System.Windows.Forms.BindingSource> kullanır.

Verilere yönelik bağlama denetimleri hakkında daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Belgede arabirim oluşturmak için

1. `ThisAddIn` sınıfında, `AdventureWorksLTDataSet` veritabanının `Customer` tablosunu göstermek ve kaydırmak için aşağıdaki denetimleri bildirin.

     [!code-vb[Trin_WordAddInDatabase#1](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDatabase#1](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#1)]

2. `ThisAddIn_Startup` yönteminde, veri kümesini başlatmak için aşağıdaki kodu ekleyin, veri kümesini `AdventureWorksLTDataSet` veritabanındaki bilgilerle doldurabilirsiniz.

     [!code-vb[Trin_WordAddInDatabase#2](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDatabase#2](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#2)]

3. `ThisAddIn_Startup` yöntemine aşağıdaki kodu ekleyin. Bu, belgeyi genişleten bir konak öğesi oluşturur. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-vb[Trin_WordAddInDatabase#3](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDatabase#3](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#3)]

4. Belgenin başlangıcında birkaç Aralık tanımlayın. Bu aralıklar, metin eklemek ve denetimlerin yerleştirileceği yeri belirler.

     [!code-vb[Trin_WordAddInDatabase#4](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDatabase#4](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#4)]

5. Arabirim denetimlerini daha önce tanımlı aralıklara ekleyin.

     [!code-vb[Trin_WordAddInDatabase#5](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDatabase#5](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#5)]

6. İçerik denetimini <xref:System.Windows.Forms.BindingSource>kullanarak `AdventureWorksLTDataSet` bağlayın. Geliştiriciler C# için<xref:Microsoft.Office.Tools.Word.Controls.Button>denetimleri için iki olay işleyicisi ekleyin.

     [!code-vb[Trin_WordAddInDatabase#6](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#6)]
     [!code-csharp[Trin_WordAddInDatabase#6](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#6)]

7. Veritabanı kayıtlarında gezinmek için aşağıdaki kodu ekleyin.

     [!code-vb[Trin_WordAddInDatabase#7](../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDatabase#7](../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs#7)]

## <a name="test-the-add-in"></a>Eklentiyi test etme

Word 'Ü açtığınızda, içerik denetimi `AdventureWorksLTDataSet` veri kümesinden verileri görüntüler. **Sonraki** ve **önceki** düğmelere tıklayarak veritabanı kayıtlarında ilerleyin.

### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisini test etmek için

1. **F5**tuşuna basın.

     `customerContentControl` adlı bir içerik denetimi oluşturulur ve verilerle doldurulur. Aynı zamanda, `adventureWorksLTDataSet` adlı bir veri kümesi nesnesi ve `customerBindingSource` adlı bir <xref:System.Windows.Forms.BindingSource> projeye eklenir. <xref:Microsoft.Office.Tools.Word.ContentControl> <xref:System.Windows.Forms.BindingSource>bağlanır, bu da DataSet nesnesine bağlanır.

2. Veritabanı kayıtlarında gezinmek için **İleri** ve **önceki** düğmelere tıklayın.

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
- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office çözümlerinde yerel veritabanı dosyalarını kullanma genel bakış](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)
