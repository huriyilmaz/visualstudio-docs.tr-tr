---
description: Bir bağlantı noktası tedarikçinin yeni bağlantı noktaları ekleyebildiğini doğrular.
title: 'IDebugPortSupplier2:: CanAddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3203dd3ec8669a3adf37580398d1089d9a93776b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088191"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Bir bağlantı noktası tedarikçinin yeni bağlantı noktaları ekleyebildiğini doğrular.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Dönüş Değeri
 Bağlantı noktası eklenebilse `S_OK` ; Aksi takdirde, `S_FALSE` Bu bağlantı noktası sağlayıcısına hiçbir bağlantı noktası eklenemeyeceğini göstermek için döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi, [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) metodunu çağırmadan önce çağırın çünkü ikinci yöntem, bağlantı noktasını ve ekleme işlemini zaman alan bir işlem olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
