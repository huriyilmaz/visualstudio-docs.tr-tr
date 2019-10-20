---
title: 'İzlenecek yol: bir Azure Mobil hizmetine bağlı WPF Masaüstü uygulaması oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 624fffb9c86a7ad874f27797dfd5251c8585870f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664023"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>İzlenecek yol: bir Azure Mobil hizmetine bağlı WPF Masaüstü uygulaması oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verileri depolamak ve sağlamak için bir Azure Mobil Hizmeti kullanan modern bir masaüstü uygulamasını hızlıca oluşturmak üzere Windows Presentation Foundation (WPF) kullanabilirsiniz.

## <a name="Requirements"></a> Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdakiler gerekir:

- Visual Studio 2015: WPF geliştirmeyi destekleyen herhangi bir sürüm.

- Etkin bir Microsoft Azure hesabı.

  - Ücretsiz deneme hesabına [buradan](https://azure.microsoft.com/pricing/free-trial/)kaydolabilirsiniz.

  - [MSDN abone avantajlarını](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F)etkinleştirebilirsiniz. MSDN aboneliğiniz, ücretli Azure hizmetleri için kullanabileceğiniz her ay kredileri sağlar.

## <a name="create-a-project-and-add-references"></a>Proje oluşturma ve başvuru ekleme
 İlk adım bir WPF projesi oluşturmaktır ve Azure Mobile Services bağlanmanıza olanak tanıyan bir NuGet paketi eklemektir.

#### <a name="to-create-the-project"></a>Proje oluşturmak için

1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual C#**  veya **Visual Basic** düğümünü genişletin ve **Windows** düğümünü seçin ve ardından **Windows** düğümünü genişletin ve **Klasik Masaüstü** düğümünü seçin.

3. Şablon listesinde **WPF uygulama** şablonunu seçin.

4. **Ad** metin kutusuna `WPFQuickStart` girin ve sonra **Tamam** düğmesini seçin.

     Proje oluşturulur ve proje dosyaları **Çözüm Gezgini**eklenir ve **MainWindow. xaml** adlı varsayılan uygulama penceresi için tasarımcı görüntülenir.

#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Windows Azure Mobile Services SDK 'sına bir başvuru eklemek için

1. **Çözüm Gezgini**' de, **Başvurular** düğümünün kısayol menüsünü açın ve **NuGet Paketlerini Yönet**' i seçin.

2. **NuGet Paket Yöneticisi**'nde **arama** alanını seçin ve `mobileservices` girin.

3. Sol bölmede, **windowsazure. MobileServices**öğesini seçin ve sağ bölmedeki **Install** düğmesini seçin.

    > [!NOTE]
    > **Önizleme** iletişim kutusu görüntülenirse, önerilen değişiklikleri gözden geçirin ve **Tamam** düğmesini seçin.

4. **Lisans kabulü** iletişim kutusunda, lisans koşullarını gözden geçirin ve kabul **ediyorum** düğmesini seçerek kabul edin.

     Gerekli başvurular **Çözüm Gezgini**eklenecektir.

    > [!NOTE]
    > Lisans koşullarını kabul etmiyorsanız, **reddetme** düğmesini seçin. İzlenecek yolun geri kalanını tamamlayamayacağız.

## <a name="create-the-user-interface"></a>Kullanıcı arabirimini oluşturma
 Bir sonraki adım, uygulama için Kullanıcı arabirimini oluşturmaktır. İlk olarak, standart yan yana iki bölme düzeni görüntüleyen yeniden kullanılabilir bir kullanıcı denetimi oluşturacaksınız. Kullanıcı denetimini ana uygulama penceresine ekleyecek ve verileri girip görüntüleyecek denetimler ekleyecek ve ardından mobil hizmet arka ucu ile etkileşimi tanımlamak için bazı kodlar yazacak.

#### <a name="to-add-a-user-control"></a>Kullanıcı denetimi eklemek için

1. **Çözüm Gezgini**, **wpfquickstart** düğümünün kısayol menüsünü açın ve **Ekle**, **Yeni klasör**' i seçin.

2. Klasörü `Common` adlandırın.

3. **Ortak** klasör için kısayol menüsünü açın ve **Ekle**, **Kullanıcı denetimi**' ni seçin.

4. **Yeni öğe Ekle** Iletişim kutusunda ad alanını seçin ve `QuickStartTask` girin ve sonra **Ekle** düğmesini seçin.

     Kullanıcı denetimi projeye eklenir ve **Quickstarttask. xaml** dosyası tasarımcıda açılır.

5. Tasarımcının alt bölmesinde `<Grid>` ve `</Grid>` etiketlerini seçin ve aşağıdaki XAML kodu ile değiştirin:

    ```xaml
    <Grid VerticalAlignment="Top">
            <StackPanel Orientation="Horizontal">
                <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">
                    <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>
                </Border>
                <StackPanel>
                    <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />
                    <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />
                </StackPanel>
            </StackPanel>
        </Grid>
    ```

     Bu XAML kodu sayı, başlık ve açıklama alanları için yer tutucuları olan yeniden kullanılabilir bir düzen oluşturur. Çalışma zamanında, yer tutucular aşağıdaki çizimde gösterildiği gibi metinle değiştirilebilir.

     ![QuickStartTask Kullanıcı denetimi](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")

6. **Çözüm Gezgini**, **quickstarttask. xaml** düğümünü genişletin ve **QuickStartTask.xaml.cs** veya **quickstarttask. xaml. vb** dosyasını açın.

7. Kod Düzenleyicisi 'nde, `namespace WPFQuickStart.Common` (C#) ad alanını veya `Public Class QuickStartTask` (vb) yöntemini aşağıdaki kodla değiştirin:

    ```csharp
    namespace WPFQuickStart.Common
    {
        /// <summary>
        /// Interaction logic for QuickStartTask.xaml
        /// </summary>
        public partial class QuickStartTask : UserControl
        {
            public QuickStartTask()
            {
                this.InitializeComponent();
                this.DataContext = this;
            }

            public int Number
            {
                get { return (int)GetValue(NumberProperty); }
                set { SetValue(NumberProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty NumberProperty =
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));

            public string Title
            {
                get { return (string)GetValue(TitleProperty); }
                set { SetValue(TitleProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty TitleProperty =
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));

            public string Description
            {
                get { return (string)GetValue(DescriptionProperty); }
                set { SetValue(DescriptionProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty DescriptionProperty =
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));
        }
    }
    ```

    ```vb
    Partial Public Class QuickStartTask
            Inherits UserControl

            Public Sub New()
                Me.InitializeComponent()
                Me.DataContext = Me
            End Sub

            Public Property Number() As Integer
                Get
                    Return CInt(Fix(GetValue(NumberProperty)))
                End Get
                Set(ByVal value As Integer)
                    SetValue(NumberProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))

            Public Property Title() As String
                Get
                    Return CStr(GetValue(TitleProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(TitleProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))

            Public Property Description() As String
                Get
                    Return CStr(GetValue(DescriptionProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(DescriptionProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))
        End Class
    ```

     Bu kod, çalışma zamanında sayı, başlık ve açıklama alanlarının değerlerini ayarlamak için bağımlılık özelliklerini kullanır.

8. Kullanıcı denetimini derlemek için menü çubuğunda **Oluştur**, **wpfhızlı başlangıç oluştur** ' u seçin.

#### <a name="to-create-and-modify-the-main-window"></a>Ana pencereyi oluşturmak ve değiştirmek için

1. **Çözüm Gezgini**, **MainWindow. xaml** dosyasını açın.

2. **Önemli**. Bu adım yalnızca için C# geçerlidir. Visual Basic kullanıyorsanız, sonraki adıma atlayın. Tasarımcının alt bölmesinde, satır `xmlns:local=”clr-namespace:WPFQuickStart”` bulun ve aşağıdaki XAML kodu ile değiştirin:

    ```xaml
    xmlns:local=”clr-namespace:WPFQuickStart.Common”
    ```

3. **Özellikler** penceresinde **ortak** kategori düğümünü genişletin ve **Title** özelliğini seçin ve sonra `WPF Todo List` girip **ENTER** tuşuna basın.

     XAML penceresindeki **title** öğesinin yeni değerle eşleşecek şekilde değişdiğine dikkat edin. Xaml özelliklerini XAML penceresinde ya da **Özellikler** penceresinde değiştirebilirsiniz ve değişiklikler eşitlenir.

4. XAML penceresinde, **Height** öğesinin değerini `768` olarak ayarlayın ve **Width** özelliğinin değerini `1280` olarak ayarlayın.

     Bu öğeler, **Özellikler** penceresindeki **Düzen** kategorisinde bulunan **Yükseklik** ve **Genişlik** özelliklerine karşılık gelir.

5. @No__t_0 ve `</Grid>` etiketlerini seçin ve aşağıdaki XAML kodu ile değiştirin:

    ```xaml
    <Grid>

            <Grid Margin="50,50,10,10">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="*" />
                </Grid.ColumnDefinitions>
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="*" />
                </Grid.RowDefinitions>

                <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">
                    <StackPanel>
                        <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>
                        <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>
                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1">
                    <StackPanel>

                        <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />

                        <StackPanel Orientation="Horizontal" Margin="72,0,0,0">
                            <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>
                            <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>
                        </StackPanel>

                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1" Grid.Column="1">
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto" />
                        <RowDefinition />
                    </Grid.RowDefinitions>
                    <StackPanel>
                        <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />
                        <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>
                    </StackPanel>

                    <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">
                        <ListView.ItemTemplate>
                            <DataTemplate>
                                <StackPanel Orientation="Horizontal">
                                    <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>
                                </StackPanel>
                            </DataTemplate>
                        </ListView.ItemTemplate>
                    </ListView>

                </Grid>

            </Grid>
        </Grid>
    ```

     Değişikliklerin tasarım penceresinde yansıtıldığını unutmayın. Ayrıca, **araç kutusu** penceresinden denetimler ekleyerek ve **Özellikler** penceresinde özellikleri ayarlayarak Kullanıcı arabirimini de tanımlamış olursunuz. Tasarımcıda yapılabildiği her şey XAML kodunda yapılabilir ve bunun tersi de geçerlidir.

     Bu noktada, tasarımın aşağıdaki şekilde görünmesi gerekir.

     ![Tasarımcıda MainWindow](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")

    > [!NOTE]
    > Sonraki birkaç yordamı takip ederken, açıksa **hata listesi** hatalar görebilirsiniz. Endişelenmeyin; Bu hatalar, kalan yordamları tamamladıktan sonra kaybolur.

6. **Çözüm Gezgini**, **MainWindow. xaml** düğümünü genişletin ve **MainWindow.xaml.cs** veya **MainWindow. xaml. vb** dosyasını açın.

7. Kod Düzenleyicisi 'nde, dosyanın en üstüne aşağıdaki `using` veya `Imports` yönergelerini ekleyin:

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    using Newtonsoft.Json;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    Imports Newtonsoft.Json
    ```

8. **Wpfhızlı başlangıç** ad alanı (C#) veya **sınıf MainWindow** sınıfı (vb) içindeki tüm kodu aşağıdaki kodla değiştirin:

    ```csharp
    namespace WPFQuickStart
    {
        /// <summary>
        /// Interaction logic for MainWindow.xaml
        /// </summary>
        public class TodoItem
        {
            public string Id { get; set; }

            [JsonProperty(PropertyName = "text")]
            public string Text { get; set; }

            [JsonProperty(PropertyName = "complete")]
            public bool Complete { get; set; }
        }

        public partial class MainWindow : Window
        {
            private MobileServiceCollection<TodoItem, TodoItem> items;
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();

            public MainWindow()
            {
                InitializeComponent();
            }

            private async void InsertTodoItem(TodoItem todoItem)
            {
                // This code inserts a new TodoItem into the database. When the operation completes
                // and Mobile Services has assigned an Id, the item is added to the CollectionView
                await todoTable.InsertAsync(todoItem);
                items.Add(todoItem);
            }

            private async void RefreshTodoItems()
            {
                try
                {
                    // This code refreshes the entries in the list view by querying the TodoItem table.
                    // The query excludes completed TodoItems
                    items = await todoTable
                        .Where(todoItem => todoItem.Complete == false)
                        .ToCollectionAsync();
                    ListItems.ItemsSource = items;
                }
                catch (MobileServiceInvalidOperationException e)
                {
                    MessageBox.Show(e.Message, "Error loading items");
                }
            }

            private async void UpdateCheckedTodoItem(TodoItem item)
            {
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService
                // responds, the item is removed from the list
                await todoTable.UpdateAsync(item);
                items.Remove(item);
            }

            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)
            {
                RefreshTodoItems();
            }

            private void ButtonSave_Click(object sender, RoutedEventArgs e)
            {
                var todoItem = new TodoItem { Text = TodoInput.Text };
                InsertTodoItem(todoItem);
                TodoInput.Text = "";
            }

            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)
            {
                CheckBox cb = (CheckBox)sender;
                TodoItem item = cb.DataContext as TodoItem;
                UpdateCheckedTodoItem(item);
            }

            protected override void OnActivated(EventArgs e)
            {
                RefreshTodoItems();
            }
        }

    }
    ```

    ```vb
    Public Class TodoItem
        Public Property Id() As String

        <JsonProperty(PropertyName:="text")>
        Public Property Text() As String

        <JsonProperty(PropertyName:="complete")>
        Public Property Complete() As Boolean
    End Class

    Partial Public Class MainWindow
        Inherits Window

        Private items As MobileServiceCollection(Of TodoItem, TodoItem)
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()

        Public Sub New()
            InitializeComponent()
        End Sub

        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)
            ' This code inserts a new TodoItem into the database. When the operation completes
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView
            Await todoTable.InsertAsync(todoItem)
            items.Add(todoItem)
        End Sub

        Private Async Sub RefreshTodoItems()
            Dim exception As MobileServiceInvalidOperationException = Nothing
            Try
                ' This code refreshes the entries in the list view by querying the TodoItem table.
                ' The query excludes completed TodoItems
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()
            Catch e As MobileServiceInvalidOperationException
                exception = e
            End Try

            If exception IsNot Nothing Then
                MessageBox.Show(exception.Message, "Error loading items")
            Else
                ListItems.ItemsSource = items
            End If
        End Sub

        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService
            ' responds, the item is removed from the list
            Await todoTable.UpdateAsync(item)
            items.Remove(item)
        End Sub

        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            RefreshTodoItems()
        End Sub

        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}
            InsertTodoItem(todoItem)
            TodoInput.Text = ""
        End Sub

        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim cb As CheckBox = DirectCast(sender, CheckBox)
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)
            UpdateCheckedTodoItem(item)
        End Sub

        Protected Overrides Sub OnActivated(ByVal e As EventArgs)
            RefreshTodoItems()
        End Sub
    End Class
    ```

     Bu kod, zaman uyumsuz yöntemleri kullanarak mobil hizmette bulunan Kullanıcı arabirimi ve veritabanı arasındaki etkileşimi tanımlar.

## <a name="create-the-azure-mobile-service"></a>Azure Mobil hizmetini oluşturma
 Son adım Microsoft Azure ' de bir mobil hizmet oluşturmak, verilerinizi depolamak için bir tablo eklemek ve ardından uygulamanızdan hizmet örneğine başvurulmadır.

#### <a name="to-create-a-mobile-service"></a>Bir mobil hizmet oluşturmak için

1. Bir Web tarayıcısı açın ve Microsoft Azure portal oturum açın ve ardından **MOBIL hizmetler** sekmesini seçin.

2. **Yeni** düğmesini seçin ve açılan Iletişim kutusunda **Işlem**, **mobil hizmet, oluştur**' u seçin.

3. **Yenı MOBIL hizmet** Iletişim kutusunda **URL** metin kutusunu seçin ve `wpfquickstart01` girin.

    > [!NOTE]
    > URL 'nin sayısal kısmını değiştirmeniz gerekebilir. Microsoft Azure her mobil hizmet için benzersiz bir URL gerektirir.

     Bu, hizmetin URL 'sini `https://wpfquickstart01.azure-mobile.net/` olarak ayarlar.

4. **Veritabanı** listesinde bir veritabanı seçeneği belirleyin. Büyük olasılıkla çok fazla kullanım gerektirmeyen bir uygulama olduğundan, **ücretsiz BIR 20 MB SQL veritabanı oluştur** seçeneğini veya aboneliğinizle ilişkilendirilmiş ücretsiz veritabanını seçebilirsiniz.

5. **Bölge** listesinde, mobil hizmeti dağıtmak istediğiniz veri merkezini seçin ve ardından **İleri** (sağ ok) düğmesini seçin.

    > [!NOTE]
    > Bu hizmet için varsayılan **arka uç** ayarı olan **JavaScript**' i kullanacaksınız.

6. Yeni bir veritabanı oluşturuyorsanız, **veritabanı ayarlarını belirtin** sayfasında, **sunucu** listesinde **Yeni SQL veritabanı sunucusu**' nu seçin, **SQL oturum açma adınızı** ve **parolanızı**girip **Tamam** ' ı (onay işareti) seçin. Bu.

7. Var olan bir veritabanını seçerseniz, **veritabanı ayarları** sayfasında, **oturum açma parolanızı** girip **Tamam** (onay işareti) düğmesini seçin.

     Mobil hizmet oluşturma işlemi başlar. İşlem tamamlandıktan sonra durum, **hazırlık** olarak değişir ve sonraki adıma geçebilirsiniz.

8. Portalda yeni oluşturulan mobil hizmeti seçin ve ardından **anahtarları Yönet** düğmesini seçin.

9. **Erişim anahtarlarını Yönet** Iletişim kutusunda **uygulama anahtarını**kopyalayın.

     Bunu bir sonraki yordamda kullanacaksınız.

#### <a name="to-create-a-table"></a>Tablo oluşturmak için

1. Microsoft Azure portal, mobil hizmetinizin adının yanında bulunan sağ oku seçin ve menü çubuğunda **veri**' yi seçin ve ardından **Tablo Ekle** bağlantısını seçin.

2. **Yeni tablo oluştur** Iletişim kutusunda **tablo adı** metin kutusuna `TodoItem` girin ve ardından **Tamam** (onay işareti) düğmesini seçin.

     Tablonun oluşturulmasını bekleyin ve sonra son yordama geçin.

#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Mobil hizmete yönelik bir bildirim eklemek için

1. Visual Studio 'ya geri dönün. **Çözüm Gezgini**, **app. xaml** (C#) veya **Application. xaml** (Visual Basic) düğümünü genişletin ve **app.xaml.cs** veya **app. xaml. vb** dosyasını açın.

2. Kod Düzenleyicisi 'nde aşağıdaki `using` ekleyin veya yönergeleri dosyanın en üstüne **Içeri aktarır** :

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    ```

3. Aşağıdaki bildirimi sınıfa ekleyin, *-SERVICE_HERE 'nizi* hizmetinizin URL 'si adıyla DEĞIŞTIRIN ve *anahtarınızı* , önceki yordamda kopyaladığınız uygulama anahtarıyla değiştirin:

    ```csharp
    public static MobileServiceClient MobileService = new MobileServiceClient(
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",
                 "YOUR-KEY-HERE"
             );
    ```

    ```vb
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")
    ```

     Bu kod, uygulamanın Microsoft Azure üzerinde çalışan mobil hizmete erişmesine izin verir.

## <a name="test-the-application"></a>Uygulamayı test etme
 Bu, Azure Mobil hizmetine erişen bir WPF Masaüstü uygulaması oluşturdunuz. Artık tüm bu sol taraf uygulamayı çalıştırmak ve bunu çalışır durumda görmektedir.

#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

1. Menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat** ' ı seçin (veya F5 tuşuna basın).

2. **Bir TodoItem** metin kutusu ekleyin, `Do something` girin ve **Kaydet** düğmesini seçin.

3. @No__t_0 girin ve ardından **Kaydet** düğmesini tekrar seçin.

     Aşağıdaki çizimde gösterildiği gibi, iki girişin **sorgu ve güncelleştirme veri** listesine eklendiğinden emin olun.

     ![Yapılacaklar öğeleri listeye eklenir.](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")

4. Listede **başka bir şey yap** girdisi için onay kutusunu seçin.

     Bu, **UpdateCheckedTodoItem** yöntemini çağırır ve öğeyi hem listeden hem de veritabanından kaldırır.

## <a name="next-steps"></a>Sonraki Adımlar
 Azure arka ucu ile bir WPF Masaüstü uygulaması için oldukça uyarlaması bir örnek tamamladınız. Tabii ki gerçek bir uygulama çok daha karmaşık olabilir, ancak aynı temel kavramlar de geçerlidir. [.NET Framework WPF](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx)'e bakın.

 Renk, şekil, grafik ve hatta animasyon ekleyerek kullanıcı arabirimini daha çarpıcı hale getirebilirsiniz. Bkz. [Visual Studio 'DA xaml tasarlama ve Visual Studio için Blend](../designers/designing-xaml-in-visual-studio.md).

 Azure Mobile Services kullanarak mevcut SQL veritabanlarına veya diğer veri kaynaklarına bağlanabilirsiniz. [Mobile Services belgelerine](https://azure.microsoft.com/services/app-service/mobile/)bakın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: Ilk WPF Masaüstü Uygulamam](../designers/walkthrough-my-first-wpf-desktop-application2.md) [Windows Presentation Foundation Ile modern masaüstü uygulamaları oluşturma](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
