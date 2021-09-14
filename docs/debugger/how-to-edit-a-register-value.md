---
title: Yazmam Değerini | Microsoft Docs
description: Yazmaçlar penceresinde değerini düzenleyerek yazmaç içeriğini değiştirmeyi öğrenin (yalnızca adres düzeyinde hata ayıklama etkinleştirildiğinde kullanılabilir).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.register.edit
dev_langs:
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 71532f7b1c1aad8959ce3a10e7b955d55c3e51d9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636686"
---
# <a name="how-to-edit-a-register-value-c"></a>Nasıl: Yazmaç Değerini Düzenleme (C++)

Yazmazlar penceresi yalnızca Seçenekler iletişim kutusundaki Hata ayıklama düğümünde adres düzeyinde **hata** ayıklama **etkinleştirildiyse** kullanılabilir.

### <a name="to-change-the-value-of-a-register"></a>Yazmanın değerini değiştirmek için

1. **Yazmazlar** penceresinde SEKME tuşuna veya fareyle ekleme noktasını değiştirmek istediğiniz değere hareket ettirin. Yazmayı başlatan imlecin üzerine yazmak istediğiniz değerin önünde yer alıyor olması gerekir.

2. Yeni değeri yazın.

    > [!CAUTION]
    > Yazmacın değerlerinin değiştirilmesi (özellikle EIP ve EBP kayıtlarında) program yürütmeyi etkileyebilir.

    > [!CAUTION]
    > Kayan nokta değerlerini düzenlemek, kesirli bileşenlerin ondalıktan ikiliye dönüştürülmesi nedeniyle küçük yanlışlıklara neden olabilir. Doğru olmayan bir düzenleme bile kayan nokta yazmaçlarında en az önemli bitlerin bazılarında değişikliklere neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../debugger/how-to-use-the-registers-window.md)
