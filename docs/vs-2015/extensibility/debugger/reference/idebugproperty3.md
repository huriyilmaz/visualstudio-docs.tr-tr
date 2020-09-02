---
title: IDebugProperty3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 479827cc83486d6bb9c68d0749b8870cd6c41861
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694757"
---
# <a name="idebugproperty3"></a>IDebugProperty3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim için destek sağlar:  
  
- Özelliği ile ilişkili rastgele bir uzun dize alma.  
  
- Benzersiz bir KIMLIĞI özelliği ile ilişkilendirme.  
  
- Özelliği için özel görüntüleyicilerin bir listesi alınıyor.  
  
- Bir özelliğin değerini, ortaya çıkan hataları bildirme özelliğiyle ayarlama  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE), uzun dizeler, özellik kimlikleri ve özel görüntüleyiciler için destek sağlamak üzere [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) uygulayan aynı nesne üzerinde bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugProperty2` Bu arabirimi edinmek Için arabirim üzerinde QueryInterface 'i çağırın.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Kaynağından devralınan yöntemlere ek olarak `IDebugProperty2` , `IDebugProperty3` arabirimi aşağıdaki yöntemleri sunar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Özelliği ile ilişkili dizenin uzunluğunu döndürür.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Kullanıcı tarafından sağlanan arabellekteki dizeyi döndürür.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Bu özellik için benzersiz bir KIMLIK oluşturur.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Bu özellik için benzersiz KIMLIĞI yok eder.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Bu özelliğin görüntülenebilmesini sağlayan özel görüntüleyicilerin sayısını döndürür.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Bu özelliğin görüntülenebilmesini sağlayan özel görüntüleyicilerin listesini döndürür.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Bu özelliğin değerini ayarlar, bir sorun varsa hata iletisi döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) , oturum hata ayıklama Yöneticisi 'nın (SDM) bir özelliğin değerini ayarlaması için tercih edilen yoldur.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
