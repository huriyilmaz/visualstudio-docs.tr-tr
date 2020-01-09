---
title: Geçici bir değişken değeriyle değiştirin.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8f0199436f5f9b1013a4c49cfb5909e760c73dcc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568873"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Satır içi bir geçici değişken yeniden düzenleme

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** geçici değişken kaldırın ve bunun yerine değeriyle değiştirme olanak tanır.

**Ne zaman:** geçici değişken kullanımı kodu anlamak zorlaştırır.

**Neden:** geçici değişken kaldırılması duruma kodu daha kolay okunabilir.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. Vurgulama veya satır içine alınmayacak kadar geçici değişken metin imleci yerleştirin:

   - C#:

       ![Vurgulanan kodu:C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/inline-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Kod sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.

3. Seçin **satır içi geçici değişken** gelen önizleme penceresi açılır.

   Değişken kaldırılır ve kendi kullanımları değişkenin değeriyle değiştirilir.

   - C#:

      ![Satır içi sonucu-C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Satır içi sonucu - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
