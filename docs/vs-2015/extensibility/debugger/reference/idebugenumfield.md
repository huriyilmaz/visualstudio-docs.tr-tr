---
title: Ihata ayıklama Genumfield | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac993e3a4676f1c84a193ddbf6e9a3b5bc8fa235
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676512"
---
# <a name="idebugenumfield"></a>IDebugEnumField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim bir sabit listesi türünü temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bir sembol sağlayıcısı, bir numaralandırmayı temsil etmek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirimi, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürürse [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden elde etmek için [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) kullanın `FIELD_TYPE_ENUM` .  
  
## <a name="methods-in-vtable-order"></a>VTable sırasındaki Yöntemler  
 `IDebugField`Ve arayüzlerindeki yöntemlere ek olarak `IDebugContainerField` , bu arabirim aşağıdaki yöntemleri uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Bu numaralandırma türü için adı açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Verilen değerle ilişkili sabit listesi sabitinin adını döndürür.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Verilen sabit listesi sabit adıyla ilişkili değeri döndürür|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Verilen sabit listesi sabit adıyla ilişkili değeri döndürür, ancak büyük/küçük harf yok sayılıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aslında [bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)ile bir konuma bağlı olan temel simgedir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol sağlayıcısı arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Bağladığınızda](../../../extensibility/debugger/reference/idebugbinder-bind.md)
