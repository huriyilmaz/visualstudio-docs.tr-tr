---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95d001c0072442d07ae12f773a26290a95a2f7f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178467"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bekleyen bir kesme noktasıyla ilişkili hata kesme noktalarını numaralandırır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE), bu arabirimi kesme noktaları desteğinin bir parçası olarak uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Visual Studio, bağlanmayan kesme noktaları listesini temsil eden bu arabirimi almak için [Canbind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) çağırır veya bağlanmamış kesme noktaları listesini temsil eden bu arabirimi elde etmek Için [enumerrorkesmenoktaları](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) .  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IEnumDebugErrorBreakpoints2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Sonraki](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Bir numaralandırma dizisinde belirtilen sayıda hata kesme noktası alır.|  
|[Atla](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Sabit Listesi dizisinde belirtilen sayıda hata kesme noktası atlar.|  
|[Sıfırla](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|  
|[Kopyalama](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Bir Numaralandırıcı içindeki hata kesme noktası sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, her biri, bağlanamamayan ve neden bağlanamadığına ilişkin bir kesme noktası tanımlayan [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) arabirimlerinin bir listesini tutar. Visual Studio, `IEnumDebugErrorBreakpoint2` IDE 'de gösterilen kesme noktalarını güncelleştirmek için arabirimini kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [Enumerrorkesmenoktaları](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
