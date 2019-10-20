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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609315"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kod Analizi İade İlkeleri için Sürüm Uyumluluğu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Farklı [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] sürümlerini kullanarak kod analizi iade ilkelerini değerlendirmeli ve yazarsa, [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] ve [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] iade ilkelerini değerlendirme ' daki farklılıkları bilmeniz gerekir.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Iade Ilkelerini değerlendirmek için sürüm uyumluluğu

- Kod Analizi iade etme ilkeleri [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] değerlendirildiğinde, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] var ancak [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] yok sayılır.

- Kod Analizi iade ilkeleri [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] değerlendirildiğinde, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] özel olan tüm yeni kurallar yok sayılır.

- Kod Analizi iade etme ilkesi kural derlemelerini belirtiyorsa, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] tanımadığı derlemeler tarafından belirtilen tüm kuralları yoksayar.

- Kod Analizi iade ilkesi [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] tanımadığı kural derlemelerini belirtiyorsa, bir ileti görüntülenir.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Iade Ilkelerini yazmak için sürüm uyumluluğu

- @No__t_1 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] sürümünü kullanarak bir kod analizi iade etme ilkesi oluşturduysanız, bunu değiştirmek için [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] sürümünü kullanamazsınız. Ayrıca, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ilkeyi değerlendiremez.

- @No__t_1 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] kullanarak bir kod analizi iade etme ilkesi oluşturduysanız, bunu değiştirmek için [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] kullanabilirsiniz ve ilke aynı zamanda [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] tarafından değerlendirilebilirler. @No__t_1 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] kullanarak ilkeyi değiştirdikten sonra, ilkeyi [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ' de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] kullanarak düzenleyemezsiniz. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], eşleşmeyen kesin adlarla sorunları olmadan ilkeleri değerlendirebilir.

- Hem [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] hem de [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] için uygulanan kural ayarlarına sahip bir kod analizi iade etme ilkesi oluşturmak için, ilkeyi [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] oluşturmanız, gerekli tüm değişiklikleri yapmanız ve ilkeyi kaydetmeniz gerekir. Kurallarda yapılan değişiklikler yalnızca [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] mevcutsa, ilkeyi [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] olarak değiştirir ve kaydedersiniz.

     İlkeyi [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] kaydettikten sonra, yalnızca [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] var olan kuralların ayarlarını değiştiremezsiniz.
