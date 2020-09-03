---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 577b2691ed67751407621d5000ee9a8abec318df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192013"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, kod yollarının bir listesini temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE), bu arabirimi kod yollarının listesini temsil etmek için uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirimi edinmek için [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) çağrısı yapın.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumCodePaths2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Sonraki](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Sabit Listesi dizisinde belirtilen sayıda kod yolunu alır.|  
|[Atla](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda kod yolunu atlar.|  
|[Sıfırla](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|  
|[Kopyalama](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Bir Numaralandırıcı içindeki kod yollarının sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir kod yolu, bir programdaki bir dal noktasını veya işlev çağrısını temsil eder. Kod yollarının listesi, kod yürütmenin alındığı yolu temsil eder.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
