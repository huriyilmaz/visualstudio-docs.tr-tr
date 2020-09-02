---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2656d3f5a3313a4538e3e0e6454dd671da635904
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686981"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, diğer semboller veya türler için kapsayıcı olan bir simgeyi veya türü temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bir sembol sağlayıcısı, bu arabirimi [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan aynı nesne üzerinde uygular. Bu arabirim Ayrıca kapsayıcıları temsil eden tüm arabirimler için temel sınıftır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Birçok arabirimde birçok yöntem bu arabirimi döndürür. Bu, tüm kapsayıcılar için bir temel sınıf olduğundan, bu arabirimden [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)kullanarak daha özelleştirilmiş arabirimler elde edilebilir. Bu tür arabirimler [ıdebuggarrayfield](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)ve [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)içerir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Bu arabirim, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimindeki yöntemlere ek olarak aşağıdaki yöntemi uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Kapsayıcının alanları için bir Numaralandırıcı oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Diziler (değişkenler için kapsayıcılar), sınıflar (yöntemlere ve değişkenlere yönelik kapsayıcılar) ve yöntemleri (parametreler ve yerel değişkenler için kapsayıcılar), kapsayıcılara örnektir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol sağlayıcısı arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
