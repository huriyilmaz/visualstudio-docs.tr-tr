---
title: Bağlantı noktaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153693"
---
# <a name="ports"></a>Bağlantı noktaları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklayıcı mimarisi açısından, bir **bağlantı noktası**:  
  
- , Sunucuda çalışan bir işlem kümesi için bir kapsayıcıdır. Örneğin, bir bağlantı noktası, Windows CE tabanlı bir cihaza seri bir kabloyla veya ağ bağlantılı DCOM olmayan bir makineye bağlantıyı temsil edebilir. Yerel makinede çalışan tüm işlemlerin bulunduğu, yerel bağlantı noktası olarak adlandırılan özel bir bağlantı noktası.  
  
- , Kendisini ada veya tanımlayıcıya göre tanımlayabilir.  
  
- Bağlantı noktasında çalışan tüm işlemlerin listesini oluşturabilir ve bu süreçler başlatabilir ve sonlandırabilirsiniz.  
  
- , [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)'A bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) bağımsız değişkeni geçirerek oluşturulan bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilir.  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , yerel ve yönetilen tüm Windows tabanlı süreçlerini işleyen varsayılan bir bağlantı noktası sağlar. Windows tabanlı olmayan dış cihazlara yönelik bağlantılar için özel bir bağlantı noktası uygulanmalıdır. Bu tür özel bağlantı noktalarını sağlamak için özel bir bağlantı noktası tedarikçinin de uygulanması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Larý](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Lerse](../../extensibility/debugger/processes.md)   
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
