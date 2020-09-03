---
title: 'Idebugexpressiondeğerlendirici:: GetMethodProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b84ac959241a8f68f4d9516879660b6414708731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155358"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, bir yöntemin Yereller, bağımsız değişkenleri ve diğer özelliklerini içeren bir özellik nesnesi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pSymbolProvider`  
 'ndaki Kullanılacak sembol sağlayıcısı bir [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) nesnesi olarak ifade edilir.  
  
 `pAddress`  
 'ndaki Koddaki, en yakın içeren işleve çözülmesi gereken bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesnesi olarak ifade edilen adres.  
  
 `pBinder`  
 'ndaki [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi olarak ifade edilen kullanılacak bağlayıcı.  
  
 `fIncludeHiddenLocals`  
 'ndaki Sıfır dışında ( `TRUE` ) gizli Yereller dahil edilecek anlamına gelir; sıfır ( `FALSE` ) gizli Yereller dışında tutulacak anlamına gelir  
  
 `ppProperty`  
 dışı Yöntemi temsil eden bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Gizli Yereller genellikle derleyici tarafından oluşturulan değişkenlerdir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idebugexpressiondeğerlendirici](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
