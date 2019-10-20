---
title: WPF'ye Giriş
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- csharp
- vb
ms.workload:
- multiple
ms.openlocfilehash: 5fe70c531a109294b49a1f6104f535cf8aca5a45
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635440"
---
# <a name="wpf-overview"></a>WPF’ye genel bakış

Windows Presentation Foundation (WPF), görsel açıdan etkileyici kullanıcı deneyimleri sayesinde Windows için masaüstü istemci uygulamaları oluşturmanıza olanak tanır.

![Contoso sağlık Kullanıcı arabirimi örneği](../designers/media/wpfintrofigure24.png)

WPF 'nin çekirdeği, modern grafik donanımının avantajlarından yararlanmak için oluşturulmuş, çözünürlükten bağımsız ve vektör tabanlı bir işleme altyapısıdır. WPF, Extensible Application Markup Language (XAML), denetimler, veri bağlama, düzen, 2B ve 3B grafikler, animasyon, stiller, şablonlar, belgeler, medya, metin ve baskı. WPF .NET 'in bir parçası olduğundan, .NET API 'nin diğer öğelerini birleştiren uygulamalar oluşturabilirsiniz.

Bu genel bakış, Newcomers 'e yöneliktir ve WPF 'in temel yeteneklerini ve kavramlarını ele alır.

## <a name="program-with-wpf"></a>WPF ile program

WPF, <xref:System.Windows> ad alanında bulunan (en fazla bölüm için) .NET türlerinin bir alt kümesi olarak mevcuttur. Daha önce ASP.NET ve Windows Forms gibi yönetilen teknolojiler kullanarak .NET ile uygulamalar oluşturduysanız, temel WPF programlama deneyimi tanıdık gelmelidir; , C# veya Visual Basic gibi en sevdiğiniz .NET programlama dilini kullanarak sınıfları örnekleyebilirsiniz, özellikleri ayarlar, yöntemleri çağırır ve olayları işleyebilirsiniz.

WPF, özellikleri ve olayları geliştiren ek programlama yapılarını içerir: [bağımlılık özellikleri](/dotnet/framework/wpf/advanced/dependency-properties-overview) ve [yönlendirilmiş olaylar](/dotnet/framework/wpf/advanced/routed-events-overview).

## <a name="markup-and-code-behind"></a>Biçimlendirme ve arka plan kodu

WPF, ASP.NET geliştiricilerin tanıdık olması gereken bir deneyim olan hem *biçimlendirme* hem de *arka plan kodu*kullanarak bir uygulama geliştirmenize olanak tanır. Genellikle XAML işaretlemesini kullanarak, davranışını uygulamak için yönetilen programlama dillerini (arka plan kod) kullanırken bir uygulamanın görünümünü uygulayın. Bu görünüm ve davranışın ayrımı aşağıdaki avantajlara sahiptir:

- Görünüme özgü biçimlendirme davranışa özgü kodla sıkı bir şekilde bağlı olmadığından geliştirme ve bakım maliyetleri azaltılır.

- Geliştiriciler uygulamanın davranışını uygulayan geliştiricilerle aynı anda bir uygulamanın görünümünü uygulayabildiğinden geliştirme daha etkilidir.

- WPF uygulamaları için [Genelleştirme ve yerelleştirme](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview) basitleştirilmiştir.

### <a name="markup"></a>Gösterilemeyen

XAML, uygulamanın görünümünü bildirimli olarak uygulayan XML tabanlı bir biçimlendirme dilidir. Genellikle Windows, iletişim kutuları, sayfalar ve Kullanıcı denetimleri oluşturmak ve bunları denetimler, şekiller ve grafiklerle doldurmanız için kullanırsınız.

Aşağıdaki örnek, tek bir düğme içeren bir pencerenin görünümünü uygulamak için XAML kullanır.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

Özellikle, bu XAML, sırasıyla `Window` ve `Button` öğelerini kullanarak bir pencere ve bir düğme tanımlar. Her öğe, pencerenin başlık çubuğu metnini belirtmek için `Window` öğenin `Title` özniteliği gibi özniteliklerle yapılandırılır. Çalışma zamanında WPF, biçimlendirme içinde tanımlanan öğeleri ve öznitelikleri WPF sınıflarının örneklerine dönüştürür. Örneğin, `Window` öğesi, <xref:System.Windows.Window.Title%2A> özelliği `Title` özniteliğinin değeri olan <xref:System.Windows.Window> sınıfının bir örneğine dönüştürülür.

Aşağıdaki şekilde, önceki örnekte XAML tarafından tanımlanan Kullanıcı arabirimi (UI) gösterilmektedir.

![Düğme içeren pencere](../designers/media/wpfintrofigure10.png)

XAML, XML tabanlı olduğundan, onunla oluşturduğunuz Kullanıcı arabirimi bir [öğe ağacı](/dotnet/framework/wpf/advanced/trees-in-wpf)olarak bilinen iç içe geçmiş öğelerin hiyerarşisinde toplanır. Öğe ağacı, Usıs oluşturmak ve yönetmek için mantıksal ve sezgisel bir yol sağlar.

### <a name="code-behind"></a>Arka plan kodu

Bir uygulamanın ana davranışı, olayları işleme (örneğin, bir menü, araç çubuğu veya düğme) ve yanıt olarak iş mantığı ve veri erişim mantığını çağırma dahil olmak üzere kullanıcı etkileşimlerine yanıt veren işlevselliği uygulamaktır. WPF 'de, bu davranış biçimlendirme ile ilişkili kodda uygulanır. Bu tür bir kod, arka plan kodu olarak bilinir. Aşağıdaki örnek, önceki örnekteki ve arka plan kodundaki güncelleştirilmiş biçimlendirmeyi gösterir.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox 

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI 
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace
```

Bu örnekte, arka plan kodu <xref:System.Windows.Window> sınıfından türetilen bir sınıf uygular. @No__t_0 özniteliği, biçimlendirmeyi arka plan kod sınıfıyla ilişkilendirmek için kullanılır. `InitializeComponent`, arka plan kod sınıfı ile biçimlendirmede tanımlanan Kullanıcı arabirimini birleştirmek için arka plan kod sınıfından çağırılır. (`InitializeComponent`, uygulamanızın oluşturulduğu zaman sizin için oluşturulur, bu nedenle el ile uygulamanız gerekmez.) @No__t_1 ve `InitializeComponent` birleşimi, uygulamanızın oluşturulduğu her seferinde doğru başlatılmış olmasını sağlamaktır. Arka plan kod sınıfı, düğmenin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir olay işleyicisi de uygular. Düğmeye tıklandığında, olay işleyicisi <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> yöntemini çağırarak bir ileti kutusu gösterir.

Aşağıdaki şekilde, düğme tıklandığında sonuç gösterilmektedir.

![Bir MessageBox](../designers/media/wpfintrofigure25.png)

## <a name="controls"></a>Denetimler

Uygulama modeli tarafından sunulan kullanıcı deneyimleri, oluşturulan denetimlerdir. WPF 'de *Denetim* , bir pencere veya sayfada BARıNDıRıLAN bir WPF sınıfı kategorisi için geçerli olan ve bir kullanıcı arabirimine sahip olan ve bazı davranışları uygulayan bir şemsiye terimidir.

Daha fazla bilgi için bkz. [denetimler](/dotnet/framework/wpf/controls/index).

### <a name="wpf-controls-by-function"></a>İşleve göre WPF denetimleri

Yerleşik WPF denetimleri burada listelenmiştir.

- **Düğmeler**: <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Primitives.RepeatButton>.

- **Veri görüntüleme**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView> ve <xref:System.Windows.Controls.TreeView>.

- **Tarih görüntüleme ve seçim**: <xref:System.Windows.Controls.Calendar> ve <xref:System.Windows.Controls.DatePicker>.

- **Iletişim kutuları**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog> ve <xref:Microsoft.Win32.SaveFileDialog>.

- **Dijital mürekkep**: <xref:System.Windows.Controls.InkCanvas> ve <xref:System.Windows.Controls.InkPresenter>.

- **Belgeler**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer> ve <xref:System.Windows.Controls.StickyNoteControl>.

- **Giriş**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox> ve <xref:System.Windows.Controls.PasswordBox>.

- **Düzen**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, 0, 1, 2, 3, 4, 5 , 6, 7, 8, 9 ve 0.

- **Medya**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Controls.SoundPlayerAction>.

- **Menüler**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu> ve <xref:System.Windows.Controls.ToolBar>.

- **Gezinti**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow> ve <xref:System.Windows.Controls.TabControl>.

- **Seçim**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton> ve <xref:System.Windows.Controls.Slider>.

- **Kullanıcı bilgileri**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.ToolTip>.

## <a name="input-and-commands"></a>Giriş ve komutlar

Denetimler çoğu zaman Kullanıcı girişini algılar ve yanıtlar. [WPF giriş sistemi](/dotnet/framework/wpf/advanced/input-overview) metin girişi, odak yönetimi ve fare konumlandırmayı desteklemek için hem doğrudan hem de yönlendirilmiş olayları kullanır.

Uygulamalar genellikle karmaşık giriş gereksinimlerine sahiptir. WPF, Kullanıcı giriş eylemlerini bu eylemlere yanıt veren koddan ayıran bir [komut sistemi](/dotnet/framework/wpf/advanced/commanding-overview) sağlar.

## <a name="layout"></a>Düzen

Bir kullanıcı arabirimi oluşturduğunuzda, bir düzen oluşturmak için denetimlerinizi konuma ve boyuta göre düzenleyin. Herhangi bir düzenin önemli bir gereksinimi, pencere boyutu ve görüntüleme ayarlarındaki değişikliklere uyum sağlar. Bu koşullarda bir düzeni uyarlamak için kodu yazmanızı zorlamak yerine WPF, sizin için birinci sınıf bir Genişletilebilir düzen sistemi sağlar.

Düzen sisteminin temel taşı, değişen pencere ve görüntüleme koşullarına uyum sağlayan göreli konumlardır. Ayrıca, Düzen sistemi, düzeni belirleme denetimleri arasındaki anlaşmayı yönetir. Anlaşma iki adımlı bir işlemdir: ilk olarak, bir denetim üst öğeye gereken konumu ve boyutu söyler; İkincisi, üst öğe denetime ne kadar boşluk yapabileceğini söyler.

Düzen sistemi, temel WPF sınıfları aracılığıyla alt denetimlere açıktır. WPF, yığınlama ve yerleştirme gibi ortak düzenler için çeşitli düzen denetimleri içerir:

- <xref:System.Windows.Controls.Canvas>: alt denetimler kendi düzenlerini sağlar.

- <xref:System.Windows.Controls.DockPanel>: alt denetimler panelin kenarlarına hizalanır.

- <xref:System.Windows.Controls.Grid>: alt denetimler satırlara ve sütunlara göre konumlandırılır.

- <xref:System.Windows.Controls.StackPanel>: alt denetimler dikey ya da yatay olarak yığılır.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: alt denetimler sanallaştırılır ve yatay veya dikey olarak yönelimli tek bir satırda düzenlenir.

- <xref:System.Windows.Controls.WrapPanel>: alt denetimler soldan sağa düzende konumlandırılır ve geçerli satırda alanın izin verdiğinden daha fazla denetim olduğunda sonraki satıra kaydırılır.

Aşağıdaki örnek, birkaç <xref:System.Windows.Controls.TextBox> denetimini düzenlemek için bir <xref:System.Windows.Controls.DockPanel> kullanır.

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_1.xaml)]

@No__t_0, alt <xref:System.Windows.Controls.TextBox> denetimlerinin nasıl düzenlendiğini anlatmasını sağlar. Bunu yapmak için <xref:System.Windows.Controls.DockPanel>, her birinin bir yerleştirme stili belirtmesini sağlamak üzere alt denetimlere açık olan `Dock` iliştirilmiş bir özelliği uygular.

> [!NOTE]
> Alt denetimler tarafından kullanılmak üzere bir üst denetim tarafından uygulanan bir özellik, [iliştirilmiş özelliği](/dotnet/framework/wpf/advanced/attached-properties-overview)olarak ADLANDıRıLAN bir WPF yapısıdır.

Aşağıdaki şekilde, önceki örnekteki XAML biçimlendirmesinin sonucu gösterilmektedir.

![DockPanel sayfası](../designers/media/wpfintrofigure11.png)

## <a name="data-binding"></a>Veri bağlama

Birçok uygulama, kullanıcılara verileri görüntüleme ve düzenleme araçlarını sağlamak için oluşturulur. WPF uygulamaları için, veri depolama ve erişme işi SQL Server ve ADO .NET gibi teknolojiler tarafından zaten sunulmaktadır. Verilere erişildikten ve uygulamanın yönetilen nesnelerine yüklendikten sonra, WPF uygulamalarına yönelik sabit çalışma başlar. Temelde, bu iki şeyi içerir:

1. Yönetilen nesnelerden verileri, verilerin görüntülenebildiği ve düzenlenebileceği denetimlere kopyalama.

2. Denetimler kullanılarak verilerde yapılan değişikliklerin, yönetilen nesnelere geri kopyalanmasını sağlamak.

WPF, uygulama geliştirmeyi basitleştirmek için, bu adımları otomatik olarak gerçekleştirmek üzere bir veri bağlama altyapısı sağlar. Veri bağlama altyapısının çekirdek birimi, işi bir denetimi (bağlama hedefi) bir veri nesnesine (bağlama kaynağı) bağlamak olan <xref:System.Windows.Data.Binding> sınıfıdır. Bu ilişki aşağıdaki şekilde gösterilmiştir:

![Temel veri bağlama diyagramı](../designers/media/databindingmostbasic.png)

Sonraki örnekte, bir <xref:System.Windows.Controls.TextBox> özel bir `Person` nesnesinin örneğine nasıl bağlayacağınız gösterilmektedir. @No__t_0 uygulama aşağıdaki kodda gösterilmektedir:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/VisualBasic/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/CSharp/introduction-to-wpf_2.cs)]

Aşağıdaki biçimlendirme <xref:System.Windows.Controls.TextBox> özel bir `Person` nesnesinin örneğine bağlar.

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_6.cs)]

Bu örnekte, `Person` sınıfı arka plan kodunda oluşturulur ve `DataBindingWindow` veri bağlamı olarak ayarlanır. Biçimlendirme ' de, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox.Text%2A> özelliği `Person.Name` özelliğine bağımlıdır ("`{Binding ... }`" XAML sözdizimi kullanılarak). Bu XAML, WPF <xref:System.Windows.Controls.TextBox> denetimini pencerenin <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğinde depolanan `Person` nesnesine bağlamasını söyler.

WPF veri bağlama altyapısı, doğrulama, sıralama, filtreleme ve gruplamayı içeren ek destek sağlar. Ayrıca, veri bağlama, standart WPF denetimleri tarafından görüntülenecek kullanıcı arabirimi uygun olmadığında, bağlantılı veriler için özel kullanıcı arabirimi oluşturmak üzere veri şablonlarının kullanımını destekler.

Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="graphics"></a>Grafikler

WPF, aşağıdaki avantajları içeren kapsamlı, ölçeklenebilir ve esnek bir grafik özellikleri kümesi sunar:

- **Çözünürlükten bağımsız ve cihazdan bağımsız grafikler**. WPF Grafik sistemindeki temel ölçü birimi, gerçek ekran çözünürlüğünden bağımsız olarak bir inç 1/96th olan cihazdan bağımsız pikseldir ve çözünürlükten bağımsız ve cihazdan bağımsız işleme için temel sağlar. Her cihazdan bağımsız piksel, üzerinde oluşturduğu sistemin inç başına nokta (DPI) ayarıyla eşleşecek şekilde otomatik olarak ölçeklendirilir.

- **İyileştirilmiş duyarlık**. WPF koordinat sistemi, tek duyarlık yerine çift duyarlıklı kayan noktalı sayılar ile ölçülür. Dönüşümler ve opaklık değerleri de çift duyarlıklı olarak ifade edilir. WPF ayrıca geniş bir renk gamutu (scRGB) destekler ve farklı renk uzaylarından girişleri yönetmek için tümleşik destek sağlar.

- **Gelişmiş grafikler ve animasyon desteği**. WPF, sizin için animasyon sahneleri yöneterek grafik programlamayı basitleştirir; sahne işleme, işleme döngüleri ve Bilinear ilişkilendirme konusunda endişelenmenize gerek yoktur. Ayrıca WPF, isabet testi desteği ve tam alfa birleştirme desteği sağlar.

- **Donanım hızlandırma**. WPF Grafik sistemi, CPU kullanımını en aza indirmek için grafik donanımından yararlanır.

### <a name="2d-shapes"></a>2B şekiller

WPF, aşağıdaki çizimde gösterilen dikdörtgenler ve üç nokta gibi yaygın bir vektör çizilmiş 2B şekil kitaplığı sağlar:

![Üç nokta ve dikdörtgen](../designers/media/wpfintrofigure4.PNG)

Şekillerin ilginç bir özelliği yalnızca görüntüleme için değildir; şekiller, klavye ve fare girişi dahil olmak üzere denetimlerden beklediğinizi birçok özelliği uygular. Aşağıdaki örnek, işlenmekte olan bir <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.UIElement.MouseUp> olayını gösterir.

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_8.cs)]

Aşağıdaki şekilde, önceki kod tarafından üretilen değer gösterilmektedir.

!["Elips&#33;tıkladınız" metnini içeren pencere](../designers/media/wpfintrofigure12.png)

Daha fazla bilgi için bkz. [WPF 'de şekillere ve temel çizime genel bakış](/dotnet/framework/wpf/data/data-binding-overview).

### <a name="2d-geometries"></a>2B geometriler

WPF tarafından sunulan 2B şekiller, temel şekillerin standart kümesini kapsar. Ancak, özelleştirilmiş bir kullanıcı arabiriminin tasarımını kolaylaştırmak için özel şekiller oluşturmanız gerekebilir. Bu amaçla WPF, geometriler sağlar. Aşağıdaki şekilde, doğrudan çizilemeyen, fırça olarak kullanılan veya diğer şekilleri ve denetimleri kırpmak için kullanılan özel bir şekil oluşturmak için geometriler kullanımı gösterilmektedir.

<xref:System.Windows.Shapes.Path> nesneler, kapalı veya açık şekiller, birden çok şekil ve hatta eğri şekiller çizmek için kullanılabilir.

<xref:System.Windows.Media.Geometry> nesneler kırpma, isabet testi ve 2B grafik verileri işleme için kullanılabilir.

![Yolun çeşitli kullanımları](../designers/media/wpfintrofigure5.png)

Daha fazla bilgi için bkz. [geometriye genel bakış](/dotnet/framework/wpf/graphics-multimedia/geometry-overview).

### <a name="2d-effects"></a>2B efektler

WPF 2B özellikleri alt kümesi degradeler, bit eşlemler, çizimler, videolar, döndürme, ölçeklendirme ve eğriltme gibi görsel etkileri içerir. Bunlar fırçalar ile elde edilir; Aşağıdaki şekilde bazı örnekler gösterilmektedir.

![Farklı fırçaların çizimi](../designers/media/wpfintrofigure6.png)

Daha fazla bilgi için bkz. [WPF Fırçalarına Genel Bakış](/dotnet/framework/wpf/graphics-multimedia/wpf-brushes-overview).

### <a name="3d-rendering"></a>3B işleme

WPF ayrıca, daha heyecan verici ve ilginç Kullanıcı arabirimleri oluşturulmasına olanak tanımak için 2-b grafiklerle tümleştirilen 3B işleme özelliklerini de içerir. Örneğin, aşağıdaki şekilde 3B şekiller üzerinde işlenen 2D görüntüleri gösterilmektedir.

![Visual3d değil örnek ekran görüntüsü](../designers/media/wpfintrofigure13.png)

Daha fazla bilgi için bkz. [3B grafiklere genel bakış](/dotnet/framework/wpf/graphics-multimedia/3-d-graphics-overview).

## <a name="animation"></a>Animasyon

WPF animasyon desteği, denetimlerin büyümesi, sallanması, dönmesi ve belirmesini, ilginç sayfa geçişleri oluşturmak ve daha fazlasını yapmanızı sağlar. Birçok WPF sınıfının, hatta özel sınıfların animasyonunu yapabilirsiniz. Aşağıdaki şekilde, eylem içinde basit bir animasyon gösterilmektedir.

![Animasyonlu küpün görüntüleri](../designers/media/wpfintrofigure7.png)

Daha fazla bilgi için bkz. [animasyon genel bakış](/dotnet/framework/wpf/graphics-multimedia/animation-overview).

## <a name="media"></a>Medyasını

Zengin içerik iletmenin bir yolu, Audiovisual medyası kullanmaktır. WPF, görüntüler, videolar ve ses için özel destek sağlar.

### <a name="images"></a>Görüntüler

Görüntüler çoğu uygulama için ortaktır ve WPF bunları kullanmak için çeşitli yollar sağlar. Aşağıdaki şekilde, küçük resim görüntüleri içeren bir liste kutusuyla bir kullanıcı arabirimi gösterilmektedir. Küçük resim seçildiğinde görüntü tam boyut olarak gösterilir.

![Küçük resim görüntüleri ve tam&#45;boyut görüntüsü](../designers/media/wpfintrofigure8.png)

Daha fazla bilgi için bkz. [Imaging 'e genel bakış](/dotnet/framework/wpf/graphics-multimedia/imaging-overview).

### <a name="video-and-audio"></a>Video ve ses

@No__t_0 denetimi hem videoyu hem de sesi oynatabilen ve özel bir medya yürütücüsünün temeli olması yeterince esnektir. Aşağıdaki XAML biçimlendirmesi bir medya oynatıcı uygular.

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_9.xaml)]

Aşağıdaki şekilde gösterilen pencerede, <xref:System.Windows.Controls.MediaElement> denetimi eylem içinde gösterilmektedir.

![Ses ve video ile MediaElement denetimi](../designers/media/wpfintrofigure1.png)

Daha fazla bilgi için bkz. [grafik ve multimedya](/dotnet/framework/wpf/graphics-multimedia).

## <a name="text-and-typography"></a>Metin ve tipografi

WPF, yüksek kaliteli metin işlemesini kolaylaştırmak için aşağıdaki özellikleri sunar:

- OpenType yazı tipi desteği.

- ClearType geliştirmeleri.

- Donanım hızlandırmasının avantajlarından yararlanan yüksek performans.

- Medya, grafik ve animasyonla metin tümleştirmesi.

- Uluslararası yazı tipi desteği ve geri dönüş mekanizmaları.

Grafiklerle metin tümleştirmesinin bir sunumu olarak, aşağıdaki şekilde metin düzenlemelerinin uygulaması gösterilmektedir.

![Çeşitli metin süslemeleri içeren metin](../designers/media/wpfintrofigure23.png)

Daha fazla bilgi için bkz. [tipografi Windows Presentation Foundation](/dotnet/framework/wpf/advanced/typography-in-wpf).

## <a name="customize-wpf-apps"></a>WPF uygulamalarını özelleştirme

Bu noktaya kadar, uygulama geliştirmeye yönelik temel WPF yapı taşlarını gördünüz. Genellikle denetimlerden oluşan uygulama içeriğini barındırmak ve sunmak için uygulama modelini kullanırsınız. Bir kullanıcı arabirimindeki denetimlerin düzenlemesini basitleştirmek ve düzenlemenin pencere boyutu ve görüntüleme ayarlarında yapılan değişiklikler üzerinde tutulmasını sağlamak için WPF düzen sistemini kullanırsınız. Çoğu uygulama, kullanıcıların verilerle etkileşime girmesine izin vertiğinden, Kullanıcı arabiriminizi verilerle tümleştirme işini azaltmak için veri bağlamayı kullanırsınız. Uygulamanızın görsel görünümünü geliştirmek için WPF tarafından sunulan kapsamlı grafik, animasyon ve medya desteği aralığını kullanırsınız.

Genellikle, temel bilgiler, gerçekten ayrı ve görsel açıdan etkileyici bir kullanıcı deneyimi oluşturmak ve yönetmek için yeterli değildir. Standart WPF denetimleri uygulamanızın istenen görünümüyle tümleştirilemeyebilir. Veriler en etkili şekilde görüntülenmeyebilir. Uygulamanızın genel kullanıcı deneyimi, Windows temalarının varsayılan görünümü ve hislerine uygun olmayabilir. Birçok şekilde, bir sunum teknolojisinin diğer genişletilebilirlik türleri kadar çok görsel genişletilebilirliği olması gerekir.

Bu nedenle WPF, denetimler, Tetikleyiciler, denetim ve veri şablonları, stiller, Kullanıcı arabirimi kaynakları ve Temalar ve kaplamalar için zengin bir içerik modeli de dahil olmak üzere benzersiz kullanıcı deneyimleri oluşturmak için çeşitli mekanizmalar sunar.

### <a name="content-model"></a>İçerik modeli

WPF denetimlerinin çoğunluğunun ana amacı içeriği görüntülemektir. WPF içinde, bir denetimin içeriğini oluşturan öğelerin türü ve sayısı denetimin *içerik modeli*olarak adlandırılır. Bazı denetimler, tek bir öğe ve içerik türü içerebilir; Örneğin, bir <xref:System.Windows.Controls.TextBox> içeriği <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine atanan bir dize değeridir. Aşağıdaki örnek bir <xref:System.Windows.Controls.TextBox> içeriğini ayarlar.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Aşağıdaki şekilde sonuç gösterilmektedir.

![Metin içeren TextBox denetimi](../designers/media/wpfintrofigure21.png)

Bununla birlikte, diğer denetimler farklı türde içeriklerde birden çok öğe içerebilir; <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği tarafından belirtilen <xref:System.Windows.Controls.Button> içeriği, düzen denetimleri, metin, Resimler ve şekiller gibi çeşitli öğeleri içerebilir. Aşağıdaki örnekte, bir <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border> ve <xref:System.Windows.Controls.MediaElement> içeren içeriğe sahip bir <xref:System.Windows.Controls.Button> gösterilmektedir.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

Aşağıdaki şekilde bu düğmenin içeriği gösterilmektedir.

![Birden çok türde içerik içeren bir düğme](../designers/media/wpfintrofigure22.png)

Çeşitli denetimler tarafından desteklenen içerik türleri hakkında daha fazla bilgi için bkz. [WPF içerik modeli](/dotnet/framework/wpf/controls/wpf-content-model).

### <a name="triggers"></a>Tetikleyiciler

XAML biçimlendirmesinin ana amacı uygulamanın görünümünü uygulamak olsa da, bir uygulamanın davranışının bazı yönlerini uygulamak için XAML de kullanabilirsiniz. Bir örnek, bir uygulamanın görünümünü kullanıcı etkileşimlerine göre değiştirmek için tetikleyicilerin kullanılması. Daha fazla bilgi için bkz. [Stiller ve şablonlar](/dotnet/desktop-wpf/fundamentals/styles-templates-overview).

### <a name="control-templates"></a>Denetim şablonları

WPF denetimleri için varsayılan kullanıcı arabirimleri genellikle diğer denetimlerden ve şekillerden oluşturulur. Örneğin, bir <xref:System.Windows.Controls.Button> hem <xref:Microsoft.Windows.Themes.ButtonChrome> hem de <xref:System.Windows.Controls.ContentPresenter> denetimlerinden oluşur. @No__t_0, standart düğme görünümünü sağlar. <xref:System.Windows.Controls.ContentPresenter>, düğme içeriğini <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği tarafından belirtilen şekilde görüntüler.

Bazen bir denetimin varsayılan görünümü bir uygulamanın genel görünümüyle birlikte kullanılamaz. Bu durumda, içeriğini ve davranışını değiştirmeden denetimin kullanıcı arabiriminin görünümünü değiştirmek için bir <xref:System.Windows.Controls.ControlTemplate> kullanabilirsiniz.

Örneğin, aşağıdaki örnek, bir <xref:System.Windows.Controls.ControlTemplate> kullanarak <xref:System.Windows.Controls.Button> görünümünün nasıl değiştirileceğini gösterir.

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_17.vb)]

Bu örnekte, varsayılan düğme Kullanıcı arabirimi koyu mavi kenarlığa sahip bir <xref:System.Windows.Shapes.Ellipse> değiştirilmiştir ve <xref:System.Windows.Media.RadialGradientBrush> kullanılarak doldurulmuştur. @No__t_0 denetim <xref:System.Windows.Controls.Button> içeriğini görüntüler, "bana tıklayın!" @No__t_0 tıklandığında, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay <xref:System.Windows.Controls.Button> denetiminin varsayılan davranışının parçası olarak yine de oluşturulur. Sonuç aşağıdaki şekilde gösterilmiştir:

![Elips düğme ve ikinci bir pencere](../designers/media/wpfintrofigure2.png)

### <a name="data-templates"></a>Veri şablonları

Bir denetim şablonu bir denetimin görünümünü belirtmenize izin verirken, bir veri şablonu bir denetimin içeriğinin görünümünü belirtmenize olanak tanır. Veri şablonları genellikle, bağlantılı verilerin nasıl görüntülendiğini iyileştirmek için kullanılır. Aşağıdaki şekilde, her görevin bir ad, açıklama ve önceliğe sahip olduğu bir `Task` nesneleri koleksiyonuna bağlanan bir <xref:System.Windows.Controls.ListBox> için varsayılan görünüm gösterilmektedir.

![Varsayılan görünümü içeren bir liste kutusu](../designers/media/wpfintrofigure18.png)

Varsayılan görünüm, <xref:System.Windows.Controls.ListBox> beklediğiniz şeydir. Ancak, her görevin varsayılan görünümü yalnızca görev adını içerir. Görev adını, açıklamasını ve önceliğini göstermek için, <xref:System.Windows.Controls.ListBox> denetiminin bağlantılı liste öğelerinin varsayılan görünümünün bir <xref:System.Windows.DataTemplate> kullanılarak değiştirilmesi gerekir. Aşağıdaki XAML, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özniteliği kullanılarak her bir göreve uygulanan böyle bir <xref:System.Windows.DataTemplate> tanımlar.

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

Aşağıdaki şekilde bu kodun etkisi gösterilmektedir.

![Veri şablonu kullanan liste kutusu](../designers/media/wpfintrofigure19.png)

@No__t_0 davranışını ve genel görünümünü beklediğini unutmayın; yalnızca liste kutusu tarafından görüntülenmekte olan içeriğin görünümü değişmiştir.

Daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](/dotnet/framework/wpf/data/data-templating-overview).

### <a name="styles"></a>Stiller

Stiller, geliştiricilerin ve tasarımcıların ürünlerinin belirli bir görünümünü standartlaştırmasını sağlar. WPF, <xref:System.Windows.Style> öğesi olan bir güçlü stil modeli sunar. Aşağıdaki örnek, bir penceredeki her <xref:System.Windows.Controls.Button> için arka plan rengini `Orange` olarak ayarlayan bir stil oluşturur.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

Bu stil tüm <xref:System.Windows.Controls.Button> denetimlerini hedeflediğinden, stil aşağıdaki şekilde gösterildiği gibi penceredeki tüm düğmelere otomatik olarak uygulanır:

![İki turuncu düğme](../designers/media/wpfintrofigure20.png)

Daha fazla bilgi için bkz. [Stiller ve şablonlar](/dotnet/desktop-wpf/fundamentals/styles-templates-overview).

### <a name="resources"></a>Kaynaklar

Bir uygulamadaki denetimler aynı görünümü paylaşmalıdır. Bu, yazı tiplerinden ve arka plan renklerinden şablonları, veri şablonlarını ve stilleri denetleyebilen herhangi bir şeyi içerebilir. Bu kaynakları yeniden kullanım için tek bir konumda kapsüllemek üzere, WPF 'nin Kullanıcı arabirimi kaynakları desteğini kullanabilirsiniz.

Aşağıdaki örnek, bir <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Label> tarafından paylaşılan ortak bir arka plan rengi tanımlar.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

Bu örnek `Window.Resources` Property öğesini kullanarak bir arka plan rengi kaynağı uygular. Bu kaynak <xref:System.Windows.Window> tüm alt öğeleri için kullanılabilir. Aşağıdakiler de dahil olmak üzere çeşitli kaynak kapsamları çözümlendikleri sırayla listelenmiştir:

1. Tek bir denetim (devralınan <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> özelliğini kullanarak).

2. Bir <xref:System.Windows.Window> veya <xref:System.Windows.Controls.Page> (devralınan <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> özelliğini de kullanarak).

3. Bir <xref:System.Windows.Application> (<xref:System.Windows.Application.Resources%2A?displayProperty=fullName> özelliğini kullanarak).

Çeşitli kapsamlar, kaynaklarınızı tanımladığınız ve paylaştığınız yönteme göre esneklik sağlar.

Kaynaklarınızın belirli bir kapsamla doğrudan ilişkilendirilmesi için alternatif olarak, bir veya daha fazla kaynağı, uygulamanın diğer bölümlerinde başvurulabilen ayrı bir <xref:System.Windows.ResourceDictionary> kullanarak paketleyebilir. Örneğin, aşağıdaki örnekte kaynak sözlüğünde varsayılan bir arka plan rengi tanımlanmaktadır.

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

Aşağıdaki örnek, bir uygulama genelinde paylaşılabilmesi için önceki örnekte tanımlanan kaynak sözlüğüne başvurur.

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

Kaynaklar ve kaynak sözlükleri, Temalar ve kaplamalar için WPF desteğinin temelini içerir.

Daha fazla bilgi için bkz. [kaynaklar](/dotnet/framework/wpf/advanced/xaml-resources).

### <a name="custom-controls"></a>Özel denetimler

WPF, özelleştirme desteği sunan bir konak sağlasa da, mevcut WPF denetimlerinin uygulamanızın veya kullanıcılarınızın ihtiyaçlarını karşılamadığında karşılaşabileceğiniz durumlarla karşılaşabilirsiniz. Bu durum şu durumlarda oluşabilir:

- İhtiyaç duyduğunuz Kullanıcı arabirimi, mevcut WPF uygulamalarının görünümü özelleştirilerek oluşturulamaz.

- Gerekli olan davranış, mevcut WPF uygulamaları tarafından desteklenmez (veya kolayca desteklenmez).

Ancak, bu noktada, yeni bir denetim oluşturmak için üç WPF modelinden birini kullanabilirsiniz. Her model belirli bir senaryoyu hedefler ve özel denetiminizin belirli bir WPF Taban sınıfından türemesini gerektirir. Üç model burada listelenmiştir:

- **Kullanıcı denetimi modeli**. Özel denetim <xref:System.Windows.Controls.UserControl> türetilir ve bir veya daha fazla denetimden oluşur.

- **Denetim modeli**. Özel bir denetim <xref:System.Windows.Controls.Control> türetilir ve davranışlarını, WPF denetimlerinin çoğunluğuna benzer şekilde, şablonları kullanarak görünüşlerinden ayıran uygulamalar oluşturmak için kullanılır. @No__t_0 türetmek, Kullanıcı denetimlerinden özel bir kullanıcı arabirimi oluşturmak için daha fazla özgürlük sağlar, ancak daha fazla çaba gerektirebilir.

- **Framework öğe modeli**. Özel bir denetim, görünümü özel işleme mantığı (şablon değil) tarafından tanımlandığında <xref:System.Windows.FrameworkElement> türetilir.

Aşağıdaki örnek, <xref:System.Windows.Controls.UserControl> türetilen özel bir sayısal yukarı/aşağı denetimi gösterir.

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/CSharp/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/VisualBasic/introduction-to-wpf_34.vb)]

Sonraki örnekte, Kullanıcı denetimini bir <xref:System.Windows.Window> eklemek için gereken XAML gösterilmektedir.

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_37.xaml)]

Aşağıdaki şekilde, bir <xref:System.Windows.Window> barındırılan `NumericUpDown` denetimi gösterilmektedir.

![Özel bir UserControl](../designers/media/wpfintrofigure3.png)

Özel denetimler hakkında daha fazla bilgi için bkz. [Denetim yazma genel bakış](/dotnet/framework/wpf/controls/control-authoring-overview).

## <a name="wpf-best-practices"></a>WPF en iyi uygulamaları

Her türlü geliştirme platformunda olduğu gibi, WPF istenen sonuca ulaşmak için çeşitli yollarla kullanılabilir. WPF uygulamalarınızın gerekli Kullanıcı deneyimini sağlayıp, genel olarak hedef kitle taleplerini karşıladığından emin olmanın bir yolu olarak erişilebilirlik, Genelleştirme ve yerelleştirme ve performans için önerilen en iyi uygulamalar vardır. Daha fazla bilgi için bkz.:

- [Erişilebilirlik](/dotnet/framework/ui-automation/accessibility-best-practices)
- [WPF Genelleştirme ve yerelleştirme](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)
- [WPF uygulama performansı](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [WPF güvenliği](/dotnet/framework/wpf/security-wpf)

## <a name="next-steps"></a>Sonraki adımlar

WPF 'nin temel özelliklerine baktık. Şimdi ilk WPF uygulamanızı oluşturma zamanı.

> [!div class="nextstepaction"]
> [İzlenecek yol: ilk WPF Masaüstü Uygulamam](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)

## <a name="see-also"></a>Ayrıca bkz.

- [WPF kullanmaya başlama](../designers/getting-started-with-wpf.md)
- [Windows Presentation Foundation](/dotnet/framework/wpf/index)
- [WPF topluluk kaynakları](/dotnet/framework/wpf/getting-started/community-feedback)