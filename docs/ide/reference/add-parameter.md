---
title: Yöntem hızlı eylemine parametre ekleme
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6720421fd5188688214665d85de682542b1c1357
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595871"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Hızlı eylem kullanarak bir yönteme parametre ekleme

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir yönteme, kullanıma göre otomatik olarak bir parametre eklemenizi sağlar.

**Ne zaman:** Yöntemine bir parametre eklemeniz ve bunu otomatik olarak doğru bir şekilde bildirmek istemeniz gerekir.

**Neden:** Metodu çağırmadan önce yöntemi bildirimine ekleyebilirsiniz, ancak bu özellik bir yöntem çağrısına göre otomatik olarak ekler.

## <a name="how-to-use-it"></a>Kullanımı

1. Yöntem çağrısına fazladan bir bağımsız değişken ekleyin.

   Bir kırmızı dalgalı çizgi, çağırdığınız yöntemin adı altında görünür.

2. Hızlı Eylemler menüsü görünene kadar işaretçinizi kırmızı dalgalı çizgi üzerine getirin. Hızlı Eylemler menüsünde **aşağı oku** seçin ve ardından **parametre Ekle ' yi [Yöntem]** seçin.

   ![Visual Studio 'da yönteme parametre ekleme hızlı eylem](media/add-parameter-to-method.png)

   > [!TIP]
   > Hızlı Eylemler menüsüne imlecinizi yöntem çağrısının satırına yerleştirerek ve ardından **Ctrl**+tuşlarına basarak da erişebilirsiniz **.** (nokta) veya dosya kenar boşluğunda ampul simgesini seçin.

   Visual Studio, yöntem bildirimine yeni parametreyi ekler.

> [!NOTE]
> Yöntemine başka çağrılar varsa, yeni eklenen parametre için bir bağımsız değişken belirtmedikleri için, bu hızlı eylemi kullandıktan sonra hatalar üretebilirler.

## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturucuya parametre Ekle](generate-constructor.md#addparameter)
