---
title: 'IDebugEngine2:: SetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e2a6dbd5d5700d4d64625490c016da2d04af6d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878948"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Hata ayıklama altyapısının (DE) belirli bir özel durumu nasıl işleyeceğini belirtir.

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
'ndaki Özel durumu ve nasıl hata ayıklaması yapıldığını açıklayan [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) yapısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bir DE, birinci şans, ikinci şans veya hiç olmadığı için bir özel durum oluşturan programın durdurulması için bir DE talimat verebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
