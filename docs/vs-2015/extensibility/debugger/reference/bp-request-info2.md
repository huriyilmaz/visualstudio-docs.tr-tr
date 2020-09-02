---
title: BP_REQUEST_INFO2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65edef6585fd8367c6fb23c291bf4e8376de8861
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153354"
---
# <a name="bp_request_info2"></a>BP_REQUEST_INFO2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Satıcı GUID, kısıtlama ve izleme noktası dahil bir kesme noktası uygulamak için gereken bilgileri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_REQUEST_INFO2 {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```csharp  
public struct BP_REQUEST_INFO2 {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
};  
```  
  
## <a name="members"></a>Üyeler  
 `dwFields`  
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi.  
  
 `guidLanguage`  
 Dil GUID 'SI.  
  
 `bpLocation`  
 Kesme noktası konumunun türünü belirten [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) yapısı.  
  
 `pProgram`  
 Kesme noktasının gerçekleştiği uygulamayı temsil eden [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.  
  
 `bstrProgramName`  
 Kesme noktasının gerçekleştiği uygulamanın adı.  
  
 `pThread`  
 Kesme noktasının gerçekleştiği iş parçacığını temsil eden [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) nesnesi.  
  
 `bstrThreadName`  
 Kesme noktasının gerçekleştiği iş parçacığının adı.  
  
 `bpCondition`  
 Kesme noktasının tetikleneceği koşulları açıklayan [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) yapısı.  
  
 `bpPassCount`  
 Kesme noktasının geçiş sayısı bilgilerini içeren [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) yapısı.  
  
 `dwFlags`  
 İstenen kesme noktasına yönelik bayrakları belirten [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) numaralandırmasındaki bayrakların birleşimi.  
  
 `guidVendor`  
 Satıcının GUID 'SI. Null bir değer olabilir.  
  
 `bstrConstraint`  
 Kesme noktası kısıtlamasının adı. Null bir değer olabilir.  
  
 `bstrTracepoint`  
 İzleme noktasının adı. Null bir değer olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) yöntemi tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
