---
title: Proje şablonu, bölüm 2 ile site sütunu proje öğesi oluşturma
titleSuffix: ''
description: Proje öğesini içeren bir proje oluşturmak üzere şablonu kullanan kullanıcılardan veri toplamak için bir site sütunu proje şablonuna SharePoint sihirbaz ekleyin.
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
ms.openlocfilehash: c4530a43787b2e29c2600476a44c808132d668ceaa89b851efeddd403c2c30e6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352829"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Adım adım kılavuz: Proje şablonuyla site sütunu proje öğesi oluşturma, Bölüm 2
  Proje öğesi için özel bir SharePoint tanımladığınız ve bunu Visual Studio proje şablonuyla ilişkilendirmeniz sonrasında, şablon için bir sihirbaz sağlamak da iyi olabilir. Proje öğesini içeren yeni bir proje oluşturmak üzere şablonlarınızı kullanan kullanıcılardan bilgi toplamak için sihirbazı kullanabilirsiniz. Toplayan bilgiler proje öğesini başlatmak için kullanılabilir.

 Bu kılavuzda, Site Sütunu proje şablonuna, Adım 1: Bir Site Sütunu Project Öğesi Oluşturma bölümünde Project sihirbazı [eklenecektir.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md) Kullanıcı bir Site Sütunu projesi oluşturduğunda sihirbaz, site sütunu (temel türü ve grubu gibi) hakkında bilgi toplar ve bu bilgileri *yeni projedeElements.xml* dosyasına ekler.

 Bu kılavuz aşağıdaki görevleri gösterir:

- Özel bir proje şablonu SharePoint bir proje şablonuyla ilişkili proje öğesi türü için sihirbaz oluşturma.

- SharePoint projelerinin yerleşik sihirbazlara benzeyen özel bir sihirbaz kullanıcı arabirimi Visual Studio.

- Sihirbaz *SharePoint yerel* siteye çağrı yapmak için kullanılan iki SharePoint komut oluşturma. SharePoint komutları, Visual Studio sunucu nesne modelinde API'SharePoint çağıran yöntemlerdir. Daha fazla bilgi için [bkz. nesne SharePoint çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

- Proje dosyalarını sihirbazda toplayan SharePoint başlatmak için değiştirilebilir parametreleri kullanma.

- Her yeni Site Sütunu proje örneğinde yeni bir .snk dosyası oluşturma. Bu dosya, çözüm derlemesini genel derleme önbelleğine SharePoint proje çıktısını imzalamak için kullanılır.

- Sihirbazda hata ayıklama ve test etme.

> [!NOTE]
> Bir dizi örnek iş akışı için bkz. [SharePoint örnekleri.](/sharepoint/dev/general-development/sharepoint-workflow-samples)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu gerçekleştirmek için öncelikle Adım Adım: Bir Site Sütunu Project Öğesi Oluşturma, Bölüm 1'i tamamlayarak SiteColumnProjectItem çözümünü [Project oluşturmanız gerekir.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)

 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere de ihtiyacınız vardır:

- Desteklenen Windows, SharePoint ve Visual Studio.

- Visual Studio SDK'sı. Bu kılavuzda, **proje öğesini Project** bir VSIX paketi oluşturmak için SDK'daki VSIX uygulama şablonu kullanılır. Daha fazla bilgi için [bkz. SharePoint'de Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

  Aşağıdaki kavramlar hakkında bilgi sahibi olmak, izlenecek yolu tamamlamak için faydalıdır ancak gerekli değildir:

- Proje ve öğe şablonları için sihirbazlar Visual Studio. Daha fazla bilgi için, [bkz. How to: Use Wizards with Project templates](../extensibility/how-to-use-wizards-with-project-templates.md) and <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> the interface.

- SharePoint. Daha fazla bilgi için bkz. [Sütunlar.](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))

## <a name="understand-the-wizard-components"></a>Sihirbaz bileşenlerini anlama
 Bu kılavuzda gösteren sihirbaz çeşitli bileşenler içerir. Aşağıdaki tabloda bu bileşenler açıkmektedir.

|Bileşen|Açıklama|
|---------------|-----------------|
|Sihirbaz uygulaması|Bu, arabirimini uygulayan `SiteColumnProjectWizard` adlı bir <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> sınıftır. Bu arabirim, sihirbaz başlatıldığında Visual Studio ve sihirbaz çalışırken belirli zamanlarda çağıran yöntemleri tanımlar.|
|Sihirbaz kullanıcı arabirimi|Bu, adlı WPF tabanlı bir `WizardWindow` penceredir. Bu pencere, ve adlı iki kullanıcı denetimi `Page1` `Page2` içerir. Bu kullanıcı denetimleri sihirbazın iki sayfalarını temsil eder.<br /><br /> Bu kılavuzda, sihirbaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> uygulamasının yöntemi sihirbaz kullanıcı arabirimini görüntüler.|
|Sihirbaz veri modeli|Bu, sihirbaz kullanıcı arabirimi ile sihirbaz uygulaması arasında bir katman sağlayan adlı `SiteColumnWizardModel` bir ara sınıftır. Bu örnek, sihirbaz uygulamasını ve sihirbaz kullanıcı arabirimini diğerlerinden soyutlamanıza yardımcı olmak için bu sınıfı kullanır; Bu sınıf, tüm sihirbazların gerekli bir bileşeni değildir.<br /><br /> Bu kılavuzda, sihirbaz uygulaması sihirbaz kullanıcı arabirimini `SiteColumnWizardModel` görüntülerken bir nesneyi sihirbaz penceresine iletir. Sihirbaz kullanıcı arabirimi, kullanıcı arabiriminde denetimlerin değerlerini kaydetmek ve giriş sitesi URL'sinin geçerli olduğunu doğrulama gibi görevleri gerçekleştirmek için bu nesnenin yöntemlerini kullanır. Kullanıcı sihirbazı tamamladikten sonra sihirbaz uygulaması, kullanıcı `SiteColumnWizardModel` arabiriminin son durumunu belirlemek için nesnesini kullanır.|
|Project yöneticisi|Bu, sihirbaz uygulaması tarafından her yeni proje örneğinde yeni bir key.snk dosyası oluşturmak için kullanılan adlı bir `ProjectSigningManager` yardımcı sınıftır.|
|SharePoint komutları|Bunlar, sihirbaz çalışırken yerel SharePoint için sihirbaz veri modeli tarafından kullanılan yöntemlerdir. Bu SharePoint 3.5'i .NET Framework gerekir, çünkü bu komutlar sihirbaz kodunun geri kalanından farklı bir derlemede uygulanır.|

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için, Izlenecek Yol: Proje şablonuyla site sütunu proje öğesi oluşturma bölümünde oluşturduğunuz SiteColumnProjectItem çözümüne birkaç proje eklemeniz [gerekir, Bölüm 1:](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)

- WPF projesi. Bu projede <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimini uygulayacak ve sihirbaz kullanıcı arabirimini tanımlayabilirsiniz.

- Uygulama komutlarını tanımlayan bir sınıf SharePoint projesi. Bu proje, the.NET Framework 3.5'i hedeflemeli.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-wpf-project"></a>WPF projesini oluşturmak için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SiteColumnProjectItem çözümünü açın.

2. Bu **Çözüm Gezgini** **SiteColumnProjectItem** çözüm düğümünün kısayol menüsünü açın, Ekle'yi seçin ve ardından Yeni **oluştur'Project.** 

3. Yeni Sürüm Ekle iletişim **Project** üst kısmında, .NET Framework sürüm listesinde **.NET Framework 4.5'in** .NET Framework.

4. Visual **C# düğümünü** veya **Visual Basic** düğümünü genişletin ve **Windows** seçin.

5. Proje şablonları listesinde **WPF** Kullanıcı Denetim Kitaplığı'ı seçin, projeye **ProjectTemplateWizard adını ve** ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ProjectTemplateWizard** projesini çözüme ekler ve varsayılan UserControl1.xaml dosyasını açar.

6. Projeden UserControl1.xaml dosyasını silin.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint komutları projesini oluşturmak için

1. Bu **Çözüm Gezgini** SiteColumnProjectItem çözüm düğümünün kısayol menüsünü açın, Ekle'yi ve ardından Yeni **Oluştur'u Project.**

2. Yeni Uygulama Ekle iletişim **kutusunun Project,** .NET Framework sürümleri **listesinden 3.5'i** .NET Framework.

3. Visual **C# düğümünü** veya **Visual Basic** düğümünü genişletin ve ardından **Windows** seçin.

4. Sınıf Kitaplığı **proje şablonunu** seçin, projeye **SharePointCommands adını ve** ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**SharePointCommands projesini** çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Sihirbazı oluşturmadan önce, projelere bazı kod dosyaları ve derleme başvuruları eklemeniz gerekir.

#### <a name="to-configure-the-wizard-project"></a>Sihirbaz projesini yapılandırmak için

1. Bu **Çözüm Gezgini** **ProjeTemplateWizard** proje düğümü için kısayol menüsünü açın ve Özellikler'i **seçin.**

2. Project **Tasarımcısı'nda,** bir Visual  C# projesinin Uygulama sekmesini  veya bir Visual Basic seçin.

3. Hedef çerçevenin .NET Framework 4.5 İstemci Profili'ne değil .NET Framework 4.5'e ayarlanmış olduğundan emin olun.

     Daha fazla bilgi için, [bkz. How to: Target a Version of the .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

4. **ProjectTemplateWizard projesinin kısayol** menüsünü açın, Ekle'yi **ve** ardından Yeni Öğe'yi **seçin.**

5. Pencere **(WPF) öğesini** seçin, öğeye **SihirbazWindow** adını ve ardından Ekle **düğmesini** seçin.

6. Projeye iki **Kullanıcı Denetimi (WPF)** öğe ekleyin ve bunları **Page1** ve **Page2 olarak adlarına ekleyin.**

7. Projeye dört kod dosyası ekleyin ve aşağıdaki adları ekleyin:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - Commandıds

8. **ProjectTemplateWizard proje** düğümünün kısayol menüsünü açın ve Başvuru **Ekle'yi seçin.**

9. Derlemeler **düğümünü** genişletin, **Uzantılar düğümünü** seçin ve ardından aşağıdaki derlemelerin yanındaki onay kutularını seçin:

    - Envdte

    - Microsoft.visualstudio.ole

    - Microsoft.VisualStudio. SharePoint

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.Shell.Interop.10.0

    - Microsoft.VisualStudio.Shell.Interop.11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

10. Derlemeleri  projeye eklemek için Tamam düğmesini seçin.

11. Bu **Çözüm Gezgini,** **ProjectTemplateWizard** projesinin Başvurular klasörünün altında **EnvDTE'yi seçin.** 

12. Özellikler **penceresinde** Birlikte Çalışma Türleri Ekle **özelliğinin değerini** False olarak **değiştirin.**

13. Bir Visual Basic projesi geliştiriyorsanız, Project Designer'ı kullanarak ProjeTemplateWizard ad **alanını projenize aktarın.**

     Daha fazla bilgi için, [bkz. How to: Add or Remove Imported Namespaces &#40;Visual Basic&#41;. ](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointcommands projesini yapılandırmak için

1. Bu **Çözüm Gezgini** **SharePointCommands proje düğümünü** seçin.

2. Menü çubuğunda , Var Olan **Öğeyi Project** **seçeneğini belirleyin.**

3. Var **Olan Öğeyi Ekle** iletişim kutusunda ProjectTemplateWizard projesinin kod dosyalarını içeren klasöre göz atarak **CommandIds** kod dosyasını seçin.

4. Ekle düğmesinin yanındaki **oku** seçin ve ardından görüntülenen **menüden** Farklı Ekle Bağlantısı seçeneğini belirleyin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , kod dosyasını **SharePointCommands projesine** bir bağlantı olarak ekler. Kod dosyası **ProjectTemplateWizard** projesinde bulunur, ancak dosyanın kodu **SharePointCommands projesinde de derlenmiş** olur.

5. **SharePointCommands projesine** Commands adlı başka bir kod dosyası ekleyin.

6. SharePointCommands projesini seçin ve ardından menü çubuğunda Başvuru **Ekle'Project**  >  **seçin.**

7. Derlemeler **düğümünü** genişletin, **Uzantılar düğümünü** seçin ve ardından aşağıdaki derlemelerin yanındaki onay kutularını seçin:

    - Microsoft. SharePoint

    - Microsoft.VisualStudio. SharePoint. Komut

8. Derlemeleri  projeye eklemek için Tamam düğmesini seçin.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Sihirbaz modeli, imzalama yöneticisi ve SharePoint kimlikleri oluşturma
 Örnekte aşağıdaki bileşenleri uygulamak için ProjectTemplateWizard projesine kod ekleyin:

- Komut SharePoint kimlikleri. Bu dizeler, sihirbazın SharePoint komutlarını tanımlamak için kullanılır. Bu kılavuzda daha sonra, komutları uygulamak için SharePointCommands projesine kod ekleneceksiniz.

- Sihirbaz veri modeli.

- Proje imzalama yöneticisi.

  Bu bileşenler hakkında daha fazla bilgi için [bkz. Sihirbaz bileşenlerini anlama.](#understand-the-wizard-components)

#### <a name="to-define-the-sharepoint-command-ids"></a>Komut kimliklerini SharePoint için

1. ProjectTemplateWizard projesinde CommandIds kod dosyasını açın ve ardından bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb" id="Snippet5":::

#### <a name="to-create-the-wizard-model"></a>Sihirbaz modelini oluşturmak için

1. SiteColumnWizardModel kod dosyasını açın ve bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs" id="Snippet6":::

#### <a name="to-create-the-project-signing-manager"></a>Proje imzalama yöneticisini oluşturmak için

1. ProjectSigningManager kod dosyasını açın ve ardından bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb" id="Snippet8":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs" id="Snippet8":::

## <a name="create-the-wizard-ui"></a>Sihirbaz kullanıcı arabirimini oluşturma
 Sihirbaz penceresinin kullanıcı arabirimini ve sihirbaz sayfaları için kullanıcı arabirimini sağlayan iki kullanıcı denetimi tanımlamak için XAML ekleyin ve pencerenin ve kullanıcı denetimlerinin davranışını tanımlamak için kod ekleyin. Sizin oluşturyruz sihirbaz, SharePoint'daki projelerin yerleşik sihirbazına Visual Studio.

> [!NOTE]
> Aşağıdaki adımlarda, projenize XAML veya kod ekledikten sonra projeniz bazı derleme hatalarına sahip olur. Sonraki adımlarda kod eklerken bu hatalar gider.

#### <a name="to-create-the-wizard-window-ui"></a>Sihirbaz penceresi kullanıcı arabirimini oluşturmak için

1. ProjectTemplateWizard projesinde WizardWindow.xaml dosyasının kısayol menüsünü açın ve  ardından Aç'ı seçerek pencereyi tasarımcıda açın.

2. Tasarımcının XAML görünümünde geçerli XAML'i aşağıdaki XAML ile değiştirin. XAML, başlığı, sihirbaz sayfalarını içeren bir kullanıcı arabirimini ve pencerenin alt kısmında gezinti <xref:System.Windows.Controls.Grid> düğmelerini içeren bir kullanıcı arabirimi tanımlar.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml" id="Snippet10":::

    > [!NOTE]
    > Bu XAML'de oluşturulan pencere temel sınıftan <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> türetildi. Visual Studio'a özel bir WPF iletişim kutusu eklerken, diğer Visual Studio iletişim kutularıyla tutarlı stile sahip olmak ve aksi halde ortaya çıkabilir kalıcı iletişim kutusu sorunlarını önlemek için iletişim kutusunu bu sınıftan türetmenizi öneririz. Daha fazla bilgi için [bkz. Kalıcı İletişim Kutuları Oluşturma ve Yönetme.](../extensibility/creating-and-managing-modal-dialog-boxes.md)

3. Bir Visual Basic projesi geliştiriyorsanız, `ProjectTemplateWizard` öğenin `WizardWindow` özniteliğinde sınıf `x:Class` adı'dan ad alanını `Window` kaldırın. Bu öğe XAML'nin ilk satırıdır. Bitirin, ilk satır aşağıdaki örnekteki gibi gelsin.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow.xaml dosyasının arka arkasındaki kod dosyasını açın.

5. Dosyanın üst kısmında yer alan bildirim dışındaki bu dosyanın içeriğini `using` aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs" id="Snippet4":::

#### <a name="to-create-the-first-wizard-page-ui"></a>İlk sihirbaz sayfası kullanıcı arabirimini oluşturmak için

1. ProjectTemplateWizard projesinde Page1.xaml dosyasının kısayol menüsünü açın ve  ardından Aç'ı seçerek kullanıcı denetimi tasarımcıda açın.

2. Tasarımcının XAML görünümünde geçerli XAML'i aşağıdaki XAML ile değiştirin. XAML, kullanıcıların hata ayıklama için kullanmak istediğiniz yerel sitelerin URL'sini girebilirsiniz metin kutusu içeren bir kullanıcı arabirimi tanımlar. Kullanıcı arabirimi, kullanıcıların projenin korumalı alan olarak kabul edip olmadığını belirte seçen düğmelerini de içerir.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml" id="Snippet11":::

3. Bir Visual Basic projesi geliştiriyorsanız, `ProjectTemplateWizard` öğenin `Page1` özniteliğinde sınıf `x:Class` adı'dan ad alanını `UserControl` kaldırın. Bu, XAML'nin ilk satırıdır. Bitirin, ilk satır aşağıdaki gibi görünüyor.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Page1.xaml dosyasının içeriğini, dosyanın üst kısmında yer alan bildirim `using` dışında aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs" id="Snippet2":::

#### <a name="to-create-the-second-wizard-page-ui"></a>İkinci sihirbaz sayfası kullanıcı arabirimini oluşturmak için

1. ProjectTemplateWizard projesinde Page2.xaml dosyasının kısayol menüsünü açın ve aç'ı **seçin.**

     Kullanıcı denetimi tasarımcıda açılır.

2. XAML görünümünde geçerli XAML'i aşağıdaki XAML ile değiştirin. XAML, site sütunlarının temel türünü seçmek için açılan liste, galeride site sütununu görüntülemek üzere yerleşik veya özel bir grup belirtmeye yönelik birleşik giriş kutusu ve site sütunlarının adını belirtmek için bir metin kutusu içeren bir kullanıcı arabirimi tanımlar.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml" id="Snippet12":::

3. Bir Visual Basic projesi geliştiriyorsanız, `ProjectTemplateWizard` öğenin `Page2` özniteliğinde sınıf `x:Class` adı'dan ad alanını `UserControl` kaldırın. Bu, XAML'nin ilk satırıdır. Bitirin, ilk satır aşağıdaki gibi görünüyor.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Page2.xaml dosyasının arka arkasındaki kod dosyasının içeriğini, dosyanın üst kısmında yer alan bildirim dışında `using` aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs" id="Snippet3":::

## <a name="implement-the-wizard"></a>Sihirbazı uygulama
 Arabirimini kullanarak sihirbazın ana işlevselliğini <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> tanımlayın. Bu arabirim, sihirbaz başlatıldığında Visual Studio ve sihirbaz çalışırken belirli zamanlarda çağıran yöntemleri tanımlar.

#### <a name="to-implement-the-wizard"></a>Sihirbazı uygulamak için

1. ProjectTemplateWizard projesinde SiteColumnProjectWizard kod dosyasını açın.

2. Bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs" id="Snippet7":::

## <a name="create-the-sharepoint-commands"></a>SharePoint oluşturma
 Sunucu nesne modeline çağrı SharePoint özel komut oluşturun. Bir komut, kullanıcının sihirbazda türetir site URL'si geçerli olup olmadığını belirler. Diğer komut, kullanıcıların yeni site sütunu için temel olarak hangi SharePoint seçeleri için belirtilen siteden tüm alan türlerini alır.

#### <a name="to-define-the-sharepoint-commands"></a>Komutlarını tanımlamak SharePoint için

1. **SharePointCommands projesinde** Komutlar kod dosyasını açın.

2. Bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb" id="Snippet9":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs" id="Snippet9":::

## <a name="checkpoint"></a>Checkpoint
 Kılavuzda bu noktada, sihirbazın tüm kodu artık projededir. Hatasız derlenmiş olduğundan emin olmak için projeyi derle.

#### <a name="to-build-your-project"></a>Projenizi derlemek için

1. Menü çubuğunda Derleme   >  **Çözümü'ne tıklayın.**

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Proje şablonundan key.snk dosyasını kaldırma
 Kılavuz: Proje şablonu olan [1.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)Bölüm ile bir site sütunu proje öğesi oluşturma bölümünde, oluşturduğunuz proje şablonu her Site Sütunu proje örneğini imzalamak için kullanılan bir key.snk dosyası içerir. Sihirbaz artık her proje için yeni bir key.snk dosyası oluştur olduğundan bu key.snk dosyası artık gerekli değildir. proje şablonundan key.snk dosyasını kaldırın ve bu dosyaya yapılan başvuruları kaldırın.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Key.snk dosyasını proje şablonundan kaldırmak için

1. Bu **Çözüm Gezgini** **SiteColumnProjectTemplate** düğümünün altında **key.snk** dosyasının kısayol menüsünü açın ve Sil'i **seçin.**

2. Görüntülenen onay iletişim kutusunda Tamam **düğmesini** seçin.

3. **SiteColumnProjectTemplate** düğümü altında SiteColumnProjectTemplate.vstemplate dosyasını açın ve ardından bundan aşağıdaki öğeyi kaldırın.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Dosyayı kaydedin ve kapatın.

5. **SiteColumnProjectTemplate** düğümünün altında ProjectTemplate.csproj veya ProjectTemplate.vbproj dosyasını açın ve ardından bundan `PropertyGroup` aşağıdaki öğeyi kaldırın.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Aşağıdaki öğeyi `None` kaldırın.

    ```xml
    <None Include="key.snk" />
    ```

7. Dosyayı kaydedin ve kapatın.

## <a name="associating-the-wizard-with-the-project-template"></a>Sihirbazı proje şablonuyla birlikte kullanma
 Sihirbazı uygulamaya başladınız, artık sihirbazı Site Sütunu proje **şablonuyla ilişkilendirmeniz** gerekir. Bunu yapmak için tamamlamanız gereken üç yordam vardır:

1. Sihirbaz derlemeyi bir güçlü adla imzalar.

2. Sihirbaz derlemesi için ortak anahtar belirteci alın.

3. Site Sütunu proje şablonu için .vstemplate dosyasında sihirbaz derlemesi **için bir** başvuru ekleyin.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Sihirbaz derlemeyi güçlü bir adla imzalamak için

1. Bu **Çözüm Gezgini** projesinde **ProjectTemplateWizard projesinin kısayol** menüsünü açın ve Özellikler'i **seçin.**

2. İmzalama **sekmesinde** Derlemeyi **imzala onay** kutusunu seçin.

3. Bir **güçlü ad anahtar dosyası seçin listesinde'yi** **\<New...>** seçin.

4. Güçlü **Ad Anahtarı Oluştur** iletişim kutusunda yeni anahtar dosyası için  bir ad girin, Anahtar dosyamı parolayla koru onay kutusunun işaretini kaldırın ve ardından Tamam **düğmesini** seçin.

5. **ProjectTemplateWizard projesinin kısayol** menüsünü açın ve derleme dosyasını oluşturmak **için** Oluştur'ProjectTemplateWizard.dll seçin.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Sihirbaz derlemesi için ortak anahtar belirteci almak için

1. Başlat Menüsünde Tüm  **Programlar'ı** seçin, Microsoft Visual Studio' **Visual Studio Araçları** **seçin** ve **Geliştirici Komut İstemi.**

     Bir Visual Studio komut istemi penceresi açılır.

2. Aşağıdaki komutu çalıştırın ve *PathToWizardAssembly* yerine geliştirme bilgisayarınızda ProjectTemplateWizard projesi için ProjectTemplateWizard.dll derlemenin tam yolunu yazın:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     ProjectTemplateWizard.dll derlemesi için ortak anahtar belirteci, Visual Studio istemi penceresine yazılır.

3. Visual Studio İstemi penceresini açık tutma. Sonraki yordam sırasında ortak anahtar belirtecin gerekir.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.vstemplate dosyasında sihirbaz derlemesi için başvuru eklemek için

1. Bu **Çözüm Gezgini** **SiteColumnProjectTemplate** proje düğümünü genişletin ve SiteColumnProjectTemplate.vstemplate dosyasını açın.

2. Dosyanın sonuna yakın bir yerde ve etiketleri `WizardExtension` arasına aşağıdaki `</TemplateContent>` öğeyi `</VSTemplate>` ekleyin. özniteliğinin *belirteç* `PublicKeyToken` değerini, önceki yordamda edinilen ortak anahtar belirteci ile değiştirin.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     öğesi hakkında daha fazla bilgi `WizardExtension` için bkz. [WizardExtension Öğesi &#40;Visual Studio Şablonları&#41;. ](../extensibility/wizardextension-element-visual-studio-templates.md)

3. Dosyayı kaydedin ve kapatın.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Proje şablonunda Elements.xml parametresi ekleme
 SiteColumnProjectTemplate projesindeElements.xmlbirçok değiştirilebilir parametre ekleyin.  Bu parametreler, daha önce `RunStarted` tanımlandığı `SiteColumnProjectWizard` sınıftaki yönteminde başlatılır. Bir kullanıcı bir Site Sütunu projesi oluşturduğunda, Visual Studio yeni projede yer alan *Elements.xml* bu parametreleri sihirbazda belirtilen değerlerle otomatik olarak değiştirir.

 Değiştirilebilir parametre, dolar işareti ($) karakteriyle başlayan ve sona eren bir belirteçtir. Kendi değiştirilebilir parametrelerinizi tanımlamaya ek olarak, proje sistemi tarafından tanımlanan ve başlatılan yerleşik SharePoint kullanabilirsiniz. Daha fazla bilgi için [bkz. Değiştirilebilir parametreler.](../sharepoint/replaceable-parameters.md)

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Elements.xml dosyasına değiştirilebilir parametreler eklemek için

1. SiteColumnProjectTemplate projesinde, *Elements.xml* dosyasının içeriğini aşağıdaki XML ile değiştirin.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     Yeni XML, ve özniteliklerini özel `Name` `DisplayName` `Type` `Group` değiştirilebilir parametrelerle değiştirir.

2. Dosyayı kaydedin ve kapatın.

## <a name="add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSIX paketine ekleme
 Sihirbazı Site Sütunu proje şablonunu içeren VSIX paketiyle dağıtmak için, vsIX projesinde source.extension.vsixmanifest dosyasına sihirbaz projesine ve SharePoint komutları projesine başvurular ekleyin.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSIX paketine eklemek için

1. Bu **Çözüm Gezgini** **SiteColumnProjectItem** projesinde **source.extension.vsixmanifest** dosyasının kısayol menüsünü açın ve aç'ı **seçin.**

     Visual Studio bildirim düzenleyicisinde açılır.

2. Düzenleyicinin  Varlıklar sekmesinde Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu açılır.

3. Tür **listesinde** **Microsoft.VisualStudio.Assembly'i seçin.**

4. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

5. Yeni **Project** **ProjectTemplateWizard'ı ve** ardından Tamam **düğmesini** seçin.

6. Düzenleyicinin **Varlıklar** sekmesinde Yeni düğmesini **yeniden** seçin.

     Yeni **Varlık Ekle iletişim** kutusu açılır.

7. Tür **listesine** **SharePoint. Commands.v4**.

8. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

9. İlk **Project** **SharePointCommands projesini** ve ardından Tamam **düğmesini** seçin.

10. Menü çubuğunda Derleme   >  **Çözümü'yü seçin** ve çözümün hatasız olarak derlemeye devam edin.

## <a name="test-the-wizard"></a>Sihirbazı test etme
 Artık sihirbazı test etmeye hazırsınız. İlk olarak, Visual Studio'nin deneysel örneğinde SiteColumnProjectItem çözümünde hata ayıklamaya Visual Studio. Ardından, sitenin deneysel örneğinde Site Sütunu projesinin sihirbazını Visual Studio. Son olarak, site sütununu beklendiği gibi çalıştığını doğrulamak için projeyi derleme ve çalıştırma.

#### <a name="to-start-debugging-the-solution"></a>Çözümde hata ayıklamaya başlamak için

1. Yönetici Visual Studio ile yeniden başlatın ve ardından SiteColumnProjectItem çözümünü açın.

2. ProjectTemplateWizard projesinde SiteColumnProjectWizard kod dosyasını açın ve ardından yönteminde ilk kod satırına bir kesme noktası `RunStarted` ekleyin.

3. Menü çubuğunda Özel Durumlarda **Hata Ayıkla'ya**  >  **tıklayın.**

4. Özel **Durumlar iletişim** kutusunda, Ortak Dil Çalışma Zamanı Özel Durumları için  Thrown ve **User tarafından** işsiz onay **kutularının** temiz olduğundan emin olun ve ardından **Tamam düğmesini** seçin.

5. **F5** anahtarını veya menü çubuğunda Hata AyıklamaYı Başlat'ı **seçerek hata**  >  **ayıklamayı başlatabilirsiniz.**

     Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 uzantısını yüklüp deneysel bir Visual Studio. Proje öğesini bu örnek içinde test Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Sihirbazı test etmek için Visual Studio

1. Deneysel Visual Studio örneğinde, menü çubuğunda Dosya Yeni Dosya'Project.  >    >  

2. Visual **C# düğümünü** **veya Visual Basic** düğümünü genişletin (proje şablonunuz tarafından kullanılan dile bağlı olarak), **SharePoint** düğümünü genişletin ve **ardından 2010 düğümünü** seçin.

3. Proje şablonları listesinde Site Sütunu'na **tıklayın,** projeye **SiteColumnWizardTest adını ve** ardından Tamam **düğmesini** seçin.

4. Uygulamanın diğer örneğinde yer alan kodun Visual Studio daha önce yönteminde ayar güvenlik kesme noktası üzerinde durduğu `RunStarted` doğrulayın.

5. **F5** anahtarını seçerek veya menü çubuğunda Devam'da Hata Ayıkla'ya seçerek projede **hata ayıklamaya**  >  **devam eder.**

6. SharePoint **Özelleştirme** Sihirbazı'nda, hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin ve ardından Sonraki **düğmesini** seçin.

7. Özelleştirme Sihirbazı'nın **SharePoint sayfasında** aşağıdaki seçimleri yapın:

   - Tür **listesinde** **Boolean'ı seçin.**

   - Grup listesinde **Özel** **Evet/Sütun Yok'a tıklayın.**

   - Ad **kutusuna** **Evet/Hayır Sütunum yazın** ve son **düğmesini** seçin.

     Bu **Çözüm Gezgini,** yeni bir proje görünür ve **Alan1** adlı bir proje öğesi içerir ve Visual Studio projeninElements.xml *dosyasını* düzenleyicide açar.

8. Bu *Elements.xml* sihirbazda belirttiğiniz değerleri içerdiğini doğrulayın.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Site sütununu test etmek için SharePoint

1. Deneysel Visual Studio **F5 anahtarını** seçin.

     Site sütunu, projenin Site URL'si özelliğinin SharePoint **site** için paketli ve dağıtılmıştır. Web tarayıcısı bu sitenin varsayılan sayfasını açar.

    > [!NOTE]
    > Betik **Hata Ayıklama Devre Dışı** iletişim kutusu görüntülenirse projede **hata** ayıklamaya devam etmek için Evet düğmesini seçin.

2. Site Eylemleri **menüsünde Site** **eylemleri'Ayarlar.**

3. Site Sütunları Ayarlar Galeriler'in altında Site sütunları **bağlantısını** seçin.

4. Site sütunları listesinde, Özel **Evet/Hayır** Sütunları grubunun **Evet/Hayır** Sütunum adlı bir sütun içerdiğini doğrulayın ve ardından web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizleme
 Proje öğesini test etme tamam olduktan sonra, proje şablonunu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizlemek için

1. Deneysel Visual Studio menü çubuğunda Araçlar Uzantıları ve   >  **Güncelleştirmeler'i seçin.**

     Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

2. Uzantı listesinde Site Sütunu'na **ve** ardından Kaldır **düğmesini** seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı  kaldırmak istediğinizden emin olmak için Evet düğmesini  seçin ve ardından kaldırma işlemini tamamlamak için Şimdi Yeniden Başlat düğmesini seçin.

4. Hem deneysel Visual Studio hem de CustomActionProjectItem çözümünün açık olduğu örneği kapatın.

     Uzantıları dağıtma hakkında bilgi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] için bkz. [Gönderim Visual Studio uzantıları.](../extensibility/shipping-visual-studio-extensions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: Proje şablonuyla site sütunu proje öğesi oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Özel proje SharePoint türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint Proje Öğeleri için Öğe Şablonları ve Proje Şablonları Oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
