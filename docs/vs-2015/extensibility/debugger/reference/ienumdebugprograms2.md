---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d9d1030616fa8d7f3a1bfc6b533c4ed8433ea89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703899"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, geçerli hata ayıklama oturumunda çalışan programları numaralandırır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE), bu arabirimi, ' DE hata ayıklamakta olan programların bir listesini sağlamak için uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Visual Studio bu arabirimi edinmek için [Enumprograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 'ı çağırır. [Enumprograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) , Visual Studio tarafından kullanılmaz.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugPrograms2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Bir numaralandırma dizisindeki belirtilen sayıda programı alır.|  
|[Atla](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Bir numaralandırma dizisinde belirtilen sayıda programı atlar.|  
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|  
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Bir Numaralandırıcı içindeki program sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Studio bu arabirimi şu amaçlarla kullanır:  
  
- **Modüller** penceresini doldurun ( [enumprograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) çağırarak ve ardından her programda [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) çağırarak).  
  
- **Işleme İliştir** listesini doldurun ( `IDebugProcess2::EnumPrograms` bir [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) arabirimi edinmek için her [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabiriminde [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 'i çağırarak ve sonra çağırarak).  
  
- İşlemdeki her programda hata ayıklayabilmesi gereken DEs listesini oluşturun ( [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)kullanarak).  
  
- Her programa Düzenle ve devam et (ENC) güncelleştirmelerini Uygula (IDebugProcess2:: EnumPrograms çağırarak ve sonra [Getencupdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)'i çağırarak).  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
