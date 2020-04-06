---
title: WPF Araç Kutusu Denetimi Oluşturma | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739575"
---
# <a name="create-a-wpf-toolbox-control"></a>WPF Araç Kutusu Denetimi Oluşturma

WPF (Windows Presentation Framework) Araç Kutusu Denetimi şablonu, uzantı yüklendiğinde **Araç Kutusu'na** otomatik olarak eklenen WPF denetimleri oluşturmanıza olanak tanır. Bu izlik, şablonun diğer kullanıcılara dağıtabileceğiniz bir **Araç Kutusu** denetimi oluşturmak için nasıl kullanılacağını gösterir.

Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-toolbox-control"></a>Araç Kutusu Denetimini Oluşturma

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF Araç Kutusu Denetimi ile uzantı oluşturma

1. Adlı `MyToolboxControl`bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.

2. Proje açıldığında, **wpf araç kutusu denetim** öğesi `MyToolboxControl`şablonu ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Yeni **Öğe Ekle** iletişim kutusunda Visual **C#** > **Genişletilebilirlik'e** gidin ve **WPF Araç Kutusu Denetimi'ni**seçin. Pencerenin altındaki **Ad** alanında komut dosyası adını *MyToolboxControl.cs*olarak değiştirin.

    Çözüm artık `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> bir kullanıcı denetimi, bir araç **kutusuna**denetim ekleyen bir ve dağıtım için VSIX bildiriminde bir **Microsoft.VisualStudio.ToolboxControl** Asset girişi içerir.

#### <a name="to-create-the-control-ui"></a>Denetim UI'sini oluşturmak için

1. Açık *MyToolboxControl.xaml* tasarımcı.

    Tasarımcı, denetim <xref:System.Windows.Controls.Grid> içeren bir <xref:System.Windows.Controls.Button> denetim gösterir.

2. Izgara düzenini düzenleyin. <xref:System.Windows.Controls.Grid> Denetimi seçtiğinizde, ızgaranın üst ve sol kenarlarında mavi denetim çubukları görünür. Çubukları tıklatarak ızgaraya satır lar ve sütunlar ekleyebilirsiniz.

3. Kılavuza alt denetimler ekleyin. Bir alt denetimi **Araç Kutusu'ndan** ızgaranın bir bölümüne sürükleyerek veya `Grid.Row` XAML'de kendi ve `Grid.Column` özniteliklerini ayarlayarak konumlandırabilirsiniz. Aşağıdaki örnek, ızgaranın üst satırına iki etiket ve ikinci satıra bir düğme ekler.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Denetimi yeniden adlandırma

 Varsayılan olarak, denetiminiz **MyToolboxControl.MyToolboxControl**adlı bir grupta **MyToolboxControl** olarak **Toolbox** olarak görünür. Bu adları *MyToolboxControl.xaml.cs* dosyasında değiştirebilirsiniz.

1. Kod görünümünde *MyToolboxControl.xaml.cs* açın.

2. `MyToolboxControl` Sınıfı bulun ve TestDenetimi olarak yeniden adlandırın. (Bunu yapmanın en hızlı yolu sınıfı yeniden adlandırmak, ardından bağlam menüsünden **Yeniden Adlandır'ı** seçmek ve adımları tamamlamaktır. (Yeniden **adlandırma** komutu hakkında daha fazla bilgi için yeniden [adlandırma (C#)](../ide/reference/rename.md)başlığına bakın.)

3. Özniteliğe `ProvideToolboxControl` gidin ve ilk parametrenin değerini **Test**olarak değiştirin. Bu, **Araç Kutusu'ndaki**denetimi içerecek grubun adıdır.

    Ortaya çıkan kod aşağıdaki gibi görünmelidir:

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>Oluşturma, test ve dağıtım

 Projeyi hata ayıklama durumunda, denetimi Visual Studio'nun deneysel örneğinin **Araç Kutusu'nda** yüklü bulmalısınız.

### <a name="to-build-and-test-the-control"></a>Denetimi oluşturmak ve test etmek için

1. Projeyi yeniden oluştur ve hata ayıklamaya başlayın.

2. Visual Studio'nun yeni örneğinde bir WPF Uygulama projesi oluşturun. XAML Tasarımcısı'nın açık olduğundan emin olun.

3. Denetiminizi Araç **Kutusu'nda** bulun ve tasarım yüzeyine sürükleyin.

4. WPF uygulamasını hata ayıklamaya başlayın.

5. Denetiminizin görüntülenin.

### <a name="to-deploy-the-control"></a>Denetimi dağıtmak için

1. Sınanan projeyi yaptıktan sonra *.vsix* dosyasını projenin *\bin\debug\* klasöründe bulabilirsiniz.

2. *.vsix* dosyasını çift tıklayarak ve yükleme yordamını izleyerek yerel bir bilgisayara yükleyebilirsiniz. Denetimi kaldırmak için **Araçlar** > **Uzantıları ve Güncelleştirmeleri'ne** gidin ve denetim uzantısını arayın, ardından **Kaldır'ı**tıklatın.

3. *.vsix* dosyasını bir ağa veya bir Web sitesine yükleyin.

    Dosyayı Visual Studio [Marketplace](https://marketplace.visualstudio.com/) Web sitesine yüklerseniz, diğer kullanıcılar denetimi çevrimiçi olarak bulmak ve yüklemek için Visual Studio'daki **Araç** > **Uzantıları nı ve Güncellemelerini** kullanabilir.
