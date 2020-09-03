---
title: IDebugDocumentContext2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6d040597f48d4514a58027df3335c080d6305a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144951"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, kaynak dosya belgesindeki bir konumu temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE), bu arabirimi kaynak kodu düzeyinde hata ayıklama desteğinin bir parçası olarak uygular. Bu arabirim, kaynak kodundaki bir konuma ek olarak, bağlamların karşılaştırılması ve bir kaynak kod belgesinde gezinmek için yöntemler sağlar.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Birçok arabirimde Yöntemler, genellikle [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) ve [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) arabirimleri, bu arabirimi döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugDocumentContext2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Bu belge bağlamını içeren belgeyi alır.|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Bu belge bağlamını içeren belgenin görüntülenebilen adını alır.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Bu belge içeriğiyle ilişkili tüm kod bağlamlarının bir listesini alır.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Bu belge içeriğiyle ilişkili dili alır.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Bu belge bağlamının dosya deyimleri aralığını alır.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Bu belge bağlamının dosya kaynak aralığını alır.|  
|[Karşılaştır](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Bu belge bağlamını, belirli bir belge bağlamı dizisiyle karşılaştırır.|  
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Belge bağlamını verilen sayıda deyim veya satır olarak kaydırır.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
