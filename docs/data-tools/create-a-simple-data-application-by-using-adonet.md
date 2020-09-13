---
title: ADO.NET kullanarak basit veri uygulaması oluşturma
ms.custom: SEO-VS-2020
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c7db4d0072f217604e7ca163e581cc8fe138ffdb
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037438"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET kullanarak basit veri uygulaması oluşturma

Veritabanındaki verileri işleyen bir uygulama oluşturduğunuzda, bağlantı dizelerini tanımlama, veri ekleme ve saklı yordamları çalıştırma gibi temel görevleri gerçekleştirirsiniz. Bu konuyu izleyerek, Visual C# veya Visual Basic ve ADO.NET kullanarak basit bir Windows Forms "veri üzerinden Forms" uygulamasının içinden bir veritabanıyla nasıl etkileşim kuracağınızı bulabilirsiniz.  Veri kümeleri, LINQ to SQL ve Entity Framework dahil olmak üzere tüm .NET veri teknolojileri, sonuçta bu makalede gösterilenler için çok benzeyen adımları gerçekleştirir.

Bu makalede, verileri bir veritabanından hızlı bir şekilde almanın basit bir yolu gösterilmektedir. Uygulamanızın verileri basit olmayan yollarla değiştirmesi ve veritabanını güncelleştirmesi gerekiyorsa, Kullanıcı arabirimi denetimlerini temel verilerdeki değişikliklerle otomatik olarak eşitlemek için Entity Framework kullanmayı ve veri bağlamayı kullanmayı göz önünde bulundurmanız gerekir.

> [!IMPORTANT]
> Kodu basit tutmak için üretime hazırlanma özel durum işleme içermez.

## <a name="prerequisites"></a>Ön koşullar

Uygulamayı oluşturmak için şunlar gerekir:

- Visual Studio.

- SQL Server Express LocalDB. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)yükleyebilirsiniz.

Bu konu başlığı altında, Visual Studio IDE 'nin temel işlevleriyle ilgili bilgi sahibi olduğunuz ve bir Windows Forms uygulaması oluşturabileceğiniz, projeye form ekleyebileceğiniz, düğmeleri ve diğer denetimleri formlara ekleyebileceğiniz, denetimlerin özelliklerini ayarlayabildiğiniz ve basit olaylar kodlarınızın olduğu varsayılmaktadır. Bu görevlerle ilgili deneyimli değilseniz, bu yönergeyi başlamadan önce [Visual C# ve Visual Basic ile çalışmaya](../ide/quickstart-visual-basic-console.md) başlama konusunu tamamlamanızı öneririz.

## <a name="set-up-the-sample-database"></a>Örnek veritabanını ayarlama

Aşağıdaki adımları izleyerek örnek veritabanını oluşturun:

1. Visual Studio 'da **Sunucu Gezgini** penceresini açın.

2. **Veri bağlantıları** ' na sağ tıklayın ve **Yeni SQL Server veritabanı oluştur**' u seçin.

3. **Sunucu adı** metin kutusuna **(LocalDB) \mssqllocaldb**yazın.

4. **Yeni veritabanı adı** metin kutusunda **Sales**yazın ve ardından **Tamam**' ı seçin.

     Boş **Satış** veritabanı oluşturulur ve Sunucu Gezgini veri bağlantıları düğümüne eklenir.

5. **Satış** verileri bağlantısına sağ tıklayın ve **Yeni sorgu**' yı seçin.

     Sorgu Düzenleyicisi penceresi açılır.

6. [Sales Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) panonuza kopyalayın.

7. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

     Kısa bir süre sonra sorgu çalışmayı sonlandırır ve veritabanı nesneleri oluşturulur. Veritabanı iki tablo içerir: müşteri ve siparişler. Bu tablolar başlangıçta veri içermez, ancak oluşturacağınız uygulamayı çalıştırdığınızda veri ekleyebilirsiniz. Veritabanı ayrıca dört basit saklı yordam içerir.

## <a name="create-the-forms-and-add-controls"></a>Formları oluşturma ve denetimleri ekleme

1. Windows Forms bir uygulama için bir proje oluşturun ve bunu **Simpledataapp**olarak adlandırın.

    Visual Studio, **Form1**adlı boş bir Windows formu dahil olmak üzere projeyi ve birkaç dosyayı oluşturur.

2. Projenize üç form olması için iki Windows formu ekleyin ve ardından aşağıdaki adları verin:

   - **Gezinti**

   - **NewCustomer**

   - **FillOrCancel**

3. Her form için aşağıdaki çizimlerde görüntülenen metin kutularını, düğmeleri ve diğer denetimleri ekleyin. Her denetim için, tabloların açıkladığı özellikleri ayarlayın.

   > [!NOTE]
   > Grup kutusu ve etiket denetimleri ekler, ancak kodda kullanılmaz.

   **Gezinti formu**

   ![Gezinti iletişim kutusu](../data-tools/media/simpleappnav.png)

|Gezinti formu için denetimler|Özellikler|
| - |----------------|
|Düğme|Ad = Btnsayfayadd|
|Düğme|Ad = Btnsayfayfillorcancel|
|Düğme|Ad = btnExit|

**NewCustomer formu**

![Yeni müşteri ekleme ve sipariş yerleştirme](../data-tools/media/simpleappnewcust.png)

|NewCustomer formu için denetimler|Özellikler|
| - |----------------|
|TextBox|Ad = txtCustomerName|
|TextBox|Ad = Txtcustomerıd<br /><br /> ReadOnly = true|
|Düğme|Ad = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maksimum = 5000<br /><br /> Ad = numOrderAmount|
|'A|Format = Short<br /><br /> Ad = dtpOrderDate|
|Düğme|Ad = btnPlaceOrder|
|Düğme|Ad = btnAddAnotherAccount|
|Düğme|Ad = btnaddbitiri|

**FillOrCancel formu**

![siparişleri doldur veya iptal etme](../data-tools/media/simpleappcancelfill.png)

|FillOrCancel formu için denetimler|Özellikler|
| - |----------------|
|TextBox|Ad = txtOrderID|
|Düğme|Ad = Btnfindbyorderıd|
|'A|Format = Short<br /><br /> Ad = dtpFillDate|
|DataGridView|Ad = dgvCustomerOrders<br /><br /> ReadOnly = true<br /><br /> RowHeadersVisible = false|
|Düğme|Ad = btnCancelOrder|
|Düğme|Ad = btnFillOrder|
|Düğme|Ad = Btnsonlandırsupdates|

## <a name="store-the-connection-string"></a>Bağlantı dizesini depolayın
Uygulamanız veritabanına bir bağlantı açmaya çalıştığında, uygulamanızın bağlantı dizesine erişimi olması gerekir. Dizeyi her bir forma el ile girmekten kaçınmak için, dizeyi projenizdeki *App.config* dosyasına depolayın ve yöntemi uygulamanızdaki herhangi bir formdan çağrıldığında dizeyi döndüren bir yöntem oluşturun.

Bağlantı dizesini **Sunucu Gezgini** ' de **Satış** verileri bağlantısına sağ tıklayıp **Özellikler**' i seçerek bulabilirsiniz. **ConnectionString** özelliğini bulun ve ardından **Ctrl** + **A** **Ctrl** + dizeyi seçmek ve panoya kopyalamak için CTRL A, CTRL**C** tuşlarını kullanın.

1. C# kullanıyorsanız, **Çözüm Gezgini**' de, proje altındaki **Özellikler** düğümünü genişletin ve ardından **Settings. Settings** dosyasını açın.
    Visual Basic kullanıyorsanız, **Çözüm Gezgini**' de **tüm dosyaları göster**' e tıklayın, **Proje** düğümünü genişletin ve ardından **ayarlar. ayarlar** dosyasını açın.

2. **Ad** sütununda, girin `connString` .

3. **Tür** listesinde **(bağlantı dizesi)** öğesini seçin.

4. **Kapsam** listesinde, **uygulama**' yı seçin.

5. **Değer** sütununda, Bağlantı dizenizi (dış tırnak işaretleri olmadan) girin ve ardından değişikliklerinizi kaydedin.

> [!NOTE]
> Gerçek bir uygulamada bağlantı dizesini [bağlantı dizeleri ve yapılandırma dosyalarında](/dotnet/framework/data/adonet/connection-strings-and-configuration-files)açıklandığı gibi güvenli bir şekilde depolamanız gerekir.

## <a name="write-the-code-for-the-forms"></a>Formların kodunu yazma

Bu bölüm her bir formun ne işe yönelik kısa genel bakış içerir. Ayrıca, formdaki bir düğmeye tıklandığında temel alınan mantığı tanımlayan kodu sağlar.

### <a name="navigation-form"></a>Gezinti formu

Uygulamayı çalıştırdığınızda gezinti formu açılır. **Hesap Ekle** düğmesi NewCustomer formunu açar. **Siparişleri doldur veya iptal et** düğmesi FillOrCancel formunu açar. **Çıkış** düğmesi uygulamayı kapatır.

#### <a name="make-the-navigation-form-the-startup-form"></a>Gezinti formunu başlangıç formu haline getirme

C# kullanıyorsanız, **Çözüm Gezgini**' de **program.cs**açın ve ardından `Application.Run` satırı bu şekilde değiştirin: `Application.Run(new Navigation());`

Visual Basic kullanıyorsanız, **Çözüm Gezgini**' de **Özellikler** penceresini açın, **uygulama** sekmesini seçin ve ardından **başlangıç formu** listesinden **simpledataapp. Navigation** öğesini seçin.

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

Boş olay işleyicisi yöntemleri oluşturmak için gezinti formundaki üç düğmeye çift tıklayın. Düğmelere çift tıklamak, tasarımcı kod dosyasında bir olayı yükseltmek üzere bir düğme tıklamalarını sağlayan otomatik oluşturulan kod de ekler.

#### <a name="add-code-for-the-navigation-form-logic"></a>Gezinti formu mantığı için kod ekleme

Gezinti formu için kod sayfasında, aşağıdaki kodda gösterildiği gibi üç düğme için yöntem gövdelerini, olay işleyicileri ' ne tıklayın.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>NewCustomer formu

Bir müşteri adı girip **Hesap oluştur** düğmesini seçtiğinizde, NewCustomer formu bir müşteri hesabı oluşturur ve SQL Server yenı müşteri kimliği olarak bir kimlik değeri döndürür. Daha sonra bir miktar ve sipariş tarihi belirtip **siparişi yerleştir** düğmesini seçerek yeni hesap için bir sipariş yerleştirebilirsiniz.

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

Dört düğmenin her birine çift tıklayarak NewCustomer formundaki her düğme için boş bir tıklama olayı işleyicisi oluşturun. Düğmelere çift tıklamak, tasarımcı kod dosyasında bir olayı yükseltmek üzere bir düğme tıklamalarını sağlayan otomatik oluşturulan kod de ekler.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>NewCustomer form mantığı için kod ekleyin

NewCustomer form mantığını gerçekleştirmek için aşağıdaki adımları izleyin.

1. `System.Data.SqlClient`Üyelerinin adlarını tam olarak nitelemeniz gerekmiyorsa, ad alanını kapsama taşıyın.

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. Aşağıdaki kodda gösterildiği gibi, sınıfa bazı değişkenler ve yardımcı yöntemler ekleyin.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Aşağıdaki kodda gösterildiği gibi dört düğme için yöntem gövdelerini, olay işleyiciler ' ı doldurun.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>FillOrCancel formu

FillOrCancel formu, bir sipariş KIMLIĞI girerken bir siparişi döndürmek için bir sorgu çalıştırır ve ardından **sırayı bul** düğmesine tıklayabilirsiniz. Döndürülen satır salt okunurdur bir veri kılavuzunda görünür. Siparişi **Iptal et** düğmesini seçerseniz siparişi iptal edildi (X) olarak işaretleyebilirsiniz veya sırayı **doldur** düğmesini seçerseniz sırayı doldurulmuş (F) olarak işaretleyebilirsiniz. **Siparişi bul** düğmesini tekrar seçerseniz, güncelleştirilmiş satır görüntülenir.

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

Düğmeleri çift tıklatarak FillOrCancel formundaki dört düğme için boş tıklama olay işleyicileri oluşturun. Düğmelere çift tıklamak, tasarımcı kod dosyasında bir olayı yükseltmek üzere bir düğme tıklamalarını sağlayan otomatik oluşturulan kod de ekler.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>FillOrCancel form mantığı için kod ekleme

FillOrCancel form mantığını gerçekleştirmek için aşağıdaki adımları izleyin.

1. Üyelerinin adlarını tamamen nitelemeniz gerekmiyorsa, aşağıdaki iki ad alanını kapsama taşıyın.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Aşağıdaki kodda gösterildiği gibi sınıfına bir değişken ve yardımcı yöntem ekleyin.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Aşağıdaki kodda gösterildiği gibi dört düğme için yöntem gövdelerini, olay işleyiciler ' ı doldurun.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Uygulamanızı test etme

Her bir tıklama olayı işleyicisini kodladıktan sonra ve sonra kodlamayı tamamladıktan sonra uygulamanızı derlemek ve test etmek için **F5** tuşunu seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
