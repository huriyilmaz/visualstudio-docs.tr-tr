---
title: Formlar arasında veri geçirme
description: Bu Windows Forms denetimleri denetler, verileri bir formdan diğerine geçirmek için adım adım yönergeler alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b22c555b961809d84778df5996455f186efc01f1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216221"
---
# <a name="pass-data-between-forms"></a>Formlar arasında veri geçirme

Bu izlenecek yol, verileri bir formdan diğerine geçirmek için adım adım yönergeler sağlar. Northwind 'deki Customers ve Orders tablolarını kullanarak, bir form kullanıcıların bir müşteriyi seçmesini sağlar ve ikinci bir form seçili müşterinin siparişlerini görüntüler. Bu izlenecek yol, ikinci formda ilk formdan veri alan bir yöntemin nasıl oluşturulacağını gösterir.

> [!NOTE]
> Bu izlenecek yol, formlar arasında veri geçirmenin yalnızca bir yolunu gösterir. Verileri almak için ikinci bir Oluşturucu oluşturma veya ilk formdan verilerle ayarlanalabilen ortak bir özellik oluşturma dahil olmak üzere bir forma veri geçirmek için başka seçenekler vardır.

Bu izlenecek yolda gösterilen görevler şunlardır:

- Yeni bir **Windows Forms uygulama** projesi oluşturuluyor.

- [Veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)ile bir veri kümesi oluşturma ve yapılandırma.

- **Veri kaynakları** penceresinden öğeleri sürüklerken formda oluşturulacak denetimi seçme. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- **Veri kaynakları** penceresinden bir forma öğe sürükleyerek veri bağlantılı denetim oluşturma.

- Verileri göstermek için kılavuza sahip ikinci bir form oluşturma.

- Belirli bir müşteri için sipariş getirmek üzere TableAdapter sorgusu oluşturma.

- Formlar arasında veri geçirme.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi** aracılığıyla yükleyin. Visual Studio Yükleyicisi, SQL Server Express LocalDB, **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yüklenebilir.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-the-windows-forms-app-project"></a>Windows Forms uygulama projesi oluşturma

1. Visual Studio 'da, **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.

2. Sol bölmedeki **Visual C#** veya **Visual Basic** genişletip **Windows Masaüstü**' nü seçin.

3. Orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **PassingDataBetweenForms** olarak adlandırın ve ardından **Tamam**' ı seçin.

     **PassingDataBetweenForms** projesi oluşturulur ve **Çözüm Gezgini** eklenir.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

2. Veri **kaynakları** penceresinde, **veri kaynağı yapılandırma** Sihirbazı ' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

4. **Bir veritabanı modeli seçin** sayfasında, **veri kümesinin** belirtildiğinden emin olun ve ardından **İleri**' ye tıklayın.

5. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

6. Veritabanınız parola gerektiriyorsa ve hassas verileri dahil etme seçeneği etkinse, seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.

7. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

8. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

9. **Müşteriler** ve **siparişler** tablolarını seçip **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve **müşteriler** ve **siparişler** tabloları **veri kaynakları** penceresinde görünür.

## <a name="create-the-first-form-form1"></a>İlk formu oluşturma (Form1)

<xref:System.Windows.Forms.DataGridView> **Müşteriler** düğümünü **veri kaynakları** penceresinden form üzerine sürükleyerek veriye dayalı bir kılavuz (bir denetim) oluşturabilirsiniz.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Formda veriye bağlı bir kılavuz oluşturmak için

- Ana **müşteriler** düğümünü **veri kaynakları** penceresinden **Form1** üzerine sürükleyin.

     <xref:System.Windows.Forms.DataGridView>Kayıt gezinmek için bir ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) **Form1** üzerinde görünür. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

## <a name="create-the-second-form"></a>İkinci formu oluşturma

Verileri iletmek için ikinci bir form oluşturun.

1. **Proje** menüsünden **Windows formu Ekle**' yi seçin.

2. Varsayılan **Form2** adını bırakın ve **Ekle**' ye tıklayın.

3. Ana **siparişler** düğümünü **veri kaynakları** penceresinden **Form2** üzerine sürükleyin.

     <xref:System.Windows.Forms.DataGridView>Kayıtlar üzerinde gezinmek için bir ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) **Form2** üzerinde görünür. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

4. Bileşen tepsisinden **OrdersBindingNavigator** öğesini silin.

     **OrdersBindingNavigator** **Form2** öğesinden kayboluyor.

## <a name="add-a-tableadapter-query"></a>TableAdapter sorgusu ekleme

Form2 'e bir TableAdapter sorgusu ekleyerek Form1 üzerinde seçilen müşteriye ait siparişleri yükleyin.

1. **Çözüm Gezgini** **NorthwindDataSet. xsd** dosyasını çift tıklayın.

2. **OrdersTableAdapter** öğesine sağ tıklayın ve **Sorgu Ekle**' yi seçin.

3. **SQL deyimlerini kullan** varsayılan seçeneğini bırakın ve ardından **İleri**' ye tıklayın.

4. **Satırları döndüren Seç** varsayılan seçeneğini bırakın ve ardından **İleri**' ye tıklayın.

5. Temelinde döndürmek için sorguya bir WHERE yan tümcesi ekleyin `Orders` `CustomerID` . Sorgu aşağıdakine benzemelidir:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Veritabanınız için doğru parametre söz dizimini doğrulayın. Örneğin, Microsoft Access 'te WHERE yan tümcesi şöyle görünür: `WHERE CustomerID = ?` .

6. **İleri**’ye tıklayın.

7. **DataTableMethod adı doldur** için yazın `FillByCustomerID` .

8. **Bir DataTable döndürün** seçeneğinin işaretini kaldırın ve ardından **İleri**' ye tıklayın.

9. **Finish (Son)** düğmesine tıklayın.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Verileri iletmek için Form2 üzerinde bir yöntem oluşturma

1. **Form2**' e sağ tıklayın ve **Kod Düzenleyicisi**'nde **Form2** ' yi açmak için **kodu görüntüle** ' yi seçin.

2. Aşağıdaki kodu yönteminden sonra **Form2** öğesine ekleyin `Form2_Load` :

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb" id="Snippet1":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs" id="Snippet1":::

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Veri geçirmek ve Form2 göstermek için Form1 üzerinde bir yöntem oluşturun

1. **Form1**' te, müşteri verileri kılavuzuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellikler** penceresinde **Olaylar**' a tıklayın.

3. **CellDoubleClick** olayına çift tıklayın.

     Kod düzenleyicisi görünür.

4. Yöntem tanımını aşağıdaki örnekle eşleşecek şekilde güncelleştirin:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet2":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet2":::

## <a name="run-the-app"></a>Uygulamayı çalıştırma

- Uygulamayı çalıştırmak için **F5**'e basın.

- Bu müşterinin siparişleriyle **Form2** açmak için **Form1** içindeki bir müşteri kaydına çift tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, formlar arasında veri geçirmeden sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- Veritabanı nesneleri eklemek veya çıkarmak için veri kümesini düzenleme. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Verileri veritabanına geri kaydetme işlevselliği ekleme. Daha fazla bilgi için bkz. [verileri veritabanına geri kaydetme](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
