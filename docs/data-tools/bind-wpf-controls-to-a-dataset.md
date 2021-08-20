---
title: Bir veri kümesine WPF denetimleri bağlama
description: Bir veri kümesinde Visual Studio ürün kayıtlarına bağlı olan veriye bağlı denetimler içeren bir WPF uygulaması oluşturun.
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
ms.openlocfilehash: c0913e3d4f54f312e7d706ec6ab9771732e7b85c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059326"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Bir veri kümesine WPF denetimleri bağlama

Bu kılavuzda, veriye bağlı denetimler içeren bir WPF uygulaması oluşturabilirsiniz. Denetimler, bir veri kümesinde kapsüllene ürün kayıtlarına bağımlıdır. Ayrıca ürünlere göz atmak ve ürün kayıtlarında yapılan değişiklikleri kaydetmek için düğmeler de eklersiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- AdventureWorksLT örnek veritabanındaki verilerden oluşturulan bir WPF uygulaması ve veri kümesi oluşturma.

- Veri Kaynakları penceresindeki veri tablolarını WPF  Tasarımcısı'nda bir pencereye sürükleyerek veriye bağlı denetimler kümesi oluşturma.

- Ürün kayıtlarında ileri ve geri gezinen düğmeler oluşturma.

- Kullanıcıların ürün kayıtlarında yapacakları değişiklikleri veri tablosuna ve temel alınan veri kaynağına kaydeden bir düğme oluşturma.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio

- Üzerinde AdventureWorks Light (AdventureWorksLT) SQL Server veritabanı SQL Server Express çalışan bir SQL Server Express örneğine erişim. AdventureWorksLT veritabanını CodePlex arşivinden [indirebilirsiniz.](https://archive.codeplex.com/?p=awlt2008dbscript)

Aşağıdaki kavramlar hakkında önceden bilgi sahibi olmak da yararlıdır ancak izlenecek yolu tamamlamak için gerekli değildir:

- Veri kümeleri ve TableAdapter'lar. Daha fazla bilgi için [bkz. dataset tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [and TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- WPF veri bağlama. Daha fazla bilgi için bkz. [Veri Bağlamaya Genel Bakış.](/dotnet/desktop-wpf/data/data-binding-overview)

## <a name="create-the-project"></a>Proje oluşturma

Ürün kayıtlarını görüntülemek için yeni bir WPF projesi oluşturun.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

2. Dosya menüsünde **Yeni** **dosya'Project.** > 

3. visual **Visual Basic** veya **Visual C# öğesini genişletin** ve ardından Windows. 

4. **WPF Uygulaması proje** şablonunu seçin.

5. Ad **kutusuna** **AdventureWorksProductsEditor yazın ve** Tamam'ı **seçin.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. C# **WPF Uygulaması proje şablonunu** arayın ve projeyi oluşturmak için adımları izleyin ve **projeyi AdventureWorksProductsEditor olarak adlandırın.**

::: moniker-end

   Visual Studio AdventureWorksProductsEditor projesini oluşturur.

## <a name="create-a-dataset-for-the-application"></a>Uygulama için veri kümesi oluşturma

Veriye bağlı denetimler oluşturamadan önce, uygulamanıza bir veri modeli tanımlamanız ve Bunu Veri Kaynakları **penceresine eklemeniz** gerekir. Bu kılavuzda, veri modeli olarak kullanmak üzere bir veri kümesi oluşturabilirsiniz.

1. Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

   Veri **Kaynakları** penceresi açılır.

2. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'ye tıklayın.**

   Veri **Kaynağı Yapılandırma** sihirbazı açılır.

3. Veri Kaynağı **Türü Seçin sayfasında Veritabanı'yı** **seçin ve** ardından Sonraki'ye **tıklayın.**

4. Veritabanı Modeli **Seçin sayfasında Veri** Kümesi'ne tıklayın **ve** ardından Sonraki'ye **tıklayın.**

5. Veri **Bağlantınızı Seçin sayfasında** aşağıdaki seçeneklerden birini belirleyin:

   - Açılan listede AdventureWorksLT örnek veritabanına bir veri bağlantısı varsa bunu seçin ve ardından Sonraki 'ye **tıklayın.**

   - Yeni **Bağlantı'ya** tıklayın ve AdventureWorksLT veritabanına bir bağlantı oluşturun.

6. Bağlantı **Dizesini Uygulama Dosya Yapılandırma Sayfasına** Kaydet sayfasında **Evet,** bağlantıyı farklı kaydet onay kutusunu işaretleyin ve ardından Sonraki 'ye **tıklayın.**

7. Veritabanı **Nesnelerinizi Seçin sayfasında** Tablolar'ı **genişletin** ve ardından **Product (SalesLT) tablosuna** tıklayın.

8. **Finish (Son)** düğmesine tıklayın.

   Visual Studio projeye yeni bir dosya ekler ve Veri Kaynakları penceresine karşılık gelen `AdventureWorksLTDataSet.xsd` **AdventureWorksLTDataSet** **öğesini** ekler. Dosya, `AdventureWorksLTDataSet.xsd` adlı türüne göre bir veri kümesi `AdventureWorksLTDataSet` ve adlı tableAdapter `ProductTableAdapter` tanımlar. Bu kılavuzda daha sonra veri kümelerini verilerle doldurmak ve değişiklikleri `ProductTableAdapter` veritabanına geri kaydetmek için kullanacağız.

9. Projeyi derleyin.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>TableAdapter'ın varsayılan fill yöntemini düzenleme

Veri kümelerini verilerle doldurmak için `Fill` yöntemini `ProductTableAdapter` kullanın. Varsayılan olarak `Fill` yöntemi, içinde product `ProductDataTable` `AdventureWorksLTDataSet` tablosundan tüm veri satırlarıyla doldurur. Satırların yalnızca bir alt kümesini geri dönmek için bu yöntemi değiştirebilirsiniz. Bu kılavuzda yöntemini `Fill` değiştirerek yalnızca fotoğrafları olan ürünlere karşılık satırlar getirebilirsiniz.

1. Bu **Çözüm Gezgini** *AdventureWorksLTDataSet.xsd dosyasına çift* tıklayın.

     Veri kümesi tasarımcısı açılır.

2. Tasarımcıda Fill , **GetData()** **sorgusuna** sağ tıklayın ve Yapılandır'ı **seçin.**

     **TableAdapter Yapılandırma** sihirbazı açılır.

3. SQL **Deyimi girin sayfasında,** metin kutusuna deyiminden sonra aşağıdaki WHERE `SELECT` yan tümcesini ekleyin.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. **Finish (Son)** düğmesine tıklayın.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimini tanımlama

WPF Tasarımcısı'nda XAML'yi değiştirerek pencereye birkaç düğme ekleyin. Bu kılavuzda daha sonra kullanıcıların bu düğmeleri kullanarak ürün kayıtlarında kaydırma ve değişiklik kaydetmelerini sağlayan kod eklenecektir.

1. Içinde **Çözüm Gezgini** *MainWindow.xaml'e çift tıklayın.*

    Pencere **WPF Tasarımcısı'nda açılır.**

2. Tasarımcı [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] görünümünde, etiketlerin arasına aşağıdaki kodu `<Grid>` ekleyin:

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

## <a name="create-data-bound-controls"></a>Veriye bağlı denetimler oluşturma

Veri Kaynakları penceresindeki tabloyu `Product` WPF Tasarımcısına **sürükleyerek müşteri** kayıtlarını görüntülüyor denetimler oluşturun.

1. Veri **Kaynakları penceresinde** Ürün düğümü için açılan menüye tıklayın ve **Ayrıntılar'ı** **seçin.**

2. Ürün **düğümünü** genişletin.

3. Bu örnekte bazı alanlar görüntülenmez, bu nedenle aşağıdaki düğümlerin yanındaki açılan menüye tıklayın ve Yok'u **seçin:**

    - ProductCategoryID

    - Productmodelıd

    - ThumbnailPhotoFileName

    - Rowguıd

    - Modifieddate

4. **ThumbNailPhoto** düğümünün yanındaki açılan menüye tıklayın ve Görüntü'yü **seçin.**

    > [!NOTE]
    > Varsayılan olarak, Veri Kaynakları penceresinde **resimleri temsil** eden öğelerin varsayılan denetimi Yok olarak **ayarlanır.** Bunun nedeni resimlerin veritabanlarında bayt dizileri olarak depolanmış ve bayt dizilerinin basit bir bayt dizisinde büyük bir uygulamanın yürütülebilir dosyasına kadar her şeyi içermesidir.

5. Veri **Kaynakları penceresinden** Product **düğümünü** düğmeleri içeren satırın altındaki kılavuz satırına sürükleyin.

     Visual Studio, **Products** tablosunda verilere bağlı bir denetim kümesi tanımlayan XAML üretir. Ayrıca verileri yüken kod da üretir. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [WPF denetimlerini](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)Visual Studio.

6. Tasarımcıda Ürün Kimliği etiketinin yanındaki metin **kutusuna** tıklayın.

7. Özellikler **penceresinde** **IsReadOnly** özelliğinin yanındaki onay kutusunu seçin.

## <a name="navigate-product-records"></a>Ürün kayıtlarına gidin

Kullanıcıların düğmeleri kullanarak ürün kayıtları arasında kaydırmalarını sağlayan kod **\<** and **>** ekleyin.

1. Tasarımcıda pencere **<** yüzeyindeki düğmeye çift tıklayın.

     Visual Studio arka arkasındaki kod dosyasını açar ve olay için yeni `backButton_Click` bir olay <xref:System.Windows.Controls.Primitives.ButtonBase.Click> işleyicisi oluşturur.

2. Olay `Window_Loaded` işleyicisini değiştirerek `ProductViewSource` , `AdventureWorksLTDataSet` ve `AdventureWorksLTDataSetProductTableAdapter` yöntemlerinin dışında olmasını ve formun tamamına erişilsin. Yalnızca bunları forma genel olacak şekilde bildirin ve bunları aşağıdakine benzer `Window_Loaded` bir olay işleyicisi içinde attayabilirsiniz:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet1":::

3. Olay işleyiciye aşağıdaki `backButton_Click` kodu ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet2":::

4. Tasarımcıya geri dönüp düğmeye çift **>** tıklayın.

5. Olay işleyiciye aşağıdaki `nextButton_Click` kodu ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet3":::

## <a name="save-changes-to-product-records"></a>Ürün kayıtlarında yapılan değişiklikleri kaydetme

Kullanıcıların Değişiklikleri kaydet düğmesini kullanarak ürün kayıtlarına değişiklikleri kaydetmelerini sağlayan **kod** ekleyin.

1. Tasarımcıda Değişiklikleri kaydet düğmesine **çift** tıklayın.

     Visual Studio arka plan kod dosyasını açar ve `saveButton_Click` olay için yeni bir olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Aşağıdaki kodu `saveButton_Click` olay işleyicisine ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb" id="Snippet4":::

    > [!NOTE]
    > Bu örnek `Save` , `TableAdapter` değişiklikleri kaydetmek için yöntemini kullanır. Yalnızca bir veri tablosu değiştiğinden bu izlenecek yol için uygundur. birden çok veri tablosuna yaptığınız değişiklikleri kaydetmeniz gerekiyorsa, bunun yerine, `UpdateAll` `TableAdapterManager` veri kümeniz ile birlikte Visual Studio yöntemini kullanabilirsiniz. Daha fazla bilgi için bkz. [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Uygulamayı test edin

Uygulamayı derleyin ve çalıştırın. Ürün kayıtlarını görüntüleyebildiğinizi ve güncelleştirebildiğinizi doğrulayın.

1. **F5** tuşuna basın.

     Uygulama oluşturulur ve çalışır. Aşağıdakileri doğrulayın:

    - Metin kutuları, fotoğrafı olan ilk ürün kaydından verileri görüntüler. Bu ürünün 713 ürün KIMLIĞI ve **uzun süreli logo adı Ile Jersey, S**.

    - **>** **<** Diğer ürün kayıtları arasında gezinmek için veya düğmelerine tıklayabilirsiniz.

2. Ürün kayıtlarından birinde, **Boyut** değerini değiştirin ve ardından **Değişiklikleri Kaydet**' e tıklayın.

3. Uygulamayı kapatın ve ardından Visual Studio ' de **F5** tuşuna basarak uygulamayı yeniden başlatın.

4. Değiştirdiğiniz ürün kaydına gidin ve değişikliğin kalıcı olduğunu doğrulayın.

5. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki adımlar

Bu yönergeyi tamamladıktan sonra, aşağıdaki ilgili görevleri deneyebilirsiniz:

- WPF denetimlerini diğer veri kaynağı türlerine bağlamak için Visual Studio **veri kaynakları** penceresini nasıl kullanacağınızı öğrenin. Daha fazla bilgi için bkz. [BIR WCF veri HIZMETINE WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- WPF denetimlerinde ilgili verileri (yani bir üst-alt ilişkisi içindeki verileri) göstermek için Visual Studio **veri kaynakları** penceresini nasıl kullanacağınızı öğrenin. Daha fazla bilgi için bkz. [Izlenecek yol: BIR WPF uygulamasında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visual Studio'daki veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md)
- [Veri Bağlamaya Genel Bakış](/dotnet/desktop-wpf/data/data-binding-overview)
