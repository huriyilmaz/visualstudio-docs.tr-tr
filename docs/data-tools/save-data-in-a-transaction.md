---
title: 'İzlenecek yol: Bir işlemde veri kaydetme'
description: Bu kılavuzda, Visual Studio ' de System. Transactions ad alanını kullanarak bir işlemde verileri kaydetme konusuna bakın.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3cc1516eb083f6446a30adba8a0973878cd99654
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161908"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>İzlenecek yol: Bir işlemde veri kaydetme

Bu izlenecek yol, ad alanını kullanarak bir işlemde nasıl veri kaydedileceğini gösterir <xref:System.Transactions> . bu kılavuzda bir Windows Forms uygulaması oluşturacaksınız. Northwind örnek veritabanındaki iki tablo için bir veri kümesi oluşturmak üzere veri kaynağı Yapılandırma Sihirbazı 'nı kullanacaksınız. Windows forma veri bağlantılı denetimler ekleyeceksiniz ve bir TransactionScope içinde veritabanını güncelleştirmek için BindingNavigator 'ın kaydet düğmesine ait kodu değiştirirsiniz.

## <a name="prerequisites"></a>Önkoşullar

bu izlenecek yol, SQL Server Express localdb ve Northwind örnek veritabanını kullanır.

1. SQL Server Express localdb yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio Yükleyicisi** aracılığıyla yükleyin. Visual Studio Yükleyicisi, SQL Server Express localdb, **.net masaüstü geliştirme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yüklenebilir.

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

4. Projeyi **SavingDataInATransactionWalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     **SavingDataInATransactionWalkthrough** projesi oluşturulup **Çözüm Gezgini** eklenir.

## <a name="create-a-database-data-source"></a>Veritabanı veri kaynağı oluşturma

Bu adım, Northwind örnek veritabanındaki ve tablolarını temel alan bir veri kaynağı oluşturmak için **veri kaynağı Yapılandırma Sihirbazı** ' nı kullanır `Customers` `Orders` .

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' i seçin.

2. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** ekranında **veritabanı**' nı seçin ve ardından **İleri**' yi seçin.

4. **Veri bağlantınızı seçin** ekranında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         -veya-

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** Iletişim kutusunu başlatın ve Northwind veritabanına bir bağlantı oluşturun.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' yi seçin.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** ekranında, **İleri**' yi seçin.

7. **Veritabanı nesnelerinizi seçin** ekranında **Tablolar** düğümünü genişletin.

8. `Customers`Ve tablolarını seçip `Orders` **son**' u seçin.

     **NorthwindDataSet** , projenize eklenir ve `Customers` `Orders` Tablolar **veri kaynakları** penceresinde görünür.

## <a name="add-controls-to-the-form"></a>Forma denetim ekleme

Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

1. **Veri kaynakları** penceresinde, **müşteriler** düğümünü genişletin.

2. Ana **müşteriler** düğümünü **veri kaynakları** penceresinden **Form1** üzerine sürükleyin.

   <xref:System.Windows.Forms.DataGridView>Kayıtlar üzerinde gezinmek için bir denetim ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) formda görüntülenir. Bileşen tepsisinde bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> görüntülenir.

3. İlgili **siparişler** düğümünü (ana **siparişler** düğümünü değil, **Faks** sütununun altındaki Ilişkili alt tablo düğümünü) **CustomersDataGridView** altında bulunan form üzerine sürükleyin.

   <xref:System.Windows.Forms.DataGridView>Form üzerinde görünür. `OrdersTableAdapter`Ve <xref:System.Windows.Forms.BindingSource> bileşen tepsisinde görünür.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System. Transactions derlemesine bir başvuru ekleyin

İşlemler <xref:System.Transactions> ad alanını kullanır. System. Transactions derlemesine bir proje başvurusu varsayılan olarak eklenmez, bu yüzden el ile eklemeniz gerekir.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System. Transactions DLL dosyasına bir başvuru eklemek için

1. **Project** menüsünde **başvuru ekle**' yi seçin.

2. **System. Transactions** ( **.net** sekmesinde) öğesini seçin ve ardından **Tamam**' ı seçin.

     **System. Transactions** öğesine bir başvuru projeye eklenir.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator 'ın saveItem düğmesinde kodu değiştirin

Formunuza bırakılan ilk tablo için, kod varsayılan olarak `click` , üzerinde Kaydet düğmesinin olayına eklenir <xref:System.Windows.Forms.BindingNavigator> . Ek tabloları güncelleştirmek için el ile kod eklemeniz gerekir. Bu izlenecek yol için, Kaydet düğmesinin tıklama olay işleyicisindeki mevcut kaydetme kodunu yeniden tasarlıyoruz. Ayrıca, satırın eklenmesi veya silinmesi gerektiğine bağlı olarak belirli güncelleştirme işlevlerini sağlamak için birkaç yöntem de oluşturacağız.

### <a name="to-modify-the-auto-generated-save-code"></a>Otomatik olarak oluşturulan kaydetme kodunu değiştirmek için

1. **CustomersBindingNavigator** (disket simgesini içeren düğme) üzerinde **Kaydet** düğmesini seçin.

2. `CustomersBindingNavigatorSaveItem_Click` yöntemini aşağıdaki kod ile değiştirin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet4":::

İlgili verilerde yapılan değişiklikleri mutabık kılma sırası aşağıdaki gibidir:

- Alt kayıtları silin. (Bu durumda, tablodaki kayıtları silin `Orders` .)

- Üst kayıtları silin. (Bu durumda, tablodaki kayıtları silin `Customers` .)

- Üst kayıtları ekleyin. (Bu durumda, kayıtları `Customers` tablosuna ekleyin.)

- Alt kayıtları ekleyin. (Bu durumda, kayıtları `Orders` tablosuna ekleyin.)

### <a name="to-delete-existing-orders"></a>Mevcut siparişleri silmek için

- Aşağıdaki `DeleteOrders` yöntemi **Form1** öğesine ekleyin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet5":::

### <a name="to-delete-existing-customers"></a>Mevcut müşterileri silmek için

- Aşağıdaki `DeleteCustomers` yöntemi **Form1** öğesine ekleyin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet6":::

### <a name="to-add-new-customers"></a>Yeni müşteriler eklemek için

- Aşağıdaki `AddNewCustomers` yöntemi **Form1** öğesine ekleyin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet7":::

### <a name="to-add-new-orders"></a>Yeni siparişler eklemek için

- Aşağıdaki `AddNewOrders` yöntemi **Form1** öğesine ekleyin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet8":::

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı çalıştırmak için **F5**'e basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: işlem kullanarak verileri kaydetme](../data-tools/save-data-by-using-a-transaction.md)
- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
