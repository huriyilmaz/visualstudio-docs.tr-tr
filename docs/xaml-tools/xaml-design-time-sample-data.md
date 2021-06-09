---
title: Visual Studio 'da XAML Tasarımcısı tasarım zamanı örnek verilerini kullanma
description: XAML 'de tasarım zamanı örnek verilerini nasıl kullanacağınızı öğrenin.
ms.date: 06/01/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: 66418d351280a0c067327716766725d22488131b
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760919"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Visual Studio 'da XAML Tasarımcısı tasarım zamanı örnek verilerini kullanma

ListView, ListBox veya DataGrid gibi bazı veri bağımlı denetimlerin veri olmadan görselleştirilmesi zor. Bu belgede, bu denetimlerde örnek verileri etkinleştirmek için **WPF .NET Core** projelerinde veya **WPF .NET Framework** projeler üzerinde çalışan geliştiricilerin yeni tasarımcı ile çalışmasına imkan tanıyan yeni bir yaklaşımı gözden geçireceğiz. 

## <a name="sample-data-feature-basics"></a>Örnek veri özelliği temelleri

Örnek veriler yalnızca tasarım zamanı görselleştirme amaçlıdır; Yani, çalışan uygulamada değil yalnızca XAML tasarımcısında görünür. Bu nedenle, ıtemı kaynak özelliğinin tasarım zamanı sürümüne uygulanır `d:ItemsSource` . Örnek veriler için tasarım zamanı ad alanının çalışması gerekir. Başlamak için, zaten mevcut değilse XAML belgenizin üstbilgisine aşağıdaki kod satırlarını ekleyin:

> [!NOTE]
> XAML 'de tasarım zamanı özellikleri hakkında daha fazla bilgi edinmek için [XAML tasarım zamanı özelliklerini](../xaml-tools/xaml-designtime-data.md) ziyaret edin.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Ad alanlarını ekledikten sonra, `d:ItemsSource="{d:SampleData}"` ListView, ListBox veya DataGrid uygulamanızda örnek verileri etkinleştirmek için kullanabilirsiniz. Örneğin:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![DataGrid ile örnek veriler](media\xaml-sample-data-empty-datagrid.png "DataGrid üzerinde etkin örnek veriler")](media\xaml-sample-data-empty-datagrid.png#lightbox)

Bu örnekte, XAML Tasarımcısı olmadan `d:ItemsSource="{d:SampleData}"` boş bir DataGrid gösterilecektir. Bunun yerine, `d:SampleData` artık oluşturulan varsayılan örnek verileri gösterir.

Varsayılan olarak, 5 öğe gösterilir. Ancak, **ItemCount** özelliğini kullanarak kaç öğe görüntülenmesini istediğinizi belirtebilirsiniz. Örneğin: `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>Örnek veriler, veri şablonları ile birlikte kullanılabilir

Veri şablonlarını kullandığınızda, örnek veriler ListBox, ListView veya DataGrid denetimleri için geçerlidir. Örnek veri özelliği, DataTemplate 'i analiz eder ve uygun verileri oluşturmaya çalışır. Örnek veriler yalnızca bağlamaları kullanan veri şablonlarındaki öğeler için oluşturulur. Bağlamaların henüz bir kaynağı olmasa bile örnek veriler oluşturulacaktır.
Örneğin:

```xml
<ListView d:ItemsSource="{d:SampleData ItemCount=3}">
     <ListView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <Image Width="50" Source="{Binding ProfilePicture}"/>
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{Binding FirstName}" Margin="5"/>
                    <Label Content="{Binding LastName}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

[![DataTemplate ile örnek veri ListView](media\xaml-sample-data-templated-listview.png "DataTemplate ile ListView 'da kullanılan örnek veriler")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>Önerilen eylemlerle örnek verileri etkinleştir

Tasarımcıdan bir denetim için örnek verileri kolayca etkinleştirmek veya devre dışı bırakmak için Önerilen Eylemler özelliğini kullanabilirsiniz. Önerilen Eylemler, tasarımcı üzerinde bir denetim seçtiğinizde en sağ üst kısımdaki bir ampul olduğunu gösterir. Denetiminizi seçerek ve ardından açık ampul ' e tıklayıp açık ' a tıklayarak örnek verileri etkinleştirebilirsiniz `Show Sample Data` . Örneğin:

[![Örnek verileri Önerilen Eylemler](media\xaml-sample-data-suggested-actions.png "Önerilen eylemlerle örnek verileri etkinleştir")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>Ivalueconverters ile örnek veriler 

Dönüştürücüler, örnek veri özelliği tarafından tam olarak desteklenmez. Bununla birlikte, aşağıdakilerden birini veya her ikisini yaparak çalışmasını sağlayabilirsiniz:
- `Convert`İşlevinizin, değerinin zaten TargetType 'inizin bulunduğu bir senaryoyu işleyebileceğini doğrulayın.

- `ConvertBack`Değeri özgün türe geri dönüştürecek işlevi uygulayın. 

## <a name="troubleshooting"></a>Sorun giderme

Örnek verileriniz herhangi bir şeyi göstermiyorsa veya doğru türü göstermiyorsa, tasarımcıyı yenilemeyi veya sayfayı kapatıp yeniden açmayı deneyebilirsiniz.

Bu bölümde listelenmeyen bir sorunla karşılaşırsanız veya sayfa yenilenerek düzeltilenemez, lütfen [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanarak bize bildirin.

### <a name="requirements"></a>Gereksinimler

- Örnek veriler, Visual Studio 2019 sürüm [16,10](/visualstudio/releases/2019/release-notes-v16.10) veya üstünü gerektirir.

- .NET Core için Windows Presentation Foundation (WPF) veya yeni tasarımcı kullanılırken .NET Framework hedeflenen Windows Masaüstü projelerini destekler. .NET Framework için yeni tasarımcı 'yı etkinleştirmek üzere araçlar > seçenekler > ortam > Önizleme özellikleri ' ne gidin, XAML Tasarımcısı için yeni WPF .NET Framework ' i seçin ve ardından Visual Studio 'Yu yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML tasarım zamanı özellikleri](../xaml-tools/xaml-designtime-data.md)
- [WPF uygulamalarında XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin. Forms uygulamalarındaki XAML](/xamarin/xamarin-forms/xaml/)