---
title: WCF Hizmeti Self-Hosted hata ayıklaması | Microsoft Docs
description: Kendinden konak WCF hizmetinin hata ayıklamayı öğrenin. En kolay yol (ancak her zaman mümkün değildir), Visual Studio ve sunucuyu başlatmak için yapılandırmadır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 73933801ca158a4e348eba26f379383ecd793a22
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074130"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama
Kendinden *konak hizmet IIS,* WCF Hizmet Ana Bilgisayarı veya Geliştirme Sunucusu içinde çalıştır olmayan bir WCF [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hizmetidir. Kendinden konak WCF'de hata ayıklamanın en kolay yolu, Hata Ayıklama menüsünde Hata Ayıklamayı Başlat'ı seçerseniz hem istemci hem de sunucuyu başlatecek [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **şekilde yapılandırmaktır.** 

 WCF hizmeti içinde kendi kendine barındırıldı ise veya NT hizmeti gibi bu şekilde başlatılamayacak bir işlem varsa, bu yöntemi kullanamazsınız. Bunun yerine, aşağıdakilerden birini yapabilirsiniz:

- Hata ayıklayıcıyı barındırma sürecine el ile iliştirin. Daha fazla bilgi için [bkz. Çalışan İşlemlere Ekleme.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

     — veya —

- İstemcide hata ayıklamaya başlama ve ardından hizmete yapılan çağrıya adımlama. Bunun için hata ayıklamayı app.config gerekir. Daha fazla bilgi için, [WCF Hata Ayıklama sınırlamaları.](../debugger/limitations-on-wcf-debugging.md)

### <a name="to-start-both-client-and-host-from-visual-studio"></a>İstemciden ve konaktan hem istemci Visual Studio

1. Hem istemci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hem de sunucu projelerini içeren bir çözüm oluşturun.

2. Hata Ayıklama menüsünde Başlat'ı seçerseniz çözümü hem istemci hem de **sunucu işlemlerini** **başlatecek şekilde** yapılandırma.

   1. Bu **Çözüm Gezgini** çözüm adına sağ tıklayın.

   2. Başlangıç **Projelerini Ayarla'ya tıklayın.**

   3. Çözüm Özellikleri **iletişim \<name> kutusunda** Birden Çok Başlangıç **Projesi'ne tıklayın.**

   4. Birden **Çok Başlangıç Projesi kılavuzunda,** sunucu projesine karşılık gelen satırda Eylem'e tıklayın ve **Başlat'ı** **seçin.**

   5. İstemci projesine karşılık gelen satırda Eylem'e tıklayın ve **Başlat'ı** **seçin.**

   6. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmetlerinde Hata Ayıklama](../debugger/debugging-wcf-services.md)
- [WCF Hata Ayıklama sınırlamaları](../debugger/limitations-on-wcf-debugging.md)
- [Nasıllı: WCF Hizmetleri'ne AdımLa](../debugger/how-to-step-into-wcf-services.md)
