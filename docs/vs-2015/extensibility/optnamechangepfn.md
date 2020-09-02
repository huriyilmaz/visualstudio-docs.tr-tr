---
title: SEÇENEKADı < PFN | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4969dff811b6517c0274a35884703a9dc0c693cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194100"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu, [SccSetOption](../extensibility/sccsetoption-function.md) (kullanma seçeneği) çağrısında belirtilen bir geri çağırma işlevidir `SCC_OPT_NAMECHANGEPFN` ve kaynak denetimi eklentisi tarafından YAPıLAN ad değişikliklerini IDE 'ye geri bildirmek için kullanılır.  
  
## <a name="signature"></a>İmza  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 pvCallerData  
 'ndaki Daha önceki bir [SccSetOption](../extensibility/sccsetoption-function.md) çağrısında belirtilen kullanıcı değeri (using seçeneği `SCC_OPT_USERDATA` ).  
  
 pszOldName  
 'ndaki Dosyanın özgün adı.  
  
 Pszyeniad  
 'ndaki Dosyanın yeniden adlandırıldığını adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yok.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak denetim işlemi sırasında bir dosya yeniden adlandırılırsa, kaynak denetimi eklentisi bu geri çağırma yoluyla ad değişikliğine ilişkin IDE 'ye bildirimde bulunabilir.  
  
 IDE bu geri çağırma işlemini desteklemiyorsa, belirtmek için [SccSetOption](../extensibility/sccsetoption-function.md) çağrısı yapmaz. Eklenti bu geri çağırma işlemini desteklemiyorsa, `SCC_E_OPNOTSUPPORTED` `SccSetOption` IDE geri aramayı ayarlamaya çalıştığında işlevinden geri döner.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDE tarafından uygulanan geri çağırma Işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
