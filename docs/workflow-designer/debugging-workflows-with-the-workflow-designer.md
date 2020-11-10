---
title: İş Akışı Tasarımcısı ile İş Akışlarında Hata Ayıklama
description: İş Akışı Tasarımcısı, varsayılan Visual Studio hata ayıklayıcıyla benzer bir işlemle iş akışlarında ve özel etkinliklerde hata ayıklama olanağı sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45219da52cdd1ff87b7243c3cc742bb4c97a74e7
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435866"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>İş Akışı Tasarımcısı iş akışlarında hata ayıkla

**İş akışı Tasarımcısı** , iş akışlarının ve özel etkinliklerin hatalarını ayıklama özelliğini sağlar. İşlem ve davranış, varsayılan Visual Studio hata ayıklayıcıyla benzerdir.

## <a name="invoke-the-workflow-debugger"></a>İş akışı hata ayıklayıcıyı çağır

Genellikle, diğer Visual Studio programlama dillerinde yazılmış programlarda hata ayıkladığınızda olduğu gibi iş akışlarında hata ayıklaması yapabilirsiniz. İş akışı hata ayıklayıcısını aşağıdaki yollarla başlatabilirsiniz:

- İş akışı örneğiniz için çalışan konak işlemini seçmek üzere **hata ayıklama** menüsünde **İşleme İliştir** ' i seçin. Bu yordam, Yönetilen koddaki bir ana bilgisayar işlemine iliştirme ile aynıdır.

- İş akışının bir örneğini çalıştırmaya başlamak veya bir kesme noktası isabet ettikten sonra çalışmaya devam etmek için **F5** tuşuna basın.

- Uzaktan hata ayıklamayı kullan. Uzaktan hata ayıklamayı kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzaktan hata ayıklamayı etkinleştirme](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > İş akışı uygulaması x86 mimarisini hedefliyorsa ve 64 bitlik bir işletim sistemi çalıştıran bir makinede barındırılıyorsa, uzak makineye Visual Studio yüklü değilse veya iş akışı uygulamasının hedefi **herhangi BIR CPU** olarak değiştirilmediği takdirde uzaktan hata ayıklama çalışmaz.

## <a name="step-through-code"></a>Kod üzerinden adımla

- **Adımla** : **F11** tuşuna basarak bir etkinliğe adımla. Hata ayıklayıcı, tanımlı herhangi bir işleyicide adımları. Hiçbir işleyici tanımlanmamışsa, etkinliğin üzerinde veya diğer etkinlikleri içeren bileşik etkinliklerle ilk yürütme etkinliğinin içine adımlayın.

- **Dışarı adımla:** **SHIFT** F11 tuşuna basarak bir etkinliğin dışına geçin + **F11**. Bir etkinliğin dışına geçmek, geçerli etkinliği ve tüm eşdüzey etkinliklerini tamamlamaya kadar çalıştırır. Hata ayıklayıcı daha sonra geçerli etkinliğin üst öğesiyle kesilir. Kod işleyiciden atlama yaparken, hata ayıklayıcı işleyicinin ilişkilendirildiği etkinliği keser.

- **Adımlama** : bir etkinliğin üzerinde, **F10** tuşuna basarak adımla. Bileşik bir etkinliğin üzerine adımlarken, hata ayıklayıcı bileşik etkinliğin ilk yürütülebilir alt öğesi üzerinde kesilir. Bir etkinlik gibi bileşik olmayan bir üzerinde Adımlama yaparken <xref:System.Activities.Statements.Assign> , hata ayıklayıcı aktiviteyi ve ilgili işleyicileri yürütür ve sonraki etkinlikte kesilir. Yürütülen etkinlik bileşik bir etkinlikte son alt etkinlikse, yürütmeden sonra hata ayıklayıcı üst etkinliği keser.

## <a name="debug-with-f5"></a>F5 ile hata ayıklama

Bir Iş akışı konsol uygulaması oluşturuyorsanız, uygulamanızda ve iş akışınızda hata ayıklamaya başlamak için **F5** tuşuna basın. Kendi başına bir etkinlik kitaplığı oluşturuyorsanız, başlangıç projesi olarak bir yürütülebilir ana bilgisayar uygulaması belirtmeniz gerekir. **Çözüm Gezgini** bir başlangıç projesi ayarlamak için konağın proje adına sağ tıklayın ve **Başlangıç projesi olarak ayarla** ' yı seçin.
