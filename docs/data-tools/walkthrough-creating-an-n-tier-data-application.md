---
title: 'İzlenecek Yol: N Katmanlı Bir Veri Uygulaması Oluşturma'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 944825c00e55fcdb3a1a8f1f0c11d3a37a25025c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639407"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>İzlenecek yol: n katmanlı veri uygulaması oluşturma
*N katmanlı* veri uygulamaları, verilere erişen ve birden çok mantıksal katmana veya katmana ayrılan *uygulamalardır.* Uygulama bileşenlerini farklı katmanlara ayırmak uygulamanızın yönetilebilirliğini ve ölçeklenebilirliğini artırır. Bunu, tüm çözümü yeniden tasarlamanıza gerek kalmadan tek bir katmana uygulanabilen yeni teknolojilerin daha kolay benimsenmesini sağlayarak yapar. N katmanlı mimaride bir sunu katmanı, bir orta katman ve bir veri katmanı bulunur. Orta katmanda genellikle bir veri erişim katmanı, iş mantığı katmanı ve kimlik doğrulaması ve doğrulama gibi paylaşılan bileşenler bulunur. Veri katmanında ilişkisel bir veritabanı vardır. N katmanlı uygulamalar hassas bilgileri orta katmanın veri erişimi katmanında depolayarak sunu katmanına erişimi olan son kullanıcılardan uzakta tutulmasını sağlar. Daha fazla bilgi için bkz. [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md).

N katmanlı uygulamada çeşitli katmanları ayırma yollarından biri, uygulamanıza eklemek istediğiniz her katman için ayrı projeler oluşturmaktır. Türü belirtilmiş veri kümelerinde, üretilen veri kümesinin ve `DataSet Project` kodunun gitmesi gereken projeleri belirleyen bir `TableAdapter` özelliği bulunur.

Bu izlenecek yol, **veri kümesi Tasarımcısı**kullanılarak veri kümesini ve `TableAdapter` kodu ayrık sınıf kitaplığı projelerine nasıl ayırabileceğinizi gösterir. Veri kümesini ve TableAdapter kodunu ayırdıktan sonra, veri erişim katmanına çağırmak için [Visual Studio hizmetinde bir Windows Communication Foundation Hizmetleri ve WCF veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) oluşturun. Son olarak, sunu katmanı olarak bir Windows Forms uygulaması oluşturursunuz. Bu katman veri hizmetindeki verilere erişir.

Bu izlenecek yol sırasında aşağıdaki adımları gerçekleştirirsiniz:

- Birden çok proje içeren yeni bir n katmanlı çözüm oluşturun.

- N katmanlı çözüme iki sınıf kitaplığı ekleme.

- **Veri kaynağı Yapılandırma Sihirbazı 'nı**kullanarak türü belirtilmiş bir veri kümesi oluşturun.

- Oluşturulan [TableAdapters](create-and-configure-tableadapters.md) ve dataset kodunu ayrık projelere ayırın.

- Veri erişim katmanına çağrı göndermek için bir Windows Communication Foundation (WCF) hizmeti oluşturma.

- Veri erişim katmanından veri almak için hizmet içinde işlevler oluşturma.

- Sunu katmanı olarak hizmet verecek bir Windows Forms uygulaması oluşturma.

- Veri kaynağına bağlanan Windows Forms denetimleri oluşturma.

- Veri tablolarını doldurmak için kod yazma.

Bu konunun video sürümü Için video ](../data-tools/media/playvideo.gif) ![link bkz. [video nasıl yapılır: n katmanlı veri uygulaması oluşturma](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Prerequisites
Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi**aracılığıyla yükleyin. **Visual Studio yükleyicisi**, SQL Server Express LocalDB 'yi **.net masaüstü geliştirme** iş yükünün parçası olarak veya bağımsız bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (**SQL Server Nesne Gezgini** , Visual Studio yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Veri kümesini tutmak için n katmanlı çözüm ve sınıf kitaplığı oluşturma (DataEntityTier)
Bu kılavuzun ilk adımı bir çözüm ve iki sınıf kitaplığı projesi oluşturmaktır. İlk sınıf kitaplığı veri kümesini (oluşturulan tür `DataSet` sınıfı ve uygulamanın verilerini tutan DataTable) barındırır. Bu proje uygulamanın veri varlık katmanı olarak kullanılır ve genellikle orta katmanda bulunur. DataSet, ilk veri kümesini oluşturur ve kodu otomatik olarak iki sınıf kitaplığına ayırır.

> [!NOTE]
> **Tamam**' a tıklamadan önce projeyi ve çözümü doğru şekilde girdiğinizden emin olun. Böylece bu kılavuzu tamamlamanız kolaylaşır.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>N katmanlı çözüm ve DataEntityTier sınıf kitaplığı oluşturmak için

1. Visual Studio 'da, **Dosya** menüsünde **Yeni**  > **projesi**' ni seçin.

2. Sol bölmedeki **görsel C#**  veya **Visual Basic** ' i genişletin ve ardından **Windows Masaüstü**' nü seçin.

3. Orta bölmede, **sınıf kitaplığı** proje türünü seçin.

4. Projeyi **DataEntityTier**olarak adlandırın.

5. Çözümü **NTierWalkthrough**olarak adlandırın ve ardından **Tamam**' ı seçin.

     DataEntityTier projesini içeren bir NTierWalkthrough Çözümü oluşturulup **Çözüm Gezgini**eklenir.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>TableAdapters (DataAccessTier) tutmak için sınıf kitaplığı oluşturma
DataEntityTier projesini oluşturduktan sonraki adım başka bir sınıf kitaplığı projesi oluşturmaktır. Bu proje oluşturulan TableAdapters barındırır ve uygulamanın *veri erişim katmanı* olarak adlandırılır. Veri erişim katmanında, veritabanına bağlanmak için gereken bilgiler bulunur ve genelde orta katmanda yer alır.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>TableAdapters için ayrı bir sınıf kitaplığı oluşturmak için

1. **Çözüm Gezgini** çözüme sağ tıklayın ve  > **Yeni proje** **Ekle** ' yi seçin.

2. **Yeni proje** iletişim kutusunda, Orta bölmede, **sınıf kitaplığı**' nı seçin.

3. Projeyi **DataAccessTier** olarak adlandırın ve **Tamam**' ı seçin.

     DataAccessTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="create-the-dataset"></a>Veri kümesini oluşturma
Sonraki adım türü belirtilmiş bir veri kümesi oluşturmaktır. Türü belirtilmiş veri kümeleri, hem veri kümesi sınıfı (`DataTables` sınıfları dahil) hem de tek bir projede `TableAdapter` sınıfları ile oluşturulur. (Tüm sınıflar tek bir dosyada oluşturulur.) Veri kümesini ve TableAdapters farklı projelere ayırdığınızda, bu, diğer projeye taşınan ve `TableAdapter` sınıfları özgün projede bırakarak veri kümesi sınıfıdır. Bu nedenle, projede sonuç olarak TableAdapters (DataAccessTier projesi) içeren veri kümesini oluşturun. **Veri kümesini veri kaynağı Yapılandırma Sihirbazı**'nı kullanarak oluşturursunuz.

> [!NOTE]
> Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanlarını kurma](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma

1. **Çözüm Gezgini**içinde **DataAccessTier** seçin.

2. **Veri** menüsünde **veri kaynaklarını göster**' i seçin.

   **Veri kaynakları** penceresi açılır.

3. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

4. **Veri kaynağı türü seç** sayfasında, **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veri bağlantınızı seçin** sayfasında, aşağıdaki eylemlerden birini gerçekleştirin:

     Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

     veya

     **Yeni bağlantı** ' yı seçerek **bağlantı ekle** iletişim kutusunu açın.

6. Veritabanı parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' yi seçin.

    > [!NOTE]
    > Bir yerel veritabanı dosyası (SQL Server'a bağlanmak yerine) seçtiyseniz projeye dosya eklemek isteyip istemediğiniz sorulabilir. Veritabanı dosyasını projeye eklemek için **Evet** ' i seçin.

7. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

8. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

9. **Müşteriler** ve **siparişler** tablolarının onay kutularını seçin ve ardından **son**' u seçin.

     NorthwindDataSet, DataAccessTier projesine eklenir ve **veri kaynakları** penceresinde görüntülenir.

## <a name="separate-the-tableadapters-from-the-dataset"></a>TableAdapters veri kümesinden ayır
Veri kümesi oluşturduktan sonra, üretilen veri kümesi sınıfını TableAdapter bağdaştırıcılarından ayırın. Bunu, **veri kümesi proje** özelliğini, ayrılmış veri kümesi sınıfının depolayabileceği proje adına ayarlayarak yapabilirsiniz.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>TableAdapter Bağdaştırıcılarını Veri Kümesinden ayırmak için

1. **Veri kümesi Tasarımcısı**veri kümesini açmak Için **Çözüm Gezgini** **NorthwindDataSet. xsd** ' ye çift tıklayın.

2. Tasarımcıda boş bir alan seçin.

3. **Özellikler** penceresinde **veri kümesi proje** düğümünü bulun.

4. **Veri kümesi proje** listesinde **DataEntityTier**' ı seçin.

5. **Build** menüsünde **Build Solution**' ı seçin.

   Veri kümesi ve TableAdapter bağdaştırıcıları iki sınıf kitaplığı projesine ayrılır. Başlangıçta tüm veri kümesini (`DataAccessTier`) içeren proje artık yalnızca TableAdapters içerir. **DataSet proje** özelliğinde (`DataEntityTier`) belirtilen proje türü belirtilmiş veri kümesini Içerir: *NorthwindDataSet. DataSet. Designer. vb* (veya *NorthwindDataSet.DataSet.Designer.cs*).

> [!NOTE]
> Veri kümelerini ve TableAdapters ayırabilirsiniz ( **veri kümesi proje** özelliğini ayarlayarak), projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

## <a name="create-a-new-service-application"></a>Yeni bir hizmet uygulaması oluştur
Bu kılavuzda, bir WCF hizmeti kullanılarak veri erişim katmanına nasıl erişebileceğiniz gösterilmektedir, bu nedenle yeni bir WCF hizmeti uygulaması oluşturalım.

### <a name="to-create-a-new-wcf-service-application"></a>Yeni bir WCF Hizmeti uygulaması oluşturmak için

1. **Çözüm Gezgini** çözüme sağ tıklayın ve  > **Yeni proje** **Ekle** ' yi seçin.

2. **Yeni proje** iletişim kutusunda, sol taraftaki bölmede, **WCF**' yi seçin. Orta bölmede, **WCF hizmet kitaplığı**' nı seçin.

3. Proje **veri hizmetini** adlandırın ve **Tamam**' ı seçin.

     DataService projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Müşteriler ve siparişler verilerini döndürmek için veri erişim katmanında Yöntemler oluşturun
Veri hizmeti, veri erişim katmanında iki yöntemi çağırmalıdır: `GetCustomers` ve `GetOrders`. Bu yöntemler, Northwind `Customers` ve `Orders` tabloları döndürür. @No__t_2 projesinde `GetCustomers` ve `GetOrders` yöntemlerini oluşturun.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Veri erişim katmanında Customers tablosunu döndüren bir yöntem oluşturmak için

1. **Çözüm Gezgini**' de, veri kümesini açmak için **NorthwindDataSet. xsd** ' ye çift tıklayın.

2. **CustomersTableAdapter** öğesine sağ tıklayın ve **Sorgu Ekle**' ye tıklayın.

3. **Bir komut türü seçin** sayfasında, varsayılan değer olan **SQL deyimlerini kullanın** ve **İleri**' ye tıklayın.

4. **Bir sorgu türü seçin** sayfasında, **satırları döndüren Seç** varsayılan değerini bırakın ve **İleri**' ye tıklayın.

5. **BIR SQL SELECT Ifadesini belirtin** sayfasında, varsayılan sorguyu bırakın ve **İleri**' ye tıklayın.

6. **Oluşturulacak yöntemleri seçin** sayfasında, **bir DataTable döndürün** bölümüne **Yöntem adı** için **GetCustomers** yazın.

7. **Son**'a tıklayın.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Veri erişim katmanında Orders tablosunu döndüren bir yöntem oluşturmak için

1. **OrdersTableAdapter** öğesine sağ tıklayın ve **Sorgu Ekle**' ye tıklayın.

2. **Bir komut türü seçin** sayfasında, varsayılan değer olan **SQL deyimlerini kullanın** ve **İleri**' ye tıklayın.

3. **Bir sorgu türü seçin** sayfasında, **satırları döndüren Seç** varsayılan değerini bırakın ve **İleri**' ye tıklayın.

4. **BIR SQL SELECT Ifadesini belirtin** sayfasında, varsayılan sorguyu bırakın ve **İleri**' ye tıklayın.

5. **Oluşturulacak yöntemleri seçin** sayfasında, **bir DataTable döndürün** bölümüne **Yöntem adı** için **GetOrders** yazın.

6. **Son**'a tıklayın.

7. **Yapı** menüsünde **çözüm oluştur**' a tıklayın.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Veri hizmetine veri varlığa ve veri erişim katmanlarına bir başvuru ekleyin
Veri hizmeti veri kümesinden ve TableAdapters bilgi gerektirdiğinden, **DataEntityTier** ve **DataAccessTier** projelerine başvurular ekleyin.

### <a name="to-add-references-to-the-data-service"></a>Veri hizmetine başvuru eklemek için

1. **Çözüm Gezgini** **veri hizmeti** ' ne sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** Iletişim kutusunda **Projeler** sekmesine tıklayın.

3. Hem **DataAccessTier** hem de **DataEntityTier** projelerini seçin.

4. **Tamam**'a tıklayın.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Veri erişim katmanında GetCustomers ve GetOrders yöntemlerini çağırmak için hizmete işlevler ekleyin
Şimdi veri erişim katmanında veri döndürme yöntemleri bulunduğuna göre, veri erişim katmanındaki yöntemleri çağırmak için veri hizmetinde yöntemler oluşturun.

> [!NOTE]
> C# projelerinde aşağıdaki kodu derlemek için `System.Data.DataSetExtensions` derlemesine bir başvuru eklemeniz gerekir.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Veri hizmetinde GetCustomers ve GetOrders işlevlerini oluşturmak için

1. **DataService** projesinde **IService1. vb** veya **IService1.cs**öğesine çift tıklayın.

2. Aşağıdaki kodu, **hizmet Işlemlerinizi ekleyin** açıklaması altına ekleyin:

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3. DataService projesinde **Service1. vb** (veya **Service1.cs**) öğesine çift tıklayın.

4. Aşağıdaki kodu **Service1** sınıfına ekleyin:

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5. **Yapı** menüsünde **çözüm oluştur**' a tıklayın.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Veri hizmetinden verileri göstermek için bir sunum katmanı oluşturma
Artık çözüm, veri erişim katmanına çağrı yapan yöntemlere sahip veri hizmetini içerdiğinden, veri hizmetine çağıran ve verileri kullanıcılara sunan başka bir proje oluşturun. Bu kılavuz için bir Windows Forms uygulaması oluşturun; bu n katmanlı uygulamanın sunu katmanıdır.

### <a name="to-create-the-presentation-tier-project"></a>Sunu katmanı projesi oluşturmak için

1. **Çözüm Gezgini** çözüme sağ tıklayın ve  > **Yeni proje** **Ekle** ' yi seçin.

2. **Yeni proje** iletişim kutusunda, sol taraftaki bölmede **Windows Masaüstü**' nü seçin. Orta bölmede **Windows Forms uygulama**' yı seçin.

3. Projeyi **PresentationTier** olarak adlandırın ve **Tamam**' a tıklayın.

    PresentationTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>PresentationTier projesini başlangıç projesi olarak ayarla
Verileri sunan ve bunlarla etkileşime girdiği gerçek istemci uygulaması olduğundan, **PresentationTier** projesini çözümün başlangıç projesi olarak ayarlayacağız.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Yeni sunum katmanı projesini başlangıç projesi olarak ayarlamak için

- **Çözüm Gezgini**, **PresentationTier** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' ya tıklayın.

## <a name="add-references-to-the-presentation-tier"></a>Sunu katmanına başvuru ekleme
İstemci uygulaması, PresentationTier hizmette yöntemlere erişebilmek için veri hizmetine bir hizmet başvurusu gerektirir. Buna ek olarak, WCF hizmeti tür paylaşımını etkinleştirmek için veri kümesine bir başvuru gerektirir. Veri hizmeti aracılığıyla tür paylaşımını etkinleştirene kadar, kısmi veri kümesi sınıfına eklenen kod sunu katmanında kullanılamaz. Genellikle bir veri tablosunun satır ve sütun değiştirme olaylarına ilişkin doğrulama kodu gibi kodu eklediğiniz için, bu koda istemciden erişmek isteyeceksiniz.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Sunu katmanına bir başvuru eklemek için

1. **Çözüm Gezgini**, **PresentationTier** öğesine sağ tıklayın ve **Başvuru Ekle**' yi seçin.

2. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesini seçin.

3. **DataEntityTier** ' ı seçin ve **Tamam**' ı seçin.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Sunu katmanına bir hizmet başvurusu eklemek için

1. **Çözüm Gezgini**, **PresentationTier** öğesine sağ tıklayıp **hizmet başvurusu Ekle**' i seçin.

2. **Hizmet başvurusu Ekle** Iletişim kutusunda **bul**' u seçin.

3. **Service1** öğesini seçin ve **Tamam**' ı seçin.

    > [!NOTE]
    > Geçerli bilgisayarda birden fazla hizmet varsa, bu kılavuzda daha önce oluşturduğunuz hizmeti (`GetCustomers` ve `GetOrders` yöntemlerini içeren hizmet) seçin.

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Veri hizmeti tarafından döndürülen verileri göstermek için forma DataGrid görünümleri ekleyin
Hizmet başvurusunu veri hizmetine ekledikten sonra, **veri kaynakları** penceresi hizmet tarafından döndürülen verilerle otomatik olarak doldurulur.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Forma iki DataGridView veri bağlama öğesi eklemek için

1. **Çözüm Gezgini**, **PresentationTier** projesini seçin.

2. **Veri kaynakları** penceresinde, **NorthwindDataSet** ' i genişletin ve **müşteriler** düğümünü bulun.

3. **Müşteriler** düğümünü Form1 üzerine sürükleyin.

4. **Veri kaynakları** penceresinde, **müşteriler** düğümünü genişletin ve ilgili **siparişler** düğümünü bulun ( **müşteriler** düğümünde iç içe geçmiş **siparişler** düğümü).

5. İlişkili **siparişler** düğümünü Form1 üzerine sürükleyin.

6. Formda boş bir alanı çift tıklayarak bir `Form1_Load` olay işleyicisi oluşturun.

7. @No__t_0 olay işleyicisine aşağıdaki kodu ekleyin.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Hizmet tarafından izin verilen en büyük ileti boyutunu artırın
@No__t_0 için varsayılan değer `Customers` ve `Orders` tablolarından alınan verileri tutabilecek kadar büyük değildir. Aşağıdaki adımlarda değeri 6553600 olarak artıracaksınız. İstemci üzerinde, hizmet başvurusunu otomatik olarak güncelleştiren değeri değiştirirsiniz.

> [!NOTE]
> Varsayılan alt sınır boyutu hizmet reddi (DoS) saldırılarına maruz kalmayı sınırlamak içindir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>MaxReceivedMessageSize değerini artırmak için

1. **Çözüm Gezgini**, **PresentationTier** projesindeki **app. config** dosyasına çift tıklayın.

2. **Maxreceived ileti** boyutu özniteliğini bulun ve değeri `6553600` değiştirin.

## <a name="test-the-application"></a>Uygulamayı test etme
**F5**tuşuna basarak uygulamayı çalıştırın. @No__t_0 ve `Orders` tablolarından alınan veriler veri hizmetinden alınır ve formda görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar
Uygulama gereksinimlerinize bağlı olarak, Windows tabanlı bir uygulama içinde ilgili verileri kaydettikten sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Örneğin, bu uygulamada aşağıdaki geliştirmeleri yapabilirsiniz:

- Veri kümesine doğrulama ekleme.

- Verileri tekrar veritabanında güncelleştirmek için hizmete ek yöntemler ekleme.

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı uygulamalarda veri kümeleriyle çalışma](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)