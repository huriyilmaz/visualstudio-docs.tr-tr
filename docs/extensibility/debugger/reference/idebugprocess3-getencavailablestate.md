---
description: Bu yöntem, sürecin geçerli Düzenle ve Devam Ediyor durumunu alır.
title: IDebugProcess3::GetENCAvailableState | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1cad537b0c575bf792c1ad06b398e564ff6a5aba25f65a919b8df372506db803
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416215"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Bu yöntem, sürecin geçerli Düzenle ve Devam Ediyor durumunu alır. Özel bir bağlantı noktası sağlayıcı her zaman geri `E_NOTIMPL` dönmeli.

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
[out] [EncUnavailableReason enumerasyonundan](../../../extensibility/debugger/reference/encunavailablereason.md) bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür.

> [!NOTE]
> Özel bir bağlantı noktası sağlayıcı her zaman geri `E_NOTIMPL` dönmeli.

## <a name="remarks"></a>Açıklamalar
 Bu durum [DisableENC tarafından etkilenebilir.](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
