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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c851689d9e47250457c93d1621acb6c5db98732b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081561"
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
