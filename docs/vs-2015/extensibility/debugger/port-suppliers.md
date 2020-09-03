---
title: Bağlantı noktası tedarikçileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153703"
---
# <a name="port-suppliers"></a>Bağlantı Noktası Sağlayıcıları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklayıcı mimarisi açısından, bir **bağlantı noktası sağlayıcısı**:  
  
- , Bir sunucu tarafından içerilir ve bu sunucuya istekte bağlantı noktaları sağlar.  
  
- , İçeren sunucuya bağlantı noktaları ekleyebilir ve kaldırabilir.  
  
- , Sunucu tarafından sağlanan tüm bağlantı noktalarını numaralandırabilirler.  
  
- , Kayıt defteri aracılığıyla Visual Studio ile kaydedilen bir [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimi tarafından temsil edilir. Bu arabirim [Getporttedarikçinin](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)çağırarak elde edilebilir.  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Varsayılan bir bağlantı noktası tedarikçisi ve varsayılan bir bağlantı noktası sağlar. Özel bir bağlantı noktasının uygulanması gerekiyorsa, bu özel bağlantı noktalarını sağlamak için özel bir bağlantı noktası tedarikçinin de uygulanması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Larý](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Adet](../../extensibility/debugger/ports.md)   
 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
