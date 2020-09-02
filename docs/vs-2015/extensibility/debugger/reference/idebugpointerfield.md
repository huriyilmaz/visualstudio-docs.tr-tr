---
title: Ihata ayıklama Gpoınterfield | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d92b1b4d6efda1b8f05c594368a05bd833c9f34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705820"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim bir işaretçi türünü temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Sembol sağlayıcısı bu arabirimi bir işaretçiyi temsil etmek için uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirimi, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürürse [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabiriminden elde etmek için [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) kullanın `FIELD_TYPE_POINTER` .  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 `IDebugField`Ve arayüzlerindeki yöntemlere ek olarak `IDebugContainerField` , bu arabirim aşağıdaki yöntemi uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|İşaretçinin hedefini açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 C/C++ ' da, bir işaretçi dizi gösterimi ile kullanılıyorsa bir kapsayıcı olabilir. Örneğin, verilen `char *pString` , `pString` için bir işaretçi türüne sahiptir `char` . `pString[3]` , `char` o kapsayıcının dördüncü öğesine başvuran bir işaretçi olan bir kapsayıcı türüne sahiptir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol sağlayıcısı arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
