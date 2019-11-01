---
title: Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9531f0495bd0dc0a9f095ff71fdfd84fc8d1380
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189783"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme
  Bir Office projesinin hedef çatısı, .NET Framework önceki bir sürümünden [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümde değiştirilirse, çözümü geliştirme ve son kullanıcı bilgisayarlarında çalıştırmaya devam etmek için bazı ek adımlar gerekebilir. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçirebileceğiniz Office projelerini çalıştırmak Için gereken değişiklikler](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)konusuna bakın.

 Ayrıca, proje artık derlenmeyebilir. Office projelerinin bazı özelliklerinin .NET Framework farklı sürümleri için farklı programlama modelleri vardır. Bir Office projesinin hedef çatısı, .NET Framework önceki bir sürümünden [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya sonraki bir sürümde değiştirildiğinde, projede aşağıdaki kod değişikliklerini yapmanız gerekir:

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Office Projelerindeki Şerit özelleştirmelerini güncelleştirme](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Outlook Projelerindeki Form bölgelerini güncelleştirme](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Projeyi Visual Studio 'nun önceki bir sürümünden yükselttiğinizde bir Office projesinin hedef çatısı değişir. Daha fazla bilgi için bkz. [Office çözümlerini yükseltme ve geçirme](../vsto/upgrading-and-migrating-office-solutions.md).

  Office projelerindeki bazı özelliklerin neden farklı bir programlama modeline sahip olduğuna ilişkin daha fazla bilgi için, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ve [.NET Framework 4 ' ü veya 4,5 .NET Framework ' yı hedefleyen Office projelerinin tasarımındaki değişikliklere](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) bakın. [ Office çalışma zamanına genel bakış için stüdyo araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md)
- [Office çözümlerinde hata giderme sorunları](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Office çözümlerinde hatalar için ek destek](../vsto/additional-support-for-errors-in-office-solutions.md)
