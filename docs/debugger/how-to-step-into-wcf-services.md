---
title: WCF Hizmetleri hizmetine | Microsoft Docs
description: Bir Windows Communication Foundation (WCF) hizmetine geçin. İstemciyle aynı çözümde Visual Studio, WCF hizmetinin içindeki kesme noktalarına tıklayın.
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
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 22889b6024dc4201b7bd4618c6fe95ae9ed11f5f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051930"
---
# <a name="how-to-step-into-wcf-services"></a>Nasıl Yapılır: WCF Hizmetleri İçine Adımlama
içinde, [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] bir WCF hizmetine adım atabilirsiniz. WCF hizmeti istemciyle aynı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çözümde ise, WCF Hizmeti'nin içindeki kesme noktalarına isabet sabilirsiniz.

 Adım adım çalışmaya devam etmek için hata ayıklamanın app.config veya Web.config gerekir. Hata ayıklamayı etkinleştirme ve WCF hizmetlerini adımlama sınırlamaları hakkında bilgi için [bkz. WCF Hata](../debugger/limitations-on-wcf-debugging.md)Ayıklama sınırlamaları.

### <a name="to-step-into-a-wcf-service"></a>WCF Hizmetine adım atma

1. Hem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] WCF istemcisini hem de WCF hizmeti projelerini içeren bir çözüm oluşturun.

2. Bu Çözüm Gezgini WCF İstemcisi projesine sağ tıklayın ve ardından Başlangıç Olarak **Ayarla'ya Project.**

3. Hata ayıklamayı app.config veya web.config etkinleştirin. Daha fazla bilgi için [bkz. WCF Hata Ayıklama sınırlamaları.](../debugger/limitations-on-wcf-debugging.md)

4. Adımlama başlatmak istediğiniz istemci projesinde bir kesme noktası ayarlayın. Genellikle bu, WCF hizmet çağrısının hemen öncesinde olur.

5. Kesme noktası için çalıştırın ve adımlamaya başlama. Hata ayıklayıcısı hizmete otomatik olarak adımlar.

## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmetlerinde Hata Ayıklama](../debugger/debugging-wcf-services.md)
- [WCF Hata Ayıklama sınırlamaları](../debugger/limitations-on-wcf-debugging.md)
- [Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama](../debugger/how-to-debug-a-self-hosted-wcf-service.md)