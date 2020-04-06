---
title: IDebugProcess3::DisableENC | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b39bb448501bacd5ab458b7e61bb1a5044bc8a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723739"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Bu yöntem, bu işlemde (ve içerdiği tüm programları) Edit ve Continue'yi açıkça devre dışı kılabilir. Özel bir bağlantı noktası `E_NOTIMPL`tedarikçisi her zaman dönmelidir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parametreler
`reason`\
[içinde] [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) numaralandırmabir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, hata kodu döndürür.

> [!NOTE]
> Özel bir bağlantı noktası `E_NOTIMPL`tedarikçisi her zaman dönmelidir.

## <a name="remarks"></a>Açıklamalar
 Bir işlem için Düzenleme ve Devam devre dışı bırakıldıktan sonra, yalnızca işlemi yeniden başlatarak yeniden etkinleştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
