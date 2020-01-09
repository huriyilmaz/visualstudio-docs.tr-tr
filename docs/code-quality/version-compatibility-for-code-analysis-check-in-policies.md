---
title: Kod Analizi İade İlkeleri için Sürüm Uyumluluğu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4757b3a105ff02a92944d9b45e645e2c63a8b81c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587166"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kod Analizi İade İlkeleri için Sürüm Uyumluluğu

Farklı [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]sürümlerini kullanarak kod analizi iade ilkelerini değerlendirmeli ve yazarsa, [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] ve [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] iade ilkelerini değerlendirme ' daki farklılıkları bilmeniz gerekir.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Iade Ilkelerini değerlendirmek için sürüm uyumluluğu

- Kod Analizi iade etme ilkeleri [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]değerlendirildiğinde, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] var ancak [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] yok sayılır.

- Kod Analizi iade ilkeleri [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]değerlendirildiğinde, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] özel olan tüm yeni kurallar yok sayılır.

- Kod Analizi iade etme ilkesi kural derlemelerini belirtiyorsa, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] tanımadığı derlemeler tarafından belirtilen tüm kuralları yoksayar.

- Kod Analizi iade ilkesi [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] tanımadığı kural derlemelerini belirtiyorsa, bir ileti görüntülenir.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Iade Ilkelerini yazmak için sürüm uyumluluğu

- [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)][!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sürümünü kullanarak bir kod analizi iade etme ilkesi oluşturduysanız, bunu değiştirmek için [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] sürümünü kullanamazsınız. Ayrıca, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ilkeyi değerlendiremez.

- [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)][!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] kullanarak bir kod analizi iade etme ilkesi oluşturduysanız, bunu değiştirmek için [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] kullanabilirsiniz ve ilke aynı zamanda [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]tarafından değerlendirilebilirler. [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)][!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] kullanarak ilkeyi değiştirdikten sonra, ilkeyi [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]' de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] kullanarak düzenleyemezsiniz. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], eşleşmeyen kesin adlarla sorunları olmadan ilkeleri değerlendirebilir.

- Hem [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] hem de [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]için uygulanan kural ayarlarına sahip bir kod analizi iade etme ilkesi oluşturmak için, ilkeyi [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]oluşturmanız, gerekli tüm değişiklikleri yapmanız ve ilkeyi kaydetmeniz gerekir. Kurallarda yapılan değişiklikler yalnızca [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]mevcutsa, ilkeyi [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]olarak değiştirir ve kaydedersiniz.

   İlkeyi [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]kaydettikten sonra, yalnızca [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] var olan kuralların ayarlarını değiştiremezsiniz.
