---
title: Kod Analizi İade İlkeleri için Sürüm Uyumluluğu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c233d174922c0853d771356e0b68185c51c368ea
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448728"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kod Analizi İade İlkeleri için Sürüm Uyumluluğu

@No__t-0 ' nın farklı sürümlerini kullanarak kod analizi iade ilkelerini değerlendirmeli ve yazarsa, [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] ve [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ' nin iade ilkelerini değerlendirme ile arasındaki farkları bilmeniz gerekir.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Iade Ilkelerini değerlendirmek için sürüm uyumluluğu

- Kod Analizi iade ilkeleri [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ' da değerlendirildiğinde, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ' de bulunan ancak [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ' de bulunmayan tüm kurallar yok sayılır.

- @No__t-0 ' da kod analizi iade ilkeleri değerlendirildiğinde, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ' e özel olan tüm yeni kurallar yok sayılır.

- Kod Analizi İade İlkesi kural derlemelerini belirtiyorsa, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], tanımadığı derlemeler tarafından belirtilen tüm kuralları yoksayar.

- Kod Analizi iade ilkesi [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ' ı tanımayan kural derlemelerini belirtiyorsa, bir ileti görüntülenir.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Iade Ilkelerini yazmak için sürüm uyumluluğu

- @No__t-1 ' in [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sürümünü kullanarak bir kod analizi iade ilkesi oluşturduysanız, bunu değiştirmek için [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ' ün [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] sürümünü kullanamazsınız. Ayrıca, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ilkeyi değerlendiremez.

- @No__t-1 ' de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ' ı kullanarak bir kod analizi iade etme ilkesi oluşturduysanız, bunu değiştirmek için [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ' de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ' yi kullanabilirsiniz ve ilke ayrıca [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] tarafından değerlendirilebilirler. İlkeyi [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ' de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ' ı kullanarak değiştirdikten sonra, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ' te [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ' yi kullanarak ilkeyi artık düzenleyemezsiniz. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], eşleşmeyen kesin adlarla sorunlar olmadan ilkeleri değerlendirebilir.

- @No__t-0 ve [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] için uygulanan kural ayarlarıyla bir kod analizi iade etme ilkesi oluşturmak için, ilkeyi [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ' de oluşturmanız, gerekli tüm değişiklikleri yapmanız ve ilkeyi kaydetmeniz gerekir. Kurallardaki değişiklikler yalnızca [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ' da mevcutsa, ilkeyi [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ' de değiştirin ve kaydedin.

   İlkeyi [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ' a kaydettikten sonra, yalnızca [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ' de var olan kuralların ayarlarını değiştiremezsiniz.
