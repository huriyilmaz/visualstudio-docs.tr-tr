---
title: 'IDebugProgramNode2:: GetEngineInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b337d9c6742c1c3b0379a757761955151cc6dc6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898658"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Bir programı çalıştıran hata ayıklama altyapısının (DE) adını ve tanımlayıcısını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>Parametreler
`pbstrEngine`\
dışı Programı çalıştıran kişinin adını döndürür (C++ özel: Bu, çağıranın altyapının adı ile ilgilenmediğini belirten bir null işaretçi olabilir).

`pguidEngine`\
dışı Programı çalıştırmanın genel benzersiz tanımlayıcısını döndürür (C++ ' a özgü: Bu, çağıranın altyapının GUID 'SI ile ilgilenmediğini belirten bir null işaretçi olabilir).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
