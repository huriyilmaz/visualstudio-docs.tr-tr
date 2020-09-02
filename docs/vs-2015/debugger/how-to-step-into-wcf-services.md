---
title: 'Nasıl yapılır: WCF hizmetlerine adımla | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 951d5f39fbf3929d094cc18de5fe108b46753b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176530"
---
# <a name="how-to-step-into-wcf-services"></a>Nasıl Yapılır: WCF Hizmetleri İçine Adımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] , BIR WCF hizmetine adım adım ekleyebilirsiniz. WCF hizmeti [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] istemcisiyle aynı çözümde ise, WCF hizmetinin içindeki kesme noktalarına de ulaşırsınız.  
  
 Çalışma adımlaması için app.config veya Web.config dosyasında hata ayıklamanın etkinleştirilmiş olması gerekir. Hata ayıklamayı etkinleştirme ve WCF hizmetlerine adımlamayı kısıtlama hakkında daha fazla bilgi için bkz. [WCF hata ayıklama kısıtlamaları](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Bir WCF hizmetine adım adım  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]WCF istemcisi ve WCF hizmeti projelerini içeren bir çözüm oluşturun.  
  
2. Çözüm Gezgini, WCF Istemci projesine sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' ya tıklayın.  
  
3. app.config veya web.config dosyasında hata ayıklamayı etkinleştirin. Daha fazla bilgi için bkz. [WCF hata ayıklama kısıtlamaları](../debugger/limitations-on-wcf-debugging.md).  
  
4. İstemci projesindeki, adımlamayı başlatmak istediğiniz konumda bir kesme noktası ayarlayın. Genellikle, bu, WCF hizmeti çağrısından hemen önce olacaktır.  
  
5. Kesme noktasında çalıştırın ve ardından adımlamayı başlatın. Hata ayıklayıcı, hizmette otomatik olarak adım adım sunulacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF hizmetlerinde hata ayıklama](../debugger/debugging-wcf-services.md)   
 [WCF hata ayıklama sınırlamaları](../debugger/limitations-on-wcf-debugging.md)   
 [Nasıl Yapılır: Kendini Barındıran WCF Hizmetinde Hata Ayıklama](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
