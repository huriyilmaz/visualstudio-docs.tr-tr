---
title: Statik yerel işlev yeniden düzenleme seçenekleri
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c297457c910c484c05c974c581e89c75e0ad44e5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77144831"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Statik yerel fonksiyon refactorings ve Hızlı Eylemler

Bu makalede, statik yerel işlevler ile ilgili iki verimlilik özellikleri özetler. Bunlardan biri, yerel bir işlevi statik kılan bir yeniden düzenleme, diğeri ise değişkenleri statik yerel işleve geçirmek için kod üreten hızlı eylemdir.

## <a name="make-local-function-static"></a>Yerel işlevi statik yap

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** Yerel bir işlevi statik yapar ve işlev in deklarasyonu ve çağrıları için işlev dışında tanımlanan değişkenler geçer.

**Ne zaman:** Yerel işlevinizin statik olmasını ve tüm değişkenlerin işlev kapsamında tanımlanmasını istiyorsunuz.

**Neden:** Statik yerel işlevler okunabilirliği artırır: belirli kodun yalıtılmış olduğunu bilmek, anlamayı, yeniden okumayı ve yeniden kullanmayı kolaylaştırır. Statik yerel işlevler, yalnızca tek bir yöntemde çağrılan statik bir işleçle bir sınıfı kirletmesini önlemek için kapsam sağlar.

### <a name="how-to"></a>Nasıl yapılır

1. Caret'inizi yerel işlev adına yerleştirin.

2. **Ctrl**+tuşuna**basın.** (dönem) Hızlı **Eylemler ve Refactorings** menüsünü tetiklemek için.

   ![Yerel işlevi statik yap](media/make-local-function-static.png)

3. **Yerel işlevi 'statik' yap'ı seçin.**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Statik yerel fonksiyonda değişkeni açıkça geçirin

Bu Hızlı Eylem aşağıdakiler için geçerlidir:

- C#

**Ne:** Bir değişkeni açıkça yerel statik bir işleve geçirir.

**Ne zaman:** Yerel bir işlevin statik olmasını istiyorsunuz, ancak yine de bunun dışında başlaşılan değişkenleri kullanıyorsunuz.

**Neden:** Statik yerel işlevlerin kullanılması, yalnızca programın belirli bir bağlamında bildirilip çağrılabileceğini bildikleri için okuyuculara açıklık sağlar. Değişkenleri bu bağlam Dışında tanımlamak için esneklik sağlar, ancak yine de bunları statik yerel işleve bağımsız değişken olarak geçirebilmeyi sağlar.

### <a name="how-to"></a>Nasıl yapılır

1. Caret'inizi statik yerel fonksiyonda kullanıldığı değişkene yerleştirin.

2. **Ctrl**+tuşuna**basın.** (dönem) Hızlı **Eylemler ve Refactorings** menüsünü tetiklemek için.

   ![Statik yerel fonksiyonda değişkeni açıkça geçirin](media/pass-variable-explicitly-static-local-function.png)

3. **Değişkeni yerel statik işlevde açıkça geçir** seçeneğini belirleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)