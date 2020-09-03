---
title: 'Nasıl yapılır: bir özel durumdan sonra sistem kodunu Inceleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c34b2fdf2b6400ffe88f9e9ff08cbe6e4b41daa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155584"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Nasıl Yapılır: Özel Durumdan Sonra Sistem Kodunu İnceleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir özel durum oluştuğunda, özel durumun nedenini öğrenmek için bir sistem çağrısının içindeki kodu incelemeniz gerekebilir. Aşağıdaki yordamda, sistem kodu için simge yüklü değilse veya Yalnızca kendi kodum etkinse bunun nasıl yapılacağı açıklanmaktadır.  
  
### <a name="to-examine-system-code-following-an-exception"></a>Özel durumu izleyen sistem kodunu incelemek için  
  
1. **Çağrı yığını** penceresinde, sağ tıklayın ve ardından **dış kodu göster**' e tıklayın.  
  
     Yalnızca kendi kodum etkinleştirilmemişse, bu seçenek kısayol menüsünde kullanılamaz ve sistem kodu varsayılan olarak gösterilir.  
  
2. Şimdi **çağrı yığını** penceresinde görüntülenen dış kod çerçevelerine sağ tıklayın.  
  
3. **Sembolleri yükle** ' nin üzerine gelin ve ardından **Microsoft sembol sunucuları**' na tıklayın.  
  
    1. Yalnızca kendi kodum etkinleştirildiyse bir iletişim kutusu görüntülenir. Yalnızca kendi kodum artık devre dışı bırakıldığını belirtir. Bu, sistem çağrılarının adımlaması için gereklidir.  
  
    2. **Ortak sembolleri indirme** iletişim kutusu görüntülenir. İndirme tamamlandığında kaybolacaktır.  
  
4. Artık **çağrı yığını** penceresinde ve diğer pencerelerin sistem kodunu inceleyebilirsiniz. Örneğin, bir kaynak veya **ayrıştırma** penceresinde kodu görüntülemek için bir çağrı yığını çerçevesine çift tıklayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)
