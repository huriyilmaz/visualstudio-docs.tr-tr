---
title: Kod Analizi İade İlkeleri için Sürüm Uyumluluğu
ms.date: 11/04/2016
description: Team System 2008 2008 Team Foundation Server ve Team Foundation Server 2010'Visual Studio iade ilkelerini nasıl farklı değerlendiriyor?
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 1cd049a8e2aea94e6dc3b581c5b6ca8ccf3ab4e8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631802"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kod Analizi İade İlkeleri için Sürüm Uyumluluğu

farklı sürümlerini kullanarak kod analizi iade ilkelerini değerlendirmeli ve yazmalısanız, iade ilkelerinin nasıl ve nasıl değerlendirilecekleri [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] arasındaki [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] farkları bilmelisiniz.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Check-In İlkelerini Değerlendirmek için Sürüm Uyumluluğu

- Kod analizi iade ilkeleri içinde değerlendiriliyorsa, içinde mevcut olan [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ancak içinde mevcut olmayan tüm kurallar [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] yoksayılır.

- Kod analizi iade ilkeleri içinde değerlendirilene, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] için özel olan tüm yeni kurallar [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] yoksayılır.

- Kod analizi iade ilkesi kural derlemelerini belirtirse, tanımaz derlemeler tarafından belirtilen [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] tüm kuralları yoksayar.

- Kod analizi iade ilkesi tanımaz kural derlemelerini [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] belirtirse, bir ileti görüntülenir.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Yazma Ve İlkeleri için Check-In Uyumluluğu

- sürümünü kullanarak bir kod analizi iade ilkesi oluşturduysanız, bu [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ilkeyi değiştirmek [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] için sürümünü [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] kullanılamaz. Ayrıca, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ilkeyi değerlendire değildir.

- içinde kullanarak bir kod analizi iade ilkesi oluşturduysanız, ilkeyi değiştirmek için içinde kullanabilirsiniz ve [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ilke tarafından da [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] değerlendirebilirsiniz. içinde kullanarak ilkeyi değiştirdikten [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sonra, artık içinde kullanarak ilkeyi [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] düzenleyemezsiniz. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , eşleşmeyen güçlü adlarla sorun olmadan ilkeleri değerlendiriyor.

- hem hem de için geçerli olan kural ayarlarıyla bir kod analizi iade ilkesi oluşturmak için, içinde ilkeyi oluşturmanız, gerekli tüm değişiklikleri yapın [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ve [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ilkeyi kaydetmeniz gerekir. Kurallarda yapılan değişiklikler yalnızca içinde [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] mevcutsa, ilkeyi değiştirir ve içinde kaydedebilirsiniz. [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]

   İlkeyi 'ye [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] kaydeddikten sonra, artık yalnızca içinde mevcut olan kuralların ayarlarını [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] değiştiremezsiniz.
