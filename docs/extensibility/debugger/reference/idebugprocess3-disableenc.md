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
ms.openlocfilehash: 429cacbc4ef87224459493b0815d9e5dcff7fac3f61ca510d334501226a08eef
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276743"
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
