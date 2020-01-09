---
title: 'İzlenecek yol: Bir işlemde veri kaydetme'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c0efdda51a52b18697828e1772eb4a71435753e8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586243"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>İzlenecek yol: Bir işlemde veri kaydetme

Bu izlenecek yol, <xref:System.Transactions> ad alanını kullanarak bir işlemde nasıl veri kaydedileceğini gösterir. Bu kılavuzda bir Windows Forms uygulaması oluşturacaksınız. Northwind örnek veritabanındaki iki tablo için bir veri kümesi oluşturmak üzere veri kaynağı Yapılandırma Sihirbazı 'nı kullanacaksınız. Bir Windows formuna veri bağlantılı denetimler ekleyeceksiniz ve bir TransactionScope içinde veritabanını güncelleştirmek için BindingNavigator 'ın Kaydet düğmesine ait kodu değiştirirsiniz.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi**aracılığıyla yükleyin. Visual Studio Yükleyicisi, SQL Server Express LocalDB, **.net masaüstü geliştirme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yüklenebilir.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Windows Forms uygulaması oluşturma

İlk adım **Windows Forms bir uygulama**oluşturmaktır.

1. Visual Studio 'da, **Dosya** menüsünde **Yeni** > **projesi**' ni seçin.

2. Sol bölmedeki **görsel C#**  veya **Visual Basic** ' i genişletin ve ardından **Windows Masaüstü**' nü seçin.

3. Orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **SavingDataInATransactionWalkthrough**olarak adlandırın ve ardından **Tamam**' ı seçin.

     **SavingDataInATransactionWalkthrough** projesi oluşturulup **Çözüm Gezgini**eklenir.

## <a name="create-a-database-data-source"></a>Veritabanı veri kaynağı oluşturma

Bu adım, Northwind örnek veritabanındaki `Customers` ve `Orders` tabloları temel alan bir veri kaynağı oluşturmak için **veri kaynağı Yapılandırma Sihirbazı** ' nı kullanır.

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' i seçin.

2. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** ekranında **veritabanı**' nı seçin ve ardından **İleri**' yi seçin.

4. **Veri bağlantınızı seçin** ekranında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         veya

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** Iletişim kutusunu başlatın ve Northwind veritabanına bir bağlantı oluşturun.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' yi seçin.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** ekranında, **İleri**' yi seçin.

7. **Veritabanı nesnelerinizi seçin** ekranında **Tablolar** düğümünü genişletin.

8. `Customers` ve `Orders` tabloları seçip **son**' u seçin.

     **NorthwindDataSet** , projenize eklenir ve `Customers` ve `Orders` tabloları **veri kaynakları** penceresinde görünür.

## <a name="add-controls-to-the-form"></a>Forma denetim ekleme

Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

1. **Veri kaynakları** penceresinde, **müşteriler** düğümünü genişletin.

2. Ana **müşteriler** düğümünü **veri kaynakları** penceresinden **Form1**üzerine sürükleyin.

   Kayıtlar üzerinde gezinmek için bir <xref:System.Windows.Forms.DataGridView> denetimi ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) formda görüntülenir. Bileşen tepsisinde bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>ve <xref:System.Windows.Forms.BindingNavigator> görüntülenir.

3. İlgili **siparişler** düğümünü (ana **siparişler** düğümünü değil, **Faks** sütununun altındaki Ilişkili alt tablo düğümünü) **CustomersDataGridView**altında bulunan form üzerine sürükleyin.

   Form üzerinde bir <xref:System.Windows.Forms.DataGridView> görünür. Bileşen tepsisinde bir `OrdersTableAdapter` ve <xref:System.Windows.Forms.BindingSource> görüntülenir.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System. Transactions derlemesine bir başvuru ekleyin

İşlemler <xref:System.Transactions> ad alanını kullanır. System. Transactions derlemesine bir proje başvurusu varsayılan olarak eklenmez, bu yüzden el ile eklemeniz gerekir.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System. Transactions DLL dosyasına bir başvuru eklemek için

1. **Proje** menüsünde, **Başvuru Ekle**' yi seçin.

2. **System. Transactions** ( **.net** sekmesinde) öğesini seçin ve ardından **Tamam**' ı seçin.

     **System. Transactions** öğesine bir başvuru projeye eklenir.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator 'ın saveItem düğmesinde kodu değiştirin

Formunuza bırakılan ilk tablo için, varsayılan olarak, <xref:System.Windows.Forms.BindingNavigator>Kaydet düğmesinin `click` olayına kod eklenir. Ek tabloları güncelleştirmek için el ile kod eklemeniz gerekir. Bu izlenecek yol için, Kaydet düğmesinin tıklama olay işleyicisindeki mevcut kaydetme kodunu yeniden tasarlıyoruz. Ayrıca, satırın eklenmesi veya silinmesi gerektiğine bağlı olarak belirli güncelleştirme işlevlerini sağlamak için birkaç yöntem de oluşturacağız.

### <a name="to-modify-the-auto-generated-save-code"></a>Otomatik olarak oluşturulan kaydetme kodunu değiştirmek için

1. **CustomersBindingNavigator** (disket simgesini içeren düğme) üzerinde **Kaydet** düğmesini seçin.

2. `CustomersBindingNavigatorSaveItem_Click` yöntemini aşağıdaki kod ile değiştirin:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

İlgili verilerde yapılan değişiklikleri mutabık kılma sırası aşağıdaki gibidir:

- Alt kayıtları silin. (Bu durumda, `Orders` tablosundan kayıtları silin.)

- Üst kayıtları silin. (Bu durumda, `Customers` tablosundan kayıtları silin.)

- Üst kayıtları ekleyin. (Bu durumda, `Customers` tablosuna kayıtlar ekleyin.)

- Alt kayıtları ekleyin. (Bu durumda, `Orders` tablosuna kayıtlar ekleyin.)

### <a name="to-delete-existing-orders"></a>Mevcut siparişleri silmek için

- Aşağıdaki `DeleteOrders` yöntemini **Form1**öğesine ekleyin:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Mevcut müşterileri silmek için

- Aşağıdaki `DeleteCustomers` yöntemini **Form1**öğesine ekleyin:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Yeni müşteriler eklemek için

- Aşağıdaki `AddNewCustomers` yöntemini **Form1**öğesine ekleyin:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Yeni siparişler eklemek için

- Aşağıdaki `AddNewOrders` yöntemini **Form1**öğesine ekleyin:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Uygulamayı çalıştırın

Uygulamayı çalıştırmak için **F5**'e basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: işlem kullanarak verileri kaydetme](../data-tools/save-data-by-using-a-transaction.md)
- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
