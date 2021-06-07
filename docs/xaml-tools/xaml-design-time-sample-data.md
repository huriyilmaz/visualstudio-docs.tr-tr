---
title: Tasarım zamanı örnek verilerini veri kaynağında XAML Tasarımcısı kullanın Visual Studio
description: XAML'de tasarım zamanı örnek verilerini kullanmayı öğrenin.
ms.date: 06/01/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: 8303e1150db7c12c404e8f67bce52418fbd05b9d
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433798"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Tasarım zamanı örnek verilerini veri kaynağında XAML Tasarımcısı kullanın Visual Studio

ListView, ListBox veya DataGrid gibi bazı veriye yönelik denetimleri veri olmadan görselleştirmek zordur. Bu belgede, **WPF .NET Core** projeleri veya WPF projelerinde çalışan geliştiricilerin bu denetimlerde örnek verileri etkinleştirmek için yeni tasarımcıyla **WPF .NET Framework** projelerine olanak sağlayan yeni bir yaklaşımı gözden geçireceğiz. 

## <a name="sample-data-feature-basics"></a>Örnek veri özelliği temelleri

Örnek veriler yalnızca tasarım zamanı görselleştirmesi için kullanılır; yani çalışan uygulamada değil yalnızca XAML tasarımcısında görünür. Bu nedenle, ItemsSource özelliğinin tasarım zamanı sürümüne `d:ItemsSource` uygulanır. Örnek Veriler için tasarım zamanı ad alanının çalışması gerekir. Çalışmaya başlamanız için, henüz yoksa XAML belgenizin üst bilgisinde aşağıdaki kod satırlarını ekleyin:

> [!NOTE]
> [XAML'de tasarım zamanı özellikleri hakkında daha](../xaml-tools/xaml-designtime-data.md) fazla bilgi edinmek için XAML tasarım zamanı özelliklerini ziyaret edin.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Ad alanlarını ekledikten sonra `d:ItemsSource="{d:SampleData}"` ListView, Listbox veya DataGrid'inize örnek verileri etkinleştirmek için kullanabilirsiniz. Örneğin:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![DataGrid ile örnek veriler](media\xaml-sample-data-empty-datagrid.png "DataGrid üzerinde etkinleştirilmiş örnek veriler")](media\xaml-sample-data-empty-datagrid.png#lightbox)

Bu örnekte, veri `d:ItemsSource="{d:SampleData}"` XAML Tasarımcısı boş bir DataGrid gösterebilir. Bunun yerine, `d:SampleData` artık oluşturulan varsayılan örnek verileri gösterir.

Varsayılan olarak 5 öğe görüntülenir. Ancak, görüntülemek istediğiniz öğe sayısı belirtmek için **ItemCount** özelliğini kullanabilirsiniz. örneğin: `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>Örnek veriler veri platformları ile çalışır

Örnek Veriler, veri şablonlarını kullanırsanız ListBox, ListView veya DataGrid denetimleri için çalışır. Örnek Veri özelliği DataTemplate'i analiz eder ve uygun verileri üretmeyi dener. Örnek Veriler yalnızca DataTemplates'te bağlamaları kullanan öğeler için oluşturulur. Bağlamaların henüz kaynağı yoksa bile örnek veriler oluşturulur.
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

[![DataTemplate ile Örnek Veri ListView](media\xaml-sample-data-templated-listview.png "DataTemplate ile ListView'da Kullanılan Örnek Veriler")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>Önerilen eylemlerle örnek verileri etkinleştirme

Tasarımcıdan bir denetim için Örnek Verileri kolayca etkinleştirmek veya devre dışı bırakmak için Önerilen Eylemler özelliğini kullanabilirsiniz. Önerilen Eylemler, bir denetimi seçerek sağ üst kısmından çıkan tasarımcıda bir ampul olur. Denetiminizi seçerek, ampule ve ardından seçeneğine tıklayarak Örnek Veriler'i `Show Sample Data` etkinleştirebilirsiniz. Örneğin:

[![Örnek Veriler Için Önerilen Eylemler](media\xaml-sample-data-suggested-actions.png "Önerilen Eylemlerle Örnek Verileri Etkinleştirme")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>IValueConverters ile örnek veriler 

Dönüştürücüler, Örnek Veri özelliği tarafından tam olarak desteklanmaz. Ancak, aşağıdakilerden birini veya her ikisini birden yaparak bu işi gerçekleştirin:
- İşlevin değerin `Convert` zaten targetType değerine sahip olduğu bir senaryoyu işleyeyene sahip olduğundan emin olun.

- Değerinizi `ConvertBack` özgün türe geri dönüştürecek işlevi uygulama. 

## <a name="troubleshooting"></a>Sorun giderme

Örnek Verileriniz herhangi bir şey göstermezse veya doğru türü gösteremezse tasarımcıyı yenilemeyi veya sayfayı kapatıp yeniden açmayı sınabilirsiniz.

Bu bölümde listelenmiyor veya sayfayı yenilerken düzeltileyemeyebilirsiniz. Sorun Bildir aracını kullanarak bunu [bize bildirebilirsiniz.](../ide/how-to-report-a-problem-with-visual-studio.md)

### <a name="requirements"></a>Gereksinimler

- Örnek Veriler için Visual Studio 2019 sürüm [16.10 veya](/visualstudio/releases/2019/release-notes-v16.10) sonraki bir sürümü gerekir.

- Yeni tasarımcı kullanılırken .NET Core Windows Presentation Foundation 'ı (WPF) .NET Framework Windows masaüstü projelerini destekler. .NET Framework tasarımcısını etkinleştirmek için Araçlar > Seçenekleri > Ortamı > Önizleme Özellikleri'ne gidin, .NET Framework için Yeni WPF XAML Tasarımcısı'yi seçin ve Visual Studio.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML tasarım zamanı özellikleri](../xaml-tools/xaml-designtime-data.md)
- [WPF uygulamalarında XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms uygulamaları içinde XAML](/xamarin/xamarin-forms/xaml/)