---
title: Formlar arasında veri geçirme
description: Bu Windows Forms denetimleri kılavuzunda, bir forma veri geçirmeye ilişkin adım adım yönergeler edinebilirsiniz.
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 030fe8a72637e82bc317c5fb457f4e8861223c52
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045053"
---
# <a name="pass-data-between-forms"></a>Formlar arasında veri geçirme

Bu kılavuz, verileri bir forma başka bir forma geçirmeye ilişkin adım adım yönergeler sağlar. Northwind'den müşteriler ve sipariş tablolarını kullanan bir form, kullanıcıların bir müşteri seçmelerini sağlar ve ikinci bir form seçilen müşterinin siparişlerini görüntüler. Bu kılavuzda, ilk forma veri alan ikinci formda bir yöntemin nasıl oluşturularak ilgili bilgiler yer alır.

> [!NOTE]
> Bu kılavuz, formlar arasında veri geçirmenin yalnızca bir yolunu gösteriyor. Bir forma veri geçirmeye yönelik başka seçenekler de vardır; örneğin, verileri almak için ikinci bir oluşturucu oluşturma veya ilk forma ait verilerle ayarlan bir genel özellik oluşturma.

Bu kılavuzda gösterilen görevler şunlardır:

- Forms Uygulaması **Windows yeni bir oluşturma.**

- Veri Kaynağı Yapılandırma Sihirbazı ile veri [kümesi oluşturma ve yapılandırma.](../data-tools/media/data-source-configuration-wizard.png)

- Veri Kaynakları penceresinden öğeleri sürüklerken formda oluşturulacak **denetimi** seçme. Daha fazla bilgi için [bkz. Veri Kaynakları penceresinden sürüklenrken oluşturulacak denetimi ayarlama.](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

- Veri Kaynakları penceresindeki öğeleri bir forma **sürükleyerek veriye bağlı** denetim oluşturma.

- Verileri görüntülemek için kılavuz ile ikinci bir form oluşturma.

- Belirli bir müşteriye ait siparişleri getirmek için TableAdapter sorgusu oluşturma.

- Formlar arasında veri geçirme.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. Yerel VERITABANınız yoksa, SQL Server Express sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Yerel Visual Studio Yükleyicisi SQL Server Express, Veri depolama ve işleme iş yükünün bir  parçası olarak veya tek bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (SQL Server Nesne Gezgini, veri depolama ve işleme iş **yükünün bir parçası** olarak Visual Studio Yükleyicisi.) SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Bir sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="create-the-windows-forms-app-project"></a>Windows Forms uygulama projesini oluşturma

1. Dosya Visual Studio Menüsünde **Yeni** Dosya'Project.   >  

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve ardından Masaüstü'Windows **seçin.**

3. Orta bölmede Windows **Forms Uygulaması proje** türünü seçin.

4. Projeye **PassingDataBetweenForms adını ve** ardından Tamam'ı **seçin.**

     **PassingDataBetweenForms** projesi oluşturulur ve **Çözüm Gezgini.**

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

1. Veri Kaynakları **penceresini açmak** için Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

2. Veri Kaynağı **Yapılandırma sihirbazını** başlatmak **için Veri Kaynakları penceresinde** Yeni Veri Kaynağı **Ekle'yi** seçin.

3. Veri **Kaynağı** Türü **Seçin sayfasında Veritabanı'ı seçin** ve ardından Sonraki'ye **tıklayın.**

4. Veritabanı **modeli seçin sayfasında,** Veri Kümesi'nin **belirtilmiş olduğunu** doğrulayın ve ardından Sonraki 'ye **tıklayın.**

5. Veri **Bağlantınızı Seçin** sayfasında, aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - Bağlantı **Ekle/Değiştir** iletişim **kutusunu başlatmak için Yeni Bağlantı'ya** tıklayın.

6. Veritabanınız bir parola gerektiriyorsa ve hassas verileri dahil olma seçeneği etkinse seçeneği belirtin ve ardından Sonraki'ye **tıklayın.**

7. Bağlantı **dizesini Uygulama Yapılandırması dosyasına kaydet sayfasında, Sonraki** 'ye **tıklayın.**

8. Veritabanı **Nesnelerinizi seçin sayfasında** Tablolar **düğümünü** genişletin.

9. **Customers** ve **Orders tablolarını seçin** ve ardından Son'a **tıklayın.**

     **NorthwindDataSet** projenize eklenir ve Veri Kaynakları **penceresinde** **Müşteriler** ve **Siparişler tabloları** görüntülenir.

## <a name="create-the-first-form-form1"></a>İlk formu oluşturma (Form1)

Veri Kaynakları penceresinden Müşteriler düğümünü forma sürükleyerek veriye bağlı kılavuz <xref:System.Windows.Forms.DataGridView> **(denetim)** oluşturabilirsiniz. 

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Formda veriye bağlı kılavuz oluşturmak için

- Ana Müşteriler **düğümünü** Veri Kaynakları **penceresinden** **Form1'e sürükleyin.**

     <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingNavigator> **Form1'de** kayıtlarda gezinmek için bir ve araç şeridi ( ) görüntülenir. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource> ve bileşen <xref:System.Windows.Forms.BindingNavigator> tepsisinde görüntülenir.

## <a name="create-the-second-form"></a>İkinci formu oluşturma

Verilerin geçeceği ikinci bir form oluşturun.

1. Project **Form** **ekle'yi Windows seçin.**

2. **Form2** varsayılan adını bırakın ve Ekle'ye **tıklayın.**

3. Ana Orders **düğümünü** Veri Kaynakları **penceresinden** **Form2'ye sürükleyin.**

     <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingNavigator> **Form2'de** kayıtlarda gezinmek için bir ve araç şeridi ( ) görüntülenir. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource> ve bileşen <xref:System.Windows.Forms.BindingNavigator> tepsisinde görüntülenir.

4. Bileşen **tepsisinde OrdersBindingNavigator'ı** silin.

     **OrdersBindingNavigator** **Form2'den kaybolur.**

## <a name="add-a-tableadapter-query"></a>TableAdapter sorgusu ekleme

Form1'de seçili müşteriye ait siparişleri yüklemek için Form2'ye bir TableAdapter sorgusu ekleyin.

1. içinde **NorthwindDataSet.xsd dosyasına** **çift Çözüm Gezgini.**

2. **OrdersTableAdapter'a sağ tıklayın ve** Sorgu **Ekle'yi seçin.**

3. Varsayılan Use **SQL deyimini bırakın** ve ardından Sonraki 'ye **tıklayın.**

4. Satırları döndüren varsayılan **SELECT seçeneğini bırakın ve ardından** Sonraki 'ye **tıklayın.**

5. temel alarak dönmek için sorguya bir WHERE `Orders` yan tümcesi `CustomerID` ekleyin. Sorgu aşağıdakine benzemelidir:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Veritabanınız için doğru parametre söz dizimini doğrulayın. Örneğin Microsoft Access'te WHERE yan tümcesi şöyle olabilir: `WHERE CustomerID = ?` .

6. **İleri**’ye tıklayın.

7. Bir **DataTableMethod Adını Doldur için** `FillByCustomerID` yazın.

8. **DataTable İadesi seçeneğinin temizlemesi** ve ardından Sonraki'ye **tıklayın.**

9. **Finish (Son)** düğmesine tıklayın.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Form2'de verilere geçiş yapmak için bir yöntem oluşturma

1. **Form2'ye sağ tıklayın** ve Kod **Düzenleyicisi'nde** **Form2'yi açmak için Kodu** **Görüntüle'yi seçin.**

2. Yöntemin ardından **Form2'ye** aşağıdaki kodu `Form2_Load` ekleyin:

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb" id="Snippet1":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs" id="Snippet1":::

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Form1'de veri geçişi yapmak ve Form2'i görüntülemek için yöntem oluşturma

1. **Form1'de** Müşteri veri kılavuzuna sağ tıklayın ve ardından Özellikler'e **tıklayın.**

2. Özellikler penceresinde **Olaylar'a** **tıklayın.**

3. **CellDoubleClick olayına çift** tıklayın.

     Kod düzenleyicisi görünür.

4. Yöntem tanımını aşağıdaki örnekle eş olacak şekilde güncelleştirin:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet2":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet2":::

## <a name="run-the-app"></a>Uygulamayı çalıştırma

- Uygulamayı çalıştırmak için **F5**'e basın.

- Form1'de bir müşteri **kaydına çift** tıklar ve **Form2'yi** müşterinin siparişleriyle açın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, formlar arasında veri geçirmenin ardından gerçekleştirmek istediğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- Veritabanı nesneleri eklemek veya çıkarmak için veri kümesini düzenleme. Daha fazla bilgi için [bkz. Veri kümeleri oluşturma ve yapılandırma.](../data-tools/create-and-configure-datasets-in-visual-studio.md)

- Verileri veritabanına geri kaydetme işlevi ekleme. Daha fazla bilgi için [bkz. Verileri veritabanına geri kaydetme.](../data-tools/save-data-back-to-the-database.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
