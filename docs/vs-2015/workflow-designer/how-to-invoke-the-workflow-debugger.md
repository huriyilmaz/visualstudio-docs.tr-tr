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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849265"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>Nasıl yapılır: Iş akışı hata ayıklayıcısını çağırma
Genellikle, diğer Visual Studio programlama dillerinde yazılmış programlarda hata ayıkladığınızda olduğu gibi iş akışlarında hata ayıklaması yapabilirsiniz. İş akışı hata ayıklayıcısını aşağıdaki yollarla başlatabilirsiniz:

- İş akışı örneğiniz için çalışan konak işlemini seçmek üzere **hata ayıklama** menüsünde **İşleme İliştir** ' i seçin. Bu yordam, Yönetilen koddaki bir ana bilgisayar işlemine iliştirme ile aynıdır.

- Tuşuna **F5** iş akışı örneği çalıştırmaya başlayın ya da bir kesme noktasına isabet sonra çalışmaya devam eder.

- Uzaktan hata ayıklamayı kullan. Uzaktan hata ayıklamayı kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzaktan hata ayıklamayı etkinleştirme](https://msdn.microsoft.com/library/febz73k0.aspx).

    > [!NOTE]
    > İş akışı uygulaması x86 mimarisini hedefliyorsa ve 64 bitlik bir işletim sistemi çalıştıran bir makinede barındırılıyorsa, uzak makineye [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] yüklenmezse veya iş akışı uygulamasının hedefi **herhangi BIR CPU**olarak değiştirilmediği takdirde uzaktan hata ayıklama çalışmaz.

### <a name="stepping-through-code"></a>Kod üzerinden adımla

- **Adım içinde**: kullanarak bir etkinlik adım **F11**. Hata ayıklama adımlarında içinde tanımlanan herhangi bir işleyici. Hiçbir tutucusu tanımlanmazsa, etkinliğin adım veya diğer etkinlikler içeren bileşik etkinliklerle ilk yürütme etkinliğini adım.

- **Dışarı adımla:** **SHIFT-F11**kullanarak bir etkinliğin dışına ilerliğinizi sağlayabilirsiniz. Bir etkinlik dışına Adımlama geçerli etkinliği ve tüm eşdüzey tamamlanana kadar etkinlikleri çalıştırır. Hata ayıklayıcı, ardından geçerli etkinliğin üst öğede keser. Bir kod işleyicisinden Adımlama, hata ayıklayıcı işleyici ilişkilendirildiği faaliyete keser.

- **Step Over**: bir etkinlik kullanıldığında üzerinden adım **F10**. Bileşik bir etkinliğin üzerine adımlarken, hata ayıklayıcı bileşik etkinliğin ilk yürütülebilir alt öğesi üzerinde kesilir. <xref:System.Activities.Statements.Assign> etkinlik gibi bir bileşik olmayan üzerinde Adımlama yaparken, hata ayıklayıcı aktiviteyi ve ilgili işleyicileri ve bir sonraki etkinliğin üzerinde kesintiler yürütür. Yürütülen etkinlik bileşik bir etkinlikte son alt etkinlikse, yürütmeden sonra hata ayıklayıcı üst etkinliği keser.

### <a name="debugging-with-f5"></a>F5 tuşuna basarak hata ayıklama

- Bir Iş akışı konsol uygulaması projesi oluşturuyorsanız, uygulamanızda ve iş akışınızda hata ayıklamaya başlamak için **F5** tuşuna basın. Kendi başına bir etkinlik kitaplığı oluşturuyorsanız, başlangıç projesi olarak bir çalıştırılabilir konak uygulamanız olması gerekir. **Çözüm Gezgini**bir başlangıç projesi ayarlamak için konağın proje adına sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır:](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [iş akışı Tasarımcısı iş akışlarında hata ayıklama Iş](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) akışlarında kesme noktaları ayarlama
