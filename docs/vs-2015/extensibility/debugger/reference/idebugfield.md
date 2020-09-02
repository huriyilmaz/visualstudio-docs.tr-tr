---
title: IDebugField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8bc18204d3cbe20635ab0680a50b4d1555dce2ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690299"
---
# <a name="idebugfield"></a>IDebugField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim bir alanı, diğer bir deyişle, bir simgenin veya türün açıklamasını temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bir sembol sağlayıcısı, bu arabirimi tüm alanları için temel sınıf olarak uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim, tüm alanlar için temel sınıftır. Bu arabirim, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md)'nin dönüş değerine bağlı olarak, [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)kullanarak daha özelleştirilmiş arabirimler döndürebilir. Ayrıca, birçok arabirim `IDebugField` çeşitli metotlardan nesne döndürür.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugField` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Sembol veya tür hakkında görüntülenebilen bilgileri alır.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Alan türünü alır.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Alan türünü alır.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Alanın kapsayıcısını alır.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Alanın adresini alır.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Bir alanın boyutunu bayt cinsinden alır.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Bir alanla ilgili genişletilmiş bilgileri alır.|  
|[Eşittir](../../../extensibility/debugger/reference/idebugfield-equal.md)|İki alanı karşılaştırır.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Sembol veya tür hakkındaki tür bağımsız bilgileri alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir tür C diline eşdeğerdir `typedef` .  
  
 Aşağıdaki C++ dili örneğinde, `weather` bir sınıf türüdür ve `sunny` `stormy` simgeler şunlardır:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Bir alanın bir simgeyi veya türü temsil edip etmediği, [Getkinleştirilen d](../../../extensibility/debugger/reference/idebugfield-getkind.md) çağırarak ve [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) sonucunu inceleyerek belirlenebilir. `FIELD_KIND_TYPE`Bit ayarlandıysa, alan bir türdür ve `FIELD_KIND_SYMBOL` bit ayarlandıysa, bir simgedir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol Sağlayıcısı Arabirimleri](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
