---
title: 'SSS: eklentileri VSPackage uzantılarına dönüştürme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6ed31f96fc2021d0d9e104692f0440cfb78a5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821266"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>SSS: Eklentileri VSPackage Uzantılarına Dönüştürme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eklentiler artık kullanım dışıdır. Yeni bir Visual Studio uzantısı oluşturmak için, bir VSıX uzantısı oluşturmanız gerekir. Visual Studio eklentisinin VSıX uzantısına nasıl dönüştürüleceği hakkında sık sorulan bazı soruların yanıtları aşağıda verilmiştir.  
  
> [!WARNING]
> Visual Studio 2015 ' den başlayarak, C# ve Visual Basic projeleri için VSıX projesini ve menü komutları, araç pencereleri ve VSPackages için öğe şablonları ekleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 2015 SDK 'daki](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)yenilikler.  
  
> [!IMPORTANT]
> Çoğu durumda, eklenti kodunuzu VSPackage proje öğesiyle bir VSıX projesine aktarmanız yeterlidir. Metodunu çağırarak DTE Otomasyon nesnesini alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
>   
> `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
> Daha fazla bilgi için bkz. [eklenti kodumu bir VSPackage Içinde nasıl çalıştırabilirim?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin)  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>VSıX uzantıları geliştirmem gereken yazılımlar nelerdir?  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Uzantı belgeleri nerede?  
 [Visual Studio uzantıları geliştirmeye başlama](../extensibility/starting-to-develop-visual-studio-extensions.md)ile başlayın. MSDN 'de VSSDK uzantı geliştirmesi ile ilgili diğer makaleler bunun altınlardır.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Eklenti projem bir VSıX projesine dönüştürebilir miyim?  
 VSıX projelerinde kullanılan mekanizmalar eklenti projelerindeki olanlarla aynı olmadığından, eklenti projesi doğrudan bir VSıX projesine dönüştürülemez. VSıX proje şablonu ve doğru proje öğesi şablonları, bir VSıX uzantısı olarak çalışmaya ve çalıştırmaya daha kolay bir şekilde kod sunar.  
  
## <a name="how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a> VSıX uzantıları geliştirmeye Nasıl yaparım? misiniz?  
 Bir menü komutu olan bir VSıX 'i aşağıda bulabilirsiniz:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Bir menü komutuna sahip bir VSıX uzantısı oluşturmak için  
  
1. VSıX projesi oluşturun. ( **Hızlı başlatma** penceresinde**Dosya**, **Yeni**, **Proje**veya tür **projesi** ). **Yeni proje** Iletişim kutusunda **Visual C#/genişletilebilirlik** veya **Visual Basic/genişletilebilirlik** ' i genişletin ve **VSIX projesi**' ni seçin.) Projeyi **Testexgeri** olarak adlandırın ve bir konum belirtin.  
  
2. Özel bir **komut** projesi öğe şablonu ekleyin. ( **Çözüm Gezgini** proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. Visual C# veya Visual Basic için **Yeni proje** iletişim kutusunda, **genişletilebilirlik** düğümünü seçin ve **özel komut**' yi seçin.)  
  
3. Projeyi derleyip hata ayıklama modunda çalıştırmak için F5 tuşuna basın.  
  
     Visual Studio 'nun ikinci bir örneği görüntülenir. Bu ikinci örneğe deneysel örnek denir ve kod yazmak için kullanmakta olduğunuz Visual Studio örneğiyle aynı ayarlara sahip olmayabilir. Deneysel örneği ilk kez çalıştırdığınızda, VS Online 'da oturum açmanız ve temanızı ve profilinizi belirtmeniz istenecektir.  
  
     **Araçlar** menüsünde (deneysel örnekte) **komut adı**adlı bir düğme görmeniz gerekir. Bu düğmeyi seçtiğinizde, bir ileti şu şekilde görünmelidir: **TestVSPackagePackage. Menuıitemcallback () içinde**.  
  
## <a name="how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a> Eklenti kodumu VSPackage içinde nasıl çalıştırabilirim?  
 Eklenti kodu genellikle iki şekilde çalışır:  
  
- Bir menü komutu tarafından tetiklendi (kod `IDTCommandTarget.Exec` yönteminde bulunur)  
  
- Otomatik olarak başlangıçta (kod `OnConnection` olay işleyicisidir.)  
  
  VSPackage 'ta aynı şeyleri yapabilirsiniz. Geri çağırma yöntemine bir eklenti kodu eklemek için aşağıdaki adımları uygulayın:  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>VSPackage içinde bir menü komutu uygulamak için  
  
1. Menü komutuna sahip bir VSPackage oluşturun. (Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2. VSPackage tanımını içeren dosyayı açın. (Bir C# projesinde, <em>\<your project name></em> Package.cs.)  
  
3. Aşağıdaki `using` deyimlerini dosyasına ekleyin:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Yöntemini bulun `MenuItemCallback` . <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>Nesnesini almak için bir çağrısı ekleyin <xref:EnvDTE80.DTE2> :  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Eklentisinin metoduna sahip olduğu kodu ekleyin `IDTCommandTarget.Exec` . Örneğin, **çıktı** penceresine yeni bir bölme ekleyen ve yeni bölmedeki "bazı metinler" yazdıran bazı kodlar aşağıda verilmiştir.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. Bu projeyi derleyin ve çalıştırın. F5 tuşuna basın veya **hata ayıklama** araç çubuğundan **Başlat** ' ı seçin. Visual Studio 'nun deneysel örneğinde, **Araçlar** menüsünde **komut adı**adlı bir düğme olmalıdır. Bu düğmeyi seçtiğinizde, **bazı metinlerin** sözcükleri **Çıkış** penceresi bölmesinde görünmelidir. ( **Çıkış** penceresini açmanız gerekebilir.)  
  
   Ayrıca, kodunuzun başlangıçta çalıştırılmasını sağlayabilirsiniz. Ancak bu yaklaşım, VSPackage uzantıları için genellikle önerilmez. Visual Studio başlatıldığında çok fazla uzantı yüklenmeye çalışırsanız, başlangıç saati daha fazla zaman zaman alabilir. Yalnızca bir koşul karşılandığında (açılan bir çözüm gibi) VSPackage 'ı otomatik olarak yüklemek daha iyi bir uygulamadır.  
  
   Bu yordamda, eklenti kodunun bir çözüm açıldığında otomatik olarak yüklenen VSPackage içinde nasıl çalıştırılacağı gösterilmektedir:  
  
#### <a name="to-autoload-a-vspackage"></a>VSPackage 'ı Oto için yükleme  
  
1. Visual Studio Package proje öğesiyle bir VSıX projesi oluşturun. (Bunu yapmak için adımlar için bkz. [nasıl yaparım? VSIX uzantıları geliştirmeye başlama?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Bunun yerine **Visual Studio Package** Proje öğesini eklemeniz yeterlidir.) VSıX projesi **TestAutoload**adını adlandırın.  
  
2. TestAutoloadPackage.cs 'i açın. Paket sınıfının bildirildiği satırı bulun:  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. Bu satırın üstünde bir öznitelikler kümesi vardır. Bu özniteliği ekleyin:  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. Yöntemde bir kesme noktası ayarlayın `Initialize()` ve hata ayıklamayı başlatın (F5).  
  
5. Deneysel örnekte bir proje açın. VSPackage yüklemesi gerekir ve kesme noktası isabet etmelidir.  
  
   İçindeki alanlarını kullanarak VSPackage ' ın yükleneceği diğer bağlamlar belirleyebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> . Daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>DTE nesnesini nasıl alabilirim?  
 Eklentileriniz Kullanıcı arabirimi (örneğin, menü komutları, araç çubuğu düğmeleri veya araç pencereleri) görüntülemezken, VSPackage 'dan DTE Automation nesnesini alırken kodunuzun olduğu sürece kodunuzu kullanabilirsiniz. Bunu yapmak için:  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Bir VSPackage 'dan DTE nesnesini almak için  
  
1. Visual Studio Package öğe şablonuna sahip bir VSıX projesinde, <em>\<project name></em> Package.cs dosyasını arayın. Bu, sınıfından türetilen sınıftır <xref:Microsoft.VisualStudio.Shell.Package> ; Visual Studio ile etkileşime başlamanıza yardımcı olabilir. Bu durumda, <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> nesnesini almak için öğesini kullanırsınız <xref:EnvDTE80.DTE2> .  
  
2. Şu `using` deyimleri ekleyin:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
3. Yöntemini bulun `Initialize` . Bu yöntem, paket sihirbazında belirttiğiniz komutu işler. <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>DTE nesnesini almak için bir çağrısı ekleyin:  
  
   ```csharp  
   DTE dte = (DTE)GetService(typeof(DTE));  
   ```  
  
   Otomasyon nesnesine sahip olduktan sonra <xref:EnvDTE.DTE> , eklenti kodunuzun geri kalanını projeye ekleyebilirsiniz. Nesneye ihtiyacınız varsa <xref:EnvDTE80.DTE2> , aynı şeyi yapabilirsiniz.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Nasıl yaparım? menü komutlarını ve araç çubuğu düğmelerini VSPackage stiline ekleme.  
 VSPackage uzantıları, menü komutlarının, araç çubuklarının, araç çubuğu düğmelerinin ve diğer Kullanıcı arabiriminin çoğunu oluşturmak için. vsct dosyasını kullanır. **Özel komut** proje öğesi şablonu, **Araçlar** menüsünde bir komut oluşturma seçeneği sunar. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 . Vsct dosyaları hakkında daha fazla bilgi için bkz. [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Menü öğeleri, araç çubukları ve araç çubuğu düğmeleri eklemek için. vsct dosyasını nasıl kullanacağınızı gösteren talimatlar için bkz. [genişletme menüleri ve komutları](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>VSPackage yöntemiyle özel araç pencereleri mi Nasıl yaparım??  
 Özel araç penceresi proje öğesi şablonu, size bir araç penceresi oluşturma seçeneği sunar. Bu proje öğesi şablonu hakkında daha fazla bilgi için bkz. [bir araç penceresi Ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md). Araç pencereleri hakkında daha fazla bilgi için bkz. araç pencerelerini ve içindeki makaleleri [genişletme ve özelleştirme](../extensibility/extending-and-customizing-tool-windows.md) , özellikle [bir araç penceresi ekleme](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Visual Studio pencerelerini VSPackage yöntemiyle yönetmek Nasıl yaparım??  
 Eklentilerinizin Visual Studio pencerelerini yönetmesi durumunda eklenti kodu bir VSPackage içinde çalışmalıdır. Örneğin, bu yordam, **Task List** VSPackage yöntemine görev listesi yöneten kodun nasıl ekleneceğini gösterir `MenuItemCallback` .  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Bir eklentiden bir VSPackage 'a pencere yönetim kodu eklemek için  
  
1. Bir menü komutuna sahip bir VSPackage oluşturun [nasıl yaparım? VSIX uzantıları geliştirmeye başla?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) bölümünde olduğu gibi.  
  
2. VSPackage tanımını içeren dosyayı açın. (Bir C# projesinde, <em>\<your project name></em> Package.cs.)  
  
3. Şu `using` deyimleri ekleyin:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Yöntemini bulun `MenuItemCallback` . <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>Nesnesini almak için bir çağrısı ekleyin <xref:EnvDTE80.DTE2> :  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Eklentiinizden kodu ekleyin. Örneğin, **görev listesi**yeni görevler ekleyen, görev sayısını listeleyen ve sonra bir görevi silen bazı kodlar aşağıda verilmiştir.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)   
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
       TaskList tl = (TaskList)dte.ToolWindows.TaskList;   
       askItem tlItem;   
  
       // Add a couple of tasks to the Task List.   
       tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",    
           vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,   
           true, "", 10, true, true);  
       tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",   
           vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);  
  
       // List the total number of task list items after adding the new task items.  
       System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);  
       System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
  
       // Remove the second task item. The items list in reverse numeric order.   
       System.Windows.Forms.MessageBox.Show("Deleting the second task item");  
       tl.TaskItems.Item(2).Delete();  
       System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
   }  
   ```  
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>VSPackage 'ta projeleri ve çözümleri yönetmek Nasıl yaparım?.  
 Eklentileriniz projeleri ve çözümleri yönetirse, eklenti kodu bir VSPackage içinde çalışmalıdır. Örneğin, bu yordam, başlangıç projesini alan kodun nasıl ekleneceğini gösterir.  
  
1. Bir menü komutuna sahip bir VSPackage oluşturun [nasıl yaparım? VSIX uzantıları geliştirmeye başla?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) bölümünde olduğu gibi.  
  
2. VSPackage tanımını içeren dosyayı açın. (Bir C# projesinde, <em>\<your project name></em> Package.cs.)  
  
3. Şu `using` deyimleri ekleyin:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Yöntemini bulun `MenuItemCallback` . <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>Nesnesini almak için bir çağrısı ekleyin <xref:EnvDTE80.DTE2> :  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Eklentiinizden kodu ekleyin. Örneğin, aşağıdaki kod bir çözümde başlangıç projesinin adını alır. (Bu paket çalıştırıldığında çoklu proje çözümünün açık olması gerekir.)  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
       SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;   
       Project startupProj;   
       string msg = "";  
  
       foreach (String item in (Array)sb.StartupProjects)   
       {  
           msg += item;   
       }  
       System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);   
       startupProj = dte.Solution.Item(msg);   
       System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);   
   }  
   ```  
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>VSPackage 'ta klavye kısayollarını ayarlamak Nasıl yaparım??  
 `<KeyBindings>`. Vsct dosyasının öğesini kullanırsınız. Aşağıdaki örnekte, komut için klavye kısayolu `idCommand1` alt + a, komutun klavye kısayolu Ise `idCommand2` alt + CTRL + A olur. Anahtar adlarına ilişkin sözdizimine dikkat edin.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>VSPackage içindeki Automation olaylarını Nasıl yaparım?.  
 Bir VSPackage içindeki Automation olaylarını, eklentiinizdeki ile aynı şekilde idare edersiniz. Aşağıdaki kod, olayın nasıl işleneceğini gösterir `OnItemRenamed` . (Bu örnek, DTE nesnesini zaten aldığını varsayar.)  
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```
