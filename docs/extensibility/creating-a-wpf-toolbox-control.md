---
title: WPF araç kutusu denetimi oluşturma | Microsoft Docs
description: Diğer kullanıcılara dağıtabileceğiniz bir araç kutusu denetimi oluşturmak için WPF araç kutusu denetim şablonunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1dccdeb09a938b3b0bbbab803faeed538001b825
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089257"
---
# <a name="create-a-wpf-toolbox-control"></a>WPF araç kutusu denetimi oluşturma

WPF (Windows Presentation Framework) araç kutusu denetim şablonu, uzantı yüklendiğinde **araç kutusuna** otomatik olarak eklenen WPF denetimleri oluşturmanızı sağlar. Bu izlenecek yolda, diğer kullanıcılara dağıtabileceğiniz bir **araç kutusu** denetimi oluşturmak için şablonunun nasıl kullanılacağı gösterilmektedir.

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Araç kutusu denetimini oluşturma

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF araç kutusu denetimiyle uzantı oluşturma

1. Adlı bir VSıX projesi oluşturun `MyToolboxControl` . "VSIX" araması yaparak VSıX proje şablonunu **Yeni proje** iletişim kutusunda bulabilirsiniz.

2. Proje açıldığında, adlı bir **WPF araç kutusu denetim** öğesi şablonu ekleyin `MyToolboxControl` . **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **WPF araç kutusu denetimi**' ni seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *MyToolboxControl. cs* olarak değiştirin.

    Çözüm artık, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> denetimi **araç kutusuna** ekleyen bir Kullanıcı denetımı ve dağıtım Için VSIX bildiriminde bir **Microsoft. VisualStudio. ToolboxControl** varlık girişi içerir.

#### <a name="to-create-the-control-ui"></a>Denetim Kullanıcı arabirimini oluşturmak için

1. Tasarımcıda *MyToolboxControl. xaml* ' i açın.

    Tasarımcı, <xref:System.Windows.Controls.Grid> Denetim içeren bir denetimi gösterir <xref:System.Windows.Controls.Button> .

2. Kılavuz yerleşimini düzenleyin. <xref:System.Windows.Controls.Grid>Denetimi seçtiğinizde, kılavuzun üst ve sol kenarlarındaki mavi denetim çubukları görüntülenir. Çubuklara tıklayarak kılavuza satır ve sütun ekleyebilirsiniz.

3. Kılavuza alt denetimler ekleyin. Bir alt denetimi **araç kutusundan** kılavuz bölümüne sürükleyerek veya `Grid.Row` `Grid.Column` xaml içindeki ve özniteliklerini ayarlayarak yerleştirebilirsiniz. Aşağıdaki örnek, kılavuzun en üst satırına ve ikinci satırdaki bir düğmeye iki etiket ekler.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Denetimi yeniden adlandırma

 Varsayılan olarak, denetiminiz **araç kutusunda** **MyToolboxControl. MyToolboxControl** adlı bir grupta **MyToolboxControl** olarak görünür. *MyToolboxControl. xaml. cs* dosyasındaki bu adları değiştirebilirsiniz.

1. Kod görünümünde *MyToolboxControl. xaml. cs* ' i açın.

2. Sınıfını bulun `MyToolboxControl` ve TestControl olarak yeniden adlandırın. (Bunu yapmanın en hızlı yolu, sınıfı yeniden adlandırmanız ve bağlam menüsünden **Yeniden Adlandır** ' ı seçip adımları tamamlamayın. ( **Yeniden adlandırma** komutu hakkında daha fazla bilgi için bkz. [yeniden düzenlemeyi yeniden adlandırma (C#)](../ide/reference/rename.md).)

3. `ProvideToolboxControl`Özniteliğine gidin ve **Test** olarak ilk parametrenin değerini değiştirin. Bu, **araç kutusunda** denetimi içerecek olan grubun adıdır.

    Elde edilen kod şöyle görünmelidir:

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

## <a name="build-test-and-deployment"></a>Derleme, test ve dağıtım

 Projede hata ayıklarken, Visual Studio 'nun deneysel örneğinin **araç kutusunda** yüklü olan denetimi bulmanız gerekir.

### <a name="to-build-and-test-the-control"></a>Denetimi derlemek ve test etmek için

1. Projeyi yeniden derleyin ve hata ayıklamayı başlatın.

2. Visual Studio 'nun yeni örneğinde bir WPF uygulama projesi oluşturun. XAML Tasarımcısı açık olduğundan emin olun.

3. **Araç kutusu** 'nda denetiminizi bulun ve tasarım yüzeyine sürükleyin.

4. WPF uygulamasında hata ayıklamayı başlatın.

5. Denetiminizin göründüğünü doğrulayın.

### <a name="to-deploy-the-control"></a>Denetimi dağıtmak için

1. Test edilen Projeyi derledikten sonra, *. vsix* dosyasını projenin * \bin\Debug \* klasöründe bulabilirsiniz.

2. Bunu, *. vsix* dosyasına çift tıklayarak ve yükleme yordamını izleyerek yerel bir bilgisayara yükleyebilirsiniz. Denetimi kaldırmak için **Araçlar**  >  **Uzantılar ve güncelleştirmeler** ' e gidin ve denetim uzantısını bulup **Kaldır**' a tıklayın.

3. *. Vsix* dosyasını bir ağa veya bir Web sitesine yükleyin.

    Dosyayı [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesine yüklerseniz, diğer kullanıcılar   >  denetimi çevrimiçi bulmak ve yüklemek için Visual Studio 'daki Araçlar **uzantılarını ve güncelleştirmeleri** kullanabilir.
