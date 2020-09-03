---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e3c9a43b6903522fe2caf0e329f8e8faa69cd6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161087"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan bir nesne koleksiyonunu temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu arabirim, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimini uygulayan nesne kümeleri sağlamak için sembol sağlayıcısı tarafından uygulanır. [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) yönteminin varlığı nedeniyle bu standart bir com numaralandırması olmadığını unutmayın.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim [Getmethodalanları byname](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) ve [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)tarafından döndürülür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Bu arabirim aşağıdaki yöntemleri uygular.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Numaralandırmadaki [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnelerinin bir sonraki kümesini alır.|  
|[Atla](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Belirtilen sayıda girişi atlar.|  
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Numaralandırmayı ilk girdiye sıfırlar.|  
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Geçerli numaralandırmanın bir kopyasını alır.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Numaralandırmadaki giriş sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol sağlayıcısı arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Getmethodalanalanları byname](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
