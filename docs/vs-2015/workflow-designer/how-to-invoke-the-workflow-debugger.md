---
title: 'Nasıl yapılır: Iş akışı hata ayıklayıcısını çağırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 34c5cdae4b8730c9058a87061456d5ab6d186c53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603664"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Nasıl yapılır: Iş akışı hata ayıklayıcısını çağırma
Genellikle, diğer Visual Studio programlama dillerinde yazılmış programlarda hata ayıkladığınızda olduğu gibi iş akışlarında hata ayıklaması yapabilirsiniz. İş akışı hata ayıklayıcısını aşağıdaki yollarla başlatabilirsiniz:

- İş akışı örneğiniz için çalışan konak işlemini seçmek üzere **hata ayıklama** menüsünde **İşleme İliştir** ' i seçin. Bu yordam, Yönetilen koddaki bir ana bilgisayar işlemine iliştirme ile aynıdır.

- İş akışının bir örneğini çalıştırmaya başlamak veya bir kesme noktası isabet ettikten sonra çalışmaya devam etmek için **F5** tuşuna basın.

- Uzaktan hata ayıklamayı kullan. Uzaktan hata ayıklamayı kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzaktan hata ayıklamayı etkinleştirme](http://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > İş akışı uygulaması x86 mimarisini hedefliyorsa ve 64 bitlik bir işletim sistemi çalıştıran bir makinede barındırılıyorsa, uzak makineye [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yüklenmedikçe veya iş akışı uygulamasının hedefi olarak **değiştirilirse uzaktan hata ayıklama çalışmaz. Herhangi bir CPU**.

### <a name="stepping-through-code"></a>Kod üzerinden adımla

- **Adım adım**: **F11**kullanarak bir etkinliğe adım adım ekleyebilirsiniz. Hata ayıklayıcı, tanımlı herhangi bir işleyicide adımları. Hiçbir işleyici tanımlanmamışsa, etkinliğin üzerinde veya diğer etkinlikleri içeren bileşik etkinliklerle ilk yürütme etkinliğinin içine adımlayın.

- **Dışarı adımla:** **SHIFT-F11**kullanarak bir etkinliğin dışına ilerliğinizi sağlayabilirsiniz. Bir etkinliğin dışına geçmek, geçerli etkinliği ve tüm eşdüzey etkinliklerini tamamlamaya kadar çalıştırır. Hata ayıklayıcı daha sonra geçerli etkinliğin üst öğesiyle kesilir. Kod işleyiciden atlama yaparken, hata ayıklayıcı işleyicinin ilişkilendirildiği etkinliği keser.

- **Adımlama**: **F10**kullanarak bir etkinliğin üzerinde ilerliğinizi yapabilirsiniz. Bileşik bir etkinliğin üzerine adımlarken, hata ayıklayıcı bileşik etkinliğin ilk yürütülebilir alt öğesi üzerinde kesilir. @No__t_0 etkinlik gibi bir bileşik olmayan üzerinde Adımlama yaparken, hata ayıklayıcı aktiviteyi ve ilgili işleyicileri ve bir sonraki etkinliğin üzerinde kesintiler yürütür. Yürütülen etkinlik bileşik bir etkinlikte son alt etkinlikse, yürütmeden sonra hata ayıklayıcı üst etkinliği keser.

### <a name="debugging-with-f5"></a>F5 ile hata ayıklama

- Bir Iş akışı konsol uygulaması projesi oluşturuyorsanız, uygulamanızda ve iş akışınızda hata ayıklamaya başlamak için **F5** tuşuna basın. Kendi başına bir etkinlik kitaplığı oluşturuyorsanız, başlangıç projesi olarak bir çalıştırılabilir konak uygulamanız olması gerekir. **Çözüm Gezgini**bir başlangıç projesi ayarlamak için konağın proje adına sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır:](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [iş akışı Tasarımcısı iş akışlarında hata ayıklama Iş](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) akışlarında kesme noktaları ayarlama