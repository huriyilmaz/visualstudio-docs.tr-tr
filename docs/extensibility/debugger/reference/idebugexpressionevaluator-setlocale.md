---
title: 'Idebugexpressiondeğerlendirici:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57ddee6e1796159c505b67982f25d1ba09684561
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729465"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Bu yöntem, yazdırılabilir sonuçlar oluşturmak için kullanılacak dili ayarlar.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parametreler
`wLangID`\
'ndaki Dil tanımlayıcısı.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, ifade değerlendiricisi (EE) yüklenirken birçok kez çağrılabilir, bu nedenle EE 'ın anında diller arasında geçiş yapabilmesi gerekir. EE, uygun dilde hata iletileri ve dizeler döndürmek için bu yerel ayarı kullanır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
