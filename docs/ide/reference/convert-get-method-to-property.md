---
title: Get yöntemini özelliğine veya özelliğinden dönüştürme
description: Bir Get yöntemini (ve isteğe bağlı olarak Set yönteminizi) bir özeleğe dönüştürmek için Hızlı Eylemler ve Yeniden Düzenlemeler menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 151f7c8e8ca99a5de00fc6c0c8d5771585133b503955bba45357dcc338cd45ba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121430037"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Get yöntemini özelliğine dönüştürme / Metodu yeniden düzenlemelerini alma özelliğine dönüştürme

Bu yeniden düzenlemelerde şular geçerlidir:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Get metodunu özelliğe dönüştürme

**Ne:** Get yöntemini bir özeleğe (ve isteğe bağlı olarak Set yönteminize) dönüştürmenize olanak sağlar.

**Ne zaman:** Herhangi bir mantık içeren bir Get yönteminiz var.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi Get yöntemi adınıza yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler ve **Yeniden Düzenleme menüsünü tetiklemek için** Önizleme penceresi açılır penceresinde **Yöntemi** özelliğiyle değiştir'i seçin.
   - **Fare**
      - Koda sağ tıklayın, Hızlı **Eylemler ve Yeniden** Düzenlemeler menüsünü seçin ve Önizleme penceresi açılır penceresinde **Yöntemi** özelliğiyle değiştir'i seçin.

1. (İsteğe bağlı) Bir Set yönteminiz varsa, şu anda Get yöntemini değiştir'i ve özelliğiyle yöntemi ayarla'yi **seçerek Set yönteminizi de dönüştürebilirsiniz.**

1. Kod önizlemesinde yapılan değişiklikten memnunsanız **Enter** tuşuna basın veya menüden düzeltmeye tıklayın; değişiklikler işlendi.

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

## <a name="convert-property-to-get-method"></a>Özelliği Get yöntemine dönüştürme

**Ne:** Bir özelliği Get yöntemine dönüştürmenizi sağlar

**Ne zaman:** Hemen ayarlama ve değer alma adımlarını içeren bir özelliğiniz var

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi Get yöntemi adınıza yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler ve **Yeniden Düzenleme menüsünü tetiklemek için** Önizleme penceresi açılır **penceresinden** Özelliği yöntemlerle değiştir'i seçin.
   - **Fare**
      - Koda sağ tıklayın, Hızlı Eylemler ve **Yeniden** Düzenlemeler menüsünü seçin ve Önizleme penceresi açılır **penceresinden Özelliği** yöntemlerle değiştir'i seçin.

1. Kod önizlemesinde yapılan değişiklikten memnunsanız **Enter** tuşuna basın veya menüden düzeltmeye tıklayın; değişiklikler işlendi.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
