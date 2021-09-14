---
title: Bir WCF veri hizmetine WPF denetimleri bağlama
description: Visual Studio içindeki bir WCF veri hizmetine WPF denetimleri bağlayın. Denetimler, bir WCF veri hizmetinde kapsüllenmiş müşteri kayıtlarına bağlanır.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631569"
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

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

- AdventureWorksLT örnek veritabanının eklendiği SQL Server veya SQL Server Express çalışan bir örneğine erişim. AdventureWorksLT veritabanını [CodePlex Web sitesinden](https://archive.codeplex.com/?p=SqlServerSamples)indirebilirsiniz.

Aşağıdaki kavramların önceki bilgileri de yararlı olmakla kalmaz, izlenecek yolu tamamlamak için gerekli değildir:

- [WCF Veri Hizmetleri](/dotnet/framework/data/wcf/wcf-data-services-overview).

- İçindeki veri modelleri [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] .

- varlık veri modelleri ve ADO.NET Entity Framework. Daha fazla bilgi için bkz. [Entity Framework genel bakış](/dotnet/framework/data/adonet/ef/overview).

- WPF veri bağlama. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-service-project"></a>Hizmet projesi oluşturma

1. C# veya Visual Basic **ASP.NET Web uygulaması** projesi oluşturarak bu yönergeyi başlatın. Projeyi **AdventureWorksService** olarak adlandırın.

2. **Çözüm Gezgini**, **default. aspx** öğesine sağ tıklayın ve **Sil**' i seçin. Bu dosya, izlenecek yol için gerekli değildir.

## <a name="create-an-entity-data-model-for-the-service"></a>Hizmet için Varlık Veri Modeli oluşturma

Bir WCF veri hizmeti kullanarak bir uygulamaya verileri göstermek için, hizmet için bir veri modeli tanımlamanız gerekir. WCF veri hizmeti iki tür veri modelini destekler: varlık veri modelleri ve arabirimi uygulayan ortak dil çalışma zamanı (CLR) nesneleri kullanılarak tanımlanan özel veri modelleri <xref:System.Linq.IQueryable%601> . Bu izlenecek yolda, veri modeli için bir Varlık Veri Modeli oluşturursunuz.

1. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

2. yüklü şablonlar listesinde, **veriler**' e tıklayın ve ardından **ADO.NET Varlık Veri Modeli** proje öğesini seçin.

3. Adı olarak değiştirin `AdventureWorksModel.edmx` ve **Ekle**' ye tıklayın.

     **Varlık veri modeli** Sihirbazı açılır.

4. **Model Içeriğini seçin** sayfasında, **veritabanından oluştur**' u ve **ardından İleri**' yi tıklatın.

5. **Veri bağlantınızı seçin** sayfasında, aşağıdaki seçeneklerden birini belirleyin:

    - Aşağı açılan listede AdventureWorksLT örnek veritabanıyla bir veri bağlantısı varsa, bunu seçin.

    - **Yeni bağlantı**' ya tıklayın ve AdventureWorksLT veritabanına bir bağlantı oluşturun.

6. **Veri bağlantınızı seçin** sayfasında, **varlık bağlantı ayarlarını App.Config olarak Kaydet ' in** seçildiğinden emin olun ve ardından **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar**' ı genişletin ve ardından **SalesOrderHeader** tablosunu seçin.

8. **Finish (Son)** düğmesine tıklayın.

## <a name="create-the-service"></a>Hizmeti oluşturma

Varlık Veri Modeli verileri bir WPF uygulamasına göstermek için bir WCF veri hizmeti oluşturun:

1. **Project** menüsünde **yeni öğe ekle**' yi seçin.

2. **Yüklü şablonlar** listesinde, **Web**' e tıklayın ve ardından **WCF veri hizmeti** Proje öğesini seçin.

3. **Ad** kutusuna yazın `AdventureWorksService.svc` ve **Ekle**' ye tıklayın.

     Visual Studio projeye ekler `AdventureWorksService.svc` .

## <a name="configure-the-service"></a>Hizmeti yapılandırma

Hizmeti, oluşturduğunuz Varlık Veri Modeli çalışacak şekilde yapılandırmanız gerekir:

1. `AdventureWorks.svc`Kod dosyasında, **AdventureWorksService** sınıfı bildirimini aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb" id="Snippet1":::

     Bu kod, **AdventureWorksService** sınıfını güncelleştirir, böylece <xref:System.Data.Services.DataService%601> `AdventureWorksLTEntities` varlık veri modeli nesne bağlamı sınıfında çalışan bir öğesinden türetilir. Ayrıca, `InitializeService` hizmet istemcilerinin varlığa tam okuma/yazma erişimi sağlamak için yöntemini de güncelleştirir `SalesOrderHeader` .

2. Projeyi derleyin ve hata olmadan derleme olduğunu doğrulayın.

## <a name="create-the-wpf-client-application"></a>WPF istemci uygulaması oluşturma

WCF veri hizmetindeki verileri göstermek için, hizmeti temel alan bir veri kaynağıyla yeni bir WPF uygulaması oluşturun. Bu izlenecek yolda daha sonra uygulamaya veri bağlantılı denetimler ekleyeceksiniz.

1. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**' ye tıklayın ve **yeni Project**' i seçin.

2. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Windows**' yı seçin.

3. **WPF uygulaması** proje şablonunu seçin.

4. **Ad** kutusuna yazın `AdventureWorksSalesEditor` ve **Tamam**' a tıklayın.

   Visual Studio, `AdventureWorksSalesEditor` projeyi çözüme ekler.

5. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

   **Veri kaynakları** penceresi açılır.

6. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

   **Veri kaynağı yapılandırma** Sihirbazı açılır.

7. Sihirbazın **veri kaynağı türünü seçin** sayfasında **hizmet**' i seçin ve ardından **İleri**' ye tıklayın.

8. **Hizmet başvurusu Ekle** Iletişim kutusunda **bul**' a tıklayın.

   Visual Studio kullanılabilir hizmetler için geçerli çözümü arar ve `AdventureWorksService.svc` **hizmetler** kutusunda kullanılabilir hizmetler listesine ekler.

9. **Ad alanı** kutusuna **AdventureWorksService** yazın.

10. **Hizmetler** kutusunda **AdventureWorksService. svc**' ye tıklayın ve ardından **Tamam**' a tıklayın.

    Visual Studio, hizmet bilgilerini indirir ve ardından **veri kaynağı yapılandırma** sihirbazına geri döner.

11. **Hizmet başvurusu Ekle** sayfasında **son**' a tıklayın.

    Visual Studio, hizmet tarafından döndürülen verileri temsil eden düğümleri **veri kaynakları** penceresine ekler.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimini tanımlama

WPF Tasarımcısında XAML 'yi değiştirerek pencereye birkaç düğme ekleyin. Bu izlenecek yolda daha sonra, kullanıcıların bu düğmeleri kullanarak satış kayıtlarını görüntülemesine ve güncelleştirmesine olanak tanıyan bir kod ekleyeceksiniz.

1. **Çözüm Gezgini**, **MainWindow. xaml**' ye çift tıklayın.

   Pencere WPF Tasarımcısı 'nda açılır.

2. [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]Tasarımcı görünümünde aşağıdaki kodu Etiketler arasına ekleyin `<Grid>` :

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

## <a name="create-the-data-bound-controls"></a>Veri bağlantılı denetimleri oluşturma

`SalesOrderHeaders`Düğümü **veri kaynakları** penceresinden tasarımcıya sürükleyerek müşteri kayıtlarını görüntüleyen denetimler oluşturun.

1. **Veri kaynakları** penceresinde, **SalesOrderHeaders** düğümünün açılan menüsüne tıklayın ve **Ayrıntılar**' ı seçin.

2. **SalesOrderHeaders** düğümünü genişletin.

3. Bu örnekte, bazı alanlar görüntülenmeyecektir, bu nedenle aşağıdaki düğümlerin yanındaki açılan menüye tıklayın ve **hiçbiri**' ni seçin:

    - **CreditCardApprovalCode**

    - **ModifiedDate & lt**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **rowguid**

    bu eylem, bir sonraki adımda bu düğümler için veri bağlantılı denetimler oluşturmasını Visual Studio engeller. Bu izlenecek yol için, son kullanıcının bu verileri görmesini gerektirmeyen varsayılmaktadır.

4. **Veri kaynakları** penceresinde, **SalesOrderHeaders** düğümünü düğmeleri içeren satırın altındaki kılavuz satırına sürükleyin.

     Visual Studio, **ürün** tablosundaki verilere bağlanan bir denetim kümesi oluşturan XAML ve kod oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [VISUAL STUDIO WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

5. Tasarımcıda **MÜŞTERI kimliği** etiketinin yanındaki metin kutusuna tıklayın.

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

     Visual Studio arka arkasındaki kod dosyasını açar ve olay için yeni `backButton_Click` bir olay <xref:System.Windows.Controls.Primitives.ButtonBase.Click> işleyicisi oluşturur.

2. Oluşturulan olay işleyiciye aşağıdaki `backButton_Click` kodu ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet3":::

3. Tasarımcıya geri dönüp düğmeye çift **>** tıklayın.

     Visual Studio arka arkasındaki kod dosyasını açar ve olay için yeni `nextButton_Click` bir olay <xref:System.Windows.Controls.Primitives.ButtonBase.Click> işleyicisi oluşturur.

4. Oluşturulan olay işleyiciye aşağıdaki `nextButton_Click` kodu ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb" id="Snippet4":::

## <a name="save-changes-to-sales-records"></a>Satış kayıtlarında yapılan değişiklikleri kaydetme

Kullanıcıların Değişiklikleri kaydet düğmesini kullanarak satış kayıtlarını görüntülemelerini ve kaydetmelerini sağlayan **kod** ekleyin:

1. Tasarımcıda Değişiklikleri Kaydet düğmesine **çift** tıklayın.

     Visual Studio arka arkasındaki kod dosyasını açar ve olay için yeni `saveButton_Click` bir olay <xref:System.Windows.Controls.Primitives.ButtonBase.Click> işleyicisi oluşturur.

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
