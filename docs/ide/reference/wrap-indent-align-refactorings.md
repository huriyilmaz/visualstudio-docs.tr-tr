---
title: Yeniden düzenlemeleri sarmalama, girintileme ve hizalama
description: Yöntem çağrılarının zincirlerini kaydırmayı ve hizalamayı öğrenin.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7c218d914bc234533af674fc5d138a1c102d85c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836274"
---
# <a name="wrap-indent-and-align-refactorings"></a>Yeniden düzenlemeleri sarmalama, girintileme ve hizalama

## <a name="wrap-and-align-call-chains"></a>Çağrı zincirlerini sarmalama ve hizalama

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Yöntem çağrılarının zincirlerini kaydırabilmenizi ve hizalamanızı sağlar.

**Ne zaman:** Tek bir bildirimde birkaç yöntem çağrısının bulunduğu uzun bir zinciriniz var.

**Neden:** Uzun bir listeyi okumak, kullanıcı tercihine göre sarmalandıklarında veya girintilendiklerinde daha kolay olur.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi çağrı zincirlerinden herhangi birine yerleştirin.
2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. Yeniden düzenlemeyi kabul etmek için **çağrı zincirini sarın** veya **Sarla ve hizalamayı** seçin.

   ![Warap çağrı zinciri seçiliyken ve C# kod değişiklikleri gösterilen Visual Studio 'daki hızlı eylemler ve yeniden düzenlemeler menüsünün görüntüsü.](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Parametreleri veya bağımsız değişkenleri sarın, Girintile ve Hizala

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Parametreleri veya bağımsız değişkenleri kaydırabilmenizi, girintilemenizi ve hizalamanızı sağlar.

**Ne zaman:** Birden çok parametresi veya bağımsız değişkeni olan bir yöntem bildirimi veya çağrın olması gerekir.

**Neden:** Bir parametre veya bağımsız değişkenlerin uzun bir listesini okumak, kullanıcı tercihine göre sarmalandıklarında veya girintilendiklerinde daha kolay olur.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi bir parametre listesine yerleştirin.
2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   ![Parametreleri sarın, Girintile ve Hizala](media/wrap-parameters.png)

3. Yeniden düzenlemeyi kabul etmek için **her parametreyi Wrap** ' ı seçin.

## <a name="wrap-binary-expressions"></a>İkili ifadeleri sarmalama

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** İkili ifadeleri kaydırabilmenizi sağlar.

**Ne zaman:** İkili ifadeniz vardır.

**Neden:** Bir ikili ifadenin okunması, kullanıcı tercihine kaydırılmasından daha kolay olur.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi ikili ifadeye koyun.
2. **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. Yeniden düzenlemeyi kabul etmek için **Wrap ifadesi** ' ni seçin.

   ![Visual Studio 'da Warap ifadesi seçili ve C# kod değişiklikleri gösterilen hızlı eylemler ve yeniden düzenlemeler menüsünün görüntüsü.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
