---
title: IDebugMethodField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d7f6fc12a3366200ca1e14c0e2d55f4f6d797f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694344"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim bir yöntemi açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bir sembol sağlayıcısı, bu arabirimi [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimini uygulayan aynı nesne üzerinde uygular. Bu arabirim, bir yöntemi sunan bir özelleşmenin bir özelleştirmesi.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirimi, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) döndürürse [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabiriminden elde etmek için [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) kullanın `FIELD_TYPE_METHOD` . Ayrıca, Yöntemler, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)ve [enumoluşturucular](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), All `IDebugMethodField` arabirimini döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ve [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) arabirimlerindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Metodun parametreleri için bir Numaralandırıcı oluşturur.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Yöntemi içeren nesnenin "This" işaretçisini alır.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Metodun tüm yerel değişkenleri için bir Numaralandırıcı oluşturur.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Metodun seçili yerel değişkenleri için bir Numaralandırıcı oluşturur.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Belirli bir özel özniteliğin tanımlanıp tanımlanmadığını belirler.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Metodun statik yerel değişkenleri için bir Numaralandırıcı oluşturur.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Metodun genel kapsayıcısını alır.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Yöntemi çağırmak için gereken her bir bağımsız değişkenin türü için bir Numaralandırıcı oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yöntem, parametreleri ve yerel değişkenleri içerebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol sağlayıcısı arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
