---
title: ADO.NET kullanarak basit veri uygulaması oluşturma
description: Visual Studio Windows Forms ve ADO.NET kullanarak basit bir form-veri uygulaması oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 506983ffacf846969f6e74fd503344d90180ca91
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631520"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET kullanarak basit veri uygulaması oluşturma

Veritabanındaki verileri işleyen bir uygulama oluşturduğunuzda, bağlantı dizelerini tanımlama, veri ekleme ve saklı yordamları çalıştırma gibi temel görevleri gerçekleştirirsiniz. bu konuyu izleyerek, Visual C# veya Visual Basic ve ADO.NET kullanarak basit bir Windows Forms "veri üzerinden Forms" uygulamasının içinden bir veritabanıyla nasıl etkileşim kuracağınızı bulabilirsiniz.  veri kümeleri, LINQ to SQL ve Entity Framework dahil olmak üzere tüm .net veri teknolojileri, sonuçta bu makalede gösterilenler için çok benzeyen adımları gerçekleştirir.

Bu makalede, verileri bir veritabanından hızlı bir şekilde almanın basit bir yolu gösterilmektedir. Uygulamanızın verileri basit olmayan yollarla değiştirmesi ve veritabanını güncelleştirmesi gerekiyorsa, Kullanıcı arabirimi denetimlerini temel verilerdeki değişikliklerle otomatik olarak eşitlemek için Entity Framework kullanmayı ve veri bağlamayı kullanmayı göz önünde bulundurmanız gerekir.

> [!IMPORTANT]
> Kodu basit tutmak için üretime hazırlanma özel durum işleme içermez.

## <a name="prerequisites"></a>Önkoşullar

Uygulamayı oluşturmak için şunlar gerekir:

- Visual Studio.

- SQL Server Express LocalDB. SQL Server Express localdb yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)yükleyebilirsiniz.

bu konu, Visual Studio ıde 'nin temel işlevleriyle ilgili bilgi sahibi olduğunuzu ve bir Windows Forms uygulaması oluşturabileceğiniz, projeye form ekleyebileceğiniz, düğmeleri ve diğer denetimleri formlara ekleyebileceğiniz, denetimlerin özelliklerini ayarlayabildiğiniz ve basit olaylar kodlarınızın olduğu varsayılmaktadır. bu görevlerle ilgili deneyimli değilseniz, bu yönergeyi başlamadan önce [Visual C# ve Visual Basic ile çalışmaya](../ide/quickstart-visual-basic-console.md) başlama konusunu tamamlamanızı öneririz.

## <a name="set-up-the-sample-database"></a>Örnek veritabanını ayarlama

Aşağıdaki adımları izleyerek örnek veritabanını oluşturun:

1. Visual Studio, **Sunucu Gezgini** penceresini açın.

2. **veri bağlantıları** ' na sağ tıklayın ve **yeni SQL Server veritabanı oluştur**' u seçin.

3. **Sunucu adı** metin kutusuna **(LocalDB) \mssqllocaldb** yazın.

4. **Yeni veritabanı adı** metin kutusunda **Sales** yazın ve ardından **Tamam**' ı seçin.

     Boş **Satış** veritabanı oluşturulur ve Sunucu Gezgini veri bağlantıları düğümüne eklenir.

5. **Satış** verileri bağlantısına sağ tıklayın ve **Yeni sorgu**' yı seçin.

     Sorgu Düzenleyicisi penceresi açılır.

6. [Sales Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) panonuza kopyalayın.

7. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **yürüt** düğmesini seçin.

     Kısa bir süre sonra sorgu çalışmayı sonlandırır ve veritabanı nesneleri oluşturulur. Veritabanı iki tablo içerir: müşteri ve siparişler. Bu tablolar başlangıçta veri içermez, ancak oluşturacağınız uygulamayı çalıştırdığınızda veri ekleyebilirsiniz. Veritabanı ayrıca dört basit saklı yordam içerir.

## <a name="create-the-forms-and-add-controls"></a>Formları oluşturma ve denetimleri ekleme

1. Windows Forms bir uygulama için bir proje oluşturun ve bunu **simpledataapp** olarak adlandırın.

    Visual Studio, **Form1** adlı boş bir Windows formu da dahil olmak üzere projeyi ve birkaç dosyayı oluşturur.

2. projenize üç form eklemek ve ardından aşağıdaki adları vermek için iki Windows form ekleyin:

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

Bağlantı dizesini **Sunucu Gezgini** ' de **Satış** verileri bağlantısına sağ tıklayıp **Özellikler**' i seçerek bulabilirsiniz. **ConnectionString özelliğini bulun,** ardından **Ctrl** + **A**, **Ctrl** C tuşlarını kullanarak dizeyi seçin +  ve panoya kopyalayın.

1. C# kullanıyorsanız, **Çözüm Gezgini** altında Özellikler düğümünü  genişletin ve **Ayarlar.settings dosyasını** açın.
    Visual Basic kullanıyorsanız, **Çözüm Gezgini** Tüm Dosyaları Göster'e **tıklayın,** **My Project** düğümünü genişletin ve **Ayarlar.settings dosyasını** açın.

2. Ad **sütununa** `connString` girin.

3. Tür **listesinde (Bağlantı** **Dizesi) öğesini seçin.**

4. Kapsam **listesinde Uygulama'ya** **tıklayın.**

5. Değer **sütununa** bağlantı dizenizi girin (dış tırnak olmadan) ve ardından değişikliklerinizi kaydedin.

> [!NOTE]
> Bağlantı dizeleri ve yapılandırma dosyaları altında açıklandığı gibi, gerçek bir uygulamada bağlantı dizesini [güvenli bir şekilde depolamanız gerekir.](/dotnet/framework/data/adonet/connection-strings-and-configuration-files)

## <a name="write-the-code-for-the-forms"></a>Formlar için kod yazma

Bu bölümde, her formun ne yaptığına ilişkin kısa genel bakışlar yer almaktadır. Ayrıca formda bir düğmeye tıkıldığında temel mantığı tanımlayan kodu da sağlar.

### <a name="navigation-form"></a>Gezinti formu

Uygulamayı çalıştırarak Gezinti formu açılır. Hesap **ekle düğmesi** NewCustomer formunu açar. Siparişleri **doldur veya iptal et** düğmesi FillOrCancel formunu açar. **Çıkış düğmesi** uygulamayı kapatır.

#### <a name="make-the-navigation-form-the-startup-form"></a>Gezinti formunu başlangıç formu yapma

C# kullanıyorsanız, **Çözüm Gezgini** içinde **Program.cs'yi** açın ve satırı `Application.Run` şu şekilde değiştirebilirsiniz: `Application.Run(new Navigation());`

Visual Basic kullanıyorsanız, **Çözüm Gezgini** penceresini açın, Uygulama sekmesini  seçin ve ardından  Başlangıç formu listesinde **SimpleDataApp.Navigation** **öğesini** seçin.

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

Boş olay işleyici yöntemleri oluşturmak için Gezinti formundaki üç düğmeye çift tıklayın. Düğmelere çift tıklarsanız Tasarımcı kod dosyasına otomatik olarak oluşturulan kod ekleyen bu kod, bir düğmeye tıklamanın bir olay oluşturması için olanak sağlar.

#### <a name="add-code-for-the-navigation-form-logic"></a>Gezinti formu mantığı için kod ekleme

Gezinti formunun kod sayfasında, aşağıdaki kodda gösterildiği gibi üç düğmenin tıklama olayı işleyicileri için yöntem gövdelerini doldurun.

:::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs" id="Snippet1":::
:::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb" id="Snippet1":::

### <a name="newcustomer-form"></a>NewCustomer formu

Bir müşteri adı girerek Hesap  Oluştur düğmesini seçerek NewCustomer formu bir müşteri hesabı oluşturur ve SQL Server kimliği olarak bir IDENTITY değeri döndürür. Ardından, bir tutar ve sipariş tarihi belirterek ve Siparişi Sırala düğmesini seçerek yeni hesap için **bir sipariş veebilirsiniz.**

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

Dört düğmenin her biri üzerine çift tıklayarak NewCustomer formundaki her düğme için boş bir Tıklama olayı işleyicisi oluşturun. Düğmelere çift tıklarsanız Tasarımcı kod dosyasına otomatik olarak oluşturulan kod ekleyen bu kod, bir düğmeye tıklamanın bir olay oluşturması için olanak sağlar.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>NewCustomer form mantığı için kod ekleme

NewCustomer form mantığını tamamlamak için aşağıdaki adımları izleyin.

1. Ad `System.Data.SqlClient` alanını kapsamına alın, böylece üyelerinin adlarını tam olarak nitelendirebilirsiniz.

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. Aşağıdaki kodda gösterildiği gibi sınıfına bazı değişkenler ve yardımcı yöntemler ekleyin.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs" id="Snippet1":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb" id="Snippet1":::

3. Dört düğmenin yöntem gövdelerini tamamlamak için aşağıdaki kodda gösterildiği gibi olay işleyicilerini tıklatın.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs" id="Snippet2":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb" id="Snippet2":::

### <a name="fillorcancel-form"></a>FillOrCancel formu

FillOrCancel formu, sipariş kimliği girerken sipariş dönmek için bir sorgu çalıştırır ve ardından Siparişi Bul **düğmesine** tıklayın. Döndürülen satır salt okunur veri kılavuzunda görünür. Siparişi İptal Et düğmesini seçerse siparişi iptal  edildi (X) olarak veya Siparişi Doldur düğmesini seçerse siparişi doldurulmuş (F) olarak **işaretlayabilirsiniz.** Siparişi Bul düğmesini **yeniden** seçersiniz, güncelleştirilmiş satır görüntülenir.

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

FillOrCancel formundaki dört düğme için düğmelere çift tıklayarak boş Tıklama olayı işleyicileri oluşturun. Düğmelere çift tıklarsanız Tasarımcı kod dosyasına otomatik olarak oluşturulan kod ekleyen bu kod, bir düğmeye tıklamanın bir olay oluşturması için olanak sağlar.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>FillOrCancel form mantığı için kod ekleme

FillOrCancel form mantığını tamamlamak için aşağıdaki adımları izleyin.

1. Üyelerinin adlarını tam olarak nitelendirmamanız için aşağıdaki iki ad alanını kapsamına alın.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Aşağıdaki kodda gösterildiği gibi sınıfına bir değişken ve yardımcı yöntemi ekleyin.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs" id="Snippet1":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb" id="Snippet1":::

3. Dört düğmenin yöntem gövdelerini tamamlamak için aşağıdaki kodda gösterildiği gibi olay işleyicilerini tıklatın.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs" id="Snippet2":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb" id="Snippet2":::

## <a name="test-your-application"></a>Uygulamalarınızı test etmek

Her Click olayı işleyicisini kodladikten sonra ve kodlamayı bitirdikten sonra, uygulamayı derlemek ve test etmek için **F5** anahtarını seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
