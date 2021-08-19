---
title: Project Item | Microsoft Docs
description: Özelliği genişletilmiş proje türünüz içinde proje dosyasında depolayarak bir proje öğesine ekley istediğiniz özelliğin nasıl kalıcı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6747329014eced976fd6b21737c86dd7e073943d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102135"
---
# <a name="persist-the-property-of-a-project-item"></a>Proje öğesinin özelliğini kalıcı olarak kalıcı olarak
Kaynak dosyanın yazarı gibi bir proje öğesine ekley istediğiniz bir özelliği kalıcı olarak kalıcı yapmak istiyor olabilir. Bunu yapmak için özelliğini proje dosyasında depoabilirsiniz.

 Proje dosyasındaki bir özelliği kalıcı yapmak için ilk adım, projenin hiyerarşisini arabirim olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> almaktır. Bu arabirimi Otomasyon veya kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> edinebilirsiniz. Arabirimi elde ettikten sonra, o anda hangi proje öğesinin seçili olduğunu belirlemek için kullanabilirsiniz. Proje öğesi kimliğine sahip olduktan sonra özelliğini <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> eklemek için kullanabilirsiniz.

 Aşağıdaki yordamlarda, *VsPkg.cs özelliğini* proje `Author` dosyasındaki `Tom` değeriyle kalıcı olarak bulundurabilirsiniz.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>DTE nesnesiyle proje hiyerarşisini almak için

1. VSPackage dosyanıza aşağıdaki kodu ekleyin:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Proje öğesi özelliğini DTE nesnesiyle kalıcı yapmak için

1. Önceki yordamda yönteminde verilen koda aşağıdaki kodu ekleyin:

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>IVsMonitorSelection kullanarak proje hiyerarşisini almak için

1. VSPackage dosyanıza aşağıdaki kodu ekleyin:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Proje hiyerarşisi verilmelidir, seçili proje öğesi özelliğini kalıcı yapmak için

1. Önceki yordamda yönteminde verilen koda aşağıdaki kodu ekleyin:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Özelliğin kalıcı olduğunu doğrulamak için

1. Çözümü [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] başlatarak ve ardından açın veya oluşturun.

2. içinde VsPkg.cs proje **öğesini Çözüm Gezgini.**

3. Bir kesme noktası kullanın veya VSPackage'nizin yükleniyor ve SetItemAttribute'ın çalıştırılmış olduğunu başka bir şekilde belirler.

   > [!NOTE]
   > KULLANıCı arabirimi bağlamında bir VSPackage'i otomatik olarak yük <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> devredebilir. Daha fazla bilgi için [bkz. VSPackage'ları Yükleme.](../extensibility/loading-vspackages.md)

4. Proje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dosyasını kapatın ve ardından proje dosyasını Not Defteri. Tom değerinin \<Author> yer alan etiketini aşağıdaki gibi görüyor gerekir:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Özel araçlar](../extensibility/internals/custom-tools.md)
