---
title: Yazmaçları Listele Komutu
description: Liste Yazmaçları komutu ve seçilen yazmaçların değerini nasıl görüntüleyeceği ve gösterilecek kayıt listesini değiştirmenize izin veren hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 7bf6d9526e61327b1ff582a74c1624f1bfd7b8c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151437"
---
# <a name="list-registers-command"></a>Yazmaçları Listele Komutu
Seçili yazmaçların değerini görüntüler ve gösterilecek kayıt listesini değiştirmenize izin verir.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Anahtarlar
/Display [{ `register`&#124;`registerGroup` }...]

Belirtilen veya değerlerini görüntüler `register` `registerGroup` . `register`Veya `registerGroup` belirtilmemişse, varsayılan kayıt listesi görüntülenir. Anahtar belirtilmemişse, davranış aynıdır. Örnek:

`Debug.ListRegisters /Display eax`

eşdeğerdir

`Debug.ListRegisters eax`

/List

Listedeki tüm kayıt gruplarını görüntüler.

/Watch [{ `register`&#124;`registerGroup` }...]

Listeye bir veya daha fazla `register` veya `registerGroup` değer ekler.

/Unwatch [{ `register`&#124;`registerGroup` }...]

Listeden bir veya daha fazla `register` veya `registerGroup` değeri kaldırır.

## <a name="remarks"></a>Açıklamalar
Diğer ad, yerine `r` kullanılabilir `Debug.ListRegisters` .

## <a name="example"></a>Örnek
Bu örnek, `Debug.ListRegisters` `r` yazmaç grubunun değerlerini göstermek için diğer adı kullanır `Flags` .

```cmd
r /Display Flags
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Hata Ayıklama Temelleri: Yazmaçlar Penceresi](../../debugger/debugging-basics-registers-window.md)
- [Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../../debugger/how-to-use-the-registers-window.md)
