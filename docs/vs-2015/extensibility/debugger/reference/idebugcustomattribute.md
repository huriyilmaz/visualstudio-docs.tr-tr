---
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5db7f060e630c0b4175ecf4708f14fc03869e431
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568944"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim özel bir özniteliği temsil eder ve özniteliğin adını, üst ve sınıf türünü sağlayabilir.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Sembol sağlayıcısı, bir sembol ile ilişkili özel öznitelikleri desteklemek için bu arabirimi uygular. Genellikle kendi nesnesine uygulanır.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bir [sonraki](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) çağrısı bu arabirimi döndürür. [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) yöntemine yapılan bir çağrı [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) arabirimini döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugCustomAttribute` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Geçerli özniteliğin eklendiği alanı alır.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Özel öznitelik sınıfı türünü alır.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Özel özniteliğin adını alır.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Öznitelik bilgilerini bayt blobu olarak alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Özel öznitelik, belirli bir sınıf veya yöntemle ilişkili özel meta verileri sağlayan bir C# yapısıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol sağlayıcısı arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
