---
title: IDebugProcessEx2::Ekle | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d70da2530a1677367a22968436a17eba809fd24a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723385"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Bu yöntem, bir oturumun artık işlemi hata ayıklama işlemi olduğunu süreci bildirir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parametreler
`pSession`\
[içinde] Bu işleme iliştirilen oturumu benzersiz olarak tanımlayan bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Geçirilen `pSession` arabirim, yalnızca bir çerez olarak ele alınacaktır, bu işleme iliştiren oturum hata ayıklama yöneticisini benzersiz olarak tanımlayan bir değer; sağlanan arabirimdeki yöntemlerin hiçbiri işlevsel değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
