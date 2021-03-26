---
description: Bu yöntem, kalıcı bağlantı noktalarının listesinin numaralandırılmasına izin veren bir nesnesi alır.
title: 'IDebugPortSupplier3:: EnumPersistedPorts | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4fe55898f6dbc7713db6e013868b1c7f22a5faf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071967"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
Bu yöntem, kalıcı bağlantı noktalarının listesinin numaralandırılmasına izin veren bir nesnesi alır.

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
'ndaki Kalıcı bağlantı noktaları arasında bulunacak ve döndürülecek bağlantı noktası adlarının listesini içeren [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) yapısı. Yalnızca bu adlara sahip kalıcı bağlantı noktaları döndürülür.

`ppEnum`\
dışı [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) arabirimini uygulayan bir nesne.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kalıcı bağlantı noktaları, bir bağlantı noktası sağlayıcısı oluşturulduğunda yüklenir ve bağlantı noktası sağlayıcısı yok edildiğinde kaydedilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
