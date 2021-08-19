---
description: 'IDebugProgram2:: GetName programın adını alır.'
title: 'IDebugProgram2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetName
helpviewer_keywords:
- IDebugProgram2::GetName
ms.assetid: a54cbf13-b3e3-4c9f-8b8d-13573232dfb0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 98af9a3634c540bb6d60f689964678fda8190c34
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159756"
---
# <a name="idebugprogram2getname"></a>IDebugProgram2::GetName
Programın adını alır.

## <a name="syntax"></a>Sözdizimi

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
dışı Programın adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin döndürdüğü ad, programı açıklayan, her zaman kolay, Kullanıcı tarafından görüntülenebilen bir addır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
