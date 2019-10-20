---
title: 'İzlenecek yol: varlık sınıflarının INSERT, Update ve DELETE davranışlarını özelleştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9901d917de2babf4992519ffe6b360454542aad1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602567"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>İzlenecek yol: varlık sınıflarının INSERT, Update ve DELETE davranışını özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) , bir veritabanındaki nesneleri temel alan [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sınıfları (varlık sınıfları) oluşturmak ve düzenlemekte kullanabileceğiniz görsel tasarım yüzeyi sağlar. [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)kullanarak, SQL veritabanlarına erışmek için LINQ teknolojisini kullanabilirsiniz. Daha fazla bilgi için bkz. [LINQ (dil Ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).

 Varsayılan olarak, güncelleştirmeleri gerçekleştirme mantığı [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] çalışma zamanı tarafından sağlanır. Çalışma zamanı, tablonun şemasına göre varsayılan INSERT, Update ve delete deyimlerini oluşturur (sütun tanımları ve birincil anahtar bilgileri). Varsayılan davranışı kullanmak istemiyorsanız, güncelleştirme davranışını yapılandırabilir ve veritabanındaki verilerle çalışmak için gerekli olan ekleme, güncelleştirme ve silme işlemlerini gerçekleştirmek için belirli saklı yordamları belirtebilirsiniz. Bunun yanı sıra, varsayılan davranış oluşturulmayan, örneğin varlık sınıflarınız görünümlerle eşlenme olduğunda da yapabilirsiniz. Ayrıca, veritabanı saklı yordamlar üzerinden tablo erişimi gerektirdiğinde varsayılan güncelleştirme davranışını geçersiz kılabilirsiniz. Daha fazla bilgi için bkz. [saklı yordamları kullanarak Işlemleri özelleştirme](https://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a).

> [!NOTE]
> Bu izlenecek yol, Northwind veritabanı için **InsertCustomer**, **UpdateCustomer**ve **DeleteCustomer** saklı yordamlarının kullanılabilir olmasını gerektirir.

 Bu izlenecek yol, depolanan yordamları kullanarak verileri veritabanına geri kaydetmeye yönelik varsayılan LINQ to SQL çalışma zamanı davranışını geçersiz kılmak için izlemeniz gereken adımları sağlar.

 Bu kılavuzda, aşağıdaki görevlerin nasıl gerçekleştirileceğini öğreneceksiniz:

- Yeni bir Windows Forms uygulaması oluşturun ve buna bir [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] dosyası ekleyin.

- Northwind Customers tablosuna eşlenmiş bir varlık sınıfı oluşturun.

- LINQ to SQL Customer sınıfına başvuran bir nesne veri kaynağı oluşturun.

- Müşteri sınıfına bağlanan bir <xref:System.Windows.Forms.DataGridView> içeren bir Windows formu oluşturun.

- Form için kaydetme işlevini uygulayın.

- @No__t_1 saklı yordamlar ekleyerek <xref:System.Data.Linq.DataContext> Yöntemler oluşturun.

- Müşteri sınıfını, ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için saklı yordamları kullanacak şekilde yapılandırın.

## <a name="prerequisites"></a>Prerequisites
 Bu yönergeyi tamamlamak için aşağıdakilere ihtiyacınız vardır:

- Northwind örnek veritabanının SQL Server sürümüne erişim.

- Northwind veritabanı için **InsertCustomer**, **UpdateCustomer**ve **DeleteCustomer** saklı yordamları.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>Uygulama oluşturma ve LINQ to SQL sınıfları ekleme
 @No__t_0 sınıflarla çalışacak ve verileri bir Windows formunda görüntüleyecek, yeni bir Windows Forms uygulaması oluşturun ve bir LINQ to SQL Classes dosyası ekleyin.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>LINQ to SQL sınıfları içeren yeni bir Windows uygulaması projesi oluşturmak için

1. **Dosya** menüsünden Yeni bir proje oluşturun.

2. Projeyi **UpdatingwithSProcsWalkthrough**olarak adlandırın.

    > [!NOTE]
    > @No__t_0 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ve C# projelerinde desteklenir. Bu nedenle, yeni projeyi bu dillerden birinde oluşturun.

3. **Windows Forms uygulama** şablonuna tıklayıp **Tamam**' a tıklayın. Daha fazla bilgi için bkz. [Istemci uygulamaları](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     UpdatingwithSProcsWalkthrough projesi oluşturulup **Çözüm Gezgini**eklenir.

4. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

5. **LINQ to SQL sınıfları** şablonuna tıklayın ve **ad** kutusuna **Northwind. dbml** yazın.

6. **Ekle**'yi tıklatın.

     Boş bir LINQ to SQL Classes dosyası (Northwind. dbml) projeye eklenir ve [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] açılır.

## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Müşteri varlık sınıfı ve nesne veri kaynağı oluşturma
 Tabloları **Sunucu Gezgini** / [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]**veritabanı Gezgini** sürükleyerek veritabanı tablolarıyla eşlenen [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sınıflar oluşturun. Sonuç, veritabanındaki tablolarla eşlenen LINQ to SQL varlık sınıflarıdır. Varlık sınıfları oluşturduktan sonra, yalnızca ortak özelliklerine sahip diğer sınıflar gibi nesne veri kaynakları olarak kullanılabilirler.

#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Bir müşteri varlık sınıfı oluşturmak ve bir veri kaynağını onunla yapılandırmak için

1. **Sunucu Gezgini** /**veritabanı Gezgini**, Northwind örnek veritabanının SQL Server sürümünde Customer tablosunu bulun.

2. **Müşteriler** düğümünü **Sunucu Gezgini** /**veritabanı Gezgini** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] yüzeyine sürükleyin.

     **Müşteri** adlı bir varlık sınıfı oluşturulur. Müşteriler tablosundaki sütunlara karşılık gelen özelliklere sahiptir. Müşteriler tablosundan tek bir müşteriyi temsil ettiğinden, varlık sınıfı **Müşteri** olarak adlandırılır ( **müşteriler**değil).

    > [!NOTE]
    > Bu yeniden adlandırma davranışı *çoğullaştırma*olarak adlandırılır. [Seçenekler Iletişim kutusunda](../ide/reference/options-dialog-box-visual-studio.md)açılıp kapatılabilir. Daha fazla bilgi için bkz. [nasıl yapılır: plurseli açma ve kapatma (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).

3. Projeyi derlemek için **Build** (Oluştur) menüsünde **UpdatingwithSProcsWalkthrough derleme** ' ye tıklayın.

4. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

5. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

6. **Veri kaynağı türü seçin** sayfasında **nesne** ' ye tıklayın ve ardından **İleri**' ye tıklayın.

7. **UpdatingwithSProcsWalkthrough** düğümünü genişletin ve **Müşteri** sınıfını bulup seçin.

    > [!NOTE]
    > **Müşteri** sınıfı kullanılabilir değilse, Sihirbazı iptal edin, projeyi derleyin ve Sihirbazı yeniden çalıştırın.

8. Veri kaynağını oluşturmak ve **veri kaynakları** penceresine **Müşteri** varlık sınıfını eklemek için **son** ' a tıklayın.

## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Bir Windows formunda müşteri verilerini göstermek için DataGridView oluşturma
 Veri **kaynakları** penceresinden bir Windows Form üzerine [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] veri kaynağı öğelerini sürükleyerek varlık sınıflarına bağlanan denetimler oluşturun.

#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>Varlık sınıflarına bağlanan denetimler eklemek için

1. Tasarım görünümü 'da Form1 ' i açın.

2. **Veri kaynakları** penceresinde, **Müşteri** düğümünü Form1 üzerine sürükleyin.

    > [!NOTE]
    > **Veri kaynakları** penceresini görüntülemek için **veri** menüsünde **veri kaynaklarını göster** ' e tıklayın.

3. Kod düzenleyicisinde Form1 ' i açın.

4. Aşağıdaki kodu, genel olarak forma, belirli bir yöntemin dışına, ancak Form1 sınıfının içine ekleyin:

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();

    ```

5. @No__t_0 olayı için bir olay işleyicisi oluşturun ve aşağıdaki kodu işleyiciye ekleyin:

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;

    ```

## <a name="implementing-save-functionality"></a>Kaydetme Işlevini uygulama
 Varsayılan olarak, Kaydet düğmesi etkin değildir ve Kaydet işlevi uygulanmaz. Ayrıca, nesne veri kaynakları için veri bağlantılı denetimler oluşturulduğunda, değiştirilen verileri veritabanına kaydetmek için de kod otomatik olarak eklenmez. Bu bölümde, Kaydet düğmesinin nasıl etkinleştirileceği ve [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] nesneleri için kaydetme işlevlerinin nasıl uygulanacağı açıklanmaktadır.

#### <a name="to-implement-save-functionality"></a>Kaydetme işlevini uygulamak için

1. Tasarım görünümü 'da Form1 ' i açın.

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

## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>Güncelleştirme gerçekleştirmeye yönelik varsayılan davranışı geçersiz kılma (ekler, güncelleştirmeler ve siler)

#### <a name="to-override-the-default-update-behavior"></a>Varsayılan güncelleştirme davranışını geçersiz kılmak için

1. @No__t_0 LINQ to SQL dosyasını açın. ( **Çözüm Gezgini** **Northwind. dbml** dosyasına çift tıklayın.)

2. **Sunucu Gezgini** /**veritabanı Gezgini**, Northwind veritabanları **saklı yordamları** düğümünü genişletin ve **InsertCustomers**, **UpdateCustomers**ve **DeleteCustomers** saklı yordamlarını bulun.

3. Üç saklı yordamı [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] üzerine sürükleyin.

     Saklı yordamlar Yöntemler bölmesine <xref:System.Data.Linq.DataContext> yöntemleri olarak eklenir. Daha fazla bilgi için bkz. [DataContext yöntemleri (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. @No__t_1 **Müşteri** varlık sınıfını seçin.

5. **Özellikler** penceresinde **Insert** özelliğini seçin.

6. **Çalışma zamanı kullan** ' ın yanındaki üç nokta (...) simgesine tıklayarak **davranışı Yapılandır** iletişim kutusunu açın.

7. **Özelleştir**' i seçin.

8. **Özelleştir** listesinden **InsertCustomers** yöntemini seçin.

9. Seçili sınıf ve davranışa ait yapılandırmayı kaydetmek için **Uygula** ' ya tıklayın.

    > [!NOTE]
    > Her bir değişiklik yaptıktan sonra **Uygula** ' ya tıkladığınızda her bir sınıf/davranış birleşiminin davranışını yapılandırmaya devam edebilirsiniz. **Uygula**' ya tıklamadan önce sınıfı veya davranışı değiştirirseniz, herhangi bir değişiklik uygulamaya fırsat sağlayan bir uyarı iletişim kutusu görüntülenir.

10. **Davranış** listesinden **Güncelleştir** ' i seçin.

11. **Özelleştir**' i seçin.

12. **Özelleştir** listesinden **UpdateCustomers** yöntemini seçin.

     **Yöntem bağımsız değişkenlerinin** ve **Sınıf özelliklerinin** listesini inceleyin ve tablodaki bazı sütunlar Için iki **Yöntem bağımsız değişkeni** ve iki **sınıf özelliği** olduğuna dikkat edin. Bu, değişiklikleri izlemenizi ve eşzamanlılık ihlallerini denetleyen deyimler oluşturmayı kolaylaştırır.

13. **Original_CustomerID** Method bağımsız değişkenini **CustomerID (özgün)** sınıf özelliği ile eşleyin.

    > [!NOTE]
    > Varsayılan olarak, yöntem bağımsız değişkenleri, adlar eşleşiyorsa sınıf özellikleriyle eşlenir. Özellik adları değiştirilirse ve artık tablo ve varlık sınıfı arasında eşleşmezse, O/R Tasarımcısı doğru eşlemeyi belirleyememesi durumunda eşlenecek eşdeğer sınıf özelliğini seçmeniz gerekebilir. Ayrıca, yöntem bağımsız değişkenlerinin eşlenecek geçerli sınıf özellikleri yoksa, **sınıf özellikleri** değerini **(yok)** olarak ayarlayabilirsiniz.

14. Seçili sınıf ve davranışa ait yapılandırmayı kaydetmek için **Uygula** ' ya tıklayın.

15. **Davranış** listesinden **Sil** ' i seçin.

16. **Özelleştir**' i seçin.

17. **Özelleştir** listesinde **DeleteCustomers** yöntemini seçin.

18. **Original_CustomerID** Method bağımsız değişkenini **CustomerID (özgün)** sınıf özelliği ile eşleyin.

19. **Tamam**'a tıklayın.

> [!NOTE]
> Bu izlenecek yol için bir sorun olmamasına karşın, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] kimlik (otomatik artırma), ROWGUIDCOL (veritabanı tarafından üretilen GUID) ve ekleme sırasında zaman damgası sütunları için otomatik olarak veritabanı tarafından oluşturulan değerleri işlediğini belirten bir değer. Güncelleştirmeleriyle. Diğer sütun türlerindeki veritabanı tarafından oluşturulan değerler beklenmedik bir şekilde null değer oluşmasına neden olur. Veritabanı tarafından oluşturulan değerleri döndürmek için, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> `true` ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> aşağıdakilerden birine el ile ayarlamanız gerekir: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> veya <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="testing-the-application"></a>Uygulamayı Test Etme
 **UpdateCustomers** saklı yordamının veritabanındaki müşteri kaydını doğru bir şekilde güncelleştirdiğini doğrulamak için uygulamayı yeniden çalıştırın.

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. F5 tuşuna basın.

2. Kılavuzdaki bir kaydı değiştirerek güncelleştirme davranışını test edin.

3. Ekleme davranışını test etmek için yeni bir kayıt ekleyin.

4. Değişiklikleri veritabanına geri kaydetmek için Kaydet düğmesine tıklayın.

5. Formu kapatın.

6. F5 tuşuna basın ve güncelleştirilmiş kaydın ve yeni eklenen kaydın kalıcı olduğunu doğrulayın.

7. Adım 3 ' te oluşturduğunuz yeni kaydı silme davranışını test etmek için silin.

8. Değişiklikleri göndermek ve silinen kaydı veritabanından kaldırmak için Kaydet düğmesine tıklayın

9. Formu kapatın.

10. F5 tuşuna basın ve silinen kaydın veritabanından kaldırıldığını doğrulayın.

    > [!NOTE]
    > Uygulamanız, veritabanı dosyasının **Çıkış Dizinine Kopyala** özelliğinin değerine bağlı olarak SQL Server Express Edition kullanıyorsa, adım 10 ' da F5 tuşuna bastığınızda değişiklikler görünmeyebilir.

## <a name="next-steps"></a>Sonraki Adımlar
 Uygulama gereksinimlerinize bağlı olarak, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] varlık sınıfları oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu uygulamada yapabileceğiniz bazı geliştirmeler şunları içerir:

- Güncelleştirmeler sırasında eşzamanlılık denetimini uygulayın. Bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](https://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694).

- Verileri filtrelemek için LINQ sorguları ekleyin. Bilgi için bkz. [LINQ Sorgularına Giriş (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'daki LINQ to SQL araçları](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [LINQ to SQL sorgular](https://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae) [(o/r Designer)](../data-tools/datacontext-methods-o-r-designer.md) [, nasıl yapılır: güncelleştirme, ekleme ve silme Işlemleri yapmak için saklı yordamlar atama (o/r Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [Pave yenilikleri Visual Studio 2012 'de veri uygulaması geliştirme](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1)
