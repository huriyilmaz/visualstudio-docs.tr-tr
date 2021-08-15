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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: be2657c94d49c73d245e7bf8bbb59e3b0b018ba84d942f6144b5e0360f968d5e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121327766"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>İzlenecek yol: Veri Kümesi Tasarımcısı bir veri kümesi oluşturma

Bu izlenecek yolda, **veri kümesi Tasarımcısı** kullanarak bir veri kümesi oluşturursunuz. Makale, yeni bir proje oluşturma ve buna yeni bir **veri kümesi** öğesi ekleme sürecinde size kılavuzluk eden bir işlemdir. Bir sihirbaz kullanmadan bir veritabanındaki tabloları temel alan tablolar oluşturmayı öğreneceksiniz.

## <a name="prerequisites"></a>Önkoşullar

bu izlenecek yol, SQL Server Express localdb ve Northwind örnek veritabanını kullanır.

1. SQL Server Express localdb yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio Yükleyicisi** aracılığıyla yükleyin. Visual Studio Yükleyicisi, SQL Server Express localdb, **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yüklenebilir.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio, **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **yürüt** düğmesini seçin.

       Kısa bir süre sonra sorgu yürütmeyi tamamlar ve Northwind veritabanı oluşturulur.

## <a name="create-a-new-windows-forms-application-project"></a>yeni bir Windows Forms uygulaması oluşturun Project

1. Visual Studio, **dosya** menüsünde **yeni**  >  **Project**' yi seçin.

2. sol bölmedeki **Visual C#** ' ı veya **Visual Basic** genişletin ve sonra **Windows masaüstü**' nü seçin.

3. orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **Datasetdesignerwalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     Visual Studio projeyi **Çözüm Gezgini** ekler ve tasarımcıda yeni bir form görüntüler.

## <a name="add-a-new-dataset-to-the-application"></a>Uygulamaya yeni bir veri kümesi ekleme

1. **Project** menüsünde **yeni öğe ekle**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Sol bölmedeki **veriler**' i seçin ve ardından orta bölmedeki veri **kümesi** ' ni seçin.

3. Veri kümesini **NorthwindDataSet** olarak adlandırın ve ardından **Ekle**' yi seçin.

     Visual Studio, projeye **NorthwindDataset. xsd** adlı bir dosya ekler ve **Veri Kümesi Tasarımcısı** açar.

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

- **Veri kaynakları** penceresinde öğeleri seçin ve bunları bir form üzerine sürükleyin. daha fazla bilgi için bkz. [Visual Studio verileri Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- TableAdapters 'e daha fazla sorgu ekleyin.

- <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> Veri kümesindeki veri tablolarının veya olaylarına doğrulama mantığı ekleyin. Daha fazla bilgi için bkz. [veri kümelerinde verileri doğrulama](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Verileri doğrulama](../data-tools/validate-data-in-datasets.md)
