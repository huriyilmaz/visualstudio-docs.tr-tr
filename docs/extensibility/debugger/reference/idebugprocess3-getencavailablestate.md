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
ms.openlocfilehash: 1aab8ade63a8db1152913ca11834bbce4b2597a6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087918"
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
