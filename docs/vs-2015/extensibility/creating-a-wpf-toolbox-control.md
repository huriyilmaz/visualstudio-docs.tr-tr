---
title: WPF araç kutusu denetimi oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 768d9747635f2106d16f755db6799e356c890838
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197442"
---
# <a name="creating-a-wpf-toolbox-control"></a>WPF Araç Kutusu Denetimi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WPF (Windows Presentation Framework) araç kutusu denetim şablonu, uzantı yüklendiğinde **araç kutusuna** otomatik olarak eklenen WPF denetimleri oluşturmanızı sağlar. Bu konu başlığı altında, diğer kullanıcılara dağıtabileceğiniz bir **araç kutusu** denetimi oluşturmak için şablonunun nasıl kullanılacağı gösterilmektedir.  
  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>WPF Araç Kutusu Denetimi Oluşturma  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF araç kutusu denetimiyle uzantı oluşturma  
  
1. Adlı bir VSıX projesi oluşturun `MyToolboxControl` . VSıX proje şablonunu, **Visual C#/genişletilebilirlik**altında **Yeni proje** iletişim kutusunda bulabilirsiniz.  
  
2. Proje açıldığında, adlı bir **WPF araç kutusu denetim** öğesi şablonu ekleyin `MyToolboxControl` . **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. **Yeni öğe Ekle** Iletişim kutusunda **Visual C#/genişletilebilirlik** ' e gidin ve **WPF araç kutusu denetimi**' ni seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını olarak değiştirin `MyToolboxControl.cs` .  
  
     Çözüm artık, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> denetimi **araç kutusuna**ekleyen bir Kullanıcı denetımı ve dağıtım Için VSIX bildiriminde bir **Microsoft. VisualStudio. ToolboxControl** varlık girişi içerir.  
  
#### <a name="to-create-the-control-ui"></a>Denetim Kullanıcı arabirimini oluşturmak için  
  
1. Tasarımcıda MyToolboxControl. xaml ' i açın.  
  
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
 Varsayılan olarak, denetiminiz **araç kutusunda** **MyToolboxControl. MyToolboxControl**adlı bir grupta **MyToolboxControl** olarak görünür. MyToolboxControl.xaml.cs dosyasında bu adları değiştirebilirsiniz.  
  
1. Kod görünümünde MyToolboxControl.xaml.cs öğesini açın.  
  
2. MyToolboxControl sınıfını bulun ve TestControl olarak yeniden adlandırın. (Bunu yapmanın en hızlı yolu, sınıfı yeniden adlandırmanız ve bağlam menüsünden **Yeniden Adlandır** ' ı seçip adımları tamamlamayın. ( **Yeniden adlandırma** komutu hakkında daha fazla bilgi için bkz. [yeniden düzenlemeyi yeniden adlandırma (C#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3. `ProvideToolboxControl`Özniteliğine gidin ve **Test**olarak ilk parametrenin değerini değiştirin. Bu, **araç kutusunda**denetimi içerecek olan grubun adıdır.  
  
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
  
## <a name="building-testing-and-deployment"></a>Oluşturma, test etme ve dağıtma  
 Projede hata ayıklarken, Visual Studio 'nun deneysel örneğinin **araç kutusunda** yüklü olan denetimi bulmanız gerekir.  
  
#### <a name="to-build-and-test-the-control"></a>Denetimi derlemek ve test etmek için  
  
1. Projeyi yeniden derleyin ve hata ayıklamayı başlatın.  
  
2. Visual Studio 'nun yeni örneğinde bir WPF uygulama projesi oluşturun. XAML Tasarımcısı açık olduğundan emin olun.  
  
3. **Araç kutusu** 'nda denetiminizi bulun ve tasarım yüzeyine sürükleyin.  
  
4. WPF uygulamasında hata ayıklamayı başlatın.  
  
5. Denetiminizin göründüğünü doğrulayın.  
  
#### <a name="to-deploy-the-control"></a>Denetimi dağıtmak için  
  
1. Test edilen projeyi oluşturduktan sonra,. vsix dosyasını projenin \bin\debug\ klasöründe bulabilirsiniz.  
  
2. Bunu,. vsix dosyasına çift tıklayarak ve yükleme yordamını izleyerek yerel bir bilgisayara yükleyebilirsiniz. Denetimi kaldırmak için **Araçlar/Uzantılar ve güncelleştirmeler** ' e gidin ve denetim uzantısını bulup **Kaldır**' a tıklayın.  
  
3. . Vsix dosyasını bir ağa veya bir Web sitesine yükleyin.  
  
     Dosyayı [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesine yüklerseniz, diğer kullanıcılar denetimi çevrimiçi bulmak ve yüklemek Için Visual Studio 'daki **Araçları/uzantıları ve güncelleştirmeleri** kullanabilir.
