---
title: Başlangıç Sayfasına Görsel Stüdyo Komutları Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740117"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Başlangıç Sayfasına Visual Studio komutları ekleme

Özel bir Başlangıç Sayfası oluşturduğunuzda, sayfaya Visual Studio komutları ekleyebilirsiniz. Bu belge, Visual Studio komutlarını Başlangıç Sayfasındaki XAML nesnelerine bağlamanın farklı yollarını tartışır.

XAML'deki komutlar hakkında daha fazla bilgi için [bkz.](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Komut iyi komutları ekleme

Özel bir Başlangıç Sayfası Oluştur'da <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> oluşturulan <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> Başlangıç [Sayfası,](../extensibility/creating-a-custom-start-page.md) aşağıdaki gibi ad alanlarını ve ad boşluklarını ekledi.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Microsoft.VisualStudio.Shell için başka bir ad alanı ekleyin derleme *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Projenizde bu derlemeye bir başvuru eklemeniz gerekebilir.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Visual Studio `vscom:` komutlarını sayfadaki XAML denetimlerine bağlamak için diğer adı, denetimin <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> `vscom:VSCommands.ExecuteCommand`özelliğini .'e ayarlayarak kullanabilirsiniz. Daha sonra aşağıdaki <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> örnekte gösterildiği gibi, yürütmekomutu adına özelliği ayarlayabilirsiniz.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> XAML şemasına atıfta bulunan `x:` diğer ad, tüm komutların başında gereklidir.

 `Command` Özelliğin değerini **Komut** penceresinden erişilebilen herhangi bir komuta ayarlayabilirsiniz. Kullanılabilir komutların listesi için [Visual Studio komut diğer adlarına](../ide/reference/visual-studio-command-aliases.md)bakın.

 Eklenecek komut ek bir parametre gerektiriyorsa, bunu `CommandParameter` özelliğin değerine ekleyebilirsiniz. Aşağıdaki örnekte gösterildiği gibi, boşlukları kullanarak komutlardan parametreleri ayırın.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Komut kuyusu uzantılarını arayın
 Diğer Visual Studio komutlarını aramak için kullanılan aynı sözdizimini kullanarak kayıtlı VSPackages'ten komutları arayabilirsiniz. Örneğin, yüklü bir VSPackage **Görünüm** menüsüne Bir **Giriş Sayfası** komutu eklerse, `CommandParameter` `View.HomePage`bu komutu .

> [!NOTE]
> VSPackage ile ilişkili bir komut çağırırsanız, komut çağrıldığınızda paketin yüklenmesi gerekir.

## <a name="add-commands-from-assemblies"></a>Derlemelerden komut ekleme
 Bir derlemeden komut çağırmak veya bir menü komutuyla ilişkili olmayan vspackage'daki koda erişmek için derleme için bir takma ad oluşturmanız ve ardından takma adı aramanız gerekir.

### <a name="to-call-a-command-from-an-assembly"></a>Derlemeden komut çağırmak için

1. Çözümünüzde, derlemeye bir başvuru ekleyin.

2. *StartPage.xaml* dosyasının üst kısmında, aşağıdaki örnekte gösterildiği gibi derleme için bir ad alanı yönergesi ekleyin.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Aşağıdaki örnekte gösterildiği `Command` gibi, bir XAML nesnesinin özelliğini ayarlayarak komutu çağırın.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Derlemenizi kopyalayıp sonra *...'a yapıştırmalısınız. \\{Visual Studio yükleme klasörü}\Common7\IDE\PrivateAssemblies\* çağrılmadan önce yüklendiğinden emin olmak için.

## <a name="add-commands-with-the-dte-object"></a>DTE nesnesi ile komut ekleme
 DTE nesnesi'ne hem biçimlendirme hem de kod olarak bir Başlangıç Sayfasından erişebilirsiniz.

 Biçimlendirmede, nesneyi aramak için [Bağlayıcı Biçimlendirme Uzantısı](/dotnet/framework/wpf/advanced/binding-markup-extension) sözdizimini kullanarak bu nesneye erişebilirsiniz. <xref:EnvDTE.DTE> Bu yaklaşımı, koleksiyonları döndüren ler gibi basit özelliklere bağlamak için kullanabilirsiniz, ancak yöntemlere veya hizmetlere bağlayamazsınız. Aşağıdaki örnek, <xref:System.Windows.Controls.TextBlock> <xref:EnvDTE._DTE.Name%2A> özelliğe bağlanan bir denetim ve <xref:System.Windows.Controls.ListBox> <xref:EnvDTE._DTE.Windows%2A> özellik tarafından döndürülen <xref:EnvDTE.Window.Caption%2A> koleksiyonun özelliklerini gösteren bir denetim gösterir.

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

 Örneğin, [Bkz. Walkthrough: Başlangıç Sayfasında kullanıcı ayarlarını kaydetme](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)
