---
title: 'Idebugexpressiondeğerlendirici:: SetRegistryRoot | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11e7cd69ed3f1e1b23cc0f2f03f3fd2cf912d308
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729420"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
Bu yöntem kayıt defteri kökünü ayarlar. Yan yana hata ayıklama için kullanılır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT SetRegistryRoot ( 
   LPCOLESTR ustrRegistryRoot
);
```

```csharp
int SetRegistryRoot(
   string ustrRegistryRoot
);
```

## <a name="parameters"></a>Parametreler
`ustrRegistryRoot`\
'ndaki Yeni kayıt defteri kökü.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Belirtilen kayıt defteri kökü genellikle ifade değerlendirici ilk kez başlatıldığında ayarlanır ve Visual Studio 'nun belirli bir sürümü (HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *X. y*) için kayıt defteri anahtarını işaret eder (burada *X. Y* bir sürüm numarasıdır).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
