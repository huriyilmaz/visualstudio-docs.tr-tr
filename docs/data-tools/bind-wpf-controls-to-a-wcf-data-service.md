---
title: Bir WCF veri hizmetine WPF denetimleri bağlama
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4abe5047bd7d6f17bb0dc23f4d92a1a842ee273a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648761"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Bir WCF veri hizmetine WPF denetimleri bağlama

Bu izlenecek yolda, veri bağlantılı denetimler içeren bir WPF uygulaması oluşturacaksınız. Denetimler, bir WCF veri hizmetinde kapsüllenmiş müşteri kayıtlarına bağlanır. Ayrıca, müşterilerin kayıtları görüntülemek ve güncelleştirmek için kullanabileceği düğmeler de ekleyeceksiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- AdventureWorksLT örnek veritabanındaki verilerden oluşturulan Varlık Veri Modeli oluşturma.

- Varlık Veri Modeli verileri bir WPF uygulamasına sunan bir WCF veri hizmeti oluşturma.

- **Veri kaynakları** penceresinden WPF tasarımcısına öğe sürükleyerek bir veri bağlantılı denetimler kümesi oluşturma.

- Müşteri kayıtları arasında ileri ve geri gitmek için düğmeler oluşturma.

- Denetimlerindeki verilerde yapılan değişiklikleri WCF veri hizmetine ve temel alınan veri kaynağına kaydeden bir düğme oluşturma.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

- AdventureWorksLT örnek veritabanının eklendiği SQL Server veya SQL Server Express çalışan bir örneğine erişim. AdventureWorksLT veritabanını [CodePlex Web sitesinden](http://go.microsoft.com/fwlink/?linkid=87843)indirebilirsiniz.

Aşağıdaki kavramların önceki bilgileri de yararlı olmakla kalmaz, izlenecek yolu tamamlamak için gerekli değildir:

- [WCF veri Hizmetleri](/dotnet/framework/data/wcf/wcf-data-services-overview).

- @No__t_0 veri modelleri.

- Varlık veri modelleri ve ADO.NET Entity Framework. Daha fazla bilgi için bkz. [Entity Framework genel bakış](/dotnet/framework/data/adonet/ef/overview).

- WPF veri bağlama. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Hizmet projesi oluşturma

1. Bir C# veya Visual Basic **ASP.NET Web uygulaması** projesi oluşturarak bu yönergeyi başlatın. Projeyi **AdventureWorksService**olarak adlandırın.

2. **Çözüm Gezgini**, **default. aspx** öğesine sağ tıklayın ve **Sil**' i seçin. Bu dosya, izlenecek yol için gerekli değildir.

## <a name="create-an-entity-data-model-for-the-service"></a>Hizmet için Varlık Veri Modeli oluşturma

Bir WCF veri hizmeti kullanarak bir uygulamaya verileri göstermek için, hizmet için bir veri modeli tanımlamanız gerekir. WCF veri hizmeti iki tür veri modelini destekler: varlık veri modelleri ve <xref:System.Linq.IQueryable%601> arabirimini uygulayan ortak dil çalışma zamanı (CLR) nesneleri kullanılarak tanımlanan özel veri modelleri. Bu izlenecek yolda, veri modeli için bir Varlık Veri Modeli oluşturursunuz.

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. Yüklü şablonlar listesinde, **veriler**' e tıklayın ve ardından **ADO.net varlık veri modeli** Proje öğesini seçin.

3. Adı `AdventureWorksModel.edmx` olarak değiştirin ve **Ekle**' ye tıklayın.

     **Varlık veri modeli** Sihirbazı açılır.

4. **Model Içeriğini seçin** sayfasında, **veritabanından oluştur**' u ve **ardından İleri**' yi tıklatın.

5. **Veri bağlantınızı seçin** sayfasında, aşağıdaki seçeneklerden birini belirleyin:

    - Aşağı açılan listede AdventureWorksLT örnek veritabanıyla bir veri bağlantısı varsa, bunu seçin.

    - **Yeni bağlantı**' ya tıklayın ve AdventureWorksLT veritabanına bir bağlantı oluşturun.

6. **Veri bağlantınızı seçin** sayfasında, **app. config dosyasındaki varlık bağlantı ayarlarını kaydet** seçeneğinin belirlenmiş olduğundan emin olun ve ardından **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar**' ı genişletin ve ardından **SalesOrderHeader** tablosunu seçin.

8. **Son**'a tıklayın.

## <a name="create-the-service"></a>Hizmeti oluşturun

Varlık Veri Modeli verileri bir WPF uygulamasına göstermek için bir WCF veri hizmeti oluşturun:

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

2. **Yüklü şablonlar** listesinde, **Web**' e tıklayın ve ardından **WCF veri hizmeti** Proje öğesini seçin.

3. **Ad** kutusuna `AdventureWorksService.svc` yazın ve **Ekle**' ye tıklayın.

     Visual Studio `AdventureWorksService.svc` projeye ekler.

## <a name="configure-the-service"></a>Hizmeti yapılandırma

Hizmeti, oluşturduğunuz Varlık Veri Modeli çalışacak şekilde yapılandırmanız gerekir:

1. @No__t_0 kod dosyasında, **AdventureWorksService** sınıfı bildirimini aşağıdaki kodla değiştirin.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     Bu kod, Varlık Veri Modeli `AdventureWorksLTEntities` nesne bağlamı sınıfında çalışan bir <xref:System.Data.Services.DataService%601> türetmesi için **AdventureWorksService** sınıfını günceller. Ayrıca, hizmet istemcilerinin `SalesOrderHeader` varlığına tam okuma/yazma erişimi sağlamak için `InitializeService` yöntemini güncelleştirir.

2. Projeyi derleyin ve hata olmadan derleme olduğunu doğrulayın.

## <a name="create-the-wpf-client-application"></a>WPF istemci uygulaması oluşturma

WCF veri hizmetindeki verileri göstermek için, hizmeti temel alan bir veri kaynağıyla yeni bir WPF uygulaması oluşturun. Bu izlenecek yolda daha sonra uygulamaya veri bağlantılı denetimler ekleyeceksiniz.

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**' ye tıklayın ve **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda,  **C# Visual** veya **Visual Basic**öğesini genişletin ve ardından **Windows**' u seçin.

3. **WPF uygulaması** proje şablonunu seçin.

4. **Ad** kutusuna `AdventureWorksSalesEditor` yazın ve **Tamam**' ı tıklatın.

   Visual Studio `AdventureWorksSalesEditor` projesini çözüme ekler.

5. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

   **Veri kaynakları** penceresi açılır.

6. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

   **Veri kaynağı yapılandırma** Sihirbazı açılır.

7. Sihirbazın **veri kaynağı türünü seçin** sayfasında **hizmet**' i seçin ve ardından **İleri**' ye tıklayın.

8. **Hizmet başvurusu Ekle** Iletişim kutusunda **bul**' a tıklayın.

   Visual Studio kullanılabilir hizmetler için geçerli çözümü arar ve **Hizmetler** kutusundaki kullanılabilir hizmetler listesine `AdventureWorksService.svc` ekler.

9. **Ad alanı** kutusuna **AdventureWorksService**yazın.

10. **Hizmetler** kutusunda **AdventureWorksService. svc**' ye tıklayın ve ardından **Tamam**' a tıklayın.

    Visual Studio, hizmet bilgilerini indirir ve ardından **veri kaynağı yapılandırma** sihirbazına geri döner.

11. **Hizmet başvurusu Ekle** sayfasında **son**' a tıklayın.

    Visual Studio, **veri kaynakları** penceresine hizmet tarafından döndürülen verileri temsil eden düğümleri ekler.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimini tanımlama

WPF Tasarımcısında XAML 'yi değiştirerek pencereye birkaç düğme ekleyin. Bu izlenecek yolda daha sonra, kullanıcıların bu düğmeleri kullanarak satış kayıtlarını görüntülemesine ve güncelleştirmesine olanak tanıyan bir kod ekleyeceksiniz.

1. **Çözüm Gezgini**, **MainWindow. xaml**' ye çift tıklayın.

   Pencere WPF Tasarımcısı 'nda açılır.

2. Tasarımcının [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] görünümünde, `<Grid>` etiketleri arasına aşağıdaki kodu ekleyin:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Projeyi oluşturun.

## <a name="create-the-data-bound-controls"></a>Veri bağlantılı denetimleri oluşturma

@No__t_0 düğümünü **veri kaynakları** penceresinden tasarımcıya sürükleyerek müşteri kayıtlarını görüntüleyen denetimler oluşturun.

1. **Veri kaynakları** penceresinde, **SalesOrderHeaders** düğümünün açılan menüsüne tıklayın ve **Ayrıntılar**' ı seçin.

2. **SalesOrderHeaders** düğümünü genişletin.

3. Bu örnekte, bazı alanlar görüntülenmeyecektir, bu nedenle aşağıdaki düğümlerin yanındaki açılan menüye tıklayın ve **hiçbiri**' ni seçin:

    - **CreditCardApprovalCode**

    - **ModifiedDate & lt**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **rowguid**

    Bu eylem, Visual Studio 'Nun bir sonraki adımda bu düğümler için veri bağlantılı denetimler oluşturmasını engeller. Bu izlenecek yol için, son kullanıcının bu verileri görmesini gerektirmeyen varsayılmaktadır.

4. **Veri kaynakları** penceresinde, **SalesOrderHeaders** düğümünü düğmeleri içeren satırın altındaki kılavuz satırına sürükleyin.

     Visual Studio, **ürün** tablosundaki verilere bağlanan bir denetim KÜMESI oluşturan xaml ve kod oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. Tasarımcıda **MÜŞTERI kimliği** etiketinin yanındaki metin kutusuna tıklayın.

6. **Özellikler** penceresinde, **IsReadOnly** özelliğinin yanındaki onay kutusunu işaretleyin.

7. Aşağıdaki metin kutularından her biri için **IsReadOnly** özelliğini ayarlayın:

    - **Satınalma siparişi numarası**

    - **Satış siparişi KIMLIĞI**

    - **Satış siparişi numarası**

## <a name="load-the-data-from-the-service"></a>Verileri hizmetten yükleyin

Hizmet proxy nesnesini kullanarak hizmetten satış verileri yükleyin. Ardından, veri kaynağına döndürülen verileri WPF penceresindeki <xref:System.Windows.Data.CollectionViewSource> atayın.

1. Tasarımcıda `Window_Loaded` olay işleyicisi oluşturmak için, şunu okuyan metne çift tıklayın: **MainWindow**.

2. Olay işleyicisini aşağıdaki kodla değiştirin. Bu koddaki *localhost* adresini geliştirme bilgisayarınızdaki yerel ana bilgisayar adresiyle değiştirdiğinizden emin olun.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>Satış kayıtlarında gezin

Kullanıcıların **\<** ve **>** düğmelerini kullanarak satış kayıtları arasında gezinmelerini sağlayan kod ekleyin.

1. Tasarımcıda pencere yüzeyinde **<** düğmesine çift tıklayın.

     Visual Studio, arka plan kod dosyasını açar ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için yeni bir `backButton_Click` olay işleyicisi oluşturur.

2. Aşağıdaki kodu oluşturulan `backButton_Click` olay işleyicisine ekleyin:

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. Tasarımcıya dönün ve **>** düğmesine çift tıklayın.

     Visual Studio, arka plan kod dosyasını açar ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için yeni bir `nextButton_Click` olay işleyicisi oluşturur.

4. Aşağıdaki kodu oluşturulan `nextButton_Click` olay işleyicisine ekleyin:

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>Değişiklikleri satış kayıtlarında Kaydet

**Değişiklikleri Kaydet** düğmesini kullanarak kullanıcıların satış kayıtlarında değişiklik görüntülemesine ve değişiklikleri kaydetmesine olanak sağlayan kod ekleyin:

1. Tasarımcıda **Değişiklikleri Kaydet** düğmesine çift tıklayın.

     Visual Studio, arka plan kod dosyasını açar ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için yeni bir `saveButton_Click` olay işleyicisi oluşturur.

2. @No__t_0 olay işleyicisine aşağıdaki kodu ekleyin.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>Uygulamayı test etme

Müşteri kayıtlarını görüntüleyip güncelleştirebildiğinizi doğrulamak için uygulamayı derleyin ve çalıştırın:

1. **Yapı** menüsünde **çözüm oluştur**' a tıklayın. Çözümün hata olmadan yapılandırıldığını doğrulayın.

2. **Ctrl** +**F5**tuşuna basın.

     Visual Studio, **AdventureWorksService** projesini hata ayıklamadan başlatır.

3. **Çözüm Gezgini**, **AdventureWorksSalesEditor** projesine sağ tıklayın.

4. Sağ tıklama menüsünde (bağlam menüsü), **Hata Ayıkla**altında **Yeni örnek Başlat**' a tıklayın.

     Uygulama çalışır. Aşağıdakileri doğrulayın:

    - Metin kutuları, satış siparişi KIMLIĞI **71774**olan ilk satış kaydından farklı veri alanları görüntüler.

    - Diğer satış kayıtlarında gezinmek için **>** veya **<** düğmelerine tıklayabilirsiniz.

5. Satış kayıtlarından birinde, **Açıklama** kutusuna bir metin yazın ve ardından **Değişiklikleri Kaydet**' e tıklayın.

6. Uygulamayı kapatın ve sonra Visual Studio 'dan uygulamayı yeniden başlatın.

7. Değiştirdiğiniz satış kaydına gidin ve uygulamayı kapatıp yeniden açtıktan sonra değişikliğin devam ettiğini doğrulayın.

8. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu yönergeyi tamamladıktan sonra, aşağıdaki ilgili görevleri gerçekleştirebilirsiniz:

- Visual Studio 'daki **veri kaynakları** PENCERESINI kullanarak WPF denetimlerini diğer veri kaynağı türlerine bağlamayı öğrenin. Daha fazla bilgi için bkz. [veri KÜMESINE WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Visual Studio 'daki **veri kaynakları** PENCERESINI kullanarak WPF denetimlerinde ilgili verileri (yani bir üst-alt ilişkisi içindeki verileri) görüntüleme hakkında bilgi edinin. Daha fazla bilgi için bkz. [Izlenecek yol: BIR WPF uygulamasında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Bir veri kümesine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [WCF genel bakış (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Entity Framework genel bakış (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Veri Bağlamaya Genel Bakış (.NET Framework)](/dotnet/framework/wpf/data/data-binding-overview)