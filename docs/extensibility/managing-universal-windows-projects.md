---
title: Evrensel Windows Projelerini Yönetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc6894bcfe3bfab3b0246d716b0bd85152ad17e2
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744943"
---
# <a name="manage-universal-windows-projects"></a>Evrensel Windows projelerini yönetme

Evrensel Windows uygulamaları, geliştiricilerin her iki platformda da kod ve diğer varlıkları kullanmasına olanak tanıyan, hem Windows 8.1 hem de Windows Phone 8.1'i hedefleyen uygulamalardır. Paylaşılan kod ve kaynaklar paylaşılan bir projede tutulurken, platforma özgü kod ve kaynaklar biri Windows, diğeri Windows Phone için olmak üzere ayrı projelerde tutulur. Evrensel Windows uygulamaları hakkında daha fazla bilgi için [Evrensel Windows uygulamalarına](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx)bakın. Projeleri yöneten Visual Studio uzantıları, evrensel Windows uygulama projelerinin tek platformlu uygulamalardan farklı bir yapıya sahip olduğunu bilmelidir. Bu izlik, paylaşılan projede nasıl gezindiğinizi ve paylaşılan öğeleri nasıl yönetebildiğinizi gösterir.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak eklenmiştir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="navigate-the-shared-project"></a>Paylaşılan projede gezinme

1. **TestUniversalProject**adında bir C# VSIX projesi oluşturun. (**Dosya** > **Yeni** > **Proje** ve sonra **C#** > **Genişletilebilirlik** > Görsel Stüdyo**Paketi**). Özel **Komut** proje öğesi şablonu ekleyin **(Çözüm Gezgini'nde,** proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin, ardından **Genişletilebilirlik'e**gidin). Dosyayı **TestUniversalProject**olarak adlandırın.

2. *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* ve *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* adresine **(Uzantılar** bölümünde) bir başvuru ekleyin.

3. *TestUniversalProject.cs* açın ve `using` aşağıdaki yönergeleri ekleyin:

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

4. `TestUniversalProject` Sınıfta **Çıkış** penceresine işaret eden özel bir alan ekleyin.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. TestUniversalProject oluşturucu içindeki çıkış bölmesine başvuruyu ayarlayın:

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

6. Varolan kodu `ShowMessageBox` yöntemden kaldırın:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Bu izlenecek yolda birkaç farklı amaç için kullanacağımız DTE nesnesini alın. Ayrıca, menü düğmesine tıklandığında bir çözümün yüklendiğinden emin olun.

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

8. Paylaşılan projeyi bulun. Paylaşılan proje saf bir kapsayıcıdır; çıktı lar oluşturmaz veya üretmez. Aşağıdaki yöntem, paylaşılan proje yeteneğine sahip <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nesneyi arayarak çözümdeki ilk paylaşılan projeyi bulur.

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

9. `ShowMessageBox` Yöntemde, paylaşılan projenin alt yazısını **(Çözüm Gezgini'nde**görünen proje adı) çıktın.

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

10. Etkin platform projesini alın. Platform projeleri, platforma özgü kod ve kaynaklar içeren projelerdir. Aşağıdaki yöntem, etkin <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> platform projesini almak için yeni alanı kullanır.

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

11. `ShowMessageBox` Yöntemde, etkin platform projesinin alt yazısını çıktı.

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

12. Platform projeleri aracılığıyla yineleyin. Aşağıdaki yöntem paylaşılan projeden tüm alma (platform) projeleri alır.

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
    > Kullanıcı deneysel örnekte bir C++ evrensel Windows uygulaması projesi açtıysa, yukarıdaki kod bir özel durum oluşturur. Bu bilinen bir sorundur. Özel durum lardan kaçınmak `foreach` için yukarıdaki bloğu aşağıdakilerle değiştirin:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. `ShowMessageBox` Yöntemde, her platform projesinin alt yazısını çıktı. Etkin platform projesinin alt yazısını oluşturan satırdan sonra aşağıdaki kodu ekleyin. Bu listede yalnızca yüklenen platform projeleri görünür.

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

14. Etkin platform projesini değiştirin. Aşağıdaki yöntem kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>etkin proje ayarlar.

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. `ShowMessageBox` Yöntemde, etkin platform projesini değiştirin. Bu kodu `foreach` bloğun içine ekleyin.

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

16. Şimdi dene. Deneysel örneği başlatmak için F5 tuşuna basın. Deneysel örnekte bir C# evrensel hub uygulaması projesi oluşturun **(Yeni Proje** iletişim kutusu, **Visual C#** > **Windows** > **Windows 8** > **Universal** > **Hub Uygulaması).** Çözüm yüklendikten sonra **Araçlar** menüsüne gidin ve **TestUniversalProject'i Çağır'ı**tıklatın ve çıktı bölmesindeki metni denetleyin. **Output** Aşağıdakine benzer bir şey görmeniz gerekir:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Platform projesinde paylaşılan öğeleri yönetme

1. Platform projesinde paylaşılan öğeleri bulun. Paylaşılan projedeki öğeler platform projesinde paylaşılan öğeler olarak görünür. **Çözüm Gezgini'nde**göremezsiniz, ancak bunları bulmak için proje hiyerarşisinde yürüyebilirsiniz. Aşağıdaki yöntem hiyerarşiyi yürütır ve paylaşılan tüm öğeleri toplar. İsteğe bağlı olarak her öğenin alt yazısını çıkarır. Paylaşılan öğeler yeni özellik <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>tarafından tanımlanır.

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

2. `ShowMessageBox` Yöntemde, platform proje hiyerarşisi öğelerini yürümek için aşağıdaki kodu ekleyin. `foreach` Bloğun içine takın.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Paylaşılan öğeleri okuyun. Paylaşılan öğeler platform projesinde gizli bağlantılı dosyalar olarak görünür ve tüm özellikleri sıradan bağlantılı dosyalar olarak okuyabilirsiniz. Aşağıdaki kod, ilk paylaşılan öğenin tam yolunu okur.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Şimdi dene. Deneysel örneği başlatmak için **F5** tuşuna basın. Deneysel örnekte **(Yeni Proje** iletişim kutusunda, **Visual C#** > **Windows Windows** > **8** > **Universal** > **Hub App)** bir C# evrensel hub uygulaması projesi oluşturun Araçlar menüsüne gidin ve **TestUniversalProject'i çağır'ı**tıklatın ve **ardından Çıktı** bölmesindeki metni denetleyin. **Tools** Aşağıdakine benzer bir şey görmeniz gerekir:

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Platform projelerindeki ve paylaşılan projelerdeki değişiklikleri algılama

1. Hiyerarşi ve proje olaylarını, platform projelerinde olduğu gibi paylaşılan projelerdeki değişiklikleri algılamak için kullanabilirsiniz. Ancak, paylaşılan projedeki proje öğeleri görünmez, bu da paylaşılan proje öğeleri değiştirildiğinde belirli olayların yanmadığını anlamına gelir.

    Projedeki bir dosyanın adı yeniden adlandırıldığında, olayların sırasını göz önünde bulundurun:

   1. Dosya adı diskte değiştirilir.

   2. Proje dosyası, dosyanın yeni adını içerecek şekilde güncelleştirilir.

      Hiyerarşi olayları (örneğin,) <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>genellikle Çözüm **Gezgini'nde**olduğu gibi UI'de görüntülenen değişiklikleri izler. Hiyerarşi olayları, dosya silme ve ardından bir dosya ekinden oluşan bir dosya yeniden adlandırma işlemini dikkate alır. Ancak, görünmez öğeler değiştirildiğinde, hiyerarşi olay <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> sistemi bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> olay değil, bir olay yangınları. Bu nedenle, bir platform projesinde bir dosyayı <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>yeniden adnız, her ikisini de alırsınız ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>, paylaşılan bir projede bir dosyayı yeniden adlarsanız, yalnızca .

      Proje öğelerindeki değişiklikleri izlemek için DTE proje öğesi olaylarını <xref:EnvDTE.ProjectItemsEventsClass>(bulunanlar) işleyebilirsiniz. Ancak, çok sayıda olayı ele alıyorsanız, 'deki <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>olayları daha iyi işleyebilirsiniz. Bu izne yalnızca hiyerarşi olayları ve DTE olayları gösteririz. Bu yordamda paylaşılan bir projeye ve bir platform projesine bir olay dinleyicisi eklersiniz. Daha sonra, paylaşılan bir projede bir dosyayı ve bir platform projesindeki başka bir dosyayı yeniden adlandırdığınızda, her yeniden adlandırma işlemi için başlatılan olayları görebilirsiniz.

      Bu yordamda paylaşılan bir projeye ve bir platform projesine bir olay dinleyicisi eklersiniz. Daha sonra, paylaşılan bir projede bir dosyayı ve bir platform projesindeki başka bir dosyayı yeniden adlandırdığınızda, her yeniden adlandırma işlemi için başlatılan olayları görebilirsiniz.

2. Olay dinleyicisi ekleyin. Projeye yeni bir sınıf dosyası ekleyin ve *HierarchyEventListener.cs.*

3. *HierarchyEventListener.cs* dosyasını açın ve yönergeleri kullanarak aşağıdaki leri ekleyin:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. `HierarchyEventListener` Sınıf uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>var:

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Aşağıdaki kodda <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>olduğu gibi, üyeleri uygulayın.

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

6. Aynı sınıfta, proje öğesi yeniden adlandırıldığında <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>oluşan DTE olayı için başka bir olay işleyicisi ekleyin.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Hiyerarşi etkinlikleri için kaydolun. Takip ettiğiniz her proje için ayrı ayrı kaydolmanız gerekir. Biri paylaşılan proje `ShowMessageBox`için, diğeri de platform projelerinden biri için aşağıdaki kodu ekleyin.

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

8. DTE proje öğesi etkinliği <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>için kaydolun. İkinci dinleyiciyi bağladıktan sonra aşağıdaki kodu ekleyin.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Paylaşılan öğeyi değiştirin. Bir platform projesinde paylaşılan öğeleri değiştiremezsiniz; bunun yerine, bunları bu öğelerin gerçek sahibi olan paylaşılan projede değiştirmeniz gerekir. Paylaşılan projede <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>ilgili madde kimliğini, paylaşılan öğenin tam yolunu vererek alabilirsiniz. Ardından paylaşılan öğeyi değiştirebilirsiniz. Değişiklik platform projelerine yayılır.

    > [!IMPORTANT]
    > Proje öğesini değiştirmeden önce paylaşılan bir öğe olup olmadığını öğrenmelisiniz.

     Aşağıdaki yöntem, proje öğesi dosyasının adını değiştirir.

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

10. Paylaşılan projedeki öğeyi dosya `ShowMessageBox` adını değiştirmek için diğer tüm koddan sonra bu yöntemi çağırın. Paylaşılan projede maddenin tam yolunu alan koddan sonra bunu ekleyin.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Projeyi oluşturun ve çalıştırın. Deneysel örnekte bir C# evrensel hub uygulaması oluşturun, **Araçlar** menüsüne gidin ve **TestUniversalProject'i Çağır'ı**tıklatın ve genel çıktı bölmesindeki metni denetleyin. Paylaşılan projedeki ilk öğenin adı *(App.xaml* dosyası olmasını bekliyoruz) değiştirilmeli ve <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> olayın ateşlediğini görmelisiniz. Bu durumda, *App.xaml'ı* yeniden *adlandırmak App.xaml.cs* de yeniden adlandırılmasına neden olduğundan, dört olay (her platform projesi için iki) görmeniz gerekir. (DTE olayları paylaşılan projedeki öğeleri izlemez.) İki <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> olay (platform projelerinin her biri için <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> bir tane) görmeniz gerekir, ancak olay görmezsiniz.

12. Şimdi bir platform projesinde bir dosyayı yeniden adlandırmayı deneyin ve ateşlenen olaylardaki farkı görebilirsiniz. Aramadan `ShowMessageBox` sonra aşağıdaki kodu `ModifyFileName`ekleyin.

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

13. Projeyi oluşturun ve çalıştırın. Deneysel örnekte bir C# Evrensel Projesi oluşturun, **Araçlar** menüsüne gidin ve **TestUniversalProject'i Çağır'ı**tıklatın ve genel çıktı bölmesindeki metni denetleyin. Platform projesindeki dosya yeniden adlandırıldıktan sonra, hem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> olayı hem de bir olayı görmeniz gerekir. Dosyayı değiştirmek başka dosyanın değiştirilmesine neden olmadığından ve bir platform projesindeki öğelerde yapılan değişiklikler hiçbir yerde yayılmadığından, bu olayların yalnızca biri vardır.
