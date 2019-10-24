---
title: 'Nasıl yapılır: şirket içinde barındırılan WCF hizmetinde hata ayıklama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12654a6aa1abb34c9813e8d29c7608814021a3f0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733977"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama
*Şirket içinde barındırılan bir hizmet* , IIS 'de, WCF hizmeti ana bilgisayarında veya [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] geliştirme sunucusunda ÇALıŞTıRMAYAN bir WCF hizmetidir. Şirket içinde barındırılan bir WCF 'yi hata ayıklamanın en kolay yolu, **hata** ayıklama menüsünde **hata ayıklamayı Başlat** ' ı seçtiğinizde hem istemci hem de sunucuyu başlatmak üzere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yapılandırmaktır.

 WCF hizmeti içinde kendiliğinden barındırılsa veya NT hizmeti gibi bu şekilde başlatılabilen bir işlem ise, bu yöntemi kullanamazsınız. Bunun yerine, aşağıdakilerden birini yapabilirsiniz:

- Hata ayıklayıcıyı barındırma işlemine el ile ekleyin. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     veya

- İstemcide hata ayıklamayı başlatın ve ardından hizmete bir çağrı yapın. Bu, App. config dosyasında hata ayıklamayı etkinleştirmenizi gerektirir. Daha fazla bilgi için [WCF hata ayıklama sınırlamaları](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Hem istemciyi hem de Konağı Visual Studio 'dan başlatmak için

1. Hem istemci hem de sunucu projelerini içeren bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çözümü oluşturun.

2. **Hata ayıklama** menüsünde **Başlat** ' ı seçtiğinizde, çözümü hem istemci hem de sunucu işlemlerini başlatacak şekilde yapılandırın.

   1. **Çözüm Gezgini**, çözüm adına sağ tıklayın.

   2. **Başlangıç projelerini ayarla**' ya tıklayın.

   3. **Çözüm \<name > özellikleri** Iletişim kutusunda **birden çok başlangıç projesi**seçin.

   4. **Birden çok başlangıç projesi** kılavuzunda, sunucu projesine karşılık gelen satırda **eylem** ' e tıklayın ve **Başlat**' ı seçin.

   5. İstemci projesine karşılık gelen satırda **eylem** ' e tıklayın ve **Başlat**' ı seçin.

   6. **Tamam**'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmetlerinde Hata Ayıklama](../debugger/debugging-wcf-services.md)
- [WCE Hata Ayıklama Sınırlamaları](../debugger/limitations-on-wcf-debugging.md)
- [Nasıl Yapılır: WCF Hizmetleri İçine Adımlama](../debugger/how-to-step-into-wcf-services.md)