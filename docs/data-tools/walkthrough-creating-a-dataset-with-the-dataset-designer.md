---
title: Veri Kümesi Tasarımcısı ile veri kümesi oluşturma
description: Bu kılavuzda, veri kümesi oluşturmak için Veri Kümesi Tasarımcısı. Yeni bir proje oluşturma ve buna yeni bir DataSet öğesi ekleme işlemini anlama.
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
ms.openlocfilehash: 9ca792310184dfe0b19cd01f34de5cecd11eff38
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133977412"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Adım adım kılavuz: Veri Kümesi oluşturma ve Veri Kümesi Tasarımcısı

Bu kılavuzda, Veri Kümesi Tasarımcısı kullanarak bir veri **kümesi Veri Kümesi Tasarımcısı.** Makale, yeni bir proje oluşturma ve buna yeni bir **DataSet** öğesi ekleme işlemi boyunca size yol gösterir. Sihirbaz kullanmadan veritabanındaki tabloları temel alan tablolar oluşturma hakkında bilgi edinebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. Yerel VERITABANınız yoksa, SQL Server Express sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Yerel Visual Studio Yükleyicisi SQL Server Express, Veri depolama ve işleme iş yükünün bir  parçası olarak veya tek bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (SQL Server Nesne Gezgini, veri depolama ve işleme iş **yükünün bir parçası olarak** Visual Studio Yükleyicisi.) SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Bir sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/main/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgu yürütmeyi tamamlar ve Northwind veritabanı oluşturulur.

## <a name="create-a-new-windows-forms-application-project"></a>Yeni Windows Forms Uygulama Project

1. Bu Visual Studio, Dosya menüsünde **Yeni** **dosya'Project.**  >  

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve ardından Masaüstü'Windows **seçin.**

3. Orta bölmede Windows **Forms Uygulaması proje** türünü seçin.

4. Projeye **DatasetDesignerWalkthrough adını ve** ardından Tamam'ı **seçin.**

     Visual Studio projeye ekler **Çözüm Gezgini** tasarımcıda yeni bir form görüntüler.

## <a name="add-a-new-dataset-to-the-application"></a>Uygulamaya Yeni Veri Kümesi Ekleme

1. Yeni **Project** **Ekle'yi seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Sol bölmede Veri'yi **ve** ardından orta **bölmede DataSet'i** seçin.

3. Veri kümesine **NorthwindDataset adını ve** ardından Ekle'yi **seçin.**

     Visual Studio **NorthwindDataset.xsd** adlı bir dosyayı projeye ekler ve dosyasında **Veri Kümesi Tasarımcısı.**

## <a name="create-a-data-connection-in-server-explorer"></a>Sunucu Gezgini'de Veri Bağlantısı oluşturma

1. Görünüm menüsünde **Seç'e** **Sunucu Gezgini.**

2. Bu **Sunucu Gezgini** veritabanına **Bağlan düğmesine** tıklayın.

3. Northwind örnek veritabanına bir bağlantı oluşturun.

## <a name="create-the-tables-in-the-dataset"></a>Veri Kümesinde Tabloları Oluşturma

Bu bölümde veri kümesine tablo ekleme açıkılmaktadır.

### <a name="to-create-the-customers-table"></a>Müşteriler tablosu oluşturmak için

1. içinde oluşturduğunuz veri bağlantısını **Sunucu Gezgini** ve ardından Tablolar **düğümünü** genişletin.

2. Customers **tabloyu** **Sunucu Gezgini** tablosuna **Veri Kümesi Tasarımcısı.**

     Veri **kümesine** **Customers veri tablosu ve CustomersTableAdapter** eklenir.

### <a name="to-create-the-orders-table"></a>Siparişler tablosu oluşturmak için

- Orders **tablosundan** **Sunucu Gezgini** tablosuna **Veri Kümesi Tasarımcısı.**

     Bir **Orders** veri tablosu, **OrdersTableAdapter** ve **Customers** ile **Orders** tabloları arasındaki veri ilişkisi veri kümesine eklenir.

### <a name="to-create-the-orderdetails-table"></a>OrderDetails tablosu oluşturmak için

- Order **Details Sunucu Gezgini** **Veri Kümesi Tasarımcısı.** 

     Order **Details veri** tablosu, **OrderDetailsTableAdapter** ve **Orders** ile **OrderDetails** tabloları arasındaki veri ilişkisi veri kümesine eklenir.

## <a name="next-steps"></a>Sonraki Adımlar

- Veri kümelerini kaydedin.

- Veri Kaynakları penceresinde **öğeleri seçin** ve bir forma sürükleyin. Daha fazla bilgi için [bkz. Windows Forms denetimlerini Visual Studio.](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

- TableAdapter'lara daha fazla sorgu ekleyin.

- Veri kümesinde veri <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> tablolarının veya olaylarına doğrulama mantığı ekleyin. Daha fazla bilgi için [bkz. Veri kümelerini verileri doğrulama.](../data-tools/validate-data-in-datasets.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Verileri doğrulama](../data-tools/validate-data-in-datasets.md)
