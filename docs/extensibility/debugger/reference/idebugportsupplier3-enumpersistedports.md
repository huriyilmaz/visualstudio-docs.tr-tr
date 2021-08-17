---
description: Bu yöntem, kalıcı bağlantı noktaları listesinin numaralarına izin veren bir nesnesi verir.
title: IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7a9b4d97f40b8ebfeefa59fb40f0c912461c9828
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030236"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Bu yöntem, kalıcı bağlantı noktaları listesinin numaralarına izin veren bir nesnesi verir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>Parametreler
`PortNames`\
[in] Kalıcı [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) bulmak ve arasında dönmek için bağlantı noktası adlarının listesini içeren bir bağlantı noktası yapısı. Yalnızca bu adlara sahip kalıcı bağlantı noktaları döndürülür.

`ppEnum`\
[out] [IEnumDebugPorts2 arabirimini uygulayan nesne.](../../../extensibility/debugger/reference/ienumdebugports2.md)

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kalıcı bağlantı noktaları, bir bağlantı noktası sağlayıcı örneği yüklendiğinde yüklenir ve bağlantı noktası sağlayıcı yok edildiklerinden kaydedilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
