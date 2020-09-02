---
title: 'IDebugParsedExpression:: EvaluateSync | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6761cd5ec9df67d511ab905e173ac0f286c5ee7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194547"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem ayrıştırılmış ifadeyi değerlendirir ve isteğe bağlı olarak sonucu başka bir veri türüne yayınlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwEvalFlags`  
 'ndaki İfadenin nasıl değerlendirileceğini denetleyen [Evalflags](../../../extensibility/debugger/reference/evalflags.md) sabitlerinin bir birleşimi.  
  
 `dwTimeout`  
 'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süreyi milisaniye olarak belirtir. `INFINITE`Sonsuza kadar beklemek için kullanın.  
  
 `pSymbolProvider`  
 'ndaki Bir [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimi olarak ifade edilen sembol sağlayıcısı.  
  
 `pAddress`  
 'ndaki Bir yöntem içinde bir [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) arabirimi olarak ifade edilen geçerli yürütme konumu.  
  
 `pBinder`  
 'ndaki [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) arabirimi olarak ifade edilen cilt.  
  
 `bstrResultType`  
 'ndaki Sonucun türüne dönüştürülmesi gereken tür. Bu bağımsız değişken null bir değer olabilir.  
  
 `ppResult`  
 dışı Değerlendirmenin sonuçlarını temsil eden [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 İfade değerlendirme bağlamı tarafından verilir; Bu, `pAddress` kapsayan yöntemi belirlemeyi ve sonra, ifadedeki simgelerin değerini belirlemek için dil kapsamı kurallarını kullanmayı mümkün kılar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
