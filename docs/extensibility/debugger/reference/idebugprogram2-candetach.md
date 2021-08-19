---
description: Bir hata ayıklama altyapısının (DE) programdan ayrılabilir olup olmadığını belirler.
title: IDebugProgram2::CanDetach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f679245f5f2918b5d938f0d88df3a96afe0482c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132775"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Bir hata ayıklama altyapısının (DE) programdan ayrılabilir olup olmadığını belirler.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Dönüş Değeri
 ayırabilirse `S_OK` döndürür; aksi takdirde bir hata kodu döndürür. `S_FALSE`DE'nin programdan ayrılamazsa döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
