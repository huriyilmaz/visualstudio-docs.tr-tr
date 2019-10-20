---
title: 'Nasıl yapılır: Iş akışlarında kesme noktaları ayarlama (eski) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 182f28a2b21ae3129ce0d34fae97280ba0a07218
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603590"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Nasıl yapılır: Iş akışlarında kesme noktaları ayarlama (eski)
Bu konuda, eski [!INCLUDE[wfd1](../includes/wfd1-md.md)] kullanarak [!INCLUDE[wf](../includes/wf-md.md)] uygulamalarında kesme noktalarının nasıl ayarlanacağı açıklanmaktadır. @No__t_1 uygulamanızın [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ya da [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedeflemesi gerektiğinde eski [!INCLUDE[wfd2](../includes/wfd2-md.md)] kullanın.

 @No__t_2 uygulaması derlemek için [!INCLUDE[vs2010](../includes/vs2010-md.md)] eski [!INCLUDE[wfd2](../includes/wfd2-md.md)] kullandığınızda, ' de kesme noktaları C# ve Visual Basic kodu Visual Studio 'da yaptığınız gibi ayarlayabilirsiniz. Beklenen şekilde, iş akışı yürütmesi, ayarladığınız her kesme noktasında durmaktadır.

 Kesme noktasında üç durum vardır: *bekleyen*, *bağlantılı*ve *hata*. Bir kesme noktası ayarladığınızda, bekliyor ve boş kırmızı simgesiyle temsil edilir. Çalışma zamanı iş akışı türünü yüklemiştir, bu, bağımlıdır ve düz bir kırmızı simgeyle temsil edilir. Kesme noktası için geçerli olmayan bir etkinlik adı gibi yanlış bir biçim belirtirseniz, bir hata penceresi görüntülenir. Kesme noktası, kesme noktası penceresine hala eklenir, ancak küçük bir "x" ile işaretlenir.

 İş akışı tasarım yüzeyinde bir etkinliğin kesme noktalarını aşağıdaki yollarla ayarlayabilirsiniz:

- Etkinliğe sağ tıklayın ve **kesme noktası \ kesme noktası Ekle**' yi seçin.

- Etkinliği seçin ve F9 tuşuna basın.

- **Hata ayıklama** menüsünden **Yeni kesme noktası** ' nı seçin.

     Bu seçeneği, hata ayıklama sırasında hata ayıklayıcı bir kesme noktasında durdurulduğunda yeni bir kesme noktası ayarlamak için de kullanabilirsiniz.

    > [!NOTE]
    > Çağrılan iş akışlarında kesme noktalarının ayarlanması desteklenmez.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>Hata ayıklama menüsündeki yeni kesme noktası seçeneğini kullanarak bir kesme noktası ayarlamak için

1. **Hata Ayıkla** menüsünde **Yeni kesme noktası**' nı seçin.

2. **Işlevde kes**' e tıklayın.

     **Yeni kesme noktası** iletişim kutusu açılır.

3. **İşlev** metin kutusunda bir etkinliğin adını şu sözdizimini kullanarak belirtin: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.

    > [!NOTE]
    > İsteğe bağlı olarak, **işlev** metin kutusunda etkinlik adını kullanmak yerine, iş akışı etkinliğinin mutlak yolunu belirterek bir kesme noktası ayarlayabilirsiniz. Örneğin, **WorkflowConsoleApplication1** adlı bir iş akışı çözümünüz olduğunu ve **Workflow1** adlı çözümde **Delay1**adlı bir etkinlik kullanan bir iş akışı olduğunu varsayalım. **Delay1** etkinlik adını kullanabilir veya yolu **Delay1: WorkflowConsoleApplication1. Workflow1** veya **Delay1: WorkflowConsoleApplication1. Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}** olarak belirtebilirsiniz.

4. İşlev adını doğrulamak için **IntelliSense kullan** onay kutusunu seçin.

     Bu onay kutusu seçili değilse, kesme noktası adı doğrulaması yapılmaz.

5. **Dil** listesinden **iş akışı** ' nı seçin.

6. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Windows Workflow Foundation Için Visual Studio hata ayıklayıcısını çağıran](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [eski Iş akışlarının hatalarını ayıklama](../workflow-designer/debugging-legacy-workflows.md) (eski)