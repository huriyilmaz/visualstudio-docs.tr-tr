---
title: Kullanılmayan değerler ve parametreler
description: Kullanılmayan değer atamaları, değişkenler ve parametreler hakkında bilgi edinin ve bunların Visual Studio kod düzenleyicisinde nasıl göründüğünü öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a3fcdd7703e6b367ba8649918ff346646982c4c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116948"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Kullanılmayan değer atamaları, değişkenler ve parametreler

Bu yeniden düzenleme için geçerlidir:

- C#
- Visual Basic

**Ne:** Kullanılmayan parametreleri soluklaştırır ve kullanılmayan ifade değerleri için bir uyarı oluşturur. Derleyici Ayrıca kullanılmayan değer atamalarını bulmak için bir Akış Analizi gerçekleştirir. Kullanılmayan değer atamaları soluklaşır ve yedekli atamayı kaldırmak için hızlı bir [eylem](../quick-actions.md) içeren bir ampul belirir. Bilinmeyen değerleri olan kullanılmayan değişkenler, yerine [atma](/dotnet/csharp/discards) işlemini kullanmak için [hızlı bir eylem](../quick-actions.md) önerisi gösterir. (Atma, uygulama kodunda kasıtlı olarak kullanılmayan geçici ve kukla değişkenlerdir. Bellek ayırmayı azaltabilir ve kodunuzu daha kolay okunabilir hale getirebilirsiniz.)

**Ne zaman:** Hiç kullanılmamış değer atamaları, parametreleri veya ifade değerleri vardır.

**Neden:** Bazen bir değer atama, değişken veya parametrenin artık kullanılmadığını söylemek zordur. Bu değerleri kaldırarak veya bir uyarı oluşturarak, hangi kodun silineceğini öğrenmek için görsel bir ipucu alırsınız.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Kullanılmayan ifade değerleri ve parametreleri tanılaması

1. Kullanılmayan herhangi bir değer atama, değişken veya parametre içermelidir.
2. Kullanılmayan değer atama veya parametresi, kullanıma hazır olarak görünür. Kullanılmayan ifade değeri bir uyarı oluşturur.

  ![Kullanılmayan parametre kullanılmamış değer ](media/unused-parameter.png)
   ![ ](media/unused-value.png)
   ![ atama kullanılmamış değer ](media/unused-value-assignment.png)
   ![ atma kullanılmıyor](media/unused-value-discard.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.net geliştiricileri için İpuçları](../csharp-developer-productivity.md)
