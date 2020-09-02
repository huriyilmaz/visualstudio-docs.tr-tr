---
title: 'IDebugPendingBreakpoint2:: bind | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 33cdcad38e2f46962120dcd63c1be21675060be0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194532"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu bekleyen kesme noktasını bir veya daha fazla kod konumuna bağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Bind(   
   void   
);  
```  
  
```csharp  
int Bind();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_BP_DELETED`Kesme noktasının silinip silinmediğini döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem çağrıldığında, bir hata ayıklama altyapısı (DE), bu bekleyen kesme noktasını eşleşen tüm kod konumlarına bağlamayı denemelidir.  
  
 Bu yöntem çağrıldıktan sonra, [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) veya [enumerrorbreakpoint](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)çağrılarına çağrı yapmadan önce çağıranın, bekleyen kesme noktasının bağlandığını veya hata olduğunu belirten olayları beklemesi gerekir. Yöntemler sırasıyla tüm bağlantılı veya hata kesme noktalarını numaralandıracaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
