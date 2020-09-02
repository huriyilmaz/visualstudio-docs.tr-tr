---
title: Bir WCF veri hizmetine WPF denetimleri bağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3589f409efe2a104391eb62f939ef76d140e5224
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850136"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Bir WCF veri hizmetine WPF denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda, veri bağlantılı denetimler içeren bir WPF uygulaması oluşturacaksınız. Denetimler, bir içinde kapsüllenmiş müşteri kayıtlarına bağlanır [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] . Ayrıca, müşterilerin kayıtları görüntülemek ve güncelleştirmek için kullanabileceği düğmeler de ekleyeceksiniz.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- AdventureWorksLT örnek veritabanındaki verilerden oluşturulan Varlık Veri Modeli oluşturma.

- Bir [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] WPF uygulamasına varlık veri modeli verileri kullanıma sunan bir oluşturma.

- **Veri kaynakları** penceresinden WPF tasarımcısına öğe sürükleyerek bir veri bağlantılı denetimler kümesi oluşturma.

- Müşteri kayıtları arasında ileri ve geri gitmek için düğmeler oluşturma.

- Denetimlerindeki verilerde yapılan değişiklikleri [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] ve temel alınan veri kaynağını kaydeden bir düğme oluşturma.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- AdventureWorksLT örnek veritabanının eklendiği SQL Server veya SQL Server Express çalışan bir örneğine erişim. AdventureWorksLT veritabanını [CodePlex Web sitesinden](https://codeplex.com/SqlServerSamples)indirebilirsiniz.

  Aşağıdaki kavramların önceki bilgileri de yararlı olmakla kalmaz, izlenecek yolu tamamlamak için gerekli değildir:

- WCF Veri Hizmetleri. Daha fazla bilgi için bkz. [Genel Bakış](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- İçindeki veri modelleri [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] .

- Varlık veri modelleri ve ADO.NET Entity Framework. Daha fazla bilgi için bkz. [Entity Framework genel bakış](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- WPF Tasarımcısı ile çalışma. Daha fazla bilgi için bkz. [WPF ve Silverlight tasarımcısına genel bakış](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- WPF veri bağlama. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-service-project"></a>Hizmet projesi oluşturma
 İçin bir proje oluşturarak bu yönergeyi başlatın [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] .

#### <a name="to-create-the-service-project"></a>Hizmet projesini oluşturmak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. **Visual C#** veya **Visual Basic**öğesini genişletin ve ardından **Web**' i seçin.

4. **ASP.NET Web uygulaması** proje şablonunu seçin.

5. **Ad** kutusuna yazın `AdventureWorksService` ve **Tamam**' ı tıklatın.

     Visual Studio projeyi oluşturur `AdventureWorksService` .

6. **Çözüm Gezgini**, **default. aspx** öğesine sağ tıklayın ve **Sil**' i seçin. Bu dosya bu kılavuzda gerekli değildir.

## <a name="create-an-entity-data-model-for-the-service"></a>Hizmet için Varlık Veri Modeli oluşturma
 Kullanarak bir uygulamaya verileri göstermek için [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] , hizmet için bir veri modeli tanımlamanız gerekir. [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]İki tür veri modelini destekler: varlık veri modelleri ve arabirimi uygulayan ortak dil çalışma zamanı (CLR) nesneleri kullanılarak tanımlanan özel veri modelleri <xref:System.Linq.IQueryable%601> . Bu izlenecek yolda, veri modeli için bir Varlık Veri Modeli oluşturursunuz.

#### <a name="to-create-an-entity-data-model"></a>Varlık Veri Modeli oluşturmak için

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. Yüklü şablonlar listesinde, **veriler**' e tıklayın ve ardından **ADO.net varlık veri modeli** Proje öğesini seçin.

3. Adı olarak değiştirin `AdventureWorksModel.edmx` ve **Ekle**' ye tıklayın.

     **Varlık veri modeli** Sihirbazı açılır.

4. **Model Içeriğini seçin** sayfasında, **veritabanından oluştur**' u ve **ardından İleri**' yi tıklatın.

5. **Veri bağlantınızı seçin** sayfasında, aşağıdaki seçeneklerden birini belirleyin:

    - Aşağı açılan listede AdventureWorksLT örnek veritabanıyla bir veri bağlantısı varsa, bunu seçin.

    - **Yeni bağlantı**' ya tıklayın ve AdventureWorksLT veritabanına bir bağlantı oluşturun.

6. **Veri bağlantınızı seçin** sayfasında, **varlık bağlantı ayarlarını App.Config olarak Kaydet ' in** seçildiğinden emin olun ve ardından **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar**' ı genişletin ve ardından **SalesOrderHeader** tablosunu seçin.

8. **Son**'a tıklayın.

## <a name="create-the-service"></a>Hizmeti oluşturma
 Varlık Veri Modeli bir [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] WPF uygulamasına verileri göstermek için oluşturun.

#### <a name="to-create-the-service"></a>Hizmeti oluşturmak için

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

2. Yüklü şablonlar listesinde, **Web**' e tıklayın ve ardından **WCF veri hizmeti** Proje öğesini seçin.

3. **Ad** kutusuna yazın `AdventureWorksService.svc` ve **Ekle**' ye tıklayın.

     Visual Studio, öğesini `AdventureWorksService.svc` projeye ekler.

## <a name="configure-the-service"></a>Hizmeti yapılandırma
 Hizmeti, oluşturduğunuz Varlık Veri Modeli çalışacak şekilde yapılandırmanız gerekir.

#### <a name="to-configure-the-service"></a>Hizmeti yapılandırmak için

1. `AdventureWorks.svc`Kod dosyasında, `AdventureWorksService` sınıf bildirimini aşağıdaki kodla değiştirin.

     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]

     Bu kod, `AdventureWorksService` sınıfı güncelleştirir, böylece <xref:System.Data.Services.DataService%601> `AdventureWorksLTEntities` varlık veri modeli nesne bağlamı sınıfında çalışan bir öğesinden türetilir. Ayrıca, `InitializeService` hizmet istemcilerinin varlığa tam okuma/yazma erişimi sağlamak için yöntemini de güncelleştirir `SalesOrderHeader` .

2. Projeyi derleyin ve hata olmadan derleme olduğunu doğrulayın.

## <a name="create-the-wpf-client-application"></a>WPF istemci uygulaması oluşturma
 İçindeki verileri göstermek için [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] , hizmeti temel alan bir veri kaynağıyla yeni BIR WPF uygulaması oluşturun. Bu izlenecek yolda daha sonra uygulamaya veri bağlantılı denetimler ekleyeceksiniz.

#### <a name="to-create-the-wpf-client-application"></a>WPF istemci uygulaması oluşturmak için

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**' ye tıklayın ve **Yeni proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic**öğesini genişletin ve ardından **Windows**' u seçin.

3. **WPF uygulaması** proje şablonunu seçin.

4. **Ad** kutusuna yazın `AdventureWorksSalesEditor` ve **Tamam**' a tıklayın.

     Visual Studio, `AdventureWorksSalesEditor` projeyi çözüme ekler.

5. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

     **Veri kaynakları** penceresi açılır.

6. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

     **Veri kaynağı yapılandırma** Sihirbazı açılır.

7. Sihirbazın **veri kaynağı türünü seçin** sayfasında **hizmet**' i seçin ve ardından **İleri**' ye tıklayın.

8. **Hizmet başvurusu Ekle** Iletişim kutusunda **bul**' a tıklayın.

     Visual Studio kullanılabilir hizmetler için geçerli çözümü arar ve `AdventureWorksService.svc` **Hizmetler** kutusunda kullanılabilir Hizmetler listesine ekler.

9. **Ad alanı** kutusuna yazın `AdventureWorksService` .

10. **Hizmetler** kutusunda **AdventureWorksService. svc**' ye tıklayın ve ardından **Tamam**' a tıklayın.

     Visual Studio, hizmet bilgilerini indirir ve ardından **veri kaynağı yapılandırma** sihirbazına geri döner.

11. **Hizmet başvurusu Ekle** sayfasında **son**' a tıklayın.

     Visual Studio, **veri kaynakları** penceresine hizmet tarafından döndürülen verileri temsil eden düğümleri ekler.

## <a name="define-the-user-interface-of-the-window"></a>Pencerenin Kullanıcı arabirimini tanımlama
 WPF Tasarımcısında XAML 'yi değiştirerek pencereye birkaç düğme ekleyin. Bu izlenecek yolda daha sonra, kullanıcıların bu düğmeleri kullanarak satış kayıtlarını görüntülemesine ve güncelleştirmesine olanak tanıyan bir kod ekleyeceksiniz.

#### <a name="to-create-the-window-layout"></a>Pencere düzeni oluşturmak için

1. **Çözüm Gezgini**, MainWindow. xaml ' ye çift tıklayın.

     Pencere WPF Tasarımcısı 'nda açılır.

2. [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]Tasarımcı görünümünde aşağıdaki kodu Etiketler arasına ekleyin `<Grid>` :

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="525" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. Projeyi derleyin.

## <a name="create-the-data-bound-controls"></a>Veri bağlantılı denetimleri oluşturma
 `SalesOrderHeaders`Düğümü **veri kaynakları** penceresinden tasarımcıya sürükleyerek müşteri kayıtlarını görüntüleyen denetimler oluşturun.

#### <a name="to-create-the-data-bound-controls"></a>Veri bağlantılı denetimleri oluşturmak için

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

    Visual Studio, **ürün** tablosundaki verilere bağlanan bir denetim KÜMESI oluşturan xaml ve kod oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

5. Tasarımcıda **MÜŞTERI kimliği** etiketinin yanındaki metin kutusuna tıklayın.

6. **Özellikler** penceresinde, **IsReadOnly** özelliğinin yanındaki onay kutusunu işaretleyin.

7. Aşağıdaki metin kutularından her biri için **IsReadOnly** özelliğini ayarlayın:

   - **Satınalma siparişi numarası**

   - **Satış siparişi KIMLIĞI**

   - **Satış Siparişi Numarası**

## <a name="load-the-data-from-the-service"></a>Verileri hizmetten yükleyin
 Hizmet proxy nesnesini kullanarak hizmetten satış verileri yükleyin. Ardından, veri kaynağına döndürülen verileri <xref:System.Windows.Data.CollectionViewSource> WPF penceresinde atayın.

#### <a name="to-load-the-data-from-the-service"></a>Verileri hizmetten yüklemek için

1. Tasarımcıda `Window_Loaded` olay işleyicisini oluşturmak için şunu okuyan metne çift tıklayın: **MainWindow**.

2. Olay işleyicisini aşağıdaki kodla değiştirin. Bu koddaki *localhost* adresini geliştirme bilgisayarınızdaki yerel ana bilgisayar adresiyle değiştirdiğinizden emin olun.

     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]

## <a name="navigatesales-records"></a>Navigatesales kayıtları
 Kullanıcıların, düğmeleri kullanarak satış kayıtları arasında gezinmelerini sağlayan kod ekleyin **\<** and **>** .

#### <a name="to-enable-users-to-navigate-sales-records"></a>Kullanıcıların satış kayıtlarında gezinme olanağı sağlamak için

1. Tasarımcıda **<** pencere yüzeyinde düğmesine çift tıklayın.

     Visual Studio, arka plan kod dosyasını açar ve olay için yeni bir `backButton_Click` olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Oluşturulan olay işleyicisine aşağıdaki kodu ekleyin `backButton_Click` :

     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]

3. Tasarımcıya geri dönün ve düğmesine çift tıklayın **>** .

     Visual Studio, arka plan kod dosyasını açar ve olay için yeni bir `nextButton_Click` olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

4. Oluşturulan olay işleyicisine aşağıdaki kodu ekleyin `nextButton_Click` :

     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]

## <a name="saving-changes-to-sales-records"></a>Değişiklikleri satış kayıtlarına kaydetme
 **Değişiklikleri Kaydet** düğmesini kullanarak kullanıcıların satış kayıtlarında değişiklik görüntülemesine ve değişiklikleri kaydetmesine olanak sağlayan kod ekleyin.

#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Değişiklikleri satış kayıtlarına kaydetme yeteneğini eklemek için

1. Tasarımcıda **Değişiklikleri Kaydet** düğmesine çift tıklayın.

     Visual Studio, arka plan kod dosyasını açar ve olay için yeni bir `saveButton_Click` olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Olay işleyicisine aşağıdaki kodu ekleyin `saveButton_Click` .

     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]

## <a name="testing-the-application"></a>Uygulamayı test etme
 Müşteri kayıtlarını görüntüleyip güncelleştirebildiğinizi doğrulamak için uygulamayı derleyin ve çalıştırın.

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. **Yapı** menüsünde **çözüm oluştur**' a tıklayın. Çözümün hata olmadan yapılandırıldığını doğrulayın.

2. **CTRL + F5**tuşlarına basın.

     Visual Studio, **AdventureWorksService** projesini hata ayıklamadan başlatır.

3. **Çözüm Gezgini**, **AdventureWorksSalesEditor** projesine sağ tıklayın.

4. Bağlam menüsünde, **Hata Ayıkla**altında **Yeni örnek Başlat**' a tıklayın.

     Uygulama çalışır. Aşağıdakileri doğrulayın:

    - Metin kutuları, satış siparişi KIMLIĞI **71774**olan ilk satış kaydından farklı veri alanları görüntüler.

    - **>** **<** Diğer satış kayıtlarında gezinmek için veya düğmelerine tıklayabilirsiniz.

5. Satış kayıtlarından birinde, **Açıklama** kutusuna bir metin yazın ve ardından **Değişiklikleri Kaydet**' e tıklayın.

6. Uygulamayı kapatın ve sonra Visual Studio 'dan uygulamayı yeniden başlatın.

7. Değiştirdiğiniz satış kaydına gidin ve uygulamayı kapatıp yeniden açtıktan sonra değişikliğin devam ettiğini doğrulayın.

8. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki Adımlar
 Bu yönergeyi tamamladıktan sonra, aşağıdaki ilgili görevleri gerçekleştirebilirsiniz:

- Visual Studio 'daki **veri kaynakları** PENCERESINI kullanarak WPF denetimlerini diğer veri kaynağı türlerine bağlamayı öğrenin. Daha fazla bilgi için bkz. [veri KÜMESINE WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Visual Studio 'daki **veri kaynakları** PENCERESINI kullanarak WPF denetimlerinde ilgili verileri (yani bir üst-alt ilişkisi içindeki verileri) görüntüleme hakkında bilgi edinin. Daha fazla bilgi için bkz. [Izlenecek yol: BIR WPF uygulamasında Ilgili verileri görüntüleme](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'daki verilere](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) WPF denetimleri bağlama WPF denetimlerini [Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) 'ya bağlama WPF [denetimlerini veri kümesine](../data-tools/bind-wpf-controls-to-a-dataset.md) [genel](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb) bakış [Entity Framework genel bakış](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0) [WPF ve Silverlight tasarımcısına](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) genel bakış [veri bağlamaya genel](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211) bakış
