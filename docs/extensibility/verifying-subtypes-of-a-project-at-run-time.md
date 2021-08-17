---
title: Çalışma Zamanında Bir Project Alt Türlerini Doğrulama | Microsoft Docs
description: VSPackage'nizin, bağlı olduğu belirli bir özel proje alt türü varlığını doğrulamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b797d8b13ec9f4c8a2d968fa0e363e74b5fa465c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056725"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Çalışma zamanında projenin alt türlerini doğrulama
Özel bir proje alt türüne bağlı bir VSPackage, alt türün mevcut olması durumuna uygun şekilde başarısız olması için bu alt türün bakarak mantık içermesi gerekir. Aşağıdaki yordamda, belirtilen bir alt türün varlığının nasıl doğrulan olduğu gösterir.

### <a name="to-verify-the-presence-of-a-subtype"></a>Bir alt türün varlığını doğrulamak için

1. VSPackage'nıza aşağıdaki kodu ekleyerek proje ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> çözüm nesnelerinden proje hiyerarşisini bir nesne olarak elde edersiniz.

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. Hiyerarşiyi arabirime <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> atlayın.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. proje türü GUID'ler listesini almak için ' i <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> seçin.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Belirtilen alt türün GUID'si için listeyi kontrol edin.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Project alt türleri](../extensibility/internals/project-subtypes.md)
- [Project alt türleri tasarımı](../extensibility/internals/project-subtypes-design.md)
- [Proje alt türleri tarafından genişletilmiş özellikler ve yöntemler](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
