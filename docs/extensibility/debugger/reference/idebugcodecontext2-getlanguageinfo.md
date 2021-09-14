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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1f3c2ac4eb0a41e94415ab83605f978e691311d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627446"
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
