---
title: Mesaj Kayıt Oyası | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e09b72bd228839268cffc228dd0dc503cc82bd9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702503"
---
# <a name="message-enumerator"></a>İleti kayıt otomu
IDE'nin `TEXTOUTPROC` [SccOpenProject'i](../extensibility/sccopenproject-function.md) aradığında sağladığı bir geri çağırma işlevi olan işlev için aşağıdaki bayraklar kullanılır (geri arama işleviyle ilgili ayrıntılar için [LPTEXTOUTPROC'a](../extensibility/lptextoutproc.md) bakın).

 IDE'den işlemi iptal etmesi istenirse, iptal iletilerinden birini alabilir. Bu durumda, kaynak denetimi eklentisi IDE'den `SCC_MSG_STARTCANCEL` **İptal** düğmesini görüntülemesini istemek için kullanır. Bundan sonra, normal iletiler herhangi bir dizi gönderilebilir. Bu döndürür `SCC_MSG_RTN_CANCEL`herhangi biri, sonra eklenti işlemi bırakır ve döndürür. Eklenti, kullanıcının `SCC_MSG_DOCANCEL` işlemi iptal edip etmediğini belirlemek için düzenli aralıklarla da anketler eler. Tüm işlemler bittiğinde veya kullanıcı iptal edilmişse, eklenti `SCC_MSG_STOPCANCEL`gönderir. Kaydırma `SCC_MSG_INFO`iletileri listesinde görüntülenen iletiler için SCC_MSG_WARNING ve SCC_MSG_ERROR türleri kullanılır. `SCC_MSG_STATUS`metnin durum çubuğunda veya geçici görüntü alanında gösterilmesi gerektiğini belirten özel bir türdür. Listede kalıcı olarak kalmaz.

## <a name="syntax"></a>Sözdizimi

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
 SCC_MSG_RTN_CANCEL İptal belirtmek için geri aramadan dönün.

 SCC_MSG_RTN_OK Geri aramadan devam etmek için geri dön.

 SCC_MSG_INFO İleti bilgilendirme amaçlıdır.

 SCC_MSG_WARNING İleti bir uyarıdır.

 SCC_MSG_ERROR İleti bir hatadır.

 SCC_MSG_STATUS İleti durum çubuğu içindir.

 SCC_MSG_DOCANCEL Metin yok; IDE `SCC_MSG_RTN_OK` döner `SCC_MSG_RTN_CANCEL`veya .

 SCC_MSG_STARTCANCEL İptal döngüsü başlatır.

 SCC_MSG_STOPCANCEL İptal döngüsüne engel olarak durur.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
