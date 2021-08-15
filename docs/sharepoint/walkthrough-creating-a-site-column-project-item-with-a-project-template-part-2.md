---
title: Proje şablonu, bölüm 2 ile site sütunu proje öğesi oluşturma
titleSuffix: ''
description: Proje öğesini içeren bir proje oluşturmak üzere şablonu kullanan kullanıcılardan veri toplamak için bir site sütunu proje şablonuna SharePoint sihirbazı ekleyin.
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
  Bir proje öğesi için özel SharePoint tanımladığınız ve bunu Visual Studio proje şablonuyla ilişkilendirmeniz sonrasında, şablon için bir sihirbaz sağlamak da iyi olabilir. Proje öğesini içeren yeni bir proje oluşturmak üzere şablonlarınızı kullanan kullanıcılardan bilgi toplamak için sihirbazı kullanabilirsiniz. Toplayan bilgiler proje öğesini başlatmak için kullanılabilir.

 Bu kılavuzda, Site Sütunu proje şablonuna kılavuz: Site Sütunu Project Öğesi Oluşturma bölümünde Project [Şablonu, Bölüm 1'de gösteren bir sihirbaz eklenecektir.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md) Kullanıcı bir Site Sütunu projesi oluşturduğunda sihirbaz, site sütunu (temel türü ve grubu gibi) hakkında bilgi toplar ve bu bilgileri *yeni projedeElements.xml* dosyasına ekler.

 Bu kılavuz aşağıdaki görevleri gösterir:

- Özel bir proje şablonu SharePoint bir proje şablonuyla ilişkili proje öğesi türü için sihirbaz oluşturma.

- SharePoint projelerinde yerleşik sihirbazlara benzeyen özel bir sihirbaz kullanıcı arabirimi Visual Studio.

- Sihirbaz *SharePoint yerel* siteye çağrı yapmak için kullanılan iki SharePoint komut oluşturma. SharePoint komutları, Visual Studio sunucu nesne modelinde API'leri SharePoint kullanılan yöntemlerdir. Daha fazla bilgi için [bkz. nesne SharePoint çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

- Proje dosyalarını sihirbazda toplayan SharePoint başlatmak için değiştirilebilir parametreleri kullanma.

- Her yeni Site Sütunu proje örneğinde yeni bir .snk dosyası oluşturma. Bu dosya, çözüm derlemesini genel derleme önbelleğine SharePoint proje çıktısını imzalamak için kullanılır.

- Sihirbazda hata ayıklama ve test etme.

> [!NOTE]
> Bir dizi örnek iş akışı için bkz. [SharePoint örnekleri.](/sharepoint/dev/general-development/sharepoint-workflow-samples)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu gerçekleştirmek için öncelikle Adım Adım: Bir Site Sütunu Project Project Öğesi Oluşturma, [Bölüm 1'i](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)tamamlayarak SiteColumnProjectItem çözümünü oluşturmanız gerekir.

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

2. Bu **Çözüm Gezgini,** **SiteColumnProjectItem** çözüm düğümü için kısayol menüsünü açın, Ekle'yi seçin ve ardından Yeni **oluştur'Project.**

3. Yeni Sürüm Ekle iletişim **Project** üst kısmında, .NET Framework sürüm listesinde **.NET Framework 4.5'in** .NET Framework.

4. Visual **C# düğümünü** veya **Visual Basic** düğümünü genişletin ve **Windows** seçin.

5. Proje şablonları listesinde **WPF** Kullanıcı Denetim Kitaplığı'ı seçin, projeye **ProjectTemplateWizard adını ve** ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ProjectTemplateWizard** projesini çözüme ekler ve varsayılan UserControl1.xaml dosyasını açar.

6. Projeden UserControl1.xaml dosyasını silin.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint komutları projesini oluşturmak için

1. Bu **Çözüm Gezgini,** SiteColumnProjectItem çözüm düğümü için kısayol menüsünü açın, Ekle'yi **seçin** ve ardından Yeni **Oluştur'Project.**

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

4. **ProjectTemplateWizard projesinin kısayol** menüsünü açın, Ekle'yi **ve** ardından Yeni **Öğe'yi seçin.**

5. Pencere **(WPF) öğesini** seçin, öğeye **SihirbazWindow** adını ve ardından Ekle **düğmesini** seçin.

6. Projeye iki **Kullanıcı Denetimi (WPF)** öğe ekleyin ve bunları **Page1** ve **Page2 olarak adlarına ekleyin.**

7. Projeye dört kod dosyası ekleyin ve aşağıdaki adları ekleyin:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - Commandıds

8. **ProjectTemplateWizard proje düğümünün kısayol** menüsünü açın ve Başvuru Ekle'yi **seçin.**

9. Derlemeler **düğümünü** genişletin, **Uzantılar düğümünü** seçin ve ardından aşağıdaki derlemelerin yanındaki onay kutularını seçin:

    - Envdte

    - Microsoft.visualstudio.ole

    - Microsoft.VisualStudio. SharePoint

    - Microsoft.VisualStudio.Shell.11.0

    - Microsoft.VisualStudio.Shell.Interop.10.0

    - Microsoft.VisualStudio.Shell.Interop.11.0

    - Microsoft. VisualStudio. TemplateWizardInterface

10. Derlemeleri projeye eklemek için **Tamam** düğmesini seçin.

11. **Çözüm Gezgini**, **ProjectTemplateWizard** projesi Için **Başvurular** klasörü altında **EnvDTE** öğesini seçin.

12. **Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğinin değerini **false** olarak değiştirin.

13. bir Visual Basic projesi geliştiriyorsanız, **Project tasarımcısını** kullanarak projecttemplatewizard ad alanını projenize aktarın.

     daha fazla bilgi için bkz. [nasıl yapılır: içeri aktarılan ad alanlarını ekleme veya kaldırma &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointcommands projesini yapılandırmak için

1. **Çözüm Gezgini**, **SharePointCommands** proje düğümünü seçin.

2. menü çubuğunda **Project**, **var olan öğeyi ekle** öğesini seçin.

3. **Varolan öğe Ekle** iletişim kutusunda, ProjectTemplateWizard projesi için kod dosyalarını içeren klasöre gidin ve ardından **CommandIds** kod dosyasını seçin.

4. **Ekle** düğmesinin yanındaki oku seçin ve ardından görüntülenen menüdeki **bağlantı olarak ekle** seçeneğini belirleyin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir bağlantı olarak **SharePointCommands** projesine kod dosyasını ekler. Kod dosyası **ProjectTemplateWizard** projesinde bulunur, ancak dosyadaki kod de **SharePointCommands** projesinde derlenir.

5. **SharePointCommands** projesinde komutları adlı başka bir kod dosyası ekleyin.

6. sharepointcommands projesini seçin ve ardından menü çubuğunda **Project**  >  **başvuru ekle**' yi seçin.

7. **Derlemeler** düğümünü genişletin, **Uzantılar** düğümünü seçin ve ardından aşağıdaki derlemelerin yanındaki onay kutularını seçin:

    - MICROSOFT. SharePoint

    - Microsoft. VisualStudio. SharePoint. Komut

8. Derlemeleri projeye eklemek için **Tamam** düğmesini seçin.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>sihirbaz modeli, imzalama yöneticisi ve SharePoint komut kimliklerini oluşturma
 Örnek içinde aşağıdaki bileşenleri uygulamak için ProjectTemplateWizard projesine kod ekleyin:

- SharePoint komut kimlikleri. bu dizeler, sihirbazın kullandığı SharePoint komutlarını belirler. Bu izlenecek yolda daha sonra, komutları uygulamak için SharePointCommands projesine kod ekleyeceksiniz.

- Sihirbaz veri modeli.

- Proje imzalama Yöneticisi.

  Bu bileşenler hakkında daha fazla bilgi için bkz. [sihirbaz bileşenlerini anlama](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>SharePoint komut kimliklerini tanımlamak için

1. ProjectTemplateWizard projesinde CommandIds kod dosyasını açın ve ardından bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb" id="Snippet5":::

#### <a name="to-create-the-wizard-model"></a>Sihirbaz modeli oluşturmak için

1. SiteColumnWizardModel kod dosyasını açın ve bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs" id="Snippet6":::

#### <a name="to-create-the-project-signing-manager"></a>Proje imzalama yöneticisini oluşturmak için

1. ProjectSigningManager kod dosyasını açın ve ardından bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb" id="Snippet8":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs" id="Snippet8":::

## <a name="create-the-wizard-ui"></a>Sihirbaz kullanıcı arabirimini oluşturma
 Sihirbaz penceresinin Kullanıcı arabirimini ve sihirbaz sayfalarına yönelik Kullanıcı ARABIRIMINI sağlayan iki kullanıcı denetimini tanımlamak için XAML ekleyin ve pencere ve Kullanıcı denetimlerinin davranışını tanımlamak için kod ekleyin. oluşturduğunuz sihirbaz, Visual Studio SharePoint projeler için yerleşik sihirbaza benzer.

> [!NOTE]
> Aşağıdaki adımlarda, projenize XAML veya kod ekledikten sonra projenizin bazı derleme hataları olacaktır. Sonraki adımlarda kod eklediğinizde bu hatalar kaybolur.

#### <a name="to-create-the-wizard-window-ui"></a>Sihirbaz penceresi Kullanıcı arabirimini oluşturmak için

1. ProjectTemplateWizard projesinde, WizardWindow. xaml dosyası için kısayol menüsünü açın ve ardından **Aç** ' ı seçerek pencereyi tasarımcıda açın.

2. Tasarımcının XAML görünümünde, geçerli XAML 'yi aşağıdaki XAML ile değiştirin. XAML, <xref:System.Windows.Controls.Grid> pencerenin alt kısmındaki Sihirbaz sayfalarını ve gezinti düğmelerini içeren bir başlık içeren bir kullanıcı arabirimi tanımlar.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml" id="Snippet10":::

    > [!NOTE]
    > Bu XAML 'de oluşturulan pencere, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> temel sınıftan türetilir. Visual Studio için özel bir WPF iletişim kutusu eklediğinizde, iletişim kutusunu bu sınıftan türetebilirsiniz ve diğer Visual Studio iletişim kutularıyla tutarlı bir stil elde edebilir ve aksi takdirde oluşabilecek kalıcı iletişim sorunlarından kaçınabilirsiniz. Daha fazla bilgi için bkz. [kalıcı Iletişim kutuları oluşturma ve yönetme](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Visual Basic bir proje geliştiriyorsanız, `ProjectTemplateWizard` ad alanını `WizardWindow` öğenin özniteliğinde sınıf adından kaldırın `x:Class` `Window` . Bu öğe, XAML 'in ilk satıröğesidir. İşiniz bittiğinde, ilk satır aşağıdaki örnekteki gibi görünmelidir.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow. xaml dosyası için arka plan kod dosyasını açın.

5. Dosyanın üst kısmındaki bildirimler hariç, bu dosyanın içeriğini `using` aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs" id="Snippet4":::

#### <a name="to-create-the-first-wizard-page-ui"></a>İlk sihirbaz sayfası kullanıcı arabirimini oluşturmak için

1. ProjectTemplateWizard projesinde, Sayfa1. xaml dosyası için kısayol menüsünü açın ve sonra tasarımcıda Kullanıcı denetimini açmak için **Aç** ' ı seçin.

2. Tasarımcının XAML görünümünde, geçerli XAML 'yi aşağıdaki XAML ile değiştirin. XAML, kullanıcıların hata ayıklama için kullanmak istedikleri yerel sitelerin URL 'sini girebilecekleri bir metin kutusu içeren bir kullanıcı arabirimi tanımlar. Kullanıcı arabirimi, kullanıcıların projenin korumalı olup olmadığını belirleyebileceği seçenek düğmelerini de içerir.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml" id="Snippet11":::

3. Visual Basic bir proje geliştiriyorsanız, `ProjectTemplateWizard` ad alanını `Page1` öğenin özniteliğinde sınıf adından kaldırın `x:Class` `UserControl` . Bu, XAML 'in ilk satırdır. İşiniz bittiğinde, ilk satır aşağıdaki gibi görünmelidir.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. `using`Aşağıdaki kodla, dosyanın en üstündeki bildirimler hariç, Sayfa1. xaml dosyasının içeriğini değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs" id="Snippet2":::

#### <a name="to-create-the-second-wizard-page-ui"></a>İkinci sihirbaz sayfası kullanıcı arabirimini oluşturmak için

1. ProjectTemplateWizard projesinde, Page2. xaml dosyası için kısayol menüsünü açın ve **Aç** öğesini seçin.

     Kullanıcı denetimi tasarımcıda açılır.

2. XAML görünümünde, geçerli XAML 'yi aşağıdaki XAML ile değiştirin. XAML, site sütununun temel türünü seçmek için açılan bir liste, galeride site sütununun görüntüleneceği bir yerleşik veya özel grup belirtmeye yönelik bir açılan kutu ve site sütununun adını belirtmek için bir metin kutusu içeren bir kullanıcı arabirimi tanımlar.

     :::code language="xml" source="../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml" id="Snippet12":::

3. Visual Basic bir proje geliştiriyorsanız, `ProjectTemplateWizard` ad alanını `Page2` öğenin özniteliğinde sınıf adından kaldırın `x:Class` `UserControl` . Bu, XAML 'in ilk satırdır. İşiniz bittiğinde, ilk satır aşağıdaki gibi görünmelidir.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Page2. xaml dosyası için arka plan kod dosyasının içeriğini, `using` dosyanın en üstündeki bildirimler dışında, aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs" id="Snippet3":::

## <a name="implement-the-wizard"></a>Sihirbazı uygulama
 Arabirimi uygulayarak sihirbazın ana işlevlerini tanımlayın <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . bu arabirim, sihirbaz başlatıldığında ve tamamlandığında ve sihirbaz çalışırken belirli zamanlarda Visual Studio çağıran yöntemleri tanımlar.

#### <a name="to-implement-the-wizard"></a>Sihirbazı uygulamak için

1. ProjectTemplateWizard projesinde SiteColumnProjectWizard kod dosyasını açın.

2. Bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs" id="Snippet7":::

## <a name="create-the-sharepoint-commands"></a>SharePoint komutlarını oluşturma
 SharePoint server nesne modeline çağıran iki özel komut oluşturun. Bir komut, sihirbazda Kullanıcı türlerindeki site URL 'sinin geçerli olup olmadığını belirler. diğer komut, kullanıcıların yeni site sütunları için temel olarak hangisini kullanacağınızı seçmesini sağlamak için, belirtilen SharePoint sitesindeki tüm alan türlerini alır.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint komutlarını tanımlamak için

1. **SharePointCommands** projesinde, komutlar kod dosyasını açın.

2. Bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb" id="Snippet9":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs" id="Snippet9":::

## <a name="checkpoint"></a>Checkpoint
 Bu noktada, sihirbazın tüm kodu artık projede bulunur. Hata olmadan derlendiğinden emin olmak için projeyi derleyin.

#### <a name="to-build-your-project"></a>Projenizi derlemek için

1. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Anahtar. snk dosyasını proje şablonundan kaldırma
 [Izlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu oluşturun](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), oluşturduğunuz proje şablonu, her site sütunu proje örneğini imzalamak için kullanılan bir Key. snk dosyası içerir. Sihirbaz artık her proje için yeni bir Key. snk dosyası oluşturduğundan, bu Key. snk dosyası artık gerekli değildir. Anahtar. snk dosyasını proje şablonundan kaldırın ve bu dosyaya başvuruları kaldırın.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Anahtar. snk dosyasını proje şablonundan kaldırmak için

1. **Çözüm Gezgini**, **SiteColumnProjectTemplate** düğümünün altında **Key. snk** dosyasının kısayol menüsünü açın ve **Sil**' i seçin.

2. Görüntülenen onay iletişim kutusunda **Tamam** düğmesini seçin.

3. **SiteColumnProjectTemplate** düğümü altında, SiteColumnProjectTemplate. vstemplate dosyasını açın ve bundan sonra aşağıdaki öğeyi kaldırın.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Dosyayı kaydedin ve kapatın.

5. **SiteColumnProjectTemplate** düğümü altında ProjectTemplate. csproj veya ProjectTemplate. vbproj dosyasını açın ve bundan sonra aşağıdaki `PropertyGroup` öğeyi kaldırın.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Aşağıdaki öğeyi kaldırın `None` .

    ```xml
    <None Include="key.snk" />
    ```

7. Dosyayı kaydedin ve kapatın.

## <a name="associating-the-wizard-with-the-project-template"></a>Sihirbazı proje şablonuyla ilişkilendirme
 Sihirbazı uyguladığınıza göre, Sihirbazı **site sütunu** proje şablonuyla ilişkilendirmeniz gerekir. Bunu yapmak için gerçekleştirmeniz gereken üç yordam vardır:

1. Sihirbaz derlemesini tanımlayıcı bir adla imzalayın.

2. Sihirbaz derlemesinin ortak anahtar belirtecini alın.

3. **Site sütunu** proje şablonu için. vstemplate dosyasındaki sihirbaz derlemesine bir başvuru ekleyin.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Sihirbaz derlemesini tanımlayıcı bir adla imzalamak için

1. **Çözüm Gezgini**, **ProjectTemplateWizard** projesi için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. **İmzalama** sekmesinde, **derlemeyi imzala** onay kutusunu seçin.

3. **Tanımlayıcı ad seçin anahtar dosyası** listesinde, öğesini seçin **\<New...>** .

4. **Tanımlayıcı ad anahtarı oluştur** iletişim kutusunda yeni anahtar dosyası için bir ad girin, **anahtar dosyamı parolayla koru** onay kutusunu temizleyin ve **Tamam** düğmesini seçin.

5. **ProjectTemplateWizard** projesi için kısayol menüsünü açın ve ardından ProjectTemplateWizard.dll dosyasını oluşturmak için **Oluştur** ' u seçin.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Sihirbaz derlemesinin ortak anahtar belirtecini almak için

1. **başlat menüsünde**, **tüm programlar**' ı seçin, **Microsoft Visual Studio**' i seçin, **Visual Studio Araçları**' ı seçin ve **Geliştirici Komut İstemi**' yı seçin.

     Visual Studio bir komut istemi penceresi açılır.

2. Geliştirme bilgisayarınızda ProjectTemplateWizard projesi için oluşturulan ProjectTemplateWizard.dll derlemesinin tam *yolunu kullanarak,* aşağıdaki komutu çalıştırın:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     ProjectTemplateWizard.dll derlemesinin ortak anahtar belirteci Visual Studio komut istemi penceresine yazılır.

3. Visual Studio komut istemi penceresini açık tutun. Bir sonraki yordamda ortak anahtar belirtecine ihtiyacınız olacaktır.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>. Vstemplate dosyasındaki sihirbaz derlemesine bir başvuru eklemek için

1. **Çözüm Gezgini**, **SiteColumnProjectTemplate** proje düğümünü genişletin ve SiteColumnProjectTemplate. vstemplate dosyasını açın.

2. Dosyanın sonuna yakın bir şekilde, `WizardExtension` ve etiketleri arasına aşağıdaki öğeyi ekleyin `</TemplateContent>` `</VSTemplate>` . Özniteliğin *belirteç* değerini, `PublicKeyToken` önceki yordamda elde ettiğiniz ortak anahtar belirteci ile değiştirin.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     öğesi hakkında daha fazla bilgi için `WizardExtension` , bkz. [wizardexgerme öğesi &#40;Visual Studio şablonlar&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Dosyayı kaydedin ve kapatın.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Proje şablonundaki Elements.xml dosyasına değiştirilebilir parametreler ekleme
 SiteColumnProjectTemplate projesindeki *Elements.xml* dosyasına çeşitli değiştirilebilir parametreler ekleyin. Bu parametreler, `RunStarted` `SiteColumnProjectWizard` daha önce tanımladığınız sınıftaki yönteminde başlatılır. bir kullanıcı bir Site sütunu projesi oluşturduğunda, Visual Studio bu parametreleri otomatik olarak yeni projedeki *Elements.xml* dosyasında, sihirbazda belirttikleri değerlerle değiştirir.

 Değiştirilebilir bir parametre, dolar işareti ($) karakteriyle başlayan ve biten bir belirteçtir. kendi değiştirilebilir parametrelerinizi tanımlamanın yanı sıra, SharePoint proje sistemi tarafından tanımlanan ve başlatılan yerleşik parametreleri de kullanabilirsiniz. Daha fazla bilgi için bkz. [değiştirilebilen parametreler](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Elements.xml dosyasına değiştirilebilir parametreler eklemek için

1. SiteColumnProjectTemplate projesinde *Elements.xml* dosyasının IÇERIĞINI aşağıdaki XML ile değiştirin.

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

     Yeni XML,,, `Name` ve özniteliklerinin değerlerini, `DisplayName` `Type` `Group` özel değiştirilebilen parametrelere dönüştürür.

2. Dosyayı kaydedin ve kapatın.

## <a name="add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSıX paketine ekleyin
 sihirbazı Site sütunu proje şablonunu içeren vsıx paketiyle dağıtmak için, sihirbaz projesine ve SharePoint komutları projesine başvuruları vsıx projesindeki source. extension. valtmanifest dosyasına ekleyin.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSıX paketine eklemek için

1. **Çözüm Gezgini**, **SiteColumnProjectItem** projesinde, **Source. Extension. valtmanifest** dosyası için kısayol menüsünü açın ve **Aç**' ı seçin.

     Visual Studio, dosyayı bildirim düzenleyicisinde açar.

2. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3. **Tür** listesinde **Microsoft. VisualStudio. Assembly** öğesini seçin.

4. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

5. **Project** listesinde, **projecttemplatewizard**' ı seçin ve ardından **tamam** düğmesini seçin.

6. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmeyi yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

7. **Tür** listesinde **SharePoint girin. Commands. v4**.

8. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

9. **Project** listesinde, **sharepointcommands** projesini seçin ve **tamam** düğmesini seçin.

10. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından çözümün hatasız olarak derlendiğinizden emin olun.

## <a name="test-the-wizard"></a>Sihirbazı test etme
 Artık Sihirbazı test etmeye hazırsınız. İlk olarak, Visual Studio deneysel örneğinde SiteColumnProjectItem çözümünde hata ayıklamaya başlayın. Daha sonra, Visual Studio deneysel örneğinde Site sütun projesi için Sihirbazı test edin. Son olarak, site sütununun beklendiği gibi çalıştığını doğrulamak için projeyi derleyin ve çalıştırın.

#### <a name="to-start-debugging-the-solution"></a>Çözümdeki hata ayıklamayı başlatmak için

1. yönetici kimlik bilgileriyle Visual Studio yeniden başlatın ve ardından sitecolumnprojectıtem çözümünü açın.

2. ProjectTemplateWizard projesinde, SiteColumnProjectWizard kod dosyasını açın ve sonra yöntemdeki kodun ilk satırına bir kesme noktası ekleyin `RunStarted` .

3. Menü çubuğunda, **hata ayıklama**  >  **özel durumları**' nı seçin.

4. **Özel durumlar** iletişim kutusunda, **ortak dil çalışma zamanı özel durumları** için **oluşturulan** ve **Kullanıcı tarafından işlenmeyen** onay kutularının temizlenmiş olduğundan emin olun ve **Tamam** düğmesini seçin.

5. **F5** tuşunu seçerek veya menü **çubuğunda hata ayıklamayı** Başlat ' ı seçerek hata ayıklamayı başlatın  >  .

     Visual Studio, uzantıyı%userprofile%\appdata\local\microsoft\visualstudio\11.0exp\extensions\contoso\site column\1.0 dizinine yükleyerek Visual Studio deneysel bir örneğini başlatır. Proje öğesini bu Visual Studio örneğinde test edersiniz.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Sihirbazı Visual Studio test etmek için

1. Visual Studio deneysel örneğinde, menü çubuğunda **dosya**  >  **yeni**  >  **Project**' ni seçin.

2. **Visual C#** düğümünü veya **Visual Basic** düğümünü (proje şablonunuzun desteklediği dile bağlı olarak) genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. Proje şablonları listesinde **site sütunu**' nı seçin, projeyi **Sitecolumnwizardtest** olarak adlandırın ve **Tamam** düğmesini seçin.

4. diğer Visual Studio örneğindeki kodun, daha önce yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın `RunStarted` .

5. **F5** tuşunu seçerek veya menü çubuğunda **Hata Ayıkla**  >  **devam et**' i seçerek projede hata ayıklamaya devam edin.

6. **SharePoint özelleştirme sihirbazında**, hata ayıklama için kullanmak istediğiniz sitenin URL 'sini girin ve ardından **ileri** düğmesini seçin.

7. **SharePoint özelleştirme sihirbazının** ikinci sayfasında, aşağıdaki seçimleri yapın:

   - **Tür** listesinde **Boole**' yi seçin.

   - **Grup** listesinde, **özel Evet/Hayır sütunu**' nı seçin.

   - **Ad** kutusuna **Evet/Hayır sütunumu** girin ve ardından **son** düğmesini seçin.

     **Çözüm Gezgini**, yeni bir proje belirir ve **alan1** adlı bir proje öğesi içerir ve Visual Studio projenin *Elements.xml* dosyasını düzenleyicide açar.

8. *Elements.xml* , sihirbazda belirttiğiniz değerleri içerdiğini doğrulayın.

#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint site sütununu test etmek için

1. Visual Studio deneysel örneğinde **F5** tuşunu seçin.

     site sütunu paketlenir ve projenin **site URL** özelliğinin belirttiği SharePoint sitesine dağıtılır. Web tarayıcısı, bu sitenin varsayılan sayfasına açılır.

    > [!NOTE]
    > **Betik hata ayıklaması devre dışı** iletişim kutusu görüntülenirse, projede hata ayıklamaya devam etmek için **Evet** düğmesini seçin.

2. **site eylemleri** menüsünde **site Ayarlar**' yi seçin.

3. site Ayarlar sayfasında, **galeriler**' ın altında, **site sütunları** bağlantısını seçin.

4. Site sütunları listesinde, **özel bir Evet/Hayır** sütun grubunun **Evet/Hayır sütunu** adlı bir sütun içerdiğini doğrulayın ve sonra Web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 Proje öğesini sınamayı bitirdikten sonra, proje şablonunu Visual Studio deneysel örneğinden kaldırın.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizlemek için

1. Visual Studio deneysel örneğinde, menü çubuğunda **araçlar**  >  **uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde **site sütunu**' nı ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin ve ardından kaldırma işlemini gerçekleştirmek Için **Şimdi yeniden Başlat** düğmesini seçin.

4. Visual Studio deneysel örneğini ve CustomActionProjectItem çözümünün açık olduğu örneğini kapatın.

     uzantıların nasıl dağıtılacağı hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bkz. [Visual Studio uzantıları gönderme](../extensibility/shipping-visual-studio-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint Proje Öğeleri için Öğe Şablonları ve Proje Şablonları Oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
