---
title: Kod çözümleme Iade Ilkeleri için sürüm uyumluluğu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609315"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kod Analizi İade İlkeleri için Sürüm Uyumluluğu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Farklı sürümlerini kullanarak kod analizi iade ilkelerini değerlendirmeli ve yazarsa [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , iade ilkelerinin nasıl ve nasıl değerlendirileceği hakkında farkları bilmeniz gerekir [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] .

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Iade Ilkelerini değerlendirmek için sürüm uyumluluğu

- İçinde kod analizi iade etme ilkeleri değerlendirildiğinde [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , içinde var olan ancak bulunmayan tüm kurallar yok [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] sayılır.

- Kod Analizi iade ilkeleri ' de değerlendirildiğinde [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , için özel olan tüm yeni kurallar [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] yok sayılır.

- Kod Analizi iade etme ilkesi, kural derlemelerini belirtiyorsa, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] tanımadığı derlemeler tarafından belirtilen tüm kuralları yoksayar.

- Kod Analizi iade etme ilkesi, tanımadığı kural derlemelerini belirtiyorsa [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] bir ileti görüntülenir.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Iade Ilkelerini yazmak için sürüm uyumluluğu

- Sürümünü kullanarak bir kod analizi iade etme ilkesi oluşturduysanız [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] bunu değiştirmek için sürümünü kullanamazsınız. Ayrıca, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ilke değerlendirilemiyor.

- ' De kullanarak bir kod analizi iade etme ilkesi oluşturduysanız, [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] bunu değiştirmek için ' de kullanabilirsiniz ve ilke tarafından da değerlendirilebilirler [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . ' De kullanarak ilkeyi değiştirdikten sonra [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , ' [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] de kullanarak ilkeyi düzenleyemezsiniz [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] . [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , eşleşmeyen kesin adlarla sorunları olmadan ilkeleri değerlendirebilir.

- Ve için uygulanan kural ayarlarıyla bir kod analizi iade etme ilkesi oluşturmak için, ilkeyi ' [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] de oluşturmanız [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , gereken tüm değişiklikleri yapmanız ve ilkeyi kaydetmeniz gerekir. Kurallarda yapılan değişiklikler yalnızca içinde mevcutsa [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , ilkeyi ' de değiştirin ve kaydedin [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] .

     İlkeyi ' de kaydettikten sonra [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , yalnızca içindeki kuralların ayarlarını değiştiremezsiniz [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] .
