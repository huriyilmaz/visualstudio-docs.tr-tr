---
title: IDebugBinder::ResolveRuntimeType | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bdbff651618365f3b68a142a6cb1e76836876a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735962"
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
[içinde] Çözülecek [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

`ppResolved`\
[çıkış] Nesnenin türünü [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)olarak döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir nesnenin çalışma zamanı türü derleme zamanında her zaman bilinmemektedir. Örneğin, çok biçimlilik kullanarak, bir bağımsız değişken bir düğme sınıfı gibi taban sınıf olarak bir işleve geçirilebilir. Gerçek bağımsız değişken, radyo düğmesi sınıfı gibi türetilmiş bir sınıf olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
