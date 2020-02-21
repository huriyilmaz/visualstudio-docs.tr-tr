---
title: Wrap, Girintile ve yeniden düzenlemeler Hizala
description: Yöntem çağrılarının zincirlerini kaydırmayı ve hizalamayı öğrenin.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 349f2eeccfea4fea03967929b01114c0de1af155
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527670"
---
# <a name="wrap-indent-and-align-refactorings"></a>Wrap, Girintile ve yeniden düzenlemeler Hizala

## <a name="wrap-and-align-call-chains"></a>Çağrı zincirlerini sarmalama ve hizalama

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** Yöntem çağrılarının zincirlerini kaydırabilmenizi ve hizalamanızı sağlar.

**Ne zaman:** Tek bir bildirimde birkaç yöntem çağrısının bulunduğu uzun bir zinciriniz var.

**Neden:** Uzun bir listeyi okumak, kullanıcı tercihine göre sarmalandıklarında veya girintilendiklerinde daha kolay olur.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi çağrı zincirlerinden herhangi birine yerleştirin.
2. **Ctrl**+tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. Yeniden düzenlemeyi kabul etmek için **çağrı zincirini sarın** veya **Sarla ve hizalamayı** seçin.

   ![Çağrı zincirlerini kaydırın ve hizalayın](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Parametreleri veya bağımsız değişkenleri sarın, Girintile ve Hizala

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Parametreleri veya bağımsız değişkenleri kaydırabilmenizi, girintilemenizi ve hizalamanızı sağlar.

**Ne zaman:** Birden çok parametresi veya bağımsız değişkeni olan bir yöntem bildirimi veya çağrın olması gerekir.

**Neden:** Bir parametre veya bağımsız değişkenlerin uzun bir listesini okumak, kullanıcı tercihine göre sarmalandıklarında veya girintilendiklerinde daha kolay olur.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi bir parametre listesine yerleştirin.
2. **Ctrl**+tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   ![Parametreleri sarın, Girintile ve Hizala](media/wrap-parameters.png)

3. Yeniden düzenlemeyi kabul etmek için **her parametreyi Wrap** ' ı seçin.

## <a name="wrap-binary-expressions"></a>İkili ifadeleri sarmalama

Bu yeniden düzenleme için geçerlidir:

- C#

**Ne:** İkili ifadeleri kaydırabilmenizi sağlar.

**Ne zaman:** İkili ifadeniz vardır.

**Neden:** Bir ikili ifadenin okunması, kullanıcı tercihine kaydırılmasından daha kolay olur.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi ikili ifadeye koyun.
2. **Ctrl**+tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. Yeniden düzenlemeyi kabul etmek için **Wrap ifadesi** ' ni seçin.

   ![Çağrı zincirlerini kaydırın ve hizalayın](media/wrap-binary-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenleme](../refactoring-in-visual-studio.md)
