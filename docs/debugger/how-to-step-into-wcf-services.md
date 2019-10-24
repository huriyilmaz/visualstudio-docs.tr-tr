---
title: 'Nasıl yapılır: WCF hizmetlerine adımla | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c405b4fcca91f8deddce4d65c8a4155b90af49e0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732591"
---
# <a name="how-to-step-into-wcf-services"></a>Nasıl Yapılır: WCF Hizmetleri İçine Adımlama
@No__t_0, bir WCF hizmetine adım adım ekleyebilirsiniz. WCF hizmeti istemcisiyle aynı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çözümindeyse, WCF hizmeti içindeki kesme noktalarına da basabilirsiniz.

 Çalışma adımlaması için App. config veya Web. config dosyasında hata ayıklamanın etkinleştirilmiş olması gerekir. Hata ayıklamayı etkinleştirme ve WCF hizmetlerine adımlamayı kısıtlama hakkında daha fazla bilgi için bkz. [WCF hata ayıklama kısıtlamaları](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Bir WCF hizmetine adım adım

1. WCF istemcisi ve WCF hizmeti projelerini içeren bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çözümü oluşturun.

2. Çözüm Gezgini, WCF Istemci projesine sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' ya tıklayın.

3. App. config veya Web. config dosyasında hata ayıklamayı etkinleştirin. Daha fazla bilgi için bkz. [WCF hata ayıklama kısıtlamaları](../debugger/limitations-on-wcf-debugging.md).

4. İstemci projesindeki, adımlamayı başlatmak istediğiniz konumda bir kesme noktası ayarlayın. Genellikle, bu, WCF hizmeti çağrısından hemen önce olacaktır.

5. Kesme noktasında çalıştırın ve ardından adımlamayı başlatın. Hata ayıklayıcı, hizmette otomatik olarak adım adım sunulacaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmetlerinde Hata Ayıklama](../debugger/debugging-wcf-services.md)
- [WCE Hata Ayıklama Sınırlamaları](../debugger/limitations-on-wcf-debugging.md)
- [Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama](../debugger/how-to-debug-a-self-hosted-wcf-service.md)