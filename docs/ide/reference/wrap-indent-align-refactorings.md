---
title: Yeniden düzenlemeleri sarmalama, girintileme ve hizalama
description: Yöntem çağrılarının zincirlerini sarma ve hizalamayı öğrenin.
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
ms.openlocfilehash: 54e0fccbc4ff1994b6c7c1e3469232eaf7a64ece75e575d203a8d6e845afccc7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371801"
---
# <a name="wrap-indent-and-align-refactorings"></a>Yeniden düzenlemeleri sarmalama, girintileme ve hizalama

## <a name="wrap-and-align-call-chains"></a>Çağrı zincirlerini sarmalama ve hizalama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Yöntem çağrılarının zincirlerini sarmalar ve hizalar.

**Ne zaman:** Bir deyiminde birkaç yöntem çağrısından oluşan uzun bir zinciriniz var.

**Neden:** Uzun bir listeyi okumak, kullanıcı tercihlerine göre sarmalanmış veya girintili hale geldiğinde daha kolaydır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi çağrı zincirlerinden herhangi birine yerleştirin.
2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
3. Yeniden **düzenlemeyi kabul etmek için** Çağrı **zincirini** sarmala veya Çağrı zincirini sarmala ve hizala'ya seçin.

   ![Warap çağrı zinciri seçiliyken ve C# kod değişikliklerinin gösterildiği Visual Studio Eylemler ve Yeniden Düzenleme menüsünün ana sayfası.](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Parametreleri veya bağımsız değişkenleri sarmala, girintile ve hizala

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Parametreleri veya bağımsız değişkenleri sarmalar, girintiler ve hizalar.

**Ne zaman:** Birden çok parametre veya bağımsız değişken içeren bir yöntem bildiriminiz veya çağrınız var.

**Neden:** Uzun bir parametre veya bağımsız değişken listesini okumak, kullanıcı tercihlerine göre sarmalanmış veya girintili hale geldiğinde daha kolaydır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi bir parametre listesine ekleyin.
2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.

   ![Parametreleri Sarmala, Girintile ve Hizala](media/wrap-parameters.png)

3. Yeniden **düzenlemeyi kabul etmek** için Her parametreyi sarmala'ya seçin.

## <a name="wrap-binary-expressions"></a>İkili ifadeleri sarmalama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** İkili ifadeleri sarmamanizi sağlar.

**Ne zaman:** bir ikili ifadeye sahipsiniz.

**Neden:** Bir ikili ifadeyi okumak, kullanıcı tercihi için sarmalanmış olduğunda daha kolaydır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi ikili ifadeye yerleştirin.
2. **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.
3. Yeniden **düzenlemeyi kabul** etmek için İfadeyi sarmala'ya seçin.

   ![Warap ifadesi seçili ve C# kod değişikliklerinin gösterildiği Visual Studio Eylemler ve Yeniden Düzenleme menüsünün ana sayfası.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
