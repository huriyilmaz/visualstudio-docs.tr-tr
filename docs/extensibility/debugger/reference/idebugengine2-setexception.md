---
description: Hata ayıklama altyapısının (DE) belirli bir özel durumu nasıl işlemesi gerektiğini belirtir.
title: IDebugEngine2::SetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf8dea7fb30d51140b6445642865d71af08d78de
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636313"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Hata ayıklama altyapısının (DE) belirli bir özel durumu nasıl işlemesi gerektiğini belirtir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parametreler
`pException`\
[in] Özel [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) ve hata ayıklamayı açıklayan bir özel durum yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 DE'ye programın ilk fırsatta, ikinci şansta veya hiç özel durum oluşturmaması için durdurması talimatı ve vernildi.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
