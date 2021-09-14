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
ms.openlocfilehash: f82d6ca09e67cd2911a0dc9803e65f14b85cca6c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726749"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Adım adım kılavuz: Proje şablonuyla site sütunu proje öğesi oluşturma, Bölüm 2
  Bir proje öğesi için özel SharePoint tanımladığınız ve bunu Visual Studio proje şablonuyla ilişkilendirmeniz, şablon için bir sihirbaz sağlamak da iyi olabilir. Proje öğesini içeren yeni bir proje oluşturmak üzere şablonlarınızı kullanan kullanıcılardan bilgi toplamak için sihirbazı kullanabilirsiniz. Toplayan bilgiler proje öğesini başlatmak için kullanılabilir.

 Bu kılavuzda, Site Sütunu proje şablonuna, Adım 1' bölümünde yer alan Bir Site Sütunu Project Öğesi Oluşturma bölümünde Project [sihirbaz eklenecektir.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md) Kullanıcı bir Site Sütunu projesi oluşturduğunda sihirbaz, site sütunu (temel türü ve grubu gibi) hakkında bilgi toplar ve bu bilgileri *yeni projedeElements.xml* dosyasına ekler.

 Bu kılavuz aşağıdaki görevleri gösterir:

- Özel bir proje şablonu SharePoint bir proje şablonuyla ilişkili proje öğesi türü için sihirbaz oluşturma.

- Visual Studio'daki projelerin yerleşik sihirbazları gibi özel bir SharePoint kullanıcı arabirimi tanımlama.

- Sihirbaz *SharePoint yerel* siteye çağrı yapmak için SharePoint iki komut oluşturma. SharePoint komutları, Visual Studio sunucu nesne modelinde API'leri SharePoint için kullanılan yöntemlerdir. Daha fazla bilgi için [bkz. Nesne SharePoint Çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)

- Proje dosyalarını sihirbazda toplayan SharePoint başlatmak için değiştirilebilir parametreleri kullanma.

- Her yeni Site Sütunu proje örneğinde yeni bir .snk dosyası oluşturma. Bu dosya, çözüm derlemesini genel derleme önbelleğine SharePoint proje çıktısını imzalamak için kullanılır.

- Sihirbazda hata ayıklama ve test etme.

> [!NOTE]
> Bir dizi örnek iş akışı için bkz. [SharePoint örnekleri.](/sharepoint/dev/general-development/sharepoint-workflow-samples)

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu gerçekleştirmek için, önce Adım adım Kılavuz: Site Sütunu oluşturma Project Öğe oluşturma, [1.](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)Bölüm'Project SiteColumnProjectItem çözümünü oluşturmanız gerekir.

 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarda aşağıdaki bileşenlere de ihtiyacınız vardır:

- Desteklenen Windows, SharePoint ve Visual Studio sürümleri.

- Visual Studio SDK'sı. Bu kılavuzda, **proje öğesini Project** bir VSIX paketi oluşturmak için SDK'daki VSIX uygulama şablonu kullanılır. Daha fazla bilgi için [bkz. SharePoint'de Visual Studio.](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)

  Aşağıdaki kavramlar hakkında bilgi sahibi olmak, izlenecek yolu tamamlamak için faydalıdır ancak gerekli değildir:

- Proje ve öğe şablonları için sihirbazlar Visual Studio. Daha fazla bilgi için, [bkz. How to: Use Wizards with Project templates](../extensibility/how-to-use-wizards-with-project-templates.md) and <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> the interface.

- Web'de site SharePoint. Daha fazla bilgi için bkz. [Sütunlar.](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))

## <a name="understand-the-wizard-components"></a>Sihirbaz bileşenlerini anlama
 Bu kılavuzda gösteren sihirbaz çeşitli bileşenler içerir. Aşağıdaki tabloda bu bileşenler açıkmektedir.

|Bileşen|Açıklama|
|---------------|-----------------|
|Sihirbaz uygulaması|Bu, arabirimini uygulayan `SiteColumnProjectWizard` adlı bir <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> sınıftır. Bu arabirim, sihirbaz başlatıldığında Visual Studio ve sihirbaz çalışırken belirli zamanlarda çağıran yöntemleri tanımlar.|
|Sihirbaz kullanıcı arabirimi|Bu, adlı WPF tabanlı bir `WizardWindow` penceredir. Bu pencere, ve adlı iki kullanıcı denetimi `Page1` `Page2` içerir. Bu kullanıcı denetimleri sihirbazın iki sayfalarını temsil eder.<br /><br /> Bu kılavuzda, sihirbaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> uygulamasının yöntemi sihirbaz kullanıcı arabirimini görüntüler.|
|Sihirbaz veri modeli|Bu, sihirbaz kullanıcı arabirimi ile sihirbaz uygulaması arasında bir katman sağlayan adlı `SiteColumnWizardModel` bir ara sınıftır. Bu örnek, sihirbaz uygulamasını ve sihirbaz kullanıcı arabirimini diğerlerinden soyutlamanıza yardımcı olmak için bu sınıfı kullanır; Bu sınıf, tüm sihirbazların gerekli bir bileşeni değildir.<br /><br /> Bu kılavuzda, sihirbaz uygulaması sihirbaz kullanıcı arabirimini `SiteColumnWizardModel` görüntülerken bir nesneyi sihirbaz penceresine iletir. Sihirbaz kullanıcı arabirimi, kullanıcı arabiriminde denetimlerin değerlerini kaydetmek ve giriş sitesi URL'sinin geçerli olduğunu doğrulama gibi görevleri gerçekleştirmek için bu nesnenin yöntemlerini kullanır. Kullanıcı sihirbazı tamamladikten sonra sihirbaz uygulaması, kullanıcı arabiriminin son `SiteColumnWizardModel` durumunu belirlemek için nesnesini kullanır.|
|Project yöneticisi|Bu, sihirbaz uygulaması tarafından her yeni proje örneğinde yeni bir key.snk dosyası oluşturmak için kullanılan adlı `ProjectSigningManager` bir yardımcı sınıftır.|
|SharePoint komutları|Bunlar, sihirbaz çalışırken yerel SharePoint çağrısı yapmak için sihirbaz veri modeli tarafından kullanılan yöntemlerdir. Bu SharePoint 3.5'.NET Framework hedeflemesi gerekenden, bu komutlar sihirbaz kodunun geri kalanından farklı bir derlemede uygulanır.|

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu izlenecek yolu tamamlamak için, Izlenecek Yol: Proje şablonuyla site sütunu proje öğesi oluşturma bölümünde oluşturduğunuz SiteColumnProjectItem çözümüne birkaç proje eklemeniz [gerekir, Bölüm 1:](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)

- WPF projesi. Bu projede <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> arabirimini uygulayacak ve sihirbaz kullanıcı arabirimini tanımlayabilirsiniz.

- Uygulama komutlarını tanımlayan bir sınıf SharePoint projesi. Bu proje, the.NET Framework 3.5'i hedeflemeli.

  Projeleri oluşturarak izlenecek yolu başlatma.

#### <a name="to-create-the-wpf-project"></a>WPF projesini oluşturmak için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SiteColumnProjectItem çözümünü açın.

2. Bu **Çözüm Gezgini** **SiteColumnProjectItem** çözüm düğümünün kısayol menüsünü açın, Ekle'yi ve ardından Yeni **Oluştur'u Project.** 

3. Yeni Uygulama Ekle iletişim **Project** üst kısmında, .NET Framework sürüm listesinde **.NET Framework 4.5'in** .NET Framework.

4. Visual **C# düğümünü** veya **Visual Basic** düğümünü genişletin ve **Windows** seçin.

5. Proje şablonları listesinde **WPF** Kullanıcı Denetim Kitaplığı'ı seçin, projeye **ProjectTemplateWizard adını ve** ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ProjectTemplateWizard** projesini çözüme ekler ve varsayılan UserControl1.xaml dosyasını açar.

6. Projeden UserControl1.xaml dosyasını silin.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint komutları projesini oluşturmak için

1. Bu **Çözüm Gezgini,** SiteColumnProjectItem çözüm düğümü için kısayol menüsünü açın, Ekle'yi ve ardından Yeni **Oluştur'u Project.**

2. Yeni Uygulama Ekle iletişim **kutusunun Project,** .NET Framework sürümleri **listesinden 3.5'i** .NET Framework.

3. Visual **C# düğümünü** veya **Visual Basic** genişletin ve ardından Windows **seçin.**

4. Sınıf Kitaplığı **proje şablonunu** seçin, projeye **SharePointCommands adını ve** ardından Tamam **düğmesini** seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**SharePointCommands projesini** çözüme ekler ve varsayılan Class1 kod dosyasını açar.

5. Projeden Class1 kod dosyasını silin.

## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Sihirbazı oluşturmadan önce, projelere bazı kod dosyaları ve derleme başvuruları eklemeniz gerekir.

#### <a name="to-configure-the-wizard-project"></a>Sihirbaz projesini yapılandırmak için

1. Bu **Çözüm Gezgini** **ProjeTemplateWizard** proje düğümü için kısayol menüsünü açın ve özellikler'i **seçin.**

2. Project **Tasarımcısı'nda,** bir Visual  C# projesinin Uygulama sekmesini  veya bir Visual Basic seçin.

3. Hedef çerçevenin 4.5 İstemci Profili .NET Framework 4.5 .NET Framework olduğundan emin olun.

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
 Sihirbazı uyguladığınıza göre, Sihirbazı **site sütunu** proje şablonuyla ilişkilendirmeniz gerekir. Bunu yapmak için tamamlamanız gereken üç yordam vardır:

1. Sihirbaz derlemeyi bir güçlü adla imzalar.

2. Sihirbaz derlemesi için ortak anahtar belirteci alın.

3. Site Sütunu proje şablonu için .vstemplate dosyasında sihirbaz derlemesi **için bir** başvuru ekleyin.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Sihirbaz derlemeyi güçlü bir adla imzalamak için

1. Bu **Çözüm Gezgini** **ProjectTemplateWizard projesinin** kısayol menüsünü açın ve Özellikler'i **seçin.**

2. İmzalama **sekmesinde** Derlemeyi **imzala onay** kutusunu seçin.

3. Bir **güçlü ad anahtar dosyası seçin listesinde'yi** **\<New...>** seçin.

4. Güçlü **Ad Anahtarı Oluştur** iletişim kutusunda yeni anahtar dosyası için  bir ad girin, Anahtar dosyamı parolayla koru onay kutusunun işaretini kaldırın ve ardından Tamam **düğmesini** seçin.

5. **ProjectTemplateWizard** projesinin kısayol menüsünü açın ve  derleme dosyasını oluşturmak için Oluştur'ProjectTemplateWizard.dll seçin.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Sihirbaz derlemesi için ortak anahtar belirteci almak için

1. Başlat Menüsünde Tüm  **Programlar'ı** seçin, **Microsoft Visual Studio'Visual Studio Araçları** **seçin** ve sonra da **Geliştirici Komut İstemi.**

     Bir Visual Studio Komut İstemi penceresi açılır.

2. Aşağıdaki komutu çalıştırın ve *PathToWizardAssembly* yerine geliştirme bilgisayarınızda ProjectTemplateWizard projesi için ProjectTemplateWizard.dll derlemenin tam yolunu yazın:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     ProjectTemplateWizard.dll derlemesi için ortak anahtar belirteci, Visual Studio istemi penceresine yazılır.

3. Komut Visual Studio penceresini açık tutma. Sonraki yordam sırasında ortak anahtar belirtecin gerekir.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.vstemplate dosyasında sihirbaz derlemesi için başvuru eklemek için

1. Bu **Çözüm Gezgini** **SiteColumnProjectTemplate** proje düğümünü genişletin ve SiteColumnProjectTemplate.vstemplate dosyasını açın.

2. Dosyanın sonuna yakın bir yerde ve etiketleri `WizardExtension` arasına aşağıdaki `</TemplateContent>` öğeyi `</VSTemplate>` ekleyin. özniteliğinin *belirteç* değerini `PublicKeyToken` önceki yordamda edinilen ortak anahtar belirteci ile değiştirin.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     öğesi hakkında daha fazla bilgi `WizardExtension` için bkz. [WizardExtension Öğesi &#40;Visual Studio Şablon&#41;. ](../extensibility/wizardextension-element-visual-studio-templates.md)

3. Dosyayı kaydedin ve kapatın.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Proje şablonunda yer alan Elements.xml değiştirilebilir parametreler ekleme
 SiteColumnProjectTemplate projesindeElements.xmlbirçok değiştirilebilir parametre ekleyin.  Bu parametreler, daha önce `RunStarted` tanımlandığı `SiteColumnProjectWizard` sınıftaki yönteminde başlatılır. Kullanıcı bir Site Sütunu projesi oluşturduğunda, Visual Studio yeni projede yer alan *Elements.xml* dosyasındaki bu parametreleri sihirbazda belirtilen değerlerle otomatik olarak değiştirir.

 Değiştirilebilir parametre, dolar işareti ($) karakteriyle başlayan ve sona eren bir belirteçtir. Kendi değiştirilebilir parametrelerinizi tanımlamaya ek olarak, proje sistemi tarafından tanımlanan ve başlatılan yerleşik SharePoint kullanabilirsiniz. Daha fazla bilgi için [bkz. Değiştirilebilir parametreler.](../sharepoint/replaceable-parameters.md)

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Elements.xml dosyasına değiştirilebilir parametreler eklemek için

1. SiteColumnProjectTemplate projesinde, *Elements.xml* içeriğini aşağıdaki XML ile değiştirin.

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
 Sihirbazı Site Sütunu proje şablonunu içeren VSIX paketiyle dağıtmak için, VSIX projesinde source.extension.vsixmanifest dosyasına sihirbaz projesine ve SharePoint komutları projesine başvurular ekleyin.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSIX paketine eklemek için

1. Bu **Çözüm Gezgini** **SiteColumnProjectItem** projesinde **source.extension.vsixmanifest** dosyasının kısayol menüsünü açın ve Aç'ı **seçin.**

     Visual Studio bildirim düzenleyicisinde açılır.

2. Düzenleyicinin  Varlıklar sekmesinde Yeni **düğmesini** seçin.

     Yeni **Varlık Ekle iletişim** kutusu açılır.

3. Tür listesinde **Microsoft.VisualStudio.Assembly'i seçin.** 

4. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

5. Yeni **Project** **ProjectTemplateWizard'ı ve** ardından Tamam **düğmesini** seçin.

6. Düzenleyicinin **Varlıklar** sekmesinde Yeni düğmesini **yeniden** seçin.

     Yeni **Varlık Ekle iletişim** kutusu açılır.

7. Tür **listesine** **SharePoint. Commands.v4**.

8. Kaynak **listesinde Geçerli** çözümde **bir proje'yi seçin.**

9. Aşağıdaki **Project** **SharePointCommands projesini** ve ardından Tamam **düğmesini** seçin.

10. Menü çubuğunda Derleme **Çözümü'yü**  >  **seçin** ve çözümün hatasız olarak derlemeye devam edin.

## <a name="test-the-wizard"></a>Sihirbazı test etme
 Artık sihirbazı test etmeye hazırsınız. İlk olarak, Visual Studio'nin deneysel örneğinde SiteColumnProjectItem çözümünde hata ayıklamaya Visual Studio. Ardından, sitenin deneysel örneğinde Site Sütunu projesinin sihirbazını Visual Studio. Son olarak, site sütununu beklendiği gibi çalıştığını doğrulamak için projeyi derleme ve çalıştırma.

#### <a name="to-start-debugging-the-solution"></a>Çözümde hata ayıklamaya başlamak için

1. Yönetici Visual Studio ile yeniden başlatın ve ardından SiteColumnProjectItem çözümünü açın.

2. ProjectTemplateWizard projesinde SiteColumnProjectWizard kod dosyasını açın ve ardından yönteminde ilk kod satırına bir kesme noktası `RunStarted` ekleyin.

3. Menü çubuğunda Özel Durumlarda **Hata Ayıkla'ya**  >  **tıklayın.**

4. Özel **Durumlar iletişim** kutusunda, Ortak Dil Çalışma Zamanı Özel Durumları için  Thrown ve **User tarafından** işsiz onay **kutularının** temiz olduğundan emin olun ve ardından **Tamam düğmesini** seçin.

5. **F5** anahtarını veya menü çubuğunda Hata AyıklamaYı Başlat'ı seçerek **hata**  >  **ayıklamayı başlatabilirsiniz.**

     Visual Studio %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 uzantısını yüklüp deneysel bir Visual Studio. Proje öğesini bu örnek içinde test Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Sihirbazı test etmek için Visual Studio

1. Deneysel Visual Studio örneğinde, menü çubuğunda Dosya Yeni Dosya'Project.  >    >  

2. Visual **C# düğümünü** **veya Visual Basic** düğümünü genişletin (proje şablonunuz tarafından kullanılan dile bağlı olarak), **SharePoint** düğümünü genişletin ve **ardından 2010 düğümünü** seçin.

3. Proje şablonları listesinde Site Sütunu'na **tıklayın,** projeye **SiteColumnWizardTest** adını ve ardından Tamam **düğmesini** seçin.

4. uygulamanın diğer örneğinde yer alan kodun Visual Studio daha önce yönteminde ayar güvenlik kesme noktası üzerinde durduğu `RunStarted` doğrulayın.

5. **F5** anahtarını seçerek veya menü çubuğunda Devam'da Hata Ayıkla'ya seçerek projede **hata ayıklamaya**  >  **devam eder.**

6. SharePoint **Özelleştirme Sihirbazı'nda,** hata ayıklama için kullanmak istediğiniz sitenin URL'sini girin ve ardından Sonraki **düğmesini** seçin.

7. Özelleştirme Sihirbazı'nın **SharePoint sayfasında** aşağıdaki seçimleri yapın:

   - Tür **listesinde** **Boolean'ı seçin.**

   - Grup listesinde **Özel** **Evet/Sütun Yok'a tıklayın.**

   - Ad **kutusuna** **Evet/Hayır Sütunum yazın** ve son **düğmesini** seçin.

     Bu **Çözüm Gezgini** yeni bir proje görünür ve **Alan1** adlı bir proje öğesi içerir ve Visual Studio projeninElements.xml *dosyasını* düzenleyicide açar.

8. Bu *Elements.xml* sihirbazda belirttiğiniz değerleri içerdiğini doğrulayın.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Site sütununu test etmek için SharePoint

1. Deneysel Visual Studio **F5 anahtarını** seçin.

     Site sütunu, projenin Site **URL'si** özelliğinin SharePoint site için paketli ve dağıtılmıştır. Web tarayıcısı bu sitenin varsayılan sayfasını açar.

    > [!NOTE]
    > Betik **Hata Ayıklama Devre Dışı** iletişim kutusu görüntülenirse, projede **hata** ayıklamaya devam etmek için Evet düğmesini seçin.

2. Site Eylemleri **menüsünde Site** **öğeleri'Ayarlar.**

3. Site Sütunları Ayarlar Galeriler'in altında Site sütunları **bağlantısını** seçin.

4. Site sütunları listesinde, Özel **Evet/Hayır** Sütunları grubunun **Evet/Hayır** Sütunum adlı bir sütun içerdiğini doğrulayın ve ardından web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizleme
 Proje öğesini test etme tamamladikten sonra, proje şablonunu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarlarını temizlemek için

1. Deneysel Visual Studio menü çubuğunda Araçlar Uzantıları ve   >  **Güncelleştirmeler'i seçin.**

     Uzantılar **ve Güncelleştirmeler** iletişim kutusu açılır.

2. Uzantı listesinde Site Sütunu'na **ve** ardından Kaldır **düğmesini** seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı  kaldırmak istediğinizden emin olmak için Evet düğmesini  seçin ve ardından kaldırma işlemini tamamlamak için Şimdi Yeniden Başlat düğmesini seçin.

4. Hem deneysel Visual Studio hem de CustomActionProjectItem çözümünün açık olduğu örneği kapatın.

     Uzantıları dağıtma hakkında bilgi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] için bkz. [Gönderim Visual Studio Uzantıları.](../extensibility/shipping-visual-studio-extensions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: Proje şablonuyla site sütunu proje öğesi oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Özel proje SharePoint türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint Proje Öğeleri için Öğe Şablonları ve Proje Şablonları Oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
