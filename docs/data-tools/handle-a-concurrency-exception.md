---
title: Bir eşzamanlılık özel durumunu işleme
ms.date: 09/11/2017
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6096e8919d21a93af0dbf6beea2f263bd500d26c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648438"
---
# <a name="handle-a-concurrency-exception"></a>Bir eşzamanlılık özel durumunu işleme

Eşzamanlılık özel durumları (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) iki kullanıcı aynı anda bir veritabanında aynı verileri değiştirmeye çalıştıklarında tetiklenir. Bu kılavuzda, bir <xref:System.Data.DBConcurrencyException> nasıl yakalayacağınızı gösteren bir Windows uygulaması oluşturacaksınız, hataya neden olan satırı nasıl bulabileceğinizi ve nasıl işleyeceğinizi gösteren bir strateji öğreneceksiniz.

Bu izlenecek yol, aşağıdaki işlem boyunca size kılavuzluk eden bir işlemdir:

1. Yeni bir **Windows Forms uygulama** projesi oluşturun.

2. Northwind Customers tablosunu temel alan yeni bir veri kümesi oluşturun.

3. Verileri göstermek için <xref:System.Windows.Forms.DataGridView> bir form oluşturun.

4. Northwind veritabanındaki Customers tablosunun verileri ile bir veri kümesini doldur.

5. Müşteriler tablosunun verilerine erişmek ve bir kaydı değiştirmek için **Sunucu Gezgini** Içindeki **tablo verilerini göster** özelliğini kullanın.

6. Aynı kaydı farklı bir değerle değiştirin, veri kümesini güncelleştirin ve değişiklikleri veritabanına yazmayı deneyin, bu da bir eşzamanlılık hatası oluşur.

7. Hatayı Yakalayın, ardından kaydın farklı sürümlerini görüntüleyin, kullanıcının devam edip etmediğini ve veritabanını güncelleştirip güncelleştirmeyeceğini belirlemesine izin verir veya güncelleştirmeyi iptal edin.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi**aracılığıyla yükleyin. **Visual Studio yükleyicisi**, SQL Server Express LocalDB 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

Yeni bir Windows Forms uygulaması oluşturarak başlayın:

1. Visual Studio 'da, **Dosya** menüsünde **Yeni**  > **projesi**' ni seçin.

2. Sol bölmedeki **görsel C#**  veya **Visual Basic** ' i genişletin ve ardından **Windows Masaüstü**' nü seçin.

3. Orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **ConcurrencyWalkthrough**olarak adlandırın ve ardından **Tamam**' ı seçin.

     **ConcurrencyWalkthrough** projesi oluşturulup **Çözüm Gezgini**eklenir ve tasarımcıda yeni bir form açılır.

## <a name="create-the-northwind-dataset"></a>Northwind veri kümesini oluşturma

Sonra, **NorthwindDataSet**adlı bir veri kümesi oluşturun:

1. **Veri** menüsünde **Yeni veri kaynağı Ekle**' yi seçin.

   Veri kaynağı Yapılandırma Sihirbazı açılır.

2. **Veri kaynağı türü seçin** ekranında **veritabanı**' nı seçin.

   ![Visual Studio 'da veri kaynağı Yapılandırma Sihirbazı](media/data-source-configuration-wizard.png)

3. Kullanılabilir bağlantılar listesinden Northwind örnek veritabanına bir bağlantı seçin. Bağlantı listesinde bağlantı yoksa, **Yeni bağlantı**' yı seçin.

    > [!NOTE]
    > Bir yerel veritabanı dosyasına bağlanıyorsanız, dosyayı projenize eklemek isteyip istemediğiniz sorulduğunda **Hayır** ' ı seçin.

4. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** ekranında, **İleri**' yi seçin.

5. **Tablolar** düğümünü genişletin ve **müşteriler** tablosunu seçin. Veri kümesinin varsayılan adı **NorthwindDataSet**olmalıdır.

6. Veri kümesini projeye eklemek için **son** ' u seçin.

## <a name="create-a-data-bound-datagridview-control"></a>Veri bağlantılı DataGridView denetimi oluşturma

Bu bölümde, **müşteriler** öğesini **veri kaynakları** penceresinden Windows formunuzun üzerine sürükleyerek bir <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> oluşturursunuz.

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' i seçin.

2. **Veri kaynakları** penceresinde **NorthwindDataSet** düğümünü genişletin ve ardından **Customers** tablosunu seçin.

3. Tablo düğümünde aşağı oku seçin ve ardından açılır listeden **DataGridView** ' i seçin.

4. Tabloyu formunuzun boş bir alanının üzerine sürükleyin.

     **CustomersDataGridView**adlı bir <xref:System.Windows.Forms.DataGridView> denetimi ve **customersbindingnavigator**adlı bir <xref:System.Windows.Forms.BindingNavigator>, <xref:System.Windows.Forms.BindingSource> bağlanan forma eklenir. Bu, sırasıyla NorthwindDataSet 'teki Customers tablosuna bağlanır.

## <a name="test-the-form"></a>Formu test etme

Artık formu, bu noktaya kadar beklenen şekilde davrandığından emin olmak için test edebilirsiniz:

1. Uygulamayı çalıştırmak için **F5** ' i seçin.

     Form, Müşteriler tablosundaki verilerle doldurulmuş bir <xref:System.Windows.Forms.DataGridView> denetimiyle görüntülenir.

2. **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur**' u seçin.

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

Bir güncelleştirme gerçekleştirmeye çalıştığınızda ve bir özel durum ortaya çıktığında, genellikle oluşturulan özel durum tarafından verilen bilgilerle ilgili bir şey yapmak istersiniz. Bu bölümde, veritabanını güncelleştirmeyi deneyen kodu eklersiniz. Ayrıca, başka özel durumlar da ortaya çıkarılan <xref:System.Data.DBConcurrencyException> de işleyebilirsiniz.

> [!NOTE]
> @No__t_0 ve `ProcessDialogResults` yöntemleri daha sonra izlenecek yolda eklenir.

1. @No__t_0 yönteminin altına aşağıdaki kodu ekleyin:

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. @No__t_0 yöntemini, aşağıdaki gibi görünmesi için `UpdateDatabase` yöntemini çağırmak üzere değiştirin:

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Kullanıcı için seçimleri görüntüle

Yeni yazdığınız kod, kullanıcıya hata bilgilerini göstermek için `CreateMessage` yordamını çağırır. Bu izlenecek yol için, kaydın farklı sürümlerini kullanıcıya göstermek üzere bir ileti kutusu kullanın. Bu, kullanıcının değişikliklerle ilgili kaydın üzerine yazılıp yazılmayacağını veya düzenlemeyi iptal edip etmediğini seçmesini sağlar. Kullanıcı, ileti kutusunda bir seçenek seçtiğinde (bir düğmeye tıkladığında), yanıt `ProcessDialogResult` yöntemine geçirilir.

**Kod düzenleyicisine**aşağıdaki kodu ekleyerek iletiyi oluşturun. @No__t_0 yönteminin altına bu kodu girin:

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Kullanıcının yanıtını işle

Kullanıcının ileti kutusuna yanıtını işlemek için de kod gerekir. Seçenekler, önerilen değişiklikle veritabanındaki geçerli kaydın üzerine yazar veya yerel değişiklikleri iptal edebilir ve veri tablosunu veritabanında Şu anda olan kayıtla yeniler. Kullanıcı **Evet**' i seçerse <xref:System.Data.DataTable.Merge%2A> yöntemi *PreserveChanges* bağımsız değişkeniyle **doğru**olarak ayarlanır. Bu, kaydın orijinal sürümü artık veritabanındaki kayıtla eşleştiğinden güncelleştirme denemesinin başarılı olmasına neden olur.

Önceki bölümde eklenmiş olan kodun altına aşağıdaki kodu ekleyin:

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Formu test etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz. Eşzamanlılık ihlalinin benzetimini yapmak için, NorthwindDataSet 'i doldurduktan sonra veritabanındaki verileri değiştirirsiniz.

1. Uygulamayı çalıştırmak için **F5** ' i seçin.

2. Form görüntülendikten sonra çalışır durumda bırakın ve Visual Studio IDE 'ye geçin.

3. **Görünüm** menüsünde **Sunucu Gezgini**' yi seçin.

4. **Sunucu Gezgini**, uygulamanızın kullandığı bağlantıyı genişletin ve **Tablolar** düğümünü genişletin.

5. **Müşteriler** tablosuna sağ tıklayın ve ardından **tablo verilerini göster**' i seçin.

6. İlk kayıtta (**alfki**) **ContactName** öğesini **Maria Anders2**olarak değiştirin.

    > [!NOTE]
    > Değişikliği uygulamak için farklı bir satıra gidin.

7. ConcurrencyWalkthrough 'in çalışan formuna geçiş yapın.

8. Formdaki (**alfki**) ilk kayıtta, **ContactName** öğesini **Maria Anders1**olarak değiştirin.

9. **Kaydet** düğmesini seçin.

     Eşzamanlılık hatası oluşur ve ileti kutusu görüntülenir.

   **Hayır** seçilirse güncelleştirme iptal edilir ve veri kümesini veritabanında Şu anda olan değerlerle günceller. **Evet** seçildiğinde önerilen değer veritabanına yazılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)