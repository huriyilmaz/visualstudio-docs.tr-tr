---
title: 'İzlenecek yol: VSTO eklenti projesinde basit veri bağlama'
description: Bir Microsoft Word belgesine nasıl denetim ekleyebileceğiniz ve çalışma zamanında denetimleri verilere nasıl bağlayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e1891173f10acfff74e0f7ef7ab17e29b258b80e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826843"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>İzlenecek yol: VSTO eklenti projesinde basit veri bağlama

VSTO eklenti projelerinde verileri konak denetimlerine ve Windows Forms denetimlerine bağlayabilirsiniz. Bu izlenecek yol, Microsoft Office bir Word belgesine nasıl denetim ekleneceğini ve çalışma zamanında denetimleri verilere nasıl bağlayacağınızı gösterir.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma zamanında <xref:Microsoft.Office.Tools.Word.ContentControl> belgeye ekleme.

- Denetimi bir <xref:System.Windows.Forms.BindingSource> veri kümesinin örneğine bağlayan bir oluşturma.

- Kullanıcının kayıtlarda gezinmelerini ve denetimde görüntülemesini sağlama.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Örnek veritabanının eklendiği SQL Server 2005 veya SQL Server 2005 Express 'in çalışan bir örneğine erişim `AdventureWorksLT` . `AdventureWorksLT`Veritabanını [SQL Server örnekleri GitHub deposundan](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)indirebilirsiniz. Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak bir veritabanı eklemek için bkz. [nasıl yapılır: veritabanı iliştirme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırını kullanarak bir veritabanı eklemek için, bkz. [nasıl yapılır: SQL Server Express veritabanı dosyası iliştirme](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Yeni proje oluşturma

İlk adım, bir Word VSTO eklenti projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. Visual Basic veya C# kullanarak **bir veritabanından belge doldurma** adlı BIR Word VSTO eklentisi projesi oluşturun.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio, *ThisAddIn. vb* veya *ThisAddIn. cs* dosyasını açar ve bir veritabanı projesinden **Çözüm Gezgini** **belge doldurmayı** ekler.

2. Projeniz [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ' i hedefliyorsa, *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* derlemesine bir başvuru ekleyin. Bu izlenecek yolda daha sonra belgeye Windows Forms denetimleri eklemek için bu başvuru gerekir.

## <a name="create-a-data-source"></a>Veri kaynağı oluşturma

Projenize türü belirtilmiş bir veri kümesi eklemek için **veri kaynakları** penceresini kullanın.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Projeye türü belirtilmiş bir veri kümesi eklemek için

1. **Veri kaynakları** penceresi görünür değilse, menü çubuğunda,   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçerek bunu görüntüleyin.

2. **Veri kaynağı Yapılandırma Sihirbazı 'nı** başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veritabanı**' na ve ardından **İleri**' ye tıklayın.

4. Veritabanına var olan bir bağlantınız varsa `AdventureWorksLT` , bu bağlantıyı seçin ve **İleri**' ye tıklayın.

    Aksi takdirde, **Yeni bağlantı**' ya tıklayın ve yeni bağlantıyı oluşturmak Için **bağlantı ekle** iletişim kutusunu kullanın. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

5. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

6. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** ' ı genişletin ve müşteri ' yi **(SalesLT)** seçin.

7. **Finish (Son)** düğmesine tıklayın.

    *AdventureWorksLTDataSet. xsd* dosyası **Çözüm Gezgini** eklenir. Bu dosya aşağıdaki öğeleri tanımlar:

   - Adında bir türü belirtilmiş veri kümesi `AdventureWorksLTDataSet` . Bu veri kümesi AdventureWorksLT veritabanındaki **Customer (SalesLT)** tablosunun içeriğini temsil eder.

   - Adında bir TableAdapter `CustomerTableAdapter` . Bu TableAdapter, içindeki verileri okumak ve yazmak için kullanılabilir `AdventureWorksLTDataSet` . Daha fazla bilgi için bkz. [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Bu iki nesneyi daha sonra Bu izlenecek yolda kullanacaksınız.

## <a name="create-controls-and-binding-controls-to-data"></a>Verilere denetimler oluşturma ve denetimleri bağlama

Bu izlenecek yolda veritabanı kayıtlarını görüntüleme arabirimi temel ve belge içinde oluşturulur. <xref:Microsoft.Office.Tools.Word.ContentControl>Tek seferde tek bir veritabanı kaydını görüntüler ve iki <xref:Microsoft.Office.Tools.Word.Controls.Button> Denetim kayıtlarda ileri ve geri kaydıramanıza imkan tanır. İçerik denetimi, <xref:System.Windows.Forms.BindingSource> veritabanına bağlanmak için bir kullanır.

Verilere yönelik bağlama denetimleri hakkında daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-create-the-interface-in-the-document"></a>Belgede arabirim oluşturmak için

1. `ThisAddIn`Sınıfında, veritabanı tablosunu göstermek ve kaydırmak için aşağıdaki denetimleri bildirin `Customer` `AdventureWorksLTDataSet` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet1":::

2. `ThisAddIn_Startup`Yönteminde, veri kümesini başlatmak için aşağıdaki kodu ekleyin, veri kümesini veritabanından alınan bilgilerle doldurabilirsiniz `AdventureWorksLTDataSet` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet2":::

3. `ThisAddIn_Startup` yöntemine aşağıdaki kodu ekleyin. Bu, belgeyi genişleten bir konak öğesi oluşturur. Daha fazla bilgi için bkz. [çalışma ZAMANıNDA VSTO Eklentilerindeki Word belgelerini ve Excel çalışma kitaplarını genişletme](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet3":::

4. Belgenin başlangıcında birkaç Aralık tanımlayın. Bu aralıklar, metin eklemek ve denetimlerin yerleştirileceği yeri belirler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet4":::

5. Arabirim denetimlerini daha önce tanımlı aralıklara ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet5":::

6. Kullanarak içerik denetimini bağlayın `AdventureWorksLTDataSet` <xref:System.Windows.Forms.BindingSource> . C# geliştiricileri için, denetimler için iki olay işleyicisi ekleyin <xref:Microsoft.Office.Tools.Word.Controls.Button> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet6":::

7. Veritabanı kayıtlarında gezinmek için aşağıdaki kodu ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet7":::

## <a name="test-the-add-in"></a>Eklentiyi test etme

Word 'Ü açtığınızda içerik denetimi veri kümesinden verileri görüntüler `AdventureWorksLTDataSet` . **Sonraki** ve **önceki** düğmelere tıklayarak veritabanı kayıtlarında ilerleyin.

### <a name="to-test-the-vsto-add-in"></a>VSTO eklentisini test etmek için

1. **F5** tuşuna basın.

     Adlı bir içerik denetimi `customerContentControl` oluşturulur ve verilerle doldurulur. Aynı zamanda, adlı ve adlı bir veri kümesi nesnesi `adventureWorksLTDataSet` <xref:System.Windows.Forms.BindingSource> `customerBindingSource` projeye eklenir. , <xref:Microsoft.Office.Tools.Word.ContentControl> ' A bağlanır ve <xref:System.Windows.Forms.BindingSource> veri kümesi nesnesine bağlanır.

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
