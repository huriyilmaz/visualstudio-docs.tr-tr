---
title: IDebugProgram2::Sonlandırma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913c90e34e308ce5bb4ceecface739afc8d03f3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722752"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Programı sonlandırır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Mümkünse, program sonlandırılır ve işlemden indirilir; aksi takdirde, hata ayıklama motoru (DE) gerekli herhangi bir temizleme gerçekleştirecektir.

 Bu yöntem veya [Sonlandırma](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) yöntemi, genellikle kullanıcının tüm hata ayıklamadurdurma yanıt olarak, IDE tarafından çağrılır. Bu yöntemin uygulanması, ideal olarak, süreç içinde programı sona erdirmelidir. Bu mümkün değilse, DE programın bu işlemde daha fazla çalışmasını engellemelidir (ve gerekli temizlemeyi yapmak). Yöntem `IDebugProcess2::Terminate` IDE tarafından çağrıldıysa, `IDebugProgram2::Terminate` yöntem çağrıldıktan sonra tüm işlem sonlandırılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
