---
description: süreçteki tüm programları ayırarak hata ayıklayıcıyı bu işlemden ayırır.
title: IDebugProcess2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 957579bb2a19bffb0774ecd400218e5f8105127734969c26c43772dbea743bdc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276873"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
süreçteki tüm programları ayırarak hata ayıklayıcıyı bu işlemden ayırır.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Tüm programlar ve işlem çalışmaya devam eder, ancak artık hata ayıklama oturumunun bir parçası değil. Ayırma işlemi tamamlandıktan sonra, bu işlem (ve programları) için artık hata ayıklama olayları gönderilmez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
