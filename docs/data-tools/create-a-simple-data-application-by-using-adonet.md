---
title: ADO.NET kullanarak basit veri uygulaması oluşturma
description: Windows Forms kullanarak basit bir formlar ADO.NET uygulaması Visual Studio.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161999"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET kullanarak basit veri uygulaması oluşturma

Veritabanındaki verileri yönlendiren bir uygulama bilgisayarınızda bağlantı dizelerini tanımlama, veri ekleme ve saklı yordamları çalıştırma gibi temel görevleri gerçekleştirebilirsiniz. Bu konuyu takip etmek için Visual C# veya Visual Basic ve ADO.NET kullanarak basit bir Windows Forms "veriler üzerinde formlar" uygulamasından bir veritabanıyla ADO.NET.  Veri kümeleri, veri kümeleri, LINQ to SQL ve Entity Framework gibi tüm .NET veri teknolojileri, sonunda bu makalede gösterilenlere çok benzer adımlar gerçekleştirmektedir.

Bu makalede, veritabanından hızlı bir şekilde veri almak için basit bir yol açıklanmıştır. Uygulamanıza verileri önemsiz yollarla değiştirmesi ve veritabanını güncelleştirmesi gerekirse, kullanıcı arabirimi denetimlerini temel alınan verilerde yapılan değişikliklerle otomatik olarak eşitlemek için Entity Framework ve veri bağlamayı kullanmayı göz önünde bulundurabilirsiniz.

> [!IMPORTANT]
> Kodu basit tutmak için üretime hazır özel durum işleme dahil değildir.

## <a name="prerequisites"></a>Önkoşullar

Uygulamayı oluşturmak için aşağıdakiler gerekir:

- Visual Studio.

- SQL Server Express Localdb. Yerel VERITABANınız yoksa, SQL Server Express indirme sayfasından [SQL Server Express yükleyebilirsiniz.](https://www.microsoft.com/sql-server/sql-server-editions-express)

Bu konu başlığında, Visual Studio IDE'nin temel işlevleri hakkında bilgi sahibi olduğunuz ve bir Windows Forms uygulaması oluşturabilirsiniz, projeye form ekleyebilir, formlara düğmeler ve diğer denetimler ekleyebilir, denetimlerin özelliklerini ayarlayabilirsiniz ve basit olayları kodlayabilirsiniz. Bu görevlerden rahatsızsanız, bu kılavuza başlamadan önce [Visual C#](../ide/quickstart-visual-basic-console.md) ile çalışmaya başlama ve Visual Basic konusunu tamamlamanızı öneririz.

## <a name="set-up-the-sample-database"></a>Örnek veritabanını ayarlama

Aşağıdaki adımları kullanarak örnek veritabanını oluşturun:

1. Bu Visual Studio' **Sunucu Gezgini** açın.

2. Veri Bağlantıları'ne **sağ tıklayın ve Veritabanı** için Yeni SQL Server **seçin.**

3. Sunucu **adı metin** kutusuna **(localdb)\mssqllocaldb girin.**

4. Yeni veritabanı **adı metin kutusuna** Sales yazın ve **Tamam'ı** **seçin.**

     Boş **Sales** veritabanı oluşturulur ve veri kümesinde Veri Bağlantıları düğümüne Sunucu Gezgini.

5. Satış verileri bağlantısına **sağ tıklayın** ve Yeni Sorgu'yı **seçin.**

     Sorgu düzenleyicisi penceresi açılır.

6. Sales [Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) kopyalayın.

7. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

     Kısa bir süre sonra sorgunun çalışıyor ve veritabanı nesneleri oluşturulur. Veritabanı iki tablo içerir: Customer ve Orders. Bu tablolar başlangıçta veri içermemektedir, ancak oluşturacakları uygulamayı çalıştırarak veri ebilirsiniz. Veritabanı dört basit saklı yordam da içerir.

## <a name="create-the-forms-and-add-controls"></a>Formları oluşturma ve denetim ekleme

1. Windows Forms uygulaması için bir proje oluşturun ve **simpleDataApp olarak ad girin.**

    Visual Studio projeyi ve Form1 adlı boş bir Windows dosyası da dahil olmak üzere birkaç **dosya oluşturur.**

2. Projenize Windows form ekleyen iki form ekleyin ve ardından aşağıdaki adları ekleyin:

   - **Gezinti**

   - **NewCustomer**

   - **FillOrCancel**

3. Her form için, aşağıdaki çizimlerde görünen metin kutularını, düğmeleri ve diğer denetimleri ekleyin. Her denetim için, tabloların açık olduğu özellikleri ayarlayın.

   > [!NOTE]
   > Grup kutusu ve etiket denetimleri netlik sağlar ancak kodda kullanılmaz.

   **Gezinti formu**

   ![Gezinti iletişim kutusu](../data-tools/media/simpleappnav.png)

|Gezinti formu denetimleri|Özellikler|
| - |----------------|
|Düğme|Ad = btnGoToAdd|
|Düğme|Ad = btnGoToFillOrCancel|
|Düğme|Ad = btnExit|

**NewCustomer formu**

![Yeni müşteri ekleme ve sipariş düzenleme](../data-tools/media/simpleappnewcust.png)

|NewCustomer formu için denetimler|Özellikler|
| - |----------------|
|TextBox|Ad = txtCustomerName|
|TextBox|Ad = txtCustomerID<br /><br /> Readonly = True|
|Düğme|Ad = btnCreateAccount|
|Numericupdown|DecimalPlaces = 0<br /><br /> En fazla = 5000<br /><br /> Ad = numOrderAmount|
|Datetimepicker|Format = Short<br /><br /> Ad = dtpOrderDate|
|Düğme|Ad = btnPlaceOrder|
|Düğme|Ad = btnAddAnotherAccount|
|Düğme|Ad = btnAddFinish|

**FillOrCancel formu**

![siparişleri doldurma veya iptal etme](../data-tools/media/simpleappcancelfill.png)

|FillOrCancel formu için denetimler|Özellikler|
| - |----------------|
|TextBox|Ad = txtOrderID|
|Düğme|Ad = btnFindByOrderID|
|Datetimepicker|Format = Short<br /><br /> Ad = dtpFillDate|
|Datagridview|Ad = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|Düğme|Ad = btnCancelOrder|
|Düğme|Ad = btnFillOrder|
|Düğme|Ad = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Bağlantı dizesini depolama
Uygulamanız veritabanına bir bağlantı açmaya çalıştığında, uygulamanın bağlantı dizesine erişimi olmalıdır. Dizeyi her forma el ile girmekten kaçınmak için dizeyi *projenizinApp.config* dosyasında depolar ve uygulamanıza herhangi bir formda yöntem çağrıldında dizeyi döndüren bir yöntem oluşturun.

Bağlantı dizesini, bağlantı dizesinde Satış  verileri bağlantısına sağ tıklar ve **özellikler'Sunucu Gezgini** **bulabilirsiniz.** **ConnectionString özelliğini bulun,** ardından **Ctrl** + **A**, **Ctrl** C tuşlarını kullanarak dizeyi seçin +  ve panoya kopyalayın.

1. C# kullanıyorsanız, **Çözüm Gezgini** proje altındaki Özellikler  düğümünü genişletin ve **Ayarlar.settings dosyasını** açın.
    Visual Basic kullanıyorsanız, Çözüm Gezgini Tüm Dosyaları **Göster'e** **tıklayın,** My **Project** düğümünü genişletin ve **Ayarlar.settings dosyasını** açın.

2. Ad **sütununa** `connString` girin.

3. Tür **listesinde (Bağlantı** **Dizesi) öğesini seçin.**

4. Kapsam **listesinde Uygulama'ya** **tıklayın.**

5. Değer **sütununa** bağlantı dizenizi girin (dış tırnak olmadan) ve ardından değişikliklerinizi kaydedin.

> [!NOTE]
> Bağlantı dizeleri ve yapılandırma dosyaları altında açıklandığı gibi, gerçek bir uygulamada bağlantı dizesini [güvenli bir şekilde depolamanız gerekir.](/dotnet/framework/data/adonet/connection-strings-and-configuration-files)

## <a name="write-the-code-for-the-forms"></a>Formlar için kod yazma

Bu bölümde, her formun ne yaptığına ilişkin kısa genel bakışlar yer almaktadır. Ayrıca formda bir düğmeye tıkıldığında temel mantığı tanımlayan kodu da sağlar.

### <a name="navigation-form"></a>Gezinti formu

Uygulamayı çalıştırarak Gezinti formu açılır. Hesap **ekle düğmesi** NewCustomer formunu açar. Siparişleri **doldur veya iptal et** düğmesi FillOrCancel formunu açar. Çıkış  düğmesi uygulamayı kapatır.

#### <a name="make-the-navigation-form-the-startup-form"></a>Gezinti formunu başlangıç formu yapma

C# kullanıyorsanız, **Çözüm Gezgini**'de **Program.cs'yi** açın ve satırı `Application.Run` şu şekilde değiştirirsiniz: `Application.Run(new Navigation());`

Visual Basic kullanıyorsanız, **Çözüm Gezgini** penceresini açın, Uygulama sekmesini seçin  ve ardından  Başlangıç formu listesinde **SimpleDataApp.Navigation** **öğesini** seçin.

#### <a name="create-auto-generated-event-handlers"></a>Otomatik olarak oluşturulan olay işleyicileri oluşturma

Boş olay işleyici yöntemleri oluşturmak için Gezinti formundaki üç düğmeye çift tıklayın. Düğmelere çift tıklarsanız Tasarımcı kod dosyasına otomatik olarak oluşturulan kod ekleyen bu kod, bir düğmeye tıklamanın bir olay oluşturması için olanak sağlar.

#### <a name="add-code-for-the-navigation-form-logic"></a>Gezinti formu mantığı için kod ekleme

Gezinti formunun kod sayfasında, aşağıdaki kodda gösterildiği gibi üç düğmenin tıklama olayı işleyicileri için yöntem gövdelerini doldurun.

:::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs" id="Snippet1":::
:::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb" id="Snippet1":::

### <a name="newcustomer-form"></a>NewCustomer formu

Bir müşteri adı girerek Hesap  Oluştur düğmesini seçerek NewCustomer formu bir müşteri hesabı oluşturur SQL Server yeni müşteri kimliği olarak bir IDENTITY değeri döndürür. Ardından, bir tutar ve sipariş tarihi belirterek ve Siparişi Sırala düğmesini seçerek yeni hesap için **bir sipariş veebilirsiniz.**

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

1. Üyelerinin adlarını tam olarak nitelendirmanız gerekmay için aşağıdaki iki ad alanını kapsamına alın.

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
