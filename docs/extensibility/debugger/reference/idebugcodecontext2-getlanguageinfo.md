---
description: Bu kod bağlamı için dil bilgisini alır.
title: 'IDebugCodeContext2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dccf0c34b6483ad85cc7bfd9cff7078cc20524f3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164129"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Bu kod bağlamı için dil bilgisini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

## <a name="parameters"></a>Parametreler
`pbstrLanguage`\
[in, out] "C++" gibi dilin adını içeren bir dize döndürür.

`pguidLanguage`\
[in, out] Kod bağlamı dilinin GUID 'sini döndürür; Örneğin, `guidCPPLang` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Parametrelerden en az birinin null olmayan bir değer döndürmesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
