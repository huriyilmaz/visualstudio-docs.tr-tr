---
title: Kullanılmayan değerler ve parametreler
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce2b0f1e0c0db45c478c3917306683b314da0564
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531872"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Kullanılmayan değer atamaları, değişkenler ve parametreler

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#
- Visual Basic

**Ne:** Kullanılmayan parametreleri solur ve kullanılmayan ifade değerleri için bir uyarı oluşturur. Derleyici, kullanılmayan değer atamalarını bulmak için bir akış çözümlemesi de gerçekleştirir. Kullanılmayan değer atamaları solmaya ve bir ampul gereksiz atama kaldırmak için [hızlı eylem](../quick-actions.md) ile görünür. Bilinmeyen değerlere sahip kullanılmayan değişkenler, bunun yerine [atları](/dotnet/csharp/discards) kullanmak için [hızlı eylem](../quick-actions.md) önerisi gösterir. (Atar, uygulama kodunda kasıtlı olarak kullanılmayan geçici, sahte değişkenlerdir. Bellek ayırmayı azaltabilir ve kodunuzu okumayı kolaylaştırabilir.)

**Ne zaman:** Hiç kullanılmayan değer atamalarınız, parametrelerinuz veya ifade değerleriniz vardır.

**Neden:** Bazen bir değer ataması, değişken veya parametre artık kullanılıp kullanılmamadığını anlamak zor olabilir. Bu değerleri salarak veya bir uyarı oluşturarak, hangi kodu silebileceğinize işaret edebilirsiniz.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Kullanılmayan ifade değerleri ve parametreleri tanılama

1. Kullanılmayan herhangi bir değer ataması, değişken veya parametreye sahip.
2. Kullanılmayan değer ataması veya parametresi soluk görünüyor. Kullanılmayan ifade değeri bir uyarı oluşturur.

  ![Kullanılmayan parametre](media/unused-parameter.png)
  ![Kullanılmayan](media/unused-value.png)
  ![değer atama](media/unused-value-assignment.png)
  ![Kullanılmayan değer atma](media/unused-value-discard.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET Geliştiricileri için ipuçları](../csharp-developer-productivity.md)
