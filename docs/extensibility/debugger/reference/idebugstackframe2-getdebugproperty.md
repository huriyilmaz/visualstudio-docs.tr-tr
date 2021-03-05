---
description: Yığın çerçevesinin özelliklerinin açıklamasını alır.
title: 'IDebugStackFrame2:: GetDebugProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDebugProperty
helpviewer_keywords:
- IDebugStackFrame2::GetDebugProperty
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 658da43471f483e80a1e77bd61f69dbc454a141e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159893"
---
# <a name="idebugstackframe2getdebugproperty"></a>IDebugStackFrame2::GetDebugProperty
Yığın çerçevesinin özelliklerinin açıklamasını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDebugProperty ( 
   IDebugProperty2** ppDebugProp
);
```

```csharp
int GetDebugProperty ( 
   out IDebugProperty2 ppDebugProp
);
```

## <a name="parameters"></a>Parametreler
`ppDebugProp`\
dışı Bu yığın çerçevesinin özelliklerini açıklayan bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yönteminin uygun filtrelerle çağrılması, yerel değişkenleri, yöntem parametrelerini, Yazmaçları ve yığın çerçevesiyle ilişkili "This" işaretçisini alabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
