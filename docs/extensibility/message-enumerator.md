---
title: İleti Numaralayıcı | Microsoft Docs
description: Bu numaralayıcının üyeleri, IDE'nin SccOpenProject çağrısında sağladığı bir geri çağırma işlevi olan TEXTOUTPROC işlevi için kullanılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2ade39f1c90e3201d19975bd671674c8a2d113f0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122110247"
---
# <a name="message-enumerator"></a>İleti numaralayıcı
Aşağıdaki bayraklar, IDE'nin SccOpenProject çağrısında sağladığı bir geri çağırma işlevi olan işlev için kullanılır (geri çağırma işleviyle ilgili ayrıntılar için `TEXTOUTPROC` [bkz. LPTEXTOUTPROC).](../extensibility/lptextoutproc.md) [](../extensibility/sccopenproject-function.md)

 IDE'nin işlemi iptal etmesi istense, iptal iletilerinden birini alabilirsiniz. Bu durumda, kaynak denetimi eklentisi `SCC_MSG_STARTCANCEL` IDE'den İptal düğmesini görüntülemesini istemek **için kullanır.** Bundan sonra, herhangi bir normal ileti kümesi gönderebilirsiniz. Bu değerlerden herhangi biri `SCC_MSG_RTN_CANCEL` döndürürse eklenti işlemi bırakır ve döndürür. Eklenti ayrıca kullanıcının işlemi iptal `SCC_MSG_DOCANCEL` edip etmey olmadığını belirlemek için düzenli aralıklarla yoklar. Tüm işlemler tamam olduğunda veya kullanıcı iptal etti ise eklenti `SCC_MSG_STOPCANCEL` gönderir. , SCC_MSG_WARNING ve SCC_MSG_ERROR türleri, ileti kaydırma listesinde görüntülenen `SCC_MSG_INFO` iletiler için kullanılır. `SCC_MSG_STATUS` , metnin bir durum çubuğunda veya geçici görüntüleme alanında göster gerektiğini belirten özel bir tür. Listede kalıcı olarak kalmaz.

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
 SCC_MSG_RTN_CANCEL geri çağırmadan geri dön'e çağrıyı seçin.

 SCC_MSG_RTN_OK geri çağırmadan geri dön'e geri dön.

 SCC_MSG_INFO İleti bilgilendirmedir.

 SCC_MSG_WARNING İleti bir uyarıdır.

 SCC_MSG_ERROR İleti bir hatadır.

 SCC_MSG_STATUS İleti durum çubuğu için hazır.

 SCC_MSG_DOCANCEL metin yok; IDE veya `SCC_MSG_RTN_OK` `SCC_MSG_RTN_CANCEL` döndürür.

 SCC_MSG_STARTCANCEL bir iptal döngüsü başlatır.

 SCC_MSG_STOPCANCEL döngüyü durdurur.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
