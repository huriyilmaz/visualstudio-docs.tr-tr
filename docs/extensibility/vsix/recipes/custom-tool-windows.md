---
title: Özel araç pencereleri oluşturma
description: Uygulamanıza özel araç pencereleri eklemeye Visual Studio.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: c7080bcb279d5ca50477f7efdf5d51f9340be576
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516740"
---
# <a name="build-custom-tool-windows"></a>Özel araç pencereleri oluşturma

Özel araç pencereleri, uygulamanıza karmaşık kullanıcı arabirimi eklemek için Visual Studio.

Araç penceresi, Visual Studio bir kullanıcı arabirimi kavramıdır ve aşağıdaki videoda özel pencere ekleme adımları gösterilir.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWPhtK]

Araç penceresi, Çözüm Gezgini, Hata Listesi ve diğer iyi bilinen araç pencereleri gibi taşınarak yerleştirilene bir penceredir. Araç penceresi, Visual Studio tarafından sağlanan dış kabuk ve genellikle uzantı tarafından sağlanan bir XAML olan özel bir iç kullanıcı `<usercontrol>` arabirimi denetimidir.

>[!NOTE]
> Araç penceresiyle yeni bir uzantı oluşturmak için **VSIX Project w/Tool Window (Community)** şablonunu kullanarak yeni bir proje oluşturun ve bu tarifin geri kalanını atlayabilirsiniz. Daha [fazla bilgi için](../get-started/first-extension.md) bkz. başlarken.

Mevcut uzantıya araç penceresi eklemek için 4 basit adım gerekir:

1. Bir araç penceresi dış kabuk sınıfı oluşturun.
2. Araç penceresine bir XAML `<usercontrol>` ekleyin.
3. Araç penceresini kaydetme.
4. Araç penceresini göstermek için bir komut oluşturun.

1. adımla başlayalım.

## <a name="create-the-tool-window"></a>Araç penceresini oluşturma
Genel `BaseToolWindow<T>` temel sınıfı kullanarak birkaç temel bilgi sağlamamız istendi. Araç penceresinin başlığını belirtmemiz, XAML kullanıcı denetimi oluşturmamız ve iademiz ve pencerenin dış kabuğunu oluşturmak için Visual Studio tarafından kullanılan gerçek sınıfı `ToolWindowPane` ayarlamamız gerekir.

```csharp
using System;
using System.Runtime.InteropServices;
using System.Threading;
using System.Threading.Tasks;
using System.Windows;
using Community.VisualStudio.Toolkit;
using EnvDTE80;
using Microsoft.VisualStudio.Imaging;
using Microsoft.VisualStudio.Shell;

public class MyToolWindow : BaseToolWindow<MyToolWindow>
{
    public override string GetTitle(int toolWindowId) => "My Tool Window";

    public override Type PaneType => typeof(Pane);

    public override async Task<FrameworkElement> CreateAsync(int toolWindowId, CancellationToken cancellationToken)
    {
        await Task.Delay(2000); // Long running async task
        return new MyUserControl();
    }

    // Give this a new unique guid
    [Guid("d3b3ebd9-87d1-41cd-bf84-268d88953417")] 
    internal class Pane : ToolWindowPane
    {
        public Pane()
        {
            // Set an image icon for the tool window
            BitmapImageMoniker = KnownMonikers.StatusInformation;
        }
    }
}
```

Yönteminden özel kullanıcı denetiminizin bir örneğini oluşturmanız gerekir. Bu örnek, daha sonra bu yöntem tarafından oluşturulurken otomatik olarak araç `CreateAsync(int, CancellationToken)` penceresi kabuğuna Visual Studio.

Ancak öncelikle kullanıcı denetimi oluşturmanız gerekir.

## <a name="add-the-xaml-user-control"></a>XAML kullanıcı denetimi ekleme
Arka arkasındaki kod sınıfına sahip herhangi bir XAML olabilir, bu nedenle tek bir düğme içeren basit `<usercontrol>` bir örnek:

```xml
<UserControl x:Class="MyUserControl"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
             xmlns:toolkit="clr-namespace:Community.VisualStudio.Toolkit;assembly=Community.VisualStudio.Toolkit"
             mc:Ignorable="d"
             toolkit:Themes.UseVsTheme="True"
             d:DesignHeight="300" d:DesignWidth="300"
             Name="MyToolWindow">
    <Grid>
        <StackPanel Orientation="Vertical">
            <Label Margin="10" HorizontalAlignment="Center">My Window</Label>
            <Button Content="Click me!" Click="button1_Click" Width="120" Height="80" Name="button1"/>
        </StackPanel>
    </Grid>
</UserControl>
```

Artık özel denetimimizi döndüren araç pencere sınıfımız var. Sonraki adım, araç penceremizi Visual Studio.

## <a name="register-the-tool-window"></a>Araç penceresini kaydetme
Araç penceresini kaydetmek, Visual Studio ve nasıl örnekleymız olduğunu anlattığımız anlamına gelir. Bunu, özniteliğini kullanarak paket sınıfımızda `[ProvideToolWindow]` yapabiliriz.

```csharp
[ProvideToolWindow(typeof(MyToolWindow.Pane))]
public sealed class MyPackage : ToolkitPackage
{
     protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
     {
         this.RegisterToolWindows();
     }
}
```

>[!NOTE]
> Paket sınıfının veya sınıfından değil, `ToolkitPackage` sınıfından devralması gerektiğini `Package` `AsyncPackage` unutmayın.

Araç penceresinin hangi stile sahip olması gerektiğini ve varsayılan olarak nerede göster gerektiğini belirtebilirsiniz. Aşağıdaki örnek, araç penceresinin bağlantılı stilde yer alan kapsayıcıyla aynı yerleştirme Çözüm Gezgini gerektiğini gösterir.

```csharp
[ProvideToolWindow(typeof(MyToolWindow.Pane), Style = VsDockStyle.Linked, Window = WindowGuids.SolutionExplorer)]
```

Araç penceresini varsayılan olarak görünür yapmak için özniteliğini kullanarak farklı kullanıcı arabirimi bağlamlarında görünürlüğünü `[ProvideToolWindowVisibility]` belirtebilirsiniz.

```csharp
[ProvideToolWindowVisibility(typeof(MyToolWindow.Pane), VSConstants.UICONTEXT.NoSolution_string)]
```

## <a name="command-to-show-the-tool-window"></a>Araç penceresini gösterme komutu
Bu, diğer komutlar ile aynıdır ve Menüler menüsünde Komutlar tarifine [nasıl & bakabilirsiniz.](menus-buttons-commands.md)

Araç penceresini gösteren komut işleyicisi sınıfı şuna benzer olacaktır:

```csharp
using Community.VisualStudio.Toolkit;
using Microsoft.VisualStudio.Shell;
using Task = System.Threading.Tasks.Task;

[Command(PackageIds.RunnerWindow)]
internal sealed class MyToolWindowCommand : BaseCommand<MyToolWindowCommand>
{
    protected override async Task ExecuteAsync(OleMenuCmdEventArgs e) =>
        await MyToolWindow.ShowAsync();
}
```

Araç pencereleri için komut yerleşimi genellikle ana **menüde Görünüm -> Diğer Windows** altındadır.

İşte bu kadar. Tebrikler, özel araç pencerenizi oluşturduğunuza göre.

## <a name="get-the-source-code"></a>Kaynak kodunu alma
Bu tarifin kaynak kodunu örnekler deposunda [bulabilirsiniz.](https://github.com/VsixCommunity/Samples/tree/master/ToolWindow)
