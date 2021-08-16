---
title: Project öğenin özelliğini kalıcı hale getirme | Microsoft Docs
description: Özelliği Genişletilmiş proje dosyanızdaki proje dosyasında depolayarak proje öğesine eklediğiniz bir özelliği kalıcı hale getirme hakkında bilgi edinin.
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
ms.openlocfilehash: e201b60ea4634c6960d6e98c64214deadd62a6b7608cb73d15b71bf2a497254f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305288"
---
# <a name="persist-the-property-of-a-project-item"></a>Proje öğesinin özelliğini kalıcı hale getirme
Bir kaynak dosyanın yazarı gibi bir proje öğesine eklediğiniz bir özelliği kalıcı hale getirmek isteyebilirsiniz. Bunu, özelliği proje dosyasında depolayarak yapabilirsiniz.

 Bir proje dosyasında bir özelliği kalıcı hale getirmek için ilk adım, projenin hiyerarşisini arabirim olarak elde etmek <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . Bu arabirimi Otomasyon kullanarak veya kullanarak elde edebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . Arabirimi edindikten sonra, o anda hangi proje öğesinin seçili olduğunu anlamak için kullanabilirsiniz. Proje öğesi KIMLIĞI ' ne sahip olduktan sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> özelliğini eklemek için kullanabilirsiniz.

 Aşağıdaki yordamlarda, *VsPkg. cs* özelliğini `Author` Proje dosyasındaki değeriyle kalıcı hale getirin `Tom` .

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>DTE nesnesi ile proje hiyerarşisini almak için

1. VSPackage 'a aşağıdaki kodu ekleyin:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Proje öğesi özelliğini DTE nesnesi ile kalıcı hale getirmek için

1. Aşağıdaki kodu, önceki yordamdaki yönteminde verilen koda ekleyin:

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Ismonitorselection kullanarak proje hiyerarşisini elde etmek için

1. VSPackage 'a aşağıdaki kodu ekleyin:

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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Proje hiyerarşisi belirtilen seçili proje öğesi özelliğini kalıcı hale getirmek için

1. Aşağıdaki kodu, önceki yordamdaki yönteminde verilen koda ekleyin:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Özelliğin kalıcı olduğunu doğrulamak için

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Bir çözüm başlatın ve açın veya oluşturun.

2. **Çözüm Gezgini** Içindeki VsPkg. cs Proje öğesini seçin.

3. Bir kesme noktası kullanın veya VSPackage 'un yüklendiğini ve SetItemAttribute 'ın çalıştığını saptayın.

   > [!NOTE]
   > UI bağlamında bir VSPackage 'ı tekrar yükleyebilirsiniz <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . Daha fazla bilgi için bkz. [VSPackages yükleme](../extensibility/loading-vspackages.md).

4. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Not Defteri ' de proje dosyasını kapatın ve sonra açın. \<Author>Aşağıdaki gibi, Tom değeri ile etiketini görmeniz gerekir:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Özel araçlar](../extensibility/internals/custom-tools.md)
