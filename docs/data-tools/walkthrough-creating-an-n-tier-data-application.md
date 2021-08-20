---
title: 'İzlenecek yol: N katmanlı veri uygulaması oluşturma'
description: Bu izlenecek yolda N katmanlı bir veri uygulaması oluşturun. N katmanlı veri uygulamaları, verilere erişen ve birçok mantıksal katmana veya katmana ayrılan uygulamalardır.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fbdd4b7ffbfdef2cfce9904a92cc392594e6508f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129941"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>İzlenecek yol: n katmanlı veri uygulaması oluşturma
*N katmanlı* veri uygulamaları, verilere erişen ve birden çok mantıksal katmana veya katmana ayrılan *uygulamalardır.* Uygulama bileşenlerini farklı katmanlara ayırmak uygulamanızın yönetilebilirliğini ve ölçeklenebilirliğini artırır. Bunu, tüm çözümü yeniden tasarlamanıza gerek kalmadan tek bir katmana uygulanabilen yeni teknolojilerin daha kolay benimsenmesini sağlayarak yapar. N katmanlı mimaride bir sunu katmanı, bir orta katman ve bir veri katmanı bulunur. Orta katmanda genellikle bir veri erişim katmanı, iş mantığı katmanı ve kimlik doğrulaması ve doğrulama gibi paylaşılan bileşenler bulunur. Veri katmanında ilişkisel bir veritabanı vardır. N katmanlı uygulamalar hassas bilgileri orta katmanın veri erişimi katmanında depolayarak sunu katmanına erişimi olan son kullanıcılardan uzakta tutulmasını sağlar. Daha fazla bilgi için bkz. [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md).

N katmanlı uygulamada çeşitli katmanları ayırma yollarından biri, uygulamanıza eklemek istediğiniz her katman için ayrı projeler oluşturmaktır. Türü belirtilmiş veri kümelerinde, üretilen veri kümesinin ve `DataSet Project` kodunun gitmesi gereken projeleri belirleyen bir `TableAdapter` özelliği bulunur.

Bu izlenecek yol `TableAdapter` , **veri kümesi Tasarımcısı** kullanarak veri kümesini ve kodu ayrık sınıf kitaplığı projelerine nasıl ayırabileceğinizi gösterir. veri kümesini ve TableAdapter kodunu ayırdıktan sonra, veri erişim katmanını çağırmak için Visual Studio hizmetinde bir [Windows Communication Foundation hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) oluşturun. son olarak, sunu katmanı olarak bir Windows Forms uygulaması oluşturursunuz. Bu katman veri hizmetindeki verilere erişir.

Bu izlenecek yol sırasında aşağıdaki adımları gerçekleştirirsiniz:

- Birden çok proje içeren yeni bir n katmanlı çözüm oluşturun.

- N katmanlı çözüme iki sınıf kitaplığı ekleme.

- **Veri kaynağı Yapılandırma Sihirbazı 'nı** kullanarak türü belirtilmiş bir veri kümesi oluşturun.

- Oluşturulan [TableAdapters](create-and-configure-tableadapters.md) ve dataset kodunu ayrık projelere ayırın.

- Veri erişim katmanına çağrı göndermek için bir Windows Communication Foundation (WCF) hizmeti oluşturma.

- Veri erişim katmanından veri almak için hizmet içinde işlevler oluşturma.

- Sunu katmanı olarak hizmet verecek bir Windows Forms uygulaması oluşturma.

- Veri kaynağına bağlanan Windows Forms denetimleri oluşturma.

- Veri tablolarını doldurmak için kod yazma.

![video bağlantısı ](../data-tools/media/playvideo.gif) Bu konunun video sürümü için bkz. [video nasıl yapılır: n katmanlı veri uygulaması oluşturma](/previous-versions/visualstudio/visual-studio-2008/cc178916(v=vs.90)).

## <a name="prerequisites"></a>Önkoşullar
bu izlenecek yol, SQL Server Express localdb ve Northwind örnek veritabanını kullanır.

1. SQL Server Express localdb yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio Yükleyicisi** aracılığıyla yükleyin. **Visual Studio Yükleyicisi**, SQL Server Express localdb 'yi **.net masaüstü geliştirme** iş yükünün parçası olarak veya bağımsız bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio, **SQL Server Nesne Gezgini** penceresini açın. (**SQL Server Nesne Gezgini** , Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **yürüt** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Veri kümesini tutmak için n katmanlı çözüm ve sınıf kitaplığı oluşturma (DataEntityTier)
Bu kılavuzun ilk adımı bir çözüm ve iki sınıf kitaplığı projesi oluşturmaktır. İlk sınıf kitaplığı veri kümesini (oluşturulan türü belirtilmiş `DataSet` sınıfı ve uygulamanın verilerini tutan DataTable) barındırır. Bu proje uygulamanın veri varlık katmanı olarak kullanılır ve genellikle orta katmanda bulunur. DataSet, ilk veri kümesini oluşturur ve kodu otomatik olarak iki sınıf kitaplığına ayırır.

> [!NOTE]
> **Tamam**' a tıklamadan önce projeyi ve çözümü doğru şekilde girdiğinizden emin olun. Böylece bu kılavuzu tamamlamanız kolaylaşır.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>N katmanlı çözüm ve DataEntityTier sınıf kitaplığı oluşturmak için

1. Visual Studio, **dosya** menüsünde **yeni**  >  **Project**' yi seçin.

2. sol bölmedeki **Visual C#** ' ı veya **Visual Basic** genişletin ve sonra **Windows masaüstü**' nü seçin.

3. Orta bölmede, **sınıf kitaplığı** proje türünü seçin.

4. Projeyi **DataEntityTier** olarak adlandırın.

5. Çözümü **NTierWalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     DataEntityTier projesini içeren bir NTierWalkthrough Çözümü oluşturulup **Çözüm Gezgini** eklenir.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>TableAdapters (DataAccessTier) tutmak için sınıf kitaplığı oluşturma
DataEntityTier projesini oluşturduktan sonraki adım başka bir sınıf kitaplığı projesi oluşturmaktır. Bu proje oluşturulan TableAdapters barındırır ve uygulamanın *veri erişim katmanı* olarak adlandırılır. Veri erişim katmanında, veritabanına bağlanmak için gereken bilgiler bulunur ve genelde orta katmanda yer alır.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>TableAdapters için ayrı bir sınıf kitaplığı oluşturmak için

1. **Çözüm Gezgini** çözüme sağ tıklayın ve   >  **yeni Project** ekle ' yi seçin.

2. **yeni Project** iletişim kutusunda, orta bölmede, **sınıf kitaplığı**' nı seçin.

3. Projeyi **DataAccessTier** olarak adlandırın ve **Tamam**' ı seçin.

     DataAccessTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="create-the-dataset"></a>Veri kümesini oluşturma
Sonraki adım türü belirtilmiş bir veri kümesi oluşturmaktır. Türü belirtilmiş veri kümeleri, hem veri kümesi sınıfı ( `DataTables` sınıflar dahil) hem de `TableAdapter` tek bir projedeki sınıflar ile oluşturulur. (Tüm sınıflar tek bir dosyada oluşturulur.) Veri kümesini ve TableAdapters farklı projelere ayırdığınızda, bu, diğer projeye taşınan ve sınıflar orijinal projedeki dışında bırakarak veri kümesi sınıfıdır `TableAdapter` . Bu nedenle, projede sonuç olarak TableAdapters (DataAccessTier projesi) içeren veri kümesini oluşturun. **Veri kümesini veri kaynağı Yapılandırma Sihirbazı**'nı kullanarak oluşturursunuz.

> [!NOTE]
> Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanlarını kurma](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma

1. **Çözüm Gezgini** içinde **DataAccessTier** seçin.

2. **Veri** menüsünde **veri kaynaklarını göster**' i seçin.

   **Veri kaynakları** penceresi açılır.

3. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

4. **Veri kaynağı türü seç** sayfasında, **veritabanı** ' nı seçin ve ardından **İleri**' yi seçin.

5. **Veri bağlantınızı seçin** sayfasında, aşağıdaki eylemlerden birini gerçekleştirin:

     Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

     -veya-

     **Yeni bağlantı** ' yı seçerek **bağlantı ekle** iletişim kutusunu açın.

6. Veritabanı parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' yi seçin.

    > [!NOTE]
    > Bir yerel veritabanı dosyası (SQL Server'a bağlanmak yerine) seçtiyseniz projeye dosya eklemek isteyip istemediğiniz sorulabilir. Veritabanı dosyasını projeye eklemek için **Evet** ' i seçin.

7. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri ' yi** seçin.

8. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

9. **Müşteriler** ve **siparişler** tablolarının onay kutularını seçin ve ardından **son**' u seçin.

     NorthwindDataSet, DataAccessTier projesine eklenir ve **veri kaynakları** penceresinde görüntülenir.

## <a name="separate-the-tableadapters-from-the-dataset"></a>TableAdapters veri kümesinden ayır
Veri kümesi oluşturduktan sonra, üretilen veri kümesi sınıfını TableAdapter bağdaştırıcılarından ayırın. bunu, **dataset Project** özelliğini, ayrılmış veri kümesi sınıfının depolayabileceği proje adına ayarlayarak yapabilirsiniz.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>TableAdapter Bağdaştırıcılarını Veri Kümesinden ayırmak için

1. **Veri kümesi Tasarımcısı** veri kümesini açmak Için **Çözüm Gezgini** **NorthwindDataSet. xsd** ' ye çift tıklayın.

2. Tasarımcıda boş bir alan seçin.

3. **özellikler** penceresinde **veri kümesi Project** düğümünü bulun.

4. **veri kümesi Project** listesinde **dataentitytier**' ı seçin.

5. **Build** menüsünde **Build Solution**' ı seçin.

   Veri kümesi ve TableAdapter bağdaştırıcıları iki sınıf kitaplığı projesine ayrılır. Başlangıçta tüm veri kümesi ( ) içeren proje `DataAccessTier` artık yalnızca TableAdapter'ları içeriyor. **DataSet Project** özelliğinde belirlenen proje ( ) türü belirlenmiş veri kümesi `DataEntityTier` içerir: *NorthwindDataSet.Dataset.Designer.vb* (veya *NorthwindDataSet.Dataset.Designer.cs*).

> [!NOTE]
> Veri kümelerini ve TableAdapter'ları ayırarak **(DataSet Project** özelliğini ayarerek), projede mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

## <a name="create-a-new-service-application"></a>Yeni Hizmet Uygulaması Oluşturma
Bu kılavuz bir WCF hizmeti kullanarak veri erişim katmanına nasıl erişeceklerini gösterdiği için yeni bir WCF hizmet uygulaması oluşturacağız.

### <a name="to-create-a-new-wcf-service-application"></a>Yeni bir WCF Hizmeti uygulaması oluşturmak için

1. içinde çözüme sağ tıklayın ve **Çözüm Gezgini** **Ekle'yi**  >  **Project.**

2. Yeni **Project** iletişim kutusunda, sol bölmede **WCF'yi seçin.** Orta bölmede **WCF Hizmet Kitaplığı'ı seçin.**

3. Projeyi **DataService olarak adlandır ve** Tamam'ı **seçin.**

     DataService projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Müşterileri ve sipariş verilerini iade etmek için veri erişim katmanında yöntemler oluşturma
Veri hizmetinin veri erişim katmanında iki yöntem çağırsı gerekir: `GetCustomers` ve `GetOrders` . Bu yöntemler Northwind ve `Customers` tablolarını `Orders` geri döner. Projede `GetCustomers` ve `GetOrders` yöntemlerini `DataAccessTier` oluşturun.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Veri erişim katmanında Customers tablosunu döndüren bir yöntem oluşturmak için

1. Bu **Çözüm Gezgini,** **NorthwindDataset.xsd'ye çift** tıklar ve veri kümesine tıklayın.

2. **CustomersTableAdapter'a sağ tıklayın ve** Sorgu **Ekle'ye tıklayın.**

3. Komut **Türü Seçin sayfasında, Varsayılan** Use **SQL deyimini** bırakın ve Ardından'ya **tıklayın.**

4. Sorgu **Türü Seçin sayfasında satırları döndüren** varsayılan SELECT değerini bırakın **ve Sonraki** 'ye **tıklayın.**

5. Select **deyimini SQL sayfasında** varsayılan sorguyu bırakın ve Sonraki 'ye **tıklayın.**

6. Oluşturulecek **Yöntemleri Seçin sayfasında,** **DataTable** İadesi bölümünde Yöntem adı **olarak** **GetCustomers** yazın.

7. **Finish (Son)** düğmesine tıklayın.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Veri erişim katmanında Orders tablosunu döndüren bir yöntem oluşturmak için

1. **OrdersTableAdapter'a sağ tıklayın ve** Sorgu **Ekle'ye tıklayın.**

2. Komut **Türü Seçin sayfasında, Varsayılan** Use **SQL deyimini** bırakın ve Ardından'ya **tıklayın.**

3. Sorgu **Türü Seçin sayfasında satırları döndüren** varsayılan SELECT değerini bırakın **ve Sonraki** 'ye **tıklayın.**

4. Select **deyimini SQL sayfasında** varsayılan sorguyu bırakın ve Sonraki 'ye **tıklayın.**

5. Oluşturulecek **Yöntemleri Seçin sayfasında,** DataTable İadesi bölümünde Yöntem adı **için** **GetOrders** yazın. 

6. **Finish (Son)** düğmesine tıklayın.

7. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Veri hizmetine veri varlığı ve veri erişim katmanlarına başvuru ekleme
Veri hizmeti veri kümesinden ve TableAdapter'lardan bilgi gerektirdiğinden **DataEntityTier** ve **DataAccessTier projelerine başvurular** ekleyin.

### <a name="to-add-references-to-the-data-service"></a>Veri hizmetine başvuru eklemek için

1. **Çözüm Gezgini'de DataService'e** **sağ tıklayın ve** Başvuru **Ekle'ye tıklayın.**

2. Başvuru **Ekle** iletişim kutusundaki **Projeler sekmesine** tıklayın.

3. **DataAccessTier ve** **DataEntityTier projelerini seçin.**

4. **Tamam**'a tıklayın.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Veri erişim katmanında GetCustomers ve GetOrders yöntemlerini çağıran işlevler ekleme
Şimdi veri erişim katmanında veri döndürme yöntemleri bulunduğuna göre, veri erişim katmanındaki yöntemleri çağırmak için veri hizmetinde yöntemler oluşturun.

> [!NOTE]
> C# projelerinde aşağıdaki kodu derlemek için `System.Data.DataSetExtensions` derlemesine bir başvuru eklemeniz gerekir.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Veri hizmetinde GetCustomers ve GetOrders işlevlerini oluşturmak için

1. **DataService projesinde IService1.vb** veya **IService1.cs'ye çift tıklayın.** 

2. Hizmet işlemlerinizi buraya ekleyin **açıklamasına aşağıdaki kodu** ekleyin:

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

3. DataService projesinde **Service1.vb** 'ye (veya **Service1.cs) çift tıklayın.**

4. Service1 sınıfına **aşağıdaki kodu** ekleyin:

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

5. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Veri hizmetlerinden verileri görüntülemek için sunu katmanı oluşturma
Çözüm, veri erişim katmanına çağrıda bulunan yöntemleri olan veri hizmetini içerdiğine göre, veri hizmetine çağrıda bulunan ve verileri kullanıcılara sunan başka bir proje oluşturun. Bu kılavuz için bir Windows Forms uygulaması oluşturun; bu n katmanlı uygulamanın sunu katmanıdır.

### <a name="to-create-the-presentation-tier-project"></a>Sunu katmanı projesi oluşturmak için

1. içinde çözüme sağ tıklayın ve **Çözüm Gezgini** **Ekle'yi**  >  **Project.**

2. Yeni **Project** iletişim kutusunda, sol bölmede Masaüstü'Windows **seçin.** Orta bölmede Formlar **Uygulaması'Windows seçin.**

3. Projeye **PresentationTier adını girin ve** Tamam'a **tıklayın.**

    PresentationTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>PresentationTier projesini başlangıç projesi olarak ayarlama
Veri sunan ve verilerle etkileşime geçen gerçek istemci uygulaması olduğundan **PresentationTier** projesini çözümün başlangıç projesi olarak ayarlayalım.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Yeni sunu katmanı projesini başlangıç projesi olarak ayarlamak için

- Içinde **Çözüm Gezgini,** **PresentationTier'a sağ tıklayın** ve Başlangıç Olarak **Ayarla'ya Project.**

## <a name="add-references-to-the-presentation-tier"></a>Sunu Katmanına Başvuru Ekleme
İstemci uygulaması PresentationTier, hizmetteki yöntemlere erişmek için veri hizmetine bir hizmet başvurusu gerektirir. Buna ek olarak, WCF hizmeti tür paylaşımını etkinleştirmek için veri kümesine bir başvuru gerektirir. Veri hizmeti aracılığıyla tür paylaşımını etkinleştirene kadar kısmi veri kümesi sınıfına eklenen kod sunu katmanında kullanılamaz. Genellikle bir veri tablosuna satıra doğrulama kodu ve sütun değiştirme olayları gibi kodlar eklersiniz. Bu koda büyük olasılıkla istemciden erişmek istemeniz gerekir.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Sunu katmanına bir başvuru eklemek için

1. Bu **Çözüm Gezgini** **PresentationTier'a sağ tıklayın ve** Başvuru **Ekle'yi seçin.**

2. Başvuru **Ekle iletişim** kutusunda Projeler **sekmesini** seçin.

3. **DataEntityTier'ı ve Tamam'ı** **seçin.**

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Sunu katmanına bir hizmet başvurusu eklemek için

1. Bu **Çözüm Gezgini** **PresentationTier'a sağ tıklayın ve** Hizmet Başvurusu Ekle. 

2. Yeni **Hizmet Başvurusu Ekle** kutusunda Keşfet'i **seçin.**

3. **Hizmet1'i ve** Tamam'ı **seçin.**

    > [!NOTE]
    > Geçerli bilgisayarda birden çok hizmetiniz varsa, bu kılavuzda daha önce oluşturduğunuz hizmeti (ve yöntemlerini içeren `GetCustomers` `GetOrders` hizmet) seçin.

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Veri hizmeti tarafından döndürülen verileri görüntülemek için forma DataGridViews ekleme
Hizmet başvurularını veri hizmetine eklemenizin ardından Veri Kaynakları **penceresi,** hizmet tarafından döndürülen verilerle otomatik olarak doldurulur.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Forma iki DataGridView veri bağlama öğesi eklemek için

1. Bu **Çözüm Gezgini** **PresentationTier projesini** seçin.

2. Veri Kaynakları penceresinde **NorthwindDataSet'i genişletin** ve **Müşteriler düğümünü** bulun. 

3. Müşteriler **düğümünü** Form1'e sürükleyin.

4. Veri **Kaynakları penceresinde** Müşteriler düğümünü **genişletin** ve ilgili **Siparişler düğümünü** **(Müşteriler** düğümünde iç içe geçmiş **Siparişler düğümü)** bulun.

5. İlgili Orders **düğümünü** Form1'e sürükleyin.

6. Formda boş bir alanı çift tıklayarak bir `Form1_Load` olay işleyicisi oluşturun.

7. Olay işleyiciye aşağıdaki `Form1_Load` kodu ekleyin.

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

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Hizmet tarafından izin verilen en büyük ileti boyutunu artırma
için varsayılan `maxReceivedMessageSize` değer, ve tablolarından alınan verileri tutacak kadar `Customers` büyük `Orders` değildir. Aşağıdaki adımlarda değeri 6553600 olarak artıracağız. İstemcideki değeri değiştirirsiniz ve bu da hizmet başvurularını otomatik olarak ler.

> [!NOTE]
> Varsayılan alt sınır boyutu hizmet reddi (DoS) saldırılarına maruz kalmayı sınırlamak içindir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>MaxReceivedMessageSize değerini artırmak için

1. Bu **Çözüm Gezgini,** **PresentationTier** **projesindeapp.config** dosyasına çift tıklayın.

2. **maxReceivedMessage size** özniteliğini bulun ve değerini olarak `6553600` değiştirme.

## <a name="test-the-application"></a>Uygulamayı test edin
F5 tuşuna basarak **uygulamayı çalıştırın.** ve `Customers` tablolarından `Orders` alınan veriler veri hizmetten alınır ve formda görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar
Uygulama gereksinimlerinize bağlı olarak, Windows tabanlı bir uygulama içinde ilgili verileri kaydettikten sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Örneğin, bu uygulamada aşağıdaki geliştirmeleri yapabilirsiniz:

- Veri kümesine doğrulama ekleme.

- Verileri tekrar veritabanında güncelleştirmek için hizmete ek yöntemler ekleme.

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı uygulamalarda veri kümeleriyle çalışma](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
