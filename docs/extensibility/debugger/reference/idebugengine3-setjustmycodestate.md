---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9930f8ecf0c2f9b6fff4ce1c9e3edb935c5a7912
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730679"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Bu yöntem, hata ayıklama motoruna JustMyCode durum bilgileri hakkında bilgi verebolur.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parametreler
`fUpdate`\
[içinde] Nonzero`TRUE`( ) geçerli bilgileri`FALSE`güncelleştirmek için, sıfır ( ) tüm bilgileri sıfırlamak için (daha önce ayarlanmış bir şeyi yok saymak).

`dwModules`\
[içinde] Bilgi yapılarının sayısı`rgJMCSpec.`

`rgJMCSpec`\
[içinde] Kullanılacak [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) yapıları dizisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 JustMyCode, yalnızca kullanıcıya ait kodu hata ayıklama ve sistem kodu gibi tüm ara kodları yok sayma kavramıdır— kaynak kodu bu sistem kodu için kullanılabilir olsa bile.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
