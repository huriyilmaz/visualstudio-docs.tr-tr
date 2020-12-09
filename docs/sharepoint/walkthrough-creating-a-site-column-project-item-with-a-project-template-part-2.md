---
title: Proje şablonu, Bölüm 2 ile site sütunu proje öğesi oluştur
titleSuffix: ''
description: Bir site sütunu proje şablonuna, Proje öğesini içeren bir SharePoint projesi oluşturmak için şablonu kullandıklarında verileri toplamak üzere bir sihirbaz ekleyin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e6e5c9a0bb461f6b81b9cb7e1aa5f0134a7bdcbd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915147"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>İzlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma
  Özel bir SharePoint proje öğesi türü tanımladıktan ve Visual Studio 'daki bir proje şablonuyla ilişkilendirdikten sonra, şablon için bir sihirbaz de sağlamak isteyebilirsiniz. Sihirbazı kullanarak, Proje öğesini içeren yeni bir proje oluşturmak için şablonunuzu kullandıklarında kullanıcılardan bilgi toplayabilirsiniz. Topladığınız bilgiler Proje öğesini başlatmak için kullanılabilir.

 Bu kılavuzda, site sütunu proje şablonuna [Izlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma adlı](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)bir sihirbaz ekleyeceksiniz. Bir Kullanıcı bir site sütunu projesi oluşturduğunda, sihirbaz site sütunuyla ilgili bilgileri (temel türü ve grubu gibi) toplar ve bu bilgileri yeni projedeki *Elements.xml* dosyasına ekler.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir proje şablonuyla ilişkili özel bir SharePoint proje öğesi türü için sihirbaz oluşturma.

- Visual Studio 'da SharePoint projeleri için yerleşik sihirbazlara benzeyen özel bir sihirbaz Kullanıcı Arabirimi tanımlama.

- Sihirbaz çalışırken yerel SharePoint sitesine çağırmak için kullanılan iki *SharePoint komutu* oluşturma. SharePoint komutları, Visual Studio uzantıları tarafından SharePoint Server nesne modelindeki API 'Leri çağırmak için kullanılabilen yöntemlerdir. Daha fazla bilgi için bkz. [SharePoint nesne modellerine çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Sihirbazda topladığınız verilerle SharePoint proje dosyalarını başlatmak için değiştirilebilen parametreleri kullanma.

- Her yeni site sütunu proje örneğinde yeni bir. snk dosyası oluşturuluyor. Bu dosya, SharePoint çözüm derlemesinin Genel derleme önbelleğine dağıtılması için proje çıkışını imzalamak için kullanılır.

- Hata ayıklama ve Sihirbazı test etme.

> [!NOTE]
> Bir dizi örnek iş akışı için bkz. [SharePoint Workflow örnekleri](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Önkoşullar
 Bu yönergeyi gerçekleştirmek için, önce [Izlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma '](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)yı tamamlayarak SiteColumnProjectItem çözümünü oluşturmanız gerekir.

 Bu izlenecek yolu tamamlamak için geliştirme bilgisayarında aşağıdaki bileşenlere de ihtiyacınız vardır:

- Windows, SharePoint ve Visual Studio 'nun desteklenen sürümleri.

- Visual Studio SDK 'Sı. Bu izlenecek yol, Proje öğesini dağıtmak üzere bir VSıX paketi oluşturmak için SDK 'daki **VSIX proje** şablonunu kullanır. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  İzlenecek yolu tamamlamak için aşağıdaki kavramların bilgisi yararlıdır, ancak gerekli değildir:

- Visual Studio 'da proje ve öğe şablonları için sihirbazlar. Daha fazla bilgi için bkz. [nasıl yapılır: sihirbazları proje şablonlarıyla](../extensibility/how-to-use-wizards-with-project-templates.md) ve arabirimiyle kullanma <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

- SharePoint 'te site sütunları. Daha fazla bilgi için bkz. [sütunlar](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

## <a name="understand-the-wizard-components"></a>Sihirbaz bileşenlerini anlama
 Bu izlenecek yolda gösterilen sihirbaz çeşitli bileşenleri içerir. Aşağıdaki tabloda bu bileşenler açıklanmaktadır.

|Bileşen|Açıklama|
|---------------|-----------------|
|Sihirbaz uygulama|Bu, arabirimini uygulayan adlı bir sınıftır `SiteColumnProjectWizard` <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . Bu arabirim, sihirbaz başladığında ve tamamlandığında Visual Studio 'Nun çağırdığı ve sihirbaz çalışırken belirli zamanlarda çağrı yaptığı yöntemleri tanımlar.|
|Sihirbaz kullanıcı arabirimi|Bu, adlı WPF tabanlı bir pencere `WizardWindow` . Bu pencere, ve adlı iki kullanıcı denetimini `Page1` içerir `Page2` . Bu Kullanıcı denetimleri, sihirbazın iki sayfasını temsil eder.<br /><br /> Bu kılavuzda, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> sihirbaz uygulamasının yöntemi sihirbaz kullanıcı arabirimini görüntüler.|
|Sihirbaz veri modeli|Bu, `SiteColumnWizardModel` Sihirbaz kullanıcı arabirimi ve sihirbaz uygulamasıyla bir katman sağlayan adlı bir aracı sınıfıdır. Bu örnek, sihirbaz uygulamasının ve sihirbaz Kullanıcı arabiriminin birbirinden soyut olarak yardımcı olması için bu sınıfı kullanır; Bu sınıf, tüm sihirbazların gerekli bir bileşeni değildir.<br /><br /> Bu kılavuzda, sihirbaz uygulamasının sihirbaz `SiteColumnWizardModel` Kullanıcı arabirimini görüntülediğinde sihirbaz penceresine bir nesne geçirir. Sihirbaz kullanıcı arabirimi bu nesnenin yöntemlerini kullanarak Kullanıcı arabirimindeki denetim değerlerini kaydeder ve giriş site URL 'sinin geçerli olduğunu doğrulama gibi görevleri gerçekleştirir. Kullanıcı Sihirbazı tamamladıktan sonra, sihirbaz uygulaması `SiteColumnWizardModel` Kullanıcı arabiriminin son durumunu öğrenmek için nesnesini kullanır.|
|Proje imzalama Yöneticisi|Bu, `ProjectSigningManager` sihirbaz uygulamasının her yeni proje örneğinde yeni bir Key. snk dosyası oluşturmak için kullanılan adlı bir yardımcı sınıftır.|
|SharePoint komutları|Bunlar, sihirbaz çalışırken, sihirbaz veri modeli tarafından yerel SharePoint sitesine çağrı yapmak için kullanılan yöntemlerdir. SharePoint komutlarının .NET Framework 3,5 ' i hedeflemesi gerektiğinden, bu komutlar, sihirbaz kodunun geri kalanından farklı bir derlemede uygulanır.|

## <a name="create-the-projects"></a>Projeleri oluşturma
 Bu yönergeyi tamamlamak için, [Izlenecek yol: proje şablonu ile bir site sütunu proje öğesi oluşturma, 1. Bölüm](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Bir WPF projesi. <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>Bu projede arabirimini uygular ve sihirbaz kullanıcı arabirimini tanımlayacaksınız.

- SharePoint komutlarını tanımlayan bir sınıf kitaplığı projesi. Bu proje the.NET Framework 3,5 ' i hedeflemelidir.

  Projeleri oluşturarak yönergeyi başlatın.

#### <a name="to-create-the-wpf-project"></a>WPF projesini oluşturmak için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , SiteColumnProjectItem çözümünü açın.

2. **Çözüm Gezgini**, **SiteColumnProjectItem** çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

3. **Yeni Proje Ekle** iletişim kutusunun üst kısmında, .NET Framework sürümleri listesinde **4,5 .NET Framework** seçildiğinden emin olun.

4. **Visual C#** düğümünü veya **Visual Basic** düğümünü genişletin ve **Windows** düğümünü seçin.

5. Proje şablonları listesinde **WPF Kullanıcı denetimi kitaplığı**' nı seçin, Project **ProjectTemplateWizard**' ı adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözüme **ProjectTemplateWizard** projesini ekler ve varsayılan UserControl1. xaml dosyasını açar.

6. Projedeki UserControl1. xaml dosyasını silin.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint komutları projesi oluşturmak için

1. **Çözüm Gezgini**, SiteColumnProjectItem çözüm düğümünün kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni proje**' yi seçin.

2. **Yeni Proje Ekle** iletişim kutusunun üst kısmında .NET Framework sürümleri listesinde **.NET Framework 3,5** ' ı seçin.

3. **Visual C#** düğümünü veya **Visual Basic** düğümünü genişletin ve ardından **Windows** düğümünü seçin.

4. **Sınıf kitaplığı** proje şablonu ' nu seçin, projeyi **SharePointCommands** olarak adlandırın ve **Tamam** düğmesini seçin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözüme **SharePointCommands** projesini ekler ve varsayılan Class1 kod dosyasını açar.

5. Class1 kod dosyasını projeden silin.

## <a name="configure-the-projects"></a>Projeleri yapılandırma
 Sihirbazı oluşturmadan önce, projelere bazı kod dosyaları ve derleme başvuruları eklemeniz gerekir.

#### <a name="to-configure-the-wizard-project"></a>Sihirbaz projesini yapılandırmak için

1. **Çözüm Gezgini**, **ProjectTemplateWizard** proje düğümünün kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. **Proje tasarımcısında**, bir Visual C# projesi için **uygulama** sekmesini veya bir Visual Basic projesi için **Derle** sekmesini seçin.

3. Hedef Framework 'ün .NET Framework 4,5 Istemci profiline değil .NET Framework 4,5 ' e ayarlandığından emin olun.

     Daha fazla bilgi için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md).

4. **ProjectTemplateWizard** projesinin kısayol menüsünü açın, **Ekle**' yi ve ardından **Yeni öğe**' yi seçin.

5. **Pencere (WPF)** öğesini seçin, öğe **WizardWindow** adını adlandırın ve ardından **Ekle** düğmesini seçin.

6. Projeye iki **Kullanıcı denetimi (WPF)** öğesi ekleyin ve bunları **Sayfa1** ve **Page2** olarak adlandırın.

7. Projeye dört kod dosyası ekleyin ve aşağıdaki adları verin:

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. **ProjectTemplateWizard** proje düğümünün kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin.

9. **Derlemeler** düğümünü genişletin, **Uzantılar** düğümünü seçin ve ardından aşağıdaki derlemelerin yanındaki onay kutularını seçin:

    - EnvDTE

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. Shell. Interop. 10.0

    - Microsoft. VisualStudio. Shell. Interop. 11.0

    - Microsoft. VisualStudio. TemplateWizardInterface

10. Derlemeleri projeye eklemek için **Tamam** düğmesini seçin.

11. **Çözüm Gezgini**, **ProjectTemplateWizard** projesi Için **Başvurular** klasörü altında **EnvDTE** öğesini seçin.

12. **Özellikler** penceresinde, **birlikte çalışma türlerini katıştır** özelliğinin değerini **false** olarak değiştirin.

13. Bir Visual Basic projesi geliştiriyorsanız, **Proje tasarımcısını** kullanarak ProjectTemplateWizard ad alanını projenize aktarın.

     Daha fazla bilgi için bkz. [nasıl yapılır: Içeri aktarılan ad alanlarını ekleme veya kaldırma &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointcommands projesini yapılandırmak için

1. **Çözüm Gezgini**, **SharePointCommands** proje düğümünü seçin.

2. Menü çubuğunda **Proje**,  **Varolan öğe Ekle**' yi seçin.

3. **Varolan öğe Ekle** iletişim kutusunda, ProjectTemplateWizard projesi için kod dosyalarını içeren klasöre gidin ve ardından **CommandIds** kod dosyasını seçin.

4. **Ekle** düğmesinin yanındaki oku seçin ve ardından görüntülenen menüdeki **bağlantı olarak ekle** seçeneğini belirleyin.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir bağlantı olarak **SharePointCommands** projesine kod dosyasını ekler. Kod dosyası **ProjectTemplateWizard** projesinde bulunur, ancak dosyadaki kod de **SharePointCommands** projesinde derlenir.

5. **SharePointCommands** projesinde komutları adlı başka bir kod dosyası ekleyin.

6. SharePointCommands projesini seçin ve ardından menü çubuğunda **Proje**  >  **Başvuru Ekle**' yi seçin.

7. **Derlemeler** düğümünü genişletin, **Uzantılar** düğümünü seçin ve ardından aşağıdaki derlemelerin yanındaki onay kutularını seçin:

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

8. Derlemeleri projeye eklemek için **Tamam** düğmesini seçin.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Sihirbaz modeli, imzalama Yöneticisi ve SharePoint komut kimliklerini oluşturma
 Örnek içinde aşağıdaki bileşenleri uygulamak için ProjectTemplateWizard projesine kod ekleyin:

- SharePoint komut kimlikleri. Bu dizeler, sihirbazın kullandığı SharePoint komutlarını belirler. Bu izlenecek yolda daha sonra, komutları uygulamak için SharePointCommands projesine kod ekleyeceksiniz.

- Sihirbaz veri modeli.

- Proje imzalama Yöneticisi.

  Bu bileşenler hakkında daha fazla bilgi için bkz. [sihirbaz bileşenlerini anlama](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>SharePoint komut kimliklerini tanımlamak için

1. ProjectTemplateWizard projesinde CommandIds kod dosyasını açın ve ardından bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>Sihirbaz modeli oluşturmak için

1. SiteColumnWizardModel kod dosyasını açın ve bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>Proje imzalama yöneticisini oluşturmak için

1. ProjectSigningManager kod dosyasını açın ve ardından bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>Sihirbaz kullanıcı arabirimini oluşturma
 Sihirbaz penceresinin Kullanıcı arabirimini ve sihirbaz sayfalarına yönelik Kullanıcı ARABIRIMINI sağlayan iki kullanıcı denetimini tanımlamak için XAML ekleyin ve pencere ve Kullanıcı denetimlerinin davranışını tanımlamak için kod ekleyin. Oluşturduğunuz sihirbaz, Visual Studio 'daki SharePoint projeleri için yerleşik sihirbaza benzer.

> [!NOTE]
> Aşağıdaki adımlarda, projenize XAML veya kod ekledikten sonra projenizin bazı derleme hataları olacaktır. Sonraki adımlarda kod eklediğinizde bu hatalar kaybolur.

#### <a name="to-create-the-wizard-window-ui"></a>Sihirbaz penceresi Kullanıcı arabirimini oluşturmak için

1. ProjectTemplateWizard projesinde, WizardWindow. xaml dosyası için kısayol menüsünü açın ve ardından **Aç** ' ı seçerek pencereyi tasarımcıda açın.

2. Tasarımcının XAML görünümünde, geçerli XAML 'yi aşağıdaki XAML ile değiştirin. XAML, <xref:System.Windows.Controls.Grid> pencerenin alt kısmındaki Sihirbaz sayfalarını ve gezinti düğmelerini içeren bir başlık içeren bir kullanıcı arabirimi tanımlar.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    > Bu XAML 'de oluşturulan pencere, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> temel sınıftan türetilir. Visual Studio 'ya özel bir WPF iletişim kutusu eklediğinizde, diğer Visual Studio iletişim kutuları ile tutarlı bir Stillendirme ve aksi takdirde oluşabilecek kalıcı iletişim sorunlarından kaçınmak için iletişim kutusunu bu sınıftan türetmenizi öneririz. Daha fazla bilgi için bkz. [kalıcı Iletişim kutuları oluşturma ve yönetme](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Visual Basic bir proje geliştiriyorsanız, `ProjectTemplateWizard` ad alanını `WizardWindow` öğenin özniteliğinde sınıf adından kaldırın `x:Class` `Window` . Bu öğe, XAML 'in ilk satıröğesidir. İşiniz bittiğinde, ilk satır aşağıdaki örnekteki gibi görünmelidir.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow. xaml dosyası için arka plan kod dosyasını açın.

5. Dosyanın üst kısmındaki bildirimler hariç, bu dosyanın içeriğini `using` aşağıdaki kodla değiştirin.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>İlk sihirbaz sayfası kullanıcı arabirimini oluşturmak için

1. ProjectTemplateWizard projesinde, Sayfa1. xaml dosyası için kısayol menüsünü açın ve sonra tasarımcıda Kullanıcı denetimini açmak için **Aç** ' ı seçin.

2. Tasarımcının XAML görünümünde, geçerli XAML 'yi aşağıdaki XAML ile değiştirin. XAML, kullanıcıların hata ayıklama için kullanmak istedikleri yerel sitelerin URL 'sini girebilecekleri bir metin kutusu içeren bir kullanıcı arabirimi tanımlar. Kullanıcı arabirimi, kullanıcıların projenin korumalı olup olmadığını belirleyebileceği seçenek düğmelerini de içerir.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3. Visual Basic bir proje geliştiriyorsanız, `ProjectTemplateWizard` ad alanını `Page1` öğenin özniteliğinde sınıf adından kaldırın `x:Class` `UserControl` . Bu, XAML 'in ilk satırdır. İşiniz bittiğinde, ilk satır aşağıdaki gibi görünmelidir.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. `using`Aşağıdaki kodla, dosyanın en üstündeki bildirimler hariç, Sayfa1. xaml dosyasının içeriğini değiştirin.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>İkinci sihirbaz sayfası kullanıcı arabirimini oluşturmak için

1. ProjectTemplateWizard projesinde, Page2. xaml dosyası için kısayol menüsünü açın ve **Aç** öğesini seçin.

     Kullanıcı denetimi tasarımcıda açılır.

2. XAML görünümünde, geçerli XAML 'yi aşağıdaki XAML ile değiştirin. XAML, site sütununun temel türünü seçmek için açılan bir liste, galeride site sütununun görüntüleneceği bir yerleşik veya özel grup belirtmeye yönelik bir açılan kutu ve site sütununun adını belirtmek için bir metin kutusu içeren bir kullanıcı arabirimi tanımlar.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3. Visual Basic bir proje geliştiriyorsanız, `ProjectTemplateWizard` ad alanını `Page2` öğenin özniteliğinde sınıf adından kaldırın `x:Class` `UserControl` . Bu, XAML 'in ilk satırdır. İşiniz bittiğinde, ilk satır aşağıdaki gibi görünmelidir.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Page2. xaml dosyası için arka plan kod dosyasının içeriğini, `using` dosyanın en üstündeki bildirimler dışında, aşağıdaki kodla değiştirin.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>Sihirbazı uygulama
 Arabirimi uygulayarak sihirbazın ana işlevlerini tanımlayın <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . Bu arabirim, sihirbaz başladığında ve tamamlandığında Visual Studio 'Nun çağırdığı ve sihirbaz çalışırken belirli zamanlarda çağrı yaptığı yöntemleri tanımlar.

#### <a name="to-implement-the-wizard"></a>Sihirbazı uygulamak için

1. ProjectTemplateWizard projesinde SiteColumnProjectWizard kod dosyasını açın.

2. Bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>SharePoint komutlarını oluşturma
 SharePoint Server nesne modeli ' ni çağıran iki özel komut oluşturun. Bir komut, sihirbazda Kullanıcı türlerindeki site URL 'sinin geçerli olup olmadığını belirler. Diğer komut, kullanıcıların yeni site sütunları için temel olarak hangisini kullanacağınızı seçmesini sağlamak için, belirtilen SharePoint sitesindeki tüm alan türlerini alır.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint komutlarını tanımlamak için

1. **SharePointCommands** projesinde, komutlar kod dosyasını açın.

2. Bu dosyanın tüm içeriğini aşağıdaki kodla değiştirin.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

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

1. **Başlat menüsünde**, **tüm programlar**' ı seçin, **Microsoft Visual Studio**' i seçin, **Visual Studio Araçları**' ı seçin ve **Geliştirici komut istemi**' yı seçin.

     Bir Visual Studio komut Istemi penceresi açılır.

2. Geliştirme bilgisayarınızda ProjectTemplateWizard projesi için oluşturulan ProjectTemplateWizard.dll derlemesinin tam *yolunu kullanarak,* aşağıdaki komutu çalıştırın:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     ProjectTemplateWizard.dll derlemesinin ortak anahtar belirteci, Visual Studio komut Istemi penceresine yazılır.

3. Visual Studio komut Istemi penceresini açık tutun. Bir sonraki yordamda ortak anahtar belirtecine ihtiyacınız olacaktır.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>. Vstemplate dosyasındaki sihirbaz derlemesine bir başvuru eklemek için

1. **Çözüm Gezgini**, **SiteColumnProjectTemplate** proje düğümünü genişletin ve SiteColumnProjectTemplate. vstemplate dosyasını açın.

2. Dosyanın sonuna yakın bir şekilde, `WizardExtension` ve etiketleri arasına aşağıdaki öğeyi ekleyin `</TemplateContent>` `</VSTemplate>` . Özniteliğin *belirteç* değerini, `PublicKeyToken` önceki yordamda elde ettiğiniz ortak anahtar belirteci ile değiştirin.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Öğesi hakkında daha fazla bilgi için `WizardExtension` bkz. [Wizardexgerme öğesi &#40;Visual Studio şablonları&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Dosyayı kaydedin ve kapatın.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Proje şablonundaki Elements.xml dosyasına değiştirilebilir parametreler ekleme
 SiteColumnProjectTemplate projesindeki *Elements.xml* dosyasına çeşitli değiştirilebilir parametreler ekleyin. Bu parametreler, `RunStarted` `SiteColumnProjectWizard` daha önce tanımladığınız sınıftaki yönteminde başlatılır. Bir Kullanıcı bir site sütunu projesi oluşturduğunda, Visual Studio otomatik olarak bu parametreleri yeni projedeki *Elements.xml* dosyasında, sihirbazda belirttikleri değerlerle değiştirir.

 Değiştirilebilir bir parametre, dolar işareti ($) karakteriyle başlayan ve biten bir belirteçtir. Kendi değiştirilebilir parametrelerinizi tanımlamanın yanı sıra, SharePoint proje sistemi tarafından tanımlanan ve başlatılan yerleşik parametreleri de kullanabilirsiniz. Daha fazla bilgi için bkz. [değiştirilebilen parametreler](../sharepoint/replaceable-parameters.md).

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
 Sihirbazı site sütunu proje şablonunu içeren VSıX paketiyle dağıtmak için, sihirbaz projesine ve SharePoint komutları projesine başvuruları VSıX projesindeki Source. Extension. valtmanifest dosyasına ekleyin.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Sihirbazı VSıX paketine eklemek için

1. **Çözüm Gezgini**, **SiteColumnProjectItem** projesinde, **Source. Extension. valtmanifest** dosyası için kısayol menüsünü açın ve **Aç**' ı seçin.

     Visual Studio, dosyayı bildirim düzenleyicisinde açar.

2. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmesini seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

3. **Tür** listesinde **Microsoft. VisualStudio. Assembly** öğesini seçin.

4. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

5. **Proje** listesinde **ProjectTemplateWizard**' ı seçin ve ardından **Tamam** düğmesini seçin.

6. Düzenleyicinin **varlıklar** sekmesinde **Yeni** düğmeyi yeniden seçin.

     **Yeni varlık Ekle** iletişim kutusu açılır.

7. **Tür** listesinde, **SharePoint. Commands. v4** girin.

8. **Kaynak** listesinde, **Geçerli çözümde bir proje** seçin.

9. **Proje** listesinde, **SharePointCommands** projesini seçin ve **Tamam** düğmesini seçin.

10. Menü **çubuğunda Build**  >  **Build Solution** öğesini seçin ve ardından çözümün hatasız olarak derlendiğinizden emin olun.

## <a name="test-the-wizard"></a>Sihirbazı test etme
 Artık Sihirbazı test etmeye hazırsınız. İlk olarak, Visual Studio 'nun deneysel örneğinde SiteColumnProjectItem çözümünde hata ayıklamaya başlayın. Ardından, Visual Studio 'nun Deneysel örneğindeki Site sütun projesi için Sihirbazı test edin. Son olarak, site sütununun beklendiği gibi çalıştığını doğrulamak için projeyi derleyin ve çalıştırın.

#### <a name="to-start-debugging-the-solution"></a>Çözümdeki hata ayıklamayı başlatmak için

1. Visual Studio 'Yu yönetici kimlik bilgileriyle yeniden başlatın ve ardından SiteColumnProjectItem çözümünü açın.

2. ProjectTemplateWizard projesinde, SiteColumnProjectWizard kod dosyasını açın ve sonra yöntemdeki kodun ilk satırına bir kesme noktası ekleyin `RunStarted` .

3. Menü çubuğunda, **hata ayıklama**  >  **özel durumları**' nı seçin.

4. **Özel durumlar** iletişim kutusunda, **ortak dil çalışma zamanı özel durumları** için **oluşturulan** ve **Kullanıcı tarafından işlenmeyen** onay kutularının temizlenmiş olduğundan emin olun ve **Tamam** düğmesini seçin.

5. **F5** tuşunu seçerek veya menü **çubuğunda hata ayıklamayı** Başlat ' ı seçerek hata ayıklamayı başlatın  >  **Start Debugging**.

     Visual Studio, uzantıyı%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 konumuna yükleyerek Visual Studio 'nun deneysel bir örneğini başlatır. Bu Visual Studio örneğinde Proje öğesini test edeceksiniz.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Visual Studio 'da Sihirbazı test etmek için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

2. **Visual C#** düğümünü veya **Visual Basic** düğümünü (proje şablonunuzun desteklediği dile bağlı olarak) genişletin, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. Proje şablonları listesinde **site sütunu**' nı seçin, projeyi **Sitecolumnwizardtest** olarak adlandırın ve **Tamam** düğmesini seçin.

4. Visual Studio 'nun diğer örneğindeki kodun, daha önce yönteminde ayarladığınız kesme noktasında durduğunu doğrulayın `RunStarted` .

5. **F5** tuşunu seçerek veya menü çubuğunda **Hata Ayıkla**  >  **devam et**' i seçerek projede hata ayıklamaya devam edin.

6. **SharePoint Özelleştirme Sihirbazı**'nda, hata ayıklama için kullanmak istediğiniz sitenin URL 'sini girin ve sonra **İleri** düğmesini seçin.

7. **SharePoint Özelleştirme Sihirbazı**'nın ikinci sayfasında, aşağıdaki seçimleri yapın:

   - **Tür** listesinde **Boole**' yi seçin.

   - **Grup** listesinde, **özel Evet/Hayır sütunu**' nı seçin.

   - **Ad** kutusuna **Evet/Hayır sütunumu** girin ve ardından **son** düğmesini seçin.

     **Çözüm Gezgini**, yeni bir proje görünür ve **alan1** adlı bir proje öğesi içerir ve Visual Studio projenin *Elements.xml* dosyasını düzenleyicide açar.

8. *Elements.xml* , sihirbazda belirttiğiniz değerleri içerdiğini doğrulayın.

#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint 'te site sütununu test etmek için

1. Visual Studio 'nun deneysel örneğinde **F5** tuşunu seçin.

     Site sütunu paketlenir ve projenin **SITE URL** özelliğinin belirttiği SharePoint sitesine dağıtılır. Web tarayıcısı, bu sitenin varsayılan sayfasına açılır.

    > [!NOTE]
    > **Betik hata ayıklaması devre dışı** iletişim kutusu görüntülenirse, projede hata ayıklamaya devam etmek için **Evet** düğmesini seçin.

2. **Site eylemleri** menüsünde, **site ayarları**' nı seçin.

3. Site Ayarları sayfasında, **galeriler** altında, **site sütunları** bağlantısını seçin.

4. Site sütunları listesinde, **özel bir Evet/Hayır** sütun grubunun **Evet/Hayır sütunu** adlı bir sütun içerdiğini doğrulayın ve sonra Web tarayıcısını kapatın.

## <a name="clean-up-the-development-computer"></a>Geliştirme bilgisayarını Temizleme
 Proje öğesini sınamayı bitirdikten sonra, Visual Studio 'nun deneysel örneğinden proje şablonunu kaldırın.

#### <a name="to-clean-up-the-development-computer"></a>Geliştirme bilgisayarını temizlemek için

1. Visual Studio 'nun deneysel örneğinde, menü çubuğunda **Araçlar**  >  **Uzantılar ve güncelleştirmeler**' i seçin.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2. Uzantılar listesinde **site sütunu**' nı ve ardından **Kaldır** düğmesini seçin.

3. Görüntülenen iletişim kutusunda, uzantıyı kaldırmak istediğinizi onaylamak için **Evet** düğmesini seçin ve ardından kaldırma işlemini gerçekleştirmek Için **Şimdi yeniden Başlat** düğmesini seçin.

4. Visual Studio 'nun Deneysel örneğini ve CustomActionProjectItem çözümünün açık olduğu örneğini kapatın.

     Uzantıları dağıtma hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bkz. [Visual Studio uzantılarını gönderme](../extensibility/shipping-visual-studio-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint Proje Öğeleri için Öğe Şablonları ve Proje Şablonları Oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Nasıl Yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
