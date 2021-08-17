---
description: Nesnenin kullanıcı verilerini temsil edip ettiğini belirler.
title: IDebugObject2::IsUserData | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b62e150a210222e47269ebeb948e90b2521b55e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043069"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Nesnenin kullanıcı verilerini temsil edip ettiğini belirler.

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
[out] Nesne kullanıcı verilerini temsil ediyorsa sıfır olmayan ( ) `TRUE` döndürür; yoksa sıfır ( `FALSE` ) döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kullanıcı verileri, JustMyCode olarak belirlenmiş bir modülün parçası olan herhangi bir nesnedir (bir modülü kullanıcı kodu olarak işaret alan ve bu nedenle yığın izlemesinde görünür olan kullanıcı tarafından yapılandırılabilir bir seçenek).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
