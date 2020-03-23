---
title: Get yöntemini özelliğe dönüştürün; özelliği Get yöntemine dönüştürün
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
ms.openlocfilehash: af507a8b437a20e3d4f4807d582abab6f9a12e27
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094202"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Yöntem refactorings almak için özellik / Dönüştür metod alameti dönüştürme

Bu refactorings için geçerlidir:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Get metodunu özelliğe dönüştürme

**Ne:** Get yöntemini bir özelliğe (ve isteğe bağlı olarak Set yönteminize) dönüştürmenizi sağlar.

**Ne zaman:** Herhangi bir mantık içermeyen bir Get yönteminiz var.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi Get metodu adınıza yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Yeniden Çarpanlara Yönelikler** menüsünü tetiklemek ve Önizleme penceresinden özellik ile değiştir **yöntemini** seçin.
   - **Fare**
      - Kodu sağ tıklatın, **Hızlı Eylemler ve Yeniden Faktörler** menüsünü seçin ve Önizleme penceresi açılır penceresinden özellik ile değiştir **yöntemini** seçin.

1. (İsteğe bağlı) Bir Set yönteminiz varsa, şu anda Get **yöntemini değiştir ve özelliği olan yöntemi ayarla yöntemini**seçerek Set yönteminizi de dönüştürebilirsiniz.

1. Kod önizlemesindeki değişiklikten memnunsanız, menüden **Enter** tuşuna basın veya düzeltmeyi tıklatın ve değişiklikler tamamlanır.

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

**Ne zaman:** Hemen ayar ve değer almaktan daha fazlasını içeren bir özelliğiniz var

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi Get metodu adınıza yerleştirin.

1. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Yeniden Çarpanlara Yönelikmenü'yü** tetiklemek ve Önizleme penceresinden **yöntemlerle özelliği değiştir'i** seçin.
   - **Fare**
      - Kodu sağ tıklatın, **Hızlı Eylemler ve Yeniden Faktörler** menüsünü seçin ve Önizleme penceresi açılır penceresinden **yöntemlerle özelliği değiştir'i** seçin.

1. Kod önizlemesindeki değişiklikten memnunsanız, menüden **Enter** tuşuna basın veya düzeltmeyi tıklatın ve değişiklikler tamamlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
