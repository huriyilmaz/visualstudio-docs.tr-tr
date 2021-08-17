---
title: Bir eşzamanlılık özel durumunu işleme
description: İki kullanıcı aynı anda veritabanındaki aynı verileri değiştirmeye çalışsa ortaya konan bir eşzamanlılık özel durumu (System.Data.DBConcurrencyException) işleme.
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

İki kullanıcı aynı anda bir veritabanındaki aynı verileri değiştirmeye çalışırken eşzamanlılık özel durumları ( <xref:System.Data.DBConcurrencyException?displayProperty=fullName> ) ortaya çıkar. Bu kılavuzda, bir yakalamayı Windows, hataya neden olan satırın yerini gösteren ve nasıl işlenecekleri hakkında bir strateji öğrenen bir Windows <xref:System.Data.DBConcurrencyException> uygulaması oluşturabilirsiniz.

Bu izlenecek yol, aşağıdaki işlem boyunca size yol sağlar:

1. Forms Uygulaması **Windows yeni bir dosya** oluşturun.

2. Northwind Customers tablosuna göre yeni bir veri kümesi oluşturun.

3. Verileri görüntülemek için ile <xref:System.Windows.Forms.DataGridView> bir form oluşturun.

4. Northwind veritabanındaki Customers tablosundan verilerle bir veri kümesi doldurun.

5. **Customers-table'ın** verilerine **erişmek Sunucu Gezgini** kaydı değiştirmek için tablodaki Tablo Verilerini Göster özelliğini kullanın.

6. Aynı kaydı farklı bir değerle değiştirme, veri kümesi güncelleştirme ve değişiklikleri veritabanına yazmayı deneme; bu da eşzamanlılık hatasının ortaya konarak sonuç verir.

7. Hatayı yakalar, ardından kaydın farklı sürümlerini görüntüler ve kullanıcının devam edip veritabanını güncelleştirme veya güncelleştirmeyi iptal etme konusunda karar vermesini sağlar.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. Yerel VERITABANınız yoksa, SQL Server Express sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Bu **Visual Studio Yükleyicisi,** yerel SQL Server Express veri depolama ve işleme iş  yükünün bir parçası olarak veya tek bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (SQL Server Nesne Gezgini, veri depolama ve işleme iş **yükünün bir parçası** olarak Visual Studio Yükleyicisi.) SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Bir sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

Başlangıç olarak yeni bir Windows Forms uygulaması oluşturma:

1. Dosya Visual Studio Menüsünde **Yeni** Dosya'Project.   >  

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve ardından Masaüstü'Windows **seçin.**

3. Orta bölmede Windows **Forms Uygulaması proje** türünü seçin.

4. Projeye **ConcurrencyWalkthrough adını ve** ardından Tamam'ı **seçin.**

     **ConcurrencyWalkthrough** projesi oluşturulur ve **Çözüm Gezgini** eklenir ve tasarımcıda yeni bir form açılır.

## <a name="create-the-northwind-dataset"></a>Northwind veri kümesi oluşturma

Ardından **NorthwindDataSet** adlı bir veri kümesi oluşturun:

1. Veri menüsünde **Yeni** Veri kaynağı **Ekle'yi seçin.**

   Veri Kaynağı Yapılandırma Sihirbazı açılır.

2. Veri **Kaynağı Türü Seçin ekranında Veritabanı'ı** **seçin.**

   ![Visual Studio'de Veri Kaynağı Yapılandırma Sihirbazı](media/data-source-configuration-wizard.png)

3. Kullanılabilir bağlantılar listesinden Northwind örnek veritabanına bir bağlantı seçin. Bağlantı listesinde bağlantı kullanılamıyorsa Yeni **Bağlantı'ya tıklayın.**

    > [!NOTE]
    > Yerel bir veritabanı dosyasına bağlanıyorsanız,  dosyayı projenize eklemek istediğiniz sorulsa Hayır'ı seçin.

4. Bağlantı **dizesini uygulama yapılandırma dosyasına kaydet ekranında,** Sonraki'yi **seçin.**

5. Tablolar **düğümünü** genişletin ve **Müşteriler tablolarını** seçin. Veri kümesi için varsayılan ad **NorthwindDataSet'tir.**

6. Veri **kümesi** projeye eklemek için Son'a tıklayın.

## <a name="create-a-data-bound-datagridview-control"></a>Veriye bağlı DataGridView denetimi oluşturma

Bu bölümde, Veri Kaynakları penceresinden Müşteriler öğesini Veri <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> Kaynakları form **sayfanıza** sürükleyerek bir Windows oluşturabilirsiniz. 

1. Veri Kaynakları **penceresini açmak** için Veri menüsünde **Veri** Kaynaklarını **Göster'i seçin.**

2. Veri **Kaynakları penceresinde** **NorthwindDataSet düğümünü genişletin** ve Ardından Müşteriler **tablosuna** tıklayın.

3. Tablo düğümünde aşağı oku ve ardından açılan listeden **DataGridView'u** seçin.

4. Tabloyu formuzdaki boş bir alana sürükleyin.

     <xref:System.Windows.Forms.DataGridView> **CustomersDataGridView** adlı bir denetim <xref:System.Windows.Forms.BindingNavigator> ve **CustomersBindingNavigator** adlı bir denetim, 'a bağlı forma <xref:System.Windows.Forms.BindingSource> eklenir. Bu da NorthwindDataSet'te Customers tablosuna bağlı olur.

## <a name="test-the-form"></a>Formu test etmek

Artık formu test etmek için şu noktaya kadar beklendiği gibi davranacak şekilde davranabilirsiniz:

1. Uygulamayı **çalıştırmak için F5'i** seçin.

     Form, Üzerinde Customers <xref:System.Windows.Forms.DataGridView> tablosundan verilerle doldurulmuş bir denetimle görüntülenir.

2. **Hata Ayıklama** menüsünde **Hata Ayıklamayı Durdur**’u seçin.

## <a name="handle-concurrency-errors"></a>Eşzamanlılık hatalarını işleme

Hataları işlemeniz, uygulamanızı yöneten belirli iş kurallarına bağlıdır. Bu kılavuzda, eşzamanlılık hatasını işlemeye örnek olarak aşağıdaki stratejiyi kullanacağız.

Uygulama, kullanıcıya kaydın üç sürümünü sunar:

- Veritabanındaki geçerli kayıt

- Veri kümesine yüklenen özgün kayıt

- Veri kümesinde önerilen değişiklikler

Kullanıcı daha sonra önerilen sürümle veritabanının üzerine yazarak veya güncelleştirmeyi iptal edip veri kümesini veritabanındaki yeni değerlerle yeniler.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Eşzamanlılık hatalarının işlenmesini etkinleştirmek için

1. Özel hata işleyicisi oluşturun.

2. Kullanıcıya seçimleri görüntüleme.

3. Kullanıcının yanıtını işleme.

4. Güncelleştirmeyi yeniden veya veri kümesinde verileri sıfırlayın.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Eşzamanlılık özel durumlarını işlemek için kod ekleme

Bir güncelleştirmeyi gerçekleştirmeye çalışırken bir özel durum ortaya çıkarsa, genel olarak, yükseltilmiş özel durum tarafından sağlanan bilgilerle bir şey yapmak istersiniz. Bu bölümde, veritabanını güncelleştirmeye çalışan kodu eklersiniz. Ayrıca, hem ortaya <xref:System.Data.DBConcurrencyException> çıkarlan tüm özel durumları hem de diğer özel durumları işleysiniz.

> [!NOTE]
> ve `CreateMessage` `ProcessDialogResults` yöntemleri, kılavuzda daha sonra eklenir.

1. Aşağıdaki kodu yönteminin altına `Form1_Load` ekleyin:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet1":::

2. yöntemini `CustomersBindingNavigatorSaveItem_Click` çağırarak yöntemini `UpdateDatabase` aşağıdaki gibi olacak şekilde değiştirin:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet2":::

### <a name="display-choices-to-the-user"></a>Kullanıcıya seçenekleri görüntüleme

Az önce yazdığını kod, `CreateMessage` kullanıcıya hata bilgilerini görüntülemek için yordamını çağırıyor. Bu kılavuzda, kaydın farklı sürümlerini kullanıcıya görüntülemek için bir ileti kutusu kullanırsınız. Bu, kullanıcının kaydın üzerine değişiklik yazma veya düzenlemeyi iptal etme seçmesini sağlar. Kullanıcı ileti kutusunda bir seçenek (bir düğmeye tıkladığında) yanıt yöntemine `ProcessDialogResult` geçirildi.

Kod Düzenleyicisi'ne aşağıdaki kodu ekleyerek **iletiyi oluşturun.** Yönteminin altına şu kodu `UpdateDatabase` girin:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet4":::

### <a name="process-the-users-response"></a>Kullanıcının yanıtını işleme

İleti kutusuna kullanıcının yanıtını işlemesi için de koda ihtiyacınız vardır. Seçenekler, önerilen değişiklikle veritabanındaki geçerli kaydın üzerine yazmak veya yerel değişiklikleri bırakmak ve veri tablolarını veritabanındaki kayıtla yenilemektir. Kullanıcı Evet'i **seçerse,** preserveChanges bağımsız değişkeni true olarak <xref:System.Data.DataTable.Merge%2A> ayarlanmış şekilde yöntemi **çağrılır.**  Kaydın özgün sürümü artık veritabanındaki kayıtla eş olduğundan bu güncelleştirme girişiminin başarılı olmasına neden olur.

Önceki bölümde eklenen kodun altına aşağıdaki kodu ekleyin:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form-behavior"></a>Form davranışını test etmek

Artık formu test etmek için beklendiği gibi davranarak emin olun. Eşzamanlılık ihlalinin benzetimini yapmak için NorthwindDataSet'i doldurduktan sonra veritabanındaki verileri değiştirirsiniz.

1. Uygulamayı **çalıştırmak için F5'i** seçin.

2. Form görüntülendiğinde, açık bırakın ve IDE'nin Visual Studio olun.

3. Görünüm menüsünde **Seç'i** Sunucu Gezgini.

4. Bu **Sunucu Gezgini,** uygulamanın kullanmakta olduğu bağlantıyı genişletin ve ardından Tablolar **düğümünü** genişletin.

5. Customers tablosuna **sağ tıklayın** ve Tablo Verilerini **Göster'i seçin.**

6. İlk kayıtta (**ALFKI),** **ContactName'i** **Maria Anders2 olarak değiştirir.**

    > [!NOTE]
    > Değişikliği işlemek için farklı bir satıra gidin.

7. ConcurrencyWalkthrough'ın çalışan formuna geçiş.

8. Formda ilk kayıtta (**ALFKI),** **ContactName'i** **Maria Anders1 olarak değiştirir.**

9. **Kaydet** düğmesini seçin.

     Eşzamanlılık hatası oluştu ve ileti kutusu görüntülenir.

   **Hayır'ı** seçmek güncelleştirmeyi iptal eder ve veri kümesi şu anda veritabanında olan değerlerle güncelleştirmeyi sağlar. **Evet'i** seçmek önerilen değeri veritabanına yazar.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
