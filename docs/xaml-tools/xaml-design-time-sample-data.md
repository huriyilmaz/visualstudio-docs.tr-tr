---
title: Visual Studio XAML Tasarımcısı tasarım zamanı örnek verilerini kullanın
description: XAML 'de tasarım zamanı örnek verilerini nasıl kullanacağınızı öğrenin.
ms.date: 06/01/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
monikerRange: '>=vs-2019'
ms.openlocfilehash: b12ab7e93fbd7c7adab188492853ec4a9230cc7d
ms.sourcegitcommit: 2eb12954b7b0ac9508fff11a86c54e880f3d104f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439814"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Visual Studio XAML Tasarımcısı tasarım zamanı örnek verilerini kullanın

, Ve gibi veri tabanlı bazı denetimlerin `ListView` `ListBox` `DataGrid` veri olmadan görselleştirilmesi zordur. bu makalede, bu denetimlerde örnek verileri etkinleştirmek için Windows Presentation Foundation (WPF) .net Core projelerinde veya wpf .NET Framework projelerinde çalışan geliştiricilerin Visual Studio içindeki XAML Tasarımcısı olan yeni bir yaklaşımı gözden geçireceğiz. 

## <a name="requirements"></a>Gereksinimler

örnek veri özelliği Visual Studio 2019 sürüm [16,10](/visualstudio/releases/2019/release-notes-v16.10) veya üstünü gerektirir.

özelliği, yeni tasarımcıyı kullanırken .net Core veya .NET Framework için WPF 'yi hedefleyen Windows masaüstü projelerini destekler. .NET Framework için yeni tasarımcıyı etkinleştirmek için:

1. **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri**' ne gidin.
2. **.NET Framework için yeni WPF XAML Tasarımcısı** seçin ve Visual Studio yeniden başlatın.

## <a name="basics-of-the-sample-data-feature"></a>Örnek veri özelliğinin temelleri

Örnek veri özelliği yalnızca tasarım zamanı görselleştirmedir. Yalnızca XAML tasarımcısında görünür, çalışan uygulamada değil. Bu nedenle, özelliğin tasarım zamanı sürümüne uygulanır `ItemsSource` `d:ItemsSource` . Örnek veriler için tasarım zamanı ad alanının çalışması gerekir. 

> [!NOTE]
> XAML 'de tasarım zamanı özellikleri hakkında daha fazla bilgi edinmek için bkz. [XAML tasarım zamanı özellikleri](../xaml-tools/xaml-designtime-data.md).

Başlamak için, zaten mevcut değilse XAML belgenizin üstbilgisine aşağıdaki kod satırlarını ekleyin:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Ad alanlarını ekledikten sonra, `d:ItemsSource="{d:SampleData}"` veya denetimindeki örnek verileri etkinleştirmek için kullanabilirsiniz `ListView` `Listbox` `DataGrid` . Örnek:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![Veri kılavuzunda örnek verileri gösteren ekran görüntüsü.](media\xaml-sample-data-empty-datagrid.png "Veri kılavuzunda etkinleştirilen örnek veriler")](media\xaml-sample-data-empty-datagrid.png#lightbox)

Bu örnekte, olmadan `d:ItemsSource="{d:SampleData}"` XAML Tasarımcısı boş bir veri kılavuzu gösterecektir. Bunun yerine, `d:SampleData` artık oluşturulan varsayılan örnek verileri gösterir.

Varsayılan olarak, beş öğe görüntülenir. Ancak, `ItemCount` özelliğini kullanarak kaç öğe görüntülenmesini istediğinizi belirtebilirsiniz. Örneğin: `d:ItemsSource="{d:SampleData ItemCount=2}"`.

## <a name="sample-data-with-data-templates"></a>Veri şablonlarıyla örnek veriler

Örnek veri özelliği `ListBox` , `ListView` `DataGrid` veri şablonlarını kullandığınızda, veya denetimleri için geçerlidir. Özellik denetimi analiz eder `DataTemplate` ve uygun verileri oluşturmaya çalışır. 

Örnek veriler, yalnızca bağlamaları kullanan veri şablonlarındaki öğeler için oluşturulur. Bağlamaların henüz bir kaynağı olmasa bile örnek veriler oluşturulacaktır. Örnek:

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

[![Veri şablonuyla bir liste görünümünde örnek verileri gösteren ekran görüntüsü.](media\xaml-sample-data-templated-listview.png "Veri şablonuyla bir liste görünümünde kullanılan örnek veriler")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="sample-data-with-suggested-actions"></a>Önerilen eylemlerle örnek veriler

Tasarımcıdan bir denetim için örnek verileri kolayca etkinleştirmek veya devre dışı bırakmak için Önerilen Eylemler özelliğini kullanabilirsiniz. Önerilen Eylemler, bir denetim seçtiğinizde sağ üst köşede görüntülenen, tasarımcı üzerinde yer alan bir ampul olur. Denetiminizi seçip ampul ' i seçip **örnek verileri göster**' i seçerek örnek verileri etkinleştirebilirsiniz. Örnek:

[![Önerilen eylemlerle örnek verileri gösteren ekran görüntüsü.](media\xaml-sample-data-suggested-actions.png "Önerilen eylemlerle örnek verileri etkinleştir")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-the-ivalueconverter-interface"></a>IValueConverter arabirimiyle örnek veriler 

Örnek veri özelliği, dönüştürücüleri veya arabirimi tam olarak desteklemez `IValueConverter` . Bununla birlikte, aşağıdakilerden birini veya her ikisini yaparak çalışmasını sağlayabilirsiniz:

- `Convert`İşlevinizin, değerin zaten hedef türü olduğu bir senaryoyu işleyebildiği şekilde emin olun.
- `ConvertBack`Değeri özgün türe geri dönüştürecek işlevi uygulayın. 

## <a name="troubleshooting"></a>Sorun giderme

Örnek verileriniz herhangi bir şeyi göstermiyorsa veya doğru türü göstermiyorsa, tasarımcıyı yenilemeyi veya sayfayı kapatıp yeniden açmayı deneyebilirsiniz.

Bu bölümde listelenmeyen veya sayfa yenilenerek düzeltimeyen bir sorunla karşılaşırsanız lütfen [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanarak bize bildirin.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML tasarım zamanı özellikleri](../xaml-tools/xaml-designtime-data.md)
- [WPF uygulamalarında XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin. Forms uygulamalarındaki XAML](/xamarin/xamarin-forms/xaml/)