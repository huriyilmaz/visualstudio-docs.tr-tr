---
title: Ekleme/güncelleştirme/silme davranışını özelleştirme
description: Bu kılavuzda, linq (Language-Integrated Query) kullanarak varlık sınıflarının ekleme, güncelleştirme ve silme davranışını SQL araçları Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b2b0aa8b3f7a80212ac608fceb249e8243919e68
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133977906"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>Adım adım kılavuz: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme

LINQ to SQL [araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) veritabanındaki nesneleri temel alan LINQ to SQL sınıfları (varlık sınıfları) oluşturmak ve düzenlemek için görsel bir tasarım yüzeyi sağlar. linq [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)kullanarak, veritabanlarına erişmek için LINQ SQL kullanabilirsiniz. Daha fazla bilgi için bkz. [LINQ (Language-Integrated query)](/dotnet/csharp/linq/).

Varsayılan olarak, güncelleştirmeleri gerçekleştirme mantığı çalışma zamanı tarafından LINQ to SQL sağlanır. Çalışma zamanı, tablonun şemasını (sütun tanımları ve birincil anahtar bilgileri) temel alarak varsayılan `Insert` `Update` , ve `Delete` deyimlerini oluşturur. Varsayılan davranışı kullanmak istemiyorsa, güncelleştirme davranışını yapılandırabilir ve veritabanındaki verilerle çalışmak için gerekli eklemeleri, güncelleştirmeleri ve silmeleri gerçekleştirmek üzere belirli saklı yordamlar atabilirsiniz. Bunu, varsayılan davranış oluşturulmazken de (örneğin, varlık sınıflarınızı görünümlere eşleye) de yapabiliriz. Ayrıca, veritabanı saklı yordamlar aracılığıyla tablo erişimi gerektirdiğinde varsayılan güncelleştirme davranışını geçersiz kılabilirsiniz. Daha fazla bilgi için [bkz. Saklı yordamları kullanarak işlemleri özelleştirme.](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures)

> [!NOTE]
> Bu kılavuz, Northwind veritabanı için **InsertCustomer,** **UpdateCustomer** ve **DeleteCustomer** saklı yordamlarının kullanılabilirliğini gerektirir.

Bu kılavuzda, saklı yordamları kullanarak verileri bir veritabanına geri kaydetmeye LINQ to SQL çalışma zamanı davranışını geçersiz kılmak için izlemeli adımları sağlar.

Bu kılavuzda, aşağıdaki görevleri nasıl gerçekleştireceklerini öğrenirsiniz:

- Yeni bir Windows Forms uygulaması oluşturun ve LINQ to SQL bir dosya ekleyin.

- Northwind tablosuna eşlenmiş bir varlık sınıfı `Customers` oluşturun.

- LINQ to SQL sınıfına başvurulan bir nesne LINQ to SQL `Customer` oluşturun.

- sınıfına Windows içeren bir <xref:System.Windows.Forms.DataGridView> Form `Customer` oluşturun.

- Form için kaydetme işlevini uygulama.

- <xref:System.Data.Linq.DataContext>O/R Tasarımcısı'na saklı **yordamlar ekleyerek yöntemler oluşturun.**

- Ekleme, `Customer` güncelleştirme ve silme işlemleri gerçekleştirmek için saklı yordamları kullanmak üzere sınıfını yapılandırma.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. Yerel VERITABANınız yoksa, SQL Server Express sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Bu **Visual Studio Yükleyicisi,** yerel SQL Server Express veri depolama ve işleme iş  yükünün bir parçası olarak veya tek bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (**SQL Server Nesne Gezgini** veri depolama ve işleme iş **yükünün** parçası olarak **Visual Studio Yükleyicisi.)** SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Bir sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/main/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Uygulama oluşturma ve LINQ to SQL ekleme

LINQ to SQL sınıfları ile çalıştığınız ve verileri Windows Form'da görüntüleyerek yeni bir Windows Forms uygulaması oluşturun ve LINQ to SQL Classes dosyası ekleyin.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>Yeni sınıflarını içeren Windows form uygulaması projesi LINQ to SQL için

1. Bu Visual Studio, Dosya menüsünde **Yeni** **dosya'Project.**  >  

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve ardından Masaüstü'Windows **seçin.**

3. Orta bölmede Windows **Forms Uygulaması proje** türünü seçin.

4. Projeye **UpdatingWithSProcsWalkthrough adını ve** ardından Tamam'ı **seçin.**

     **UpdatingWithSProcsWalkthrough** projesi oluşturulur ve **Çözüm Gezgini.**

4. Yeni **Project** Ekle'ye **tıklayın.**

5. LINQ to SQL **Sınıfları şablonuna** tıklayın ve **Ad kutusuna Northwind.dbml** **yazın.**

6. **Ekle**'ye tıklayın.

     Projeye boş LINQ to SQL Classes dosyası (**Northwind.dbml**) eklenir ve **O/R Tasarımcısı** açılır.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Müşteri varlık sınıfını ve nesne veri kaynağını oluşturma

Tabloları LINQ to SQL veya tablolarını O/R Tasarımcısı'na sürükleyerek **Sunucu Gezgini** **Veritabanı Gezgini** **sınıflarını oluşturun.** Sonuç, LINQ to SQL tablolarına eşlene varlık sınıflarına göre oluşturulur. Varlık sınıfları oluşturduklarından sonra, bunlar genel özelliklere sahip diğer sınıflar gibi nesne veri kaynakları olarak kullanılabilir.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Müşteri varlık sınıfı oluşturmak ve bu sınıfla bir veri kaynağı yapılandırmak için

1. Sunucu Gezgini  veya Veritabanı Gezgini'da, Northwind örnek  veritabanının SQL Server müşteri tablosunda Müşteri tablosu'SQL Server bulun. 

2. Müşteriler **düğümünü** bir **Sunucu Gezgini** **veya Veritabanı Gezgini** **O/R Tasarımcısı yüzeyine* sürükleyin.

     Customer adlı bir **varlık** sınıfı oluşturulur. Customers tablosunda sütunlara karşılık gelen özelliklere sahiptir. Varlık sınıfı Customer **(Müşteriler** değil) olarak **adlandırılmıştır** çünkü Customers tablosundan tek bir müşteriyi temsil eder.

    > [!NOTE]
    > Bu yeniden başlatma davranışı *çoğullaştırma olarak adlandırılan bir davranıştır.* Seçenekler iletişim kutusunda aç veya [kapatabilirsiniz.](../ide/reference/options-dialog-box-visual-studio.md) Daha fazla bilgi için [bkz. Nasıl kullanılır: Çoğullaştırmayı açma ve kapatma (O/R Tasarımcısı)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. Projeyi **derlemek için** Derleme menüsünde **GüncelleştirwithSProcsWalkthrough** seçeneğine tıklayın.

4. Veri Kaynakları **penceresini açmak** için Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

5. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

6. Veri **Kaynağı** Türü **Seçin sayfasında Nesne'ye ve** ardından Sonraki'ye **tıklayın.**

7. **UpdatingwithSProcsWalkthrough düğümünü** genişletin ve **Customer** sınıfını bulup seçin.

    > [!NOTE]
    > Customer **sınıfı** kullanılamıyorsa, sihirbazı iptal edin, projeyi derlemeyi ve sihirbazı yeniden çalıştırın.
8. Veri **kaynağını** oluşturmak için Son'a tıklayın ve **Müşteri** varlık sınıfını Veri Kaynakları **penceresine** ekleyin.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Veri Koruma Formu'Windows müşteri verilerini görüntülemek için DataGridView oluşturma

Veri Kaynakları penceresindeki veri kaynağı öğelerini LINQ to SQL Form'a sürükleyerek **varlık** sınıflarına Windows oluşturun.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Varlık sınıflarını bağlı denetimler eklemek için

1. **Form1'i** Tasarım görünümü.

2. Veri **Kaynakları penceresinden** Müşteri **düğümünü** **Form1'e sürükleyin.**

    > [!NOTE]
    > Veri Kaynakları **penceresini görüntülemek için** Veri menüsünde Veri Kaynaklarını **Göster'e** tıklayın. 

3. Kod **Düzenleyicisi'nde Form1'i** açın.

4. Aşağıdaki kodu forma, forma genel, belirli bir yöntemin dışında, ancak sınıfının içine `Form1` ekleyin:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5. Olay için bir olay `Form_Load` işleyicisi oluşturun ve aşağıdaki kodu işleyiciye ekleyin:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>Kaydetme işlevini uygulama

Varsayılan olarak kaydet düğmesi etkin değildir ve kaydetme işlevi uygulanmaz. Ayrıca, nesne veri kaynakları için veriye bağlı denetimler oluşturulduğunda değiştirilen verileri veritabanına kaydetmek için kod otomatik olarak eklenmez. Bu bölümde kaydet düğmesinin nasıl etkinleştirilip nesneler için kaydetme işlevinin LINQ to SQL açıktır.

### <a name="to-implement-save-functionality"></a>Kaydetme işlevini uygulamak için

1. **Form1'i** Tasarım görünümü.

2. **CustomerBindingNavigator'da** (disket simgesi olan düğme) kaydet düğmesini seçin.

3. Özellikler **penceresinde** Etkin özelliğini True **olarak** **ayarlayın.**

4. Bir olay işleyicisi oluşturmak ve Kod Düzenleyicisi'ne geçmek için kaydet düğmesine çift tıklayın.

5. Kaydet düğmesi olay işleyicisine aşağıdaki kodu ekleyin:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Güncelleştirmeleri (eklemeler, güncelleştirmeler ve silmeler) gerçekleştirmek için varsayılan davranışı geçersiz kılın

### <a name="to-override-the-default-update-behavior"></a>Varsayılan güncelleştirme davranışını geçersiz kılmak için

1. Çalışma LINQ to SQL **O/R Tasarımcısı'nda açın.** (dosyanın içinde **Northwind.dbml** dosyasına **çift Çözüm Gezgini.)**

2. Sunucu Gezgini  veya **Veritabanı Gezgini'** içinde Northwind veritabanları Saklı  Yordamlar düğümünü genişletin ve **InsertCustomers**, **UpdateCustomers** ve **DeleteCustomers** saklı yordamlarını bulun.

3. Üç saklı yordam da **O/R Tasarımcısı'na sürükleyin.**

     Saklı yordamlar yöntemler bölmesine yöntemler olarak <xref:System.Data.Linq.DataContext> eklenir. Daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md).

4. O/R **Tasarımcısı'nda** Müşteri varlık **sınıfını seçin.**

5. Özellikler **penceresinde** Ekle **özelliğini** seçin.

6. Davranışı Yapılandır iletişim kutusunu açmak için Çalışma Zamanı **Kullan'ın** yanındaki üç nokta (**...**) **seçeneğine** tıklayın.

7. **Özelleştir**'i seçin.

8. Özelleştir **listesinde InsertCustomers** **yöntemini** seçin.

9. Seçili **Sınıf ve** Davranış için yapılandırmayı kaydetmek üzere Uygula'ya tıklayın.

    > [!NOTE]
    > Her değişiklik sonrasında Uygula'ya tıklarken her sınıf/davranış bileşimi **için** davranışı yapılandırmaya devam edin. Uygula'ya tıklamadan önce sınıfı veya davranışı **değiştirirsanız,** değişiklikleri uygulama fırsatı sağlayan bir uyarı iletişim kutusu görüntülenir.

10. Davranış **listesinde** **Güncelleştir'i** seçin.

11. **Özelleştir**'i seçin.

12. Özelleştir **listesinde UpdateCustomers** **yöntemini** seçin.

     Yöntem Bağımsız Değişkenleri **ve Sınıf Özellikleri** listesini **inceler** ve tablodaki bazı sütunlar için iki Yöntem Bağımsız Değişkeni ve **iki** Sınıf Özelliği olduğunu fark etmek.  Bu, değişiklikleri izlemenizi ve eşzamanlılık ihlallerini kontrollayan deyimler oluşturmanızı kolaylaştırır.

13. Original_CustomerID **bağımsız** değişkenlerini **CustomerID (Özgün) sınıf özelliğiyle** eşler.

    > [!NOTE]
    > Varsayılan olarak, adlar eşlence yöntem bağımsız değişkenleri sınıf özellikleriyle eşler. Özellik adları değiştirilirse ve tablo ile varlık sınıfı arasında artık eşleşmezse, **O/R Tasarımcısı** doğru eşlemeyi belirleyemeyecekse eşlemek için eşdeğer sınıf özelliğini seçmeniz gerekir. Ayrıca, yöntem bağımsız değişkenlerini eşlemek için geçerli sınıf özellikleri yoksa, Sınıf Özellikleri **değerini** **(Hiçbiri) olarak ayarlayın.**

14. Seçili **Sınıf ve** Davranış için yapılandırmayı kaydetmek üzere Uygula'ya tıklayın.

15. Davranış **listesinde** **Sil'i** seçin.

16. **Özelleştir**'i seçin.

17. Özelleştir **listesinde DeleteCustomers** **yöntemini** seçin.

18. Original_CustomerID **bağımsız** değişkenlerini **CustomerID (Özgün) sınıf özelliğiyle** eşler.

19. **Tamam**'a tıklayın.

> [!NOTE]
> Bu kılavuz için sorun oluşturmasa da, eklemeler ve güncelleştirmeler sırasında LINQ to SQL tarafından oluşturulan değerleri kimlik (otomatik artırma), rowguidcol (veritabanı tarafından oluşturulan GUID) ve zaman damgası sütunları için otomatik olarak işlemektedir. Diğer sütun türlerinde veritabanı tarafından oluşturulan değerler beklenmedik şekilde null değere neden olur. Veritabanı tarafından oluşturulan değerleri geri dönmek için şu değerlerden birini elle olarak ve olarak <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> `true` ayarlamalısınız: <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)veya [AutoSync.OnUpdate.](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)

## <a name="test-the-application"></a>Uygulamayı test edin

**UpdateCustomers** saklı yordamının veritabanındaki müşteri kaydını doğru şekilde güncelleştiren uygulamayı yeniden çalıştırın.

1. **F5 tuşuna basın.**

2. Güncelleştirme davranışını test etmek için kılavuzda bir kaydı değiştirme.

3. Ekleme davranışını test etmek için yeni bir kayıt ekleyin.

4. Değişiklikleri veritabanına geri kaydetmek için kaydet düğmesine tıklayın.

5. Formu kapatın.

6. **F5 tuşuna** basın ve güncelleştirilmiş kaydın ve yeni eklenen kaydın kalıcı olduğunu doğrulayın.

7. Silme davranışını test etmek için 3. adımda oluşturduğunuz yeni kaydı silin.

8. Değişiklikleri göndermek ve silinen kaydı veritabanından kaldırmak için kaydet düğmesine tıklayın.

9. Formu kapatın.

10. **F5 tuşuna** basın ve silinen kaydın veritabanından kaldırılmış olduğunu doğrulayın.

    > [!NOTE]
    > Uygulamanız SQL Server Express Edition kullanıyorsa, veritabanı dosyasının **Çıkış** Dizinine Kopyala özelliğinin değerine bağlı olarak, 10. adımda **F5** tuşuna bassanız değişiklikler görüne görünebilir.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, varlık sınıflarını oluşturduk sonra gerçekleştirmek istediğiniz LINQ to SQL vardır. Bu uygulamada gerçekleştirebilirsiniz bazı geliştirmeler aşağıdakileri içerir:

- Güncelleştirmeler sırasında eşzamanlılık denetimi uygulama. Bilgi için bkz. [İyimser Eşzamanlılık: genel bakış.](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview)

- Verileri filtrelemek için LINQ sorguları ekleyin. Bilgi için [bkz. LINQ sorgularına giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL araçları Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext metotları](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapacaksınız: Güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL sorguları](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)
