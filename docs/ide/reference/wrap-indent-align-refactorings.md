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
ms.openlocfilehash: 951bc8fa65991daaad2661744efd6bcbd17bdcd4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056075"
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
2. **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.
3. Yeniden **düzenlemeyi kabul etmek için** Çağrı **zincirini** sarmala veya Çağrı zincirini sarmala ve hizala'ya seçin.

   ![Warap çağrı zinciri seçili ve C# kod değişikliklerinin gösterildiği Visual Studio Eylemler ve Yeniden Düzenleme menüsünün ana sayfası.](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Parametreleri veya bağımsız değişkenleri sarmala, girintile ve hizala

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Parametreleri veya bağımsız değişkenleri sarma, girintileme ve hizalamaya olanak sağlar.

**Ne zaman:** Birden çok parametre veya bağımsız değişken içeren bir yöntem bildiriminiz veya çağrınız var.

**Neden:** Uzun bir parametre veya bağımsız değişken listesini okumak, kullanıcı tercihlerine göre sarmalanmış veya girintili hale geldiğinde daha kolaydır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi bir parametre listesine ekleyin.
2. **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.

   ![Parametreleri Sarmala, Girintile ve Hizala](media/wrap-parameters.png)

3. Yeniden **düzenlemeyi kabul etmek** için Her parametreyi sarmala'ya seçin.

## <a name="wrap-binary-expressions"></a>İkili ifadeleri sarmalama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** İkili ifadeleri sarmalar.

**Ne zaman:** bir ikili ifadeye sahipsiniz.

**Neden:** bir ikili ifadeyi okumak, kullanıcı tercihi için sarmalanmış olduğunda daha kolaydır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi ikili ifadeye yerleştirin.
2. **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.
3. Yeniden **düzenlemeyi kabul** etmek için İfadeyi sarmala'ya seçin.

   ![Warap ifadesi seçili ve C# kod değişikliklerinin gösterildiği Visual Studio Eylemler ve Yeniden Düzenleme menüsünün ana sayfası.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
