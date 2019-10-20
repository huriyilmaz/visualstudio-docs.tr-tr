---
title: 'Nasıl yapılır: kaydırma çubuğunu özelleştirerek kodunuzu Izleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a852b0e5ac6c6a677caab97279a0b0cb0299d27f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670631"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Nasıl yapılır: kaydırma çubuğunu özelleştirerek kodunuzu Izleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzun kod dosyalarıyla çalışırken her şeyi göz önünde bulundurmanız zor olabilir. Kodunuzda neler olduğunu bir kuşbakışı görünümü sağlamak için kod penceresinin kaydırma çubuğunu özelleştirebilirsiniz.

### <a name="to-show-annotations-on-the-scroll-bar"></a>Kaydırma çubuğundaki ek açıklamaları göstermek için

1. Kaydırma çubuğunu, kod değişikliklerini, kesme noktalarını, hataları ve yer imlerini gösterecek şekilde ayarlayabilirsiniz.

     **Kaydırma çubuğu** seçenekleri sayfasını açın (**Araçlar, Seçenekler metin düzenleyici. Tüm diller** veya belirli bir dil ya da hızlı başlatma penceresinde **kaydırma çubuğu** yazın.

2. **Dikey kaydırma çubuğu üzerinde ek açıklamaları göster**' i seçin ve ardından görmek istediğiniz ek açıklamaları seçin. ( **İşaretler** seçeneği kesme noktaları ve yer işaretleri içerir.)

3. Şimdi deneyin. Büyük bir kod dosyası açın ve dosyadaki birkaç yerde ortaya çıkan bir şeyi değiştirin. Kaydırma çubuğu, değişikliklerinizin etkisini gösterir. bu sayede, sahip olmayan bir şeyi değiştirdiyseniz değişikliklerinizi geri alabilirsiniz.

     Bu, bir dize aramadan sonra kaydırma çubuğunun nasıl göründüğünü aşağıda bulabilirsiniz. Dizenin tüm örneklerinin göründüğünü unutmayın.

     ![Bir dize aramadan sonra kaydırma çubuğu.](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")

     Dizenin tüm örnekleri değiştirildikten sonra kaydırma çubuğu. İşlemin bazı sorunlara neden olduğunu hemen görebilirsiniz.

     ![Bir dizeyi hatalar ile değiştirdikten sonra kaydırma çubuğu](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")

### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Kaydırma çubuğunun görüntüleme modunu ayarlamak için

1. Kaydırma çubuğunun iki modu, çubuk modu (varsayılan) ve eşleme modu vardır. Çubuk modu yalnızca kaydırma çubuğundaki ek açıklama göstergelerini görüntüler. Harita modunda kod satırları kaydırma çubuğunda gösterilir. Ne kadar geniş olduğunu ve işaretçinin üzerine getirdiğinizde temeldeki kodu gösterip göstermediğini seçebilirsiniz. Kaydırma çubuğundaki bir konuma tıkladığınızda, imleç koddaki bu konuma gider. Daraltılmış bölgeler farklı şekilde gölgelidir; bunları çift tıklattığınızda genişletilir.

     **Kaydırma çubuğu** seçenekleri sayfasında **Dikey kaydırma çubuğu Için çubuk modunu kullan** ' ı veya **Dikey kaydırma çubuğu için eşleme modunu kullan**' ı seçin. **Kaynak genel bakış** açılan menüsünde genişliği seçebilirsiniz.

     Arama örneği, eşleme modu açık olduğunda ve genişlik orta olarak ayarlandığında şöyle görünür:

     ![Harita modundaki kaydırma çubuğu](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")

2. Harita modunda, imleci yukarı ve aşağı kaydırma çubuğunu taşırken kodun önizlemelerini etkinleştirmek için **Önizleme araç Ipucunu göster** seçeneğini belirleyin. Şöyle görünür:

     ![Araç İpucu içeren kaydırma çubuğu](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")

     Harita modu kaydırma davranışını ve Önizleme araç ipucunu korumak ancak kaynak koda genel bakış görmek istemiyorsanız, **kaynağa genel bakış** seçeneğini **kapalı**olarak ayarlayabilirsiniz.
