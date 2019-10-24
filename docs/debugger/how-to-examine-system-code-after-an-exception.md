---
title: Bir özel durumdan sonra sistem kodunu inceleme | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98f3eb98024e20350151904f297f7e7b4d6f1fea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733383"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Nasıl Yapılır: Özel Durumdan Sonra Sistem Kodunu İnceleme
Bir özel durum oluştuğunda, özel durumun nedenini öğrenmek için bir sistem çağrısının içindeki kodu incelemeniz gerekebilir. Aşağıdaki yordamda, sistem kodu için simge yüklü değilse veya Yalnızca kendi kodum etkinse bunun nasıl yapılacağı açıklanmaktadır.

### <a name="to-examine-system-code-following-an-exception"></a>Özel durumu izleyen sistem kodunu incelemek için

1. **Çağrı yığını** penceresinde, sağ tıklayın ve ardından **dış kodu göster**' e tıklayın.

     Yalnızca kendi kodum etkinleştirilmemişse, bu seçenek kısayol menüsünde kullanılamaz ve sistem kodu varsayılan olarak gösterilir.

2. Şimdi **çağrı yığını** penceresinde görüntülenen dış kod çerçevelerine sağ tıklayın.

3. **Sembolleri yükle** ' nin üzerine gelin ve ardından **Microsoft sembol sunucuları**' na tıklayın.

    1. Yalnızca kendi kodum etkinleştirildiyse bir iletişim kutusu görüntülenir. Yalnızca kendi kodum artık devre dışı bırakıldığını belirtir. Bu, sistem çağrılarının adımlaması için gereklidir.

    2. **Ortak sembolleri indirme** iletişim kutusu görüntülenir. İndirme tamamlandığında kaybolacaktır.

4. Artık **çağrı yığını** penceresinde ve diğer pencerelerin sistem kodunu inceleyebilirsiniz. Örneğin, bir kaynak veya **ayrıştırma** penceresinde kodu görüntülemek için bir çağrı yığını çerçevesine çift tıklayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)