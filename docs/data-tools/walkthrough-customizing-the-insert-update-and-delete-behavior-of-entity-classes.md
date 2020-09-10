---
title: Ekleme/güncelleştirme/silme davranışını özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 01fe4cf160ed3a7548fd8b8bed003838abee3d04
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741819"
---
# <a name="walkthrough-customize-the-insert-update-and-delete-behavior-of-entity-classes"></a>İzlenecek yol: varlık sınıflarının INSERT, Update ve DELETE davranışını özelleştirme

[Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) , bir veritabanındaki nesneleri temel alan LINQ to SQL sınıfları (varlık sınıfları) oluşturmak ve düzenlemekte kullanabileceğiniz görsel tasarım yüzeyi sağlar. [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)kullanarak, SQL veritabanlarına erışmek için LINQ teknolojisini kullanabilirsiniz. Daha fazla bilgi için bkz. [LINQ (dil Ile tümleşik sorgu)](/dotnet/csharp/linq/).

Varsayılan olarak, güncelleştirmeleri gerçekleştirme mantığı LINQ to SQL çalışma zamanı tarafından sağlanır. Çalışma zamanı, `Insert` `Update` `Delete` tablonun şemasına göre varsayılan, ve deyimlerini oluşturur (sütun tanımları ve birincil anahtar bilgileri). Varsayılan davranışı kullanmak istemiyorsanız, güncelleştirme davranışını yapılandırabilir ve veritabanındaki verilerle çalışmak için gerekli olan ekleme, güncelleştirme ve silme işlemlerini gerçekleştirmek için belirli saklı yordamları belirtebilirsiniz. Bunun yanı sıra, varsayılan davranış oluşturulmayan, örneğin varlık sınıflarınız görünümlerle eşlenme olduğunda da yapabilirsiniz. Ayrıca, veritabanı saklı yordamlar üzerinden tablo erişimi gerektirdiğinde varsayılan güncelleştirme davranışını geçersiz kılabilirsiniz. Daha fazla bilgi için bkz. [saklı yordamları kullanarak Işlemleri özelleştirme](/dotnet/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures).

> [!NOTE]
> Bu izlenecek yol, Northwind veritabanı için **InsertCustomer**, **UpdateCustomer**ve **DeleteCustomer** saklı yordamlarının kullanılabilir olmasını gerektirir.

Bu izlenecek yol, depolanan yordamları kullanarak verileri veritabanına geri kaydetmek için varsayılan LINQ to SQL çalışma zamanı davranışını geçersiz kılmak için izlemeniz gereken adımları sağlar.

Bu kılavuzda, aşağıdaki görevlerin nasıl gerçekleştirileceğini öğreneceksiniz:

- Yeni bir Windows Forms uygulaması oluşturun ve buna bir LINQ to SQL dosyası ekleyin.

- Northwind tablosuna eşlenmiş bir varlık sınıfı oluşturun `Customers` .

- LINQ to SQL sınıfına başvuran bir nesne veri kaynağı oluşturun `Customer` .

- Sınıfına bağlanan bir içeren bir Windows formu oluşturun <xref:System.Windows.Forms.DataGridView> `Customer` .

- Form için kaydetme işlevini uygulayın.

- <xref:System.Data.Linq.DataContext> **O/R tasarımcısına**saklı yordamlar ekleyerek Yöntemler oluşturun.

- `Customer`Ekleme, güncelleştirme ve silme işlemlerini gerçekleştirmek üzere saklı yordamları kullanmak için sınıfını yapılandırın.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi**aracılığıyla yükleyin. **Visual Studio yükleyicisi**, SQL Server Express LocalDB 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (**SQL Server Nesne Gezgini** , **Visual Studio yükleyicisi** **veri depolama ve işleme** iş yükünün bir parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Uygulama oluşturma ve LINQ to SQL sınıfları ekleme

LINQ to SQL sınıflarıyla çalıştığınızdan ve verileri bir Windows formunda görüntüleyerek, yeni bir Windows Forms uygulaması oluşturun ve bir LINQ to SQL Classes dosyası ekleyin.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-new-windows-forms-application-project-that-contains-linq-to-sql-classes"></a>LINQ to SQL sınıfları içeren yeni bir Windows Forms uygulama projesi oluşturmak için

1. Visual Studio 'da, **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.

2. Sol bölmedeki **Visual C#** veya **Visual Basic** genişletip **Windows Masaüstü**' nü seçin.

3. Orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **UpdatingwithSProcsWalkthrough**olarak adlandırın ve ardından **Tamam**' ı seçin.

     **UpdatingwithSProcsWalkthrough** projesi oluşturulur ve **Çözüm Gezgini**eklenir.

4. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

5. **LINQ to SQL sınıfları** şablonuna tıklayın ve **ad** kutusuna **Northwind. dbml** yazın.

6. **Ekle**'ye tıklayın.

     Boş bir LINQ to SQL Classes dosyası (**Northwind. dbml**) projeye eklenir ve **O/R Tasarımcısı** açılır.

## <a name="create-the-customer-entity-class-and-object-data-source"></a>Müşteri varlık sınıfı ve nesne veri kaynağı oluşturma

**Sunucu Gezgini** veya **veritabanı Gezgini** tabloları **O/R tasarımcısına**sürükleyerek veritabanı tablolarıyla eşlenen LINQ to SQL sınıflar oluşturun. Sonuç, veritabanındaki tablolarla eşlenen LINQ to SQL varlık sınıflarıdır. Varlık sınıfları oluşturduktan sonra, yalnızca ortak özelliklerine sahip diğer sınıflar gibi nesne veri kaynakları olarak kullanılabilirler.

### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Bir müşteri varlık sınıfı oluşturmak ve bir veri kaynağını onunla yapılandırmak için

1. **Sunucu Gezgini** veya **veritabanı Gezgini**içinde, Northwind örnek veritabanının SQL Server sürümünde **Customer** tablosunu bulun.

2. **Müşteriler** düğümünü **Sunucu Gezgini** veya **veritabanı Gezgini** , **O/R tasarımcı* yüzeyine sürükleyin.

     **Müşteri** adlı bir varlık sınıfı oluşturulur. Müşteriler tablosundaki sütunlara karşılık gelen özelliklere sahiptir. Müşteriler tablosundan tek bir müşteriyi temsil ettiğinden, varlık sınıfı **Müşteri** olarak adlandırılır ( **müşteriler**değil).

    > [!NOTE]
    > Bu yeniden adlandırma davranışı *çoğullaştırma*olarak adlandırılır. [Seçenekler iletişim kutusunda](../ide/reference/options-dialog-box-visual-studio.md)açılıp kapatılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: plurseli açma ve kapatma (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. Projeyi derlemek için **Build** (Oluştur) menüsünde **UpdatingwithSProcsWalkthrough derleme** ' ye tıklayın.

4. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

5. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

6. **Veri kaynağı türü seçin** sayfasında **nesne** ' ye tıklayın ve ardından **İleri**' ye tıklayın.

7. **UpdatingwithSProcsWalkthrough** düğümünü genişletin ve **Müşteri** sınıfını bulup seçin.

    > [!NOTE]
    > **Müşteri** sınıfı kullanılabilir değilse, Sihirbazı iptal edin, projeyi derleyin ve Sihirbazı yeniden çalıştırın.
8. Veri kaynağını oluşturmak ve **veri kaynakları** penceresine **Müşteri** varlık sınıfını eklemek için **son** ' a tıklayın.

## <a name="create-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Bir Windows formunda müşteri verilerini göstermek için bir DataGridView oluşturma

Veri **kaynakları** penceresinden bir Windows Form üzerine LINQ to SQL veri kaynağı öğelerini sürükleyerek varlık sınıflarına bağlanan denetimler oluşturun.

### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Varlık sınıflarına bağlanan denetimler eklemek için

1. Tasarım görünümü 'da **Form1** ' i açın.

2. **Veri kaynakları** penceresinde, **Müşteri** düğümünü **Form1**üzerine sürükleyin.

    > [!NOTE]
    > **Veri kaynakları** penceresini görüntülemek için **veri** menüsünde **veri kaynaklarını göster** ' e tıklayın.

3. Kod düzenleyicisinde **Form1** ' i açın.

4. Aşağıdaki kodu, genel olarak forma, belirli bir yöntemin dışına, ancak sınıfının içine ekleyin `Form1` :

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();
    ```

5. Olay için bir olay işleyicisi oluşturun `Form_Load` ve aşağıdaki kodu işleyiciye ekleyin:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;
    ```

## <a name="implement-save-functionality"></a>Kaydetme işlevini Uygula

Varsayılan olarak, Kaydet düğmesi etkin değildir ve Kaydet işlevi uygulanmaz. Ayrıca, nesne veri kaynakları için veri bağlantılı denetimler oluşturulduğunda, değiştirilen verileri veritabanına kaydetmek için de kod otomatik olarak eklenmez. Bu bölümde, Kaydet düğmesinin nasıl etkinleştirileceği ve LINQ to SQL nesneleri için kaydetme işlevlerinin nasıl uygulanacağı açıklanmaktadır.

### <a name="to-implement-save-functionality"></a>Kaydetme işlevini uygulamak için

1. Tasarım görünümü 'da **Form1** ' i açın.

2. **CustomerBindingNavigator** (disket simgesini içeren düğme) üzerinde Kaydet düğmesini seçin.

3. **Özellikler** penceresinde, **etkin** özelliği **true**olarak ayarlayın.

4. Kaydet düğmesine çift tıklayarak bir olay işleyicisi oluşturun ve kod düzenleyicisine geçiş yapın.

5. Kaydet düğmesi olay işleyicisine aşağıdaki kodu ekleyin:

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="override-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Güncelleştirmeleri gerçekleştirmek için varsayılan davranışı geçersiz kılın (ekler, güncelleştirmeler ve siler)

### <a name="to-override-the-default-update-behavior"></a>Varsayılan güncelleştirme davranışını geçersiz kılmak için

1. **U/R tasarımcısında**LINQ to SQL dosyasını açın. ( **Çözüm Gezgini** **Northwind. dbml** dosyasına çift tıklayın.)

2. **Sunucu Gezgini** veya **veritabanı Gezgini**' de, Northwind veritabanları **saklı yordamları** düğümünü genişletin ve **InsertCustomers**, **UpdateCustomers**ve **DeleteCustomers** saklı yordamlarını bulun.

3. Tüm üç saklı yordamı **O/R tasarımcısına**sürükleyin.

     Saklı yordamlar Yöntemler bölmesine yöntemler olarak eklenir <xref:System.Data.Linq.DataContext> . Daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. **O/R tasarımcısında** **Müşteri** varlık sınıfını seçin.

5. **Özellikler** penceresinde **Insert** özelliğini seçin.

6. **Çalışma zamanı kullan** ' ın yanındaki üç nokta (**...**) simgesine tıklayarak **davranışı Yapılandır** iletişim kutusunu açın.

7. **Özelleştir**'i seçin.

8. **Özelleştir** listesinden **InsertCustomers** yöntemini seçin.

9. Seçili sınıf ve davranışa ait yapılandırmayı kaydetmek için **Uygula** ' ya tıklayın.

    > [!NOTE]
    > Her bir değişiklik yaptıktan sonra **Uygula** ' ya tıkladığınızda her bir sınıf/davranış birleşiminin davranışını yapılandırmaya devam edebilirsiniz. **Uygula**' ya tıklamadan önce sınıfı veya davranışı değiştirirseniz, herhangi bir değişiklik uygulamaya fırsat sağlayan bir uyarı iletişim kutusu görüntülenir.

10. **Davranış** listesinden **Güncelleştir** ' i seçin.

11. **Özelleştir**'i seçin.

12. **Özelleştir** listesinden **UpdateCustomers** yöntemini seçin.

     **Yöntem bağımsız değişkenlerinin** ve **Sınıf özelliklerinin** listesini inceleyin ve tablodaki bazı sütunlar Için iki **Yöntem bağımsız değişkeni** ve iki **sınıf özelliği** olduğuna dikkat edin. Bu, değişiklikleri izlemenizi ve eşzamanlılık ihlallerini denetleyen deyimler oluşturmayı kolaylaştırır.

13. **Original_CustomerID** yöntemi bağımsız değişkenini **CustomerID (orijinal)** sınıf özelliği ile eşleyin.

    > [!NOTE]
    > Varsayılan olarak, yöntem bağımsız değişkenleri, adlar eşleşiyorsa sınıf özellikleriyle eşlenir. Özellik adları değiştirilirse ve artık tablo ve varlık sınıfı arasında eşleşmezse, **O/R Tasarımcısı** doğru eşlemeyi belirleyememesi durumunda eşlenecek eşdeğer sınıf özelliğini seçmeniz gerekebilir. Ayrıca, yöntem bağımsız değişkenlerinin eşlenecek geçerli sınıf özellikleri yoksa, **sınıf özellikleri** değerini **(yok)** olarak ayarlayabilirsiniz.

14. Seçili sınıf ve davranışa ait yapılandırmayı kaydetmek için **Uygula** ' ya tıklayın.

15. **Davranış** listesinden **Sil** ' i seçin.

16. **Özelleştir**'i seçin.

17. **Özelleştir** listesinde **DeleteCustomers** yöntemini seçin.

18. **Original_CustomerID** yöntemi bağımsız değişkenini **CustomerID (orijinal)** sınıf özelliği ile eşleyin.

19. **Tamam**'a tıklayın.

> [!NOTE]
> Bu izlenecek yol için bir sorun olmasa da, LINQ to SQL kimlik (otomatik artırma), ROWGUIDCOL (veritabanı tarafından üretilen GUID) ve ekleme ve güncelleştirme sırasında zaman damgası sütunları için veritabanı tarafından oluşturulan değerleri otomatik olarak işlediğini belirten bir değer. Diğer sütun türlerindeki veritabanı tarafından oluşturulan değerler beklenmedik bir şekilde null değer oluşmasına neden olur. Veritabanı tarafından oluşturulan değerleri döndürmek için, aşağıdakilerden birine el ile ve olarak ayarlamanız gerekir <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> `true` <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> : [oto Sync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [oto Sync. OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)veya [oto Sync. OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="test-the-application"></a>Uygulamayı test etme

**UpdateCustomers** saklı yordamının veritabanındaki müşteri kaydını doğru bir şekilde güncelleştirdiğini doğrulamak için uygulamayı yeniden çalıştırın.

1. **F5**tuşuna basın.

2. Kılavuzdaki bir kaydı değiştirerek güncelleştirme davranışını test edin.

3. Ekleme davranışını test etmek için yeni bir kayıt ekleyin.

4. Değişiklikleri veritabanına geri kaydetmek için Kaydet düğmesine tıklayın.

5. Formu kapatın.

6. **F5** tuşuna basın ve güncelleştirilmiş kaydın ve yeni eklenen kaydın kalıcı olduğunu doğrulayın.

7. Adım 3 ' te oluşturduğunuz yeni kaydı silme davranışını test etmek için silin.

8. Değişiklikleri göndermek ve silinen kaydı veritabanından kaldırmak için Kaydet düğmesine tıklayın.

9. Formu kapatın.

10. **F5** tuşuna basın ve silinen kaydın veritabanından kaldırıldığını doğrulayın.

    > [!NOTE]
    > Uygulamanız, veritabanı dosyasının **Çıkış Dizinine Kopyala** özelliğinin değerine bağlı olarak SQL Server Express Edition kullanıyorsa, adım 10 ' da **F5** tuşuna bastığınızda değişiklikler görünmeyebilir.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, LINQ to SQL varlık sınıfları oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu uygulamada yapabileceğiniz bazı geliştirmeler şunları içerir:

- Güncelleştirmeler sırasında eşzamanlılık denetimini uygulayın. Bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](/dotnet/framework/data/adonet/sql/linq/optimistic-concurrency-overview).

- Verileri filtrelemek için LINQ sorguları ekleyin. Bilgi için bkz. [LINQ Sorgularına Giriş (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext metotları](../data-tools/datacontext-methods-o-r-designer.md)
- [Nasıl yapılır: güncelleştirme, ekleme ve silme işlemleri gerçekleştirmek için saklı yordamlar atama](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ - SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [LINQ to SQL sorguları](/dotnet/framework/data/adonet/sql/linq/linq-to-sql-queries)
