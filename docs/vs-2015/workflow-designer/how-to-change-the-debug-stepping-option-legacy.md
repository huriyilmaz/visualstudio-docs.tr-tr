---
title: 'Nasıl yapılır: hata ayıklama adımlamayı değiştirme seçeneği (eski) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663444"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Nasıl Yapılır: Hata Ayıklama Adımlama Seçeneğini Değiştirme (Eski)
Bu konuda [!INCLUDE[wf](../includes/wf-md.md)] , eski ' de bulunan ve eşzamanlı eylemleri olan uygulamalar için hata ayıklama adımlaması seçeneğinin nasıl değiştirileceği açıklanmaktadır [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Ya da ' i hedefliyorsanız, eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 **ParallelActivity** veya **ConditionedActivityGroup**gibi eşzamanlı yürütmeye sahip eski etkinliklerden hata ayıklaması yaparken, kodunuzda ilerlemek için iki seçenekten birini kullanabilirsiniz.

 Eski iş akışı projenizdeki hata ayıklama adımı seçeneğini değiştirmek için aşağıdaki adımları izleyin.

## <a name="procedures"></a>Yordamlar

#### <a name="to-change-the-debug-stepping-option"></a>Hata ayıklama adımlaması seçeneğini değiştirmek için

1. Visual Studio’yu çalıştırın.

2. Mevcut bir eski iş akışı projesini açın veya eşzamanlı etkinlikleri kullanan ve ya da ' i hedefleyen yeni bir proje oluşturun [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

3. Eski içindeki **Iş akışı** menüsünde [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Hata Ayıkla**' nın üzerine gelin ve ardından **atlama seçenekleri**' ne gelin.

4. **Örnek** ya da **dal**seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Eski Iş akışlarında hata](../workflow-designer/debugging-legacy-workflows.md) ayıklama [atlama seçenekleri (eski)](../workflow-designer/debug-stepping-options-legacy.md)