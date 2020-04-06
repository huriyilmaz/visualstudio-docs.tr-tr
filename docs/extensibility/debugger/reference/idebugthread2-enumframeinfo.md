---
title: IDebugThread2::EnumFrameInfo | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bd3c6d46a577930cc7a2b87c85cd82a55f8cf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718853"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Bu iş parçacığı için yığın çerçevelerinin listesini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
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

## <a name="parameters"></a>Parametreler
`dwFieldSpec`\
[içinde] [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapılarının hangi alanlarının dolduruleceğini belirten [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) numaralandırmadan gelen bayrakların birleşimi. Işlev `FIF_FUNCNAME_FORMAT` adını tek bir dize halinde biçimlendirmek için bayrağı belirtin.

`nRadix`\
[içinde] Radix, sayısal bilgileri sayısal olarak biçimlendirmede kullanılır.

`ppEnum`\
[çıkış] Yığın çerçevesini açıklayan [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapılarının listesini içeren bir [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacığının çerçeveleri sırayla numaralandırılır ve geçerli çerçeve ilk sırada numaralandırılır ve en eski çerçeve en son numaralandırılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
