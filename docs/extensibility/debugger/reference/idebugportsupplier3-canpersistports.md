---
description: Bu yöntem, bağlantı noktası üreticisinin hata ayıklayıcıyı etkinleştirmeleri arasında bağlantı noktalarını (diske yazarak) kalıcı yapıp yapamayacağını belirler.
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 092f6e372d8f98e731ad90a7d261fe015d019656
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172015"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Bu yöntem, bağlantı noktası üreticisinin hata ayıklayıcıyı etkinleştirmeleri arasında bağlantı noktalarını (diske yazarak) kalıcı yapıp yapamayacağını belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Dönüş Değeri
 `S_OK` bağlantı noktaları kalıcı hale gelebilir veya `S_FALSE` bağlantı noktalarının kalıcı olarak olmadığını belirtmek için.

## <a name="remarks"></a>Açıklamalar
 Bağlantı noktası tedarikçisi bağlantı noktalarını kalıcı hale getirebilse, bu, yok edildiğinde bunu yapması gerekir ve bir kez daha sonra yeniden yüklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
