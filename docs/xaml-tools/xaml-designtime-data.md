---
title: Tasarım Zamanı Verilerini XAML Tasarımcısı ile Visual Studio
description: XAML'de tasarım zamanı verilerini kullanmayı öğrenin.
ms.date: 04/22/2021
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
monikerRange: '>=vs-2019'
ms.openlocfilehash: 3867c12dddd57403bc744711a75f31866f0aec90
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045625"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Tasarım Zamanı Verilerini XAML Tasarımcısı ile Visual Studio

Bazı düzenleri veri olmadan görselleştirmek zordur. Bu belgede, masaüstü projelerinde çalışan geliştiricilerin XAML tasarımcısında sahte veriler için kullanabileceği yaklaşımlardan birini gözden geçireceğiz. Bu yaklaşım, var olan Ignorable "d:" ad alanı kullanılarak yapılır. Bu yaklaşımla, tam bir sahte ViewModel oluşturmanıza gerek kalmadan sayfalarınıza veya denetimlerinize tasarım zamanı verilerini hızla ekleyebilir veya bu değişikliklerin yayın derlemelerinizi etkileyeceğini düşünmeden özellik değişikliğinin uygulamanızı nasıl etkileyeyeceğini test edersiniz. Tüm d: veriler yalnızca XAML Tasarımcısı tarafından kullanılır ve yalıtılamaz ad alanı değerleri uygulamaya derlenmiş olmaz.

> [!NOTE]
> Xamarin.Forms kullanıyorsanız bkz. [Xamarin.Forms Tasarım Zamanı Verileri](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>Tasarım Zamanı Verileri temel bilgileri

Tasarım zamanı verileri, denetimlerinizi veri kümesinde görselleştirmeyi kolaylaştırmak için ayar XAML Tasarımcısı. Çalışmaya başlamanız için, henüz mevcut olmayan XAML belgenizin üst bilgisinde aşağıdaki kod satırlarını ekleyin:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Ad alanlarını ekledikten sonra, herhangi bir özniteliğin veya denetimin önüne koyarak yalnızca çalışma `d:` zamanında değil XAML Tasarımcısı içinde gösterebilirsiniz.

Örneğin, genellikle buna bağlı verileri olan bir TextBlock'a metin eklersiniz.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![TextBlock içinde metin olan tasarım zamanı verileri](media\xaml-design-time-textblock.png "Etiket metniyle tasarım zamanı verileri")](media\xaml-design-time-textblock.png#lightbox)

Bu örnekte, `d:Text` olmadan, XAML Tasarımcısı TextBlock için hiçbir şey göstermez. Bunun yerine , "Name!" Burada TextBlock çalışma zamanında gerçek verilere sahip olur.

Herhangi bir UWP veya WPF .NET Core denetimi için renkler, yazı tipi boyutları ve boşluk gibi `d:` özniteliklerle kullanabilirsiniz. Hatta denetimin kendisine de eklersiniz.

```xml
<d:Button Content="Design Time Button" />
```

[![Düğme denetimi ile tasarım zamanı verileri](media\xaml-design-time-button.png "Düğme denetimi ile tasarım zamanı verileri")](media\xaml-design-time-button.png#lightbox)

Bu örnekte düğme yalnızca tasarım zamanında görüntülenir. Özel bir denetime yer tutucu koymak veya farklı denetimleri denemek için bu yöntemi kullanın. Çalışma `d:` zamanı sırasında tüm öznitelikler ve denetimler yoksayılır.

## <a name="preview-images-at-design-time"></a>Tasarım zamanında görüntüleri önizleme

Sayfaya bağlı veya dinamik olarak yüklenen görüntüler için tasarım zamanı kaynağı oluşturabilirsiniz. Projenize eklemek istediğiniz görüntüyü XAML Tasarımcısı ekleyin. Daha sonra bu görüntüyü tasarım zamanında XAML Tasarımcısı görüntüde gösterebilirsiniz:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> Bu örnekteki görüntünün çözümde mevcut olması gerekir.

## <a name="design-time-data-for-listviews"></a>ListViews için tasarım zamanı verileri

ListViews, Desktop uygulamanıza veri görüntülemenin popüler bir yolu olarak kullanılır. Ancak veri olmadan görselleştirmek zordur. ItemSource veya Items satır içi tasarım zamanı verileri oluşturmak için bu özelliği kullanabilirsiniz. Bu XAML Tasarımcısı, ListView'uzda tasarım zamanında bu dizide ne olduğunu görüntüler.

### <a name="wpf-net-core-example"></a>WPF .NET Core örneği
system:String türünü kullanmak için XAML üst bilginize `xmlns:system="clr-namespace:System;assembly=mscorlib` dahil olduğundan emin olun.

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![ListView ile tasarım zamanı verileri](media\xaml-design-time-listview-strings.png "ListView ile tasarım zamanı verileri")](media\xaml-design-time-listview-strings.png#lightbox)

Bu önceki örnekte, önceki örnekte üç TextBlocks'a sahip bir ListView XAML Tasarımcısı.

Ayrıca bir veri nesnesi dizisi de oluşturabilirsiniz. Örneğin, bir veri nesnesinin `City` genel özellikleri tasarım zamanı verileri olarak oluşturulur.

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

XAML'de sınıfını kullanmak için kök düğümdeki ad alanını içeri aktarmanız gerekir.

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![ListView ile tasarım zamanı verisinde gerçek model](media\xaml-design-time-listview-models.png "ListView ile gerçek model tasarım zamanı verileri")](media\xaml-design-time-listview-models.png#lightbox)

Burada avantajı, denetimlerinizi modelinizin tasarım zamanı statik sürümüne bağlayabilirsiniz.

### <a name="uwp-example"></a>UWP örneği

X:Array, UWP'de desteklenmiyor. Bu nedenle bunun yerine `<d:ListView.Items>` kullanabiliriz. system:String türünü kullanmak için XAML üst bilginize `http://schemas.microsoft.com/winfx/2009/xaml` dahil olduğundan emin olun.

```xml
    <StackPanel>
        <ListView>
            <d:ListView.Items>
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </d:ListView.Items>
        </ListView>
    </StackPanel>
```

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Özel türler ve özelliklerle tasarım zamanı verilerini kullanma

Bu özellik varsayılan olarak yalnızca platform denetimleri ve özellikleriyle çalışır. Bu bölümde, Visual Studio 2019 sürüm [16.8](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümü kullanan müşterilerin kullanabileceği yeni bir özellik olan tasarım zamanı denetimleri olarak kendi özel denetimlerinizi kullanmanızı sağlamak için gereken adımların üzerinden geçeceğiz. Bunu etkinleştirmek için üç gereklilik vardır:

- Özel xmlns ad alanı

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Ad alanınız için tasarım zamanı sürümü. Bu, yalnızca sonuna /design ekli olarak sağlanmıştır.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- tasarım zamanı ön ekini mc:Ignorable'a ekleme

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

Tüm bu adımları tamamladikten sonra, tasarım zamanı `myDesignTimeControls` denetimlerinizi oluşturmak için ön ekini kullanabilirsiniz.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Özel xmlns ad alanı oluşturma

WPF .NET Core'da özel xmlns ad alanı oluşturmak için özel XML ad alanınızı denetimlerinizin içinde yer alan CLR ad alanına eşlemeniz gerekir. Bunu yapmak için dosyanıza `XmlnsDefinition` derleme düzeyi özniteliğini `AssemblyInfo.cs` ebilirsiniz. Dosya, projenizin kök hiyerarşisinde bulunur.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Sorun giderme

Bu bölümde listelenmiyor olan bir sorunla karşı karşısanız lütfen Sorun Bildir aracını [kullanarak bize haber](../ide/how-to-report-a-problem-with-visual-studio.md) verebilirsiniz.

### <a name="requirements"></a>Gereksinimler

- Tasarım zamanı verileri için 2019 Visual Studio [16.7 veya sonraki bir sürümü](/visualstudio/releases/2019/release-notes-v16.7) gerekir.

- .NET Core Windows UWP için Windows Presentation Foundation (WPF) hedef alan masaüstü projelerini destekler. Bu özellik, Önizleme kanalında .NET Framework için [de kullanılabilir.](/visualstudio/releases/2019/release-notes-preview) Etkinleştirmek için Araçlar Seçenekler Ortam Önizleme **Özellikleri'ne** gidin, Yeni  >    >    >   **WPF XAML Tasarımcısı'.NET Framework'ı** seçin ve Visual Studio.

- 2019 Visual Studio 16.7 sürümünden başlayarak, bu özellik WPF ve UWP çerçevelerinden gelen tüm in-the-box denetimleriyle çalışır. Üçüncü taraf denetimleri için destek artık [16.8 yayında kullanılabilir.](/visualstudio/releases/2019/release-notes/)

### <a name="the-xaml-designer-stopped-working"></a>XAML Tasarımcısı çalışmayı durdurdu

XAML dosyasını kapatıp yeniden açmayı ve projenizi temizlemeyi ve yeniden oluşturmayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Xamarin.Forms Önizicisi ile Zaman Verileri Tasarlama](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [WPF uygulamalarında XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms uygulamaları içinde XAML](/xamarin/xamarin-forms/xaml/)