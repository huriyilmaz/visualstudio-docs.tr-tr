---
title: Visual Studio XAML Tasarımcısı tasarım zamanı verilerini kullanın
description: XAML 'de tasarım zamanı verilerini nasıl kullanacağınızı öğrenin.
ms.date: 04/22/2021
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
monikerRange: '>=vs-2019'
ms.openlocfilehash: 3b1c2da762be4f1ee9d7b903f9098e82857eec5e08cd4f7fa14315f6e7b54860
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267110"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Visual Studio XAML Tasarımcısı tasarım zamanı verilerini kullanın

Bazı mizanpajlar veri olmadan görselleştirilecek. Bu belgede, masaüstü projeleri üzerinde çalışan geliştiricilerden birini, XAML tasarımcısında veri dokusunu yapmak için kullanabileceğiniz yaklaşımlardan birini inceliyoruz. Bu yaklaşım, var olan yoksayılabilir "d:" ad alanı kullanılarak yapılır. Bu yaklaşım sayesinde, tam bir sahte ViewModel oluşturmaya gerek kalmadan sayfalarınıza veya denetimlerine hızlı bir şekilde tasarım zamanı verileri ekleyebilir veya bir özellik değişikliğinin, bu değişikliklerin yayın derlemelerinizi etkileyeceğini endişelenmeden uygulamanızı nasıl etkileyebileceğini test edebilirsiniz. Tüm d: verileri yalnızca XAML Tasarımcısı tarafından kullanılır ve hiçbir yoksayılabilir ad alanı değeri uygulamaya derlenirler.

> [!NOTE]
> Xamarin. Forms kullanıyorsanız bkz. [Xamarin. Forms tasarım zamanı verileri](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>Tasarım zamanı verileri temelleri

Tasarım zamanı verileri, denetimlerinizi XAML Tasarımcısı görselleştirmeyi kolaylaştırmak için ayarladığınız veri verileri. Başlamak için, zaten mevcut değilse XAML belgenizin üstbilgisine aşağıdaki kod satırlarını ekleyin:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Ad alanlarını ekledikten sonra, `d:` herhangi bir özniteliğin veya denetimin önüne yalnızca XAML Tasarımcısı, çalışma zamanında değil yalnızca gösterilmesini sağlayabilirsiniz.

Örneğin, genellikle veriye bağlanan bir TextBlock öğesine metin ekleyebilirsiniz.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![TextBlock içindeki metinle tasarım zamanı verileri](media\xaml-design-time-textblock.png "Metin etiketli tasarım zamanı verileri")](media\xaml-design-time-textblock.png#lightbox)

Bu örnekte, olmadan `d:Text` XAML Tasarımcısı TextBlock için hiçbir şey göstermez. Bunun yerine, "ad!" gösterir Burada TextBlock, çalışma zamanında gerçek veriye sahip olacaktır.

`d:`Her UWP veya WPF .NET Core denetimi için, renkler, yazı tipi boyutları ve boşluklar gibi özniteliklerle birlikte kullanabilirsiniz. Hatta denetimin kendisine ekleyebilirsiniz.

```xml
<d:Button Content="Design Time Button" />
```

[![Bir düğme denetimiyle tasarım zamanı verileri](media\xaml-design-time-button.png "Bir düğme denetimiyle tasarım zamanı verileri")](media\xaml-design-time-button.png#lightbox)

Bu örnekte, düğme yalnızca tasarım zamanında görüntülenir. Özel bir denetim için ' de bir yer tutucu koymak veya farklı denetimleri denemek için bu yöntemi kullanın. `d:`Çalışma zamanı sırasında tüm öznitelikler ve denetimler yok sayılacak.

## <a name="preview-images-at-design-time"></a>Tasarım zamanında görüntüleri önizleme

Sayfaya bağlı olan veya dinamik olarak yüklenen görüntüler için bir tasarım zamanı kaynağı ayarlayabilirsiniz. XAML Tasarımcısı göstermek istediğiniz görüntüyü projenize ekleyin. Daha sonra bu görüntüyü tasarım zamanında XAML Tasarımcısı gösterebilirsiniz:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> Bu örnekteki görüntünün çözümde mevcut olması gerekir.

## <a name="design-time-data-for-listviews"></a>ListViews için tasarım zamanı verileri

ListViews, masaüstü uygulamanızdaki verileri görüntülemenin popüler bir yoludur. Ancak, herhangi bir veri olmadan görselleştirmeleri zordur. Bu özelliği, bir satır içi tasarım zamanı veri ItemSource veya öğeleri oluşturmak için kullanabilirsiniz. XAML Tasarımcısı, tasarım zamanında ListView içinde bu dizide yer alan öğeleri görüntüler.

### <a name="wpf-net-core-example"></a>WPF .NET Core örneği
System: String türünü kullanmak için XAML üst bilgisine dahil ettiğinizden emin olun `xmlns:system="clr-namespace:System;assembly=mscorlib` .

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

Bu önceki örnekte XAML Tasarımcısı üç metin bloğuyla bir ListView gösterilmektedir.

Ayrıca, veri nesneleri dizisi de oluşturabilirsiniz. Örneğin, bir veri nesnesinin ortak özellikleri `City` Tasarım zamanı verileri olarak oluşturulabilir.

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

Sınıfını XAML 'de kullanmak için, ad alanını kök düğümünde içeri aktarmanız gerekir.

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

[![ListView ile tasarım zamanı verilerinde gerçek model](media\xaml-design-time-listview-models.png "ListView ile gerçek model tasarım zamanı verileri")](media\xaml-design-time-listview-models.png#lightbox)

Buradaki avantaj, denetimlerinizi modelinizin tasarım zamanı statik sürümüne bağlayabilmeniz için gereken avantajdır.

### <a name="uwp-example"></a>UWP örneği

, UWP 'de x:Array desteklenmez. Bu nedenle, `<d:ListView.Items>` bunun yerine kullanabiliriz. System: String türünü kullanmak için XAML üst bilgisine dahil ettiğinizden emin olun `http://schemas.microsoft.com/winfx/2009/xaml` .

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

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Özel türler ve özelliklerle tasarım zamanı verileri kullanma

Bu özellik varsayılan olarak yalnızca platform denetimleri ve özellikleriyle birlikte kullanılabilir. bu bölümde, kendi özel denetimlerinizi tasarım zamanı denetimleri olarak kullanmanıza olanak tanımak için gereken adımları inceleyeceğiz Visual Studio 2019 sürüm [16,8](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümünü kullanan müşteriler için yeni bir özellik sunulmaktadır. Bunu etkinleştirmek için üç gereksinim vardır:

- Özel bir xmlns ad alanı

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Ad alanınız için tasarım zamanı sürümü. Bu, sonunda/Design eklenerek elde edilebilir.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- Tasarım zamanı ön ekini mc: Ignorable 'e ekleme

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

Tüm bu adımları tamamladıktan sonra, `myDesignTimeControls` Tasarım zamanı denetimlerinizi oluşturmak için ön ekini kullanabilirsiniz.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Özel bir xmlns ad alanı oluşturma

WPF .NET Core 'da özel bir xmlns ad alanı oluşturmak için özel XML ad alanınızı, denetimlerinizin bulunduğu CLR ad alanına eşlemeniz gerekir. Bunu, `XmlnsDefinition` dosyanıza derleme düzeyi özniteliğini ekleyerek yapabilirsiniz `AssemblyInfo.cs` . Dosya, projenizin kök hiyerarşisinde bulunur.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Sorun giderme

Bu bölümde listelenmeyen bir sorunla karşılaşırsanız lütfen [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanarak bize bildirin.

### <a name="requirements"></a>Gereksinimler

- tasarım zamanı verileri Visual Studio 2019 sürüm [16,7](/visualstudio/releases/2019/release-notes-v16.7) veya üzeri bir sürümü gerektirir.

- , .net Core ve UWP için Windows Presentation Foundation (WPF) hedefleyen masaüstü projelerini Windows destekler. bu özellik, [önizleme kanalında](/visualstudio/releases/2019/release-notes-preview).NET Framework için de kullanılabilir. etkinleştirmek için **araçlar**  >  **seçenekler**  >  **ortam**  >  **önizleme özellikleri**' ne gidin, **.NET Framework için yeni WPF XAML Tasarımcısı** seçin ve Visual Studio yeniden başlatın.

- Visual Studio 2019 sürüm 16,7 ' den itibaren, bu özellik WPF ve UWP çerçevelerinden gelen tüm yerleşik denetimlerle birlikte kullanılabilir. Üçüncü taraf denetimleri için destek artık [16,8 sürümünde](/visualstudio/releases/2019/release-notes/)sunulmaktadır.

### <a name="the-xaml-designer-stopped-working"></a>XAML Tasarımcısı çalışmayı durdurdu

XAML dosyasını kapatıp yeniden açmayı ve projenizi temizleyip yeniden oluşturmayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Xamarin. Forms önizleyicisi ile tasarım zamanı verileri](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [WPF uygulamalarında XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin. Forms uygulamalarındaki XAML](/xamarin/xamarin-forms/xaml/)