---
title: IDebugProgram2::GetDebugProperty | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722885"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Programın özelliklerini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Parametreler
`ppProperty`\
[çıkış] Programın özelliklerini temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemle döndürülen özellikler programa özgüdir. Programın birden fazla özelliği döndürmesi gerekiyorsa, bu yöntemle döndürülen [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi ek özelliklerden oluşan bir kapsayıcıdır ve [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yöntemini çağırmak tüm özelliklerin listesini döndürür.

 Bir `IDebugProperty2` program, arabirim üzerinden açıklanabilecek herhangi bir sayı ve ek özellik türünü ortaya çıkarabilir. Bir IDE, ek program özelliklerini genel bir özellik tarayıcısı kullanıcı arabirimi aracılığıyla görüntüleyebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
