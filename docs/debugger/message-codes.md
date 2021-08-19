---
title: İleti kodları | Microsoft Docs
description: Mesaj Iletilerinin her ileti satırında gösterilen ileti kodlarının anlamlarını öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146842"
---
# <a name="message-codes"></a>İleti Kodları
[Iletiler görünümünde](../debugger/messages-view.md) gösterilen her ileti satırı bir ' P, ', ' 's ' veya ' R ' kodu içerir. Bu kodlar aşağıdaki anlamlara sahiptir:

|Kod|Anlamı|
|----------|-------------|
|P|İleti, **PostMessage** işleviyle kuyruğa gönderildi. İletinin son değerlendirmesi ile ilgili bilgi yok.|
|S|İleti, **SendMessage** işleviyle gönderilmiştir. Bu, alıcı iletiyi işleyerek ve döndürünceye kadar gönderenin denetimi geri kazanmayacağı anlamına gelir. Bu nedenle alıcı, gönderene geri dönüş değeri geçirebilir.|
|s|İleti gönderildi, ancak güvenlik dönüş değerine erişimi engelliyor.|
|R|Her birinin ' satırı, ileti dönüş değerini listeleyen karşılık gelen bir ' R ' (Return) satırına sahiptir. Bazen ileti çağrıları iç içe gelir, yani bir ileti işleyicisi başka bir ileti gönderir.|