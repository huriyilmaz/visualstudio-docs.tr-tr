---
title: Çalışma Zamanında Bir Projenin Alt Türlerini Doğrulama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698177"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Projenin alt türlerini çalışma zamanında doğrulama
Özel bir proje alt türüne bağlı bir VSPackage, alt tip yoksa düzgün bir şekilde başarısız olması için bu alt türü aramak için mantık içermelidir. Aşağıdaki yordam, belirtilen bir alt türün varlığını nasıl doğrulayişsüreceğini gösterir.

### <a name="to-verify-the-presence-of-a-subtype"></a>Bir alt türün varlığını doğrulamak için

1. VSPackage'ınıza aşağıdaki kodu ekleyerek proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ve çözüm nesnelerinden nesne olarak proje hiyerarşisini alın.

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

2. Hiyerarşiyi <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> arabirime atın.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. 'yi çağırarak proje türü GUID'lerin <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>listesini alın.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Belirtilen alt türün GUID için listesini kontrol edin.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Proje alt türleri](../extensibility/internals/project-subtypes.md)
- [Proje alt türleri tasarımı](../extensibility/internals/project-subtypes-design.md)
- [Proje alt türlerine göre genişletilmiş özellikler ve yöntemler](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
