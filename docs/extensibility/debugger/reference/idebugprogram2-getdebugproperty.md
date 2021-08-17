---
description: Programın özelliklerini alır.
title: IDebugProgram2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e733c57b83cce517bad5680f409abe23ef1432db134276389bbb54880f4328ce
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338884"
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
[out] Programın özelliklerini [temsil eden bir IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem tarafından döndürülen özellikler programa özeldir. Programın birden fazla özellik dönmesi gerekirse, bu yöntem tarafından döndürülen [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi ek özelliklerin bir kapsayıcısıdır ve [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) yöntemini çağırarak tüm özelliklerin listesini döndürür.

 Bir program, arabirim aracılığıyla tanımlanebilecek herhangi bir sayıda ve tür ek özelliği açığa `IDebugProperty2` çıkarır. IDE, genel bir özellik tarayıcısı kullanıcı arabirimi aracılığıyla ek program özelliklerini görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
