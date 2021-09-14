---
title: İleti Kodları | Microsoft Docs
description: İletiler Görünümü'nin her ileti satırına gösterilen ileti kodlarının anlamını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ce6fe678785719ed52e9be59e28d7eedd98ebef6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725407"
---
# <a name="message-codes"></a>İleti Kodları
İletiler Görünümünde gösterilen [her ileti satırı](../debugger/messages-view.md) bir 'P,' 'S,' 's' veya 'R' kodu içerir. Bu kodlar aşağıdaki anlamlara sahiptir:

|Kod|Anlamı|
|----------|-------------|
|P|İleti, PostMessage işleviyle **kuyruğa gönderildi.** İletinin son değerlendirmesinde hiçbir bilgi yoktur.|
|S|İleti **SendMessage işleviyle gönderildi.** Bu, alıcı iletiyi işleyene ve döndürene kadar gönderenin denetimi yeniden elde etmey olduğu anlamına gelir. Bu nedenle alıcı, gönderene geri bir dönüş değeri iletir.|
|s|İleti gönderildi, ancak güvenlik dönüş değerine erişimi engelledi.|
|R|Her 'S' satırı, ileti dönüş değerini listeleye karşılık gelen bir 'R' (dönüş) satırına sahip olur. Bazen ileti çağrıları iç içe geçmiş olur, bu da bir ileti işleyicinin başka bir ileti gönderdiği anlamına gelir.|