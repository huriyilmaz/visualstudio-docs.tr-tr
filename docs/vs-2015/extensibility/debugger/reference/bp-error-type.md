---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2317fafe410cacfca1c77b669a54669ea6e2224a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153541"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir kesme noktasının hata türünü belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Üyeler  
 BPET_NONE  
 Kesme noktası hatası olmadığını belirtir.  
  
 BPET_TYPE_WARNING  
 Bir uyarı stili kesme noktası hatası belirtir.  
  
 BPET_TYPE_ERROR  
 Bir hata stili kesme noktası hatası belirtir.  
  
 BPET_SEV_HIGH  
 Yüksek öneme sahip kesme noktası hatasını belirtir.  
  
 BPET_SEV_GENERAL  
 Orta öneme sahip kesme noktası hatasını belirtir.  
  
 BPET_SEV_LOW  
 Düşük öneme sahip kesme noktası hatasını belirtir.  
  
 BPET_TYPE_MASK  
 Bir maske stili kesme noktası hatası belirtir.  
  
 BPET_SEV_MASK  
 Bir önem düzeyi-maske stili kesme noktası hatası belirtir.  
  
 BPET_GENERAL_WARNING  
 Genel uyarı stili kesme noktası hatasını belirtir.  
  
 BPET_GENERAL_ERROR  
 Genel hata stili kesme noktası hatasını belirtir.  
  
 BPET_ALL  
 Tüm kesme noktası hata türlerini belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değerler bit düzeyinde birleştirilebilir `OR` ve `dwType` [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) yapısının üyesi için kullanılabilir. [Enumerrorkesmenoktaları](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) metoduna parametre olarak geçirilir.  
  
 Kesme noktası hata türü bir tür ve önem derecesi oluşur. Bu, kesme noktası hata türünün hiçbir şekilde bir tür (örneğin, `BPET_TYPE_ERROR` ) veya önem derecesi (örneğin,) olduğu anlamına gelir `BPET_SEV_GENERAL` . `BPET_GENERAL_WARNING` ve `BPET_GENERAL_ERROR` genel uyarı ve hata kesme noktaları için önceden tanımlanmış değerler sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
