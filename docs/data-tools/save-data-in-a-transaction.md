---
title: 'İzlenecek yol: Bir işlemde veri kaydetme'
description: Bu kılavuzda, veri kaynağında System.Transactions ad alanını kullanarak bir işlemde veri Visual Studio.
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
ms.openlocfilehash: 223a5985a34f5063eacfcd0125b624a09520e6fb
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133978465"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>İzlenecek yol: Bir işlemde veri kaydetme

Bu kılavuz, ad alanını kullanarak bir işlemde veri kaydetmeyi <xref:System.Transactions> gösterir. Bu kılavuzda, bir Windows Forms uygulaması oluşturabilirsiniz. Northwind örnek veritabanında iki tablo için veri kümesi oluşturmak üzere Veri Kaynağı Yapılandırma Sihirbazı'nı kullanalım. Veri bağlama denetimlerini bir Windows formuna ek olarak BindingNavigator'ın kaydetme düğmesinin kodunu değiştirerek TransactionScope içindeki veritabanını güncelleştirebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. Yerel VERITABANınız yoksa, SQL Server Express sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Yerel Visual Studio Yükleyicisi,SQL Server Express.NET masaüstü geliştirme iş yükünün parçası olarak  veya tek bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (SQL Server Nesne Gezgini, veri depolama ve işleme iş **yükünün bir parçası olarak** Visual Studio Yükleyicisi.) SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Bir sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/main/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Windows Forms uygulaması oluşturma

İlk adım, bir Windows **Forms Uygulaması oluşturmaktır.**

1. Bu Visual Studio, Dosya menüsünde **Yeni** **dosya'Project.**  >  

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve ardından Masaüstü'Windows **seçin.**

3. Orta bölmede Windows **Forms Uygulaması proje** türünü seçin.

4. Projeye **SavingDataInATransactionWalkthrough adını ve** ardından Tamam'ı **seçin.**

     **SavingDataInATransactionWalkthrough** projesi oluşturulur ve **Çözüm Gezgini.**

## <a name="create-a-database-data-source"></a>Veritabanı veri kaynağı oluşturma

Bu adım, Northwind **örnek veritabanındaki** ve tablolarını temel alan bir veri kaynağı oluşturmak için Veri Kaynağı `Customers` Yapılandırma `Orders` Sihirbazı'nı kullanır.

1. Veri Kaynakları **penceresini açmak** için Veri menüsünde **Veri** Kaynaklarını **Göster'i seçin.**

2. Veri Kaynağı **Yapılandırma Sihirbazı'nı** başlatmak **için Veri Kaynakları penceresinde** Yeni Veri Kaynağı **Ekle'yi seçin.**

3. Veri Kaynağı **Türü Seçin ekranında Veritabanı'ı** **ve ardından** Sonraki'yi **seçin.**

4. Veri **Bağlantınızı Seçin ekranında,** aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         -veya-

    - Bağlantı **Ekle/Değiştir** iletişim **kutusunu başlatmak ve** Northwind veritabanına bir bağlantı oluşturmak için Yeni Bağlantı'ya tıklayın.

5. Veritabanınız parola gerektiriyorsa hassas verileri dahil etmek için seçeneğini belirleyin ve ardından Sonraki seçeneğini **belirleyin.**

6. Bağlantı **dizesini Uygulama Yapılandırması dosyasına kaydet ekranında, Sonraki'yi** **seçin.**

7. Veritabanı **Nesnelerinizi seçin ekranında** Tablolar **düğümünü** genişletin.

8. ve `Customers` tablolarını `Orders` ve ardından Son'a **seçin.**

     **NorthwindDataSet** projenize eklenir ve ve `Customers` tabloları Veri Kaynakları `Orders` **penceresinde** görüntülenir.

## <a name="add-controls-to-the-form"></a>Forma denetimler ekleme

Veri Kaynakları penceresindeki öğeleri form üzerine sürükleyerek **veriye bağlı** denetimler oluşturabilirsiniz.

1. Veri **Kaynakları penceresinde** Müşteriler **düğümünü** genişletin.

2. Ana Müşteriler **düğümünü** Veri Kaynakları **penceresinden** **Form1'e sürükleyin.**

   Formda <xref:System.Windows.Forms.DataGridView> kayıtlarda gezinmek için bir denetim ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) görüntülenir. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , ve bileşenleri bileşen <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> tepsisinde görüntülenir.

3. İlgili **Orders düğümünü** (ana **Orders** düğümünü değil, **Faks** sütununu altındaki ilgili alt tablo düğümünü) **CustomersDataGridView** öğesinin altındaki forma sürükleyin.

   Formda <xref:System.Windows.Forms.DataGridView> bir görünür. ve, `OrdersTableAdapter` <xref:System.Windows.Forms.BindingSource> bileşen tepsisinde görüntülenir.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System.Transactions derlemesi için başvuru ekleme

İşlemler ad alanını <xref:System.Transactions> kullanır. System.transactions derlemesi için proje başvurusu varsayılan olarak eklenmez, bu nedenle el ile eklemeniz gerekir.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System.Transactions DLL dosyasına başvuru eklemek için

1. Yeni **Project** Başvuru Ekle'yi **seçin.**

2. **System.Transactions 'ı** **(.NET sekmesinde)** ve ardından Tamam'ı **seçin.**

     Projeye **System.Transactions** başvurusu eklenir.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator'ın SaveItem düğmesinde kodu değiştirme

Form üzerine bırakılan ilk tablo için kod varsayılan olarak üzerinde `click` kaydet düğmesinin olayına <xref:System.Windows.Forms.BindingNavigator> eklenir. Ek tabloları güncelleştirmek için el ile kod eklemeniz gerekir. Bu kılavuzda, mevcut kaydetme kodunu kaydet düğmesinin tıklama olayı işleyicisi dışında yeniden düzenlememiz gerekir. Ayrıca satırın ekleniyor mu yoksa silin mi olduğuna bağlı olarak belirli güncelleştirme işlevleri sağlamak için birkaç yöntem daha oluşturuz.

### <a name="to-modify-the-auto-generated-save-code"></a>Otomatik olarak oluşturulan kaydetme kodunu değiştirmek için

1. **CustomersBindingNavigator'da** Kaydet düğmesini seçin (disket simgesi olan düğme). 

2. `CustomersBindingNavigatorSaveItem_Click` yöntemini aşağıdaki kod ile değiştirin:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet4":::

İlgili verilerde yapılan değişiklikleri mutabık kılınma sırası aşağıdaki gibidir:

- Alt kayıtları silin. (Bu durumda, tablodaki kayıtları `Orders` silin.)

- Üst kayıtları silme. (Bu durumda, tablodaki kayıtları `Customers` silin.)

- Üst kayıtlar ekleme. (Bu durumda tabloya kayıtlar `Customers` ekler.)

- Alt kayıtlar ekleme. (Bu durumda tabloya kayıtlar `Orders` ekler.)

### <a name="to-delete-existing-orders"></a>Mevcut siparişleri silmek için

- `DeleteOrders`Form1'e aşağıdaki **yöntemi ekleyin:**

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet5":::

### <a name="to-delete-existing-customers"></a>Mevcut müşterileri silmek için

- `DeleteCustomers`Form1'e aşağıdaki **yöntemi ekleyin:**

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet6":::

### <a name="to-add-new-customers"></a>Yeni müşteriler eklemek için

- `AddNewCustomers`Form1'e aşağıdaki **yöntemi ekleyin:**

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet7":::

### <a name="to-add-new-orders"></a>Yeni siparişler eklemek için

- `AddNewOrders`Form1'e aşağıdaki **yöntemi ekleyin:**

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet8":::

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı çalıştırmak için **F5**'e basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl kullanılır: bir işlem kullanarak veri kaydetme](../data-tools/save-data-by-using-a-transaction.md)
- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
