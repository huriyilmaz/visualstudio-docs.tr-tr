---
title: Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme
description: Office çözümlerini .NET Framework 4 ' e veya sonraki bir sürüme nasıl geçirebileceğinizi öğrenmek için projenizin çalışmaya devam etmesi gerekir.
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
ms.workload:
- office
ms.openlocfilehash: 8c11b2f107414ac5ffb048d7c5e49609ba0b17b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946143"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Office çözümlerini .NET Framework 4 veya sonraki sürümlere geçirme
  Bir Office projesinin hedef çatısı [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .NET Framework önceki bir sürümünden veya daha sonraki bir sürüme değiştirilmişse, çözümü geliştirme ve son kullanıcı bilgisayarlarında çalıştırmaya devam etmek için bazı ek adımlar gerekli olabilir. Daha fazla bilgi için, [.NET Framework 4 ' e veya .NET Framework 4,5 ' a geçirebileceğiniz Office projelerini çalıştırmak Için gereken değişiklikler](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)konusuna bakın.

 Ayrıca, proje artık derlenmeyebilir. Office projelerinin bazı özelliklerinin .NET Framework farklı sürümleri için farklı programlama modelleri vardır. Bir Office projesinin hedef çerçevesi [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .NET Framework önceki bir sürümünden veya daha sonraki bir sürüme değiştirildiğinde, projede aşağıdaki kod değişikliklerini yapmanız gerekir:

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Excel ve Word projelerini güncelleştirme](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Office Projelerindeki Şerit özelleştirmelerini güncelleştirme](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [.NET Framework 4 ' e veya .NET Framework 4,5 ' ye geçirebileceğiniz Outlook Projelerindeki Form bölgelerini güncelleştirme](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Projeyi Visual Studio 'nun önceki bir sürümünden yükselttiğinizde bir Office projesinin hedef çatısı değişir. Daha fazla bilgi için bkz. [Office çözümlerini yükseltme ve geçirme](../vsto/upgrading-and-migrating-office-solutions.md).

  Veya sonraki bir sürümü hedeflediğinizde Office projelerindeki bazı özelliklerden farklı bir programlama modeline sahip olma hakkında daha fazla bilgi için [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , [.NET Framework 4 ' ü hedefleyen Office projelerinin tasarımında yapılan değişikliklere veya](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) [Office çalışma zamanına genel bakış için Visual Studio Araçları](../vsto/visual-studio-tools-for-office-runtime-overview.md)4,5 .NET Framework bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md)
- [Office çözümlerinde hata giderme sorunları](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Office çözümlerinde hatalar için ek destek](../vsto/additional-support-for-errors-in-office-solutions.md)
