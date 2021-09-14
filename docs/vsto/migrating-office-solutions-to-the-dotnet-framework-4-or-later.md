---
title: Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme
description: Office çözümlerini .NET Framework 4 veya sonraki bir sürüme nasıl geçirebileceğinizi öğrenmek için projenizin çalışmaya devam etmesi gerekir.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 36ad3fa7fb59dcef142030d16dda5f637427a378
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726113"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme
  bir Office projesinin hedef çatısı [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .NET Framework önceki bir sürümünden veya daha sonraki bir sürüme değiştirilmişse, çözümü geliştirme ve son kullanıcı bilgisayarlarında çalıştırmaya devam etmek için bazı ek adımlar gerekli olabilir. daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Office projeler çalıştırmak için gerekli değişiklikler](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)konusuna bakın.

 Ayrıca, proje artık derlenmeyebilir. Office projelerinin bazı özelliklerinin .NET Framework farklı sürümleri için farklı programlama modelleri vardır. bir Office projesinin hedef çerçevesi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .NET Framework önceki bir sürümünden veya daha sonraki bir sürümüne değiştirildiğinde, projede aşağıdaki kod değişikliklerini yapmanız gerekir:

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Office projelerinde şerit özelleştirmelerini güncelleştirme](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Outlook projelerindeki form bölgelerini güncelleştirme](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  bir Office projesinin hedef çatısı, bu projeyi Visual Studio önceki bir sürümünden yükselttiğinizde değişir. daha fazla bilgi için bkz. [Office çözümleri yükseltme ve geçirme](../vsto/upgrading-and-migrating-office-solutions.md).

  veya sonraki bir sürümü hedeflediğinizde Office projelerindeki bazı özelliklerden farklı bir programlama modeline sahip olma hakkında daha fazla bilgi için [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , .NET Framework 4 ' ü veya .NET Framework 4,5 ' i veya [Office için Visual Studio Araçları çalışma zamanına genel bakış](../vsto/visual-studio-tools-for-office-runtime-overview.md)' ı [hedefleyen Office projelerin tasarımındaki değişiklikler](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md)
- [Office çözümlerinde hata giderme](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Office çözümlerinde hatalar için ek destek](../vsto/additional-support-for-errors-in-office-solutions.md)
