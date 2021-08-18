---
description: Bir program düğümünü hata ayıklama altyapıları (DEs) ve oturum hata ayıklama yöneticisi (SDM) tarafından kullanılabilir yapar.
title: IDebugProgramPublisher2::P ublishProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b004a6537eed565d1a607f99a35ea77267fa7ce
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118664"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
Bir program düğümünü hata ayıklama altyapıları (DEs) ve oturum hata ayıklama yöneticisi (SDM) tarafından kullanılabilir yapar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT PublishProgramNode(
   IDebugProgramNode2 *pProgramNode
);
```

```csharp
int PublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parametreler
`pProgramNode`\
[in] Kullanılabilir hale için program düğümünü temsil eden bir [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, programların hata ayıklama için bunları seçmeden ve başlatmadan önce bilgi sorgulamasını sağlar.

 Bir program düğümünü kullanılabilirlikten kaldırmak için [UnpublishProgramNode yöntemini](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
