---
description: Bu yöntem, bu işlemde (ve içerdiği tüm programlarda) Düzenle ve Devam'ı açıkça devre dışı bırakıyor.
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88be8c57bac99761ac4bcfb6d92451ba0245c483
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071993"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Bu yöntem, bu işlemde (ve içerdiği tüm programlarda) Düzenle ve Devam'ı açıkça devre dışı bırakıyor. Özel bir bağlantı noktası sağlayıcı her zaman geri `E_NOTIMPL` dönmeli.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parametreler
`reason`\
[in] [EncUnavailableReason enumerasyonundan](../../../extensibility/debugger/reference/encunavailablereason.md) bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür.

> [!NOTE]
> Özel bir bağlantı noktası sağlayıcı her zaman geri `E_NOTIMPL` dönmeli.

## <a name="remarks"></a>Açıklamalar
 Bir işlem için Düzenle ve Devam Edin devre dışı bırakılmıştır, yalnızca işlemi yeniden başlatarak yeniden etkinleştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
