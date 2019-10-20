---
title: Tanımlayıcılar için deyimin tamamlanması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643852"
---
# <a name="statement-completion-for-identifiers"></a>Tanımlayıcılar İçin İfade Tamamlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript, değişken bildirimleri için açık yazmaya izin vermez. Sonuç olarak, IntelliSense her zaman nesneler için tamamlama listeleri sağlayamaz. Bu durum çeşitli durumlarda gerçekleşebilir. Aşağıdakiler yaygın olarak karşılaşılan birkaç tane.

- Bir parametre bildirilmiştir, ancak aşağıdaki örnekte gösterildiği gibi etkin belgede başka bir yerde çağrılmadı.

  ```javascript
  function illuminate(light) {
           light.  // Accurate statement completion is not available
                   // unless illuminate is called elsewhere with a
                   // parameter that has a value. If it is called only
                   // in a function that is a sibling to
                   // illuminate(light) in the call hierarchy, the
                   // IntelliSense engine also cannot determine the
                   // parameter type.
       }

  // Sibling function. No statement completion for light
  // object in preceding code.
  function lightLamp() {
      var x = illuminate(1);
  }

  // Uncomment the next line to obtain statement completion for
  // light object in preceding code.
  // var x = illuminate(1);
  ```

- Bir nesne, olaya yanıt olarak çağrılan bir işlevdir. Tasarım zamanında, IntelliSense altyapısı bu durumda kullanılan nesnelerin türünü belirleyemez.

   IntelliSense altyapısı, genellikle etkin belgedeki olayın `addEventListener` kullanımı aracılığıyla olayın çağrılması gerektiğini tespit edebilir, daha doğru IntelliSense bilgileri sağlanır.

  IntelliSense bir nesneyi tanımlayamıyorsa, IntelliSense altyapısı tamamlama listesini etkin belgede mevcut olan adlandırılmış varlıklar veya tanımlayıcılarla doldurur. Tamamlanma listesi bu tanımlayıcıları içerdiğinde, bunların yanında bilgi simgeleri görünür. Ayrıca, her tanımlayıcı için bir araç ipucu, ifadenin bilinmediğini gösterir. Aşağıdaki çizimde, nesne ve özellikleri tanımsız olduğundan belirlenemediği `light` türünde bir nesne için ifade tamamlama seçenekleri gösterilmektedir. Ancak, `intensity` özelliği, `illuminate` işlevinde kullanıldığı için tanımlayıcı listesinde kullanılabilir.

  **Belirlenemediğini belirten bir nesne için tamamlama seçenekleri**

  ![Tanımlayıcılar için JavaScript IntelliSense](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")

  XML belge açıklamalarını veya JavaScript IntelliSense genişletilebilirlik özelliklerini kullanarak bir nesnenin tamamlanma listesini geçersiz kılabilirsiniz. Bu özellikleri kullanarak tür bilgilerini ve daha fazla açıklayıcı IntelliSense bilgilerini, aksi halde kullanılabilir olmadığında sağlayabilirsiniz. Daha fazla bilgi için bkz. [JavaScript IntelliSense 'ı genişletme](../ide/extending-javascript-intellisense.md) ve [XML belgesi açıklamaları oluşturma](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
