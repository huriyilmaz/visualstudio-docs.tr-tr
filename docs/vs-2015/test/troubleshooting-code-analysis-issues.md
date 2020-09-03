---
title: Kod Analizi sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4eee70b3184496e8dbb7d784501a5cac2aac00ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672112"
---
# <a name="troubleshooting-code-analysis-issues"></a>Kod Analizi Sorunlarını Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, aşağıdaki Visual Studio kod analizi sorunlarıyla ilgili sorun giderme bilgilerini içerir.

- [Visual Studio 2010 kural kümesindeki değişiklikler önceki Visual Studio sürümlerine yansıtılmıyor](#ChildRuleSetChangesInPreviousVersions)

## <a name="changes-in-a-visual-studio-2010-rule-set-are-not-reflected-in-previous-visual-studio-versions"></a><a name="ChildRuleSetChangesInPreviousVersions"></a> Visual Studio 2010 kural kümesindeki değişiklikler önceki Visual Studio sürümlerine yansıtılmıyor

Öğesinde [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] bir alt kural kümesi içeren bir kural kümesi oluşturduğunuzda, Visual Studio 'nun önceki bir sürümünü kullanan bilgisayarlarda kod analizi çalıştırmaları için alt kural kümesine yapılan bir değişiklik uygulanmayabilir. Bu sorunu çözmek için, üst kural kümesini, alt kural kümesini içeren kural kümesi olan bir yeniden yazmayı zorlamanız gerekir.

1. İçinde üst kural kümesini açın [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] .

2. Bir kural ekleme veya kaldırma gibi bir değişiklik yapın ve ardından kural kümesini kaydedin.

3. Kural kümesini yeniden açın, değişikliği tersine çevirin ve sonra kural kümesini yeniden kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Kalitesini Analiz Etme](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)
- [Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Kod Çözümleme Kurallarını Gruplandırmak için Kural Kümeleri Kullanma](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
