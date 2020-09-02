---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca0b6b7e9753b346b8a995ffd8ddcb6cc53fe7c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697523"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bir bağlantı noktasının sunucusuna ve bildirim tesislerini erişmek için çeşitli yöntemler sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Visual Studio, programlara erişmek için hata ayıklama bağlantı noktasını göstermek üzere bu arabirimi uygular. Özel bir bağlantı noktası sağlayıcısı, uzaktan hata ayıklamayı işlediğinde da bu arabirimi uygulayabilir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) arabirimindeki yöntemlere bir bağımsız değişken bu arabirimi sağlar. [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabiriminde [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) çağrısı, bu arabirimi de edinebilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Bu arabirim, [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)içinde tanımlanan yöntemlere ek olarak aşağıdaki yöntemleri uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Bu bağlantı noktasından bağlantı noktası bildirim arabirimini alır.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Bu bağlantı noktasını barındıran sunucunun arabirimini alır.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bu bağlantı noktasının yerel makinede çalışıp çalışmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 "" Adı `IDebugDefaultPort2` , varsayılan bir bağlantı noktasını temsil etmediği için bir hatalı Nomer 'nin bir bitidir. "IDebugPort3" olarak adlandırılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
