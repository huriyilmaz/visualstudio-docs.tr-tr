---
description: Bu iş parçacığı için yığın çerçevelerinin listesini alın.
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81f44920bfec45f4ba6860343e1fc5f19569714a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153140"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Bu iş parçacığı için yığın çerçevelerinin listesini alın.

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
[in] FRAMEINFO [yapılarının hangi alanlarının doldurulacaklarını](../../../extensibility/debugger/reference/frameinfo-flags.md) belirten bir FRAMEINFO_FLAGS [enumerasyonundan](../../../extensibility/debugger/reference/frameinfo.md) gelen bayrakların birleşimi. İşlev adını `FIF_FUNCNAME_FORMAT` tek bir dizede biçimlendirmek için bayrağını belirtin.

`nRadix`\
[in] Numaralayıcıda sayısal bilgileri biçimlendirmek için kullanılan radix.

`ppEnum`\
[out] Yığın çerçevesini açıklayan [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapılarının listesini içeren [bir IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 İş parçacığının çerçeveleri sırasıyla numaralandı, geçerli kare önce numaralandı ve en eski kare en son numaralandı.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
