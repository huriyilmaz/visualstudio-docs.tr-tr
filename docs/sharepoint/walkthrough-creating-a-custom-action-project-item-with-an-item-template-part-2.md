---
title: Öğe şablonu, Bölüm 2 ile özel eylem proje öğesi oluşturma
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 957af3fdb4a86f4973ff8ac24251bae923ec299c
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585477"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>İzlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma
  Özel bir SharePoint proje öğesi türü tanımladıktan ve Visual Studio 'daki bir öğe şablonuyla ilişkilendirdikten sonra, şablon için bir sihirbaz sağlamak isteyebilirsiniz. Bir projeye proje öğesinin yeni bir örneğini eklemek için şablonunuzu kullandıklarında kullanıcılardan bilgi toplamak için Sihirbazı kullanabilirsiniz. Topladığınız bilgiler Proje öğesini başlatmak için kullanılabilir.

 Bu kılavuzda, özel eylem proje öğesine [Izlenecek yol: bir öğe şablonuyla bir özel eylem proje öğesi oluşturun, 1. Bölüm](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)olarak bir sihirbaz ekleyeceksiniz. Bir Kullanıcı bir SharePoint projesine özel bir eylem proje öğesi eklediğinde, sihirbaz özel eylem (örneğin, konumu ve bir son kullanıcı seçtiğinde gidilecek URL) hakkında bilgi toplar ve bu bilgileri yeni proje öğesindeki *Elements.xml* dosyasına ekler.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir öğe şablonuyla ilişkili özel bir SharePoint proje öğesi türü için sihirbaz oluşturma.

- Visual Studio 'da SharePoint proje öğeleri için yerleşik sihirbazlara benzeyen özel bir sihirbaz Kullanıcı Arabirimi tanımlama.

- Sihirbazda topladığınız verilerle SharePoint proje dosyalarını başlatmak için değiştirilebilen parametreleri kullanma.

- Hata ayıklama ve Sihirbazı test etme.

> [!NOTE]
> Bir iş akışı için nasıl özel etkinlik oluşturulacağını gösteren [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 'dan bir örnek indirebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Bu yönergeyi gerçekleştirmek için, önce [Izlenecek yol: bir öğe şablonuyla bir özel eylem proje öğesi oluşturun, 1. Bölüm ' i](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)tamamlayarak CustomActionProjectItem çözümünü oluşturmanız gerekir.

 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere de ihtiyacınız vardır:

- Windows, SharePoint ve Visual Studio 'nun desteklenen sürümleri.

- Visual Studio SDK 'Sı. Bu izlenecek yol, Proje öğesini dağıtmak üzere bir VSıX paketi oluşturmak için SDK 'daki **VSIX proje** şablonunu kullanır. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- Visual Studio 'da proje ve öğe şablonları için sihirbazlar. Daha fazla bilgi için bkz. [nasıl yapılır: sihirbazları proje şablonlarıyla](../extensibility/how-to-use-wizards-with-project-templates.md) ve arabirimiyle kullanma <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

- SharePoint 'te özel eylemler. Daha fazla bilgi için bkz. [özel eylem](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Sihirbaz projesi oluşturma
 Bu izlenecek yolu tamamlamak için, [Izlenecek yol: bir öğe şablonuyla bir özel eylem proje öğesi oluşturma, 1. Bölüm](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)olarak bir proje eklemeniz gerekir. <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>Bu projede arabirimini uygular ve sihirbaz kullanıcı arabirimini tanımlayacaksınız.

#### <a name="to-create-the-wizard-project"></a>Sihirbaz projesi oluşturmak için

1. Visual Studio 'da CustomActionProjectItem çözümünü açın

2. **Çözüm Gezgini**, çözüm düğümü için kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

3. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümlerini genişletin ve sonra **Windows** düğümünü seçin.

4. **Yeni proje** iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **4,5 .NET Framework** seçildiğinden emin olun.

5. **WPF Kullanıcı denetimi kitaplığı** proje şablonu ' nu seçin, projenin **ItemTemplateWizard**' ı adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözümdeki **ItemTemplateWizard** projesini ekler.

6. Projedeki UserControl1 öğesini silin.

## <a name="configure-the-wizard-project"></a>Sihirbaz projesini yapılandırma
 Sihirbazı oluşturmadan önce, projeye bir Windows Presentation Foundation (WPF) penceresi, bir kod dosyası ve derleme başvuruları eklemeniz gerekir.

#### <a name="to-configure-the-wizard-project"></a>Sihirbaz projesini yapılandırmak için

1. **Çözüm Gezgini**' de, **ItemTemplateWizard** proje düğümünden kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. **Proje tasarımcısında**, hedef framework 'ün .NET Framework 4,5 olarak ayarlandığından emin olun.

     Visual C# projeleri için, bu değeri **uygulama** sekmesinde ayarlayabilirsiniz. Visual Basic projeler için, bu değeri **Derle** sekmesinde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md).

3. **ItemTemplateWizard** projesinde, projeye bir **pencere (WPF)** öğesi ekleyin ve ardından Item **WizardWindow**' u adlandırın.

4. CustomActionWizard ve dizeler adlı iki kod dosyası ekleyin.

5. **ItemTemplateWizard** projesi için kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

6. **Başvuru Yöneticisi-ItemTemplateWizard** iletişim kutusunda, **derlemeler** düğümü altında, **Uzantılar** düğümünü seçin.

7. Aşağıdaki derlemelerin yanındaki onay kutularını işaretleyin ve ardından **Tamam** düğmesini seçin:

    - EnvDTE

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. TemplateWizardInterface

8. **Çözüm Gezgini**, ItemTemplateWizard projesi için **Başvurular** klasöründe **EnvDTE** başvurusunu seçin.

9. **Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğinin değerini **false**olarak değiştirin.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Özel eylemler için varsayılan konumu ve KIMLIK dizelerini tanımlayın
 Her özel eylemin, `GroupID` `Location` `CustomAction` *Elements.xml* dosyasındaki öğesinin ve ÖZNITELIKLERINDE belirtilen bir konum ve kimliği vardır. Bu adımda, ItemTemplateWizard projesinde bu öznitelikler için geçerli dizelerin bazılarını tanımlarsınız. Bu izlenecek yolu tamamladığınızda, kullanıcılar sihirbazda bir konum ve KIMLIK belirtmede bu dizeler özel eylem proje öğesindeki *Elements.xml* dosyasına yazılır.

 Kolaylık olması için, bu örnek yalnızca kullanılabilir varsayılan konumların ve kimliklerin bir alt kümesini destekler. Tam liste için bkz. [varsayılan özel eylem konumları ve kimlikleri](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14)).

#### <a name="to-define-the-default-location-and-id-strings"></a>Varsayılan konumu ve KIMLIK dizelerini tanımlamak için

1. açın.

2. **ItemTemplateWizard** projesinde, dizeler kod dosyasındaki kodu aşağıdaki kodla değiştirin.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>Sihirbaz kullanıcı arabirimini oluşturma
 Sihirbazın kullanıcı arabirimini tanımlamak için XAML ekleyin ve sihirbazdaki bazı denetimleri KIMLIK dizelerine bağlamak için bazı kodlar ekleyin. Oluşturduğunuz sihirbaz, Visual Studio 'daki SharePoint projeleri için yerleşik sihirbaza benzer.

#### <a name="to-create-the-wizard-ui"></a>Sihirbaz kullanıcı arabirimini oluşturmak için

1. **ItemTemplateWizard** projesinde, **WizardWindow. xaml** dosyası için kısayol menüsünü açın ve ardından **Aç** ' ı seçerek pencereyi tasarımcıda açın.

2. XAML görünümünde, geçerli XAML 'yi aşağıdaki XAML ile değiştirin. XAML, bir başlık, özel eylem davranışını belirtme denetimleri ve pencerenin alt kısmındaki gezinti düğmeleri içeren bir kullanıcı arabirimi tanımlar.

    > [!NOTE]
    > Bu kodu ekledikten sonra projeniz bazı derleme hatalarına sahip olacaktır. Sonraki adımlarda kod eklediğinizde bu hatalar kaybolur.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > Bu XAML 'de oluşturulan pencere, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> temel sınıftan türetilir. Visual Studio 'ya özel bir WPF iletişim kutusu eklediğinizde, bu sınıftan iletişim kutusunu, Visual Studio 'daki diğer iletişim kutularıyla tutarlı bir stil elde etmek ve kalıcı iletişim kutularında oluşabilecek sorunları önlemek için türetmenizi öneririz. Daha fazla bilgi için bkz. [kalıcı Iletişim kutuları oluşturma ve yönetme](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Visual Basic bir proje geliştiriyorsanız, `ItemTemplateWizard` ad alanını `WizardWindow` öğenin özniteliğinde sınıf adından kaldırın `x:Class` `Window` . Bu öğe, XAML 'in ilk satıröğesidir. İşiniz bittiğinde, ilk satır aşağıdaki koda benzemelidir:

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow. xaml dosyası için arka plan kod dosyasında, geçerli kodu aşağıdaki kodla değiştirin.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>Sihirbazı uygulama
 Arabirimini uygulayarak sihirbazın işlevselliğini tanımlayın <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

#### <a name="to-implement-the-wizard"></a>Sihirbazı uygulamak için

1. **ItemTemplateWizard** projesinde, **CustomActionWizard** kod dosyasını açın ve ardından bu dosyadaki geçerli kodu şu kodla değiştirin:

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>Checkpoint
 Bu noktada, sihirbazın tüm kodu artık projede bulunur. Hata olmadan derlendiğinden emin olmak için projeyi derleyin.

#### <a name="to-build-your-project"></a>Projenizi derlemek için

1. Menü **çubuğunda Build**  >  **Build Solution**öğesini seçin.

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

5. Menü **çubuğunda Build**  >  **Build Solution**öğesini seçin.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Sihirbaz derlemesinin ortak anahtar belirtecini almak için

1. Bir Visual Studio komut Istemi penceresinde, aşağıdaki komutu çalıştırarak, geliştirme bilgisayarınızda bulunan ItemTemplateWizard projesi için bir yerleşik ItemTemplateWizard.dll derlemesinin tam yolu ile *PathToWizardAssembly* ' ı değiştirin.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     *ItemTemplateWizard.dll* derlemesinin ortak anahtar belirteci, Visual Studio komut istemi penceresine yazılır.

2. Visual Studio komut Istemi penceresini açık tutun. Bir sonraki yordamı tamamlayabilmeniz için ortak anahtar belirtecine ihtiyacınız olacaktır.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>. Vstemplate dosyasındaki sihirbaz derlemesine bir başvuru eklemek için

1. **Çözüm Gezgini**, **ItemTemplate** projesi düğümünü genişletin ve ardından *ItemTemplate. vstemplate* dosyasını açın.

2. Dosyanın sonuna yakın bir şekilde, `WizardExtension` ve etiketleri arasına aşağıdaki öğeyi ekleyin `</TemplateContent>` `</VSTemplate>` . Özniteliğin *YourToken* değerini, `PublicKeyToken` önceki yordamda elde ettiğiniz ortak anahtar belirteci ile değiştirin.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Öğesi hakkında daha fazla bilgi için `WizardExtension` bkz. [Wizardexgerme öğesi &#40;Visual Studio şablonları&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Dosyayı kaydedin ve kapatın.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Öğe şablonundaki *Elements.xml* dosyasına değiştirilebilir parametreler ekleme
 ItemTemplate projesindeki *Elements.xml* dosyasına çeşitli değiştirilebilir parametreler ekleyin. Bu parametreler, `PopulateReplacementDictionary` `CustomActionWizard` daha önce tanımladığınız sınıftaki yönteminde başlatılır. Bir Kullanıcı bir projeye özel bir eylem proje öğesi eklediğinde, Visual Studio otomatik olarak bu parametreleri yeni proje öğesindeki *Elements.xml* dosyasında, sihirbazda belirttikleri değerlerle değiştirir.

 Değiştirilebilir bir parametre, dolar işareti ($) karakteriyle başlayan ve biten bir belirteçtir. Kendi değiştirilebilen parametreleri tanımlamanın yanı sıra, SharePoint proje sisteminin tanımladığı ve Başlatan yerleşik parametreleri de kullanabilirsiniz. Daha fazla bilgi için bkz. [değiştirilebilen parametreler](../sharepoint/replaceable-parameters.md).

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

3. **Tür** listesinde **Microsoft. VisualStudio. Assembly**öğesini seçin.

4. **Kaynak** listesinde, **Geçerli çözümde bir proje**seçin.

5. **Proje** listesinde **ItemTemplateWizard**' ı seçin ve ardından **Tamam** düğmesini seçin.

6. Menü **çubuğunda Build**  >  **Build Solution**öğesini seçin ve ardından çözümün hatasız derlendiğinden emin olun.

## <a name="test-the-wizard"></a>Sihirbazı test etme
 Artık Sihirbazı test etmeye hazırsınız. İlk olarak, Visual Studio 'nun Deneysel örneğindeki CustomActionProjectItem çözümünde hata ayıklamaya başlayın. Ardından, Visual Studio 'nun Deneysel örneğindeki bir SharePoint projesindeki özel eylem proje öğesi için Sihirbazı test edin. Son olarak, özel eylemin beklendiği gibi çalıştığını doğrulamak için SharePoint projesini derleyin ve çalıştırın.

#### <a name="to-start-to-debug-the-solution"></a>Çözümdeki hata ayıklamaya başlamak için

1. Visual Studio 'Yu yönetici kimlik bilgileriyle yeniden başlatın ve CustomActionProjectItem çözümünü açın.

2. ItemTemplateWizard projesinde, CustomActionWizard kod dosyasını açın ve sonra yöntemdeki kodun ilk satırına bir kesme noktası ekleyin `RunStarted` .

3. Menü çubuğunda, **hata ayıklama**  >  **özel durumları**' nı seçin.

4. **Özel durumlar** iletişim kutusunda, **ortak dil çalışma zamanı özel durumları** için **oluşturulan** ve **Kullanıcı tarafından işlenmeyen** onay kutularının temizlenmiş olduğundan emin olun ve **Tamam** düğmesini seçin.

5. **F5** tuşunu seçerek veya menü **çubuğunda hata ayıklamayı**Başlat ' ı seçerek hata ayıklamayı başlatın  >  **Start Debugging**.

     Visual Studio, uzantıyı%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Action Project ıtem\1.0 konumuna yükleyerek Visual Studio 'nun deneysel bir örneğini başlatır. Bu Visual Studio örneğinde Proje öğesini test edeceksiniz.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Visual Studio 'da Sihirbazı test etmek için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

2. **Visual C#** veya **Visual Basic** düğümünü (öğe şablonunuzun desteklediği dile bağlı olarak) genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. Proje şablonları listesinde **SharePoint 2010 projesi**' ni seçin, projeyi **CustomActionWizardTest**olarak adlandırın ve **Tamam** düğmesini seçin.

4. **SharePoint Özelleştirme Sihirbazı**'nda, hata ayıklama için kullanmak istediğiniz sitenin URL 'sini girin ve ardından **son** düğmesini seçin.

5. **Çözüm Gezgini**, proje düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

6. **Yeni öğe Ekle-CustomItemWizardTest** Iletişim kutusunda **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü genişletin.

7. Proje öğeleri listesinde **özel eylem** öğesini seçin ve sonra **Ekle** düğmesini seçin.

8. Visual Studio 'nun diğer örneğindeki kodun, daha önce yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın `RunStarted` .

9. **F5** tuşunu seçerek veya menü çubuğunda **Hata Ayıkla**  >  **devam et**' i seçerek projede hata ayıklamaya devam edin.

     SharePoint Özelleştirme Sihirbazı görüntülenir.

10. **Konum**' un altında, **Liste Düzenle** seçenek düğmesini seçin.

11. **Grup Kimliği** listesinde **iletişimler**' i seçin.

12. **Başlık** kutusuna **SharePoint Geliştirici Merkezi**' ni girin.

13. **Açıklama** kutusuna **SharePoint Geliştirici Merkezi Web sitesini açar**yazın.

14. **URL** kutusuna girin **https://docs.microsoft.com/sharepoint/dev/** ve ardından **son** düğmesini seçin.

     Visual Studio projenize **CustomAction1** adlı bir öğe ekler ve *Elements.xml* dosyasını düzenleyicide açar. *Elements.xml* , sihirbazda belirttiğiniz değerleri içerdiğini doğrulayın.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint 'te özel eylemi test etmek için

1. Visual Studio 'nun deneysel örneğinde **F5** tuşunu seçin veya menü çubuğunda **Hata Ayıkla**  >  **Başlat hata**Ayıkla ' yı seçin.

     Özel eylem paketlenir ve projenin **site URL 'si** özelliği tarafından belirtilen SharePoint sitesine dağıtılır ve Web tarayıcısı bu sitenin varsayılan sayfasında açılır.

    > [!NOTE]
    > **Betik hata ayıklama devre dışı** iletişim kutusu görüntülenirse, **Evet** düğmesini seçin.

2. SharePoint sitesinin listeler alanında **Görevler** bağlantısını seçin.

     **Görevler-tüm görevler** sayfası görüntülenir.

3. Şeridin **Liste araçları** sekmesinde, **liste** sekmesini seçin ve ardından **Ayarlar** grubunda **Liste ayarları**' nı seçin.

     **Liste ayarları** sayfası görüntülenir.

4. Sayfanın üst kısmındaki **iletişim** başlığı altında **SharePoint Geliştirici Merkezi** bağlantısını seçin, tarayıcının Web sitesini açtığından emin olun https://docs.microsoft.com/sharepoint/dev/ ve ardından tarayıcıyı kapatın.

## <a name="cleaning-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 Proje öğesini test etmeyi tamamladıktan sonra, Visual Studio 'nun deneysel örneğinden proje öğesi şablonunu kaldırın.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizlemek için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde **özel eylem proje öğesi** uzantısını seçin ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin ve ardından kaldırma işlemini gerçekleştirmek Için **Şimdi yeniden Başlat** düğmesini seçin.

4. Her iki Visual Studio örneğini kapatın (CustomActionProjectItem çözümünün açık olduğu deneysel örnek ve Visual Studio örneği).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: öğe şablonu, Bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
- [Varsayılan özel eylem konumları ve kimlikleri](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
