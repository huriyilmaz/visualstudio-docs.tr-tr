---
description: Bu yöntem, işlemin geçerli düzenleme ve devam etme durumunu alır.
title: 'IDebugProcess3:: GetENCAvailableState | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13ad3bc88ab1e9f10dc87db7d7124adc993b168c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149788"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Bu yöntem, işlemin geçerli düzenleme ve devam etme durumunu alır. Özel bir bağlantı noktası sağlayıcısı her zaman döndürmelidir `E_NOTIMPL` .

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>Parametreler
`pReason`\
dışı [Encunkullanılabilirliği Blereason](../../../extensibility/debugger/reference/encunavailablereason.md) numaralandırmasından bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

> [!NOTE]
> Özel bir bağlantı noktası sağlayıcısı her zaman döndürmelidir `E_NOTIMPL` .

## <a name="remarks"></a>Açıklamalar
 Bu durum, [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)'den etkilenebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
