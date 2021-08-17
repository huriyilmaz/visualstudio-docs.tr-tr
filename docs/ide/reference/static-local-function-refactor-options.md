---
title: Statik yerel işlev yeniden düzenleme seçenekleri
description: Yerel bir işlevi statik yapmak ve işlevin dışında tanımlanan değişkenleri işlevin bildirimine ve çağrılarına iletirken Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: aea122e61bec36a5e8c37ce443e4fdf0254bc6d6950cff704721e282b6dabb10
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400149"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Statik yerel işlev yeniden düzenlemeleri ve Hızlı Eylemler

Bu makalede statik yerel işlevlerle ilgili iki üretkenlik özelliği özetlemektedir. Bunlardan biri yerel işlevi statik yapan bir yeniden düzenleme, diğeri ise değişkenleri statik bir yerel işleve geçecek kod oluşturan Hızlı Eylemdir.

## <a name="make-local-function-static"></a>Yerel işlevi statik yap

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

**Ne:** Yerel bir işlevi statik yapar ve işlevin dışında tanımlanan değişkenleri işlevin bildirimine ve çağrılarına iletir.

**Ne zaman:** Yerel işlevinizin statik ve tüm değişkenlerin işlev kapsamında tanımlanmalıdır.

**Neden:** Statik yerel işlevler okunabilirliği artırır: Belirli bir kodun yalıtılmış olduğunu bilmek, daha kolay anlaşılır, yeniden okunabilir ve yeniden kullanılabilir. Statik yerel işlevler, bir sınıfı yalnızca tek bir yöntemde çağrılan statik bir işlevle zehirlemenin önlenmesi için de bir yöntem sağlar.

### <a name="how-to"></a>Nasıl yapılır

1. Yerel işlev adına caret'inizi girin.

2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler ve Yeniden **Düzenleme menüsünü tetiklemek için (dönem).**

   ![Yerel işlevi statik yap](media/make-local-function-static.png)

3. Yerel **işlevi 'statik' hale'yi seçin.**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Değişkeni statik bir yerel işlevde açıkça geçme

Bu Hızlı Eylem aşağıdakiler için geçerlidir:

- C#

**Ne:** Bir değişkeni açıkça yerel bir statik işleve iletir.

**Ne zaman:** Yerel bir işlevin statik olması ancak bunun dışında başlatılan değişkenleri kullanmaya devam etmek istemeniz.

**Neden:** Statik yerel işlevlerin kullanımı okuyuculara açıklama sağlar çünkü bunun yalnızca programın belirli bir bağlamında bildiril ve çağrıl olduğunu bilmektedir. Değişkenleri bu bağlamın dışında tanımlama esnekliği sağlar, ancak yine de bunları statik yerel işleve bağımsız değişken olarak geçebilirsiniz.

### <a name="how-to"></a>Nasıl yapılır

1. Caret'inizi statik yerel işlevde kullanılan değişkenin üzerine yer.

2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler ve Yeniden **Düzenleme menüsünü tetiklemek için (dönem).**

   ![Statik yerel işlevde değişkeni açıkça geçme](media/pass-variable-explicitly-static-local-function.png)

3. **Değişkeni yerel statik işlevde açıkça geçir** seçeneğini belirleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)