---
title: IDebugProcess3::GetENCAvailableState | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77345cfc3aa1dd95482052893e7c09591ad7cd4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723647"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Bu yöntem, geçerli Edit ve Devam işleminin durumunu alır. Özel bir bağlantı noktası `E_NOTIMPL`tedarikçisi her zaman dönmelidir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>Parametreler
`pReason`\
[çıkış] [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) numaralandırmabir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, hata kodu döndürür.

> [!NOTE]
> Özel bir bağlantı noktası `E_NOTIMPL`tedarikçisi her zaman dönmelidir.

## <a name="remarks"></a>Açıklamalar
 Bu durum [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)tarafından etkilenebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
