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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663444"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Nasıl yapılır: hata ayıklama adımlamayı değiştirme seçeneği (eski)
Bu konuda, eşzamanlı eylemleri olan eski [!INCLUDE[wfd1](../includes/wfd1-md.md)] [!INCLUDE[wf](../includes/wf-md.md)] uygulamalar için hata ayıklama adım seçeneğinin nasıl değiştirileceği açıklanmaktadır. @No__t_1 veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedeflemek gerektiğinde eski [!INCLUDE[wfd2](../includes/wfd2-md.md)] kullanın.

 **ParallelActivity** veya **ConditionedActivityGroup**gibi eşzamanlı yürütmeye sahip eski etkinliklerden hata ayıklaması yaparken, kodunuzda ilerlemek için iki seçenekten birini kullanabilirsiniz.

 Eski iş akışı projenizdeki hata ayıklama adımı seçeneğini değiştirmek için aşağıdaki adımları izleyin.

## <a name="procedures"></a>Yordamlar

#### <a name="to-change-the-debug-stepping-option"></a>Hata ayıklama adımlaması seçeneğini değiştirmek için

1. Visual Studio 'Yu başlatın.

2. Mevcut bir eski iş akışı projesini açın veya eşzamanlı etkinlikleri kullanan ve [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ya da [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedefleyen yeni bir proje oluşturun.

3. Eski [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Iş akışı** menüsünde, **Hata Ayıkla**' nın üzerine gelin ve ardından **atlama seçenekleri**' ne gelin.

4. **Örnek** ya da **dal**seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Eski Iş akışlarında hata](../workflow-designer/debugging-legacy-workflows.md) ayıklama [atlama seçenekleri (eski)](../workflow-designer/debug-stepping-options-legacy.md)