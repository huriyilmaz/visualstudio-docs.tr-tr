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
ms.openlocfilehash: 062bf282f68326014b47c27503e9454bd2484798
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127838"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Bir WCF veri hizmetine WPF denetimleri bağlama

Bu kılavuzda, veriye bağlı denetimler içeren bir WPF uygulaması oluşturabilirsiniz. Denetimler, WCF Veri Hizmeti'ne kapsüllene müşteri kayıtlarına bağlı olur. Ayrıca, müşterilerin kayıtları görüntülemek ve güncelleştirmek için kullanabileceği düğmeler de ekleyebilirsiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- AdventureWorksLT Varlık Veri Modeli veritabanındaki verilerden oluşturulan bir veritabanı oluşturma.

- Bir WPF uygulamasındaki verileri bir Varlık Veri Modeli WCF Veri Hizmeti oluşturma.

- Veri Kaynakları penceresindeki öğeleri WPF tasarımcısına **sürükleyerek bir** dizi veriye bağlı denetim oluşturma.

- Müşteri kayıtlarında ileri ve geri gezinen düğmeler oluşturma.

- Denetimlerde yapılan veri değişikliklerini WCF Veri Hizmeti'ne ve temel alınan veri kaynağına kaydeden bir düğme oluşturma.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

- AdventureWorksLT örnek veritabanının SQL Server veya SQL Server Express örneğine erişim. Veritabanını indirmek için bkz. [AdventureWorks örnek veritabanları](/sql/samples/adventureworks-install-configure?tabs=ssms)

Aşağıdaki kavramlar hakkında önceden bilgi sahibi olmak da yararlıdır ancak izlenecek yolu tamamlamak için gerekli değildir:

- [WCF Veri Hizmetleri.](/dotnet/framework/data/wcf/wcf-data-services-overview)

- içinde veri [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] modelleri.

- Varlık Veri Modelleri ve ADO.NET Entity Framework. Daha fazla bilgi için bkz. [Entity Framework bakın.](/dotnet/framework/data/adonet/ef/overview)

- WPF veri bağlama. Daha fazla bilgi için bkz. [Veri Bağlamaya genel bakış.](/dotnet/desktop-wpf/data/data-binding-overview)

## <a name="create-the-service-project"></a>Hizmet projesini oluşturma

1. Web Uygulaması projesi için bir C# veya Visual Basic **ASP.NET bu izlenecek yolu** başlatabilirsiniz. Projeyi **AdventureWorksService olarak adlandırın.**

2. Bu **Çözüm Gezgini** **Default.aspx'e** sağ tıklayın ve Sil'i **seçin.** Bu dosya izlenecek yol için gerekli değildir.

## <a name="create-an-entity-data-model-for-the-service"></a>Hizmet Varlık Veri Modeli oluşturma

WCF Veri Hizmeti kullanarak bir uygulamaya veri göstermek için, hizmet için bir veri modeli tanımlamanız gerekir. WCF Veri Hizmeti iki tür veri modeli destekler: Varlık Veri Modelleri ve arabirimi uygulayan ortak dil çalışma zamanı (CLR) nesneleri kullanılarak tanımlanan özel veri <xref:System.Linq.IQueryable%601> modelleri. Bu kılavuzda, veri modeli Varlık Veri Modeli bir örnek oluşturabilirsiniz.

1. Yeni **Project** Ekle'ye **tıklayın.**

2. Yüklü Şablonlar listesinde Veri 'ye **tıklayın** ve ardından ADO.NET Varlık Veri Modeli **öğesini** seçin.

3. Adı olarak değiştir ve `AdventureWorksModel.edmx` **Ekle'ye tıklayın.**

     Varlık Veri Modeli  sihirbazı açılır.

4. Model **İçeriğiNi seçin sayfasında,** Veritabanından **oluştur'a ve Ardından'ya** **tıklayın.**

5. Veri **Bağlantınızı Seçin sayfasında** aşağıdaki seçeneklerden birini belirleyin:

    - Açılan listede AdventureWorksLT örnek veritabanına bir veri bağlantısı varsa bunu seçin.

    - Yeni **Bağlantı'ya** tıklayın ve AdventureWorksLT veritabanına bir bağlantı oluşturun.

6. Veri **Bağlantınızı Seçin sayfasında** Varlık bağlantısı ayarlarını farklı kaydet seçeneğinin **App.Config** ve ardından Sonraki'ne **tıklayın.**

7. Veritabanı **Nesnelerinizi Seçin sayfasında** Tablolar'ı **genişletin** ve **ardından SalesOrderHeader tablosuna** tıklayın.

8. **Finish (Son)** düğmesine tıklayın.

## <a name="create-the-service"></a>Hizmeti oluşturma

Bir WPF uygulamasındaki verileri açığa çıkarmak için Varlık Veri Modeli WCF Veri Hizmeti oluşturun:

1. Yeni **Project** **Ekle'yi seçin.**

2. Yüklü **Şablonlar listesinde Web 'e** tıklayın ve **ardından WCF Veri Hizmeti proje öğesini** seçin. 

3. Ad **kutusuna yazın** ve `AdventureWorksService.svc` Ekle'ye **tıklayın.**

     Visual Studio projeye `AdventureWorksService.svc` ekler.

## <a name="configure-the-service"></a>Hizmeti yapılandırma

Hizmeti, oluşturduğunuz Varlık Veri Modeli yapılandırabilirsiniz:

1. Kod `AdventureWorks.svc` dosyasında **AdventureWorksService sınıf bildirimini** aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb" id="Snippet1":::

     Bu **kod, AdventureWorksService sınıfını,** nesnenizin nesne bağlamı sınıfında çalışan bir <xref:System.Data.Services.DataService%601> `AdventureWorksLTEntities` sınıfından türetecek şekilde Varlık Veri Modeli. Ayrıca, hizmetin `InitializeService` istemcilerinin varlığa tam okuma/yazma erişimine izin vermek için yöntemini de `SalesOrderHeader` günceller.

2. Projeyi derleme ve hatasız olarak derlemesini doğrulama.

## <a name="create-the-wpf-client-application"></a>WPF istemci uygulamasını oluşturma

WCF Veri Hizmeti'nin verilerini görüntülemek için, hizmeti temel alan bir veri kaynağı ile yeni bir WPF uygulaması oluşturun. Bu kılavuzda daha sonra uygulamaya veriye bağlı denetimler eklenecektir.

1. Bu **Çözüm Gezgini,** çözüm düğümüne sağ tıklayın, Ekle'ye **tıklayın** ve Yeni **girişler'Project.**

2. Yeni Project iletişim **kutusunda,** **Visual C#** veya **Visual Basic** genişletin ve sonra Dale'i **Windows.**

3. **WPF Uygulaması proje** şablonunu seçin.

4. Ad **kutusuna yazın** ve `AdventureWorksSalesEditor` Tamam'a **tıklayın.**

   Visual Studio `AdventureWorksSalesEditor` çözümüne ekler.

5. Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

   Veri **Kaynakları** penceresi açılır.

6. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

   Veri **Kaynağı Yapılandırma** sihirbazı açılır.

7. Sihirbazın **Veri Kaynağı Türü Seçin sayfasında** Hizmet'i seçin **ve** ardından Sonraki 'ye **tıklayın.**

8. Hizmet Başvurusu Ekle **iletişim** kutusunda, Keşfet'e **tıklayın.**

   Visual Studio kullanılabilir hizmetler için geçerli çözümü arar ve Hizmetler kutusunda `AdventureWorksService.svc` kullanılabilir hizmetler **listesine** ekler.

9. Ad Alanı **kutusuna** **AdventureWorksService yazın.**

10. Hizmetler kutusunda **AdventureWorksService.svc'ye ve** ardından Tamam'a **tıklayın.** 

    Visual Studio, hizmet bilgilerini indirir ve ardından Veri Kaynağı **Yapılandırma sihirbazına** geri döner.

11. Yeni **Hizmet Başvurusu Ekle** Son'a **tıklayın.**

    Visual Studio, hizmet tarafından döndürülen verileri temsil eden düğümleri Veri Kaynakları **penceresine** ekler.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimini tanımlama

WPF tasarımcısında XAML'yi değiştirerek pencereye birkaç düğme ekleyin. Bu kılavuzda daha sonra, kullanıcıların bu düğmeleri kullanarak satış kayıtlarını görüntülemesini ve güncelleştirmesini sağlayan kod eklenecektir.

1. Içinde **Çözüm Gezgini** **MainWindow.xaml'e çift tıklayın.**

   Pencere WPF tasarımcısında açılır.

2. Tasarımcı [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] görünümünde, etiketlerin arasına aşağıdaki kodu `<Grid>` ekleyin:

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

6. Özellikler **penceresinde** **IsReadOnly** özelliğinin yanındaki onay kutusunu seçin.

7. Aşağıdaki metin kutularının her biri için **IsReadOnly** özelliğini ayarlayın:

    - **Satın Alma Siparişi Numarası**

    - **Satış Siparişi Kimliği**

    - **Satış Siparişi Numarası**

## <a name="load-the-data-from-the-service"></a>Hizmetten verileri yükleme

Hizmetten satış verilerini yüklemek için hizmet proxy nesnesini kullanın. Ardından döndürülen verileri WPF penceresinde için veri <xref:System.Windows.Data.CollectionViewSource> kaynağına attayın.

1. Tasarımcıda, olay işleyicisini oluşturmak için şu `Window_Loaded` metni çift tıklatın: **MainWindow**.

2. Olay işleyicisini aşağıdaki kodla değiştirin. Bu kodda yer alan *localhost* adresini geliştirme bilgisayarınızda yerel ana bilgisayar adresiyle değiştirebilirsiniz.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet2":::

## <a name="navigate-sales-records"></a>Satış kayıtlarına gidin

Kullanıcıların düğmeleri kullanarak satış kayıtları arasında kaydırmalarını sağlayan kod **\<** and **>** ekleyin.

1. Tasarımcıda pencere **<** yüzeyindeki düğmeye çift tıklayın.

     Visual Studio arka kapı kod dosyasını açar ve olay için yeni `backButton_Click` bir olay <xref:System.Windows.Controls.Primitives.ButtonBase.Click> işleyicisi oluşturur.

2. Oluşturulan olay işleyiciye aşağıdaki `backButton_Click` kodu ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet3":::

3. Tasarımcıya geri dönüp düğmeye çift **>** tıklayın.

     Visual Studio arka kapı kod dosyasını açar ve olay için yeni `nextButton_Click` bir olay <xref:System.Windows.Controls.Primitives.ButtonBase.Click> işleyicisi oluşturur.

4. Oluşturulan olay işleyiciye aşağıdaki `nextButton_Click` kodu ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet4":::

## <a name="save-changes-to-sales-records"></a>Satış kayıtlarında yapılan değişiklikleri kaydetme

Kullanıcıların Değişiklikleri kaydet düğmesini kullanarak satış kayıtlarını görüntülemelerini ve kaydetmelerini sağlayan **kod** ekleyin:

1. Tasarımcıda Değişiklikleri Kaydet düğmesine **çift** tıklayın.

     Visual Studio arka kapı kod dosyasını açar ve olay için yeni `saveButton_Click` bir olay <xref:System.Windows.Controls.Primitives.ButtonBase.Click> işleyicisi oluşturur.

2. Olay işleyiciye aşağıdaki `saveButton_Click` kodu ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet5":::

## <a name="test-the-application"></a>Uygulamayı test edin

Müşteri kayıtlarını görüntüp güncelleştirebilirsiniz doğrulamak için uygulamayı derleme ve çalıştırma:

1. Derleme **menüsünde** Çözümü **Derleme'ye tıklayın.** Çözümün hatasız olarak derlemesi olduğunu doğrulayın.

2. **Ctrl** + **F5 tuşlarına basın.**

     Visual Studio hata **ayıklamadan AdventureWorksService** projesini başlatır.

3. Bu **Çözüm Gezgini** **AdventureWorksSalesEditor projesine sağ** tıklayın.

4. Sağ tıklama menüsünde (bağlam menüsü) Hata Ayıkla'nın **altında** Yeni örneği **başlat'a tıklayın.**

     Uygulama çalışır. Aşağıdakileri doğrulayın:

    - Metin kutuları, **71774** satış siparişi kimliğine sahip olan ilk satış kaydından farklı veri alanlarını görüntüler.

    - Veya düğmelerine **>** **<** tıklar ve diğer satış kayıtları arasında gezinebilirsiniz.

5. Satış kayıtlarından birinin Açıklama kutusuna metin yazın ve **Değişiklikleri** **kaydet'e tıklayın.**

6. Uygulamayı kapatın ve uygulamayı yeniden başlatarak uygulamayı Visual Studio.

7. Değiştirmiş olduğunu satış kaydına gidin ve uygulamayı kapatıp yeniden açtıktan sonra değişikliğin devam ettiği doğrulayın.

8. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu izlenecek yolu tamamladıktan sonra aşağıdaki ilgili görevleri gerçekleştirebilirsiniz:

- WPF denetimlerini **diğer veri** kaynağı türlerine bağlamak Visual Studio veri kaynakları penceresinin nasıl kullanacağını öğrenin. Daha fazla bilgi için [bkz. WPF denetimlerini bir veri kümesine bağlama.](../data-tools/bind-wpf-controls-to-a-dataset.md)

- WPF denetimlerini **kullanarak** ilgili Visual Studio (üst-alt ilişki içindeki veriler) görüntülemek için veri kaynakları penceresini kullanmayı öğrenin. Daha fazla bilgi için [bkz. Adım adım kılavuz: WPF uygulamasında ilgili verileri görüntüleme.](../data-tools/display-related-data-in-wpf-applications.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Bir veri kümesine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [WCF'ye genel bakış (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Entity Framework genel bakış (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [Veri Bağlamaya genel bakış (.NET Framework)](/dotnet/desktop-wpf/data/data-binding-overview)
