---
title: 'adım adım kılavuz: N katmanlı veri uygulaması oluşturma'
description: Bu kılavuzda N katmanlı bir veri uygulaması oluşturun. N katmanlı veri uygulamaları, verilere erişen ve birçok mantıksal katmana veya katmana ayrılan uygulamalardır.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631047"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Adım adım kılavuz: N katmanlı veri uygulaması oluşturma
*N katmanlı veri* uygulamaları, verilere erişen ve birden çok mantıksal katmana veya katmana ayrılan *uygulamalardır.* Uygulama bileşenlerini farklı katmanlara ayırmak uygulamanızın yönetilebilirliğini ve ölçeklenebilirliğini artırır. Bunu, tüm çözümü yeniden tasarlamanıza gerek kalmadan tek bir katmana uygulanabilen yeni teknolojilerin daha kolay benimsenmesini sağlayarak yapar. N katmanlı mimaride bir sunu katmanı, bir orta katman ve bir veri katmanı bulunur. Orta katmanda genellikle bir veri erişim katmanı, iş mantığı katmanı ve kimlik doğrulaması ve doğrulama gibi paylaşılan bileşenler bulunur. Veri katmanında ilişkisel bir veritabanı vardır. N katmanlı uygulamalar hassas bilgileri orta katmanın veri erişimi katmanında depolayarak sunu katmanına erişimi olan son kullanıcılardan uzakta tutulmasını sağlar. Daha fazla bilgi için [bkz. N katmanlı veri uygulamalarına genel bakış.](../data-tools/n-tier-data-applications-overview.md)

N katmanlı uygulamada çeşitli katmanları ayırma yollarından biri, uygulamanıza eklemek istediğiniz her katman için ayrı projeler oluşturmaktır. Türü belirtilmiş veri kümelerinde, üretilen veri kümesinin ve `DataSet Project` kodunun gitmesi gereken projeleri belirleyen bir `TableAdapter` özelliği bulunur.

Bu kılavuzda, veri kümesi ve kodu ayrı sınıf kitaplığı projelerine ayırmak için `TableAdapter` Veri Kümesi Tasarımcısı.  Veri kümesi ve TableAdapter kodunu ayırarak, [veri erişim katmanına çağrı yapmak için Windows Communication Foundation Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) WCF Veri Hizmetleri ve Visual Studio hizmette bir Visual Studio hizmeti oluşturun. Son olarak, sunum Windows form uygulaması olarak bir form uygulaması oluştururuz. Bu katman veri hizmetindeki verilere erişir.

Bu kılavuz sırasında aşağıdaki adımları gerçekleştirebilirsiniz:

- Birden çok proje içeren yeni bir n katmanlı çözüm oluşturun.

- N katmanlı çözüme iki sınıf kitaplığı ekleme.

- Veri Kaynağı Yapılandırma Sihirbazı'nı kullanarak **türe bağlı bir veri kümesi oluşturun.**

- Oluşturulan [TableAdapter'ları](create-and-configure-tableadapters.md) ve veri kümesi kodunu ayrı projelere ayırma.

- Veri erişim katmanına çağrı göndermek için bir Windows Communication Foundation (WCF) hizmeti oluşturma.

- Veri erişim katmanından veri almak için hizmet içinde işlevler oluşturma.

- Sunu katmanı olarak hizmet verecek bir Windows Forms uygulaması oluşturma.

- Veri kaynağına bağlanan Windows Forms denetimleri oluşturma.

- Veri tablolarını doldurmak için kod yazma.

![video bağlantısı ](../data-tools/media/playvideo.gif) Bu konunun video sürümü için bkz. Video [Nasıl: N katmanlı veri uygulaması oluşturma.](/previous-versions/visualstudio/visual-studio-2008/cc178916(v=vs.90))

## <a name="prerequisites"></a>Önkoşullar
Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. YerelDB'yi SQL Server Express yükleme sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Bu **Visual Studio Yükleyicisi**, **.NET** masaüstü SQL Server Express iş yükünün parçası olarak veya tek bir bileşen olarak YerelDB'yi yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (**SQL Server Nesne Gezgini,** veri depolama ve işleme iş **yükünün bir parçası olarak** Visual Studio Yükleyicisi.) SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Veri kümesi (DataEntityTier) için n katmanlı çözüm ve sınıf kitaplığı oluşturma
Bu kılavuzun ilk adımı bir çözüm ve iki sınıf kitaplığı projesi oluşturmaktır. Birinci sınıf kitaplığı veri kümesi (oluşturulan türü oluşturulan sınıf ve uygulamanın verilerini `DataSet` tutan DataTable'lar) içerir. Bu proje uygulamanın veri varlık katmanı olarak kullanılır ve genellikle orta katmanda bulunur. Veri kümesi ilk veri kümesi oluşturur ve kodu otomatik olarak iki sınıf kitaplığına ayıracaktır.

> [!NOTE]
> Tamam'a tıklamadan önce projeyi ve çözümü doğru şekilde addan emin **olun.** Böylece bu kılavuzu tamamlamanız kolaylaşır.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>N katmanlı çözüm ve DataEntityTier sınıf kitaplığı oluşturmak için

1. Yeni Visual Studio'nin Dosya **menüsünde Yeni**   >  **dosya'Project.**

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve masaüstüne **Windows seçin.**

3. Orta bölmede Sınıf Kitaplığı **proje türünü** seçin.

4. Projeye **DataEntityTier adını girin.**

5. Çözüme **NTierWalkthrough adını ve** ardından Tamam'ı **seçin.**

     DataEntityTier projesini içeren bir NTierWalkthrough çözümü oluşturulur ve **Çözüm Gezgini.**

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>TableAdapter'ları tutmak için sınıf kitaplığı oluşturma (DataAccessTier)
DataEntityTier projesini oluşturduktan sonraki adım başka bir sınıf kitaplığı projesi oluşturmaktır. Bu proje, oluşturulan TableAdapter'ları tutar ve *uygulamanın veri erişim* katmanı olarak çağrılır. Veri erişim katmanında, veritabanına bağlanmak için gereken bilgiler bulunur ve genelde orta katmanda yer alır.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>TableAdapter'lar için ayrı bir sınıf kitaplığı oluşturmak için

1. içinde çözüme sağ tıklayın ve **Çözüm Gezgini** **Ekle'yi**  >  **Project.**

2. Yeni **Project** iletişim kutusunda, orta bölmede Sınıf Kitaplığı'ı **seçin.**

3. Projeye **DataAccessTier adını girin ve** Tamam'ı **seçin.**

     DataAccessTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="create-the-dataset"></a>Veri Kümesi oluşturma
Sonraki adım türü belirtilmiş bir veri kümesi oluşturmaktır. Türü oluşturulan veri kümeleri hem veri kümesi sınıfıyla (sınıflar dahil) hem de `DataTables` tek bir proje içinde sınıflar ile `TableAdapter` oluşturulur. (Tüm sınıflar tek bir dosyada oluşturulur.) Veri kümesi ve TableAdapter'ları farklı projelere ayırarak diğer projeye taşınan veri kümesi sınıfıdır ve sınıflar özgün `TableAdapter` projede bırakılmaktadır. Bu nedenle, sonunda TableAdapter'ları (DataAccessTier projesi) içeren projede veri kümesi oluşturun. Veri kümesi oluşturmak için Veri Kaynağı Yapılandırma **Sihirbazı'nı kullanırsınız.**

> [!NOTE]
> Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [Nasıl kullanılır: Örnek veritabanlarını yükleme.](../data-tools/installing-database-systems-tools-and-samples.md)

### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma

1. içinde **DataAccessTier'ı** **Çözüm Gezgini.**

2. Veri menüsünde **Veri** Kaynaklarını **Göster'i seçin.**

   Veri **Kaynakları** penceresi açılır.

3. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'yi seçerek** Veri Kaynağı **Yapılandırma Sihirbazı'nı başlatın.**

4. Veri Kaynağı **Türü Seçin sayfasında Veritabanı'ı** ve **ardından Sonraki'yi** **seçin.**

5. Veri **Bağlantınızı Seçin sayfasında** aşağıdaki eylemlerden birini gerçekleştirin:

     Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

     -veya-

     Bağlantı **Ekle iletişim** kutusunu açmak için Yeni **Bağlantı'ya** tıklayın.

6. Veritabanı bir parola gerektiriyorsa, hassas verileri dahil etmek için seçeneğini belirtin ve ardından Sonraki'yi **seçin.**

    > [!NOTE]
    > Bir yerel veritabanı dosyası (SQL Server'a bağlanmak yerine) seçtiyseniz projeye dosya eklemek isteyip istemediğiniz sorulabilir. Veritabanı **dosyasını** projeye eklemek için Evet'i seçin.

7. Bağlantı **Dizesini** **Uygulama Yapılandırma Dosyasına Kaydet sayfasından Sonraki'yi** seçin.

8. Veritabanı **Nesnelerinizi** Seçin sayfasında **Tablolar düğümünü** genişletin.

9. Customers ve Orders tablolarına **onay kutularını** **ve** ardından Son'a **seçin.**

     NorthwindDataSet DataAccessTier projesine eklenir ve Veri Kaynakları **penceresinde** görünür.

## <a name="separate-the-tableadapters-from-the-dataset"></a>TableAdapter'ları Veri Kümesinden ayırma
Veri kümesi oluşturduktan sonra, üretilen veri kümesi sınıfını TableAdapter bağdaştırıcılarından ayırın. Bunu yapmak için **DataSet Project** özelliğini, ayrılmış veri kümesi sınıfını depolandırarak projenin adına ayarlarsanız.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>TableAdapter Bağdaştırıcılarını Veri Kümesinden ayırmak için

1. veri kümesinde açmak için Çözüm Gezgini'de  **NorthwindDataSet.xsd'ye** **çift Veri Kümesi Tasarımcısı.**

2. Tasarımcıda boş bir alan seçin.

3. Özellikler penceresinde **DataSet Project** **düğümünü** bulun.

4. **DataSet Project** **DataEntityTier öğesini seçin.**

5. Derleme menüsünde **Çözümü** **Derleme'yi seçin.**

   Veri kümesi ve TableAdapter bağdaştırıcıları iki sınıf kitaplığı projesine ayrılır. Başlangıçta tüm veri kümesini () içeren proje `DataAccessTier` artık yalnızca TableAdapters içerir. **dataset Project** property () içinde belirtilen proje `DataEntityTier` türü belirtilmiş veri kümesini içerir: *NorthwindDataSet. dataset. designer. vb* (veya *NorthwindDataSet. dataset. designer. cs*).

> [!NOTE]
> veri kümelerini ve TableAdapters ayırabilirsiniz ( **dataset Project** özelliğini ayarlayarak), projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

## <a name="create-a-new-service-application"></a>Yeni bir hizmet uygulaması oluştur
Bu kılavuzda, bir WCF hizmeti kullanılarak veri erişim katmanına nasıl erişebileceğiniz gösterilmektedir, bu nedenle yeni bir WCF hizmeti uygulaması oluşturalım.

### <a name="to-create-a-new-wcf-service-application"></a>Yeni bir WCF Hizmeti uygulaması oluşturmak için

1. **Çözüm Gezgini** çözüme sağ tıklayın ve   >  **yeni Project** ekle ' yi seçin.

2. **yeni Project** iletişim kutusunda, sol taraftaki bölmede, **WCF**' yi seçin. Orta bölmede, **WCF hizmet kitaplığı**' nı seçin.

3. Proje **veri hizmetini** adlandırın ve **Tamam**' ı seçin.

     DataService projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Müşteriler ve siparişler verilerini döndürmek için veri erişim katmanında Yöntemler oluşturun
Veri hizmeti, veri erişim katmanında iki yöntemi çağırmalıdır: `GetCustomers` ve `GetOrders` . Bu yöntemler, Northwind `Customers` ve `Orders` tabloları döndürür. `GetCustomers`Ve `GetOrders` yöntemlerini `DataAccessTier` projede oluşturun.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Veri erişim katmanında Customers tablosunu döndüren bir yöntem oluşturmak için

1. **Çözüm Gezgini**' de, veri kümesini açmak için **NorthwindDataSet. xsd** ' ye çift tıklayın.

2. **CustomersTableAdapter** öğesine sağ tıklayın ve **Sorgu Ekle**' ye tıklayın.

3. **bir komut türü seçin** sayfasında, **Use SQL deyimlerinin** varsayılan değerini bırakın ve **ileri**' ye tıklayın.

4. **Bir sorgu türü seçin** sayfasında, **satırları döndüren Seç** varsayılan değerini bırakın ve **İleri**' ye tıklayın.

5. **SQL bir select ifadesini belirtin** sayfasında, varsayılan sorguyu bırakın ve **ileri**' ye tıklayın.

6. **Oluşturulacak yöntemleri seçin** sayfasında, **bir DataTable döndürün** bölümüne **Yöntem adı** için **GetCustomers** yazın.

7. **Finish (Son)** düğmesine tıklayın.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Veri erişim katmanında Orders tablosunu döndüren bir yöntem oluşturmak için

1. **OrdersTableAdapter** öğesine sağ tıklayın ve **Sorgu Ekle**' ye tıklayın.

2. **bir komut türü seçin** sayfasında, **Use SQL deyimlerinin** varsayılan değerini bırakın ve **ileri**' ye tıklayın.

3. **Bir sorgu türü seçin** sayfasında, **satırları döndüren Seç** varsayılan değerini bırakın ve **İleri**' ye tıklayın.

4. **SQL bir select ifadesini belirtin** sayfasında, varsayılan sorguyu bırakın ve **ileri**' ye tıklayın.

5. **Oluşturulacak yöntemleri seçin** sayfasında, **bir DataTable döndürün** bölümüne **Yöntem adı** için **GetOrders** yazın.

6. **Finish (Son)** düğmesine tıklayın.

7. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

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

1. **DataService** projesinde **IService1. vb** veya **IService1. cs**' ye çift tıklayın.

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

3. DataService projesinde **Service1. vb** (veya **Service1. cs**) öğesine çift tıklayın.

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

5. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Veri hizmetinden verileri göstermek için bir sunum katmanı oluşturma
Artık çözüm, veri erişim katmanına çağrı yapan yöntemlere sahip veri hizmetini içerdiğinden, veri hizmetine çağıran ve verileri kullanıcılara sunan başka bir proje oluşturun. Bu kılavuz için bir Windows Forms uygulaması oluşturun; bu n katmanlı uygulamanın sunu katmanıdır.

### <a name="to-create-the-presentation-tier-project"></a>Sunu katmanı projesi oluşturmak için

1. **Çözüm Gezgini** çözüme sağ tıklayın ve   >  **yeni Project** ekle ' yi seçin.

2. **yeni Project** iletişim kutusunda, sol taraftaki bölmede **masaüstü Windows**' ni seçin. orta bölmede **Windows Forms uygulama**' yı seçin.

3. Projeyi **PresentationTier** olarak adlandırın ve **Tamam**' a tıklayın.

    PresentationTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>PresentationTier projesini başlangıç projesi olarak ayarla
Verileri sunan ve bunlarla etkileşime girdiği gerçek istemci uygulaması olduğundan, **PresentationTier** projesini çözümün başlangıç projesi olarak ayarlayacağız.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Yeni sunum katmanı projesini başlangıç projesi olarak ayarlamak için

- **Çözüm Gezgini**, **PresentationTier** öğesine sağ tıklayın ve **Başlangıç Project olarak ayarla**' ya tıklayın.

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
    > Geçerli bilgisayarda birden fazla hizmetiniz varsa, bu kılavuzda daha önce oluşturduğunuz hizmeti ( `GetCustomers` ve yöntemlerini içeren hizmeti `GetOrders` ) seçin.

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Veri hizmeti tarafından döndürülen verileri göstermek için forma DataGrid görünümleri ekleyin
Hizmet başvurusunu veri hizmetine ekledikten sonra, **veri kaynakları** penceresi hizmet tarafından döndürülen verilerle otomatik olarak doldurulur.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Forma iki DataGridView veri bağlama öğesi eklemek için

1. **Çözüm Gezgini**, **PresentationTier** projesini seçin.

2. **Veri kaynakları** penceresinde, **NorthwindDataSet** ' i genişletin ve **müşteriler** düğümünü bulun.

3. **Müşteriler** düğümünü Form1 üzerine sürükleyin.

4. **Veri kaynakları** penceresinde, **müşteriler** düğümünü genişletin ve ilgili **siparişler** düğümünü bulun ( **müşteriler** düğümünde iç içe geçmiş **siparişler** düğümü).

5. İlişkili **siparişler** düğümünü Form1 üzerine sürükleyin.

6. Formda boş bir alanı çift tıklayarak bir `Form1_Load` olay işleyicisi oluşturun.

7. Olay işleyicisine aşağıdaki kodu ekleyin `Form1_Load` .

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
İçin varsayılan değer `maxReceivedMessageSize` , ve tablolarından alınan verileri tutabilecek kadar büyük değildir `Customers` `Orders` . Aşağıdaki adımlarda değeri 6553600 olarak artıracaksınız. İstemci üzerinde, hizmet başvurusunu otomatik olarak güncelleştiren değeri değiştirirsiniz.

> [!NOTE]
> Varsayılan alt sınır boyutu hizmet reddi (DoS) saldırılarına maruz kalmayı sınırlamak içindir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>MaxReceivedMessageSize değerini artırmak için

1. **Çözüm Gezgini**, **presentationtier** projesindeki **app.config** dosyasına çift tıklayın.

2. **Maxreceived ileti** boyutu özniteliğini bulun ve değerini olarak değiştirin `6553600` .

## <a name="test-the-application"></a>Uygulamayı test edin
**F5** tuşuna basarak uygulamayı çalıştırın. Ve tablolarından alınan veriler `Customers` `Orders` veri hizmetinden alınır ve formda görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar
Uygulama gereksinimlerinize bağlı olarak, Windows tabanlı bir uygulama içinde ilgili verileri kaydettikten sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Örneğin, bu uygulamada aşağıdaki geliştirmeleri yapabilirsiniz:

- Veri kümesine doğrulama ekleme.

- Verileri tekrar veritabanında güncelleştirmek için hizmete ek yöntemler ekleme.

## <a name="see-also"></a>Ayrıca bkz.

- [N katmanlı uygulamalarda veri kümeleriyle çalışma](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md)
- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
