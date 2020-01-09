---
title: İş Akışı Tasarımcısı ile İş Akışlarında Hata Ayıklama
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
ms.openlocfilehash: 4b8de1ff9875d175c956a45b87d459d0943e783c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597067"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>İş Akışı Tasarımcısı iş akışlarında hata ayıkla

**İş akışı Tasarımcısı** , iş akışlarının ve özel etkinliklerin hatalarını ayıklama özelliğini sağlar. İşlem ve davranış, varsayılan Visual Studio hata ayıklayıcıyla benzerdir.

## <a name="invoke-the-workflow-debugger"></a>İş akışı hata ayıklayıcıyı çağır

Genellikle, diğer Visual Studio programlama dillerinde yazılmış programlarda hata ayıkladığınızda olduğu gibi iş akışlarında hata ayıklaması yapabilirsiniz. İş akışı hata ayıklayıcısını aşağıdaki yollarla başlatabilirsiniz:

- İş akışı örneğiniz için çalışan konak işlemini seçmek üzere **hata ayıklama** menüsünde **İşleme İliştir** ' i seçin. Bu yordam, Yönetilen koddaki bir ana bilgisayar işlemine iliştirme ile aynıdır.

- Tuşuna **F5** iş akışı örneği çalıştırmaya başlayın ya da bir kesme noktasına isabet sonra çalışmaya devam eder.

- Uzaktan hata ayıklamayı kullan. Uzaktan hata ayıklamayı kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzaktan hata ayıklamayı etkinleştirme](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

   > [!NOTE]
   > İş akışı uygulaması x86 mimarisini hedefliyorsa ve 64 bitlik bir işletim sistemi çalıştıran bir makinede barındırılıyorsa, uzak makineye Visual Studio yüklü değilse veya iş akışı uygulamasının hedefi **herhangi BIR CPU**olarak değiştirilmediği takdirde uzaktan hata ayıklama çalışmaz.

## <a name="step-through-code"></a>Kodunuz içinde adım adım

- **Adımla**: **F11**tuşuna basarak bir etkinliğe adımla. Hata ayıklama adımlarında içinde tanımlanan herhangi bir işleyici. Hiçbir tutucusu tanımlanmazsa, etkinliğin adım veya diğer etkinlikler içeren bileşik etkinliklerle ilk yürütme etkinliğini adım.

- **Dışarı adımla:** **Shıft**+**F11**tuşuna basarak bir etkinliği adımla. Bir etkinlik dışına Adımlama geçerli etkinliği ve tüm eşdüzey tamamlanana kadar etkinlikleri çalıştırır. Hata ayıklayıcı, ardından geçerli etkinliğin üst öğede keser. Bir kod işleyicisinden Adımlama, hata ayıklayıcı işleyici ilişkilendirildiği faaliyete keser.

- **Adımlama**: bir etkinliğin üzerinde, **F10**tuşuna basarak adımla. Bileşik bir etkinliğin üzerine adımlarken, hata ayıklayıcı bileşik etkinliğin ilk yürütülebilir alt öğesi üzerinde kesilir. <xref:System.Activities.Statements.Assign> etkinlik gibi bir bileşik olmayan üzerinde Adımlama yaparken, hata ayıklayıcı aktiviteyi ve ilgili işleyicileri ve bir sonraki etkinliğin üzerinde kesintiler yürütür. Yürütülen etkinlik bileşik bir etkinlikte son alt etkinlikse, yürütmeden sonra hata ayıklayıcı üst etkinliği keser.

## <a name="debug-with-f5"></a>F5 ile hata ayıklama

Bir Iş akışı konsol uygulaması oluşturuyorsanız, uygulamanızda ve iş akışınızda hata ayıklamaya başlamak için **F5** tuşuna basın. Kendi başına bir etkinlik kitaplığı oluşturuyorsanız, başlangıç projesi olarak bir yürütülebilir ana bilgisayar uygulaması belirtmeniz gerekir. **Çözüm Gezgini**bir başlangıç projesi ayarlamak için konağın proje adına sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.
