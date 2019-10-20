---
title: 'Nasıl yapılır: Iş akışlarında kesme noktaları ayarlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d1bbb18a9015b52b3d65cb8f8fd02674693abc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659134"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Nasıl yapılır: Iş akışlarında kesme noktalarını ayarlama
@No__t_0 kullandığınızda, grafik iş akışlarınızda Visual Basic veya C# kod içinde yaptığınız gibi kesme noktaları belirleyebilirsiniz. Beklenen şekilde, iş akışı yürütmesi, ayarladığınız her kesme noktasında durmaktadır.

 Kesme noktasında üç durum vardır: *bekleyen*, *bağlantılı*ve *hata*. Bir kesme noktası ayarladığınızda, beklemede olur ve düz kırmızı simgeyle temsil edilir. Çalışma zamanı, iş akışı türünü yüklemiştir, bu, bağlanır olur. Kesme noktası için geçerli olmayan bir etkinlik adı gibi yanlış bir biçim belirtirseniz, bir hata penceresi görüntülenir. Kesme noktası, kesme noktası penceresine hala eklenir, ancak küçük bir "x" ile işaretlenir.

> [!NOTE]
> Çağrılan iş akışlarında kesme noktalarının ayarlanması desteklenmez.
>
> [!WARNING]
> Hata ayıklamadan önce **Araçlar**, **Seçenekler**, **hata ayıklama** menüsünden **yalnızca kendi kodum etkinleştir (yalnızca yönetilen)** seçeneğini seçtiğinizden emin olun. Başka bir sıra içinde iç içe geçmiş iki diziniz varsa ve ilk iç dizide bir kesme noktası ayarladıysanız, <strong>yalnızca kendi kodum etkinleştir (yalnızca yönetilen)</strong>seçeneği seçili değilse, **F11** tuşuna basmak ikinci iç dizide hata ayıklamaz.
>
> [!WARNING]
> XAML dosya özelliğinin tam yolu doğru değilse iş akışındaki kesme noktaları isabet almaz. XAML dosyasının tam yolu, proje/çözüm başka bir klasöre veya başka bir makineye taşıdıktan sonra doğru değil. Tam yol özelliğini kaydetmek ve güncelleştirmek için CTRL + S ' yi seçin.

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Tasarım görünümündeki bir etkinlikte bir kesme noktası ayarlamak için

1. Hata ayıklayıcının kesilmesini istediğiniz etkinliği seçin.

2. **Hata Ayıkla** menüsünde, **kesme noktasını aç**' ı seçin. Etkinliğin sol üst köşesinde kırmızı bir simge görünür.

     Alternatif olarak, etkinlik seçildikten sonra kısayol **F9** tuşuna da basabilir veya etkinliğe sağ tıklayıp **kesme noktası** ' nı seçip bağlam menüsünden **kesme noktası** ' nı seçebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır:](../workflow-designer/how-to-invoke-the-workflow-debugger.md) [iş akışı Tasarımcısı](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) [nasıl yapılır: XAML hatalarını ayıklama iş akışı Tasarımcısı ile](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md) iş akışı hata ayıklaması