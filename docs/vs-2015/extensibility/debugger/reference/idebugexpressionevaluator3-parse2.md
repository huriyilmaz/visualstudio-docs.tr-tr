---
title: IDebugExpressionEvaluator3::P arse2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c8629fb996dd020882ce81ae9975ccd799d863c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148976"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir ifade dizesini sembol sağlayıcısı ve değerlendirme çerçevesinin adresi verilen ayrıştırılmamış ifadeye dönüştürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametreler  
 `upstrExpression`  
 'ndaki Ayrıştırılacak ifade dizesi.  
  
 `dwFlags`  
 'ndaki İfadenin nasıl ayrıştırılaceğini tespit eden bir [Parseflags](../../../extensibility/debugger/reference/parseflags.md) sabitleri koleksiyonu.  
  
 `nRadix`  
 'ndaki Sayısal bilgileri yorumlamak için kullanılacak taban tabanı.  
  
 `pSymbolProvider`  
 'ndaki Sembol sağlayıcısının arabirimi.  
  
 `pAddress`  
 'ndaki Değerlendirme çerçevesinin adresi.  
  
 `pbstrError`  
 dışı Hatayı insanlarca okunabilir metin olarak döndürür.  
  
 `pichError`  
 dışı İfade dizesinde hatanın başlangıcı olan karakter konumunu döndürür.  
  
 `ppParsedExpression`  
 dışı Bir [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) nesnesinde ayrıştırılmış ifadeyi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, gerçek bir değer değil ayrıştırılmamış bir ifade oluşturur. Ayrıştırılmış bir ifade değerlendirilmeye, yani bir değere dönüştürülecek.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) arabirimini kullanıma sunan bir **Cee** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.  
  
```cpp#  
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
        out_pbstrError      ,   // BSTR*  
        inout_pichError,        // UINT*  
        pSymbolProvider,  
        out_ppParsedExpression  // Output  
    };  
  
    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)
