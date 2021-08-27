---
title: Öğe şablonu, bölüm 2 ile özel eylem proje öğesi oluşturma
titleSuffix: ''
description: Bu kılavuzda, bir öğe şablonu kullanarak bir özel eylem proje öğesini bir web sitesine eklemek üzere kullanıcılardan bilgi toplamak için SharePoint ekleyin.
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
ms.openlocfilehash: b31a68bcc8c3dac0cb0056a4c3f429063747b4df
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980501"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, bölüm 2
  Proje öğesi için özel bir SharePoint tanımladığınız ve bunu Visual Studio bir öğe şablonuyla ilişkilendirmeniz sonrasında, şablon için bir sihirbaz sağlamak da iyi olabilir. Bir projeye proje öğesinin yeni bir örneğini eklemek üzere şablonlarınızı kullanan kullanıcılardan bilgi toplamak için sihirbazı kullanabilirsiniz. Toplayan bilgiler proje öğesini başlatmak için kullanılabilir.

 Bu kılavuzda, Kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma [bölümünde (Bölüm 1)](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)gösterilen Özel Eylem proje öğesine bir sihirbaz eklenecektir. Bir kullanıcı bir SharePoint projesine Özel Eylem proje öğesi eklerken, sihirbaz özel eylem (örneğin, son kullanıcı bunu seçerken gidilen konum ve URL) hakkında bilgi toplar ve bu bilgileri yeni proje öğesinde *Elements.xml* dosyasına ekler.

 Bu kılavuz aşağıdaki görevleri gösterir:

- Bir öğe şablonuyla ilişkili SharePoint proje öğesi türü için sihirbaz oluşturma.

- Yerleşik sihirbazlara benzer özel bir sihirbaz kullanıcı arabirimi tanımlama ve SharePoint proje öğelerini Visual Studio.

- Proje dosyalarını sihirbazda toplayan SharePoint başlatmak için değiştirilebilir parametreleri kullanma.

- Sihirbazda hata ayıklama ve test etme.

> [!NOTE]
> GitHub'dan iş [](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) akışı için özel etkinlikler oluşturma adımlarını gösteren bir örnek indirebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu gerçekleştirmek için öncelikle Adım adım: Öğe şablonuyla özel eylem proje öğesi oluşturma Bölüm 1'i tamamlayarak CustomActionProjectItem [çözümünü oluşturmanız gerekir.](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere de ihtiyacınız vardır:

- Desteklenen Windows, SharePoint ve Visual Studio.

- Visual Studio SDK'sı. Bu kılavuzda, **proje öğesini Project** bir VSIX paketi oluşturmak için SDK'daki VSIX uygulama şablonu kullanılır. Daha fazla bilgi için [bkz. SharePoint'de Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

  Aşağıdaki kavramlar hakkında bilgi sahibi olmak, izlenecek yolu tamamlamak için faydalıdır ancak gerekli değildir:

- Proje ve öğe şablonları için sihirbazlar Visual Studio. Daha fazla bilgi için, [bkz. How to: Use Wizards with Project templates](../extensibility/how-to-use-wizards-with-project-templates.md) and <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> the interface.

- Uygulama içinde özel SharePoint. Daha fazla bilgi için bkz. [Özel Eylem](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Sihirbaz projesi oluşturma
 Bu izlenecek yolu tamamlamak için, Kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma bölümünde oluşturduğunuz CustomActionProjectItem çözümüne bir proje eklemeniz [gerekir, Bölüm 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Bu projede <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimini uygulayacak ve sihirbaz kullanıcı arabirimini tanımlayabilirsiniz.

#### <a name="to-create-the-wizard-project"></a>Sihirbaz projesi oluşturmak için

1. Bu Visual Studio CustomActionProjectItem çözümünü açın

2. Bu **Çözüm Gezgini,** çözüm düğümünün kısayol menüsünü açın, Ekle'yi **ve** ardından Yeni **düğümler'i Project.**

3. Yeni **Project** iletişim kutusunda **Visual C#** veya Visual Basic **genişletin** ve ardından Windows **seçin.**

4. Yeni Sürümler **iletişim Project** üst kısmında, .NET Framework sürüm listesinde **4.5'in** .NET Framework.

5. **WPF Kullanıcı Denetimi Kitaplığı proje** şablonunu seçin, projeye **ItemTemplateWizard adını ve** ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Çözüme ItemTemplateWizard** projesini ekler.

6. UserControl1 öğesini projeden silin.

## <a name="configure-the-wizard-project"></a>Sihirbaz projesini yapılandırma
 Sihirbazı oluşturmadan önce, projeye bir Windows Presentation Foundation (WPF) penceresi, bir kod dosyası ve derleme başvuruları eklemeniz gerekir.

#### <a name="to-configure-the-wizard-project"></a>Sihirbaz projesini yapılandırmak için

1. Bu **Çözüm Gezgini,** **ItemTemplateWizard** proje düğümünden kısayol menüsünü açın ve ardından Özellikler'i **seçin.**

2. Project **Tasarımcısı'nda,** hedef çerçevenin 4.5'e .NET Framework emin olun.

     Visual C# projeleri için bu değeri Uygulama **sekmesinden** ayarlayabilirsiniz. Diğer Visual Basic için bu değeri Derle **sekmesinden** ayarlayabilirsiniz. Daha fazla bilgi için, [bkz. How to: Target a Version of the .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

3. **ItemTemplateWizard** projesinde, projeye **bir Pencere (WPF)** öğesi ekleyin ve ardından öğeyi **WizardWindow olarak ad girin.**

4. CustomActionWizard ve Strings adlı iki kod dosyası ekleyin.

5. **ItemTemplateWizard projesinin kısayol menüsünü açın ve** Başvuru Ekle'yi **seçin.**

6. Başvuru **Yöneticisi - ItemTemplateWizard** iletişim kutusunun Derlemeler **düğümü** altında Uzantılar **düğümünü** seçin.

7. Aşağıdaki derlemelerin yanındaki onay kutularını ve ardından Tamam **düğmesini** seçin:

    - Envdte

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. Bu **Çözüm Gezgini,** ItemTemplateWizard projesinin Başvurular klasöründe **EnvDTE başvuruyu** seçin. 

9. Özellikler **penceresinde** Birlikte Çalışma Türleri Ekle **özelliğinin değerini** False olarak **değiştirin.**

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Özel eylemler için varsayılan konum ve kimlik dizelerini tanımlama
 Her özel eylemin,Elements.xmldosyasındaki öğesinin ve özniteliklerinde `GroupID` `Location` belirtilen bir `CustomAction` *Elements.xml* vardır. Bu adımda, ItemTemplateWizard projesinde bu öznitelikler için bazı geçerli dizeleri tanımlarız. Bu kılavuz tamamlandıktan sonra, kullanıcılar sihirbazda bir *konumElements.xml* kimlik belirttiğinizde bu dizeler Özel Eylem proje öğesinde yer alanElements.xmldosyasına yazılır.

 Kolaylık olması için bu örnek, kullanılabilir varsayılan konumların ve kimliklerin yalnızca bir alt kümesini destekler. Tam liste için bkz. [Varsayılan Özel Eylem Konumları ve kimlikleri.](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))

#### <a name="to-define-the-default-location-and-id-strings"></a>Varsayılan konum ve kimlik dizelerini tanımlamak için

1. Açık.

2. **ItemTemplateWizard projesinde** Dizeler kod dosyasındaki kodu aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs" id="Snippet6":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb" id="Snippet6":::

## <a name="create-the-wizard-ui"></a>Sihirbaz kullanıcı arabirimini oluşturma
 Sihirbazın kullanıcı arabirimini tanımlamak için XAML ekleyin ve sihirbazda bazı denetimleri kimlik dizeleri ile bağlamak için kod ekleyin. Sizin oluşturyruz sihirbaz, SharePoint projelerinin yerleşik sihirbazına Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Sihirbaz kullanıcı arabirimini oluşturmak için

1. **ItemTemplateWizard** projesinde **WizardWindow.xaml** dosyasının kısayol menüsünü açın ve  ardından Aç'ı seçerek pencereyi tasarımcıda açın.

2. XAML görünümünde geçerli XAML'i aşağıdaki XAML ile değiştirin. XAML; başlığı, özel eylemin davranışını belirtme denetimlerini ve pencerenin alt kısmında gezinti düğmelerini içeren bir kullanıcı arabirimi tanımlar.

    > [!NOTE]
    > Bu kodu ekledikten sonra projeniz bazı derleme hatalarına neden olur. Sonraki adımlarda kod eklerken bu hatalar gider.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml" id="Snippet9":::

    > [!NOTE]
    > Bu XAML'de oluşturulan pencere temel sınıftan <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> türetildi. Visual Studio'a özel bir WPF iletişim kutusu eklerken, Visual Studio'de diğer iletişim kutularıyla tutarlı stil oluşturmak ve kalıcı iletişim kutularıyla başka türlü ortaya çıkabilir sorunları önlemek için iletişim kutusunu bu sınıftan türetmenizi öneririz. Daha fazla bilgi için [bkz. Kalıcı İletişim Kutuları Oluşturma ve Yönetme.](../extensibility/creating-and-managing-modal-dialog-boxes.md)

3. Bir Visual Basic projesi geliştiriyorsanız, `ItemTemplateWizard` öğenin `WizardWindow` özniteliğinde sınıf `x:Class` adı'dan ad alanını `Window` kaldırın. Bu öğe XAML'nin ilk satırıdır. Bitirin, ilk satır aşağıdaki koda benzesin:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow.xaml dosyasının arka arkasındaki kod dosyasında geçerli kodu aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs" id="Snippet7":::

## <a name="implement-the-wizard"></a>Sihirbazı uygulama
 Arabirimini kullanarak sihirbazın işlevselliğini <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> tanımlayın.

#### <a name="to-implement-the-wizard"></a>Sihirbazı uygulamak için

1. **ItemTemplateWizard** projesinde **CustomActionWizard** kod dosyasını açın ve ardından bu dosyada yer alan geçerli kodu aşağıdaki kodla değiştirin:

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs" id="Snippet8":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb" id="Snippet8":::

## <a name="checkpoint"></a>Checkpoint
 Kılavuzda bu noktada, sihirbazın tüm kodu artık projededir. Hatasız derlenmiş olduğundan emin olmak için projeyi derle.

#### <a name="to-build-your-project"></a>Projenizi derlemek için

1. Menü çubuğunda Derleme   >  **Çözümü'ne tıklayın.**

## <a name="associate-the-wizard-with-the-item-template"></a>Sihirbazı öğe şablonuyla ilişkilendirme
 Sihirbazı uygulamaya başladınız, üç ana adımı tamamlayarak bunu **Özel Eylem** öğesi şablonuyla ilişkilendirmeniz gerekir:

1. Sihirbaz derlemeyi bir güçlü adla imzalar.

2. Sihirbaz derlemesi için ortak anahtar belirteci alın.

3. Özel Eylem öğesi şablonu için .vstemplate dosyasında sihirbaz **derlemesine bir başvuru** ekleyin.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Sihirbaz derlemeyi güçlü bir adla imzalamak için

1. Bu **Çözüm Gezgini,** **ItemTemplateWizard** proje düğümünden kısayol menüsünü açın ve ardından Özellikler'i **seçin.**

2. İmzalama **sekmesinde** Derlemeyi **imzala onay** kutusunu seçin.

3. Bir **güçlü ad anahtar dosyası seçin listesinde'yi** **\<New...>** seçin.

4. Güçlü **Ad Anahtarı Oluştur iletişim** kutusunda bir ad  girin, Anahtar dosyamı parolayla koru onay kutusunun işaretini kaldırın ve ardından Tamam **düğmesini** seçin.

5. Menü çubuğunda Derleme   >  **Çözümü'ne tıklayın.**

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Sihirbaz derlemesi için ortak anahtar belirteci almak için

1. Bir Visual Studio Komut İstemi penceresinde *pathToWizardAssembly* yerine geliştirme bilgisayarınızda ItemTemplateWizard projesi için yerleşik ItemTemplateWizard.dll derlemenin tam yolunu yazın.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     *ItemTemplateWizard.dll* derlemesinin ortak anahtar belirteci Visual Studio komut istemi penceresine yazılır.

2. Visual Studio komut istemi penceresini açık tutun. Bir sonraki yordamı tamamlayabilmeniz için ortak anahtar belirtecine ihtiyacınız olacaktır.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>. Vstemplate dosyasındaki sihirbaz derlemesine bir başvuru eklemek için

1. **Çözüm Gezgini**, **ItemTemplate** projesi düğümünü genişletin ve ardından *ItemTemplate. vstemplate* dosyasını açın.

2. Dosyanın sonuna yakın bir şekilde, `WizardExtension` ve etiketleri arasına aşağıdaki öğeyi ekleyin `</TemplateContent>` `</VSTemplate>` . Özniteliğin *YourToken* değerini, `PublicKeyToken` önceki yordamda elde ettiğiniz ortak anahtar belirteci ile değiştirin.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     öğesi hakkında daha fazla bilgi için `WizardExtension` , bkz. [wizardexgerme öğesi &#40;Visual Studio şablonlar&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Dosyayı kaydedin ve kapatın.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Öğe şablonundaki *Elements.xml* dosyasına değiştirilebilir parametreler ekleme
 ItemTemplate projesindeki *Elements.xml* dosyasına çeşitli değiştirilebilir parametreler ekleyin. Bu parametreler, `PopulateReplacementDictionary` `CustomActionWizard` daha önce tanımladığınız sınıftaki yönteminde başlatılır. bir kullanıcı bir projeye özel bir eylem proje öğesi eklediğinde, Visual Studio otomatik olarak yeni proje öğesindeki *Elements.xml* dosyasında bu parametreleri sihirbazda belirttikleri değerlerle değiştirir.

 Değiştirilebilir bir parametre, dolar işareti ($) karakteriyle başlayan ve biten bir belirteçtir. kendi değiştirilebilir parametrelerinizi tanımlamanın yanı sıra, SharePoint projesi sisteminin tanımladığı ve başlatan yerleşik parametreleri de kullanabilirsiniz. Daha fazla bilgi için bkz. [değiştirilebilen parametreler](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>*Elements.xml* dosyasına değiştirilebilir parametreler eklemek için

1. ItemTemplate projesinde, *Elements.xml* dosyanın IÇERIĞINI aşağıdaki XML ile değiştirin.

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

     Yeni XML,,,, `Id` `GroupId` `Location` `Description` ve `Url` özniteliklerinin değerlerini değiştirilebilen parametrelere dönüştürür.

2. Dosyayı kaydedin ve kapatın.

## <a name="add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSıX paketine ekleyin
 VSıX projesindeki kaynak. Extension. valtmanifest dosyasında, Proje öğesini içeren VSıX paketiyle dağıtılacak şekilde sihirbaz projesine bir başvuru ekleyin.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSıX paketine eklemek için

1. **Çözüm Gezgini**' de, CustomActionProjectItem projesindeki **kaynak. Extension. valtmanifest** dosyasındaki kısayol menüsünü açın ve sonra dosyayı bildirim düzenleyicisinde açmak için **Aç** ' ı seçin.

2. Bildirim Düzenleyicisi 'nde **varlıklar** sekmesini seçin ve ardından **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu görüntülenir.

3. **Tür** listesinde **Microsoft. VisualStudio. Assembly** öğesini seçin.

4. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

5. **Project** listesinde **ıtemtemplatewizard**' ı seçin ve ardından **tamam** düğmesini seçin.

6. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından çözümün hatasız derlendiğinden emin olun.

## <a name="test-the-wizard"></a>Sihirbazı test etme
 Artık Sihirbazı test etmeye hazırsınız. İlk olarak, Visual Studio deneysel örneğinde CustomActionProjectItem çözümünde hata ayıklamaya başlayın. sonra, Visual Studio deneysel örneğinde SharePoint projesindeki özel eylem proje öğesi için sihirbazı test edin. son olarak, özel eylemin beklendiği gibi çalıştığını doğrulamak için SharePoint projesi derleyin ve çalıştırın.

#### <a name="to-start-to-debug-the-solution"></a>Çözümdeki hata ayıklamaya başlamak için

1. yönetici kimlik bilgileriyle Visual Studio yeniden başlatın ve sonra CustomActionProjectItem çözümünü açın.

2. ItemTemplateWizard projesinde, CustomActionWizard kod dosyasını açın ve sonra yöntemdeki kodun ilk satırına bir kesme noktası ekleyin `RunStarted` .

3. Menü çubuğunda, **hata ayıklama**  >  **özel durumları**' nı seçin.

4. **Özel durumlar** iletişim kutusunda, **ortak dil çalışma zamanı özel durumları** için **oluşturulan** ve **Kullanıcı tarafından işlenmeyen** onay kutularının temizlenmiş olduğundan emin olun ve **Tamam** düğmesini seçin.

5. **F5** tuşunu seçerek veya menü **çubuğunda hata ayıklamayı** Başlat ' ı seçerek hata ayıklamayı başlatın  >  .

     Visual Studio, uzantıyı%userprofile%\appdata\local\microsoft\visualstudio\11.0exp\extensions\contoso\custom Action Project ıtem\1.0 dizinine yükleyip deneysel bir Visual Studio örneğini başlatır. Proje öğesini bu Visual Studio örneğinde test edersiniz.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Sihirbazı Visual Studio test etmek için

1. Visual Studio deneysel örneğinde, menü çubuğunda **dosya**  >  **yeni**  >  **Project**' ni seçin.

2. **Visual C#** veya **Visual Basic** düğümünü (öğe şablonunuzun desteklediği dile bağlı olarak) genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. proje şablonları listesinde **SharePoint 2010 Project** öğesini seçin, projeyi **CustomActionWizardTest** olarak adlandırın ve **tamam** düğmesini seçin.

4. **SharePoint özelleştirme sihirbazında**, hata ayıklama için kullanmak istediğiniz sitenin URL 'sini girin ve ardından **son** düğmesini seçin.

5. **Çözüm Gezgini**, proje düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

6. **yeni öğe ekle-customıtemwizardtest** iletişim kutusunda **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü genişletin.

7. Proje öğeleri listesinde **özel eylem** öğesini seçin ve sonra **Ekle** düğmesini seçin.

8. diğer Visual Studio örneğindeki kodun, daha önce yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın `RunStarted` .

9. **F5** tuşunu seçerek veya menü çubuğunda **Hata Ayıkla**  >  **devam et**' i seçerek projede hata ayıklamaya devam edin.

     SharePoint özelleştirme sihirbazı görüntülenir.

10. **Konum**' un altında, **Liste Düzenle** seçenek düğmesini seçin.

11. **Grup Kimliği** listesinde **iletişimler**' i seçin.

12. **başlık** kutusuna **SharePoint geliştirici merkezi** yazın.

13. **açıklama** kutusuna **SharePoint geliştirici merkezi web sitesini açar** yazın.

14. **URL** kutusuna girin `https://docs.microsoft.com/sharepoint/dev/` ve ardından **son** düğmesini seçin.

     Visual Studio, projenize **CustomAction1** adlı bir öğe ekler ve *Elements.xml* dosyasını düzenleyicide açar. *Elements.xml* , sihirbazda belirttiğiniz değerleri içerdiğini doğrulayın.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint özel eylemi test etmek için

1. Visual Studio deneysel örneğinde **F5** tuşunu seçin veya menü çubuğunda **hata ayıkla**  >  **başlat hata** ayıkla ' yı seçin.

     özel eylem paketlenir ve projenin **site URL 'si** özelliği tarafından belirtilen SharePoint sitesine dağıtılır ve web tarayıcısı bu sitenin varsayılan sayfasında açılır.

    > [!NOTE]
    > **Betik hata ayıklama devre dışı** iletişim kutusu görüntülenirse, **Evet** düğmesini seçin.

2. SharePoint sitesinin listeler alanında **görevler** bağlantısını seçin.

     **Görevler-tüm görevler** sayfası görüntülenir.

3. şeridin **liste araçları** sekmesinde **liste** sekmesini seçin ve ardından **Ayarlar** grubunda **liste Ayarlar**' yı seçin.

     **liste Ayarlar** sayfası görüntülenir.

4. sayfanın üst kısmındaki **iletişim** başlığı altında, **SharePoint geliştirici merkezi** bağlantısı ' nı seçin, tarayıcının web sitesini açtığından emin olun `https://docs.microsoft.com/sharepoint/dev/` ve ardından tarayıcıyı kapatın.

## <a name="cleaning-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 Proje öğesini test etmeyi tamamladıktan sonra, Visual Studio deneysel örneğinden proje öğesi şablonunu kaldırın.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizlemek için

1. Visual Studio deneysel örneğinde, menü çubuğunda **araçlar**  >  **uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. uzantılar listesinde, **öğe uzantısını Project özel eylem** ' i seçin ve ardından **kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin ve ardından kaldırma işlemini gerçekleştirmek Için **Şimdi yeniden Başlat** düğmesini seçin.

4. her iki Visual Studio örneğini (deneysel örnek ve CustomActionProjectItem çözümünün açık olduğu Visual Studio örneğini) kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: öğe şablonu, Bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Varsayılan özel eylem konumları ve kimlikleri](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
