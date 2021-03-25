---
title: Özel başlangıç sayfası oluşturma | Microsoft Docs
description: Özel başlangıç sayfası oluşturmayı öğrenin. Boş bir başlangıç sayfasıyla başlayın, boş UserControl öğesine denetimler ekleyin ve ardından sayfanızı test edin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: f76451ca2a650283125cc7659d0053ef984115fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089387"
---
# <a name="creating-a-custom-start-page"></a>Özel başlangıç sayfası oluşturma

Bu belgedeki adımları izleyerek özel bir başlangıç sayfası oluşturabilirsiniz.

## <a name="create-a-blank-start-page"></a>Boş bir başlangıç sayfası oluştur

İlk olarak, Visual Studio 'Nun tanıyacağı bir etiket yapısına sahip bir *. xaml* dosyası oluşturarak boş bir başlangıç sayfası oluşturun. Ardından, istediğiniz görünüm ve işlevselliği oluşturmak için biçimlendirme ve arka plan kodu ekleyin.

1. **WPF uygulaması** türünde yeni bir proje oluşturun (**Visual C#**  >  **Windows Masaüstü**).

2. Öğesine bir başvuru ekleyin `Microsoft.VisualStudio.Shell.14.0` .

3. XML düzenleyicisinde XAML dosyasını açın ve en üst düzey \<Window> öğeyi bir \<UserControl> ad alanı bildiriminin hiçbirini kaldırmadan bir öğe olarak değiştirin.

4. `x:Class`Bildirimi en üst düzey öğeden kaldırın. Bu, XAML içeriğini başlangıç sayfasını barındıran Visual Studio araç penceresiyle uyumlu hale getirir.

5. Aşağıdaki ad alanı bildirimlerini en üst düzey \<UserControl> öğeye ekleyin.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Bu ad alanları, Visual Studio komutları, denetimleri ve Kullanıcı arabirimi ayarlarına erişmenizi sağlar. Daha fazla bilgi için bkz. [Başlangıç sayfasına Visual Studio komutları ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     Aşağıdaki örnekte, boş bir başlangıç sayfası için *. xaml* dosyasındaki biçimlendirme gösterilmektedir. Herhangi bir özel içerik iç öğe içine gitmelidir <xref:System.Windows.Controls.Grid> .

    ```vb
    <UserControl
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        xmlns:local="clr-namespace:StartPageHost"
        mc:Ignorable="d"
         Height="350" Width="525">
        <Grid>
        <!--Add content here.-->
        </Grid>
    </UserControl>
    ```

6. \<UserControl>Özel Başlangıç sayfanıza doldurulacak boş öğeye denetimler ekleyin. Visual Studio 'ya özgü işlevsellik ekleme hakkında daha fazla bilgi için, bkz. [Visual Studio komutlarını bir başlangıç sayfasına ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Özel başlangıç sayfasını test etme ve uygulama

Visual Studio 'nun kilitlenmediğinden emin olana kadar, Visual Studio 'nun birincil örneğini özel başlangıç sayfasını çalıştıracak şekilde ayarlamayın. Bunun yerine, deneysel örnekte test edin.

### <a name="to-test-a-manually-created-custom-start-page"></a>El ile oluşturulan özel başlangıç sayfasını test etmek için

1. XAML dosyanızı ve destekleyici metin dosyalarını veya biçimlendirme dosyalarını, *%USERPROFILE%\My SiteStudio 2015 \ StartPages \\* klasörüne kopyalayın.

2. Başlangıç sayfanız, Visual Studio tarafından yüklenmeyen derlemelerdeki denetimlere veya türlere başvuruyorsa, derlemeleri kopyalayın ve *{Visual Studio yükleme klasörü} \Common7\IDE\PrivateAssemblies \\* içine yapıştırın.

3. Visual Studio komut isteminde **devenv/rootsuffix exp** yazarak Visual Studio 'nun deneysel bir örneğini açın.

4. Deneysel örnekte, **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Başlangıç** sayfasına gidin ve **Başlangıç sayfasını Özelleştir** açılan menüsünden XAML dosyanızı seçin.

5. **Görünüm** menüsünde, **Başlangıç sayfası**' nı tıklatın.

     Özel başlangıç sayfanız görüntülenmelidir. Herhangi bir dosyayı değiştirmek istiyorsanız, deneysel örneği kapatmanız, değişiklikleri yapmanız, değiştirilen dosyaları kopyalayıp yapıştırmanız ve sonra değişiklikleri görüntülemek için deneysel örneği yeniden açmanız gerekir.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Özel başlangıç sayfasını Visual Studio 'nun birincil örneğine uygulamak için

- Başlangıç sayfanızı test ettikten ve kararlı olduğunu bulduktan sonra, **Seçenekler** Iletişim kutusundaki başlangıç sayfasını **Özelleştir** seçeneğini kullanarak Visual Studio 'nun birincil örneğindeki başlangıç sayfası olarak seçin

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: başlangıç sayfasına özel XAML ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Başlangıç sayfasına kullanıcı denetimi Ekle](../extensibility/adding-user-control-to-the-start-page.md)
- [Başlangıç sayfasına Visual Studio komutları ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [İzlenecek yol: bir başlangıç sayfasına kullanıcı ayarlarını kaydetme](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Özel başlangıç sayfalarını dağıtma](../extensibility/deploying-custom-start-pages.md)
