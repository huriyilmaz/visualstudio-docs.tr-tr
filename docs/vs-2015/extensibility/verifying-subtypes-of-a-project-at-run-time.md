---
title: Çalışma zamanında bir projenin alt türlerini doğrulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3940097ac53255b7bdd2c12c9ccc64605016e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62584911"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Çalışma Zamanında Proje Alt Türlerini Doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Özel bir proje alt türüne bağımlı olan VSPackage, alt tür yoksa düzgün bir şekilde başarısız olması için o alt türü aramak için mantık içermelidir. Aşağıdaki yordamda, belirtilen bir alt tür varlığının nasıl doğrulanyapılacağı gösterilmektedir.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Bir alt tür varlığını doğrulamak için  
  
1. VSPackage 'a aşağıdaki kodu ekleyerek proje ve çözüm nesnelerinden proje hiyerarşisini bir nesne olarak alın <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2. Hiyerarşiyi <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> arabirime atayın.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3. Öğesini çağırarak proje türü GUID 'Lerinin listesini alın <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4. Belirtilen alt tür için GUID listesini denetleyin.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje alt türleri](../extensibility/internals/project-subtypes.md)   
 [Proje alt türleri tasarımı](../extensibility/internals/project-subtypes-design.md)   
 [Proje Alt Türleri Tarafından Genişletilen Özellikler ve Metotlar](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
