---
description: Programı sonlandırır.
title: 'IDebugProgram2:: Terminate | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 404df2be6718ab691ec47081b6fd400a1ddc8891
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084473"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Programı sonlandırır.

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
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Mümkünse, program sonlandırılır ve işlemden kaldırılır; Aksi takdirde, hata ayıklama altyapısı (DE) gerekli temizleme işlemlerini gerçekleştirir.

 Bu yöntem veya [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) yöntemi IDE tarafından, genellikle kullanıcıya yanıt olarak tüm hata ayıklamayı durdurma olarak çağrılır. Bu yöntemin uygulanması ideal olarak programı işlem içinde sonlandıracaktır. Bu mümkün değilse, DE programın bu işlemde daha fazla çalışma yapmasını (ve gerekli temizleme işlemlerini yapmasını) önlemesi gerekir. `IDebugProcess2::Terminate`YÖNTEMI IDE tarafından çağrıldıysa, Yöntem çağrıldıktan sonra işlemin tamamının sonlandırılması gerekir `IDebugProgram2::Terminate` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
