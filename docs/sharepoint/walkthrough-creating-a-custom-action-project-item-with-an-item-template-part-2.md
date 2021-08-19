---
title: Öğe şablonu, Bölüm 2 ile özel eylem proje öğesi oluşturma
titleSuffix: ''
description: bu kılavuzda, bir SharePoint sitesine özel bir eylem proje öğesi eklemek için bir öğe şablonu kullandıklarında kullanıcılardan bilgi toplamak için bir sihirbaz ekleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 21dc546890bf8e7e75a32c8b00246bec915098bc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083992"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>İzlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma
  SharePoint proje öğesi özel bir türünü tanımladıktan ve Visual Studio bir öğe şablonuyla ilişkilendirdikten sonra, şablon için bir sihirbaz sağlamak da isteyebilirsiniz. Bir projeye proje öğesinin yeni bir örneğini eklemek için şablonunuzu kullandıklarında kullanıcılardan bilgi toplamak için Sihirbazı kullanabilirsiniz. Topladığınız bilgiler Proje öğesini başlatmak için kullanılabilir.

 Bu kılavuzda, özel eylem proje öğesine [Izlenecek yol: bir öğe şablonuyla bir özel eylem proje öğesi oluşturun, 1. Bölüm](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)olarak bir sihirbaz ekleyeceksiniz. bir kullanıcı bir SharePoint projesine özel bir eylem proje öğesi eklediğinde, sihirbaz özel eylem (örneğin, konumu ve bir son kullanıcı seçtiğinde gidilecek URL) hakkında bilgi toplar ve bu bilgileri yeni proje öğesinde *Elements.xml* dosyasına ekler.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- bir öğe şablonuyla ilişkili özel SharePoint proje öğesi türü için sihirbaz oluşturma.

- Visual Studio SharePoint proje öğeleri için yerleşik sihirbazlara benzer bir özel sihirbaz kullanıcı arabirimi tanımlama.

- SharePoint proje dosyalarını sihirbazda topladığınız verilerle başlatmak için değiştirilebilen parametreleri kullanma.

- Hata ayıklama ve Sihirbazı test etme.

> [!NOTE]
> Bir iş akışı için nasıl özel etkinlik oluşturulacağını gösteren [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 'dan bir örnek indirebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Bu yönergeyi gerçekleştirmek için, önce [Izlenecek yol: bir öğe şablonuyla bir özel eylem proje öğesi oluşturun, 1. Bölüm ' i](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)tamamlayarak CustomActionProjectItem çözümünü oluşturmanız gerekir.

 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere de ihtiyacınız vardır:

- Windows, SharePoint ve Visual Studio desteklenen sürümleri.

- Visual Studio SDK. bu izlenecek yol SDK 'daki **vsıx Project** şablonunu, proje öğesini dağıtmak için bir vsıx paketi oluşturmak için kullanır. daha fazla bilgi için bkz. [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- Visual Studio içindeki proje ve öğe şablonları için sihirbazlar. daha fazla bilgi için bkz. [nasıl yapılır: sihirbazları Project şablonları](../extensibility/how-to-use-wizards-with-project-templates.md) ve arabirimiyle kullanma <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

- SharePoint özel eylemler. Daha fazla bilgi için bkz. [özel eylem](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Sihirbaz projesi oluşturma
 Bu izlenecek yolu tamamlamak için, [Izlenecek yol: bir öğe şablonuyla bir özel eylem proje öğesi oluşturma, 1. Bölüm](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)olarak bir proje eklemeniz gerekir. <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>Bu projede arabirimini uygular ve sihirbaz kullanıcı arabirimini tanımlayacaksınız.

#### <a name="to-create-the-wizard-project"></a>Sihirbaz projesi oluşturmak için

1. Visual Studio, CustomActionProjectItem çözümünü açın

2. **Çözüm Gezgini**, çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **yeni Project**' ı seçin.

3. **yeni Project** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve ardından **Windows** düğümünü seçin.

4. **yeni Project** iletişim kutusunun üst kısmında .NET Framework sürümleri listesinde **.NET Framework 4,5** ' nin seçildiğinden emin olun.

5. **WPF Kullanıcı denetimi kitaplığı** proje şablonu ' nu seçin, projenin **ItemTemplateWizard**' ı adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözümdeki **ItemTemplateWizard** projesini ekler.

6. Projedeki UserControl1 öğesini silin.

## <a name="configure-the-wizard-project"></a>Sihirbaz projesini yapılandırma
 sihirbazı oluşturmadan önce, projeye bir Windows Presentation Foundation (WPF) penceresi, bir kod dosyası ve derleme başvuruları eklemeniz gerekir.

#### <a name="to-configure-the-wizard-project"></a>Sihirbaz projesini yapılandırmak için

1. **Çözüm Gezgini**' de, **ItemTemplateWizard** proje düğümünden kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. **Project tasarımcısında**, hedef framework 'ün .NET Framework 4,5 olarak ayarlandığından emin olun.

     Visual C# projeleri için, bu değeri **uygulama** sekmesinde ayarlayabilirsiniz. Visual Basic projeler için, bu değeri **derle** sekmesinde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md).

3. **ItemTemplateWizard** projesinde, projeye bir **pencere (WPF)** öğesi ekleyin ve ardından Item **WizardWindow**' u adlandırın.

4. CustomActionWizard ve dizeler adlı iki kod dosyası ekleyin.

5. **ItemTemplateWizard** projesi için kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

6. **Başvuru Yöneticisi-ItemTemplateWizard** iletişim kutusunda, **derlemeler** düğümü altında, **Uzantılar** düğümünü seçin.

7. Aşağıdaki derlemelerin yanındaki onay kutularını işaretleyin ve ardından **Tamam** düğmesini seçin:

    - EnvDTE

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. TemplateWizardInterface

8. **Çözüm Gezgini**, ItemTemplateWizard projesi için **Başvurular** klasöründe **EnvDTE** başvurusunu seçin.

9. **Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğinin değerini **false** olarak değiştirin.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Özel eylemler için varsayılan konumu ve KIMLIK dizelerini tanımlayın
 Her özel eylemin, `GroupID` `Location` `CustomAction` *Elements.xml* dosyasındaki öğesinin ve ÖZNITELIKLERINDE belirtilen bir konum ve kimliği vardır. Bu adımda, ItemTemplateWizard projesinde bu öznitelikler için geçerli dizelerin bazılarını tanımlarsınız. Bu izlenecek yolu tamamladığınızda, kullanıcılar sihirbazda bir konum ve KIMLIK belirtmede bu dizeler özel eylem proje öğesindeki *Elements.xml* dosyasına yazılır.

 Kolaylık olması için, bu örnek yalnızca kullanılabilir varsayılan konumların ve kimliklerin bir alt kümesini destekler. Tam liste için bkz. [varsayılan özel eylem konumları ve kimlikleri](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14)).

#### <a name="to-define-the-default-location-and-id-strings"></a>Varsayılan konumu ve KIMLIK dizelerini tanımlamak için

1. açın.

2. **ItemTemplateWizard** projesinde, dizeler kod dosyasındaki kodu aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb" id="Snippet6":::

## <a name="create-the-wizard-ui"></a>Sihirbaz kullanıcı arabirimini oluşturma
 Sihirbazın kullanıcı arabirimini tanımlamak için XAML ekleyin ve sihirbazdaki bazı denetimleri KIMLIK dizelerine bağlamak için bazı kodlar ekleyin. oluşturduğunuz sihirbaz, Visual Studio SharePoint projeler için yerleşik sihirbaza benzer.

#### <a name="to-create-the-wizard-ui"></a>Sihirbaz kullanıcı arabirimini oluşturmak için

1. **ItemTemplateWizard** projesinde, **WizardWindow. xaml** dosyası için kısayol menüsünü açın ve ardından **Aç** ' ı seçerek pencereyi tasarımcıda açın.

2. XAML görünümünde, geçerli XAML 'yi aşağıdaki XAML ile değiştirin. XAML, bir başlık, özel eylem davranışını belirtme denetimleri ve pencerenin alt kısmındaki gezinti düğmeleri içeren bir kullanıcı arabirimi tanımlar.

    > [!NOTE]
    > Bu kodu ekledikten sonra projeniz bazı derleme hatalarına sahip olacaktır. Sonraki adımlarda kod eklediğinizde bu hatalar kaybolur.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml" id="Snippet9":::

    > [!NOTE]
    > Bu XAML 'de oluşturulan pencere, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> temel sınıftan türetilir. Visual Studio için özel bir WPF iletişim kutusu eklediğinizde, iletişim kutusunu bu sınıftan türeten Visual Studio diğer iletişim kutularıyla tutarlı bir stil elde etmenizi ve aksi halde kalıcı iletişim kutularında oluşabilecek sorunlardan kaçınmanızı öneririz. Daha fazla bilgi için bkz. [kalıcı Iletişim kutuları oluşturma ve yönetme](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Visual Basic bir proje geliştiriyorsanız, `ItemTemplateWizard` ad alanını `WizardWindow` öğenin özniteliğinde sınıf adından kaldırın `x:Class` `Window` . Bu öğe, XAML 'in ilk satıröğesidir. İşiniz bittiğinde, ilk satır aşağıdaki koda benzemelidir:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow. xaml dosyası için arka plan kod dosyasında, geçerli kodu aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs" id="Snippet7":::

## <a name="implement-the-wizard"></a>Sihirbazı uygulama
 Arabirimini uygulayarak sihirbazın işlevselliğini tanımlayın <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

#### <a name="to-implement-the-wizard"></a>Sihirbazı uygulamak için

1. **ItemTemplateWizard** projesinde, **CustomActionWizard** kod dosyasını açın ve ardından bu dosyadaki geçerli kodu şu kodla değiştirin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs" id="Snippet8":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb" id="Snippet8":::

## <a name="checkpoint"></a>Checkpoint
 Bu noktada, sihirbazın tüm kodu artık projede bulunur. Hata olmadan derlendiğinden emin olmak için projeyi derleyin.

#### <a name="to-build-your-project"></a>Projenizi derlemek için

1. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

## <a name="associate-the-wizard-with-the-item-template"></a>Sihirbazı öğe şablonuyla ilişkilendir
 Sihirbazı uyguladığınıza göre, üç ana adımı tamamlayarak **özel eylem** öğesi şablonuyla ilişkilendirmeniz gerekir:

1. Sihirbaz derlemesini tanımlayıcı bir adla imzalayın.

2. Sihirbaz derlemesinin ortak anahtar belirtecini alın.

3. **Özel eylem** öğesi şablonu için. vstemplate dosyasındaki sihirbaz derlemesine bir başvuru ekleyin.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Sihirbaz derlemesini tanımlayıcı bir adla imzalamak için

1. **Çözüm Gezgini**' de, **ItemTemplateWizard** proje düğümünden kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. **İmzalama** sekmesinde, **derlemeyi imzala** onay kutusunu seçin.

3. **Tanımlayıcı ad seçin anahtar dosyası** listesinde, öğesini seçin **\<New...>** .

4. **Tanımlayıcı ad anahtarı oluştur** iletişim kutusunda bir ad girin, **anahtar dosyamı parolayla koru** onay kutusunu temizleyin ve **Tamam** düğmesini seçin.

5. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Sihirbaz derlemesinin ortak anahtar belirtecini almak için

1. bir Visual Studio komut istemi penceresinde, aşağıdaki komutu çalıştırarak, geliştirme bilgisayarınızda ıtemtemplatewizard projesi için yerleşik ItemTemplateWizard.dll derlemesinin tam yolunu ile *pathtowizardassembly* ' ı değiştirin.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     *ItemTemplateWizard.dllderlemesi için* ortak anahtar belirteci, Visual Studio istemi penceresine yazılır.

2. Visual Studio İstemi penceresini açık tutma. Sonraki yordamı tamamlamak için ortak anahtar belirteci gerekir.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.vstemplate dosyasında sihirbaz derlemesi için başvuru eklemek için

1. Bu **Çözüm Gezgini** **ItemTemplate** proje düğümünü genişletin ve *itemTemplate.vstemplate dosyasını* açın.

2. Dosyanın sonuna yakın bir yerde ve etiketleri `WizardExtension` arasına aşağıdaki `</TemplateContent>` öğeyi `</VSTemplate>` ekleyin. özniteliğinin *YourToken* değerini `PublicKeyToken` önceki yordamda edinilen ortak anahtar belirteci ile değiştirin.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     öğesi hakkında daha fazla bilgi `WizardExtension` için bkz. [WizardExtension Öğesi &#40;Visual Studio Şablonları&#41;. ](../extensibility/wizardextension-element-visual-studio-templates.md)

3. Dosyayı kaydedin ve kapatın.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Öğe şablonundaElements.xml *parametreleri* ekleme
 ItemTemplate projesinde Elements.xmldeğiştirilebilir parametreler ekleyin. Bu parametreler, daha önce `PopulateReplacementDictionary` tanımlandığı `CustomActionWizard` sınıftaki yönteminde başlatılır. Kullanıcı bir projeye Özel Eylem proje öğesi ekleyirken, Visual Studio yeni proje öğesinde yer alan *Elements.xml* dosyasındaki bu parametreleri sihirbazda belirtilen değerlerle otomatik olarak değiştirir.

 Değiştirilebilir parametre, dolar işareti ($) karakteriyle başlayan ve sona eren bir belirteçtir. Kendi değiştirilebilir parametrelerinizi tanımlamaya ek olarak, proje sisteminin tanımladığı ve SharePoint yerleşik parametreleri de kullanabilirsiniz. Daha fazla bilgi için [bkz. Değiştirilebilir parametreler.](../sharepoint/replaceable-parameters.md)

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Elements.xmldosyasına *değiştirilebilir parametreler* eklemek için

1. ItemTemplate projesinde, dosyanın içeriğini *Elements.xml* XML ile değiştirin.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="$IdValue$"
                    GroupId="$GroupIdValue$"
                    Location="$LocationValue$"
                    Sequence="1000"
                    Title="$TitleValue$"
                    Description="$DescriptionValue$" >
        <UrlAction Url="$UrlValue$"/>
      </CustomAction>
    </Elements>
    ```

     Yeni XML, , `Id` , , ve `GroupId` `Location` `Description` `Url` özniteliklerinin değerlerini değiştirilebilir parametrelerle değiştirir.

2. Dosyayı kaydedin ve kapatın.

## <a name="add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSIX paketine ekleme
 VSIX projesinin source.extension.vsixmanifest dosyasında, proje öğesini içeren VSIX paketiyle dağıtılması için sihirbaz projesine bir başvuru ekleyin.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSIX paketine eklemek için

1. **Çözüm Gezgini'da** CustomActionProjectItem projesinde **source.extension.vsixmanifest** dosyasındaki kısayol menüsünü açın ve  dosyayı bildirim düzenleyicisinde açmak için Aç'ı seçin.

2. Bildirim düzenleyicisinde Varlıklar sekmesini **ve** ardından Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu görüntülenir.

3. Tür **listesinde** **Microsoft.VisualStudio.Assembly'i seçin.**

4. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

5. Yeni **Project** **ItemTemplateWizard'ı ve** ardından Tamam **düğmesini** seçin.

6. Menü çubuğunda Derleme   >  **Çözümü'yü seçin** ve çözümün hatasız derlenmiş olduğundan emin olun.

## <a name="test-the-wizard"></a>Sihirbazı test etme
 Artık sihirbazı test etmeye hazırsınız. İlk olarak, Visual Studio'nin deneysel örneğinde CustomActionProjectItem çözümünde hata ayıklamaya Visual Studio. Ardından, SharePoint'nin deneysel örneğinde yer alan bir SharePoint Proje öğesi için sihirbazı Visual Studio. Son olarak, özel eylemin SharePoint çalıştığını doğrulamak için SharePoint projesini derleme ve çalıştırma.

#### <a name="to-start-to-debug-the-solution"></a>Çözümde hata ayıklamaya başlamak için

1. Yönetici Visual Studio ile yeniden başlatın ve CustomActionProjectItem çözümünü açın.

2. ItemTemplateWizard projesinde CustomActionWizard kod dosyasını açın ve ardından yönteminde ilk kod satırına bir kesme noktası `RunStarted` ekleyin.

3. Menü çubuğunda Özel Durumlarda **Hata Ayıkla'ya**  >  **tıklayın.**

4. Özel **Durumlar iletişim** kutusunda, Ortak Dil Çalışma Zamanı Özel Durumları için  Thrown ve **User tarafından** işsiz onay **kutularının** temiz olduğundan emin olun ve ardından **Tamam düğmesini** seçin.

5. **F5** anahtarını seçerek veya menü çubuğunda Hata AyıklamaYı Başlat hata ayıklamayı **seçerek**  >  **hata ayıklamayı başlatabilirsiniz.**

     Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Action Project Item\1.0 uzantısını yüker ve deneysel Visual Studio. Proje öğesini bu örnek içinde test Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Sihirbazı test etmek için Visual Studio

1. Deneysel Visual Studio örneğinde, menü çubuğunda Dosya Yeni   >    >  Dosya'Project.

2. Visual **C#** **veya Visual Basic** düğümünü genişletin (öğe şablonunuz tarafından kullanılan dile bağlı olarak), **SharePoint** düğümünü genişletin ve **ardından 2010 düğümünü** seçin.

3. Proje şablonları listesinde, SharePoint **2010 Project'ı** seçin, projeyi **CustomActionWizardTest** olarak adlanın ve ardından **Tamam düğmesini** seçin.

4. SharePoint **Özelleştirme Sihirbazı'nda,** hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin ve ardından Son **düğmesini** seçin.

5. Bu **Çözüm Gezgini** proje düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **Öğe'yi seçin.**

6. Yeni Öğe **Ekle - CustomItemWizardTest** iletişim kutusunda, SharePoint **düğümünü** genişletin ve **ardından 2010 düğümünü** genişletin.

7. Proje öğeleri listesinde Özel Eylem öğesini **ve** ardından Ekle **düğmesini** seçin.

8. Uygulamanın diğer örneğinde yer alan kodun Visual Studio daha önce yönteminde ayar güvenlik kesme noktası üzerinde durduğu `RunStarted` doğrulayın.

9. **F5** anahtarını seçerek veya menü çubuğunda Devam'da Hata Ayıkla'ya seçerek projede **hata ayıklamaya**  >  **devam eder.**

     SharePoint Özelleştirme Sihirbazı görüntülenir.

10. Konum **altında** Düzenle seçeneğini **listele** düğmesini seçin.

11. Grup Kimliği **listesinde İletişim'i** **seçin.**

12. Başlık **kutusuna** Geliştirici **Merkezi'SharePoint girin.**

13. Açıklama kutusuna **Geliştirici** Merkezi **web sitesini SharePoint yazın.**

14. URL **kutusuna** yazın ve **https://docs.microsoft.com/sharepoint/dev/** son **düğmesini** seçin.

     Visual Studio **CustomAction1** adlı bir öğeyi projenize ekler ve *Elements.xml* dosyasını düzenleyicide açar. Bu *Elements.xml* sihirbazda belirttiğiniz değerleri içerdiğini doğrulayın.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Özel eylemi test etmek için SharePoint

1. Deneysel örnek Visual Studio **F5** anahtarını seçin veya menü çubuğunda Hata Ayıklama Hata AyıklamaYı   >  **Başlat'ı seçin.**

     Özel eylem, SharePoint sitenin **Site URL'si** özelliği tarafından belirtilen siteye dağıtılır ve web tarayıcısı bu sitenin varsayılan sayfasını açar.

    > [!NOTE]
    > Betik **Hata Ayıklama Devre Dışı** iletişim kutusu görüntülenirse Evet **düğmesini** seçin.

2. Yeni sitenin Listeler SharePoint Görevler **bağlantısını** seçin.

     Görevler **- Tüm Görevler** sayfası görüntülenir.

3. Şeridin **Liste Araçları** sekmesinde Liste  sekmesini seçin ve ardından Ayarlar **grubunda** Listele'yi **Ayarlar.**

     Liste **Ayarlar** sayfası görüntülenir.

4. Sayfanın **üst kısmında** yer alan İletişim başlığı altında geliştirici **SharePoint** bağlantısını seçin, tarayıcının web sitesini açtığını doğrulayın ve https://docs.microsoft.com/sharepoint/dev/ ardından tarayıcıyı kapatın.

## <a name="cleaning-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizleme
 Proje öğesini test etme tamam olduktan sonra, proje öğesi şablonunu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizlemek için

1. Deneysel Visual Studio menü çubuğunda Araçlar Uzantıları ve   >  **Güncelleştirmeler'i seçin.**

     Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde, Özel Eylem Ve Öğe **Project'ı seçin** ve ardından Kaldır **düğmesini** seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı  kaldırmak istediğinizden emin olmak için Evet düğmesini  seçin ve ardından kaldırma işlemini tamamlamak için Şimdi Yeniden Başlat düğmesini seçin.

4. Her iki Visual Studio (deneysel örnek ve CustomActionProjectItem çözümünün açık olduğu Visual Studio örneği) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Özel proje SharePoint türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Proje öğeleri için öğe şablonları ve SharePoint şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Varsayılan Özel Eylem Konumları ve Kimlikleri](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
