---
title: İleti kodları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92cc911b0217a406302553b3d913c032fc915b4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182957"
---
# <a name="message-codes"></a>İleti Kodları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Iletiler görünümünde](../debugger/messages-view.md) gösterilen her ileti satırı bir ' P, ', ' 's ' veya ' R ' kodu içerir. Bu kodlar aşağıdaki anlamlara sahiptir:  
  
|Kod|Anlamı|  
|----------|-------------|  
|P|İleti, **PostMessage** işleviyle kuyruğa gönderildi. İletinin son değerlendirmesi ile ilgili bilgi yok.|  
|S|İleti, **SendMessage** işleviyle gönderilmiştir. Bu, alıcı iletiyi işleyerek ve döndürünceye kadar gönderenin denetimi geri kazanmayacağı anlamına gelir. Bu nedenle alıcı, gönderene geri dönüş değeri geçirebilir.|  
|s|İleti gönderildi, ancak güvenlik dönüş değerine erişimi engelliyor.|  
|R|Her birinin ' satırı, ileti dönüş değerini listeleyen karşılık gelen bir ' R ' (Return) satırına sahiptir. Bazen ileti çağrıları iç içe gelir, yani bir ileti işleyicisi başka bir ileti gönderir.|
