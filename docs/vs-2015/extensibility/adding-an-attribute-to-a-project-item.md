---
title: Proje öğesine öznitelik ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1740ac4dfdeb64d5b4b2b0aab264845de9c186dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184825"
---
# <a name="adding-an-attribute-to-a-project-item"></a>Proje Öğesine Öznitelik Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yöntemler <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> bir proje öğesinin özniteliklerinin değerini alır ve ayarlar. SetItemAttribute, zaten mevcut değilse özniteliği oluşturur ve proje öğesi meta verilerine ekler.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Proje öğesine öznitelik ekleme  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>Bir proje öğesine öznitelik eklemek için  
  
- Aşağıdaki kod, <xref:EnvDTE.DTE> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> bir proje öğesine öznitelik eklemek için Automation nesnesini ve yöntemini kullanır. Proje öğesi KIMLIĞI, "program.cs" proje öğesi adından elde edilir. "MyAttribute" özniteliği bu proje öğesine eklenir ve "MyValue" değeri verilir.  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
