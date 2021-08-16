---
description: Bu yöntem, bir alanın boyutunu bayt cinsinden alır.
title: 'IDebugField:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 705d597993c0d29ba66a9165c17c65c4ca475cc157c29252bafa27383f430798
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360332"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Bu yöntem, bir alanın boyutunu bayt cinsinden alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>Parametreler
`pdwSize`\
dışı Boyutunu döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Tüm alanlar bir türe sahiptir ve tüm türlerin boyutu vardır. Örneğin, bayt türünde bir alan 1 baytlık bir boyuta sahiptir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
