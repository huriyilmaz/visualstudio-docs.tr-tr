---
title: FRAMEıNFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0fa2299e47924a10a6d0b02a982535865164191
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160156"
---
# <a name="frameinfo"></a>FRAMEINFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Yığın çerçevesini açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```csharp  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## <a name="members"></a>Üyeler  
 m_dwValidFields  
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi.  
  
 m_bstrFuncName  
 Yığın çerçevesiyle ilişkili işlev adı.  
  
 m_bstrReturnType  
 Yığın çerçevesiyle ilişkili dönüş türü.  
  
 m_bstrArgs  
 Yığın çerçevesiyle ilişkili işlevin bağımsız değişkenleri.  
  
 m_bstrLanguage  
 İşlevin uygulandığı dil.  
  
 m_bstrModule  
 Yığın çerçevesiyle ilişkili modül adı.  
  
 m_addrMin  
 En düşük fiziksel yığın adresi.  
  
 m_addrMAX  
 En büyük fiziksel yığın adresi.  
  
 m_pFrame  
 Bu yığın çerçevesini temsil eden [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) nesnesi.  
  
 m_pFrame  
 Bu yığın çerçevesini içeren modülü temsil eden [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) nesnesi.  
  
 m_fHasDebugInfo  
 `TRUE`Verilen çerçevede hata ayıklama bilgileri varsa sıfır olmayan ().  
  
 m_fHasDebugInfo  
 `TRUE`Yığın çerçevesi artık geçerli olmayan kodla ilişkilendirilirse sıfır olmayan ().  
  
 m_fHasDebugInfo  
 `TRUE`Yığın çerçevesine oturum hata ayıklama Yöneticisi (SDM) tarafından açıklama eklendiğinde sıfır olmayan ().  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, doldurulacak [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) yöntemine geçirilir. Bu yapı Ayrıca, [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) yöntemine yapılan çağrıdan döndürülen [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) arabiriminde bulunan bir listede de bulunur.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
