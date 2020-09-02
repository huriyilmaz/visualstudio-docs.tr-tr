---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d2b036bd68aca126675f26b9823d2c786a0ae652
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675325"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) işleme iliştirmekte veya işlemden ayrıldığı bir işlemi bilgilendirmesini sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Özel bir bağlantı noktası sağlayıcısı, bu arabirimi şu şekilde [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabirimiyle aynı nesne üzerinde uygular:  
  
- Bir işleme bağlı oturumların izlenmesini destekleme  
  
- Birden çok hata ayıklama altyapısı genelinde otomatik iliştirme desteği  
  
  Özel bağlantı noktası sağlayıcısı, seçerse bu arabirimi uygulayabilir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
  
- SDM, [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugProcess2` Bu arabirimi almak Için bir arabirimdeki QueryInterface 'i çağırır.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProcessEx2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[İliştir](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|İşlemde bir oturumun hata ayıklaması olduğunu bildirir.|  
|[Ayır](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Bir oturumun işlemde artık hata ayıklalamadığını işleme bildirir.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Hata ayıklama altyapısının listesi için program düğümleri ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim, SDM ve işlem arasında özeldir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: Portprıv. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
