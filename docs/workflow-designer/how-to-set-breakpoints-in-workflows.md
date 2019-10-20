---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: Iş akışlarında kesme noktaları ayarlama'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6d2806a8757f00924d51c76aea82cfc8c6a5673
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650325"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Nasıl yapılır: iş akışlarında kesme noktalarını ayarlama

İş Akışı Tasarımcısı kullandığınızda, grafik iş akışlarınızda Visual Basic veya C# kod içinde yaptığınız gibi kesme noktaları belirleyebilirsiniz. Beklenen şekilde, iş akışı yürütmesi, ayarladığınız her kesme noktasında durmaktadır.

Kesme noktasında üç durum vardır: *bekleyen*, *bağlantılı*ve *hata*. Bir kesme noktası ayarladığınızda, beklemede olur ve düz kırmızı simgeyle temsil edilir. Çalışma zamanı, iş akışı türünü yüklemiştir, bu, bağlanır olur. Kesme noktası için geçerli olmayan bir etkinlik adı gibi yanlış bir biçim belirtirseniz, bir hata penceresi görüntülenir. Kesme noktası, kesme noktası penceresine hala eklenir, ancak küçük bir "x" ile işaretlenir.

> [!NOTE]
> Çağrılan iş akışlarında kesme noktalarının ayarlanması desteklenmez.

> [!NOTE]
> Hata ayıklamadan önce **araçlar**  > **Seçenekler**  > **hata ayıklama** menüsünden **yalnızca kendi kodum etkinleştir (yalnızca yönetilen)** seçeneğini seçtiğinizden emin olun. Seçenek seçilmezse ve başka bir sıra içinde iç içe geçmiş iki diziniz varsa ve ilk iç dizide bir kesme noktası ayarlarsanız, **F11** tuşuna basmak ikinci iç dizide hata ayıklamaz.

> [!NOTE]
> XAML dosya özelliğinin tam yolu doğru değilse, iş akışındaki kesme noktaları isabet etmez. XAML dosyasının tam yolu, proje veya çözümü başka bir klasöre veya başka bir makineye taşıdıktan sonra doğru değil. Tam yol özelliğini kaydetmek ve güncelleştirmek için **Ctrl** +**S** ' yi seçin.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Tasarım görünümündeki bir etkinlikte bir kesme noktası ayarlamak için

1. Hata ayıklayıcının kesilmesini istediğiniz etkinliği seçin.

2. **Hata Ayıkla** menüsünde, **kesme noktasını aç**' ı seçin. Etkinliğin sol üst köşesinde kırmızı bir simge görünür.

   Alternatif olarak, etkinliği seçtikten sonra **F9** tuşuna basabilir veya sağ tıklama menüsünden**kesme noktası eklemek**  >  **kesme noktası** ' nı seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısı ile İş Akışlarında Hata Ayıklama](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Nasıl Yapılır: İş Akışı Tasarımcısı ile XAML Hatalarını Ayıklama](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)