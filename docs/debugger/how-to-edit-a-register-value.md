---
title: Kayıt değerini Düzenle | Microsoft Docs
description: Yazmaçların içeriğini kayıt defteri penceresinde (yalnızca adres düzeyi hata ayıklama etkinse kullanılabilir) düzenleyerek nasıl değiştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4187be3bd4d5d2099374acea58d86bd093538ef7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917385"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Nasıl yapılır: yazmaç değerini düzenleme (C#, C++, Visual Basic, F #)

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