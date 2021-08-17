---
title: Başlangıç Visual Studio Komutlarını Ekleme | Microsoft Docs
description: Visual Studio'de özel bir Başlangıç Sayfasındaki XAML nesnelerine komut bağlamanın farklı Visual Studio.
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
ms.openlocfilehash: 9ab2fc534b2ef986b15102667bd23e108ea4c69256fe64516b0df08595b1157c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403508"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Başlangıç Visual Studio komutlarını ekleme

Özel bir Başlangıç Sayfası 7.000.000 Visual Studio ekleyebilirsiniz. Bu belgede, bir Başlangıç Sayfasındaki XAML nesnelerine Visual Studio komutlarını bağlamanın farklı yolları ele alır.

XAML'de komutlar hakkında daha fazla bilgi için bkz. [Komuta genel bakış](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Komut well komutundan komut ekleme

Özel Başlangıç Sayfası Oluşturma [içinde oluşturulan Başlangıç Sayfası,](../extensibility/creating-a-custom-start-page.md) ve ad <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> alanlarını aşağıdaki gibi <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> ekledi.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Derlemeden Microsoft.VisualStudio.Shell için başka bir ad alanı *Microsoft.VisualStudio.Shell.Immutable.11.0.dll.* (Projenize bu derlemeye bir başvuru eklemeniz gerekir.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Diğer adı kullanarak denetimin özelliğini Visual Studio XAML denetimlerine bağlamak için `vscom:` <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> `vscom:VSCommands.ExecuteCommand` kullanabilirsiniz. Daha sonra <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> özelliğini, aşağıdaki örnekte gösterildiği gibi yürütülecek komutun adına göre ayarlayın.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> `x:`XAML şemasına başvuran diğer ad, tüm komutların başında gereklidir.

 özelliğinin değerini Komut `Command` penceresinden erişilebilen herhangi bir komuta **göre ayarlayın.** Kullanılabilir komutların listesi için bkz. [Visual Studio adları.](../ide/reference/visual-studio-command-aliases.md)

 Ekleme komutu ek bir parametre gerektiriyorsa, özelliğin değerine `CommandParameter` ekebilirsiniz. Aşağıdaki örnekte gösterildiği gibi parametreleri boşluk kullanarak komutlardan ayırabilirsiniz.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Komut well'den uzantıları çağırma
 Kayıtlı VSPackage'lardan komutları, diğer uygulama komutları için kullanılan söz dizimlerini kullanarak Visual Studio çağırabilirsiniz. Örneğin, yüklü bir VSPackage Görünüm  menüsüne bir  Giriş Sayfası komutu eklerse, komutunu olarak ayarerek bu komutu `CommandParameter` `View.HomePage` çağırabilirsiniz.

> [!NOTE]
> VSPackage ile ilişkili bir komutu çağırırsanız, komut çağrıldığında paketin yüklenmiş olması gerekir.

## <a name="add-commands-from-assemblies"></a>Derlemelerden komut ekleme
 Bir derlemeden komut çağırma veya bir menü komutuyla ilişkilendirilen bir VSPackage'daki koda erişmek için, derleme için bir diğer ad oluşturmanız ve ardından diğer adı çağırmalısınız.

### <a name="to-call-a-command-from-an-assembly"></a>Bir derlemeden komut çağırma

1. Çözümünüzde derlemeye bir başvuru ekleyin.

2. *StartPage.xaml* dosyasının en üstüne, aşağıdaki örnekte gösterildiği gibi derleme için bir ad alanı yönergesi ekleyin.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Aşağıdaki örnekte gösterildiği gibi bir XAML nesnesinin `Command` özelliğini ayarerek komutunu çağırma.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Derlemenizi kopyalayıp *. \\ Çağrılmadan Visual Studio emin olmak için {Visual Studio yükleme klasörü}\Common7\IDE\PrivateAssemblies. \*

## <a name="add-commands-with-the-dte-object"></a>DTE nesnesiyle komut ekleme
 DTE nesnesine hem işaretleme hem de kod ile bir Başlangıç Sayfasından erişebilirsiniz.

 İşaretlemede, nesnesine çağrı yapmak için Bağlama [İşaretleme Uzantısı söz](/dotnet/framework/wpf/advanced/binding-markup-extension) dizimi kullanarak <xref:EnvDTE.DTE> erişebilirsiniz. Bu yaklaşımı, koleksiyonlar gibi basit özelliklere bağlamak için kullanabilirsiniz, ancak yöntemlere veya hizmetlere bağlanamazsiniz. Aşağıdaki örnekte özelliğine bağlanan bir denetim ve özelliği tarafından döndürülen koleksiyonun özelliklerini listeleyen <xref:System.Windows.Controls.TextBlock> <xref:EnvDTE._DTE.Name%2A> bir denetim yer <xref:System.Windows.Controls.ListBox> <xref:EnvDTE.Window.Caption%2A> <xref:EnvDTE._DTE.Windows%2A> almaktadır.

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

 Bir örnek için [bkz. Adım adım: Kullanıcı ayarlarını Başlangıç Sayfasına kaydetme.](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)
