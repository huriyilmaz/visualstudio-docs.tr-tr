---
description: Nesnenin Kullanıcı verilerini temsil edip etmediğini belirler.
title: 'IDebugObject2:: IsUserData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 485583c0d6ef8ac42b78612e68995462ef900795
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053730"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Nesnenin Kullanıcı verilerini temsil edip etmediğini belirler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Parametreler
`pfUser`\
dışı `TRUE`Nesne, Kullanıcı verilerini temsil ediyorsa sıfır () değerini döndürür `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanıcı verileri, Ditmycode olarak belirtilen bir modülün parçası olan herhangi bir nesnedir (bir modülü kullanıcı kodu olarak işaretleyen ve bu nedenle bir yığın izlemesinde görünür) Kullanıcı tarafından yapılandırılabilir bir seçenek.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
