---
title: Özel Başlangıç Sayfası Oluşturma | Microsoft Docs
description: Özel başlangıç sayfası oluşturma hakkında bilgi edinebilirsiniz. Boş bir başlangıç sayfasıyla başlama, boş UserControl öğesine denetimler ekleme ve ardından sayfanızı test edin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 34e8f64b0007231ef3c5208d7020d415d65e6d67
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073545"
---
# <a name="creating-a-custom-start-page"></a>Özel Başlangıç Sayfası oluşturma

Bu belgede yer alan adımları kullanarak özel bir Başlangıç Sayfası oluşturabilirsiniz.

## <a name="create-a-blank-start-page"></a>Boş bir Başlangıç Sayfası oluşturma

İlk olarak, tanıyacak etiket yapısına sahip *bir .xaml* dosyası oluşturarak Visual Studio olun. Ardından istediğiniz görünümü ve işlevi üretmek için işaretleme ve arka kod ekleyin.

1. **WPF** Uygulaması türünde yeni bir proje oluşturun (**Visual C#**  >  **Windows Desktop**).

2. için bir başvuru `Microsoft.VisualStudio.Shell.14.0` ekleyin.

3. XAML dosyasını XML düzenleyicisinde açın ve ad alanı bildirimlerini kaldırmadan en üst düzey öğeyi \<Window> \<UserControl> bir öğe olarak değiştirebilirsiniz.

4. Bildirimi `x:Class` üst düzey öğesinden kaldırın. Bu, XAML içeriğini Başlangıç Sayfasını barındıran Visual Studio aracı penceresiyle uyumlu yapar.

5. Aşağıdaki ad alanı bildirimlerini üst düzey öğesine \<UserControl> ekleyin.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Bu ad alanları, kullanıcı arabirimi Visual Studio, denetimlere ve kullanıcı arabirimi ayarlarına erişmeye izin verir. Daha fazla bilgi için [bkz. Başlangıç Visual Studio komutlarını ekleme.](../extensibility/adding-visual-studio-commands-to-a-start-page.md)

     Aşağıdaki örnek boş bir Başlangıç Sayfası için *.xaml* dosyasındaki işaretlemeyi gösterir. Tüm özel içerikler iç öğeye <xref:System.Windows.Controls.Grid> gitli.

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

6. Özel Başlangıç Sayfanızı \<UserControl> doldurmak için boş öğeye denetimler ekleyin. Uygulamanıza özel işlevler ekleme hakkında bilgi için Visual Studio, [bkz. Başlangıç Visual Studio komutlarını ekleme.](../extensibility/adding-visual-studio-commands-to-a-start-page.md)

## <a name="test-and-apply-the-custom-start-page"></a>Özel Başlangıç Sayfasını test edin ve uygulama

Özel Başlangıç Sayfası'nın Visual Studio çalışmayıncaya kadar özel başlangıç sayfasının birincil örneğini ayarlayıncaya kadar Visual Studio. Bunun yerine, deneysel örnekte test etmek.

### <a name="to-test-a-manually-created-custom-start-page"></a>El ile oluşturulan özel Başlangıç Sayfasını test etmek için

1. XAML dosyanızı ve tüm desteklenen metin dosyalarını veya işaretleme dosyalarını *%USERPROFILE%\Belgelerim\Visual Studio 2015\StartPages klasörüne \\* kopyalayın.

2. Başlangıç sayfanız Visual Studio tarafından yüklenmemiş derlemelerde herhangi bir denetime veya türe başvurursa, derlemeleri kopyalayın ve *ardından {Visual Studio yükleme klasörü}\Common7\IDE\PrivateAssemblies \\* dizinine yapıştırın.

3. Bir Visual Studio komut isteminde, deneysel bir örnek açmak için **devenv /rootsuffix Exp** Visual Studio.

4. Deneysel örnekte Araçlar Seçenekleri Ortam Başlatma **sayfasına** gidin ve Başlangıç Sayfasını Özelleştir açılan  >    >    >   menüsünden XAML **dosyanızı** seçin.

5. Görünüm menüsünde **Başlangıç** **Sayfası'nın üzerine tıklayın.**

     Özel başlangıç sayfanız görüntüleniyor. Herhangi bir dosyayı değiştirmek için deneysel örneği kapatmanız, değişiklikleri yapmanız, değiştirilen dosyaları kopyalayıp yapıştırmanız ve ardından deneysel örneği yeniden açıp değişiklikleri görüntülemeniz gerekir.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Özel başlangıç sayfasını uygulamanın birincil örneğine Visual Studio

- Başlangıç Sayfanızı test ettikten ve kararlı olduğunu  buladikten sonra  Seçenekler iletişim kutusundaki Başlangıç Sayfasını Özelleştir seçeneğini kullanarak sayfanın birincil örneğinde başlangıç sayfası olarak Visual Studio

## <a name="see-also"></a>Ayrıca bkz.

- [Adım adım kılavuz: Başlangıç Sayfasına özel XAML ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Başlangıç Sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)
- [Başlangıç Visual Studio komutlarını ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Adım adım kılavuz: Kullanıcı ayarlarını Başlangıç Sayfasına kaydetme](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Özel Başlangıç Sayfaları dağıtma](../extensibility/deploying-custom-start-pages.md)
