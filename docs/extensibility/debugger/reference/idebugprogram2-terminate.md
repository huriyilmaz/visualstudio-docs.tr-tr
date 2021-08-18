---
description: Programı sonlandırılır.
title: IDebugProgram2::Terminate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a78679b57f4d10679d9aa0bd36efe79d7d52970a3eb4dd919371934acfea9a98
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292344"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Programı sonlandırılır.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Mümkünse program sonlandırılır ve işlemden kaldırılacaktır; aksi takdirde, hata ayıklama altyapısı (DE) gerekli temizlemeyi gerçekleştirecek.

 Bu yöntem veya [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) yöntemi, genellikle kullanıcının tüm hata ayıklamalarını durdurması için IDE tarafından çağrılır. İdeal olarak bu yöntemin uygulanması, işlemi içinde programı sonlandırmalı. Bu mümkün yoksa, DE programın bu işlemde daha fazla çalışmasına engel olmalı (ve gerekli temizlemeleri yapılmalıdır). Yöntem IDE tarafından çağrılsa, yöntem çağrıldıktan bir süre `IDebugProcess2::Terminate` sonra tüm `IDebugProgram2::Terminate` işlem sonlandırılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
