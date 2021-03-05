---
description: Birçok formdan birindeki belgenin adını alır.
title: 'IDebugDocument2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1b68fb60cb13d88941b21f6625e6cc0e38ceeda4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166547"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Birçok formdan birindeki belgenin adını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>Parametreler
`gnType`\
'ndaki [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) Numaralandırmadaki, döndürülecek ad türünü belirleyen bir değer.

`pbstrFileName`\
dışı Belge adını içeren bir dize döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem Örneğin, belgenin adını bir başlık veya dosya adı olarak ya da dosya adının bir parçası olarak döndürebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
