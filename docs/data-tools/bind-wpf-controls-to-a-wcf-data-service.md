---
title: Bir WCF veri hizmetine WPF denetimleri bağlama
description: WPF denetimlerini bir WCF veri hizmetine bağlama Visual Studio. Denetimler, WCF veri hizmetine kapsüllene müşteri kayıtlarına bağlı olur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 214975aa03da6181108e2d10046610d1afa20580
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067172"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Bir WCF veri hizmetine WPF denetimleri bağlama

Bu kılavuzda, veriye bağlı denetimler içeren bir WPF uygulaması oluşturabilirsiniz. Denetimler, WCF Veri Hizmeti'ne kapsüllene müşteri kayıtlarına bağımlıdır. Ayrıca müşterilerin kayıtları görüntülemek ve güncelleştirmek için kullanabileceği düğmeler de ekleyebilirsiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- AdventureWorksLT Varlık Veri Modeli veritabanındaki verilerden oluşturulan bir veritabanı oluşturma.

- Bir WPF uygulamasındaki verileri bir VARLıK VERI MODELI WCF Veri Hizmeti oluşturma.

- Veri Kaynakları penceresindeki öğeleri WPF tasarımcısına **sürükleyerek bir** dizi veriye bağlı denetim oluşturma.

- Müşteri kayıtlarında ileri ve geri gezinen düğmeler oluşturma.

- Denetimlerde yapılan veri değişikliklerini WCF Veri Hizmeti'ne ve temel alınan veri kaynağına kaydeden bir düğme oluşturma.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

- AdventureWorksLT örnek veritabanının SQL Server veya SQL Server Express örnek veritabanına erişim. AdventureWorksLT veritabanını CodePlex web [sitesinden indirebilirsiniz.](https://archive.codeplex.com/?p=SqlServerSamples)

Aşağıdaki kavramlar hakkında önceden bilgi sahibi olmak da yararlıdır ancak izlenecek yolu tamamlamak için gerekli değildir:

- [WCF Veri Hizmetleri.](/dotnet/framework/data/wcf/wcf-data-services-overview)

- içinde veri [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] modelleri.

- Varlık Veri Modelleri ve ADO.NET Entity Framework. Daha fazla bilgi için bkz. [Entity Framework genel bakış.](/dotnet/framework/data/adonet/ef/overview)

- WPF veri bağlama. Daha fazla bilgi için bkz. [Veri Bağlamaya genel bakış.](/dotnet/desktop-wpf/data/data-binding-overview)

## <a name="create-the-service-project"></a>Hizmet projesini oluşturma

1. Web Uygulaması projesi için bir C# veya Visual Basic **ASP.NET bu izlenecek yolu** başlatabilirsiniz. Projeyi **AdventureWorksService olarak adlandırın.**

2. Bu **Çözüm Gezgini** **Default.aspx'e sağ tıklayın ve** Sil'i **seçin.** Bu dosya izlenecek yol için gerekli değildir.

## <a name="create-an-entity-data-model-for-the-service"></a>Hizmet Varlık Veri Modeli oluşturma

WCF Veri Hizmeti kullanarak bir uygulamaya veri göstermek için, hizmet için bir veri modeli tanımlamanız gerekir. WCF Veri Hizmeti iki tür veri modeli destekler: Varlık Veri Modelleri ve arabirimi uygulayan ortak dil çalışma zamanı (CLR) nesneleri kullanılarak tanımlanan özel veri <xref:System.Linq.IQueryable%601> modelleri. Bu kılavuzda, veri modeli Varlık Veri Modeli bir örnek oluşturabilirsiniz.

1. Yeni **Project** Ekle'ye **tıklayın.**

2. Yüklü Şablonlar listesinde Veri 'ye **tıklayın** ve ardından ADO.NET Varlık Veri Modeli **öğesini** seçin.

3. Adı olarak değiştir ve `AdventureWorksModel.edmx` **Ekle'ye tıklayın.**

     Varlık Veri Modeli  sihirbazı açılır.

4. Model İçeriği **Seç sayfasında,** Veritabanından **oluştur'a ve ardından** Sonraki'ye **tıklayın.**

5. Veri **Bağlantınızı Seçin sayfasında** aşağıdaki seçeneklerden birini belirleyin:

    - Açılan listede AdventureWorksLT örnek veritabanına bir veri bağlantısı varsa bunu seçin.

    - Yeni **Bağlantı'ya** tıklayın ve AdventureWorksLT veritabanına bir bağlantı oluşturun.

6. Veri **Bağlantınızı Seçin sayfasında** Varlık bağlantı ayarlarını Farklı Kaydet seçeneğinin **App.Config** ve ardından Sonraki'ne **tıklayın.**

7. Veritabanı **Nesnelerinizi Seçin sayfasında** Tablolar'ı **genişletin** ve **ardından SalesOrderHeader tablosuna** tıklayın.

8. **Finish (Son)** düğmesine tıklayın.

## <a name="create-the-service"></a>Hizmeti oluşturma

Bir WPF uygulamasındaki verileri bir VARLıK VERI MODELI IÇIN WCF Veri Hizmeti oluşturun:

1. Yeni **Project** **Ekle'yi seçin.**

2. Yüklü **Şablonlar listesinde Web 'e** **tıklayın** ve **ardından WCF Veri Hizmeti proje öğesini** seçin.

3. Ad **kutusuna yazın** ve `AdventureWorksService.svc` Ekle'ye **tıklayın.**

     Visual Studio projeye `AdventureWorksService.svc` ekler.

## <a name="configure-the-service"></a>Hizmeti yapılandırma

Hizmeti, oluşturduğunuz çalışma Varlık Veri Modeli yapılandırabilirsiniz:

1. Kod `AdventureWorks.svc` dosyasında **AdventureWorksService sınıf bildirimini** aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb" id="Snippet1":::

     Bu **kod, AdventureWorksService sınıfını,** nesnenizin nesne bağlamı sınıfında çalışan bir sınıfından <xref:System.Data.Services.DataService%601> `AdventureWorksLTEntities` türetecek şekilde Varlık Veri Modeli. Ayrıca, hizmetin `InitializeService` istemcilerinin varlığa tam okuma/yazma erişimine izin vermek için yöntemini de `SalesOrderHeader` günceller.

2. Projeyi derleme ve hatasız olarak derlemesini doğrulama.

## <a name="create-the-wpf-client-application"></a>WPF istemci uygulamasını oluşturma

WCF Veri Hizmeti'nin verilerini görüntülemek için, hizmeti temel alan bir veri kaynağı ile yeni bir WPF uygulaması oluşturun. Bu kılavuzda daha sonra uygulamaya veriye bağlı denetimler eklenecektir.

1. Bu **Çözüm Gezgini,** çözüm düğümüne sağ tıklayın, Ekle'ye **tıklayın** ve Yeni **giriş'Project.**

2. Yeni Project iletişim **kutusunda,** **Visual C#** veya **Visual Basic** genişletin ve sonra Dale'i **Windows.**

3. **WPF Uygulaması proje** şablonunu seçin.

4. Ad **kutusuna yazın** ve `AdventureWorksSalesEditor` Tamam'a **tıklayın.**

   Visual Studio `AdventureWorksSalesEditor` çözümüne ekler.

5. Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

   Veri **Kaynakları** penceresi açılır.

6. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

   Veri **Kaynağı Yapılandırma** sihirbazı açılır.

7. Sihirbazın **Veri Kaynağı Türü Seçin sayfasında** Hizmet'i seçin **ve** ardından Sonraki'ye **tıklayın.**

8. Hizmet Başvurusu Ekle **iletişim** kutusunda, Keşfet'e **tıklayın.**

   Visual Studio kullanılabilir hizmetler için geçerli çözümü arar ve Hizmetler `AdventureWorksService.svc` kutusunda kullanılabilir hizmetler **listesine** ekler.

9. Ad Alanı **kutusuna** **AdventureWorksService yazın.**

10. Hizmetler kutusunda **AdventureWorksService.svc'ye ve** ardından Tamam'a **tıklayın.** 

    Visual Studio, hizmet bilgilerini indirir ve ardından Veri Kaynağı **Yapılandırma sihirbazına** geri döner.

11. Yeni **Hizmet Başvurusu Ekle** Son'a **tıklayın.**

    Visual Studio, hizmet tarafından döndürülen verileri temsil eden düğümleri Veri Kaynakları **penceresine** ekler.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimini tanımlama

WPF tasarımcısında XAML'yi değiştirerek pencereye birkaç düğme ekleyin. Bu kılavuzda daha sonra, kullanıcıların bu düğmeleri kullanarak satış kayıtlarını görüntülemesini ve güncelleştirmesini sağlayan kod eklenecektir.

1. Içinde **Çözüm Gezgini** **MainWindow.xaml'e çift tıklayın.**

   Pencere WPF tasarımcısında açılır.

2. Tasarımcı [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] görünümünde, etiketler arasına aşağıdaki kodu `<Grid>` ekleyin:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Projeyi derleyin.

## <a name="create-the-data-bound-controls"></a>Veriye bağlı denetimleri oluşturma

Düğümü Veri Kaynakları penceresinden tasarımcıya `SalesOrderHeaders` sürükleyerek müşteri **kayıtlarını görüntülüyor** denetimler oluşturun.

1. Veri **Kaynakları penceresinde** **SalesOrderHeaders** düğümünün açılan menüsüne tıklayın ve Ayrıntılar'ı **seçin.**

2. **SalesOrderHeaders düğümünü** genişletin.

3. Bu örnekte bazı alanlar görüntülenmez, bu nedenle aşağıdaki düğümlerin yanındaki açılan menüye tıklayın ve Yok'u **seçin:**

    - **CreditCardApprovalCode**

    - **Modifieddate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **Rowguıd**

    Bu eylem, Visual Studio sonraki adımda bu düğümler için veriye bağlı denetimler oluşturmasını önler. Bu kılavuzda, son kullanıcının bu verileri görme ihtiyacı olmadığını varsayalım.

4. Veri **Kaynakları penceresinde** **SalesOrderHeaders düğümünü** düğmeleri içeren satırın altındaki kılavuz satırına sürükleyin.

     Visual Studio, Product tablosunda verilere bağlı bir dizi denetim oluşturan XAML ve **kod** oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [WPF denetimlerini](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)Visual Studio.

5. Tasarımcıda Müşteri Kimliği etiketinin yanındaki metin **kutusuna** tıklayın.

6. **Özellikler** penceresinde, **IsReadOnly** özelliğinin yanındaki onay kutusunu işaretleyin.

7. Aşağıdaki metin kutularından her biri için **IsReadOnly** özelliğini ayarlayın:

    - **Satınalma siparişi numarası**

    - **Satış siparişi KIMLIĞI**

    - **Satış Siparişi Numarası**

## <a name="load-the-data-from-the-service"></a>Verileri hizmetten yükleyin

Hizmet proxy nesnesini kullanarak hizmetten satış verileri yükleyin. Ardından, veri kaynağına döndürülen verileri <xref:System.Windows.Data.CollectionViewSource> WPF penceresinde atayın.

1. Tasarımcıda `Window_Loaded` olay işleyicisini oluşturmak için şunu okuyan metne çift tıklayın: **MainWindow**.

2. Olay işleyicisini aşağıdaki kodla değiştirin. Bu koddaki *localhost* adresini geliştirme bilgisayarınızdaki yerel ana bilgisayar adresiyle değiştirdiğinizden emin olun.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet2":::

## <a name="navigate-sales-records"></a>Satış kayıtlarında gezin

Kullanıcıların, düğmeleri kullanarak satış kayıtları arasında gezinmelerini sağlayan kod ekleyin **\<** and **>** .

1. Tasarımcıda **<** pencere yüzeyinde düğmesine çift tıklayın.

     Visual Studio arka plan kod dosyasını açar ve `backButton_Click` olay için yeni bir olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Oluşturulan olay işleyicisine aşağıdaki kodu ekleyin `backButton_Click` :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet3":::

3. Tasarımcıya geri dönün ve düğmesine çift tıklayın **>** .

     Visual Studio arka plan kod dosyasını açar ve `nextButton_Click` olay için yeni bir olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

4. Oluşturulan olay işleyicisine aşağıdaki kodu ekleyin `nextButton_Click` :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet4":::

## <a name="save-changes-to-sales-records"></a>Değişiklikleri satış kayıtlarında Kaydet

**Değişiklikleri Kaydet** düğmesini kullanarak kullanıcıların satış kayıtlarında değişiklik görüntülemesine ve değişiklikleri kaydetmesine olanak sağlayan kod ekleyin:

1. Tasarımcıda **Değişiklikleri Kaydet** düğmesine çift tıklayın.

     Visual Studio arka plan kod dosyasını açar ve `saveButton_Click` olay için yeni bir olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Olay işleyicisine aşağıdaki kodu ekleyin `saveButton_Click` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet5":::

## <a name="test-the-application"></a>Uygulamayı test edin

Müşteri kayıtlarını görüntüleyip güncelleştirebildiğinizi doğrulamak için uygulamayı derleyin ve çalıştırın:

1. **Yapı** menüsünde **çözüm oluştur**' a tıklayın. Çözümün hata olmadan yapılandırıldığını doğrulayın.

2. **CTRL** + **F5** tuşuna basın.

     Visual Studio, **AdventureWorksService** projesini hata ayıklamadan başlatır.

3. **Çözüm Gezgini**, **AdventureWorksSalesEditor** projesine sağ tıklayın.

4. Sağ tıklama menüsünde (bağlam menüsü), **Hata Ayıkla** altında **Yeni örnek Başlat**' a tıklayın.

     Uygulama çalışır. Aşağıdakileri doğrulayın:

    - Metin kutuları, satış siparişi KIMLIĞI **71774** olan ilk satış kaydından farklı veri alanları görüntüler.

    - **>** **<** Diğer satış kayıtlarında gezinmek için veya düğmelerine tıklayabilirsiniz.

5. Satış kayıtlarından birinde, **Açıklama** kutusuna bir metin yazın ve ardından **Değişiklikleri Kaydet**' e tıklayın.

6. Uygulamayı kapatın ve ardından Visual Studio ' den uygulamayı yeniden başlatın.

7. Değiştirdiğiniz satış kaydına gidin ve uygulamayı kapatıp yeniden açtıktan sonra değişikliğin devam ettiğini doğrulayın.

8. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu yönergeyi tamamladıktan sonra, aşağıdaki ilgili görevleri gerçekleştirebilirsiniz:

- WPF denetimlerini diğer veri kaynağı türlerine bağlamak için Visual Studio **veri kaynakları** penceresini nasıl kullanacağınızı öğrenin. Daha fazla bilgi için bkz. [veri KÜMESINE WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md).

- WPF denetimlerinde ilgili verileri (yani bir üst-alt ilişkisi içindeki verileri) göstermek için Visual Studio **veri kaynakları** penceresini nasıl kullanacağınızı öğrenin. Daha fazla bilgi için bkz. [Izlenecek yol: BIR WPF uygulamasında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Bir veri kümesine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [WCF genel bakış (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Entity Framework genel bakış (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Veri Bağlamaya Genel Bakış (.NET Framework)](/dotnet/desktop-wpf/data/data-binding-overview)
