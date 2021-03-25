---
description: Bir programı çalıştıran hata ayıklama altyapısının (DE) adını ve tanımlayıcısını alır.
title: 'IDebugProgramNode2:: GetEngineInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a902db31cb4d48810e673e7807bd3944c2a875
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053535"
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
