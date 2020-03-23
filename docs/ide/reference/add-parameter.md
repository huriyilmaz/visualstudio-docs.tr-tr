---
title: Yönteme hızlı eyleme parametre ekleme
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6720421fd5188688214665d85de682542b1c1357
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595871"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Hızlı Eylem kullanarak yönteme parametre ekleme

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir yönteme kullanıma dayalı bir parametreyi otomatik olarak eklemenizi sağlar.

**Ne zaman:** Bir yönteme bir parametre eklemeniz gerekir ve yöntemi otomatik olarak düzgün bir şekilde bildirmek istemeniz gerekir.

**Neden:** Parametreyi aramadan önce yöntem bildirimine ekleyebilirsiniz, ancak bu özellik bir yöntem çağrısına dayalı olarak otomatik olarak ekler.

## <a name="how-to-use-it"></a>Nasıl kullanılır?

1. Yöntem çağrısına ek bir bağımsız değişken ekleyin.

   Kırmızı bir dalgalı olarak adlandırdığınız yöntemin adı altında görünür.

2. Hızlı Hareketler menüsü görünene kadar işaretçinizi kırmızı dalgalının üzerine yerleştirin. Hızlı İşlemler menüsündeki **aşağı ok'u** seçin ve sonra **[yöntem] için parametre ekle'yi**seçin.

   ![Visual Studio'da yöntem hızlı eyleme parametre ekleme](media/add-parameter-to-method.png)

   > [!TIP]
   > Ayrıca imlecinizi yöntem çağrısı satırına yerleştirerek ve **ctrl**+tuşuna basarak Hızlı İşlemler menüsüne de erişebilirsiniz.**.** (dönem) veya dosya kenar boşluğundaki ampul simgesini seçme.

   Visual Studio yöntem bildirimine yeni parametreekler.

> [!NOTE]
> Yönteme başka çağrılarınız varsa, bu Hızlı Eylem'i kullandıktan sonra hatalara neden olabilir, çünkü yeni eklenen parametre için bir bağımsız değişken belirtmezler.

## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturucuya parametre ekleme](generate-constructor.md#addparameter)
