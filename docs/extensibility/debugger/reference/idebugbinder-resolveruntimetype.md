---
description: Bu yöntem, bir nesnenin çalışma zamanı türünü belirler.
title: IDebugBinder::ResolveRuntimeType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62679b7a7f981ca2f45ef6c63ba61895b91471f93a01a1765ca8cef6c0fb1740
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360774"
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
[in] [Çözümlenecek IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

`ppResolved`\
[out] Nesnesinin türünü [IDebugField olarak döndürür.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir nesnenin çalışma zamanı türü derleme zamanında her zaman bilinmemektedir. Örneğin, çok biçimlilik kullanarak bağımsız değişken, bir işleve düğme sınıfı gibi temel sınıfı olarak geçirebilirsiniz. Gerçek bağımsız değişken, radyo düğmesi sınıfı gibi türetilmiş bir sınıf olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
