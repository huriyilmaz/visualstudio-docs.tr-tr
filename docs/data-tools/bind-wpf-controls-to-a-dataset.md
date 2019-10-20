---
title: Bir veri kümesine WPF denetimleri bağlama
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 56c49f0d3cef6dbb054c8d7d97b4e875b83cb518
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648812"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Bir veri kümesine WPF denetimleri bağlama

Bu izlenecek yolda, veri bağlantılı denetimler içeren bir WPF uygulaması oluşturacaksınız. Denetimler, bir veri kümesinde kapsüllenmiş ürün kayıtlarına bağlanır. Ayrıca, ürünlere göz atıp ürün kayıtlarına yapılan değişiklikleri kaydetmek için düğmeler de eklersiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir WPF uygulaması ve AdventureWorksLT örnek veritabanındaki verilerden oluşturulan bir veri kümesi oluşturma.

- Veri **kaynakları** penceresinden WPF Tasarımcısı 'ndaki bir pencereye bir veri tablosu sürükleyerek veri bağlantılı denetimler kümesi oluşturma.

- Ürün kayıtları arasında ileri ve geri gitmek için düğmeler oluşturma.

- Kullanıcıların ürün kayıtlarında veri tablosuna ve temel alınan veri kaynağına yaptığı değişiklikleri kaydeden bir düğme oluşturma.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

- Çalışan bir SQL Server veya SQL Server Express, kendisine eklenmiş olan AdventureWorks Light (AdventureWorksLT) örnek veritabanının bulunduğu bir örneğe erişim. AdventureWorksLT veritabanını [CodePlex Arşivi](https://archive.codeplex.com/?p=awlt2008dbscript)' nden indirebilirsiniz.

Aşağıdaki kavramların önceki bilgileri de yararlı olmakla kalmaz, izlenecek yolu tamamlamak için gerekli değildir:

- Veri kümeleri ve TableAdapters. Daha fazla bilgi için bkz. [Visual Studio 'Da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md) ve [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- WPF veri bağlama. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Projeyi oluşturma

Ürün kayıtlarını göstermek için yeni bir WPF projesi oluşturun.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. **Dosya** menüsünde **Yeni** > **Proje**' yi seçin.

3. **Visual Basic** veya **görsel C#** ' i genişletin ve ardından **Windows**' u seçin.

4. **WPF uygulaması** proje şablonunu seçin.

5. **Ad** kutusuna **AdventureWorksProductsEditor** girin ve sonra **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. C# **WPF uygulaması** proje şablonunu arayın ve projeyi oluşturmak için proje **AdventureWorksProductsEditor**adlandırarak adımları izleyin.

::: moniker-end

   Visual Studio, AdventureWorksProductsEditor projesi oluşturur.

## <a name="create-a-dataset-for-the-application"></a>Uygulama için bir veri kümesi oluşturma

Veriye dayalı denetimler oluşturabilmeniz için önce uygulamanız için bir veri modeli tanımlamanız ve **veri kaynakları** penceresine eklemeniz gerekir. Bu kılavuzda, veri modeli olarak kullanılacak bir veri kümesi oluşturacaksınız.

1. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

   **Veri kaynakları** penceresi açılır.

2. **Veri kaynakları** penceresinde **Yeni veri kaynağı Ekle**' ye tıklayın.

   **Veri kaynağı yapılandırma** Sihirbazı açılır.

3. **Veri kaynağı türü seç** sayfasında, **veritabanı**' nı seçin ve ardından **İleri**' ye tıklayın.

4. **Veritabanı modeli seçin** sayfasında **veri kümesi**' ni seçin ve ardından **İleri**' ye tıklayın.

5. **Veri bağlantınızı seçin** sayfasında, aşağıdaki seçeneklerden birini belirleyin:

   - Aşağı açılan listede AdventureWorksLT örnek veritabanıyla bir veri bağlantısı varsa, bunu seçin ve ardından **İleri**' ye tıklayın.

   - **Yeni bağlantı**' ya tıklayın ve AdventureWorksLT veritabanına bir bağlantı oluşturun.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, Evet ' i seçin **, bağlantıyı farklı kaydet** onay kutusunu işaretleyin ve ardından **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar**' ı genişletin ve ardından **ürün (SalesLT)** tablosunu seçin.

8. **Son**'a tıklayın.

   Visual Studio, projeye yeni bir `AdventureWorksLTDataSet.xsd` dosyası ekler ve **veri kaynakları** penceresine karşılık gelen bir **AdventureWorksLTDataSet** öğesi ekler. @No__t_0 dosyası, `AdventureWorksLTDataSet` adlı türü belirtilmiş bir veri kümesini ve `ProductTableAdapter` adlı TableAdapter 'ı tanımlar. Bu izlenecek yolda daha sonra, veri kümesini verilerle birlikte doldurmanız ve değişiklikleri veritabanına geri kaydetmek için `ProductTableAdapter` kullanacaksınız.

9. Projeyi oluşturun.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>TableAdapter 'ın varsayılan Fill metodunu düzenleme

Veri kümesini verilerle birlikte doldurmanız için `ProductTableAdapter` `Fill` yöntemini kullanın. @No__t_0 yöntemi, varsayılan olarak, ürün tablosundaki tüm veri satırlarıyla `AdventureWorksLTDataSet` `ProductDataTable` doldurur. Bu yöntemi, yalnızca satırların bir alt kümesini döndürecek şekilde değiştirebilirsiniz. Bu izlenecek yol için `Fill` yöntemini yalnızca fotoğrafların bulunduğu ürünlerin satırlarını döndürecek şekilde değiştirin.

1. **Çözüm Gezgini**, The *AdventureWorksLTDataSet. xsd* dosyasını çift tıklayın.

     Veri kümesi Tasarımcısı açılır.

2. Tasarımcıda **Fill**, **GetData ()** sorgusuna sağ tıklayın ve **Yapılandır**' ı seçin.

     **TableAdapter Yapılandırma** Sihirbazı açılır.

3. **BIR SQL deyimi girin** sayfasında, metin kutusundaki `SELECT` deyimden sonra aşağıdaki where yan tümcesini ekleyin.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. **Son**'a tıklayın.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimini tanımlama

WPF Tasarımcısında XAML 'yi değiştirerek pencereye birkaç düğme ekleyin. Bu izlenecek yolda daha sonra, kullanıcıların bu düğmeleri kullanarak ürün kayıtlarında gezinmelerini ve değişiklikleri kaydetmesini sağlayan bir kod ekleyeceksiniz.

1. **Çözüm Gezgini**, *MainWindow. xaml*' ye çift tıklayın.

    Pencere **WPF Tasarımcısı**'nda açılır.

2. Tasarımcının [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] görünümünde, `<Grid>` etiketleri arasına aşağıdaki kodu ekleyin:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Projeyi oluşturun.

## <a name="create-data-bound-controls"></a>Veri bağlantılı denetimler oluşturma

@No__t_0 tablosunu **veri kaynakları** penceresinden WPF tasarımcısına sürükleyerek müşteri kayıtlarını görüntüleyen denetimler oluşturun.

1. **Veri kaynakları** penceresinde, **ürün** düğümünün açılan menüsüne tıklayın ve **Ayrıntılar**' ı seçin.

2. **Ürün** düğümünü genişletin.

3. Bu örnekte, bazı alanlar görüntülenmeyecektir, bu nedenle aşağıdaki düğümlerin yanındaki açılan menüye tıklayın ve **hiçbiri**' ni seçin:

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate & lt

4. **ThumbnailPhoto** düğümünün yanındaki açılan menüye tıklayın ve **görüntü**' ı seçin.

    > [!NOTE]
    > Varsayılan olarak, resimleri temsil eden **veri kaynakları** penceresindeki öğelerin varsayılan denetimleri **none**olarak ayarlanmıştır. Bunun nedeni, resimlerin veritabanlarında bayt dizileri olarak depolanmasıdır ve bayt dizileri basit bir bayt dizisinden büyük bir uygulamanın yürütülebilir dosyasına kadar herhangi bir şeyi içerebilir.

5. **Veri kaynakları** penceresinde, **ürün** düğümünü düğmeleri içeren satırın altındaki kılavuz satırına sürükleyin.

     Visual Studio, **Ürünler** tablosundaki verilere bağlanan bir denetim KÜMESINI tanımlayan xaml oluşturur. Ayrıca, verileri yükleyen kodu oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Tasarımcıda **ürün kimliği** etiketinin yanındaki metin kutusuna tıklayın.

7. **Özellikler** penceresinde, **IsReadOnly** özelliğinin yanındaki onay kutusunu işaretleyin.

## <a name="navigate-product-records"></a>Ürün kayıtlarında gezin

Kullanıcıların, **\<** ve **>** düğmelerini kullanarak ürün kayıtları arasında gezinmelerini sağlayan kod ekleyin.

1. Tasarımcıda pencere yüzeyinde **<** düğmesine çift tıklayın.

     Visual Studio, arka plan kod dosyasını açar ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için yeni bir `backButton_Click` olay işleyicisi oluşturur.

2. @No__t_0 olay işleyicisini değiştirin, böylece `ProductViewSource`, `AdventureWorksLTDataSet` ve `AdventureWorksLTDataSetProductTableAdapter` yönteminin dışında ve formun tamamına erişilebilir. Yalnızca form için genel olacak şekilde bildirme ve bunları şuna benzer `Window_Loaded` olay işleyicisi içinde atama:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3. @No__t_0 olay işleyicisine aşağıdaki kodu ekleyin:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4. Tasarımcıya dönün ve **>** düğmesine çift tıklayın.

5. @No__t_0 olay işleyicisine aşağıdaki kodu ekleyin:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Ürün kayıtlarında yapılan değişiklikleri Kaydet

**Değişiklikleri Kaydet** düğmesini kullanarak kullanıcıların ürün kayıtlarında değişiklik kaydetmesine olanak tanıyan kodu ekleyin.

1. Tasarımcıda **Değişiklikleri Kaydet** düğmesine çift tıklayın.

     Visual Studio, arka plan kod dosyasını açar ve <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için yeni bir `saveButton_Click` olay işleyicisi oluşturur.

2. @No__t_0 olay işleyicisine aşağıdaki kodu ekleyin:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > Bu örnekte, değişiklikleri kaydetmek için `TableAdapter` `Save` yöntemi kullanılmaktadır. Yalnızca bir veri tablosu değiştiğinden bu izlenecek yol için uygundur. Birden çok veri tablosuna yaptığınız değişiklikleri kaydetmeniz gerekiyorsa alternatif olarak, Visual Studio 'nun veri kümeniz ile oluşturduğu `TableAdapterManager` `UpdateAll` yöntemini kullanabilirsiniz. Daha fazla bilgi için bkz. [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Uygulamayı test etme

Uygulamayı derleyin ve çalıştırın. Ürün kayıtlarını görüntüleyebildiğinizi ve güncelleştirebildiğinizi doğrulayın.

1. **F5**tuşuna basın.

     Uygulama oluşturulur ve çalışır. Aşağıdakileri doğrulayın:

    - Metin kutuları, fotoğrafı olan ilk ürün kaydından verileri görüntüler. Bu ürünün 713 ürün KIMLIĞI ve **uzun süreli logo adı Ile Jersey, S**.

    - Diğer ürün kayıtlarında gezinmek için **>** ya da **<** düğmelerine tıklayabilirsiniz.

2. Ürün kayıtlarından birinde, **Boyut** değerini değiştirin ve ardından **Değişiklikleri Kaydet**' e tıklayın.

3. Uygulamayı kapatın ve ardından Visual Studio 'da **F5** tuşuna basarak uygulamayı yeniden başlatın.

4. Değiştirdiğiniz ürün kaydına gidin ve değişikliğin kalıcı olduğunu doğrulayın.

5. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu yönergeyi tamamladıktan sonra, aşağıdaki ilgili görevleri deneyebilirsiniz:

- Visual Studio 'daki **veri kaynakları** PENCERESINI kullanarak WPF denetimlerini diğer veri kaynağı türlerine bağlamayı öğrenin. Daha fazla bilgi için bkz. [BIR WCF veri HIZMETINE WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Visual Studio 'daki **veri kaynakları** PENCERESINI kullanarak WPF denetimlerinde ilgili verileri (yani bir üst-alt ilişkisi içindeki verileri) görüntüleme hakkında bilgi edinin. Daha fazla bilgi için bkz. [Izlenecek yol: BIR WPF uygulamasında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Veri Bağlamaya Genel Bakış](/dotnet/framework/wpf/data/data-binding-overview)
