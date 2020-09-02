---
title: Veri kümesine WPF denetimleri bağlama | Microsoft Docs
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
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 937e28e923c26a72940b0181da16cf34199bb9aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852150"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Bir veri kümesine WPF denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda, veri bağlantılı denetimler içeren bir WPF uygulaması oluşturacaksınız. Denetimler, bir veri kümesinde kapsüllenmiş ürün kayıtlarına bağlanır. Ayrıca, ürünlere göz atmanızı ve ürün kayıtlarına yapılan değişiklikleri kaydetmenizi sağlayacak düğmeler de ekleyeceksiniz.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir WPF uygulaması ve AdventureWorksLT örnek veritabanındaki verilerden oluşturulan bir veri kümesi oluşturma.

- Veri **kaynakları** penceresinden WPF Tasarımcısı 'ndaki bir pencereye bir veri tablosu sürükleyerek veri bağlantılı denetimler kümesi oluşturma.

- Ürün kayıtları arasında ileri ve geri gitmek için düğmeler oluşturma.

- Kullanıcıların ürün kayıtlarında veri tablosuna ve temel alınan veri kaynağına yaptığı değişiklikleri kaydeden bir düğme oluşturma.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- AdventureWorksLT örnek veritabanının eklendiği SQL Server veya SQL Server Express çalışan bir örneğine erişim. AdventureWorksLT veritabanını [CodePlex Web sitesinden](https://codeplex.com/SqlServerSamples)indirebilirsiniz.

  Aşağıdaki kavramların önceki bilgileri de yararlı olmakla kalmaz, izlenecek yolu tamamlamak için gerekli değildir:

- Veri kümeleri ve TableAdapters. Daha fazla bilgi için bkz. [Visual Studio 'Da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md).

- WPF Tasarımcısı ile çalışma. Daha fazla bilgi için bkz. [WPF ve Silverlight tasarımcısına genel bakış](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- WPF veri bağlama. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="create-the-project"></a>Proje oluşturma
 Yeni bir WPF projesi oluşturun. Projede ürün kayıtları görüntülenir.

#### <a name="to-create-the-project"></a>Proje oluşturmak için

1. Visual Studio’yu çalıştırın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. **Visual Basic** veya **Visual C#**' yi genişletin ve ardından **Windows**' u seçin.

4. **WPF uygulaması** proje şablonunu seçin.

5. **Ad** kutusuna yazın `AdventureWorksProductsEditor` ve **Tamam**' ı tıklatın.

     Visual Studio projeyi oluşturur `AdventureWorksProductsEditor` .

## <a name="create-a-dataset-for-the-application"></a>Uygulama için bir veri kümesi oluşturma
 Veriye dayalı denetimler oluşturabilmeniz için önce uygulamanız için bir veri modeli tanımlamanız ve **veri kaynakları** penceresine eklemeniz gerekir. Bu kılavuzda, veri modeli olarak kullanılacak bir veri kümesi oluşturacaksınız.

#### <a name="to-create-a-dataset"></a>Bir veri kümesi oluşturmak için

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

     Visual Studio, projeye yeni bir AdventureWorksLTDataSet. xsd dosyası ekler ve **veri kaynakları** penceresine karşılık gelen bir **AdventureWorksLTDataSet** öğesi ekler. AdventureWorksLTDataSet. xsd dosyası adlandırılmış bir veri kümesini `AdventureWorksLTDataSet` ve adında bir TableAdapter tanımlar `ProductTableAdapter` . Bu izlenecek yolda daha sonra, `ProductTableAdapter` veri kümesini verilerle birlikte doldurmanız ve değişiklikleri veritabanına geri kaydetmek için öğesini kullanacaksınız.

9. Projeyi derleyin.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>TableAdapter 'ın varsayılan Fill metodunu düzenleme
 Veri kümesini verilerle birlikte doldurmanız için `Fill` yöntemini kullanın `ProductTableAdapter` . Varsayılan olarak, `Fill` Yöntemi öğesini `ProductDataTable` `AdventureWorksLTDataSet` ürün tablosundaki tüm veri satırlarıyla doldurur. Bu yöntemi, yalnızca satırların bir alt kümesini döndürecek şekilde değiştirebilirsiniz. Bu izlenecek yol için, `Fill` yöntemini yalnızca fotoğrafların bulunduğu ürünlerin satırlarını döndürecek şekilde değiştirin.

#### <a name="to-load-product-rows-that-have-photos"></a>Fotoğraflara sahip ürün satırlarını yüklemek için

1. **Çözüm Gezgini**, The AdventureWorksLTDataSet. xsd dosyasını çift tıklayın.

     Veri kümesi Tasarımcısı açılır.

2. Tasarımcıda **Fill, GetData ()** sorgusuna sağ tıklayın ve **Yapılandır**' ı seçin.

     **TableAdapter Yapılandırma** Sihirbazı açılır.

3. **BIR SQL deyimi girin** sayfasında, `SELECT` metin kutusundaki deyimden sonra aşağıdaki where yan tümcesini ekleyin.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. **Son**'a tıklayın.

## <a name="define-the-user-interface"></a>Kullanıcı arabirimini tanımlama
 WPF Tasarımcısında XAML 'yi değiştirerek pencereye birkaç düğme ekleyin. Bu izlenecek yolda daha sonra, kullanıcıların bu düğmeleri kullanarak ürün kayıtlarında gezinmelerini ve değişiklikleri kaydetmesini sağlayan bir kod ekleyeceksiniz.

#### <a name="to-define-the-user-interface-of-the-window"></a>Pencerenin Kullanıcı arabirimini tanımlamak için

1. **Çözüm Gezgini**, MainWindow. xaml ' ye çift tıklayın.

     Pencere WPF Tasarımcısı 'nda açılır.

2. [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]Tasarımcı görünümünde aşağıdaki kodu Etiketler arasına ekleyin `<Grid>` :

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. Projeyi derleyin.

## <a name="createdata-bound-controls"></a>Createdata bağlantılı denetimler
 `Product`Tabloyu **veri kaynakları** penceresinden WPF tasarımcısına sürükleyerek müşteri kayıtlarını görüntüleyen denetimler oluşturun.

#### <a name="to-create-data-bound-controls"></a>Veri bağlantılı denetimler oluşturmak için

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

     Visual Studio, **Ürünler** tablosundaki verilere bağlanan bir denetim KÜMESINI tanımlayan xaml oluşturur. Ayrıca, verileri yükleyen kodu oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. Tasarımcıda **ürün kimliği** etiketinin yanındaki metin kutusuna tıklayın.

7. **Özellikler** penceresinde, **IsReadOnly** özelliğinin yanındaki onay kutusunu işaretleyin.

## <a name="navigating-product-records"></a>Ürün kayıtlarına gitme
 Kullanıcıların, düğmeleri kullanarak ürün kayıtları arasında gezinmelerini sağlayan kod ekleyin **\<** and **>** .

#### <a name="to-enable-users-to-navigate-product-records"></a>Kullanıcıların ürün kayıtlarına gitmesini sağlamak için

1. Tasarımcıda **<** pencere yüzeyinde düğmesine çift tıklayın.

     Visual Studio, arka plan kod dosyasını açar ve olay için yeni bir `backButton_Click` olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. ,, Ve,,, `Window_Loaded` `ProductViewSource` `AdventureWorksLTDataSet` ve `AdventureWorksLTDataSetProductTableAdapter` tüm form için erişilebilir olan olay işleyicisini değiştirin. Yalnızca bu form için genel olacak şekilde bildirme ve bunları `Window_Loaded` Şuna benzer olay işleyicisi içinde atama:

     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]

3. Aşağıdaki kodu `backButton_Click` olay işleyicisine ekleyin:

     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]

4. Tasarımcıya dönün ve düğmeye çift tıklayın **>** .

5. Aşağıdaki kodu `nextButton_Click` olay işleyicisine ekleyin:

     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]

## <a name="savechanges-to-product-records"></a>SaveChanges 'ten ürün kayıtlarına
 **Değişiklikleri Kaydet** düğmesini kullanarak kullanıcıların ürün kayıtlarında değişiklik kaydetmesine olanak tanıyan kodu ekleyin.

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Ürün kayıtlarına yapılan değişiklikleri kaydetme yeteneğini eklemek için

1. Tasarımcıda **Değişiklikleri Kaydet** düğmesine çift tıklayın.

     Visual Studio, arka plan kod dosyasını açar ve olay için yeni bir `saveButton_Click` olay işleyicisi oluşturur <xref:System.Windows.Controls.Primitives.ButtonBase.Click> .

2. Aşağıdaki kodu `saveButton_Click` olay işleyicisine ekleyin:

     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]

    > [!NOTE]
    > Bu örnek `Save` , `TableAdapter` değişiklikleri kaydetmek için yöntemini kullanır. Yalnızca bir veri tablosu değiştiğinden bu izlenecek yol için uygundur. Birden çok veri tablosuna yaptığınız değişiklikleri kaydetmeniz gerekiyorsa alternatif olarak, `UpdateAll` `TableAdapterManager` Visual Studio 'nun veri kümeniz ile oluşturduğu yöntemini kullanabilirsiniz. Daha fazla bilgi için bkz. [TableAdapterManager Overview](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).

## <a name="test-the-application"></a>Uygulamayı test etme
 Uygulamayı derleyin ve çalıştırın. Ürün kayıtlarını görüntüleyebildiğinizi ve güncelleştirebildiğinizi doğrulayın.

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. **F5**tuşuna basın.

     Uygulama oluşturulur ve çalışır. Aşağıdakileri doğrulayın:

    - Metin kutuları, fotoğrafı olan ilk ürün kaydından verileri görüntüler. Bu ürünün 713 ürün KIMLIĞI ve **uzun süreli logo adı Ile Jersey, S**.

    - **>** **<** Diğer ürün kayıtları arasında gezinmek için veya düğmelerine tıklayabilirsiniz.

2. Ürün kayıtlarından birinde, **Boyut** değerini değiştirin ve ardından **Değişiklikleri Kaydet**' e tıklayın.

3. Uygulamayı kapatın ve ardından Visual Studio 'da **F5** tuşuna basarak uygulamayı yeniden başlatın.

4. Değiştirdiğiniz ürün kaydına gidin ve değişikliğin kalıcı olduğunu doğrulayın.

5. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki Adımlar
 Bu yönergeyi tamamladıktan sonra, aşağıdaki ilgili görevleri gerçekleştirebilirsiniz:

- Visual Studio 'daki **veri kaynakları** PENCERESINI kullanarak WPF denetimlerini diğer veri kaynağı türlerine bağlamayı öğrenin. Daha fazla bilgi için bkz. [BIR WCF veri HIZMETINE WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Visual Studio 'daki **veri kaynakları** PENCERESINI kullanarak WPF denetimlerinde ilgili verileri (yani bir üst-alt ilişkisi içindeki verileri) görüntüleme hakkında bilgi edinin. Daha fazla bilgi için bkz. [Izlenecek yol: BIR WPF uygulamasında Ilgili verileri görüntüleme](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio 'daki [VERILERE WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [bağlama WPF denetimleri](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [WPF ve Silverlight tasarımcısına genel bakış](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) [veri bağlamaya genel](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211) bakış
