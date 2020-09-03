---
title: WPF ve Entity Framework 6 ile basit veri uygulaması
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4aa978098c459d9e55ef0dc1423080357e067a5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282767"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF ve Entity Framework 6 kullanarak basit veri uygulaması oluşturma

Bu izlenecek yolda, Visual Studio 'da temel bir "veri üzerinden Forms" uygulamasının nasıl oluşturulacağı gösterilmektedir. Uygulama SQL Server LocalDB, Northwind veritabanı, Entity Framework 6 (Entity Framework Core değil) ve .NET Framework için Windows Presentation Foundation (.NET Core değil) kullanır. Ana ayrıntı görünümü ile temel veri bağlamanın nasıl yapılacağını gösterir ve ayrıca, **Ileri taşı**, **Öncekini**taşı, **başlangıca**taşı, son, **Güncelleştir** ve **Sil**düğmelerine sahip özel bir bağlama **Gezginine**sahip olur.

Bu makalede, Visual Studio 'da veri araçları kullanılmaya odaklanılır ve temel alınan teknolojiler herhangi bir derinlikte açıklanmaz. XAML, Entity Framework ve SQL ile temel bir benzerlik olduğunu varsayar. Bu örnek, WPF uygulamaları için standart olan Model-View-ViewModel (MVVM) mimarisini de göstermez. Ancak, bu kodu birkaç değişiklik ile kendi MVVM uygulamanıza kopyalayabilirsiniz.

## <a name="install-and-connect-to-northwind"></a>Northwind 'ye yükleyip bağlanın

Bu örnek SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır. Bu ürüne yönelik ADO.NET veri sağlayıcısı Entity Framework destekliyorsa, aynı zamanda diğer SQL veritabanı ürünleriyle de birlikte çalışmalıdır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi**aracılığıyla yükleyin. **Visual Studio yükleyicisi**, SQL Server Express LocalDB 'yi **.net masaüstü geliştirme** iş yükünün parçası olarak veya bağımsız bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (**SQL Server Nesne Gezgini** , **Visual Studio yükleyicisi** **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

3. Northwind için [Yeni bağlantı ekleyin](../data-tools/add-new-connections.md) .

## <a name="configure-the-project"></a>Projeyi yapılandırma

1. Visual Studio 'da yeni bir C# **WPF uygulaması** projesi oluşturun.

2. Entity Framework 6 için NuGet paketini ekleyin. **Çözüm Gezgini**, proje düğümünü seçin. Ana menüde **Proje**  >  **NuGet Paketlerini Yönet**' i seçin.

     ![NuGet Paketlerini Yönet menü öğesi](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. **NuGet Paket Yöneticisi**' nde, **Gözden** geçirme bağlantısına tıklayın. Entity Framework, büyük olasılıkla listedeki en üst pakettir. Sağ bölmedeki **yüklensin** ' e tıklayın ve yönergeleri izleyin. Çıkış penceresi, yüklemenin ne zaman tamamlandığını söyler.

     ![NuGet paketi Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. Artık Northwind veritabanını temel alan bir model oluşturmak için Visual Studio 'Yu kullanabilirsiniz.

## <a name="create-the-model"></a>Modeli oluşturma

1. **Çözüm Gezgini** ' de proje düğümüne sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin. Sol bölmedeki C# düğümünün altında **veri** ' ı seçin ve ortadaki bölmede **ADO.net varlık veri modeli**' yi seçin.

   ![Entity Framework modeli yeni öğe](../data-tools/media/raddata-ef-new-project-item.png)

2. Modeli çağırın `Northwind_model` ve **Tamam**' ı seçin. **Varlık veri modeli Sihirbazı** açılır. **Veritabanından EF Designer** ' ı seçin ve ardından **İleri**' ye tıklayın.

   ![Veritabanından EF modeli](../data-tools/media/raddata-ef-model-from-database.png)

3. Sonraki ekranda, LocalDB Northwind bağlantınızı girin veya seçin (örneğin, (LocalDB) \MSSQLLocalDB), Northwind veritabanını belirtin ve **İleri**' ye tıklayın.

4. Sihirbazın sonraki sayfasında, Entity Framework modeline dahil edilecek tabloları, saklı yordamları ve diğer veritabanı nesnelerini seçin. Ağaç görünümünde dbo düğümünü genişletin ve **müşteriler**, **siparişler**ve **sipariş ayrıntıları**' nı seçin. Varsayılan değerleri işaretli bırakın ve **son**' a tıklayın.

    ![Model için veritabanı nesneleri seçin](../data-tools/media/raddata-choose-ef-objects.png)

5. Sihirbaz Entity Framework modelini temsil eden C# sınıfları oluşturur. Sınıflar düz eski C# sınıflarıdır ve bu, WPF Kullanıcı arabirimine bağlandığımız şeydir. *. Edmx* dosyası, sınıfları veritabanındaki nesnelerle ilişkilendiren ilişkileri ve diğer meta verileri tanımlar. *. Tt* dosyaları, modelde çalışan kodu oluşturan ve değişiklikleri veritabanına kaydeden T4 şablonlarıdır. Tüm bu dosyaları Northwind_model düğümü altında **Çözüm Gezgini** görebilirsiniz:

      ![Çözüm Gezgini EF model dosyaları](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    *. Edmx* dosyası için tasarımcı yüzeyi, modeldeki bazı özellikleri ve ilişkileri değiştirmenize olanak sağlar. Bu kılavuzda tasarımcı kullanmıyoruz.

6. *. Tt* dosyaları genel amaçlıdır ve OBSERVABLECOLLECTIONS gerektiren WPF veri bağlaması ile çalışmak için bunlardan birini ince ayar gerekir. **Çözüm Gezgini**, *Northwind_model. tt*bulana kadar Northwind_model düğümünü genişletin. (' De olmadığından emin olun *. Context.tt* dosyası *. edmx* dosyasının hemen altında.)

   - Öğesinin iki örneğini ile değiştirin <xref:System.Collections.ICollection> <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - İlk oluşumunu, <xref:System.Collections.Generic.HashSet%601> <xref:System.Collections.ObjectModel.ObservableCollection%601> satır 51 etrafında ile değiştirin. İkinci diyez kümesi oluşumunu değiştirmeyin.

   - Tek <xref:System.Collections.Generic> (431 etrafında) konumunu ile değiştirin <xref:System.Collections.ObjectModel> .

7. **Ctrl** + **Shift** + Projeyi derlemek için CTRL SHIFT**B** tuşlarına basın. Yapı tamamlandığında, model sınıfları veri kaynakları Sihirbazı 'nda görülebilir.

Artık verileri görüntüleyebilmeniz, gezinebilmeniz ve değiştirebilmeniz için bu modeli XAML sayfasına bağlamak için hazırsınız.

## <a name="databind-the-model-to-the-xaml-page"></a>Modeli XAML sayfasına bağlama

Kendi veri bağlama kodunuzu yazmak mümkündür, ancak Visual Studio 'Nun sizin için bunu yapmasına çok daha kolay.

1. **Project**  >  **Veri kaynağı Yapılandırma Sihirbazı 'nı**açmak için ana menüden proje**Yeni veri kaynağı Ekle** ' yi seçin. Veritabanına değil model sınıflarına bağladığınız için **nesne** seçin:

     ![Nesne kaynağı ile veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Projenizin düğümünü genişletin ve **Müşteri**' yi seçin. (Siparişler için kaynaklar, müşterinin siparişler gezintisi özelliğinden otomatik olarak oluşturulur.)

     ![Veri kaynakları olarak varlık sınıfları ekleme](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. **Son**'a tıklayın.

4. Kod görünümünde *MainWindow. xaml* sayfasına gidin. Bu örneğin amaçları doğrultusunda XAML 'yi basit tutuyoruz. MainWindow başlığını daha açıklayıcı bir şekilde değiştirin ve şimdilik yüksekliğini ve genişliğini 600 x 800 olarak arttırın. Daha sonra dilediğiniz zaman değiştirebilirsiniz. Şimdi bu üç satır tanımını ana kılavuza, biri müşterinin ayrıntıları için bir satıra, diğeri de emirlerini gösteren kılavuza ekleyin:

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Şimdi, tasarımcıda görüntülemekte olduğunuzdan *MainWindow. xaml* ' i açın. Bu, **veri kaynakları** penceresinin **araç kutusunun**yanındaki Visual Studio pencere kenar boşluğunda bir seçenek olarak görünmesine neden olur. Pencereyi açmak için sekmeye tıklayın veya **SHIFT** + **alt** + **D** tuşlarına basın veya **View**  >  **diğer Windows**  >  **veri kaynaklarını**görüntüle ' yi seçin. Her bir özelliği müşteriler sınıfında kendi tek metin kutusunda görüntüleyeceğiz. Önce, **müşteriler** açılan kutusunda oka tıklayın ve **Ayrıntılar**' ı seçin. Sonra, tasarımcı 'nın orta satıra gitmesini bilmesini sağlamak için düğümü tasarım yüzeyinin orta kısmına sürükleyin. Onu yanlış yerleştirirseniz, daha sonra XAML içinde satırı el ile belirtebilirsiniz. Varsayılan olarak, denetimler bir ızgara öğesine dikey olarak yerleştirilir, ancak bu noktada formda istediğiniz gibi düzenleyebilirsiniz. Örneğin, **ad** metin kutusunu, adresin üzerine en üste yerleştirmek mantıklı olabilir. Bu makaleye yönelik örnek uygulama, alanları yeniden sıralar ve bunları iki sütuna yeniden düzenler.

     ![Müşteriler veri kaynağını bireysel denetimlere bağlama](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     Kod görünümünde, artık `Grid` üst kılavuzun satır 1 ' de (orta satır) yeni bir öğe görebilirsiniz. Üst kılavuz, `DataContext` öğesine eklenen bir CollectionViewSource öğesine başvuran bir özniteliğe sahiptir `Windows.Resources` . Bu veri bağlamı verildiğinde, ilk metin kutusu **adrese**bağlandığında, bu ad `Address` `Customer` CollectionViewSource içindeki geçerli nesnede bulunan özelliğe eşlenir.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Bir müşteri pencerenin üst yarısında görünür olduğunda, siparişlerinin alt yarısında görmek istersiniz. Siparişleri tek bir kılavuz görünümü denetiminde gösterebilirsiniz. Ana ayrıntı DataBinding 'in beklenen şekilde çalışması için, ayrı siparişler düğümüne değil Customers sınıfında Orders özelliğine bağlamanız önemlidir. Müşteriler sınıfının Orders özelliğini formun alt yarısına sürükleyin, böylece tasarımcı bunu satır 2 ' ye koyar:

     ![Siparişler sınıflarını kılavuz olarak sürükleyin](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio, Kullanıcı arabirimi denetimlerini modeldeki olaylara bağlayan tüm bağlama kodunu oluşturdu. Bazı verileri görmek için yapmanız gereken tek şey, modeli doldurmak için kod yazmak olacaktır. İlk olarak, *MainWindow.xaml.cs* adresine gidin ve veri bağlamı için MainWindow sınıfına bir veri üyesi ekleyin. Sizin için oluşturulan bu nesne, modeldeki değişiklikleri ve olayları izleyen bir denetim gibi davranır. Ayrıca, müşteriler ve siparişler için CollectionViewSource veri üyeleri ve ilişkili Oluşturucu başlatma mantığı da eklersiniz. Sınıfın en üstü şöyle görünmelidir:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     `using`Yük uzantısı metodunu kapsama getirmek Için System. Data. Entity için bir yönerge ekleyin:

     ```csharp
     using System.Data.Entity;
     ```

     Şimdi aşağı kaydırın ve `Window_Loaded` olay işleyicisini bulun. Visual Studio 'Nun bir CollectionViewSource nesnesi eklediğine dikkat edin. Bu, modeli oluştururken seçtiğiniz NorthwindEntities nesnesini temsil eder. Bunu zaten eklediniz, bu nedenle buraya ihtiyacınız yoktur. `Window_Loaded`Yöntemin şimdi şunun gibi görünmesi için içindeki kodu değiştirin:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. **F5**tuşuna basın. CollectionViewSource 'a alınan ilk müşterinin ayrıntılarını görmeniz gerekir. Ayrıca, veri kılavuzundaki emirlerini de görmeniz gerekir. Biçimlendirme harika olmadığından, bunu çözelim. Ayrıca, diğer kayıtları görüntülemek ve temel CRUD işlemlerini yapmak için bir yol da oluşturabilirsiniz.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Sayfa tasarımını ayarlama ve yeni müşteriler ve siparişler için Izgaralar ekleme

Visual Studio tarafından üretilen varsayılan düzenleme uygulamanız için ideal değildir, bu nedenle kodunuzda kopyalamak için son XAML 'yi sağlayacağız. Ayrıca, kullanıcının yeni bir müşteri veya sipariş eklemesini sağlamak için bazı "Formlar" (aslında ızgaralar) gerekir. Yeni bir müşteri ve sipariş ekleyebilmek için, veri bağlantılı olmayan ayrı bir metin kutusu kümesine ihtiyacınız vardır `CollectionViewSource` . İşleyici yöntemlerinde Visible özelliğini ayarlayarak kullanıcının belirli bir zamanda hangi kılavuza bakarak olduğunu kontrol edeceksiniz. Son olarak, kullanıcıların tek bir siparişi silmesini sağlamak için Orders kılavuzundaki her satıra bir Delete düğmesi eklersiniz.

İlk olarak, bu stilleri `Windows.Resources` *MainWindow. xaml*içindeki öğesine ekleyin:

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

Windows Forms uygulamalarda, bir veritabanındaki satırlarda gezinmek ve temel CRUD işlemleri yapmak için düğmeler içeren bir BindingNavigator nesnesi alırsınız. WPF bir BindingNavigator sağlamıyor, ancak bir tane oluşturmak için yeterince kolay. Bunu yatay bir StackPanel içindeki düğmelerle yapın ve düğmeleri arkasındaki koddaki yöntemlere bağlanan komutlarla ilişkilendirirsiniz.

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

Bu işleyici yöntemlerini *MainWindow.xaml.cs*içinde MainWindow sınıfına ekleyin. Müşteriler tablosu için Collectionviewkaynağınız farklı bir ada sahipse, bu yöntemlerin her birinde adı ayarlamanız gerekir:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Hata ayıklamayı başlatmak için **F5**'e basın. Kılavuzda doldurulmuş müşteri ve sipariş verilerini görmeniz gerekir ve gezinti düğmelerinin beklenen şekilde çalışması gerekir. Verileri girdikten sonra, modele yeni bir müşteri veya sipariş eklemek için **Yürüt** ' e tıklayın. Verileri kaydetmeden yeni bir müşterinin veya yeni sipariş formunun dışına çıkmak için **Iptal 'e** tıklayın. Mevcut müşteriler ve siparişlerde düzenlemeler doğrudan metin kutularında ve bu değişiklikler modele otomatik olarak yazılır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework belgeleri](/ef/)
