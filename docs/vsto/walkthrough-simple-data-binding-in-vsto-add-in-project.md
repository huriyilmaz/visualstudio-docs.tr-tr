---
title: 'Adım adım kılavuz: Eklenti projesinde VSTO basit veri bağlama'
description: Çalışma zamanında bir belgeye denetimler Microsoft Word ve bu denetimleri verilere bağlamayı öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 10ecb5b04198a0937b06876760862c7b9cf415c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155453"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>Adım adım kılavuz: Eklenti VSTO basit veri bağlama Project

Eklenti projelerinde verileri konak denetimlerine Windows Forms VSTO bağlanabilirsiniz. Bu kılavuzda, word word belgesine denetimler Microsoft Office ve çalışma zamanında verilere nasıl bağlanacağını gösterir.

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma zamanında <xref:Microsoft.Office.Tools.Word.ContentControl> belgeye bir ekleme.

- Denetimi <xref:System.Windows.Forms.BindingSource> bir veri kümesi örneğine bağlayan bir oluşturma.

- Kullanıcının kayıtlarda kaydırma ve denetimde görüntülemesini etkinleştirme.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] veya [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Örnek veritabanının bağlı olduğu SQL Server 2005 veya SQL Server 2005 Express çalıştıran `AdventureWorksLT` bir örneğine erişim. veritabanını SQL Server `AdventureWorksLT` [Samples GitHub indirebilirsiniz.](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) Veritabanı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - SQL Server Management Studio veya SQL Server Management Studio Express kullanarak veritabanı eklemek için [bkz. Nasıl kullanılır: Veritabanı ekleme (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Komut satırı kullanarak veritabanı eklemek için bkz. [Nasıl kullanılır:](/previous-versions/sql/)Veritabanı dosyasını SQL Server Express.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

İlk adım, Word VSTO Eklenti projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. VSTO veya C# kullanarak Bir Veritabanından Belgeleri Doldurmak adıyla bir Word Visual Basic Eklenti projesi oluşturun.

     Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     Visual Studio *ThisAddIn.vb* veya *ThisAddIn.cs* dosyasını açar ve  Veritabanı projesinden Belgeleri Doldurmak için **Çözüm Gezgini.**

2. Projeniz veya [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] hedefini [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] hedeflese, derleme derlemesi için *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* ekleyin. Bu başvuru, bu kılavuzun sonraki Windows Formlar denetimlerini program aracılığıyla eklemek için gereklidir.

## <a name="create-a-data-source"></a>Veri kaynağı oluşturma

Projenize **türü** türüne göre bir veri kümesi eklemek için Veri Kaynakları penceresini kullanın.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Projeye türü türüne göre bir veri kümesi eklemek için

1. Veri **Kaynakları penceresi görünmüyorsa,** menü çubuğunda Diğer Kaynakları Görüntüle'Windows   >    >  **görüntüleniyor.**

2. Veri **Kaynağı Yapılandırma Sihirbazı'nı başlatmak** için Yeni Veri Kaynağı **Ekle'yi seçin.**

3. Veritabanı **'ne** ve ardından Sonraki'ye **tıklayın.**

4. Veritabanıyla mevcut bir bağlantınız varsa `AdventureWorksLT` bu bağlantıyı seçin ve Ardından'ya **tıklayın.**

    Aksi takdirde, **Yeni Bağlantı'ya** tıklayın **ve yeni bağlantıyı** oluşturmak için Bağlantı Ekle iletişim kutusunu kullanın. Daha fazla bilgi için [bkz. Yeni bağlantı ekleme.](../data-tools/add-new-connections.md)

5. Bağlantı **Dizesini Uygulama Yapılandırma Dosyasına Kaydet sayfasında, Sonraki** 'ye **tıklayın.**

6. Veritabanı **Nesnelerinizi Seçin sayfasında Tablolar'ı** genişletin ve **Müşteri** **(SalesLT) öğesini seçin.**

7. **Finish (Son)** düğmesine tıklayın.

    *AdventureWorksLTDataSet.xsd* dosyası **Çözüm Gezgini.** Bu dosya aşağıdaki öğeleri tanımlar:

   - adlı türüne göre bir veri `AdventureWorksLTDataSet` kümesi. Bu veri kümesi, **AdventureWorksLT veritabanındaki Customer (SalesLT)** tablosu içeriğini temsil eder.

   - adlı bir TableAdapter. `CustomerTableAdapter` Bu TableAdapter, içinde veri okumak ve yazmak için `AdventureWorksLTDataSet` kullanılabilir. Daha fazla bilgi için bkz. [TableAdapter'a genel bakış.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

     Bu adım adım kılavuzda bu nesnelerin ikisini de kullanacağız.

## <a name="create-controls-and-binding-controls-to-data"></a>Denetimler oluşturma ve verilere denetimler bağlama

Bu kılavuzda veritabanı kayıtlarını görüntüleme arabirimi temeldir ve belgenin içinde oluşturulur. Bunlardan <xref:Microsoft.Office.Tools.Word.ContentControl> biri aynı anda tek bir veritabanı kaydı görüntüler ve iki <xref:Microsoft.Office.Tools.Word.Controls.Button> denetim, kayıtlarda ileri ve geri kaydırmanız için olanak sağlar. İçerik denetimi veritabanına <xref:System.Windows.Forms.BindingSource> bağlanmak için kullanır.

Verilere denetimler bağlama hakkında daha fazla bilgi için [bkz. Veri bağlama çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="to-create-the-interface-in-the-document"></a>Belgede arabirimi oluşturmak için

1. sınıfında, `ThisAddIn` görüntülemek ve veritabanının tablosunda kaydırmak için `Customer` aşağıdaki denetimleri `AdventureWorksLTDataSet` bildirin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet1":::

2. `ThisAddIn_Startup`yönteminde, veri kümesi başlatmak için aşağıdaki kodu ekleyin, veri kümelerini veritabanındaki bilgilerle `AdventureWorksLTDataSet` doldurun.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet2":::

3. `ThisAddIn_Startup` yöntemine aşağıdaki kodu ekleyin. Bu, belgeyi genişleten bir konak öğesi üretir. Daha fazla bilgi için bkz. Word belgelerini genişletme Excel çalışma VSTO çalışma [kitaplarını çalışma zamanında genişletme.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet3":::

4. Belgenin başında birkaç aralık tanımlayın. Bu aralıklar, metin ekli ve denetimlerin nereye ekli olduğunu gösterir.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet4":::

5. Arabirim denetimlerini önceden tanımlanmış aralıklara ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet5":::

6. kullanarak içerik `AdventureWorksLTDataSet` denetimine <xref:System.Windows.Forms.BindingSource> bağlayın. C# geliştiricileri için denetimler için iki olay <xref:Microsoft.Office.Tools.Word.Controls.Button> işleyicisi ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet6":::

7. Veritabanı kayıtlarında gezinmek için aşağıdaki kodu ekleyin.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet7":::

## <a name="test-the-add-in"></a>Eklentiyi Test Etmek

Word'i açabilirsiniz. İçerik denetimi, veri `AdventureWorksLTDataSet` kümesinden verileri görüntüler. Sonraki ve Önceki düğmelerine tıklayarak **veritabanı kayıtlarını** **kaydırın.**

### <a name="to-test-the-vsto-add-in"></a>Eklentiyi VSTO için

1. **F5 tuşuna basın.**

     adlı bir içerik `customerContentControl` denetimi oluşturulur ve verilerle doldurulur. Aynı zamanda, ve adlı bir veri `adventureWorksLTDataSet` kümesi <xref:System.Windows.Forms.BindingSource> nesnesi projeye `customerBindingSource` eklenir. <xref:Microsoft.Office.Tools.Word.ContentControl>, veri kümesi <xref:System.Windows.Forms.BindingSource> nesnesine bağlı olan nesnesine bağlı olur.

2. Veritabanı **kayıtlarında** kaydırma **yapmak için** Sonraki ve Önceki düğmelerine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Office verileri](../vsto/data-in-office-solutions.md)
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Nasıl kullanılır: Çalışma sayfalarını bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl kullanılır: Belgeleri bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl kullanılır: Belgeleri hizmet verileriyle doldurmak](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl kullanılır: Çalışma sayfasındaki veritabanı kayıtları arasında kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Adım adım kılavuz: Belge düzeyi projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Adım adım kılavuz: Belge düzeyi projesinde karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Çözümlerde yerel veritabanı dosyalarını Office genel bakış](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Çözümlerde yerel veritabanı dosyalarını Office genel bakış](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)
