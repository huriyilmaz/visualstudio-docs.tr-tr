---
title: Yeniden düzenlemeleri sarmalama, girintileme ve hizalama
description: Yöntem çağrılarının zincirlerini kaydırmayı ve hizalamayı öğrenin.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 951bc8fa65991daaad2661744efd6bcbd17bdcd4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628544"
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

   ![warap çağrı zinciri seçili ve C# kod değişiklikleri gösterilen Visual Studio hızlı eylemler ve yeniden düzenlemeler menüsünün bir görüntüsü.](media/wrap-call-chain.png)

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

   ![warap ifadesi seçili ve C# kod değişiklikleri gösterilen Visual Studio hızlı eylemler ve yeniden düzenlemeler menüsünün bir görüntüsü.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
