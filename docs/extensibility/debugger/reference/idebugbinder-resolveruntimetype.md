---
description: Bu yöntem, bir nesnenin çalışma zamanı türünü belirler.
title: 'Idebugciltçi:: ResolveRuntimeType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19e7285dd25009e7fe4aeb92974c70ce4109502c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143642"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Bu yöntem, bir nesnenin çalışma zamanı türünü belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>Parametreler
`pObject`\
'ndaki Çözümlenecek [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .

`ppResolved`\
dışı Nesnenin türünü bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)olarak döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir nesnenin çalışma zamanı türü, derleme zamanında her zaman bilinmez. Örneğin, çok biçimlilik kullanarak, bir bağımsız değişken bir işleve, düğme sınıfı gibi temel sınıfı olarak geçirilebilir. Gerçek bağımsız değişken, bir radyo düğmesi sınıfı gibi türetilmiş bir sınıf olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
