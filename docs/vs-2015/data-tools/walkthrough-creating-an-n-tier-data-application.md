---
title: 'İzlenecek yol: N katmanlı veri uygulaması oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 195a3a36b53e5f84f6052a15e01007bb5ed77fac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844197"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>İzlenecek Yol: N Katmanlı Bir Veri Uygulaması Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N katmanlı * veri uygulamaları, verilere erişen ve birden çok mantıksal *katmana veya katmana*ayrılan uygulamalardır. Uygulama bileşenlerini farklı katmanlara ayırmak uygulamanızın yönetilebilirliğini ve ölçeklenebilirliğini artırır. Bunu, tüm çözümü yeniden tasarlamanıza gerek kalmadan tek bir katmana uygulanabilen yeni teknolojilerin daha kolay benimsenmesini sağlayarak yapar. N katmanlı mimaride bir sunu katmanı, bir orta katman ve bir veri katmanı bulunur. Orta katmanda genellikle bir veri erişim katmanı, iş mantığı katmanı ve kimlik doğrulaması ve doğrulama gibi paylaşılan bileşenler bulunur. Veri katmanında ilişkisel bir veritabanı vardır. N katmanlı uygulamalar hassas bilgileri orta katmanın veri erişimi katmanında depolayarak sunu katmanına erişimi olan son kullanıcılardan uzakta tutulmasını sağlar. Daha fazla bilgi için bkz. [N katmanlı veri uygulamalarına genel bakış](../data-tools/n-tier-data-applications-overview.md).

 N katmanlı uygulamada çeşitli katmanları ayırma yollarından biri, uygulamanıza eklemek istediğiniz her katman için ayrı projeler oluşturmaktır. Türü belirtilmiş veri kümelerinde, üretilen veri kümesinin ve `DataSet Project` kodunun gitmesi gereken projeleri belirleyen bir `TableAdapter` özelliği bulunur.

 Bu izlenecek yol `TableAdapter` , **veri kümesi Tasarımcısı**kullanarak veri kümesini ve kodu ayrık sınıf kitaplığı projelerine nasıl ayırabileceğinizi gösterir. Veri kümesini ve TableAdapter kodunu ayırdıktan sonra, veri erişim katmanına çağırmak için [Visual Studio hizmetinde bir Windows Communication Foundation Hizmetleri ve WCF veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) oluşturacaksınız. Son olarak, sunu katmanı olarak bir Windows Forms uygulaması oluşturacaksınız. Bu katman veri hizmetindeki verilere erişir.

 Bu kılavuzda aşağıdaki adımları gerçekleştireceksiniz:

- Birden fazla proje içeren yeni bir n katmanlı çözüm oluşturma.

- N katmanlı çözüme iki sınıf kitaplığı ekleme.

- **Veri kaynağı Yapılandırma Sihirbazı 'nı**kullanarak türü belirtilmiş bir veri kümesi oluşturun.

- Oluşturulan [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) ve dataset kodunu ayrık projelere ayırın.

- Veri erişim katmanına çağrı göndermek için bir Windows Communication Foundation (WCF) hizmeti oluşturma.

- Veri erişim katmanından veri almak için hizmet içinde işlevler oluşturma.

- Sunu katmanı olarak hizmet verecek bir Windows Forms uygulaması oluşturma.

- Veri kaynağına bağlanan Windows Forms denetimleri oluşturma.

- Veri tablolarını doldurmak için kod yazma.

  ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz. [video nasıl yapılır: N katmanlı veri uygulaması oluşturma](https://msdn2.microsoft.com/library/cc178916.aspx).

## <a name="prerequisites"></a>Önkoşullar
 Bu kılavuzu tamamlamak için gerekenler:

- Northwind örnek veritabanına erişim.

## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Veri Kümesini Tutacak N Katmanlı Çözüm ve Sınıf Kitaplığı Oluşturma (DataEntityTier)
 Bu kılavuzun ilk adımı bir çözüm ve iki sınıf kitaplığı projesi oluşturmaktır. Birinci sınıf kitaplığı veri kümesini tutacaktır (uygulama verilerini tutacak, üretilen türü belirtilmiş DataSet sınıfı ve DataTable tabloları). Bu proje uygulamanın veri varlık katmanı olarak kullanılır ve genellikle orta katmanda bulunur. Veri Kümesi Tasarımcısı, ilk veri kümesini oluşturmak ve kodu otomatik olarak iki sınıf kitaplığına ayırmak için kullanılır.

> [!NOTE]
> **Tamam**' a tıklamadan önce projeyi ve çözümü doğru şekilde girdiğinizden emin olun. Böylece bu kılavuzu tamamlamanız kolaylaşır.

#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>N katmanlı çözüm ve DataEntityTier sınıf kitaplığı oluşturmak için

1. **Dosya** menüsünden Yeni bir proje oluşturun.

    > [!NOTE]
    > **Veri kümesi Tasarımcısı** [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ve C# projelerinde desteklenir. Yeni projeyi bu dillerden birinde oluşturun.

2. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows**' a tıklayın.

3. **Sınıf kitaplığı** şablonuna tıklayın.

4. Projeyi **DataEntityTier**olarak adlandırın.

5. Çözüm **NTierWalkthrough**olarak adlandırın.

6. **Tamam**’a tıklayın.

     DataEntityTier projesini içeren bir NTierWalkthrough Çözümü oluşturulup **Çözüm Gezgini**eklenir.

## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>TableAdapter Bağdaştırıcılarını Tutacak Sınıf Kitaplığı Oluşturma (DataAccessTier)
 DataEntityTier projesini oluşturduktan sonraki adım başka bir sınıf kitaplığı projesi oluşturmaktır. Bu proje oluşturulan öğeleri tutacaktır `TableAdapter` ve uygulamanın *veri erişim katmanı* olarak adlandırılır. Veri erişim katmanında, veritabanına bağlanmak için gereken bilgiler bulunur ve genelde orta katmanda yer alır.

#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>TableAdapter bağdaştırıcılarına yönelik yeni sınıf kitaplığı oluşturmak için

1. **Dosya** menüsünde, NTierWalkthrough çözümüne yeni bir proje ekleyin.

2. **Yeni proje** iletişim kutusunda, **Şablonlar** bölmesinde, **sınıf kitaplığı**' na tıklayın.

3. Projeyi **DataAccessTier** olarak adlandırın ve **Tamam**' a tıklayın.

     DataAccessTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="creating-the-dataset"></a>Veri Kümesi Oluşturma
 Sonraki adım türü belirtilmiş bir veri kümesi oluşturmaktır. Türü belirtilmiş veri kümeleri, her iki veri kümesi sınıfıyla (DataTable sınıfları dahil) ve `TableAdapter` sınıflarıyla tek bir projede oluşturulur. (Tüm sınıflar tek bir dosyada oluşturulur.) Veri kümesini ve `TableAdapter` öğeleri farklı projelere ayırdığınızda, bu sınıf, özgün projedeki sınıfları bırakarak diğer projeye taşınan veri kümesi sınıfıdır `TableAdapter` . Bu nedenle, veri kümesini sonuçta `TableAdapter` bağdaştırıcılarını içerecek projede oluşturun (DataAccessTier projesi). **Veri kümesini veri kaynağı Yapılandırma Sihirbazı**' nı kullanarak oluşturacaksınız.

> [!NOTE]
> Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir.

#### <a name="to-create-the-dataset"></a>Veri kümesi oluşturma

1. **Çözüm Gezgini**'de DataAccessTier ' ye tıklayın.

2. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

3. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için **Yeni veri kaynağı Ekle** ' ye tıklayın.

4. **Veri kaynağı türü seç** sayfasında, **veritabanı** ' na ve ardından **İleri**' ye tıklayın.

5. **Veri bağlantınızı seçin** sayfasında, aşağıdaki eylemlerden birini gerçekleştirin:

     Northwind örnek veritabanıyla kurulan veri bağlantısı açılan listede kullanılabilir durumdaysa bu bağlantıya tıklayın.

     -veya-

     **Yeni bağlantı** ' ya tıklayarak **bağlantı ekle** iletişim kutusunu açın.

6. Veritabanı parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.

    > [!NOTE]
    > Bir yerel veritabanı dosyası (SQL Server'a bağlanmak yerine) seçtiyseniz projeye dosya eklemek isteyip istemediğiniz sorulabilir. Veritabanı dosyasını projeye eklemek için **Evet** ' e tıklayın.

7. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında **İleri** ' ye tıklayın.

8. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

9. **Müşteriler** ve **siparişler** tablolarının onay kutularına tıklayın ve ardından **son**' a tıklayın.

     NorthwindDataSet, DataAccessTier projesine eklenir ve **veri kaynakları** penceresinde görüntülenir.

## <a name="separating-the-tableadapters-from-the-dataset"></a>TableAdapter Bağdaştırıcılarını Veri Kümesinden Ayırma
 Veri kümesi oluşturduktan sonra, üretilen veri kümesi sınıfını TableAdapter bağdaştırıcılarından ayırın. Bunu, **veri kümesi proje** özelliğini, ayrılmış veri kümesi sınıfının depolayabileceği proje adına ayarlayarak yapabilirsiniz.

#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>TableAdapter Bağdaştırıcılarını Veri Kümesinden ayırmak için

1. **Veri kümesi Tasarımcısı**veri kümesini açmak Için **Çözüm Gezgini** **NorthwindDataSet. xsd** ' ye çift tıklayın.

2. Tasarımcı üzerinde boş bir alana tıklayın.

3. **Özellikler** penceresinde **veri kümesi proje** düğümünü bulun.

4. **Veri kümesi projesi** listesinde **DataEntityTier**' e tıklayın.

5. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

   Veri kümesi ve TableAdapter bağdaştırıcıları iki sınıf kitaplığı projesine ayrılır. Başlangıçta tüm veri kümesini (DataAccessTier) içeren projede şimdi yalnızca TableAdapter bağdaştırıcıları bulunur. **DataSet proje** özelliğinde (DataEntityTier) belirtilen proje türü belirtilmiş veri kümesini Içerir: NorthwindDataSet. DataSet. Designer. vb (veya NorthwindDataSet.DataSet.Designer.cs).

> [!NOTE]
> Veri kümelerini ve TableAdapters ayırabilirsiniz ( **veri kümesi proje** özelliğini ayarlayarak), projedeki mevcut kısmi veri kümesi sınıfları otomatik olarak taşınmaz. Mevcut veri kümesi kısmi sınıflarının veri kümesi projesine el ile taşınması gerekir.

## <a name="creating-a-new-service-application"></a>Yeni Hizmet Uygulaması Oluşturma
 Bu kılavuz bir WCF hizmetini kullanarak veri erişim katmanına nasıl erişileceğini gösterdiğinden yeni bir WCF hizmeti uygulaması oluşturun.

#### <a name="to-create-a-new-wcf-service-application"></a>Yeni bir WCF Hizmeti uygulaması oluşturmak için

1. **Dosya** menüsünde, NTierWalkthrough çözümüne yeni bir proje ekleyin.

2. **Yeni proje** Iletişim kutusundaki **Proje türleri** bölmesinde **WCF**' ye tıklayın. **Şablonlar** bölmesinde, **WCF hizmet kitaplığı**' na tıklayın.

3. Projeyi **DataService** olarak adlandırın ve **Tamam**' a tıklayın.

     DataService projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Müşteri ve Sipariş Verilerini Döndürmek İçin Veri Erişim Katmanında Yöntemler Oluşturma
 Veri hizmetinin veri erişim katmanında iki yöntem çağırması gerekir: GetCustomers ve GetOrders. Bu yöntemler Northwind Customers ve Orders tablolarını döndürür. DataAccessTier projesinde GetCustomers ve GetOrders yöntemlerini oluşturun.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Veri erişim katmanında Customers tablosunu döndüren bir yöntem oluşturmak için

1. **Çözüm Gezgini**, veri kümesi Tasarımcısı veri kümesini açmak için NorthwindDataSet. xsd ' ye çift tıklayın.

2. CustomersTableAdapter öğesine sağ tıklayın ve TableAdapter 'ı düzenlemek için **Sorgu Ekle** ' ye tıklayın.

3. **Bir komut türü seçin** sayfasında, varsayılan değer olan **SQL deyimlerini kullanın** ve **İleri**' ye tıklayın.

4. **Bir sorgu türü seçin** sayfasında, **satırları döndüren Seç** varsayılan değerini bırakın ve **İleri**' ye tıklayın.

5. **BIR SQL SELECT Ifadesini belirtin** sayfasında, varsayılan sorguyu bırakın ve **İleri**' ye tıklayın.

6. **Oluşturulacak yöntemleri seçin** sayfasında, **bir DataTable döndürün** bölümüne **Yöntem adı** için **GetCustomers** yazın.

7. **Son**'a tıklayın.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Veri erişim katmanında Orders tablosunu döndüren bir yöntem oluşturmak için

1. OrdersTableAdapter öğesine sağ tıklayın ve **Sorgu Ekle**' ye tıklayın.

2. **Bir komut türü seçin** sayfasında, varsayılan değer olan **SQL deyimlerini kullanın** ve **İleri**' ye tıklayın.

3. **Bir sorgu türü seçin** sayfasında, **satırları döndüren Seç** varsayılan değerini bırakın ve **İleri**' ye tıklayın.

4. **BIR SQL SELECT Ifadesini belirtin** sayfasında, varsayılan sorguyu bırakın ve **İleri**' ye tıklayın.

5. **Oluşturulacak yöntemleri seçin** sayfasında, **bir DataTable döndürün** bölümüne **Yöntem adı** için **GetOrders** yazın.

6. **Son**'a tıklayın.

7. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Veri Hizmetinin Veri Varlığı ve Veri Erişimi Katmanlarına Başvuru Ekleme
 Veri hizmetinin veri kümesinden ve TableAdapter bağdaştırıcılarından bilgi alması gerektiğinden DataEntityTier ve DataAccessTier projelerine başvurular ekleyin.

#### <a name="to-add-references-to-the-data-service"></a>Veri hizmetine başvuru eklemek için

1. **Çözüm Gezgini** veri hizmeti ' ne sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** Iletişim kutusunda **Projeler** sekmesine tıklayın.

3. Hem **DataAccessTier** hem de **DataEntityTier** projelerini seçin.

4. **Tamam**’a tıklayın.

## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Veri Erişim Katmanındaki GetCustomers ve GetOrder Yöntemlerini Çağırmak İçin Hizmete İşlev Ekleme
 Şimdi veri erişim katmanında veri döndürme yöntemleri bulunduğuna göre, veri erişim katmanındaki yöntemleri çağırmak için veri hizmetinde yöntemler oluşturun.

> [!NOTE]
> C# projelerinde aşağıdaki kodu derlemek için `System.Data.DataSetExtensions` derlemesine bir başvuru eklemeniz gerekir.

#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Veri hizmetinde GetCustomers ve GetOrders işlevlerini oluşturmak için

1. **DataService** projesinde IService1. vb veya IService1.cs öğesine çift tıklayın.

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

3. DataService projesinde Service1.vb (veya Service1.cs) öğesine çift tıklayın.

4. Aşağıdaki kodu Service1 sınıfına ekleyin:

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

## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Veri Hizmetinden Verileri Görüntülemek İçin Bir Sunu Katmanı Oluşturma
 Şimdi çözümde veri erişim katmanına çağrı gönderen yöntemler bulunduğuna göre, veri hizmetine çağrı gönderecek ve verileri kullanıcılara sunacak başka bir proje oluşturun. Bu kılavuz için bir Windows Forms uygulaması oluşturun; bu n katmanlı uygulamanın sunu katmanıdır.

#### <a name="to-create-the-presentation-tier-project"></a>Sunu katmanı projesi oluşturmak için

1. **Dosya** menüsünde, NTierWalkthrough çözümüne yeni bir proje ekleyin.

2. **Yeni proje** iletişim kutusunda, **Proje türleri** bölmesinde **Windows**' a tıklayın. **Şablonlar** bölmesinde **Windows Forms uygulama**' ya tıklayın.

3. Projeyi **PresentationTier** olarak adlandırın ve **Tamam**' a tıklayın.

4. PresentationTier projesi oluşturulur ve NTierWalkthrough çözümüne eklenir.

## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>PresentationTier Projesini Başlangıç Projesi Olarak Ayarlama
 Sunu katmanı verileri sunmak ve verilerle etkileşimde bulunmak için kullanılan gerçek istemci uygulaması olduğundan PresentationTier projesini Başlangıç projesi olarak ayarlamanız gerekir.

#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Yeni sunu katmanı projesini Başlangıç projesi olarak ayarlamak için

- **Çözüm Gezgini**, **PresentationTier** öğesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' ya tıklayın.

## <a name="adding-references-to-the-presentation-tier"></a>Sunu Katmanına Başvuru Ekleme
 PresentationTier istemci uygulaması, hizmetteki yöntemlere erişmek için veri hizmetine yönelik bir hizmet başvurusu gerektirir. Buna ek olarak, WCF hizmeti tür paylaşımını etkinleştirmek için veri kümesine bir başvuru gerektirir. Veri hizmeti aracılığıyla tür paylaşımı etkinleştirilinceye kadar kısmi veri kümesi sınıfına eklenen kod sunu katmanı tarafından kullanılamaz. Genelde veri tablosundaki satır ve sütun değişikliği olaylarını doğrulama gibi bir kod ekleyeceğiniz için büyük olasılıkla bu koda istemcisinden erişmek isteyeceksiniz.

#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Sunu katmanına bir başvuru eklemek için

1. **Çözüm Gezgini**, PresentationTier öğesine sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesine tıklayın.

3. **DataEntityTier** ' ı seçip **Tamam**' a tıklayın.

#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Sunu katmanına bir hizmet başvurusu eklemek için

1. **Çözüm Gezgini**, PresentationTier öğesine sağ tıklayın ve **hizmet başvurusu Ekle**' a tıklayın.

2. **Hizmet başvurusu Ekle** Iletişim kutusunda **bul**' a tıklayın.

3. **Service1** ve **Tamam**' ı seçin.

    > [!NOTE]
    > Geçerli bilgisayarda birden çok hizmetiniz varsa, bu kılavuzda önceden oluşturduğunuz hizmeti seçin (GetCustomers ve GetOrders yöntemlerini içeren hizmet).

## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Veri Hizmetinin Döndürdüğü Verileri Görüntülemek İçin Forma DataGridView Görünümleri Ekleme
 Hizmet başvurusunu veri hizmetine ekledikten sonra, **veri kaynakları** penceresi hizmet tarafından döndürülen verilerle otomatik olarak doldurulur.

#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Forma iki DataGridView veri bağlama öğesi eklemek için

1. **Çözüm Gezgini**, PresentationTier projesini seçin.

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

## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Hizmet Tarafından İzin Verilen En Büyük İleti Boyutunu Artırma
 Hizmet, Customers ve Orders tablolarından veri döndürdüğünden, maxReceivedMessageSize için varsayılan değer verileri tutabilecek kadar büyük değildir ve artırılması gerekir. Bu kılavuz için değeri 6553600 olarak değiştirin. İstemcideki değeri değişirin; bunu yaptığınızda hizmet başvurusu otomatik olarak güncelleştirilir.

> [!NOTE]
> Varsayılan alt sınır boyutu hizmet reddi (DoS) saldırılarına maruz kalmayı sınırlamak içindir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>MaxReceivedMessageSize değerini artırmak için

1. **Çözüm Gezgini**, PresentationTier projesindeki app.config dosyasına çift tıklayın.

2. **Maxreceived ileti** boyutu özniteliğini bulun ve değerini olarak değiştirin `6553600` .

## <a name="testing-the-application"></a>Uygulamayı Test Etme
 Uygulamayı çalıştırın. Veriler veri hizmetinden alınır ve formda görüntülenir.

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. F5 tuşuna basın.

2. Customers ve Orders tablolarındaki veriler veri hizmetinden alınır ve formda görüntülenir.

## <a name="next-steps"></a>Sonraki Adımlar
 Uygulama gereksinimlerinize bağlı olarak, Windows tabanlı bir uygulama içinde ilgili verileri kaydettikten sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Örneğin, bu uygulamada aşağıdaki geliştirmeleri yapabilirsiniz:

- Veri kümesine doğrulama ekleme. Bilgi için bkz. [Izlenecek yol: N katmanlı bir veri uygulamasına doğrulama ekleme](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).

- Verileri tekrar veritabanında güncelleştirmek için hizmete ek yöntemler ekleme.

## <a name="see-also"></a>Ayrıca Bkz.
 [N katmanlı uygulamalarda veri kümeleriyle çalışma](../data-tools/work-with-datasets-in-n-tier-applications.md) [Hiyerarşik güncelleştirme](../data-tools/hierarchical-update.md) [Visual Studio 'daki verilere erişme](../data-tools/accessing-data-in-visual-studio.md)
