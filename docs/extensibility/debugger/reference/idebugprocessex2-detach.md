---
title: IDebugProcessEx2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7379436ae0da57d7f8c47ce8484c810a53a0a453
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723364"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Bu yöntem, bir oturumun işlemde artık hata ayıklamayan süreci bilgilendirir.

## <a name="syntax"></a>Söz dizimi

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
