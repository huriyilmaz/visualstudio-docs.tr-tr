---
title: WCF hizmetlerine adımla | Microsoft Docs
description: Windows Communication Foundation (WCF) hizmetine adımlayın. istemci ile aynı Visual Studio çözümindeyse, WCF hizmeti içindeki kesme noktaları ' nı ziyaret edin.
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
ms.openlocfilehash: a73d6438547138c016533562a0b7ae71f894967b3d5da08c9d2408fdc0029bb6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453455"
---
# <a name="how-to-step-into-wcf-services"></a>Nasıl Yapılır: WCF Hizmetleri İçine Adımlama
İçinde [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] , BIR WCF hizmetine adım adım ekleyebilirsiniz. WCF hizmeti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] istemcisiyle aynı çözümde ise, WCF hizmetinin içindeki kesme noktalarına de ulaşırsınız.

 Çalışma adımlaması için app.config veya Web.config dosyasında hata ayıklamanın etkinleştirilmiş olması gerekir. Hata ayıklamayı etkinleştirme ve WCF hizmetlerine adımlamayı kısıtlama hakkında daha fazla bilgi için bkz. [WCF hata ayıklama kısıtlamaları](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Bir WCF hizmetine adım adım

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]WCF istemcisi ve WCF hizmeti projelerini içeren bir çözüm oluşturun.

2. Çözüm Gezgini, WCF Istemci projesine sağ tıklayın ve ardından **başlangıç Project olarak ayarla**' ya tıklayın.

3. app.config veya web.config dosyasında hata ayıklamayı etkinleştirin. Daha fazla bilgi için bkz. [WCF hata ayıklama kısıtlamaları](../debugger/limitations-on-wcf-debugging.md).

4. İstemci projesindeki, adımlamayı başlatmak istediğiniz konumda bir kesme noktası ayarlayın. Genellikle, bu, WCF hizmeti çağrısından hemen önce olacaktır.

5. Kesme noktasında çalıştırın ve ardından adımlamayı başlatın. Hata ayıklayıcı, hizmette otomatik olarak adım adım sunulacaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmetlerinde Hata Ayıklama](../debugger/debugging-wcf-services.md)
- [WCF hata ayıklama sınırlamaları](../debugger/limitations-on-wcf-debugging.md)
- [Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama](../debugger/how-to-debug-a-self-hosted-wcf-service.md)