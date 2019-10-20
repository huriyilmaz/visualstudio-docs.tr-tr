---
title: Kod Analizi sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6fd2735b7e601afb5a80dd027a8ae107cab58e4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672430"
---
# <a name="troubleshooting-code-analysis-issues"></a>Kod Analizi Sorunlarını Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, aşağıdaki Visual Studio kod analizi sorunlarıyla ilgili sorun giderme bilgilerini içerir.

- [Visual Studio 2010 kural kümesindeki değişiklikler önceki Visual Studio sürümlerine yansıtılmıyor](#ChildRuleSetChangesInPreviousVersions)

## <a name="ChildRuleSetChangesInPreviousVersions"></a>Visual Studio 2010 kural kümesindeki değişiklikler önceki Visual Studio sürümlerine yansıtılmıyor
 Bir alt kural kümesi içeren [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] bir kural kümesi oluşturduğunuzda, alt kural kümesindeki bir değişiklik, Visual Studio 'nun önceki bir sürümünü kullanan bilgisayarlarda kod analizi çalıştırmaları halinde uygulanmayabilir. Bu sorunu çözmek için, üst kural kümesini, alt kural kümesini içeren kural kümesi olan bir yeniden yazmayı zorlamanız gerekir.

1. @No__t_0 üst kural kümesini açın.

2. Bir kural ekleme veya kaldırma gibi bir değişiklik yapın ve ardından kural kümesini kaydedin.

3. Kural kümesini yeniden açın, değişikliği tersine çevirin ve sonra kural kümesini yeniden kaydedin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Uygulama kalitesini çözümleme](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md) [kod analizi kurallarını gruplandırmak için kural kümelerini kullanarak](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) [yönetilen kod kalitesini analiz](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) etme
