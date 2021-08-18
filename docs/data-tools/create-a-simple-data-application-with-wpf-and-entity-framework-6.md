---
title: WPF ve Entity Framework 6 ile basit veri uygulaması
description: Bu kılavuzda, Windows Presentation Foundation (WPF) ve Entity Framework 6 ile Visual Studio veri üzerinden basit bir formlar Entity Framework.
ms.custom: SEO-VS-2020
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ee9f34adcd5e654b03dcd180f85840b6c76d4456
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037219"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF ve Entity Framework 6 kullanarak basit veri uygulaması oluşturma

Bu kılavuzda, verilerde temel bir "veriler üzerinde formlar" uygulaması oluşturma Visual Studio. Uygulama, SQL Server LocalDB, Northwind veritabanı, Entity Framework 6 (Entity Framework Core değil) ve .NET Framework (.NET Core değil) için Windows Presentation Foundation kullanır. Ana ayrıntı görünümüyle temel veri bağlamayı gösterir ve ayrıca Sonrakini **Taşı,** Öncekini Taşı, En sona taşı , Güncelleştirmeyi ve Sil düğmelerini de olan özel bir Bağlama Gezgini'ne **sahiptir.**  

Bu makale, veri araçlarını Visual Studio ve temel alınan teknolojileri ayrıntılı bir şekilde açıklamaya çalışmamaktadır. XAML, Entity Framework ve SQL. Bu örnek, WPF uygulamaları için standart olan Model-View-ViewModel (MVVM) mimarisini de göstermemektedir. Ancak, bu kodu birkaç değişiklikle kendi MVVM uygulamanıza kopyaabilirsiniz.

## <a name="install-and-connect-to-northwind"></a>Northwind'i yükleme ve bağlanma

Bu örnekte LocalDB SQL Server Express Northwind örnek veritabanı kullanılır. Bu ADO.NET veri sağlayıcısı bu ürünü destekliyorsa Entity Framework diğer veritabanı ürünleriyle de SQL çalışması gerekir.

1. YerelDB'niz yoksa, SQL Server Express indirme sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Yerel **Visual Studio Yükleyicisi** **.NET** masaüstü geliştirme iş SQL Server Express parçası olarak veya tek bir bileşen olarak YerelDB'yi yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (**SQL Server Nesne Gezgini,** veri depolama ve işleme iş **yükünün parçası olarak** Visual Studio Yükleyicisi.)  SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

3. Northwind [için](../data-tools/add-new-connections.md) yeni bağlantılar ekleyin.

## <a name="configure-the-project"></a>Projeyi yapılandırma

1. Bu Visual Studio yeni bir C# **WPF Uygulaması projesi** oluşturun.

2. Entity Framework 6 için NuGet paketini ekleyin. Bu **Çözüm Gezgini** proje düğümünü seçin. Ana menüden Paketleri **Yönet'Project**  >  **seçin NuGet seçin.**

     ![Paket NuGet menü öğesini yönetme](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. Uygulama **NuGet Paket Yöneticisi** Gözat **bağlantısına** tıklayın. Entity Framework büyük olasılıkla listenin en üst paketidir. Sağ **bölmede** Yükle'ye tıklayın ve istemleri izleyin. Çıkış penceresi, yüklemenin ne zaman tamam olduğunu size söyler.

     ![Entity Framework NuGet Paketi](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. Artık Northwind Visual Studio tabanlı bir model oluşturmak için Visual Studio'i kullanabilirsiniz.

## <a name="create-the-model"></a>Modeli oluşturma

1. Proje düğümüne sağ tıklayın ve **Çözüm Gezgini** **Ekle'yi**  >  **seçin.** Sol bölmede, C# düğümünün  altında Veri'yi seçin ve orta bölmede, **ADO.NET Varlık Veri Modeli.**

   ![Entity Framework Modeli Yeni Öğe](../data-tools/media/raddata-ef-new-project-item.png)

2. Modeli çağırarak `Northwind_model` Tamam'ı **seçin.** Varlık Veri Modeli **Sihirbazı** açılır. Veritabanından **EF Designer'ı seçin ve** ardından Sonraki'ye **tıklayın.**

   ![Veritabanından EF Modeli](../data-tools/media/raddata-ef-model-from-database.png)

3. Sonraki ekranda LocalDB Northwind bağlantınızı girin veya seçin (örneğin, (localdb)\MSSQLLocalDB), Northwind veritabanını belirtin ve Ardından'ya **tıklayın.**

4. Sihirbazın sonraki sayfasında, depolama modeline hangi tabloların, saklı yordamların ve diğer veritabanı nesnelerinin dahil Entity Framework seçin. Ağaç görünümünde dbo düğümünü genişletin ve **Müşteriler,** Siparişler ve **Sipariş** **Ayrıntıları'ı seçin.** Varsayılan değerleri işaretli bırakın ve Son'a **tıklayın.**

    ![Model için veritabanı Nesnelerini seçme](../data-tools/media/raddata-choose-ef-objects.png)

5. Sihirbaz, Entity Framework modelini temsil eden C# Entity Framework üretir. Sınıflar düz eski C# sınıflarıdır ve WPF kullanıcı arabirimine veri kaynağı olarak bunları ekleriz. *.edmx* dosyası, sınıfları veritabanındaki nesnelerle ilişkilendiren ilişkileri ve diğer meta verileri açıklar. *.tt* dosyaları, model üzerinde çalışan ve değişiklikleri veritabanına kaydeden kodu oluşturan T4 şablonlarıdır. Bu dosyaların hepsini, Çözüm Gezgini **düğümü** altında Northwind_model:

      ![Çözüm Gezgini EF model dosyaları](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    *.edmx dosyasının* tasarımcı yüzeyi, modelde bazı özellikleri ve ilişkileri değiştirmenize olanak sağlar. Bu kılavuzda tasarımcıyı kullanmayeceğiz.

6. *.tt dosyaları* genel amaçlıdır ve WPF veri bağlama ile çalışmak için bunlardan birini ayarlamanız gerekir. Bu işlem ObservableCollections gerektirir. Bu **Çözüm Gezgini,** *Northwind_model.tt'i bulana kadar Northwind_model düğümünü genişletin.* (içinde olmadığınızdan emin *olun. Context.tt* *.edmx* dosyasının hemen altında olan bir dosya.)

   - iki oluşumunu ile <xref:System.Collections.ICollection> <xref:System.Collections.ObjectModel.ObservableCollection%601> değiştirin.

   - İlk oluşumunu <xref:System.Collections.Generic.HashSet%601> <xref:System.Collections.ObjectModel.ObservableCollection%601> 51. satıra kadar olanlarla değiştirin. HashSet'in ikinci oluşumunu değiştirme.

   - tek oluşumunu <xref:System.Collections.Generic> (431. satıra kadar) ile <xref:System.Collections.ObjectModel> değiştirin.

7. Projeyi **derlemek için Ctrl** +  + **Shift B** tuşlarına basın. Derleme tamam olduğunda model sınıfları veri kaynakları sihirbazı tarafından görülebilir.

Artık verileri görüntülemek, gezinmek ve değiştirmek için bu modeli XAML sayfasına bağlayabilirsiniz.

## <a name="databind-the-model-to-the-xaml-page"></a>Modeli XAML sayfasına veri ile ekleme

Kendi veri bağlama kodunuzu yazmak mümkündür, ancak bunu sizin için Visual Studio daha kolaydır.

1. Ana menüden Yeni veri **Project** ekle seçeneğini  >  **belirleyin ve** Veri Kaynağı Yapılandırma **Sihirbazı'nı açın.** **Veritabanına** değil model sınıflarını bağlamanız nedeniyle Nesne'yi seçin:

     ![Nesne Kaynağı ile Veri Kaynağı Yapılandırma Sihirbazı](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Projenizin düğümünü genişletin ve Müşteri'yi **seçin.** (Siparişler için Kaynaklar, Müşteri'de Orders gezinti özelliğinden otomatik olarak oluşturulur.)

     ![Veri kaynağı olarak varlık sınıfları ekleme](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. **Finish (Son)** düğmesine tıklayın.

4. Kod Görünümünde *MainWindow.xaml'e* gidin. XAML'i bu örneğin amaçları doğrultusunda basit tutuz. MainWindow başlığını daha açıklayıcı bir değerle değiştirin ve Yükseklik ve Genişlik'i şimdilik 600 x 800 olarak artırın. Bunu daha sonra değiştirebilirsiniz. Şimdi bu üç satır tanımını ana kılavuza, bir satır gezinti düğmelerine, biri müşterinin ayrıntılarına ve biri de siparişlerini gösteren kılavuza ekleyin:

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Şimdi *Tasarımcıda görüntülemek için MainWindow.xaml'i* açın. Bu, **Veri Kaynakları penceresinin** Araç Kutusu'Visual Studio kenar boşluğunda bir seçenek olarak **görünmesine neden olur.** Pencereyi açmak için sekmeye tıklayın veya Shift Alt D tuşuna basın veya Diğer Veri Kaynaklarını +  +    >  **Görüntüle'Windows**  >  **seçin.** Customers sınıfındaki her özelliği kendi bağımsız metin kutusunda görüntüley sunuyoruz. İlk olarak Müşteriler birleşik giriş kutusunda oka **tıklayın ve** Ayrıntılar'ı **seçin.** Ardından, tasarımcının orta satıra gitmek istediğinizden haberi olacak şekilde düğümü tasarım yüzeyinin orta parçasına sürükleyin. Bunu yanlış yere yerlerinden biri olursanız, satırı daha sonra XAML'de el ile belirtebilirsiniz. Varsayılan olarak, denetimler bir kılavuz öğesinde dikey olarak yerleştirilir, ancak bu noktada bunları formda nasıl olduğu gibi ayarlayabilirsiniz. Örneğin, Adresin üzerine Ad **metin kutusunu** koymak mantıklı olabilir. Bu makalenin örnek uygulaması alanları yeniden sıralar ve bunları iki sütunda yeniden sıralar.

     ![Müşterilerin tek tek denetimlere veri kaynağı bağlaması](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     Kod görünümünde artık üst `Grid` Kılavuzun 1. satırda (ortadaki satır) yeni bir öğeyi görüntülebilirsiniz. Üst Kılavuz, `DataContext` öğeye eklenmiş bir CollectionViewSource'a başvuran bir `Windows.Resources` özniteliğine sahiptir. Bu veri bağlamına göre, ilk metin kutusu **Address**'e bağlanıyorsa, bu ad CollectionViewSource'ta geçerli nesnede yer alan `Address` `Customer` özelliğiyle eşlenmiş olur.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Bir müşteri pencerenin ilk yarısında görünür olduğunda siparişlerini en alt yarıda görmek istersiniz. Siparişleri tek bir kılavuz görünümü denetiminde gösterirsiniz. Ana ayrıntı veri bağlamanın beklendiği gibi çalışması için ayrı Orders düğümüne değil Customers sınıfındaki Orders özelliğine bağlamanız önemlidir. Tasarımcının formu 2. satıra koyarak Customers sınıfının Orders özelliğini formun alt yarısına sürükleyin:

     ![Siparişler sınıflarını kılavuz olarak sürükleyin](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio, kullanıcı arabirimi denetimlerini modeldeki olaylara bağlayan tüm bağlama kodunu oluşturdu. Bazı verileri görmek için yapmanız gereken tek şey, modeli doldurmak için kod yazmak olacaktır. İlk olarak, *MainWindow. xaml. cs* ' ye gidin ve veri bağlamı için MainWindow sınıfına bir veri üyesi ekleyin. Sizin için oluşturulan bu nesne, modeldeki değişiklikleri ve olayları izleyen bir denetim gibi davranır. Ayrıca, müşteriler ve siparişler için CollectionViewSource veri üyeleri ve ilişkili Oluşturucu başlatma mantığı da eklersiniz. Sınıfın en üstü şöyle görünmelidir:

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet1":::

     `using`Yük uzantısı metodunu kapsama getirmek Için System. Data. Entity için bir yönerge ekleyin:

     ```csharp
     using System.Data.Entity;
     ```

     Şimdi aşağı kaydırın ve `Window_Loaded` olay işleyicisini bulun. Visual Studio bir collectionviewsource nesnesi eklediğine dikkat edin. Bu, modeli oluştururken seçtiğiniz NorthwindEntities nesnesini temsil eder. Bunu zaten eklediniz, bu nedenle buraya ihtiyacınız yoktur. `Window_Loaded`Yöntemin şimdi şunun gibi görünmesi için içindeki kodu değiştirin:

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet2":::


8. **F5** tuşuna basın. CollectionViewSource 'a alınan ilk müşterinin ayrıntılarını görmeniz gerekir. Ayrıca, veri kılavuzundaki emirlerini de görmeniz gerekir. Biçimlendirme harika olmadığından, bunu çözelim. Ayrıca, diğer kayıtları görüntülemek ve temel CRUD işlemlerini yapmak için bir yol da oluşturabilirsiniz.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Sayfa tasarımını ayarlama ve yeni müşteriler ve siparişler için Izgaralar ekleme

Visual Studio tarafından üretilen varsayılan düzenleme uygulamanız için ideal değildir, bu nedenle kodunuzda kopyalamak için son XAML 'yi sağlayacağız. Ayrıca, kullanıcının yeni bir müşteri veya sipariş eklemesini sağlamak için bazı "Formlar" (aslında ızgaralar) gerekir. Yeni bir müşteri ve sipariş ekleyebilmek için, veri bağlantılı olmayan ayrı bir metin kutusu kümesine ihtiyacınız vardır `CollectionViewSource` . İşleyici yöntemlerinde Visible özelliğini ayarlayarak kullanıcının belirli bir zamanda hangi kılavuza bakarak olduğunu kontrol edeceksiniz. Son olarak, kullanıcıların tek bir siparişi silmesini sağlamak için Orders kılavuzundaki her satıra bir Delete düğmesi eklersiniz.

İlk olarak, bu stilleri `Windows.Resources` *MainWindow. xaml* içindeki öğesine ekleyin:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

Sonra, tüm dış Kılavuzu bu biçimlendirme ile değiştirin:

```xaml
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Gezinmek, eklemek, güncelleştirmek ve silmek için düğmeler ekleyin

Windows Forms uygulamalarda, bir veritabanındaki satırlarda gezinmek ve temel crud işlemleri yapmak için düğmeler içeren bir BindingNavigator nesnesi alırsınız. WPF bir BindingNavigator sağlamıyor, ancak bir tane oluşturmak için yeterince kolay. Bunu yatay bir StackPanel içindeki düğmelerle yapın ve düğmeleri arkasındaki koddaki yöntemlere bağlanan komutlarla ilişkilendirirsiniz.

Komut mantığın dört bölümü vardır: (1) komutlar, (2) bağlamalar, (3), düğme ve (4) arka plan kodundaki komut işleyicileri.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML 'de komutları, bağlamaları ve düğmeleri ekleme

1. İlk olarak, öğesinin içinde *MainWindow. xaml* dosyasındaki komutları ekleyin `Windows.Resources` :

    ```xaml
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2. CommandBinding `RoutedUICommand` , bir olayı arkasındaki koddaki bir yönteme eşler. `CommandBindings`Kapanış etiketinden sonra bu öğeyi ekleyin `Windows.Resources` :

    ```xaml
    <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3. Şimdi `StackPanel` Gezinti, ekleme, silme ve güncelleştirme düğmelerini kullanarak ekleyin. İlk olarak, bu stili şu şekilde ekleyin `Windows.Resources` :

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     İkincisi, bu kodu, `RowDefinitions` dış öğe için hemen sonra, `Grid` xaml sayfasının en üstüne doğru yapıştırın:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>MainWindow sınıfına komut işleyicileri ekleme

Arka plan kod ekleme ve silme yöntemleri hariç en düşük düzeydedir. Gezinti, CollectionViewSource 'un View özelliğindeki Yöntemler çağırarak gerçekleştirilir. , `DeleteOrderCommandHandler` Bir siparişte art arda silmenin nasıl gerçekleştirileceğini gösterir. Öncelikle onunla ilişkili olan Order_Details silmemiz gerekir. , `UpdateCommandHandler` Koleksiyona yeni bir müşteri veya sipariş ekler ya da yalnızca mevcut bir müşteriyi veya siparişi, kullanıcının metin kutularında yaptığı değişikliklerle güncelleştirir.

Bu işleyici yöntemlerini *MainWindow. xaml. cs* içindeki MainWindow sınıfına ekleyin. Müşteriler tablosu için Collectionviewkaynağınız farklı bir ada sahipse, bu yöntemlerin her birinde adı ayarlamanız gerekir:

:::code language="csharp" source="../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs" id="Snippet3":::


## <a name="run-the-application"></a>Uygulamayı çalıştırma

Hata ayıklamayı başlatmak için **F5**'e basın. Kılavuzda doldurulmuş müşteri ve sipariş verilerini görmeniz gerekir ve gezinti düğmelerinin beklenen şekilde çalışması gerekir. Verileri girdikten sonra, modele yeni bir müşteri veya sipariş eklemek için **Yürüt** ' e tıklayın. Verileri kaydetmeden yeni bir müşterinin veya yeni sipariş formunun dışına çıkmak için **Iptal 'e** tıklayın. Mevcut müşteriler ve siparişlerde düzenlemeler doğrudan metin kutularında ve bu değişiklikler modele otomatik olarak yazılır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework belgeleri](/ef/)
