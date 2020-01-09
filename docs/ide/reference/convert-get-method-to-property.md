---
title: Get metodunu özelliğe Dönüştür; özelliği Get yöntemine Dönüştür
ms.date: 01/26/2018
ms.topic: reference
ms.devlang: csharp
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 6e3807f3902cbd0d2718f249f15cd268fb81ac51
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570238"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Get metodunu özelliğe dönüştürme / özelliği için Get yöntemini yeniden düzenlemeler dönüştürün

Bu yeniden düzenlemeler geçerlidir:

- C#

## <a name="convert-get-method-to-property"></a>Get metodunu özelliğe dönüştürme

**Ne:** , bir özellik (ve kümesi yönteminizi isteğe bağlı olarak) bir Get yöntemi dönüştürmenize olanak sağlar.

**Ne zaman:** herhangi bir mantık içermeyen bir Get yöntemi vardır.

### <a name="how-to"></a>Nasıl Yapılır Konuları

1. Get yöntemi adınızı imleci yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** seçin ve menü **özelliğiyle yöntemi Değiştir** gelen önizleme penceresi açılır.
   - **Fare**
      - Kod sağ tıklayın, **hızlı Eylemler ve yeniden düzenlemeler** seçin ve menü **özelliğiyle yöntemi Değiştir** gelen önizleme penceresi açılır.

1. (İsteğe bağlı) Set yöntemi varsa, ayrıca kümesi yönteminizi şu anda seçerek dönüştürebilirsiniz **değiştirin Get yöntemini ve özellik kümesi yöntemiyle**.

1. Mutlu kodu Önizleme'de bir değişiklik varsa, basın **Enter** veya düzeltmeyi menüsünü tıklatın ve değişiklikler uygulanır.

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

## <a name="convert-property-to-get-method"></a>Özellik Get yönteme Dönüştür

**Ne:** bir özellik için bir Get yöntemi dönüştürmenize olanak tanır.

**Ne zaman:** birden fazla hemen ayarlama ve bir değer alma içeren bir özelliğe sahiptir

### <a name="how-to"></a>Nasıl Yapılır Konuları

1. Get yöntemi adınızı imleci yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menü ve select **yöntemleriyle özelliğini değiştirin** gelen önizleme penceresi açılır.
   - **Fare**
      - Kod sağ tıklayın, **hızlı Eylemler ve yeniden düzenlemeler** menü ve select **yöntemleriyle özelliğini değiştirin** gelen önizleme penceresi açılır.

1. Mutlu kodu Önizleme'de bir değişiklik varsa, basın **Enter** veya düzeltmeyi menüsünü tıklatın ve değişiklikler uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
