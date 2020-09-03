---
title: IDebugProcess2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9036ebc44835ab6c3ebd08b9fad4408d9cb97461
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724132"
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
