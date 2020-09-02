---
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e59d3eb67fe45003babf53862736a435586deeeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537946"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir bağlantı noktası sağlayıcısı için bir çekirdek sunucu seçmek ve bunlarla etkileşim kurmak için destek sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Özel bir bağlantı noktası sağlayıcısı bu arabirimi, kullanılacak çekirdek sunucuyu seçebilmeniz için uygular.  
  
## <a name="methods"></a>Yöntemler  
 Aşağıdaki tabloda **IDebugPortSupplierEx2**yöntemleri gösterilmektedir.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Bağlantı noktası sağlayıcısı için çekirdek sunucuyu ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: Portprıv. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
