---
title: WPF ve Entity Framework 6 ile basit bir veri uygulaması oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 403415eaf8a882efdd63fdb9a73b5489b91f2529
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651080"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF ve Entity Framework 6 kullanarak basit veri uygulaması oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, Visual Studio 'da SQL Server LocalDB, Northwind veritabanı, Entity Framework 6 ve Windows Presentation Foundation ile temel bir "veri üzerinden form" uygulamasının nasıl oluşturulacağını gösterir. Ana ayrıntı görünümü ile temel veri bağlamanın nasıl yapılacağını gösterir ve ayrıca "sonrakine taşı," "öncekini taşı", "" Başlangıca Taşı "," "Güncelleştir" ve "Sil" düğmeleriyle özel bir "bağlama Gezgini" de vardır.

 Bu makalede, Visual Studio 'da veri araçları kullanılmaya odaklanılır ve temel alınan teknolojiler herhangi bir derinlikte açıklanmaz. XAML, Entity Framework ve SQL ile temel bir benzerlik olduğunu varsayar. Bu örnek, WPF uygulamaları için standart olan MVVM mimarisini de göstermez. Ancak, bu kodu, çok az değişiklik ile kendi MVVM uygulamanıza kopyalayabilirsiniz.

## <a name="install-and-connect-to-northwind"></a>Northwind 'ye yükleyip bağlanın
 Bu örnek SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır. Bu ürünün ADO.NET veri sağlayıcısı Entity Framework destekliyorsa, diğer SQL veritabanı ürünleriyle de birlikte çalışmalıdır.

1. Henüz yapmadıysanız, [SQL Server sürümleri indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server 2014 LocalDB Express 32 bit yükleyin.

2. Buradaki yönergeleri izleyerek Northwind örnek veritabanını yüklersiniz: [örnek veritabanlarını SQL Server install](../data-tools/install-sql-server-sample-databases.md).

3. Northwind için [Yeni bağlantı ekleyin](../data-tools/add-new-connections.md) .

## <a name="configure-the-project"></a>Projeyi yapılandırma

1. Visual Studio 'da  **&#124; dosya yeni proje** ' yi seçin ve ardından yeni C# bir WPF uygulaması oluşturun.

2. Daha sonra, Entity Framework 6 için NuGet paketini ekleyeceğiz. Çözüm Gezgini, proje düğümünü seçin. Ana menüde **Proje &#124; NuGet Paketlerini Yönet...** öğesini seçin.

     ![NuGet Paketlerini Yönet menü öğesi](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")

3. NuGet Paket Yöneticisi ' nde, **Gözden** geçirme bağlantısına tıklayın. Entity Framework, büyük olasılıkla listedeki en üst pakettir. Sağ bölmedeki **yüklensin** ' e tıklayın ve yönergeleri izleyin. Çıkış penceresinde, yüklemenin ne zaman tamamlandığını söyleyecektir.

     ![NuGet paketi Entity Framework](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")

4. Artık Northwind veritabanını temel alan bir model oluşturmak için Visual Studio 'Yu kullanabiliriz.

## <a name="create-the-model"></a>Model oluşturma

1. Çözüm Gezgini ' de proje düğümüne sağ tıklayın ve **Yeni öğe Ekle &#124;** ' yi seçin. Sol bölmede, C# düğüm altında, **veriler** ' i seçin ve Ortadaki bölmede **ADO.net varlık veri modeli**' yi seçin.

    ![Entity Framework modeli yeni proje öğesi](../data-tools/media/raddata-ef-new-project-item.png "radveri EF yeni proje öğesi")

2. Model `Northwind_model` çağırın ve Tamam ' ı seçin. Bu, **varlık veri modeli Sihirbazı 'nı**getirir. **Veritabanından EF Designer** ' ı seçin ve ardından **İleri**' ye tıklayın.

    ![Veritabanından EF modeli](../data-tools/media/raddata-ef-model-from-database.png "Veritabanından radveri EF modeli")

3. Sonraki ekranda, LocalDB Northwind bağlantınızı seçin ve **İleri**' ye tıklayın.

4. Sihirbazın sonraki sayfasında, hangi tabloların, saklı yordamların ve diğer veritabanı nesnelerinin Entity Framework modeline ekleneceğini seçeceğiz. Ağaç görünümünde dbo düğümünü genişletin ve müşteriler, siparişler ve sipariş ayrıntıları ' nı seçin. Varsayılanları işaretli bırakın ve **son**' a tıklayın.

    ![Model için veritabanı nesneleri seçin](../data-tools/media/raddata-choose-ef-objects.png "radveri EF nesneleri seçin")

5. Sihirbaz Entity Framework modelini temsil C# eden sınıfları oluşturur. Bunlar düz eski C# sınıflardır ve WPF Kullanıcı arabirimine DataBind yapacağız. . Edmx dosyası, sınıfları veritabanındaki nesnelerle ilişkilendiren ilişkileri ve diğer meta verileri tanımlar.  . Tt dosyaları, modelde çalışacak kodu oluşturan ve değişiklikleri veritabanına kaydedecek olan T4 şablonlarıdır. Tüm bu dosyaları Northwind_model düğümü altında Çözüm Gezgini görebilirsiniz:

    ![Çözüm Gezgini EF model dosyaları](../data-tools/media/raddata-solution-explorer-ef-model-files.png "radveri Çözüm Gezgini EF model dosyaları")

    . Edmx dosyası için tasarımcı yüzeyi, modeldeki bazı özellikleri ve ilişkileri değiştirmenize olanak sağlar. Bu kılavuzda tasarımcı kullanmıyoruz.

6. . Tt dosyaları genel amaçlı olduğundan, ObservableCollections gerektiren WPF veri bağlaması ile çalışmak için bunlardan birini ince ayar gerekir.  Çözüm Gezgini, Northwind_model. tt ' yi bulana kadar Northwind_model düğümünü genişletin. (* ' De **olmadığından** emin olun. . Edmx dosyasının hemen altındaki Context. tt dosyası).

   - @No__t_0 iki örneğini <xref:System.Collections.ObjectModel.ObservableCollection%601> ile değiştirin.

   - @No__t_0 ilk oluşumunu, 51 satırı etrafında <xref:System.Collections.ObjectModel.ObservableCollection%601> ile değiştirin. İkinci diyez kümesi oluşumunu değiştirme

   - Tek <xref:System.Collections.Generic> oluşumunu (334 satırı etrafında) <xref:System.Collections.ObjectModel> ile değiştirin.

7. Projeyi derlemek için **CTRL + SHIFT + B** tuşlarına basın. Yapı tamamlandığında, model sınıfları veri kaynakları Sihirbazı 'nda görülebilir.

   Artık verileri görüntüleyebilmemiz, gezinebilmeniz ve değiştirebilmemiz için bu modeli XAML sayfasına bağlamak için hazırsınız.

## <a name="databind-the-model-to-the-xaml-page"></a>Modeli XAML sayfasına bağlama
 Kendi veri bağlama kodunuzu yazmak mümkündür, ancak Visual Studio 'Nun sizin için bunu yapmasına çok daha kolay.

1. **Veri kaynağı Yapılandırma Sihirbazı 'nı**açmak için ana menüden **Proje &#124; yeni veri kaynağı Ekle** ' yi seçin. Veritabanına değil model sınıflarına bağlandığımız için **nesne** seçin:

     ![Nesne kaynağı ile veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "Nesne kaynağı ile radveri veri kaynağı Yapılandırma Sihirbazı")

2. Müşteri ' yi seçin.  (Siparişler için kaynaklar, müşterinin siparişler gezintisi özelliğinden otomatik olarak oluşturulur.)

     ![Veri kaynakları olarak varlık sınıfları ekleme](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "radveri veri kaynakları olarak varlık sınıfları ekleme")

3. **Son** ' a tıklayın

4. Kod görünümünde MainWindow. xaml sayfasına gidin. Bu örneğin amaçları doğrultusunda XAML 'yi çok basit tutacağız. MainWindow başlığını daha açıklayıcı bir şekilde değiştirin ve şimdilik yüksekliğini ve genişliğini 600 x 800 olarak arttırın. Daha sonra dilediğiniz zaman değiştirebilirsiniz. Şimdi bu üç satır tanımını ana kılavuza ekleyin; biri, bir tane olmak üzere, bir kullanıcı ayrıntıları olan bir kılavuz için, biri müşterinin ayrıntıları için bir satır;

    ```xaml
    <Grid.RowDefinitions>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="*"/>
           </Grid.RowDefinitions>
    ```

5. Şimdi, tasarımcıda görüntülemek için MainWindow. xaml ' i açın. Bu, veri kaynakları penceresinin araç kutusu ' nun yanındaki Visual Studio pencere kenar boşluğunda bir seçenek olarak görünmesine neden olur. Pencereyi açmak için sekmeye tıklayın veya **SHIFT + alt + D** tuşlarına basın veya **diğer Windows &#124; &#124; veri kaynaklarını görüntüle**' yi seçin. Her bir özelliği müşteriler sınıfında kendi tek metin kutusunda görüntüleyeceğiz. Önce müşteriler açılan kutusunda oka tıklayın ve **Ayrıntılar**' ı seçin. Ardından, tasarımcı 'nın orta satıra gitmesini bilmesini sağlamak için düğümü tasarım yüzeyinin orta kısmına sürükleyin.  Onu yanlış yerleştirirseniz, daha sonra XAML içinde satırı el ile belirtebilirsiniz. Denetimler varsayılan olarak bir Grid öğesine dikey olarak yerleştirilir, ancak bu noktada formda istediğiniz gibi düzenleyebilirsiniz.  Örneğin, ad metin kutusunu, adresin üzerine en üste yerleştirmek mantıklı olabilir. Bu makaleye yönelik örnek uygulama, alanları yeniden sıralar ve bunları iki sütuna yeniden düzenler.

     ![Müşteriler veri kaynağını bireysel denetimlere bağlama](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "radveri müşterileri bireysel denetimlere veri kaynağı bağlama")

     Kod görünümünde, artık üst kılavuzun satır 1 ' de (orta satır) yeni bir `Grid` öğesi görebilirsiniz. Üst kılavuzda, `Windows.Resources` öğesine eklenen bir CollectionViewSource 'a başvuran bir `DataContext` özniteliği vardır. Bu veri bağlamı, örneğin ilk metin kutusu "adres" olarak bağlandığında, bu adı CollectionViewSource içindeki geçerli `Customer` nesnesindeki `Address` özelliği ile eşlenir.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Bir müşteri pencerenin üst yarısında görünür olduğunda, siparişlerinin alt yarısında görülmesini istiyoruz. Siparişleri tek bir kılavuz görünümü denetiminde göstereceğiz. Ana ayrıntı DataBinding 'in beklenen şekilde çalışması için, ayrı siparişler düğümüne değil Customers sınıfında Orders özelliğine bağlandığımız önemlidir. Aşağıdaki çizime dikkat edin! Müşteriler sınıfının Orders özelliğini formun alt yarısına sürükleyin, böylece tasarımcı bunu satır 2 ' ye koyar:

     ![Siparişler sınıflarını kılavuz olarak sürükleyin](../data-tools/media/raddata-drag-orders-classes-as-grid.png "radveri, sipariş sınıflarını kılavuz olarak sürükle")

7. Visual Studio, Kullanıcı arabirimi denetimlerini modeldeki olaylara bağlayan tüm bağlama kodunu oluşturdu. Tek yapmanız gereken, bazı verileri görmek için, modeli doldurmak için bazı kodlar yazmak olacaktır. İlk olarak MainWindow.xaml.cs adresine gidip veri bağlamı için MainWindow sınıfına bir veri üyesi ekleyelim. Bizim için oluşturulan bu nesne, modeldeki değişiklikleri ve olayları izleyen bir denetim gibi davranır. Burada, daha sonra yeni bir müşteri veya yeni sipariş eklemek için kullanacağımız iki üye ekleyeceğiz. Ayrıca, Oluşturucu başlatma mantığını da ekleyeceğiz. Sınıfımızın en üstü şuna benzemelidir:

    ```csharp
    public partial class MainWindow : Window
       {
           public Customer newCustomer { get; set; }
           public Order newOrder { get; set; }

           NorthwindEntities context = new NorthwindEntities();
           CollectionViewSource custViewSource;
           CollectionViewSource ordViewSource;

           public MainWindow()
           {
               InitializeComponent();
               newCustomer = new Customer();
               newOrder = new Order();
               custViewSource = ((CollectionViewSource)
                   (FindResource("customerViewSource")));
               ordViewSource = ((CollectionViewSource)
                   (FindResource("customerOrdersViewSource")));
               DataContext = this;
           }
    ```

     Load genişletme metodunu kapsama getirmek için System. Data. Entity için bir `using` yönergesi ekleyin:

    ```csharp
    using System.Data.Entity;
    ```

     Şimdi aşağı kaydırın ve Window_Loaded olay işleyicisini bulun. Visual Studio 'nun ABD için bir CollectionViewSource nesnesi eklediğine dikkat edin. Bu, modeli oluşturduğumuz seçtiğiniz NorthwindEntities nesnesini temsil eder. Tüm yöntemin şimdi şöyle görünmesi için Window_loaded 'e kod ekleyelim:

    ```csharp
    private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            // Load is an extension method on IQueryable,
            // defined in the System.Data.Entity namespace.
            // This method enumerates the results of the query,
            // similar to ToList but without creating a list.
            // When used with Linq to Entities this method
            // creates entity objects and adds them to the context.
            context.Customers.Load();

            // After the data is loaded call the DbSet<T>.Local property
            // to use the DbSet<T> as a binding source.
            custViewSource.Source = context.Customers.Local;
        }
    ```

8. **F5**tuşuna basın. CollectionViewSource 'a alınan ilk müşterinin ayrıntılarını ve veri kılavuzundaki emirlerini görmeniz gerekir. Biçimlendirme harika olmadığından, bunu çözelim. ve diğer kayıtları görüntülemenin bir yolunu ve temel CRUD işlemlerini yapmanızı sağlar.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Sayfa tasarımını ayarlama ve yeni müşteriler ve siparişler için Izgaralar ekleme
 Visual Studio tarafından üretilen varsayılan düzenleme uygulamamız için ideal değildir, bu nedenle XAML 'de el ile bazı değişiklikler yapacağız. Ayrıca, kullanıcının yeni bir müşteri veya yeni sipariş eklemesini sağlamak için bazı "Formlar" (aslında ızgaralar) gerekecektir.    Yeni bir müşteri ve sipariş ekleyebilmeniz için, `CollectionViewSource` veri bağlantılı olmayan ayrı bir metin kutuları kümesine ihtiyacımız var. İşleyici metotlarında Visible özelliğini ayarlayarak kullanıcının belirli bir zamanda hangi kılavuzdan göreceğini denetliyoruz.

 Son olarak, bir kullanıcının tek bir siparişi silmesini sağlamak için Orders kılavuzundaki her satıra bir Delete düğmesi ekleyeceğiz.

 İlk olarak, bu stilleri Windows. resources 'e ekleyin:

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
<Grid >
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
     </StackPanel>
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
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>
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
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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
 Windows Forms uygulamalarda, bir veritabanındaki satırlarda gezinmek ve temel CRUD işlemleri yapmak için düğmeler içeren bir BindingNavigator nesnesi alırsınız. WPF bir BindingNavigator sağlamıyor ancak kolayca yapabilmeleri yeterlidir. Bu, sayfa kılavuzunun alt satırındaki yatay bir StackPanel içindeki düğmelere sahip olan düğmeleri ve bu düğmeleri, arkasındaki koddaki yöntemlere bağlanan komutlarla ilişkilendireceğiz.

 Komut mantığına bazı parçalar vardır: (1) komutlar, (2) bağlamalar, (3) düğmeleri ve (4) arka plan kodundaki komut işleyicileri.

#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML 'de komutları, bağlamaları ve düğmeleri ekleme

1. İlk olarak, Windows. resources öğesinin içinde MainWindow. XAML dosyasındaki komutları ekleyelim:

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

2. CommandBinding, RoutedUICommand olayını arkasındaki koddaki bir yönteme eşler. Windows. resources kapanış etiketinden sonra bu CommandBindings öğesini ekleyin:

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

3. Şimdi gezinti, ekleme, silme ve güncelleştirme düğmeleriyle StackPanel ekleyelim. İlk olarak, bu stili Windows. resources 'e ekleyin:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Şimdi bu kodu, XAML sayfasının en üstüne doğru dış kılavuz öğesi için RowDefinitions öğesinden hemen sonra yapıştırın:

    ```xaml
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

#### <a name="add-command-handlers-to-the-mainwindow-class"></a>MainWindow sınıfına komut işleyicileri ekleme

1. Arka plan kod ekleme ve silme yöntemleri hariç en düşük düzeydedir. Gezinti görünümünün, CollectionViewSource görünüm özelliği üzerinde Yöntemler çağırarak gerçekleştirildiğini unutmayın. DeleteOrderCommandHandler, sırayla art arda silmenin nasıl gerçekleştirileceğini gösterir. Öncelikle onunla ilişkili olan Order_Details öğesini silmemiz gerekir. UpdateCommandHandler, koleksiyona yeni bir müşteri ekler ya da yalnızca, metin kutularında kullanıcının yaptığı değişikliklerle mevcut nesneyi güncelleştirir.

2. Müşteriler tablosu için CollectionViewSource farklı bir ada sahipse, bu işleyici yöntemlerini MainWindow.xaml.cs içinde MainWindow sınıfına ekleyin, ardından bu yöntemlerin her birinde adı ayarlamanız gerekir:

    ```csharp
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToLast();
    }

    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToPrevious();
    }

    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToNext();
    }

    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        custViewSource.View.MoveCurrentToFirst();
    }

    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // If existing window is visible, then delete the customer and all their orders.
        // In a real application, you should add warnings and allow a user to cancel the operation.
        var cur = custViewSource.View.CurrentItem as Customer;

        var cust = (from c in context.Customers
                    where c.CustomerID == cur.CustomerID
                    select c).FirstOrDefault();

        if (cust != null)
        {
            foreach (var ord in cust.Orders.ToList())
            {
                Delete_Order(ord);
            }
            context.Customers.Remove(cust);
        }
        context.SaveChanges();
        custViewSource.View.Refresh();
    }

    // Commit changes from the new customer form, the new order form,
    // or edits made to the existing customer form.
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        if (newCustomerGrid.IsVisible)
        {
            // Create a new object because the old one
            // is being tracked by EF now.
            newCustomer = new Customer();
            newCustomer.Address = add_addressTextBox.Text;
            newCustomer.City = add_cityTextBox.Text;
            newCustomer.CompanyName = add_companyNameTextBox.Text;
            newCustomer.ContactName = add_contactNameTextBox.Text;
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;
            newCustomer.Country = add_countryTextBox.Text;
            newCustomer.CustomerID = add_customerIDTextBox.Text;
            newCustomer.Fax = add_faxTextBox.Text;
            newCustomer.Phone = add_phoneTextBox.Text;
            newCustomer.PostalCode = add_postalCodeTextBox.Text;
            newCustomer.Region = add_regionTextBox.Text;

            // Perform very basic validation
            if (newCustomer.CustomerID.Length == 5)
            {
                // Insert the new customer at correct position:
                int len = context.Customers.Local.Count();
                int pos = len;
                for (int i = 0; i < len; ++i)
                {
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)
                    {
                        pos = i;
                        break;
                    }
                }
                context.Customers.Local.Insert(pos, newCustomer);
                custViewSource.View.Refresh();
                custViewSource.View.MoveCurrentTo(newCustomer);
            }
            else
            {
                MessageBox.Show("CustomerID must have 5 characters.");
            }

            newCustomerGrid.Visibility = Visibility.Collapsed;
            existingCustomerGrid.Visibility = Visibility.Visible;
        }
        else if (newOrderGrid.IsVisible)
        {
            // Order ID is auto-generated so we don't set it here.
            // For CustomerID, address, etc we use the values from current customer.
            // User can modify these in the datagrid after the order is entered.

            newOrder.OrderDate = add_orderDatePicker.SelectedDate;
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;
            try
            {
                // Exercise for the reader if you are using Northwind:
                // Add the Northwind Shippers table to the model.
                // Acceptable ShipperID values are 1, 2, or 3.
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"
                    || add_ShipViaTextBox.Text == "3")
                {
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);
                }
                else
                {
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");
                    return;
                }
            }
            catch
            {
                MessageBox.Show("Ship Via must be convertible to int");
                return;
            }
            try
            {
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);
            }
            catch
            {
                MessageBox.Show("Freight must be convertible to decimal.");
                return;
            }

            // Add the order into the EF model
            context.Orders.Add(newOrder);
            ordViewSource.View.Refresh();
        }

        // Save the changes, either for a new customer, a new order
        // or an edit in an existing customer or order
        context.SaveChanges();
    }

    // Sets up the form so that user can enter data. Data is later
    // saved when user clicks Commit.
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Visible;

        // Clear all the text boxes before adding a new customer.
        foreach (var child in newCustomerGrid.Children)
        {
            var tb = child as TextBox;
            if (tb != null)
            {
                tb.Text = "";
            }
        }
    }

    private void NewOrder_click(object sender, RoutedEventArgs e)
    {
        var cust = custViewSource.View.CurrentItem as Customer;
        if (cust == null)
        {
            MessageBox.Show("No customer selected.");
            return;
        }

        newOrder.CustomerID = cust.CustomerID;

        // Get address and other mostly constant fields from
        // an existing order, if one exists
        var coll = custViewSource.Source as IEnumerable<Customer>;
        var lastOrder = (from c in coll
                         from ord in c.Orders
                         select ord).LastOrDefault();
        if (lastOrder != null)
        {
            newOrder.ShipAddress = lastOrder.ShipAddress;
            newOrder.ShipCity = lastOrder.ShipCity;
            newOrder.ShipCountry = lastOrder.ShipCountry;
            newOrder.ShipName = lastOrder.ShipName;
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;
            newOrder.ShipRegion = lastOrder.ShipRegion;
        }

        existingCustomerGrid.Visibility = Visibility.Collapsed;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.UpdateLayout();
        newOrderGrid.Visibility = Visibility.Visible;
    }

    // Cancels any input into the new customer form
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        add_addressTextBox.Text = "";
        add_cityTextBox.Text = "";
        add_companyNameTextBox.Text = "";
        add_contactNameTextBox.Text = "";
        add_contactTitleTextBox.Text = "";
        add_countryTextBox.Text = "";
        add_customerIDTextBox.Text = "";
        add_faxTextBox.Text = "";
        add_phoneTextBox.Text = "";
        add_postalCodeTextBox.Text = "";
        add_regionTextBox.Text = "";

        existingCustomerGrid.Visibility = Visibility.Visible;
        newCustomerGrid.Visibility = Visibility.Collapsed;
        newOrderGrid.Visibility = Visibility.Collapsed;
    }

    private void Delete_Order(Order order)
    {
        // Find the order in the EF model.
        var ord = (from o in context.Orders.Local
                   where o.OrderID == order.OrderID
                   select o).FirstOrDefault();

        // Delete all the order_details that have
        // this Order as a foreign key
        foreach (var detail in ord.Order_Details.ToList())
        {
            context.Order_Details.Remove(detail);
        }

        // Now it's safe to delete the order.
        context.Orders.Remove(ord);
        context.SaveChanges();

        // Update the data grid.
        ordViewSource.View.Refresh();
    }

    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)
    {
        // Get the Order in the row in which the Delete button was clicked.
        Order obj = e.Parameter as Order;
        Delete_Order(obj);
    }
    ```

3. **F5**tuşuna basın. Verilerinizi görmeniz gerekir ve gezinti düğmelerinin beklenen şekilde çalışması gerekir. Verileri girdikten sonra modele yeni bir müşteri veya sipariş eklemek için "Kaydet" e tıklayın.  Yeni bir müşterinin veya yeni sipariş formunun kaydedilmeden geri dönmek için "Iptal" e tıklayın. Mevcut müşteriler ve siparişlerde düzenlemeler doğrudan metin kutularında ve bu değişiklikler modele otomatik olarak yazılır.

## <a name="see-also"></a>Ayrıca Bkz.
 [.Net Entity Framework Için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md) [belgeleri](https://msdn.microsoft.com/data/ee712907.aspx)
