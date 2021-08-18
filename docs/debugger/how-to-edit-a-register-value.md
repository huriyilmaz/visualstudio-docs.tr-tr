---
title: Kayıt değerini Düzenle | Microsoft Docs
description: Yazmaçların içeriğini kayıt defteri penceresinde (yalnızca adres düzeyi hata ayıklama etkinse kullanılabilir) düzenleyerek nasıl değiştireceğinizi öğrenin.
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
ms.sourcegitcommit: 4cf966e03cdce4c520f6d4bde0b2711c099e0edd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122188692"
---
# <a name="how-to-edit-a-register-value-c"></a>Nasıl yapılır: yazmaç değerini düzenleme (C++)

Yazmaçları penceresi yalnızca, **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümünde adres düzeyi hata ayıklama etkinse kullanılabilir.

### <a name="to-change-the-value-of-a-register"></a>Bir kaydın değerini değiştirmek için

1. **Yazmaçları** penceresinde, ekleme noktasını değiştirmek istediğiniz değere TAŞıMAK için sekme tuşunu veya fareyi kullanın. Yazmaya başladığınızda, imlecin üzerine yazmak istediğiniz değerin önünde bulunması gerekir.

2. Yeni değeri yazın.

    > [!CAUTION]
    > Kayıt değerlerini değiştirme (özellikle EıP ve EBP yazmaçlarında) program yürütmesini etkileyebilir.

    > [!CAUTION]
    > Kayan nokta değerlerini düzenlemek, kesirli bileşenlerin ondalıktan ikiliye dönüştürülmesi nedeniyle küçük yanlışlıklara neden olabilir. Bir anlık zararsız düzenleme bile, kayan nokta kaydındaki en az önemli bitlerin bazılarında değişikliklere yol açabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../debugger/how-to-use-the-registers-window.md)
