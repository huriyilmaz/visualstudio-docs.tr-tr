---
title: Veri Kümesi Tasarımcısı bir veri kümesi oluşturma
description: Bu izlenecek yolda, Veri Kümesi Tasarımcısı kullanarak bir veri kümesi oluşturun. Yeni bir proje oluşturma ve buna yeni bir veri kümesi öğesi ekleme sürecini anlayın.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1fe1d75673dc47f423cf398118230cd1530def0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866235"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>İzlenecek yol: Veri Kümesi Tasarımcısı bir veri kümesi oluşturma

Bu izlenecek yolda, **veri kümesi Tasarımcısı** kullanarak bir veri kümesi oluşturursunuz. Makale, yeni bir proje oluşturma ve buna yeni bir **veri kümesi** öğesi ekleme sürecinde size kılavuzluk eden bir işlemdir. Bir sihirbaz kullanmadan bir veritabanındaki tabloları temel alan tablolar oluşturmayı öğreneceksiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi** aracılığıyla yükleyin. Visual Studio Yükleyicisi, SQL Server Express LocalDB, **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yüklenebilir.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu yürütmeyi tamamlar ve Northwind veritabanı oluşturulur.

## <a name="create-a-new-windows-forms-application-project"></a>Yeni bir Windows Forms uygulama projesi oluşturma

1. Visual Studio 'da, **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.

2. Sol bölmedeki **Visual C#** veya **Visual Basic** genişletip **Windows Masaüstü**' nü seçin.

3. Orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **Datasetdesignerwalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     Visual Studio, projeyi **Çözüm Gezgini** ekler ve tasarımcıda yeni bir form görüntüler.

## <a name="add-a-new-dataset-to-the-application"></a>Uygulamaya yeni bir veri kümesi ekleme

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Sol bölmedeki **veriler**' i seçin ve ardından orta bölmedeki veri **kümesi** ' ni seçin.

3. Veri kümesini **NorthwindDataSet** olarak adlandırın ve ardından **Ekle**' yi seçin.

     Visual Studio, projeye **NorthwindDataSet. xsd** adlı bir dosya ekler ve **veri kümesi Tasarımcısı** açar.

## <a name="create-a-data-connection-in-server-explorer"></a>Sunucu Gezgini bir veri bağlantısı oluşturma

1. **Görünüm** menüsünde **Sunucu Gezgini**' a tıklayın.

2. **Sunucu Gezgini**, **veritabanına Bağlan** düğmesine tıklayın.

3. Northwind örnek veritabanıyla bir bağlantı oluşturun.

## <a name="create-the-tables-in-the-dataset"></a>Veri kümesinde tabloları oluşturma

Bu bölümde, veri kümesine nasıl tablo ekleneceği açıklanmaktadır.

### <a name="to-create-the-customers-table"></a>Müşteriler tablosu oluşturmak için

1. **Sunucu Gezgini**' de oluşturduğunuz veri bağlantısını genişletin ve **Tablolar** düğümünü genişletin.

2. **Müşteriler** tablosunu **Sunucu Gezgini** **veri kümesi Tasarımcısı** üzerine sürükleyin.

     Bir **Customers** veri tablosu ve **CustomersTableAdapter** , DataSet 'e eklenir.

### <a name="to-create-the-orders-table"></a>Siparişler tablosu oluşturmak için

- **Orders** tablosunu **Sunucu Gezgini** **veri kümesi Tasarımcısı** üzerine sürükleyin.

     **Siparişler** veri tablosu, **OrdersTableAdapter** ve **Customers** ve **Orders** tabloları arasındaki veri ilişkisi DataSet 'e eklenir.

### <a name="to-create-the-orderdetails-table"></a>OrderDetails tablosu oluşturmak için

- **Order details** tablosunu **Sunucu Gezgini** **veri kümesi Tasarımcısı** üzerine sürükleyin.

     **Sipariş ayrıntıları** veri tablosu, **OrderDetails TableAdapter** ve **Orders** ile **OrderDetails** tabloları arasındaki bir veri ilişkisi DataSet 'e eklenir.

## <a name="next-steps"></a>Sonraki Adımlar

- Veri kümesini kaydedin.

- **Veri kaynakları** penceresinde öğeleri seçin ve bunları bir form üzerine sürükleyin. Daha fazla bilgi için bkz. [Visual Studio 'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- TableAdapters 'e daha fazla sorgu ekleyin.

- <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> Veri kümesindeki veri tablolarının veya olaylarına doğrulama mantığı ekleyin. Daha fazla bilgi için bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Verileri doğrulama](../data-tools/validate-data-in-datasets.md)
