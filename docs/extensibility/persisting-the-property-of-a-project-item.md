---
title: Proje Öğesinin Özelliğini Kalıcıyor | Microsoft Dokümanlar
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702206"
---
# <a name="persist-the-property-of-a-project-item"></a>Proje öğesinin özelliğini devam etti
Kaynak dosyanın yazarı gibi proje öğesine eklediğiniz bir özelliği kalıcı olarak sürdürmek isteyebilirsiniz. Bunu, özelliği proje dosyasında depolayarak yapabilirsiniz.

 Proje dosyasındaki bir özelliği kalıcı olarak sürdürmek için ilk adım, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirim olarak projenin hiyerarşisini elde etmektir. Bu arabirimi Otomasyon'u kullanarak veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Arabirimi elde ettikten sonra, hangi proje öğesinin şu anda seçili olduğunu belirlemek için bu arabirimi kullanabilirsiniz. Proje öğesi kimliğini aldıktan sonra, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> özelliği eklemek için kullanabilirsiniz.

 Aşağıdaki yordamlarda, proje dosyasındaki `Author` değerle `Tom` *VsPkg.cs* özelliğini devam ettirsiniz.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>DTE nesnesi ile proje hiyerarşisini elde etmek için

1. VSPackage'ınıza aşağıdaki kodu ekleyin:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>DTE nesnesi ile proje öğesi özelliğini devam etmek için

1. Önceki yordamda yöntemde verilen koda aşağıdaki kodu ekleyin:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>IVsMonitorSelection kullanarak proje hiyerarşisini elde etmek için

1. VSPackage'ınıza aşağıdaki kodu ekleyin:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Proje hiyerarşisi göz önüne alındığında, seçili proje öğesi özelliğini sürdürmek için

1. Önceki yordamda yöntemde verilen koda aşağıdaki kodu ekleyin:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Özelliğin kalıcı olduğunu doğrulamak için

1. Başlatın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve sonra açın veya bir çözüm oluşturun.

2. **Çözüm Gezgini'nde**proje öğesini VsPkg.cs seçin.

3. Bir kesme noktası kullanın veya VSPackage'ınızın yüklendiğini ve SetItemAttribute'in çalıştığını belirleyin.

   > [!NOTE]
   > Bir VSPackage'ı UI bağlamında <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>otomatik olarak yükleyebilirsiniz. Daha fazla bilgi için [Load VSPackages'e](../extensibility/loading-vspackages.md)bakın.

4. Proje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dosyasını Notepad'de kapatın ve açın. \<Yazar> değeri Tom ile etiketini aşağıdaki gibi görmelisiniz:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Özel araçlar](../extensibility/internals/custom-tools.md)
