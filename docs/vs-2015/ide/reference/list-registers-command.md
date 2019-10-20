---
title: Yazmaçları Listele komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3476244d3044eb80dbfce3559479421b012cc5fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659508"
---
# <a name="list-registers-command"></a>Yazmaçları Listele Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Seçili yazmaçların değerini görüntüler ve gösterilecek kayıt listesini değiştirmenize izin verir.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Anahtarlar
 /Display [{`register`&#124; `registerGroup`}...] Belirtilen `register` veya `registerGroup` değerlerini görüntüler. @No__t_0 veya `registerGroup` belirtilmemişse, varsayılan kayıt listesi görüntülenir. Anahtar belirtilmemişse, davranış aynıdır. Örneğin:

 `Debug.ListRegisters /Display eax`

 eşdeğerdir

 `Debug.ListRegisters eax`

 /List listedeki tüm yazmaç gruplarını görüntüler.

 /Watch [{`register`&#124; `registerGroup`}...] Listeye bir veya daha fazla `register` veya `registerGroup` değeri ekler.

 /Unwatch [{`register`&#124; `registerGroup`}...] Listeden bir veya daha fazla `register` veya `registerGroup` değeri kaldırır.

## <a name="remarks"></a>Açıklamalar
 Diğer ad `r` `Debug.ListRegisters` yerine kullanılabilir.

## <a name="example"></a>Örnek
 Bu örnek, kayıt grubu `Flags` değerlerini göstermek için `r` `Debug.ListRegisters` diğer adını kullanır.

```
r /Display Flags
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [hata ayıklama temelleri: kayıt penceresi](../../debugger/debugging-basics-registers-window.md) [nasıl yapılır: Yazmaçları penceresini kullanma](../../debugger/how-to-use-the-registers-window.md)
