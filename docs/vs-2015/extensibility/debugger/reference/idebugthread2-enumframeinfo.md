---
title: 'IDebugThread2:: EnumFrameInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efda31daae198befbda35803ef71e1d0322e9bbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153076"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu iş parçacığının yığın çerçevelerinin bir listesini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFieldSpec`  
 'ndaki [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Numaralandırmadaki, [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapılarının hangi alanlarının doldurulacağını belirten bayrakların birleşimi. `FIF_FUNCNAME_FORMAT` İşlev adını tek bir dizeye biçimlendirmek için bayrak belirtin.  
  
 `nRadix`  
 'ndaki Numaralandırıcı içindeki sayısal bilgileri biçimlendirmede kullanılan Radix.  
  
 `ppEnum`  
 dışı Yığın çerçevesini açıklayan [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) yapılarının listesini Içeren bir [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 İş parçacığının çerçeveleri, ilk olarak numaralandırılan geçerli çerçeveye ve son numaralandırılan en eski çerçeveye göre sırayla numaralandırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
