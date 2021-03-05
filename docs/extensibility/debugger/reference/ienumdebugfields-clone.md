---
description: Bu yöntem, geçerli alan numaralandırmasının bir kopyasını ayrı bir nesne olarak döndürür.
title: 'IEnumDebugFields:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Clone
helpviewer_keywords:
- IEnumDebugFields::Clone method
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 965bc201646c7e068c58f9238dccba9a9e587d26
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224908"
---
# <a name="ienumdebugfieldsclone"></a>IEnumDebugFields::Clone
Bu yöntem, geçerli numaralandırmanın ayrı bir nesne olarak kopyasını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Clone(
   IEnumDebugFields** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametreler
`ppEnum`\
dışı Bu numaralandırmanın bir kopyasını ayrı bir nesne olarak döndürür.

## <a name="property-valuereturn-value"></a>Özellik Değeri/Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Numaralandırmanın kopyası, bu yöntemin çağrılışında orijinal ile aynı duruma sahiptir. Bununla birlikte, kopyanın ve özgün durumlarının durumları ayrıdır ve tek tek değiştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
