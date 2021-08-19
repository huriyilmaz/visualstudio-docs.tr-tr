---
description: İşlemdeki tüm programları ayırarak hata ayıklayıcıyı bu işlemden ayırır.
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
ms.openlocfilehash: 44e45fa717f1292b57626df3fc68f90c8f0a9639
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126732"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
İşlemdeki tüm programları ayırarak hata ayıklayıcıyı bu işlemden ayırır.

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
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Tüm Programlar ve işlemler çalışmaya devam eder, ancak artık hata ayıklama oturumunun bir parçası değildir. Ayırma işlemi tamamlandıktan sonra, bu işlem (ve programları) için daha fazla hata ayıklama olayı gönderilmez.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
