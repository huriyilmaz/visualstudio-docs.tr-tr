---
title: başlangıç sayfasına Visual Studio komutları ekleme | Microsoft Docs
description: Visual Studio komutları Visual Studio özel bir başlangıç sayfasında XAML nesnelerine bağlamak için farklı yollar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 9d63d7267002577f72a03980eceed0b857e13157
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051358"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>başlangıç sayfasına Visual Studio komutları ekleme

özel bir başlangıç sayfası oluşturduğunuzda buna Visual Studio komutlar ekleyebilirsiniz. bu belgede, Visual Studio komutları başlangıç sayfasındaki XAML nesnelerine bağlamak için farklı yollar açıklanmaktadır.

XAML komutları hakkında daha fazla bilgi için bkz. [komut verme genel bakış](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Komut kutusu 'ndan komutlar ekleyin

[Özel başlangıç sayfası oluştur](../extensibility/creating-a-custom-start-page.md) bölümünde oluşturulan başlangıç sayfası, <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> ve <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> ad alanlarını aşağıdaki şekilde ekledi.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Derlemeden Microsoft. VisualStudio. Shell için başka bir ad alanı ekleyin *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Projenizde bu derlemeye bir başvuru eklemeniz gerekebilir.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

`vscom:`denetimin özelliğini olarak ayarlayarak sayfadaki XAML denetimlerine Visual Studio komutlarını bağlamak için diğer adı kullanabilirsiniz <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> `vscom:VSCommands.ExecuteCommand` . Ardından, <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> Aşağıdaki örnekte gösterildiği gibi, özelliğini yürütülecek komutun adı olarak ayarlayabilirsiniz.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> `x:`Xaml şemasına başvuran diğer ad, tüm komutların başlangıcında gereklidir.

 `Command`Özelliğin değerini **komut** penceresinden erişilebilen herhangi bir komut olarak ayarlayabilirsiniz. kullanılabilir komutların listesi için bkz. [Visual Studio komutu diğer adları](../ide/reference/visual-studio-command-aliases.md).

 Eklenecek komut ek bir parametre gerektiriyorsa, özelliğin değerine ekleyebilirsiniz `CommandParameter` . Aşağıdaki örnekte gösterildiği gibi, boşluk kullanarak komutlardan parametreleri ayırın.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Komut kutusu 'ndan uzantıları çağırma
 diğer Visual Studio komutlarını çağırmak için kullanılan söz dizimini kullanarak kayıtlı vspackages 'tan komut çağırabilirsiniz. Örneğin, yüklü bir VSPackage, **Görünüm** menüsüne bir **giriş sayfası** komutu eklerse, bu komutu olarak ayarlayarak çağırabilirsiniz `CommandParameter` `View.HomePage` .

> [!NOTE]
> VSPackage ile ilişkili bir komut çağırırsanız, komut çağrıldığında paketin yüklenmesi gerekir.

## <a name="add-commands-from-assemblies"></a>Derlemelerden komut ekleyin
 Bir derlemeden bir komut çağırmak veya bir menü komutuyla ilişkilendirilmemiş VSPackage içindeki koda erişmek için, derleme için bir diğer ad oluşturmanız ve ardından diğer adı çağırmanız gerekir.

### <a name="to-call-a-command-from-an-assembly"></a>Derlemeden bir komut çağırmak için

1. Çözümünüzde derlemeye bir başvuru ekleyin.

2. Aşağıdaki örnekte gösterildiği gibi, *StartPage. xaml* dosyasının en üstünde, derleme için bir ad alanı yönergesi ekleyin.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. `Command`Aşağıdaki örnekte gösterildiği gibi BIR xaml nesnesinin özelliğini ayarlayarak komutunu çağırın.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Derlemenizi kopyalamanız ve sonra * \\ içine yapıştırmanız gerekir. {Visual Studio yükleme klasörü} \Common7\IDE\PrivateAssemblies \* çağrılmadan önce yüklendiğinden emin olmak için.

## <a name="add-commands-with-the-dte-object"></a>DTE nesnesi ile komutlar ekleme
 DTE nesnesine, her ikisi de biçimlendirme ve kod içinde bir başlangıç sayfasından erişebilirsiniz.

 Biçimlendirme ' de, nesneyi çağırmak için [bağlama Işaretleme uzantısı](/dotnet/framework/wpf/advanced/binding-markup-extension) sözdizimini kullanarak erişebilirsiniz <xref:EnvDTE.DTE> . Bu yaklaşımı, koleksiyonları döndüren Koleksiyonlar gibi basit özelliklere bağlamak için kullanabilirsiniz, ancak yöntemlere veya hizmetlere bağlayamazsınız. Aşağıdaki örnek, özelliğine bağlanan bir <xref:System.Windows.Controls.TextBlock> denetimi <xref:EnvDTE._DTE.Name%2A> ve <xref:System.Windows.Controls.ListBox> <xref:EnvDTE.Window.Caption%2A> özelliği tarafından döndürülen koleksiyonun özelliklerini numaralandırır <xref:EnvDTE._DTE.Windows%2A> .

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 Bir örnek için bkz. [Izlenecek yol: Kullanıcı ayarlarını bir başlangıç sayfasına kaydetme](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)
