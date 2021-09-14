---
title: Universal Windows Projelerini yönetme | Microsoft Docs
description: Universal Windows uygulamalarını desteklemek Visual Studio, projeleri yöneten tüm uzantıların Evrensel uygulama projesi yapısına Windows olması gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d6e34a8cb8da8158eae9e6c245da45fa37d59b4e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724961"
---
# <a name="manage-universal-windows-projects"></a>Universal Windows projelerini yönetme

Evrensel Windows uygulamaları hem Windows 8.1 hem de Windows Phone 8.1'i hedef alan uygulamalardır ve geliştiricilerin her iki platformda da kod ve diğer varlıkları kullanmasına olanak sağlar. Paylaşılan kod ve kaynaklar paylaşılan projede tutulurken, platforma özgü kod ve kaynaklar ayrı projelerde, biri Windows diğeri de Windows Phone. Evrensel uygulama uygulamaları hakkında daha fazla Windows için [bkz. Evrensel Windows uygulamaları.](/windows/uwp/get-started/create-uwp-apps) Visual Studio yöneten uzantılar, evrensel Windows uygulama projelerinin tek platform uygulamalardan farklı bir yapıya sahip olduğunun farkındadır. Bu izlenecek yol, paylaşılan projede gezinmeyi ve paylaşılan öğeleri yönetmeyi gösterir.

## <a name="prerequisites"></a>Önkoşullar

2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Kurulumda isteğe bağlı bir özellik olarak Visual Studio dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="navigate-the-shared-project"></a>Paylaşılan projede gezinme

1. **TestUniversalProject** adlı bir C# VSIX projesi oluşturun. (**Dosya**  >  **Yeni**  >  **Project** ve ardından **C#**  >  **Genişletilebilirliği**  >  **Visual Studio Paketi).** Özel Komut **proje öğesi** şablonu ekleyin **(Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe Ekle'yi seçin, ardından  >   **Genişletilebilirlik'e gidin).** Dosyaya **TestUniversalProject adını girin.**

2. Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll *ve* *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* bir başvuru ekleyin **(Uzantılar bölümünde).**

3. *TestUniversalProject.cs'yi* açın ve aşağıdaki `using` yönergeleri ekleyin:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. sınıfında `TestUniversalProject` Çıkış penceresine işaret edecek özel bir **alan** ekleyin.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. TestUniversalProject oluşturucusu içindeki çıkış bölmesine başvuru ayarlayın:

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }

        // get a reference to the Output window
        output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. Mevcut kodu yönteminden `ShowMessageBox` kaldırın:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Bu kılavuzda birkaç farklı amaçla kullaneceğimiz DTE nesnesini elde edersiniz. Ayrıca, menü düğmesine tıkıldığında bir çözümün yüklendiğinden emin olun.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Paylaşılan projeyi bulun. Paylaşılan proje saf bir kapsayıcıdır; çıkış oluşturmaz veya üretmez. Aşağıdaki yöntem, paylaşılan proje özelliğine sahip nesneyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> araarak çözümde ilk paylaşılan projeyi bulur.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. yönteminde, paylaşılan projenin açıklamalı alt yazısını `ShowMessageBox` **(Çözüm Gezgini** proje adı) çıkışını ekleyin.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Etkin platform projesini al. Platform projeleri, platforma özgü kod ve kaynaklar içeren projelerdir. Aşağıdaki yöntem, etkin platform projesini <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> almak için yeni alanı kullanır.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. yönteminde `ShowMessageBox` etkin platform projesinin açıklamalı alt yazısını çıkış olarak girin.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                    MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Platform projelerinde iterate. Aşağıdaki yöntem, paylaşılan projeden tüm içeri aktarma (platform) projelerini alır.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Kullanıcı deneysel örnekte bir C++ evrensel Windows uygulama projesi açtı ise, yukarıdaki kod bir özel durum oluşturur. Bu bilinen bir sorundur. Özel durumu önlemek için yukarıdaki `foreach` bloğu aşağıdakiyle değiştirin:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. `ShowMessageBox`yönteminde, her platform projesinin açıklamalı alt yazısını çıkış olarak girin. Etkin platform projesinin açıklamalı alt yazısını çıkış olarak alan satırın sonrasını aşağıdaki kodu ekleyin. Bu listede yalnızca yüklenen platform projeleri görüntülenir.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Etkin platform projesini değiştirme. Aşağıdaki yöntem kullanarak etkin projeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> ayarlar.

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. yönteminde `ShowMessageBox` etkin platform projesini değiştirebilirsiniz. Bu kodu bloğun içine `foreach` girin.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Şimdi deneyin. Deneysel örneği başlatmak için F5'e basın. Deneysel örnekte bir C# evrensel hub uygulaması  projesi oluşturun (Yeni Project iletişim **kutusunda, Visual C#**  >  **Windows**  >  **Windows 8**  >  **Evrensel**  >  **Hub Uygulaması).** Çözüm yüklendikten sonra Araçlar menüsüne gidin, **Test ÇağırUniversalProject**'e tıklayın ve Çıkış bölmesindeki **metni** kontrol edin.  Aşağıdakine benzer bir şey görmeniz gerekir:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Platform projesinde paylaşılan öğeleri yönetme

1. Platform projesinde paylaşılan öğeleri bulun. Paylaşılan projedeki öğeler platform projesinde paylaşılan öğeler olarak görünür. Bu Çözüm Gezgini proje hiyerarşisinde bunları göreyebilirsiniz. Aşağıdaki yöntem hiyerarşide yol gösterir ve paylaşılan tüm öğeleri toplar. İsteğe bağlı olarak her öğenin açıklamalı alt yazısını çıkış olarak gösterir. Paylaşılan öğeler yeni özelliğiyle <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> tanımlanır.

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
        }
    }
    ```

2. `ShowMessageBox`yönteminde, platform projesi hiyerarşi öğelerini adım adım takip etmek için aşağıdaki kodu ekleyin. Bunu bloğun içine `foreach` ekler.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Paylaşılan öğeleri okuyun. Paylaşılan öğeler platform projesinde gizli bağlı dosyalar olarak görünür ve tüm özellikleri normal bağlantılı dosyalar olarak okuyabilirsiniz. Aşağıdaki kod, ilk paylaşılan öğenin tam yolunu okur.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Şimdi deneyin. Deneysel örneği başlatmak için **F5'e** basın. Deneysel örnekte bir C# evrensel hub uygulaması projesi oluşturun **(Yeni Project** iletişim kutusunda **Visual C#** Windows Windows 8 Evrensel Hub Uygulaması) Araçlar menüsüne gidin ve  >    >    >    >   **TestUniversalProject**   Çağır'a tıklayın ve çıkış bölmesindeki metni kontrol edin. Aşağıdakine benzer bir şey görmeniz gerekir:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Platform projelerinde ve paylaşılan projelerde yapılan değişiklikleri algılama

1. Platform projelerinde olduğu gibi paylaşılan projelerde yapılan değişiklikleri algılamak için hiyerarşi ve proje olaylarını kullanabilirsiniz. Ancak, paylaşılan projedeki proje öğeleri görünür değildir, bu da paylaşılan proje öğeleri değiştiriken belirli olayların çalışmay olduğu anlamına gelir.

    Proje içinde bir dosya yeniden adlandırıldı olduğunda olay dizisini göz önünde bulundurabilirsiniz:

   1. Diskte dosya adı değiştirilir.

   2. Proje dosyası, dosyanın yeni adını içerecek şekilde güncelleştirilir.

      Hiyerarşi olayları (örneğin, ) genellikle kullanıcı arabiriminde görüntülenen değişiklikleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> Çözüm Gezgini.  Hiyerarşi olayları, bir dosya silme ve ardından dosya eklemeden oluşan bir dosya yeniden adlandırma işlemini dikkate alır. Ancak, görünmez öğeler değiştiriken, hiyerarşi olay sistemi bir olayı değil <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> bir olayı <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> sıyrılar. Bu nedenle, bir platform projesinde bir dosyayı yeniden adlandırırsanız hem hem de olur, ancak paylaşılan bir projede bir dosyayı yeniden adlandırırsanız <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> yalnızca elde olur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>

      Proje öğelerinde yapılan değişiklikleri izlemek için DTE proje öğesi olaylarını (içinde bulunanlar) <xref:EnvDTE.ProjectItemsEventsClass> işebilirsiniz. Ancak, çok sayıda olay işleseniz, içinde olayları işlemede daha iyi performans <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> eldeabilirsiniz. Bu kılavuzda yalnızca hiyerarşi olayları ve DTE olayları göstereceğiz. Bu yordamda, paylaşılan bir projeye ve platform projesine olay dinleyicisi eklersiniz. Ardından, paylaşılan bir projede bir dosyayı ve platform projesinde başka bir dosyayı yeniden adlandırırsanız, her yeniden adlandırma işlemi için işten atılacak olayları görebilirsiniz.

      Bu yordamda, paylaşılan bir projeye ve platform projesine olay dinleyicisi eklersiniz. Ardından, paylaşılan bir projede bir dosyayı ve platform projesinde başka bir dosyayı yeniden adlandırırsanız, her yeniden adlandırma işlemi için işten atılacak olayları görebilirsiniz.

2. Olay dinleyicisi ekleyin. Projeye yeni bir sınıf dosyası ekleyin ve *hierarchyEventListener.cs olarak çağırabilirsiniz.*

3. *HierarchyEventListener.cs dosyasını* açın ve aşağıdaki using yönergelerini ekleyin:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. sınıfının `HierarchyEventListener` uygulamasına sahip <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> olmak:

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Aşağıdaki kodda <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> olduğu gibi üyelerini uygulayın.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. Aynı sınıfta, bir proje öğesi yeniden adlandırıldıklarında oluşan DTE olayı <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> için başka bir olay işleyicisi ekleyin.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Hiyerarşi olayları için kaydolma. takipte olduğunu her proje için ayrı olarak kaydolmanız gerekir. Aşağıdaki kodu `ShowMessageBox` 'a, biri paylaşılan proje için, diğeri de platform projelerinden biri için ekleyin.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. DTE proje öğesi olayına <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> kaydolma. İkinci dinleyiciyi bağladikten sonra aşağıdaki kodu ekleyin.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Paylaşılan öğeyi değiştirme. Platform projesinde paylaşılan öğeleri değiştiremezsiniz; bunun yerine, bu öğelerin gerçek sahibi olan paylaşılan projede bunları değiştirmeniz gerekir. Paylaşılan projede ilgili öğe kimliğini ile elde etmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> paylaşılan öğenin tam yolunu sebilirsiniz. Ardından paylaşılan öğeyi değiştirebilirsiniz. Değişiklik platform projelerine yayıldı.

    > [!IMPORTANT]
    > Bir proje öğesini değiştirmeden önce paylaşılan bir öğe olup olmadığını bulmalı ve bu öğeyi değiştirebilirsiniz.

     Aşağıdaki yöntem, bir proje öğesi dosyasının adını değiştiren yöntemdir.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Paylaşılan projede öğenin dosya adını `ShowMessageBox` değiştirmek için içinde diğer tüm koddan sonra bu yöntemi çağırabilirsiniz. Paylaşılan projede öğenin tam yolunu alan koddan sonra bunu girin.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Projeyi derleme ve çalıştırma. Deneysel örnekte bir C# evrensel hub uygulaması  oluşturun, Araçlar menüsüne gidin ve **Test ÇağırUniversalProject**'e tıklayın ve genel çıkış bölmesindeki metni kontrol edin. Paylaşılan projede ilk öğenin adı *(App.xaml* dosyası olmasını bekliyoruz) değiştirilsin ve olayın başlatıldı <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> olduğunu görüyor olun. Bu durumda, *App.xaml* yeniden adlandırıldı çünkü *App.xaml.cs* de yeniden adlandırıldı, dört olay (her platform projesi için iki) görüyor gerekir. (DTE olayları paylaşılan projedeki öğeleri izlemez.) İki olay <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> (platform projelerinden her biri için bir tane) görüyor ancak olay <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> görmüyorsanız.

12. Şimdi bir platform projesinde bir dosyayı yeniden yeniden adı almaya çalışsanız da, işten çıkarlanacak olaylar arasındaki farkı anabilirsiniz. çağrısının sonrasını `ShowMessageBox` içinde aşağıdaki kodu `ModifyFileName` ekleyin.

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Projeyi derleme ve çalıştırma. Deneysel örnekte bir C# Universal Project oluşturun, Araçlar  menüsüne gidin, **Test ÇağırUniversalProject**'e tıklayın ve genel çıkış bölmesindeki metni kontrol edin. Platform projesinde dosya yeniden adlandırıldıktan sonra hem olayı hem de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> olayı görüyor <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> olun. Dosyanın değiştirilmesi başka dosyanın değiştirilmesine neden olduğu için ve bir platform projesinin öğelerinde yapılan değişiklikler herhangi bir yere yayılmayarak bu olayların yalnızca biri vardır.