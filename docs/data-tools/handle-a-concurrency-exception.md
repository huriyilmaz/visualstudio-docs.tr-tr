---
title: Bir eşzamanlılık özel durumunu işleme
description: İki kullanıcı aynı anda bir veritabanında aynı verileri değiştirmeye çalıştığında oluşan eşzamanlılık özel durumunu (System. Data. DBConcurrencyException) işleyin.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6195fa7e27c6c6f72166dfc00ba888f3644cfe23cb6b38570f4ba6502f458054
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347187"
---
# <a name="handle-a-concurrency-exception"></a>Bir eşzamanlılık özel durumunu işleme

Eşzamanlılık özel durumları ( <xref:System.Data.DBConcurrencyException?displayProperty=fullName> ), iki kullanıcı aynı anda bir veritabanında aynı verileri değiştirme girişiminde bulunduğunda tetiklenir. bu kılavuzda, bir ' ın nasıl yakalandığı <xref:System.Data.DBConcurrencyException> , hataya neden olan satırı nasıl bulacağınızı gösteren bir Windows uygulaması oluşturur ve bunu nasıl işleyeceğinizi gösteren bir strateji öğreneceksiniz.

Bu izlenecek yol, aşağıdaki işlem boyunca size kılavuzluk eden bir işlemdir:

1. yeni bir **Windows Forms uygulama** projesi oluşturun.

2. Northwind Customers tablosunu temel alan yeni bir veri kümesi oluşturun.

3. Verileri göstermek için içeren bir form oluşturun <xref:System.Windows.Forms.DataGridView> .

4. Northwind veritabanındaki Customers tablosunun verileri ile bir veri kümesini doldur.

5. Müşteriler tablosunun verilerine erişmek ve bir kaydı değiştirmek için **Sunucu Gezgini** Içindeki **tablo verilerini göster** özelliğini kullanın.

6. Aynı kaydı farklı bir değerle değiştirin, veri kümesini güncelleştirin ve değişiklikleri veritabanına yazmayı deneyin, bu da bir eşzamanlılık hatası oluşur.

7. Hatayı Yakalayın, ardından kaydın farklı sürümlerini görüntüleyin, kullanıcının devam edip etmediğini ve veritabanını güncelleştirip güncelleştirmeyeceğini belirlemesine izin verir veya güncelleştirmeyi iptal edin.

## <a name="prerequisites"></a>Önkoşullar

bu izlenecek yol, SQL Server Express localdb ve Northwind örnek veritabanını kullanır.

1. SQL Server Express localdb yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio Yükleyicisi** aracılığıyla yükleyin. **Visual Studio Yükleyicisi**, SQL Server Express localdb 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio, **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **yürüt** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

yeni bir Windows Forms uygulaması oluşturarak başlayın:

1. Visual Studio, **dosya** menüsünde **yeni**  >  **Project**' yi seçin.

2. sol bölmedeki **Visual C#** ' ı veya **Visual Basic** genişletin ve sonra **Windows masaüstü**' nü seçin.

3. orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **ConcurrencyWalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     **ConcurrencyWalkthrough** projesi oluşturulup **Çözüm Gezgini** eklenir ve tasarımcıda yeni bir form açılır.

## <a name="create-the-northwind-dataset"></a>Northwind veri kümesini oluşturma

Sonra, **NorthwindDataSet** adlı bir veri kümesi oluşturun:

1. **Veri** menüsünde **Yeni veri kaynağı Ekle**' yi seçin.

   Veri kaynağı Yapılandırma Sihirbazı açılır.

2. **Veri kaynağı türü seçin** ekranında **veritabanı**' nı seçin.

   ![Visual Studio veri kaynağı Yapılandırma Sihirbazı](media/data-source-configuration-wizard.png)

3. Kullanılabilir bağlantılar listesinden Northwind örnek veritabanına bir bağlantı seçin. Bağlantı listesinde bağlantı yoksa, **Yeni bağlantı**' yı seçin.

    > [!NOTE]
    > Bir yerel veritabanı dosyasına bağlanıyorsanız, dosyayı projenize eklemek isteyip istemediğiniz sorulduğunda **Hayır** ' ı seçin.

4. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** ekranında, **İleri**' yi seçin.

5. **Tablolar** düğümünü genişletin ve **müşteriler** tablosunu seçin. Veri kümesinin varsayılan adı **NorthwindDataSet** olmalıdır.

6. Veri kümesini projeye eklemek için **son** ' u seçin.

## <a name="create-a-data-bound-datagridview-control"></a>Veri bağlantılı DataGridView denetimi oluşturma

bu bölümde, <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> **müşteriler** öğesini **veri kaynakları** penceresinden Windows formunuz üzerine sürükleyerek bir oluşturun.

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' i seçin.

2. **Veri kaynakları** penceresinde **NorthwindDataSet** düğümünü genişletin ve ardından **Customers** tablosunu seçin.

3. Tablo düğümünde aşağı oku seçin ve ardından açılır listeden **DataGridView** ' i seçin.

4. Tabloyu formunuzun boş bir alanının üzerine sürükleyin.

     <xref:System.Windows.Forms.DataGridView> **CustomersDataGridView** adlı bir denetim ve <xref:System.Windows.Forms.BindingNavigator> adlı **CustomersBindingNavigator**, öğesine bağlanan forma eklenir <xref:System.Windows.Forms.BindingSource> . Bu, sırasıyla NorthwindDataSet 'teki Customers tablosuna bağlanır.

## <a name="test-the-form"></a>Formu test etme

Artık formu, bu noktaya kadar beklenen şekilde davrandığından emin olmak için test edebilirsiniz:

1. Uygulamayı çalıştırmak için **F5** ' i seçin.

     Form, <xref:System.Windows.Forms.DataGridView> Müşteriler tablosundaki verilerle doldurulmuş bir denetim ile birlikte görüntülenir.

2. **Hata Ayıklama** menüsünde **Hata Ayıklamayı Durdur**’u seçin.

## <a name="handle-concurrency-errors"></a>Eşzamanlılık hatalarını işleme

Hataları nasıl işleyeceğinizi uygulamanızı yöneten belirli iş kurallarına göre değişir. Bu kılavuzda, eşzamanlılık hatasının nasıl ele alınacağını gösteren bir örnek olarak aşağıdaki stratejiyi kullanırız.

Uygulama, kullanıcıya kaydın üç sürümünü sunar:

- Veritabanındaki geçerli kayıt

- Veri kümesine yüklenen özgün kayıt

- Veri kümesindeki önerilen değişiklikler

Böylece Kullanıcı önerilen sürümle birlikte veritabanının üzerine yazabilir veya güncelleştirmeyi iptal edebilir ve veri kümesini veritabanından yeni değerlerle yenileyebilir.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Eşzamanlılık hatalarının işlenmesini etkinleştirmek için

1. Özel bir hata işleyicisi oluşturun.

2. Kullanıcılara seçenekleri görüntüleyin.

3. Kullanıcının yanıtını işleyin.

4. Güncelleştirmeyi yeniden gönderin veya veri kümesindeki verileri sıfırlayın.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Eşzamanlılık özel durumunu işlemek için kod ekleme

Bir güncelleştirme gerçekleştirmeye çalıştığınızda ve bir özel durum ortaya çıktığında, genellikle oluşturulan özel durum tarafından verilen bilgilerle ilgili bir şey yapmak istersiniz. Bu bölümde, veritabanını güncelleştirmeyi deneyen kodu eklersiniz. Ayrıca <xref:System.Data.DBConcurrencyException> , başka tüm özel durumlar da ortaya çıkarılan herhangi bir işlem de vardır.

> [!NOTE]
> `CreateMessage`Ve `ProcessDialogResults` yöntemleri, izlenecek yolda daha sonra eklenir.

1. Aşağıdaki kodu yönteminin altına ekleyin `Form1_Load` :

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet1":::

2. Yöntemi, `CustomersBindingNavigatorSaveItem_Click` yöntemini çağırmak için `UpdateDatabase` aşağıdaki gibi görünmesi için değiştirin:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet2":::

### <a name="display-choices-to-the-user"></a>Kullanıcı için seçimleri görüntüle

Yeni yazdığınız kod, `CreateMessage` kullanıcıya hata bilgilerini görüntüleme yordamını çağırır. Bu izlenecek yol için, kaydın farklı sürümlerini kullanıcıya göstermek üzere bir ileti kutusu kullanın. Bu, kullanıcının değişikliklerle ilgili kaydın üzerine yazılıp yazılmayacağını veya düzenlemeyi iptal edip etmediğini seçmesini sağlar. Kullanıcı, ileti kutusunda bir seçenek seçtiğinde (bir düğmeye tıkladığında), yanıt `ProcessDialogResult` yöntemine geçirilir.

**Kod düzenleyicisine** aşağıdaki kodu ekleyerek iletiyi oluşturun. Metodun altına bu kodu girin `UpdateDatabase` :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet4":::

### <a name="process-the-users-response"></a>Kullanıcının yanıtını işle

Kullanıcının ileti kutusuna yanıtını işlemek için de kod gerekir. Seçenekler, önerilen değişiklikle veritabanındaki geçerli kaydın üzerine yazar veya yerel değişiklikleri iptal edebilir ve veri tablosunu veritabanında Şu anda olan kayıtla yeniler. Kullanıcı **Evet**' i seçerse, <xref:System.Data.DataTable.Merge%2A> yöntemi *PreserveChanges* bağımsız değişkeniyle **doğru** olarak ayarlanır. Bu, kaydın orijinal sürümü artık veritabanındaki kayıtla eşleştiğinden güncelleştirme denemesinin başarılı olmasına neden olur.

Önceki bölümde eklenmiş olan kodun altına aşağıdaki kodu ekleyin:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form-behavior"></a>Form davranışını test etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz. Eşzamanlılık ihlalinin benzetimini yapmak için, NorthwindDataSet 'i doldurduktan sonra veritabanındaki verileri değiştirirsiniz.

1. Uygulamayı çalıştırmak için **F5** ' i seçin.

2. form görüntülendikten sonra çalışır durumda bırakın ve Visual Studio ıde 'ye geçin.

3. **Görünüm** menüsünde **Sunucu Gezgini**' yi seçin.

4. **Sunucu Gezgini**, uygulamanızın kullandığı bağlantıyı genişletin ve **Tablolar** düğümünü genişletin.

5. **Müşteriler** tablosuna sağ tıklayın ve ardından **tablo verilerini göster**' i seçin.

6. İlk kayıtta (**ALFKI),** **ContactName'i** **Maria Anders2 olarak değiştirir.**

    > [!NOTE]
    > Değişikliği işlemek için farklı bir satıra gidin.

7. ConcurrencyWalkthrough'un çalışan formuna geçiş.

8. Formda ilk kayıtta (**ALFKI),** **ContactName'i** **Maria Anders1 olarak değiştirir.**

9. **Kaydet** düğmesini seçin.

     Eşzamanlılık hatası oluştu ve ileti kutusu görüntülenir.

   **Hayır'ı** seçmek güncelleştirmeyi iptal eder ve veri kümesi şu anda veritabanında olan değerlerle güncelleştirmeyi sağlar. **Evet'i** seçmek önerilen değeri veritabanına yazar.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
