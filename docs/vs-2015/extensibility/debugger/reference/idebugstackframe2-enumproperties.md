---
title: 'IDebugStackFrame2:: EnumProperties | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f92db2c2fbafcd5be991281d7da4f594dcfb2c85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164796"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Yerel değişkenler gibi yığın çerçevesiyle ilişkili özellikler için bir Numaralandırıcı oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFieldSpec`  
 'ndaki Numaralandırılmış [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapılardaki hangi alanların doldurulacağını belirten [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Numaralandırmadaki bayrakların birleşimi.  
  
 `nRadix`  
 'ndaki Herhangi bir sayısal bilgiyi biçimlendirmede kullanılacak taban tabanı.  
  
 `refiid`  
 'ndaki Hangi [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapılarının numaralandırılacağını seçmek için kullanılan filtrenin GUID 'si (gibi) `guidFilterLocals` .  
  
 `dwTimeout`  
 'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süre (milisaniye cinsinden). `INFINITE`Sonsuza kadar beklemek için kullanın.  
  
 `pcelt`  
 dışı Numaralandırılan özelliklerin sayısını döndürür. Bu, [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) metodunu çağırma ile aynıdır.  
  
 `ppEnum`  
 dışı İstenen özelliklerin bir listesini içeren bir [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem tüm seçili özelliklerin tek bir çağrıyla alınmasına izin verdiğinden, [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) ve [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yöntemlerinin sıralı olarak çağrılması daha hızlıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
