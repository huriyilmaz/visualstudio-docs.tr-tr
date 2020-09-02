---
title: 'IDebugComPlusSymbolProvider:: UpdateSymbols | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UpdateSymbols
- IDebugComPlusSymbolProvider::UpdateSymbols
ms.assetid: d530f6f1-4af2-454b-bab0-02478a8fe81e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b208cadc8264bf3ddbd30d9316b9f0d5a7050b50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176754"
---
# <a name="idebugcomplussymbolproviderupdatesymbols"></a>IDebugComPlusSymbolProvider::UpdateSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bellekteki hata ayıklama sembollerini, belirtilen veri akışından gelen verilerle güncelleştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT UpdateSymbols (  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   IStream* pUpdateStream  
);  
```  
  
```csharp  
int UpdateSymbols (  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   IStream pUpdateStream  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ulAppDomainID`  
 'ndaki Uygulama etki alanının tanımlayıcısı.  
  
 `guidModule`  
 'ndaki Modülün benzersiz tanıtıcısı.  
  
 `pUpdateStream`  
 'ndaki Güncelleştirilmiş hata ayıklama sembollerini içeren veri akışı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) arabirimini kullanıma sunan bir **CDebugSymbolProvider** nesnesi için bu yöntemin nasıl uygulanacağını gösterir.  
  
```cpp#  
HRESULT CDebugSymbolProvider::UpdateSymbols(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IStream* pUpdateStream  
)  
{  
    ASSERT(!"Use UpdateSymbols2 on IDebugENCSymbolProvider2");  
    return E_NOTIMPL;  
}  
  
HRESULT CDebugSymbolProvider::UpdateSymbols2(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IStream* pUpdateStream,  
    LINEDELTA* pDeltaLines,  
    ULONG cDeltaLines  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::UpdateSymbols );  
  
    IfFailGo( GetModule( idModule, &pModule ) );  
    IfFailGo( pModule->UpdateSymbols( pUpdateStream, pDeltaLines, cDeltaLines ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::UpdateSymbols, hr );  
  
    return hr;  
}  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
