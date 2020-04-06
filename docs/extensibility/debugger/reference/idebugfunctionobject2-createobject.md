---
title: IDebugFunctionObject2::CreateObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728486"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Değerlendirme bayrağı ayarları ve zaman sonu değeri verilen bir oluşturucu kullanan bir nesne oluşturur.

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
[içinde] Oluşturulacak nesnenin oluşturucuunu temsil eden bir [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nesnesi.

`dwArgs`\
[içinde] Dizideki `pArg` parametrelerin sayısı. Oluşturucuya geçirilen parametrelerin sayısını gösterir.

`pArgs`\
[içinde] Oluşturucuya geçirilen parametreleri temsil eden [bir iDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesne dizisi.

`dwEvalFlags`\
[içinde] [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasından değerlendirmenin nasıl yapılacağını belirten bayrakların birleşimi.

`dwTimeout`\
[içinde] Bu yöntemden dönmeden önce beklemek için milisaniye cinsinden maksimum süre. Sonsuza kadar beklemek için **SONSUZ** kullanın.

`ppObject`\
[çıkış] Yeni oluşturulan nesneyi temsil eden bir **IDebugObject** döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir sınıf örneğini veya bir parametre olan bir oluşturucu gerektiren başka karmaşık türü temsil eden bir nesne oluşturmak için bu yöntemi çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
