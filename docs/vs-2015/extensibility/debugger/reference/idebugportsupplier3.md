---
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ece720cf6880bba528dee99cdbdeb25c10087a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674128"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bir arayanın bir bağlantı noktası üreticisinin, hata ayıklayıcının etkinleştirmeleri arasında bağlantı noktalarını (diske yazarak) koruyup koruyamayacağını belirlemesine izin verir ve ardından bu korunan bağlantı noktalarının bir listesini alın.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Özel bir bağlantı noktası sağlayıcısı, bu arabirimi kalıcı veya bağlantı noktası bilgilerinin diske kaydedilmesini desteklemek için uygular. Bu arabirimin [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) arabirimiyle aynı nesne üzerinde uygulanması gerekir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugPortSupplier2` Bu arabirimi edinmek için arabirimdeki QueryInterface 'i çağırın.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) arabiriminden devralınan yöntemlere ek olarak, bu arabirim aşağıdakileri destekler:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Bağlantı noktası üreticisinin, hata ayıklayıcının etkinleştirmeleri arasında bağlantı noktalarını (diske yazarak) kalıcı yapıp yapamayacağını döndürür.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Bu bağlantı noktası sağlayıcısı tarafından diske yazılan tüm bağlantı noktalarını numaralandırmak için kullanılabilecek bir nesne döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir bağlantı noktası tedarikçide bağlantı noktalarını etkinleştirmeleri arasında kalıcı hale getirebiliyorsanız, bu arabirimi uygulamalıdır. Bağlantı noktası sağlayıcısı örneği oluşturulduğunda bağlantı noktaları yüklenmelidir ve bağlantı noktası sağlayıcısı yok edildiğinde diske yazılır.  
  
 Bir hata ayıklama altyapısı genellikle bir bağlantı noktası sağlayıcısıyla etkileşime girmiyor ve bu arabirim için hiçbir kullanımı olmayacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
