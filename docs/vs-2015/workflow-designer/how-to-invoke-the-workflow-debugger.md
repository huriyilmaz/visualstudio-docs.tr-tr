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
ms.openlocfilehash: e702b402d5350641aa01d341106634efe5f6c6c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849265"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Nasıl Yapılır: İş Akışı Hata Ayıklayıcısını Çağırma
Genellikle, diğer Visual Studio programlama dillerinde yazılmış programlarda hata ayıkladığınızda olduğu gibi iş akışlarında hata ayıklaması yapabilirsiniz. İş akışı hata ayıklayıcısını aşağıdaki yollarla başlatabilirsiniz:

- İş akışı örneğiniz için çalışan konak işlemini seçmek üzere **hata ayıklama** menüsünde **İşleme İliştir** ' i seçin. Bu yordam, Yönetilen koddaki bir ana bilgisayar işlemine iliştirme ile aynıdır.

- İş akışının bir örneğini çalıştırmaya başlamak veya bir kesme noktası isabet ettikten sonra çalışmaya devam etmek için **F5** tuşuna basın.

- Uzaktan hata ayıklamayı kullan. Uzaktan hata ayıklamayı kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzaktan hata ayıklamayı etkinleştirme](https://msdn.microsoft.com/library/febz73k0.aspx).

    > [!NOTE]
    > İş akışı uygulaması x86 mimarisini hedefliyorsa ve 64 bitlik bir işletim sistemi çalıştıran bir makinede barındırılıyorsa, uzak [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] makinede yüklü olmadığı veya iş akışı uygulamasının hedefi **HERHANGI bir CPU**'ya değiştirilmediği takdirde uzaktan hata ayıklama çalışmaz.

### <a name="stepping-through-code"></a>Kod üzerinden adımla

- **Adım adım**: **F11**kullanarak bir etkinliğe adım adım ekleyebilirsiniz. Hata ayıklayıcı, tanımlı herhangi bir işleyicide adımları. Hiçbir işleyici tanımlanmamışsa, etkinliğin üzerinde veya diğer etkinlikleri içeren bileşik etkinliklerle ilk yürütme etkinliğinin içine adımlayın.

- **Dışarı adımla:** **SHIFT-F11**kullanarak bir etkinliğin dışına ilerliğinizi sağlayabilirsiniz. Bir etkinliğin dışına geçmek, geçerli etkinliği ve tüm eşdüzey etkinliklerini tamamlamaya kadar çalıştırır. Hata ayıklayıcı daha sonra geçerli etkinliğin üst öğesiyle kesilir. Kod işleyiciden atlama yaparken, hata ayıklayıcı işleyicinin ilişkilendirildiği etkinliği keser.

- **Adımlama**: **F10**kullanarak bir etkinliğin üzerinde ilerliğinizi yapabilirsiniz. Bileşik bir etkinliğin üzerine adımlarken, hata ayıklayıcı bileşik etkinliğin ilk yürütülebilir alt öğesi üzerinde kesilir. Bir etkinlik gibi bileşik olmayan bir üzerinde Adımlama yaparken <xref:System.Activities.Statements.Assign> , hata ayıklayıcı aktiviteyi ve ilgili işleyicileri yürütür ve sonraki etkinlikte kesilir. Yürütülen etkinlik bileşik bir etkinlikte son alt etkinlikse, yürütmeden sonra hata ayıklayıcı üst etkinliği keser.

### <a name="debugging-with-f5"></a>F5 ile hata ayıklama

- Bir Iş akışı konsol uygulaması projesi oluşturuyorsanız, uygulamanızda ve iş akışınızda hata ayıklamaya başlamak için **F5** tuşuna basın. Kendi başına bir etkinlik kitaplığı oluşturuyorsanız, başlangıç projesi olarak bir çalıştırılabilir konak uygulamanız olması gerekir. **Çözüm Gezgini**bir başlangıç projesi ayarlamak için konağın proje adına sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır:](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [iş akışı Tasarımcısı iş akışlarında hata ayıklama Iş](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) akışlarında kesme noktaları ayarlama
