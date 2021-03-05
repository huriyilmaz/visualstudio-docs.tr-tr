---
description: Yöntemi çağırmak için gereken her bir bağımsız değişkenin türü için bir Numaralandırıcı oluşturur.
title: 'IDebugMethodField:: EnumArguments | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 04815bb1fc148893c5b594223f6b92bfb7e0d97f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172131"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Yöntemi çağırmak için gereken her bir bağımsız değişkenin türü için bir Numaralandırıcı oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parametreler
`ppParams`\
dışı Bağımsız değişken türleri listesini temsil eden bir [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) nesnesi döndürür. Bağımsız değişken yoksa null değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür veya bağımsız değişken yoksa S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Her öğe, her parametrenin türünü temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesidir. Her parametrenin türü hakkında bilgi almak için [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) yöntemini çağırın.

 Parametresinin adı ile birlikte gerekiyorsa, [Trsarameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
