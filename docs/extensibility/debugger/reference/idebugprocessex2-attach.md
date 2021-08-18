---
description: Bu yöntem, bir oturumun artık işlemde hata ayıklarken işlem olduğunu bilgi sağlar.
title: IDebugProcessEx2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5687031d1b4cd0be439ef1953f54a609e19f6366
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071932"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Bu yöntem, bir oturumun artık işlemde hata ayıklarken işlem olduğunu bilgi sağlar.

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
[in] Bu işleme oturum ekleme işlemini benzersiz olarak tanımlayan bir değer.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Geçirilen arabirim yalnızca tanımlama bilgisi olarak kabul edilir. Bu işleme iliştirilen oturum hata ayıklama yöneticisini benzersiz olarak tanımlayan bir değerdir; sağlanan arabirimde kullanılan yöntemlerin `pSession` hiçbiri işlevsel değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
