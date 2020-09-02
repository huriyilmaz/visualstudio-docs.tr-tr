---
title: İleti numaralandırıcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bd42c825cd45068e13178856e524268b426ec53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194334"
---
# <a name="message-enumerator"></a>İleti Numaralandırıcısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki bayraklar, `TEXTOUTPROC` IDE 'Nin [SccOpenProject](../extensibility/sccopenproject-function.md) çağırdığında sağladığı bir geri çağırma işlevi olan işlevi için kullanılır (geri çağırma işlevi hakkında ayrıntılar Için bkz. [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) ).  
  
 IDE 'nin işlemi iptal etmek isteniyorsa, iptal iletilerinden birini alabilir. Bu durumda, kaynak denetimi eklentisi `SCC_MSG_STARTCANCEL` IDE 'Nin **iptal** düğmesini görüntülemesini istemek için kullanır. Bundan sonra, herhangi bir normal ileti kümesi gönderilebilir. Bunlardan herhangi biri dönerse `SCC_MSG_RTN_CANCEL` , eklenti işlemden çıkar ve döndürür. Eklenti Ayrıca, `SCC_MSG_DOCANCEL` kullanıcının işlemi iptal etmiş olup olmadığını belirlemede düzenli aralıklarla yoklar. Tüm işlemler tamamlandığında veya Kullanıcı iptal edildiyse, eklenti gönderilir `SCC_MSG_STOPCANCEL` . `SCC_MSG_INFO`, SCC_MSG_WARNING ve SCC_MSG_ERROR türleri, iletilerin kaydırılan listesinde görüntülenen iletiler için kullanılır. `SCC_MSG_STATUS` , metnin bir durum çubuğunda veya geçici görüntüleme alanında gösterilmesi gerektiğini belirten özel bir türdür. Listede kalıcı olarak kalmaz.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>Üyeler  
 SCC_MSG_RTN_CANCEL  
 İptali göstermek için geri aramadan geri dönün.  
  
 SCC_MSG_RTN_OK  
 Geri aramadan devam etmek için geri dönün.  
  
 SCC_MSG_INFO  
 İleti bilgilendirme amaçlıdır.  
  
 SCC_MSG_WARNING  
 İleti bir uyarıdır.  
  
 SCC_MSG_ERROR  
 İleti bir hatadır.  
  
 SCC_MSG_STATUS  
 İleti, durum çubuğuna yöneliktir.  
  
 SCC_MSG_DOCANCEL  
 Metin yok; IDE, `SCC_MSG_RTN_OK` veya döndürür `SCC_MSG_RTN_CANCEL` .  
  
 SCC_MSG_STARTCANCEL  
 İptal döngüsü başlatır.  
  
 SCC_MSG_STOPCANCEL  
 İptal döngüsünü sonlandırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
