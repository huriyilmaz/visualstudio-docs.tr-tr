---
title: Yeniden düzenlemeleri sarmalama, girintileme ve hizalama
description: Yöntem çağrıları zincirlerini nasıl sarıp hizalayarak saracak ve hizalayacaknızı öğrenin.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d801f052cb02e6a5b53189eeae342b9015d30f9b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093884"
---
# <a name="wrap-indent-and-align-refactorings"></a>Yeniden düzenlemeleri sarmalama, girintileme ve hizalama

## <a name="wrap-and-align-call-chains"></a>Çağrı zincirlerini sarmalama ve hizalama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Yöntem çağrıları zincirlerini sarmanızı ve hizalamanızı sağlar.

**Ne zaman:** Bir deyimde çeşitli yöntem çağrılarından oluşan uzun bir zinciriniz vardır.

**Neden:** Uzun bir listeyi okumak, kullanıcı tercihine göre paketlendiğinde veya girintisi olduğunda daha kolaydır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi çağrı zincirlerinden herhangi biri yerine yerleştirin.
2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
3. Yeniden düzenlemeyi kabul etmek için **çağrı zincirini sar** veya **Sar ve hizala'yı** seçin.

   ![Çağrı Zincirlerini Sarma ve Hizala](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Parametreleri veya bağımsız değişkenleri sarın, girintisi ve hizalama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Parametreleri veya bağımsız değişkenleri sarmanızı, girintinlemenizi ve hizalamanızı sağlar.

**Ne zaman:** Birden çok parametre veya bağımsız değişkeni olan bir yöntem bildiriminiz veya çağrınız vardır.

**Neden:** Uzun bir parametre veya bağımsız değişken listesini okumak, kullanıcı tercihine göre paketlendiğinde veya girintisi olduğunda daha kolaydır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi parametre listesine yerleştirin.
2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.

   ![Kaydırma, Girintme ve Hizalama parametreleri](media/wrap-parameters.png)

3. Yeniden düzenlemeyi kabul etmek için **her parametreyi kaydır'ı** seçin.

## <a name="wrap-binary-expressions"></a>İkili ifadeleri sarmalama

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** İkili ifadeleri sarmanızı sağlar.

**Ne zaman:** İkili bir ifaden var.

**Neden:** İkili ifadeyi okumak, kullanıcı tercihine sarıldığında daha kolaydır.

### <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi ikili ifadeye yerleştirin.
2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
3. Yeniden düzenlemeyi kabul etmek için **Sargı ifadesini** seçin.

   ![Çağrı Zincirlerini Sarma ve Hizala](media/wrap-binary-expression.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
