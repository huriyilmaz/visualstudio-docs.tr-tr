---
description: Verilen değerlendirme bayrağı ayarlarını ve bir zaman aşımı değerini kullanan bir nesnesi oluşturur.
title: IDebugFunctionObject2::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: abe71179784d69ed78d372fd5e3b3bb1e8728c0b52d20b532556f145e052f7e3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389793"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Verilen değerlendirme bayrağı ayarlarını ve bir zaman aşımı değerini kullanan bir nesnesi oluşturur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Parametreler
`pConstructor`\
[in] Oluşturulacak nesnenin oluşturucusu temsil eden bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi.

`dwArgs`\
[in] Dizide parametre `pArg` sayısı. Oluşturucuya geçirilen parametre sayısını temsil eder.

`pArgs`\
[in] Oluşturucuya geçirilen parametreleri temsil eden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesneleri dizisi.

`dwEvalFlags`\
[in] Değerlendirmenin nasıl gerçekleştirilecek [olduğunu belirten EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) numaralamasında yer alan bayrakların birleşimi.

`dwTimeout`\
[in] Bu yöntemden dönmeden önce bek için milisaniye cinsinden en uzun süre. Süresiz olarak beklemek için **INFINITE** kullanın.

`ppObject`\
[out] Yeni oluşturulan **nesneyi temsil eden bir IDebugObject** döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir sınıfın örneğini veya bir parametre olan oluşturucu gerektiren diğer karmaşık türü temsil eden bir nesne oluşturmak için bu yöntemi çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
