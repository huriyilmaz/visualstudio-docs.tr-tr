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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603590"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>Nasıl Yapılır: İş Akışlarında Kesme Noktası Ayarlama (Eski)
Bu konu başlığı altında [!INCLUDE[wf](../includes/wf-md.md)] , uygulamalar için eski sürümü kullanılarak kesme noktalarının nasıl ayarlanacağı açıklanmaktadır [!INCLUDE[wfd1](../includes/wfd1-md.md)] . [!INCLUDE[wfd2](../includes/wfd2-md.md)]Uygulamanızın ya da ' i [!INCLUDE[wf2](../includes/wf2-md.md)] hedeflemesini gerektiren eski ' ni kullanın [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[vs2010](../includes/vs2010-md.md)] Bir uygulama oluşturmak için eski ' [!INCLUDE[wf2](../includes/wf2-md.md)] nı kullandığınızda, C# ' de kesme noktaları ve Visual Studio 'da yaptığınız gibi Visual Basic kodu ayarlayabilirsiniz. Beklenen şekilde, iş akışı yürütmesi, ayarladığınız her kesme noktasında durmaktadır.

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

3. **İşlev** metin kutusunda bu söz dizimini kullanarak bir etkinliğin adını belirtin: `QualifiedActivityId[:[FullClassName][:InstanceId]]` .

    > [!NOTE]
    > İsteğe bağlı olarak, **işlev** metin kutusunda etkinlik adını kullanmak yerine, iş akışı etkinliğinin mutlak yolunu belirterek bir kesme noktası ayarlayabilirsiniz. Örneğin, **WorkflowConsoleApplication1** adlı bir iş akışı çözümünüz olduğunu ve **Workflow1** adlı çözümde **Delay1**adlı bir etkinlik kullanan bir iş akışı olduğunu varsayalım. **Delay1** etkinlik adını kullanabilir veya yolu **Delay1: WorkflowConsoleApplication1. Workflow1** veya **Delay1: WorkflowConsoleApplication1. Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}** olarak belirtebilirsiniz.

4. İşlev adını doğrulamak için **IntelliSense kullan** onay kutusunu seçin.

     Bu onay kutusu seçili değilse, kesme noktası adı doğrulaması yapılmaz.

5. **Dil** listesinden **iş akışı** ' nı seçin.

6. **Tamam**’a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Windows Workflow Foundation Için Visual Studio hata ayıklayıcısını çağıran](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [eski Iş akışlarının hatalarını ayıklama](../workflow-designer/debugging-legacy-workflows.md) (eski)