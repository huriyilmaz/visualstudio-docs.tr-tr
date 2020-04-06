---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bf436d788b517300bee9a13b66b0ca3747bcc43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724468"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Bu yöntem, bağlantı noktası tedarikçisinin hata ayıklama çağrıları arasında bağlantı noktalarını (diske yazarak) devam edip edemeyeceğini belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Dönüş Değeri
 `S_OK`bağlantı noktaları kalıcı olabilir `S_FALSE` veya bağlantı noktaları kalıcı olamaz belirtmek için.

## <a name="remarks"></a>Açıklamalar
 Bağlantı noktası tedarikçisi bağlantı noktalarını devam ettirebiliyorsa, bunu yok edildiğinde yapmalı ve bir kez daha anında yüklendiğinde yeniden yüklemelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
