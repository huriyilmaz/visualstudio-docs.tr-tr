---
title: Project öğeye öznitelik ekleme | Microsoft Docs
description: Visual Studio ' deki bir proje öğesine bir özniteliği ekleme hakkında bilgi edinmek için, bkz. gettıtemattribute ve setitemattribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8e79380bcd293013ff466991becee9bd61e43d98884090eb9696e9135fa96076
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378239"
---
# <a name="add-an-attribute-to-a-project-item"></a>Proje öğesine öznitelik ekleme
Yöntemler <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> bir proje öğesinin özniteliklerinin değerini alır ve ayarlar. SetItemAttribute, zaten mevcut değilse özniteliği oluşturur ve proje öğesi meta verilerine ekler.

## <a name="add-an-attribute-to-a-project-item"></a>Proje öğesine öznitelik ekleme

- Aşağıdaki kod, <xref:EnvDTE.DTE> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> bir proje öğesine öznitelik eklemek için Automation nesnesini ve yöntemini kullanır. Proje öğesi KIMLIĞI, "program. cs" proje öğesi adından elde edilir. "MyAttribute" özniteliği bu proje öğesine eklenir ve "MyValue" değeri verilir.

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild proje dosyasında verileri kalıcı hale getirme](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
