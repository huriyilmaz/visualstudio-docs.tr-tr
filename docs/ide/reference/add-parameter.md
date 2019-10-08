---
title: Yöntem hızlı eylemine parametre ekleme
ms.date: 09/28/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4dbed81809cb3b69814fbf10dde7129b45396eaa
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000200"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Hızlı eylem kullanarak bir yönteme parametre ekleme

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Yazdırılacak** Bir yönteme, kullanıma göre otomatik olarak bir parametre eklemenizi sağlar.

**Oluşturulurken** Yöntemine bir parametre eklemeniz ve bunu otomatik olarak doğru bir şekilde bildirmek istemeniz gerekir.

**Kaydol** Metodu çağırmadan önce yöntemi bildirimine ekleyebilirsiniz, ancak bu özellik bir yöntem çağrısına göre otomatik olarak ekler.

## <a name="how-to-use-it"></a>Kullanımı

1. Yöntem çağrısına fazladan bir bağımsız değişken ekleyin.

   Bir kırmızı dalgalı çizgi, çağırdığınız yöntemin adı altında görünür.

2. Hızlı Eylemler menüsü görünene kadar işaretçinizi kırmızı dalgalı çizgi üzerine getirin. Hızlı Eylemler menüsünde **aşağı oku** seçin ve ardından **parametre Ekle ' yi [Yöntem]** seçin.

   ![Visual Studio 'da yönteme parametre ekleme hızlı eylem](media/add-parameter-to-method.png)

   > [!TIP]
   > Hızlı Eylemler menüsüne imlecinizi yöntem çağrısının satırına yerleştirerek ve ardından **Ctrl**+ tuşlarına basarak da erişebilirsiniz **.** (nokta) veya dosya kenar boşluğunda ampul simgesini seçin.

   Visual Studio, yöntem bildirimine yeni parametreyi ekler.

> [!NOTE]
> Yöntemine başka çağrılar varsa, yeni eklenen parametre için bir bağımsız değişken belirtmedikleri için, bu hızlı eylemi kullandıktan sonra hatalar üretebilirler.

## <a name="see-also"></a>Ayrıca bkz.

- [Oluşturucuya parametre Ekle](generate-constructor.md#addparameter)