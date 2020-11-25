---
title: Get metodunu özelliğe veya bir özelliğe dönüştürme
description: GET yöntemini (ve isteğe bağlı olarak set yönteminizi) bir özelliğe dönüştürmek için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3aa7831c56068c826c9bbecf97d7115331243251
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039829"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Get metodunu Property/Convert metodunu Get yöntemine Dönüştür yeniden düzenlemeler

Bu yeniden düzenlemeler için geçerlidir:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Get metodunu özelliğe dönüştürme

**Ne:** GET yöntemini bir özelliğe (ve isteğe bağlı olarak ayarlama yöntemine) dönüştürmenize olanak sağlar.

**Ne zaman:** Herhangi bir mantık içermeyen bir get yönteminiz vardır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi get yöntemi adına yerleştirin.

1. Sonra, aşağıdakilerden birini yapın:

   - **Klavye**
      - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için Önizleme penceresi açılır penceresinde **yöntemi özelliği ile Değiştir** ' i seçin.
   - **Fare**
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve Önizleme penceresi açılır penceresinde **yöntemi özelliği ile Değiştir** ' i seçin.

1. Seçim Bir set yönteminiz varsa, **Get metodunu değiştir ve yöntemi ayarla özelliğini** seçerek de set yönteminizi Şu anda dönüştürebilirsiniz.

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

   - **Klavye**
      - **CTRL** tuşuna basın + **.** **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü tetiklemek ve özelliği önizleme penceresi açılan penceresinde **yöntemlerle Değiştir** ' i seçmek için.
   - **Fare**
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve özelliği önizleme penceresi açılan penceresinde **yöntemlerle Değiştir** ' i seçin.

1. Kod önizlemesindeki değişikliğin kutlu olsun, **ENTER** tuşuna basın veya menüdeki değişikliğe tıklayın ve değişiklikler uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
