---
description: Bir ifade dizesini, sembol sağlayıcısı ve değerlendirme çerçevesinin adresine göre ayrıştırıldı bir ifadeye dönüştürür.
title: IDebugExpressionEvaluator3::P arse2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a10db1315249a78ebbc786dec3e54da92532ba7262294490c76c145c9a11fc6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360397"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
Bir ifade dizesini, sembol sağlayıcısı ve değerlendirme çerçevesinin adresine göre ayrıştırıldı bir ifadeye dönüştürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Parse2 (
    LPCOLESTR                upstrExpression,
    PARSEFLAGS               dwFlags,
    UINT                     nRadix,
    IDebugSymbolProvider*    pSymbolProvider,
    IDebugAddress*           pAddress,
    BSTR*                    pbstrError,
    UINT*                    pichError,
    IDebugParsedExpression** ppParsedExpression
);
```

```csharp
HRESULT Parse2 (
    string                     upstrExpression,
    enum_PARSEFLAGS            dwFlags,
    uint                       nRadix,
    IDebugSymbolProvider       pSymbolProvider,
    IDebugAddress              pAddress,
    out string                 pbstrError,
    out uint                   pichError,
    out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parametreler
`upstrExpression`\
[in] Ayrıştırıla ifade dizesi.

`dwFlags`\
[in] İfadenin nasıl ayrıştır olacağını belirleyen [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) sabitleri koleksiyonu.

`nRadix`\
[in] Tüm sayısal bilgileri yorumlamak için kullanılacak radix.

`pSymbolProvider`\
[in] Sembol sağlayıcısının arabirimi.

`pAddress`\
[in] Değerlendirme çerçevesinin adresi.

`pbstrError`\
[out] Hatayı insan tarafından okunabilir metin olarak döndürür.

`pichError`\
[out] İfade dizesinde hatanın başlangıcının karakter konumunu döndürür.

`ppParsedExpression`\
[out] [IDebugParsedExpression nesnesinde ayrıştırılmış ifadeyi](../../../extensibility/debugger/reference/idebugparsedexpression.md) döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu yöntem gerçek bir değer değil ayrıştıran bir ifade üretir. Ayrıştırıldı ifadesi değerlendirilmeye, yani bir değere dönüştürül etmeye hazırdır.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) arabirimini ortaya çıkaran bir **CEE** nesnesi için bu yöntemin nasıl uygulandığını gösterir.

```cpp
HRESULT CEE::Parse2 ( LPCOLESTR in_szExprText,
  PARSEFLAGS in_FLAGS,
  UINT in_RADIX,
  IDebugSymbolProvider *pSymbolProvider,
  IDebugAddress *pAddress,
  BSTR* out_pbstrError,
  UINT* inout_pichError,
  IDebugParsedExpression** out_ppParsedExpression )
{
    // precondition
    REQUIRE( NULL != in_szExprText );
    //REQUIRE( NULL != out_pbstrError );
    REQUIRE( NULL != inout_pichError );
    REQUIRE( NULL != out_ppParsedExpression );

    if (NULL == in_szExprText)
        return E_INVALIDARG;

    if (NULL == inout_pichError)
        return E_POINTER;

    if (NULL == out_ppParsedExpression)
        return E_POINTER;

    if (out_pbstrError)
        *out_pbstrError = NULL;

    *out_ppParsedExpression = NULL;

    INVARIANT( this );

    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    // function body
    EEDomain::fParseExpression DomainVal =
    {
        this,                   // CEE*
        in_szExprText,          // LPCOLESTR
        in_FLAGS,               // EVALFLAGS
        in_RADIX,               // RADIX
        out_pbstrError,         // BSTR*
        inout_pichError,        // UINT*
        pSymbolProvider,
        out_ppParsedExpression  // Output
    };

    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)
