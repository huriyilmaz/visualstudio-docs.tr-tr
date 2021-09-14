---
title: WPF Araç Kutusu Denetim | Microsoft Docs
description: WPF Araç Kutusu Denetimi şablonunu kullanarak diğer kullanıcılara dağıtabilirsiniz bir Araç Kutusu denetimi oluşturma hakkında bilgi edinebilirsiniz.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6bf8dae61373b8a9ba5814930298896f3ba41da6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627693"
---
# <a name="create-a-wpf-toolbox-control"></a>WPF Araç Kutusu Denetimi Oluşturma

WPF (Windows Sunu Çerçevesi) Araç Kutusu Denetimi şablonu, uzantı yüklenirken Araç  Kutusuna otomatik olarak eklenen WPF denetimleri oluşturmanıza olanak sağlar. Bu kılavuz, şablonu kullanarak diğer kullanıcılara dağıtabilirsiniz bir **Araç** Kutusu denetimi oluşturma adımlarını gösterir.

2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-toolbox-control"></a>Araç Kutusu Denetimi Oluşturma

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF Araç Kutusu Denetimi ile uzantı oluşturma

1. adlı bir VSIX projesi `MyToolboxControl` oluşturun. VSIX proje şablonunu New **Project** "vsix" arayarak bulabilirsiniz.

2. Proje açıldığında adlı bir **WPF Araç Kutusu Denetimi** öğesi şablonu `MyToolboxControl` ekleyin. Yeni **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Yeni Öğe **Ekle iletişim kutusunda** Visual **C#** Genişletilebilirliği'ne gidin  >  **ve** WPF Araç Kutusu **Denetimi'ne tıklayın.** Pencerenin **en** altındaki Ad alanında, komut dosyası adını *MyToolboxControl.cs olarak değiştirebilirsiniz.*

    Çözüm artık bir kullanıcı denetimi, denetimi Araç Kutusuna ekleyen bir ve dağıtım için VSIX bildiriminde `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> **bir Microsoft.VisualStudio.ToolboxControl** Varlık girdisi içeriyor. 

#### <a name="to-create-the-control-ui"></a>Denetim kullanıcı arabirimini oluşturmak için

1. Tasarımcıda *MyToolboxControl.xaml'i* açın.

    Tasarımcı, denetim <xref:System.Windows.Controls.Grid> içeren bir denetim <xref:System.Windows.Controls.Button> gösterir.

2. Kılavuz düzenini düzenleme. Denetimi seçerek <xref:System.Windows.Controls.Grid> kılavuzun üst ve sol kenarlarında mavi denetim çubukları görünür. Çubuklara tıklayarak kılavuza satır ve sütun ekleyebilirsiniz.

3. Kılavuza alt denetimler ekleyin. Alt denetimi araç kutusundan kılavuzun  bir bölümüne sürükleyerek veya XAML'de ve özniteliklerini ayarerek `Grid.Row` `Grid.Column` konumlarını değiştirebilirsiniz. Aşağıdaki örnek, kılavuzun üst satırına iki etiket ve ikinci satıra bir düğme ekler.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>Denetimi yeniden yeniden

 Varsayılan olarak, denetiminiz Araç  Kutusunda **MyToolboxControl.MyToolboxControl** adlı bir grupta **MyToolboxControl olarak görünür.** Bu adları *MyToolboxControl.xaml.cs dosyasında değiştirebilirsiniz.*

1. Kod *görünümünde MyToolboxControl.xaml.cs'yi* açın.

2. sınıfını `MyToolboxControl` bulun ve TestControl olarak yeniden adlandırin. (Bunu yapmak için en hızlı yol sınıfını yeniden adlandırmak, ardından bağlam **menüsünden Yeniden** Adlandır'ı seçmek ve adımları tamamlamaktır. (Yeniden adlandır komutu hakkında daha **fazla bilgi** için [bkz. Yeniden düzenlemeyi yeniden adlandırma (C#) .)](../ide/reference/rename.md)

3. özniteliğine `ProvideToolboxControl` gidin ve ilk parametrenin değerini Test olarak **değiştirin.** Bu, Araç Kutusu'nda denetimi içeren grubun **adıdır.**

    Sonuçta elde edilen kod aşağıdaki gibi görünüyor olabilir:

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

 Projede hata ayıklarken, deneysel Visual Studio örneğinin **Araç** Kutusunda yüklü denetimi bulmalı Visual Studio.

### <a name="to-build-and-test-the-control"></a>Denetimi derlemek ve test etmek için

1. Projeyi yeniden oluşturma ve hata ayıklamayı başlatma.

2. Yeni Visual Studio WPF Uygulaması projesi oluşturun. Dosyanın açık XAML Tasarımcısı emin olun.

3. Araç Kutusunda **denetiminizi bulun ve** tasarım yüzeyine sürükleyin.

4. WPF uygulamasında hata ayıklamaya başlama.

5. Denetiminizin görüntülendiğinden emin olur.

### <a name="to-deploy-the-control"></a>Denetimi dağıtmak için

1. Test edilen projeyi derlemenin ardından *.vsix* dosyasını projenin *\bin\debug \* klasöründe bulabilirsiniz.

2. *.vsix* dosyasına çift tıklar ve yükleme yordamını takip edin, yerel bir bilgisayara yükleyebilirsiniz. Denetimi kaldırmak için Araçlar Uzantıları **ve**  >  **Güncelleştirmeler'e** gidin, denetim uzantısını seçin ve Kaldır'a **tıklayın.**

3. Upload *.vsix* dosyasını bir ağa veya bir Web sitesine kaydedin.

    Dosyayı Visual Studio [Market](https://marketplace.visualstudio.com/) Web sitesine yüklersiniz, diğer kullanıcılar denetimi çevrimiçi bulup yüklemek için Visual Studio'deki Araç Uzantıları ve  >   Güncelleştirmeler'i kullanabilir.
