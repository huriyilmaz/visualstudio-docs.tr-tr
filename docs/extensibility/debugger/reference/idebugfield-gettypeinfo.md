---
title: IDebugField::GetTypeInfo | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: faa3464f0396999f36604aa88c429235d4849688
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728783"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Bu yöntem, sembol veya tür hakkında türbağımsız bilgi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>Parametreler
`pTypeInfo`\
[çıkış] Verilen [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) yapısındaki tür bilgilerini verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Türden bağımsız bilgiler, örneğin AppDomain'i, modülü ve sembolü içeren sınıfı içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
