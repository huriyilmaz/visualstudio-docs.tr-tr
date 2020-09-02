---
title: 'VsgDbg:: VsgDbg (Oluşturucu) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157434"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Oluşturucu)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik `VsgDbg` Tanılama 'nın uygulama içi bileşenini, belirtilen Boolean parametresine göre varsayılan olarak yakalayıp, grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek için bir örneği ile veya kullanarak bir sınıfının örneğini oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bDefaultInit`  
 `true` Grafik tanılama 'nın uygulama içi bileşeninin grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek üzere hazırlanacağını belirtmek için; `false` uygulamanın Şu anda grafik bilgilerini etkin bir şekilde yakalayıp kaydetmek üzere hazırlanmamalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Oluşturucu `bDefaultInit` olarak ayarlandığı ile çağrıldığında `true` , grafik günlük dosyasının dosya adı, `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` uygulamanıza dahil etmeden önce ve Önişlemci simgelerinin nasıl tanımlanarak belirlenir `vsgcapture.h` .  
  
 Oluşturucu `bDefaultInit` olarak ayarlandığı ile çağrıldığında `false` , grafik tanılama 'nın uygulama içi bileşeni, daha sonra işlevi çağırarak grafik bilgilerini daha sonra yakalamak ve kaydetmek için hazır olabilir `Init` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VsgDbg:: ~ VsgDbg (yok edici)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Dengeleyici](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
