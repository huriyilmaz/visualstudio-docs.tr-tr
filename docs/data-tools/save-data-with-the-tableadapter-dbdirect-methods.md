---
title: TableAdapter DBDirect metotlarıyla veri kaydetme
description: bu kılavuzda, bir TableAdapter 'ın dbdirect yöntemlerini kullanarak SQL deyimlerini doğrudan bir veritabanına karşı çalıştırın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cf7ed024e98382ea134c27cd697cdae932d735d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113789"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>TableAdapter DBDirect metotlarıyla veri kaydetme

bu izlenecek yol, bir TableAdapter 'ın dbdirect yöntemlerini kullanarak SQL deyimlerini doğrudan bir veritabanına karşı çalıştırmaya yönelik ayrıntılı yönergeler sağlar. Bir TableAdapter 'ın DBDirect yöntemleri, veritabanı güncelleştirmeleriniz üzerinde ince bir denetim düzeyi sağlar. bu bunları, uygulamanız için gerekli olan bireysel, ve yöntemleri çağırarak belirli SQL deyimlerini ve saklı yordamları çalıştırmak için kullanabilirsiniz `Insert` `Update` `Delete` ( `Update` tümünü tek bir çağrıda UPDATE, ınsert ve DELETE deyimlerini gerçekleştiren aşırı yüklenmiş yönteme karşılık).

Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- yeni bir **Windows Forms uygulaması** oluşturun.

- [Veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)ile bir veri kümesi oluşturun ve yapılandırın.

- **Veri kaynakları** penceresinden öğeleri sürüklerken form üzerinde oluşturulacak denetimi seçin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- **Veri kaynakları** penceresinden forma öğe sürükleyerek veri bağlantılı bir form oluşturun.

- Veritabanına doğrudan erişmek ve ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için yöntemler ekleyin.

## <a name="prerequisites"></a>Önkoşullar

bu izlenecek yol, SQL Server Express localdb ve Northwind örnek veritabanını kullanır.

1. SQL Server Express localdb yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio Yükleyicisi** aracılığıyla yükleyin. **Visual Studio Yükleyicisi**, SQL Server Express localdb 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio, **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **yürüt** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Windows Forms uygulaması oluşturma

ilk adım **Windows Forms bir uygulama** oluşturmaktır.

1. Visual Studio, **dosya** menüsünde **yeni**  >  **Project**' yi seçin.

2. sol bölmedeki **Visual C#** ' ı veya **Visual Basic** genişletin ve sonra **Windows masaüstü**' nü seçin.

3. orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **TableAdapterDbDirectMethodsWalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     **TableAdapterDbDirectMethodsWalkthrough** projesi oluşturulup **Çözüm Gezgini** eklenir.

## <a name="create-a-data-source-from-your-database"></a>Veritabanınızdan bir veri kaynağı oluşturun

Bu adım, Northwind örnek veritabanındaki tabloya dayalı bir veri kaynağı oluşturmak için **veri kaynağı Yapılandırma Sihirbazı** ' nı kullanır `Region` . Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanlarını kurma](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri** menüsünde **veri kaynaklarını göster**' i seçin.

   **Veri kaynakları** penceresi açılır.

2. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** ekranında **veritabanı**' nı seçin ve ardından **İleri**' yi seçin.

4. **Veri bağlantınızı seçin** ekranında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         -veya-

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' yi seçin.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** ekranında, **İleri**' yi seçin.

7. **Veritabanı nesnelerinizi seçin** ekranında **Tablolar** düğümünü genişletin.

8. Tabloyu seçin `Region` ve ardından **son**' u seçin.

     **NorthwindDataSet** , projenize eklenir ve `Region` tablo **veri kaynakları** penceresinde görünür.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Verileri göstermek için forma denetimler ekleme

Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimler oluşturun.

Windows formunda veriye bağlı denetimler oluşturmak için, **veri kaynakları** penceresinden ana **bölge** düğümünü form üzerine sürükleyin.

<xref:System.Windows.Forms.DataGridView>Kayıtlar üzerinde gezinmek için bir denetim ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) formda görüntülenir. Bileşen tepsisinde bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter` , <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> görüntülenir.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Bireysel TableAdapter DbDirect yöntemlerini çağıran düğmeler eklemek için

1. <xref:System.Windows.Forms.Button> **Araç kutusundan** üç denetimi **Form1** ( **RegionDataGridView** altında) üzerine sürükleyin.

2. Her düğme için aşağıdaki **ad** ve **metin** özelliklerini ayarlayın.

    |Name|Metin|
    |----------|----------|
    |`InsertButton`|**Ekle**|
    |`UpdateButton`|**Güncelleştirme**|
    |`DeleteButton`|**Silme**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Veritabanına yeni kayıtlar eklemek üzere kod eklemek için

1. Tıklama olayı için bir olay işleyicisi oluşturmak ve kod düzenleyicisinde formunuzu açmak için **InsertButton** öğesini seçin.

2. `InsertButton_Click`Olay işleyicisini aşağıdaki kodla değiştirin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet1":::

### <a name="to-add-code-to-update-records-in-the-database"></a>Veritabanındaki kayıtları güncelleştirmek üzere kod eklemek için

1. Tıklama olayı için bir olay işleyicisi oluşturmak ve formunuzu Kod düzenleyicisinde açmak için **UpdateButton** öğesine çift tıklayın.

2. `UpdateButton_Click`Olay işleyicisini aşağıdaki kodla değiştirin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet2":::

### <a name="to-add-code-to-delete-records-from-the-database"></a>Veritabanından kayıtları silmek üzere kod eklemek için

1. Tıklama olayı için bir olay işleyicisi oluşturmak üzere **DeleteButton** ' ı seçin ve formunuzu Kod düzenleyicisinde açın.

2. `DeleteButton_Click`Olay işleyicisini aşağıdaki kodla değiştirin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet3":::

## <a name="run-the-application"></a>Uygulamayı çalıştırma

- Uygulamayı çalıştırmak için **F5** ' i seçin.

- **Ekle** düğmesini seçin ve yeni kaydın kılavuzda göründüğünü doğrulayın.

- **Güncelleştir** düğmesini seçin ve kaydın kılavuzda güncelleştirildiğinden emin olun.

- **Sil** düğmesini seçin ve kaydın kılavuzdan kaldırıldığını doğrulayın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, verilere bağlı bir form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- Forma arama işlevleri ekleniyor.

- **Veri kaynakları** penceresi Içinden veri **kümesini sihirbaz ile yapılandır** ' a seçerek veri kümesine ek tablolar ekleme. İlgili düğümleri form üzerine sürükleyerek ilgili verileri görüntüleyen denetimler ekleyebilirsiniz. Daha fazla bilgi için bkz. [veri kümelerinde ilişkiler](relationships-in-datasets.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
