---
title: Hata ayıklama atlama seçenekleri (eski) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 443cbac0ea9d74c61f24d6714162ec08e2906a62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656873"
---
# <a name="debug-stepping-options-legacy"></a>Hata Ayıklama Adımlama Seçenekleri (Eski)
Bu konuda [!INCLUDE[wf](../includes/wf-md.md)] , eski sürümünde eşzamanlı etkinlikleri olan uygulamalarda hata ayıklama işlemleri açıklanmaktadır [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Ya da ' i hedefliyorsanız, eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 **ParallelActivity** veya **ConditionedActivityGroup**gibi eşzamanlı yürütmeye sahip eski etkinliklerden hata ayıklaması yaparken, kodunuzda ilerlemek için aşağıdaki iki seçenekten birini kullanabilirsiniz.

- **Dal Adımlama.** Bu Adımlama modu, bir bileşik etkinliğin **Paralellactivity** veya **ConditionalActivityGroup** etkinliği gibi belirli bir dalında ilerlemenize ve hata ayıklamanıza olanak sağlar. Hata ayıklamak için bu seçeneği kullandığınızda, bir denetimdeki değişikliğin iş akışındaki diğer etkinliklerin eşzamanlı yürütmesi nedeniyle oluştuğunu fark edeceksiniz. Hata ayıklayıcı, yalnızca şu anda seçili olan daldaki etkinliklere yönelik adımları izleyerek iş akışındaki diğer etkinlikler eşzamanlı olarak yürütülemeyebilir. Örneğin, varsayılan olarak, bir **ParallelActivity** etkinliğinin en sol dalı ve bir **ConditionedActivityGroup** etkinliğinin ilk alt etkinliği Adımlama için kullanılır. Kullanıcı başka bir dalın veya alt etkinliğin hatalarını ayıklamaya ilgileniyorsa, bu dala veya alt etkinliğe açık bir kesme noktası yerleştirilmesi gerekir. Kesme noktası tetiklendiğinde, bu dalda adım devam eder.

- **Örnek Adımlama.** Bu Adımlama modu, iş akışında eşzamanlı olarak yürütülen etkinlikleri ilerlemenize ve hata ayıklamanıza olanak sağlar. Bu seçenekle, iş akışı içinde eşzamanlı olarak yürütülen etkinlikler çalıştırıldığında denetimdeki bir değişikliğin gerçekleştiğini fark edeceksiniz.

  Varsayılan olarak, dal adımla seçeneği seçilidir ve kullanıcılar eski bir iş akışında hata ayıklarken iki seçenek arasında geçiş yapabilir.

  Eski durum makinesi iş akışlarının hatalarını ayıklarken örnek adımlamayı seçmeniz gerekir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Eski Iş akışlarında hata ayıklama](../workflow-designer/debugging-legacy-workflows.md) [nasıl yapılır: hata ayıklama adımlamayı değiştirme seçeneği (eski)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)