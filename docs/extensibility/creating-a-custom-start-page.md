---
title: Özel Başlangıç Sayfası Oluşturma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739637"
---
# <a name="creating-a-custom-start-page"></a>Özel Bir Başlangıç Sayfası Oluşturma

Bu belgedeki adımları izleyerek özel bir Başlangıç Sayfası oluşturabilirsiniz.

## <a name="create-a-blank-start-page"></a>Boş bir Başlangıç Sayfası Oluşturma

İlk olarak, Visual Studio'nun tanıyacağı bir etiket yapısına sahip bir *.xaml* dosyası oluşturarak boş bir Başlangıç Sayfası yapın. Ardından, istediğiniz görünümü ve işlevselliği oluşturmak için biçimlendirme ve kod arkası ekleyin.

1. **WPF Uygulaması** türünden yeni bir proje oluşturun (**Visual C#** > **Windows Desktop**).

2. Bir başvuru `Microsoft.VisualStudio.Shell.14.0`ekleyin.

3. XML düzenleyicisinde XAML dosyasını açın ve \<ad alanı bildirimlerinden hiçbirini kaldırmadan üst düzey Pencere> öğesini \<UserControl> öğesi olarak değiştirin.

4. Bildirgeyi `x:Class` üst düzey öğeden kaldırın. Bu, XAML içeriğini Başlangıç Sayfasını barındıran Visual Studio araç penceresiile uyumlu hale getirir.

5. Üst düzey \<UserControl> öğesine aşağıdaki ad alanı bildirimleri ekleyin.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Bu ad alanları Visual Studio komutlarına, denetimlerine ve Kullanıcı Arabirimi ayarlarına erişmenizi sağlar. Daha fazla bilgi için, [Başlangıç Sayfasına Görsel Stüdyo Ekle komutlarına](../extensibility/adding-visual-studio-commands-to-a-start-page.md)bakın.

     Aşağıdaki örnekte, boş bir Başlangıç Sayfası için *.xaml* dosyasındaki biçimlendirme gösterilmektedir. Herhangi bir özel içerik <xref:System.Windows.Controls.Grid> iç öğeye gitmeli.

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

6. Özel Başlangıç Sayfanızı doldurmak için boş \<UserControl> öğesine denetimler ekleyin. Visual Studio'ya özgü işlevsellik ekleme hakkında bilgi için, [Başlangıç Sayfasına Görsel Stüdyo Ekle komutlarına](../extensibility/adding-visual-studio-commands-to-a-start-page.md)bakın.

## <a name="test-and-apply-the-custom-start-page"></a>Özel Başlangıç Sayfasını test edin ve uygulayın

Visual Studio'nun çökmediğini doğrulayana kadar Visual Studio'nun birincil örneğini özel Başlangıç Sayfasını çalıştıracak şekilde ayarlamayın. Bunun yerine, deneysel örnekte test edin.

### <a name="to-test-a-manually-created-custom-start-page"></a>El ile oluşturulmuş özel Başlangıç Sayfasını test etmek için

1. XAML dosyanızı ve desteklenen metin dosyalarını veya işaretleme dosyalarını *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\ * klasörüne kopyalayın.

2. Başlangıç sayfanız Visual Studio tarafından yüklenmeyen derlemelerde herhangi bir denetime veya türe başvuruyorsa, derlemeleri kopyalayın ve *{Visual\\Studio yükleme klasörüne yapıştırın}\Common7\IDE\PrivateAssemblies*.

3. Visual Studio komut isteminde Visual Studio'nun deneysel bir örneğini açmak için **devenv /rootsuffix Exp** yazın.

4. Deneysel durumda, **Araçlar** > **Seçenekleri** > **Ortamı** > **Başlatma** sayfasına gidin ve Başlat Sayfa açılır bırakarak **XAML** dosyanızı seçin.

5. **Görünüm** menüsünde, **Başlat Sayfasını**tıklatın.

     Özel başlangıç sayfanız görüntülenmelidir. Herhangi bir dosyayı değiştirmek istiyorsanız, deneme örneğini kapatmanız, değişiklikleri yapmanız, değiştirilen dosyaları kopyalamanız ve yapıştırmamanız ve değişiklikleri görüntülemek için deneme örneğini yeniden açmanız gerekir.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Visual Studio'nun birincil örneğinde özel başlangıç sayfasını uygulamak için

- Başlangıç Sayfanızı test ettikten ve kararlı bulduktan sonra, Visual Studio'nun birincil örneğinde başlangıç sayfası olarak seçmek için **Seçenekler** iletişim kutusundaki **Başlat Sayfasını Özelleştir** seçeneğini kullanın

## <a name="see-also"></a>Ayrıca bkz.

- [Walkthrough: Başlangıç Sayfasına özel XAML ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Başlangıç Sayfasına kullanıcı denetimi ekleme](../extensibility/adding-user-control-to-the-start-page.md)
- [Başlangıç Sayfasına Visual Studio komutları ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Walkthrough: Başlangıç Sayfasında kullanıcı ayarlarını kaydetme](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Özel Başlangıç Sayfalarını Dağıtma](../extensibility/deploying-custom-start-pages.md)
