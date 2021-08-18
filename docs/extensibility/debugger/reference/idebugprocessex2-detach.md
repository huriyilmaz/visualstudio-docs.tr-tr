---
description: Bu yöntem, bir oturumun işlemde artık hata ayıklamayan süreci bilgilendirir.
title: IDebugProcessEx2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f67ba1d07e1b92ed80e330ee279130061d0a647e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057570"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Bu yöntem, bir oturumun işlemde artık hata ayıklamayan süreci bilgilendirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametreler
`pSession`\
'ndaki Bu işlemi ayırmak için oturumu benzersiz bir şekilde tanımlayan bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Geçirilen arabirim, `pSession` Bu işleme ilk olarak eklenen oturum hata ayıklama yöneticisini benzersiz şekilde tanımlayan bir değer olan tanımlama bilgisi olarak değerlendirilir. sağlanan arabirimdeki yöntemlerin hiçbiri işlevsel değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
