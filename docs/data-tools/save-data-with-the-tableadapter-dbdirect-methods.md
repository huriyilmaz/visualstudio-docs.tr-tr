---
title: TableAdapter DBDirect metotlarıyla veri kaydetme
description: Bu kılavuzda, tableAdapter'SQL DBDirect yöntemlerini kullanarak doğrudan veritabanına yönelik deyimleri çalıştırın.
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
ms.openlocfilehash: fe4ff23c94a47ff6ef323e0bf8b4cd200f139149cf50c39d7e249f88b749c29d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346862"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>TableAdapter DBDirect metotlarıyla veri kaydetme

Bu kılavuz, TableAdapter'SQL DBDirect yöntemlerini kullanarak doğrudan bir veritabanına karşı farklı deyimleri çalıştırmaya yönelik ayrıntılı yönergeler sağlar. TableAdapter'ın DBDirect yöntemleri, veritabanı güncelleştirmeleriniz üzerinde ince bir denetim düzeyi sağlar. Bunları, belirli SQL deyimlerini ve saklı yordamları çalıştırmak için, tek tek , ve yöntemlerini uygulamanıza gereken şekilde çağırarak (UPDATE, INSERT ve DELETE deyimlerini tek bir çağrıda gerçekleştiren aşırı yüklenmiş yöntemin `Insert` `Update` `Delete` `Update` aksine) kullanabilirsiniz.

Bu kılavuzda şunları yapmayı öğrenirsiniz:

- Yeni bir form **Windows Forms Uygulaması oluşturun.**

- Veri Kaynağı Yapılandırma Sihirbazı ile bir veri [kümesi oluşturun ve yapılandırabilirsiniz.](../data-tools/media/data-source-configuration-wizard.png)

- Veri Kaynakları penceresinden öğeleri sürüklerken formda **oluşturulacak denetimi** seçin. Daha fazla bilgi için [bkz. Veri Kaynakları penceresinden sürüklenrken oluşturulacak denetimi ayarlama.](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

- Veri Kaynakları penceresindeki öğeleri forma **sürükleyerek veriye bağlı** bir form oluşturun.

- Veritabanına doğrudan erişmek ve ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için yöntemler ekleyin.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. YerelDB'niz yoksa, SQL Server Express indirme sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Bu **Visual Studio Yükleyicisi,** yerel SQL Server Express veri depolama ve işleme iş  yükünün bir parçası olarak veya tek bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (SQL Server Nesne Gezgini, veri depolama ve işleme **iş yükünün bir parçası olarak** Visual Studio Yükleyicisi.) SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Bir sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Windows Forms uygulaması oluşturma

İlk adım, bir Windows **Forms Uygulaması oluşturmaktır.**

1. Bu Visual Studio, Dosya **menüsünde Yeni** **dosya'Project.**  >  

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve ardından Masaüstü'Windows **seçin.**

3. Orta bölmede Windows **Forms Uygulaması proje** türünü seçin.

4. Projeye **TableAdapterDbDirectMethodsWalkthrough adını ve** ardından Tamam'ı **seçin.**

     **TableAdapterDbDirectMethodsWalkthrough** projesi oluşturulur ve **Çözüm Gezgini.**

## <a name="create-a-data-source-from-your-database"></a>Veritabanınıza bir veri kaynağı oluşturma

Bu adım, Northwind **örnek veritabanındaki** tabloyu temel alan bir veri kaynağı oluşturmak için Veri Kaynağı `Region` Yapılandırma Sihirbazı'nı kullanır. Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Örnek veritabanlarını yükleme.](../data-tools/installing-database-systems-tools-and-samples.md)

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. Veri menüsünde **Veri** Kaynaklarını **Göster'i seçin.**

   Veri **Kaynakları** penceresi açılır.

2. Veri Kaynağı **Yapılandırma Sihirbazı'nı** başlatmak **için Veri Kaynakları penceresinde** Yeni Veri Kaynağı **Ekle'yi seçin.**

3. Veri Kaynağı **Türü Seçin ekranında Veritabanı'ı** **ve ardından** Sonraki'yi **seçin.**

4. Veri **Bağlantınızı Seçin** ekranında, aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         -veya-

    - Bağlantı **Ekle/Değiştir** iletişim **kutusunu başlatmak için Yeni Bağlantı'ya** tıklayın.

5. Veritabanınız parola gerektiriyorsa hassas verileri dahil etmek için seçeneğini belirleyin ve ardından Sonraki seçeneğini **belirleyin.**

6. Bağlantı **dizesini Uygulama Yapılandırması dosyasına kaydet ekranında, Sonraki'yi** **seçin.**

7. Veritabanı **Nesnelerinizi seçin ekranında** Tablolar **düğümünü** genişletin.

8. Tabloyu `Region` ve ardından Son'ı **seçin.**

     **NorthwindDataSet** projenize eklenir ve `Region` tablo Veri Kaynakları **penceresinde** görüntülenir.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Verileri görüntülemek için forma denetimler ekleme

Veri Kaynakları penceresindeki öğeleri form üzerine **sürükleyerek veriye bağlı** denetimleri oluşturun.

Veri kaynağı formunda veri Windows için ana **Bölge** düğümünü Veri Kaynakları **penceresinden** forma sürükleyin.

Formda <xref:System.Windows.Forms.DataGridView> kayıtlarda gezinmek için bir denetim ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) görüntülenir. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter` , ve bileşenleri bileşen <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> tepsisinde görüntülenir.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Tek tek TableAdapter DbDirect yöntemlerini çağıracak düğmeler eklemek için

1. Araç <xref:System.Windows.Forms.Button> kutusundan **Form1'e üç** denetim sürükleyin **(RegionDataGridView'un altına).** 

2. Her düğmede **aşağıdaki** **Ad ve** Metin özelliklerini ayarlayın.

    |Name|Metin|
    |----------|----------|
    |`InsertButton`|**Ekle**|
    |`UpdateButton`|**Güncelleştirme**|
    |`DeleteButton`|**Silme**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Veritabanına yeni kayıtlar eklemek için kod eklemek için

1. **EkleButton'u** seçerek tıklama olayı için bir olay işleyicisi oluşturun ve formlarınızı kod düzenleyicisinde açın.

2. Olay `InsertButton_Click` işleyicisini aşağıdaki kodla değiştirin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet1":::

### <a name="to-add-code-to-update-records-in-the-database"></a>Veritabanındaki kayıtları güncelleştirmek için kod eklemek için

1. UpdateButton'a **çift tıklar,** tıklama olayı için bir olay işleyicisi oluşturun ve formlarınızı kod düzenleyicisinde açın.

2. Olay `UpdateButton_Click` işleyicisini aşağıdaki kodla değiştirin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet2":::

### <a name="to-add-code-to-delete-records-from-the-database"></a>Veritabanından kayıtları silmek için kod eklemek için

1. Tıklama olayı için bir olay işleyicisi oluşturmak ve formlarınızı kod düzenleyicisinde açmak için **DeleteButton'u** seçin.

2. Olay `DeleteButton_Click` işleyicisini aşağıdaki kodla değiştirin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet3":::

## <a name="run-the-application"></a>Uygulamayı çalıştırma

- Uygulamayı **çalıştırmak için F5'i** seçin.

- Ekle **düğmesini** seçin ve yeni kaydın kılavuzda görüntülendiğinden emin olur.

- Güncelleştir **düğmesini** seçin ve kaydın kılavuzda güncelleştirilmiş olduğunu doğrulayın.

- Sil **düğmesini** seçin ve kaydın kılavuzdan kaldırılmış olduğunu doğrulayın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, veriye bağlı bir form oluşturdukta gerçekleştirmek istediğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- Forma arama işlevi ekleme.

- Veri Kaynakları penceresinden Sihirbazı ile Veri Kümesi **Yapılandır'ı seçerek** veri kümesine **ek tablolar** ekleme. İlgili düğümleri forma sürükleyerek ilgili verileri görüntülüyor denetimler ebilirsiniz. Daha fazla bilgi için [bkz. Veri Kümelerde İlişkiler.](relationships-in-datasets.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
