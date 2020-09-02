---
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e0f6455e6df8db88b1aae1a7b7f6965c0ee524b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188525"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, belirli bir bağlantı noktasında işlem ve program oluşturma ve yok etme için bir dinleyiciye (genellikle oturum hata ayıklama Yöneticisi [SDM] veya hata ayıklama altyapısı) bildirir. Bu bilgiler, bağlantı noktasında çalışan işlemlerin ve programların gerçek zamanlı bir görünümünü sunmak için kullanılabilir.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Visual Studio, genellikle program oluşturma ve yok etme hakkında bildirim almak için bu arabirimi uygular. Bir hata ayıklama altyapısı, bu tür bağlantı noktası olaylarını dinlemek için de bu arabirimi uygulayabilir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Tüm [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimleri, bir arabirim için sorgulanabilir <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> . Ardından <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> yöntemi arabirimi `IDebugPortEvents2` <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> almak için arabiriminde çağırılır <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> . Son olarak, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [olay](../../../extensibility/debugger/reference/idebugportevents2-event.md) yöntemi aracılığıyla olayları göndermek için arabirimindeki yöntemi çağırılır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemi gösterilmektedir `IDebugPortEvents2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Bağlantı noktasındaki işlemlerin ve programların oluşturulmasını ve yok edilmesini tanımlayan olayları gönderir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IDebugPortEvents2` , zaten ayıklanmakta olan bir işlemde çalışan programlarda hata ayıklamak için SDM tarafından da kullanılır.  
  
 Bağlantı noktası olayları bu arabirim tarafından SDM 'ye geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
