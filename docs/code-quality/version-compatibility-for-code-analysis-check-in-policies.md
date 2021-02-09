---
title: Kod Analizi İade İlkeleri için Sürüm Uyumluluğu
ms.date: 11/04/2016
description: Team System 2008 Team Foundation Server ve Team Foundation Server 2010 ' nin Visual Studio iade ilkelerini farklı şekilde nasıl değerlendirçalıştığını öğrenin.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24a97e9175e75d8018aff269066f13a796e1cf64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867678"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kod Analizi İade İlkeleri için Sürüm Uyumluluğu

Farklı sürümlerini kullanarak kod analizi iade ilkelerini değerlendirmeli ve yazarsa [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , iade ilkelerinin nasıl ve nasıl değerlendirileceği hakkında farkları bilmeniz gerekir [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] .

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Check-In Ilkelerini değerlendirmek için sürüm uyumluluğu

- İçinde kod analizi iade etme ilkeleri değerlendirildiğinde [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , içinde var olan ancak bulunmayan tüm kurallar yok [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sayılır.

- Kod Analizi iade ilkeleri ' de değerlendirildiğinde [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , için özel olan tüm yeni kurallar [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] yok sayılır.

- Kod Analizi iade etme ilkesi, kural derlemelerini belirtiyorsa, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] tanımadığı derlemeler tarafından belirtilen tüm kuralları yoksayar.

- Kod Analizi iade etme ilkesi, tanımadığı kural derlemelerini belirtiyorsa [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] bir ileti görüntülenir.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Check-In Ilkeleri yazma için sürüm uyumluluğu

- Sürümünü kullanarak bir kod analizi iade etme ilkesi oluşturduysanız [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] bunu değiştirmek için sürümünü kullanamazsınız. Ayrıca, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ilke değerlendirilemiyor.

- ' De kullanarak bir kod analizi iade etme ilkesi oluşturduysanız, [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] bunu değiştirmek için ' de kullanabilirsiniz ve ilke tarafından da değerlendirilebilirler [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] . ' De kullanarak ilkeyi değiştirdikten sonra [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , ' [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] de kullanarak ilkeyi düzenleyemezsiniz [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] . [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , eşleşmeyen kesin adlarla sorunları olmadan ilkeleri değerlendirebilir.

- Ve için uygulanan kural ayarlarıyla bir kod analizi iade etme ilkesi oluşturmak için, ilkeyi ' [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] de oluşturmanız [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , gereken tüm değişiklikleri yapmanız ve ilkeyi kaydetmeniz gerekir. Kurallarda yapılan değişiklikler yalnızca içinde mevcutsa [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , ilkeyi ' de değiştirin ve kaydedin [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

   İlkeyi ' de kaydettikten sonra [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , yalnızca içindeki kuralların ayarlarını değiştiremezsiniz [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] .
