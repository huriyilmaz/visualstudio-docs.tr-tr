---
title: Bir veri kümesine WPF denetimleri bağlama
description: bir veri kümesinde kapsüllenmiş ürün kayıtlarına bağlanan veri bağlantılı denetimleri içeren Visual Studio bir WPF uygulaması oluşturun.
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
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7f1188df1a13d83964f455738250544149d7044e
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127435"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Bir veri kümesine WPF denetimleri bağlama

Bu izlenecek yolda, veri bağlantılı denetimler içeren bir WPF uygulaması oluşturacaksınız. Denetimler, bir veri kümesinde kapsüllenmiş ürün kayıtlarına bağlanır. Ayrıca, ürünlere göz atıp ürün kayıtlarına yapılan değişiklikleri kaydetmek için düğmeler de eklersiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir WPF uygulaması ve AdventureWorksLT örnek veritabanındaki verilerden oluşturulan bir veri kümesi oluşturma.

- Veri **kaynakları** penceresinden WPF Tasarımcısı 'ndaki bir pencereye bir veri tablosu sürükleyerek veri bağlantılı denetimler kümesi oluşturma.

- Ürün kayıtları arasında ileri ve geri gitmek için düğmeler oluşturma.

- Kullanıcıların ürün kayıtlarında veri tablosuna ve temel alınan veri kaynağına yaptığı değişiklikleri kaydeden bir düğme oluşturma.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

- çalışan bir SQL Server veya SQL Server Express, kendisine eklenmiş olan AdventureWorks Light (AdventureWorksLT) örnek veritabanının bulunduğu bir örneğe erişim. Veritabanını indirmek için bkz. [AdventureWorks örnek veritabanları](/sql/samples/adventureworks-install-configure?tabs=ssms).

Aşağıdaki kavramların önceki bilgileri de yararlı olmakla kalmaz, izlenecek yolu tamamlamak için gerekli değildir:

- Veri kümeleri ve TableAdapters. daha fazla bilgi için bkz. Visual Studio ve [TableAdapters](../data-tools/create-and-configure-tableadapters.md) [içinde veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md) .

- WPF veri bağlama. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Proje oluşturma

Ürün kayıtlarını göstermek için yeni bir WPF projesi oluşturun.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. **dosya** menüsünde **yeni** > **Project**' yi seçin.

3. **Visual Basic** veya **Visual C#**' yi genişletin ve **Windows**' ı seçin.

4. **WPF uygulaması** proje şablonunu seçin.

5. **Ad** kutusuna **AdventureWorksProductsEditor** girin ve sonra **Tamam**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. C# **WPF uygulaması** proje şablonunu arayın ve projeyi oluşturmak Için proje **AdventureWorksProductsEditor** adlandırarak adımları izleyin.

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

8. **Finish (Son)** düğmesine tıklayın.

   Visual Studio projeye yeni bir `AdventureWorksLTDataSet.xsd` dosya ekler ve **veri kaynakları** penceresine karşılık gelen bir **AdventureWorksLTDataSet** öğesi ekler. `AdventureWorksLTDataSet.xsd`Dosya adlı türü belirtilmiş bir veri kümesini `AdventureWorksLTDataSet` ve adında bir TableAdapter tanımlar `ProductTableAdapter` . Bu izlenecek yolda daha sonra, `ProductTableAdapter` veri kümesini verilerle birlikte doldurmanız ve değişiklikleri veritabanına geri kaydetmek için öğesini kullanacaksınız.

9. Projeyi derleyin.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>TableAdapter 'ın varsayılan Fill metodunu düzenleme

Veri kümesini verilerle birlikte doldurmanız için `Fill` yöntemini kullanın `ProductTableAdapter` . Varsayılan olarak, `Fill` Yöntemi öğesini `ProductDataTable` `AdventureWorksLTDataSet` ürün tablosundaki tüm veri satırlarıyla doldurur. Bu yöntemi, yalnızca satırların bir alt kümesini döndürecek şekilde değiştirebilirsiniz. Bu izlenecek yol için, `Fill` yöntemini yalnızca fotoğrafların bulunduğu ürünlerin satırlarını döndürecek şekilde değiştirin.

1. **Çözüm Gezgini**, The *AdventureWorksLTDataSet. xsd* dosyasını çift tıklayın.

     Veri kümesi Tasarımcısı açılır.

2. Tasarımcıda **Fill**, **GetData ()** sorgusuna sağ tıklayın ve **Yapılandır**' ı seçin.

     **TableAdapter Yapılandırma** Sihirbazı açılır.

3. **SQL deyimi girin** sayfasında, `SELECT` metin kutusundaki deyimden sonra aşağıdaki where yan tümcesini ekleyin.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. **Finish (Son)** düğmesine tıklayın.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimini tanımlama

WPF Tasarımcısında XAML 'yi değiştirerek pencereye birkaç düğme ekleyin. Bu izlenecek yolda daha sonra, kullanıcıların bu düğmeleri kullanarak ürün kayıtlarında gezinmelerini ve değişiklikleri kaydetmesini sağlayan bir kod ekleyeceksiniz.

1. **Çözüm Gezgini**, *MainWindow. xaml*' ye çift tıklayın.

    Pencere **WPF Tasarımcısı**'nda açılır.

2. [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]Tasarımcı görünümünde aşağıdaki kodu Etiketler arasına ekleyin `<Grid>` :

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75">&lt;</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">&gt;</Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Projeyi derleyin.

## <a name="create-data-bound-controls"></a>Veri bağlantılı denetimler oluşturma

`Product`Tabloyu **veri kaynakları** penceresinden WPF tasarımcısına sürükleyerek müşteri kayıtlarını görüntüleyen denetimler oluşturun.

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
    > Varsayılan olarak, resimleri temsil eden **veri kaynakları** penceresindeki öğelerin varsayılan denetimleri **none** olarak ayarlanmıştır. Bunun nedeni, resimlerin veritabanlarında bayt dizileri olarak depolanmasıdır ve bayt dizileri basit bir bayt dizisinden büyük bir uygulamanın yürütülebilir dosyasına kadar herhangi bir şeyi içerebilir.

5. **Veri kaynakları** penceresinde, **ürün** düğümünü düğmeleri içeren satırın altındaki kılavuz satırına sürükleyin.

     Visual Studio, **Products** tablosundaki verilere bağlanan bir denetim kümesini tanımlayan XAML oluşturur. Ayrıca, verileri yükleyen kodu oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [VISUAL STUDIO WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Tasarımcıda **ürün kimliği** etiketinin yanındaki metin kutusuna tıklayın.

7. **Özellikler** penceresinde, **IsReadOnly** özelliğinin yanındaki onay kutusunu işaretleyin.

## <a name="navigate-product-records"></a>Ürün kayıtlarında gezin

Kullanıcıların, düğmeleri kullanarak ürün kayıtları arasında gezinmelerini sağlayan kod ekleyin **\<** and **>** .

1. Tasarımcıda **<** pencere yüzeyinde düğmesine çift tıklayın.

     Visual Studio arka plan kod dosyasını açar ve `backButton_Click` olay için yeni bir olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. ,, Ve,,, `Window_Loaded` `ProductViewSource` `AdventureWorksLTDataSet` ve `AdventureWorksLTDataSetProductTableAdapter` tüm form için erişilebilir olan olay işleyicisini değiştirin. Yalnızca bu form için genel olacak şekilde bildirme ve bunları `Window_Loaded` Şuna benzer olay işleyicisi içinde atama:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet1":::

3. Aşağıdaki kodu `backButton_Click` olay işleyicisine ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet2":::

4. Tasarımcıya dönün ve düğmeye çift tıklayın **>** .

5. Aşağıdaki kodu `nextButton_Click` olay işleyicisine ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet3":::

## <a name="save-changes-to-product-records"></a>Ürün kayıtlarında yapılan değişiklikleri Kaydet

**Değişiklikleri Kaydet** düğmesini kullanarak kullanıcıların ürün kayıtlarında değişiklik kaydetmesine olanak tanıyan kodu ekleyin.

1. Tasarımcıda **Değişiklikleri Kaydet** düğmesine çift tıklayın.

     Visual Studio arka kapı kod dosyasını açar ve olay için yeni `saveButton_Click` bir olay <xref:System.Windows.Controls.Primitives.ButtonBase.Click> işleyicisi oluşturur.

2. Olay işleyiciye aşağıdaki `saveButton_Click` kodu ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet4":::

    > [!NOTE]
    > Bu örnek, `Save` değişiklikleri kaydetmek için yöntemini `TableAdapter` kullanır. Yalnızca bir veri tablosu değiştiri olduğundan, bu kılavuzda bu uygundur. Değişiklikleri birden çok veri tablosuna kaydetmeniz gerekirse, alternatif olarak veri kümeniz `UpdateAll` ile oluşturulan Visual Studio yöntemini `TableAdapterManager` kullanabilirsiniz. Daha fazla bilgi için bkz. [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Uygulamayı test edin

Uygulamayı derleyin ve çalıştırın. Ürün kayıtlarını görüntüleye ve güncelleştirenizi doğrulayın.

1. **F5 tuşuna basın.**

     Uygulama derleme ve çalıştırma. Aşağıdakileri doğrulayın:

    - Metin kutuları, fotoğrafa sahip ilk ürün kaydından verileri görüntüler. Bu ürün, 713 ürün kimliğine ve **Long-......Logo Logo Logo S adına sahip.**

    - Veya düğmelerine **>** **<** tıklar ve diğer ürün kayıtları arasında gezinebilirsiniz.

2. Ürün kayıtlarından birinin Boyut değerini ve ardından **Değişiklikleri** kaydet'e **tıklayın.**

3. Uygulamayı kapatın ve sonra uygulamanın içinde **F5** tuşuna basarak uygulamayı Visual Studio.

4. Değiştirmiş olduğunu ürün kaydına gidin ve değişikliğin kalıcı olduğunu doğrulayın.

5. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu izlenecek yolu tamamladıktan sonra aşağıdaki ilgili görevleri denemeyi ebilirsiniz:

- WPF denetimlerini **diğer veri** kaynağı türlerine bağlamak Visual Studio veri kaynakları penceresinin nasıl kullanacağını öğrenin. Daha fazla bilgi için [bkz. WPF denetimlerini bir WCF veri hizmetine bağlama.](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)

- WPF denetimlerini **kullanarak** ilgili Visual Studio (üst-alt ilişki içindeki veriler) görüntülemek için veri kaynakları penceresini kullanmayı öğrenin. Daha fazla bilgi için [bkz. Adım adım: WPF uygulamasında ilgili verileri görüntüleme.](../data-tools/display-related-data-in-wpf-applications.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Veri Bağlamaya Genel Bakış](/dotnet/desktop-wpf/data/data-binding-overview)
