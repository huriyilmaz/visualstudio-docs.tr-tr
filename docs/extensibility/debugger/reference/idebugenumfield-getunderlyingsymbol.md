---
description: Bu yöntem, numaralandırmanın adını temsil eden bir IDebugField döndürür.
title: 'Ihata ayıklama Genumfield:: GetUnderlyingSymbol | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9343c1b0908c6b132ea982a46623b8c1cf20efc9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092572"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Bu yöntem, numaralandırmanın adını temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametreler
`ppField`\
dışı Bu numaralandırmanın adını açıklayan [IDebugField 'ı](../../../extensibility/debugger/reference/idebugfield.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Numaralandırma adı Ayrıca, [bağlama](../../../extensibility/debugger/reference/idebugbinder-bind.md)kullanarak bir bellek konumuna bağlı olan numaralandırmanın türünü de içerir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bağladığınızda](../../../extensibility/debugger/reference/idebugbinder-bind.md)
