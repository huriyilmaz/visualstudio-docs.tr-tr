---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cd6afb417de4d8a362916f91593d0d0e67d307c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156503"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim bir kaynak belgeyi temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] genellikle bu arabirimi uygular. Bir hata ayıklama altyapısı (DE), kaynak kodu sağlaması gerektiğinde ve kaynak diskte yoksa, bu arabirimi de uygulayabilir.  Bu gibi durumlarda de [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) ve [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) arabirimlerini ve [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) ve [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) arabirimlerinde bazı ek yöntemleri de uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 `IDebugDocumentContext2`,, `IDebugDisassemblyStream2` `IDebugDocumentPosition2` Ve `IDebugActivateDocumentEvent2` arabirimlerinde Yöntemler bu arabirimi döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugDocument2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Birçok formdan birindeki belgenin adını alır.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Belgenin sınıf tanımlayıcısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim yalnızca, kaynak kodu sağladığı zaman uygulanır. Örneğin, bir HTML sayfasında komut dosyasında hata ayıklaması yaparken, kaynak dinamik olarak indirilip oluşturulduğundan ve bir disk dosyası olarak bulunmadığından kaynak kodu sağlar. C++ gibi geleneksel dillerde hata ayıklarken bu arabirimin uygulanması gerekmez.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ispositionındocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
