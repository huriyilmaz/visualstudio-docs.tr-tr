---
title: Get metodunu özelliğe Dönüştür; özelliği Get yöntemine Dönüştür
ms.date: 01/26/2018
ms.topic: reference
ms.devlang: csharp
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ac33db013a8cea11b373e4104bf2d58a1b22cef4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654518"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Get metodunu Property/Convert metodunu Get yöntemine Dönüştür yeniden düzenlemeler

Bu yeniden düzenlemeler için geçerlidir:

- C#

## <a name="convert-get-method-to-property"></a>Get metodunu özelliğe Dönüştür

**Ne:** GET yöntemini bir özelliğe (ve isteğe bağlı olarak ayarlama yöntemine) dönüştürmenize olanak sağlar.

**Ne zaman:** Herhangi bir mantık içermeyen bir get yönteminiz vardır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi get yöntemi adına yerleştirin.

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için Önizleme penceresi açılır penceresinde **yöntemi özelliği ile Değiştir** ' i seçin.
   - **Tığında**
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve Önizleme penceresi açılır penceresinde **yöntemi özelliği ile Değiştir** ' i seçin.

1. Seçim Bir set yönteminiz varsa, **Get metodunu değiştir ve yöntemi ayarla özelliğini**seçerek de set yönteminizi Şu anda dönüştürebilirsiniz.

1. Kod önizlemesindeki değişikliğin kutlu olsun, **ENTER** tuşuna basın veya menüdeki değişikliğe tıklayın ve değişiklikler uygulanır.

Örnek:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Özelliği Get yöntemine Dönüştür

**Ne:** Bir özelliği Get yöntemine dönüştürmenize olanak sağlar

**Ne zaman:** Hemen daha fazla ayarı ve değer almayı içeren bir özelliğe sahipsiniz

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi get yöntemi adına yerleştirin.

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü tetiklemek ve özelliği önizleme penceresi açılan penceresinde **yöntemlerle Değiştir** ' i seçmek için.
   - **Tığında**
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve özelliği önizleme penceresi açılan penceresinde **yöntemlerle Değiştir** ' i seçin.

1. Kod önizlemesindeki değişikliğin kutlu olsun, **ENTER** tuşuna basın veya menüdeki değişikliğe tıklayın ve değişiklikler uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)