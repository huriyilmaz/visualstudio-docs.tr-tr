---
title: Ayrıştırılmış kodu Listele komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ff5e620d4c53889afe17274364d6f92936025d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672736"
---
# <a name="list-disassembly-command"></a>Ayrıştırılmış Kodu Listele Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama işlemini başlatır ve hataların nasıl işleneceğini belirtmenizi sağlar.

## <a name="syntax"></a>Syntax

```
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
 Her anahtar, tamamı ya da kısa bir form kullanılarak çağrılabilir.

 /Count: `number` [veya]/c: `number` [veya]/length: `number` [veya]/L: `number` isteğe bağlı. Görüntülenecek yönerge sayısı. Varsayılan değer 8 ' dir.

 /endadddress: `expression` [veya]/e: `expression` isteğe bağlı. Ayrıştırılmış kodun durdurulacağı adres.

 /codebytes: `yes`&#124;`no` [veya]/bytes: `yes`&#124;`no` [veya]/b: `yes` `no` isteğe bağlı&#124;. Kod baytlarının görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `no` .

 /Source: `yes`&#124;`no` [veya]/s: `yes`&#124;`no` isteğe bağlı. Kaynak kodun görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `no` .

 /symbolnames: `yes`&#124;`no` [veya]/names: `yes`&#124;`no` [veya]/N: `yes`&#124;`no` isteğe bağlı. Sembol adlarının görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `yes` .

 [/linenumbers: `yes`&#124;`no` ] isteğe bağlı. Kaynak kodla ilişkili satır numaralarının görüntülenmesine izin vermez. /Linenumbers anahtarını kullanmak için/Source anahtarının bir değeri olmalıdır `yes` .

## <a name="example"></a>Örnek

```
>Debug.ListDisassembly
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Çağrı yığınını Listele komut](../../ide/reference/list-call-stack-command.md) [listesi iş parçacıkları komutu](../../ide/reference/list-threads-command.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
