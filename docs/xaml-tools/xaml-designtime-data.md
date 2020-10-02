---
title: Visual Studio 'da XAML Tasarımcısı tasarım zamanı verilerini kullanma
description: XAML 'de tasarım zamanı verilerini nasıl kullanacağınızı öğrenin.
ms.date: 09/29/2020
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: 6957c1c7d64918e91a95bf569c210c146fec1339
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659427"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Visual Studio 'da XAML Tasarımcısı tasarım zamanı verilerini kullanma

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

ListViews, masaüstü uygulamanızdaki verileri görüntülemenin popüler bir yoludur. Ancak, herhangi bir veri olmadan görselleştirmeleri zordur. Bu özelliği, bir satır içi tasarım zamanı veri ItemSource oluşturmak için kullanabilirsiniz. XAML Tasarımcısı, tasarım zamanında ListView içinde bu dizide yer alan öğeleri görüntüler. Bu, WPF .NET Core için bir örnektir. System: String türünü kullanmak için XAML üst bilgisine dahil ettiğinizden emin olun `xmlns:system="clr-namespace:System;assembly=mscorlib` .

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

## <a name="troubleshooting"></a>Sorun giderme

Bu bölümde listelenmeyen bir sorunla karşılaşırsanız lütfen [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanarak bize bildirin.

### <a name="requirements"></a>Gereksinimler

- Tasarım zamanı verileri, Visual Studio 2019 sürüm [16,7](/visualstudio/releases/2019/release-notes) veya üstünü gerektirir.

- .NET Core ve UWP için Windows Presentation Foundation (WPF) hedefleyen Windows Masaüstü projelerini destekler. Bu özellik, "Yeni WPF XAML Tasarımcısı for .NET Framework" Önizleme özelliği etkinse .NET Framework için de kullanılabilir.

- Visual Studio 2019 sürüm 16,7 ' den itibaren, bu özellik WPF ve UWP çerçevelerinden gelen tüm yerleşik denetimlerle birlikte kullanılabilir. Üçüncü taraf denetimleri için destek artık 16,8 Önizleme sürümünde sunulmaktadır.

### <a name="the-xaml-designer-stopped-working"></a>XAML Tasarımcısı çalışmayı durdurdu

XAML dosyasını kapatıp yeniden açmayı ve projenizi temizleyip yeniden oluşturmayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Xamarin. Forms önizleyicisi ile tasarım zamanı verileri](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [WPF uygulamalarında XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin. Forms uygulamalarındaki XAML](/xamarin/xamarin-forms/xaml/)