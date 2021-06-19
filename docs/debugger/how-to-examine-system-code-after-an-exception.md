---
title: Özel durum sonrasında sistem kodunu | Microsoft Docs
description: Özel durumun nedenini bulmak için sistem çağrısındaki kodu incelemeyi öğrenin. Sistem kodu için semboller yüklenmemiş olsa bile yordam uygulanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f05ae1486089eaa63ef47a9953578db2a0b6662a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384661"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Nasıl Yapılır: Özel Durumdan Sonra Sistem Kodunu İnceleme
Bir özel durum oluştuğunda, özel durumun nedenini belirlemek için sistem çağrısının içindeki kodu incelemeniz gerekir. Aşağıdaki yordamda, sistem kodu için yüklenmiş sembolleriniz yoksa veya sistem kodunuz etkinse bunun Yalnızca kendi kodum açıktır.

### <a name="to-examine-system-code-following-an-exception"></a>Bir özel durumu takip eden sistem kodunu incelemek için

1. Çağrı Yığını **penceresinde sağ** tıklayın ve ardından Dış Kodu **Göster'e tıklayın.**

     Bu Yalnızca kendi kodum etkinleştirilmediyse, bu seçenek kısayol menüsünde kullanılamaz ve sistem kodu varsayılan olarak gösterilir.

2. Artık Çağrı Yığını penceresinde görünen dış kod **çerçevelerini sağ** tıklayın.

3. Simgesinden **Sembolleri Yükle'nin üzerine gelin** ve ardından Microsoft Sembol **Sunucuları'nın üzerine tıklayın.**

    1. Etkin Yalnızca kendi kodum bir iletişim kutusu görüntülenir. Bu, Yalnızca kendi kodum devre dışı bırakılmıştır. Bu, sistem çağrılarına adımlama için gereklidir.

    2. Genel **sembolleri indir iletişim** kutusu görüntülenir. İndirme işlemi tamam olduğunda kaybolur.

4. Artık Çağrı Yığını penceresinde ve diğer **pencerelerde sistem** kodunu inceebilirsiniz. Örneğin, bir kaynak veya **Disassembly** penceresinde kodu görüntülemek için bir çağrı yığını çerçevesine çift tıklarsınız.

## <a name="see-also"></a>Ayrıca bkz.
- [Özel Durumları Hata Ayıklayıcısı ile Yönetme](../debugger/managing-exceptions-with-the-debugger.md)