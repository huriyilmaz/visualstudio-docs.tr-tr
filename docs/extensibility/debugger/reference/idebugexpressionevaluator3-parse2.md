---
description: Bir ifade dizesini sembol sağlayıcısı ve değerlendirme çerçevesinin adresi verilen ayrıştırılmamış ifadeye dönüştürür.
title: IDebugExpressionEvaluator3::P arse2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39edfbcdec6f634307c61b3db4ac76b238ac3614
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152214"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
Bir ifade dizesini sembol sağlayıcısı ve değerlendirme çerçevesinin adresi verilen ayrıştırılmamış ifadeye dönüştürür.

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
'ndaki Ayrıştırılacak ifade dizesi.

`dwFlags`\
'ndaki İfadenin nasıl ayrıştırılaceğini tespit eden bir [Parseflags](../../../extensibility/debugger/reference/parseflags.md) sabitleri koleksiyonu.

`nRadix`\
'ndaki Sayısal bilgileri yorumlamak için kullanılacak taban tabanı.

`pSymbolProvider`\
'ndaki Sembol sağlayıcısının arabirimi.

`pAddress`\
'ndaki Değerlendirme çerçevesinin adresi.

`pbstrError`\
dışı Hatayı insanlarca okunabilir metin olarak döndürür.

`pichError`\
dışı İfade dizesinde hatanın başlangıcı olan karakter konumunu döndürür.

`ppParsedExpression`\
dışı Bir [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesinde ayrıştırılmış ifadeyi döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Bu yöntem, gerçek bir değer değil ayrıştırılmamış bir ifade oluşturur. Ayrıştırılmış bir ifade değerlendirilmeye, yani bir değere dönüştürülecek.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) arabirimini kullanıma sunan bir **Cee** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.

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
