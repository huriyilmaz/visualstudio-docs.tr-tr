---
title: 'IDebugExpressionContext2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 500d5c1788e837a27b4affada50ecc59db122e8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729669"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Değerlendirme bağlamının adını alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parametreler
`pbstrName`\
dışı Değerlendirme bağlamının adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Ad, bu değerlendirme bağlamının açıklamasıdır. Bu, genellikle bu tam değerlendirme bağlamına başvuran bir ifade değerlendirici tarafından ayrıştırılabilen bir şeydir. Örneğin, C++ ' da ad aşağıdaki gibidir:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
