---
title: Yazmaçları Listele Komutu
description: Yazmazları Listele komutunu ve seçilen yazmaların değerini nasıl görüntülemektedir ve kayıt listesini gösterilecek şekilde değiştirmenizi sağlar.
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
ms.openlocfilehash: 37ec0e5211cebda7c2497c069bcb72a7e56ae2bb1987b5dbec71c67ff6274526
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387518"
---
# <a name="list-registers-command"></a>Yazmaçları Listele Komutu
Seçilen yazmaların değerini görüntüler ve kayıt listesini gösterecek şekilde değiştirmenize olanak sağlar.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Anahtarlar
/Display [{ `register`&#124;`registerGroup` }...]

Belirtilen veya değerlerini `register` `registerGroup` görüntüler. Yoksa `register` veya `registerGroup` belirtilmezse, varsayılan yazmaz listesi görüntülenir. Anahtar belirtilmezse davranış aynıdır. Örnek:

`Debug.ListRegisters /Display eax`

eşdeğerdir

`Debug.ListRegisters eax`

/List

Listede tüm yazmam gruplarını görüntüler.

/Watch [{ `register`&#124;`registerGroup` }...]

Listeye bir veya `register` daha `registerGroup` fazla değer ekler.

/Unwatch [{ `register`&#124;`registerGroup` }...]

Listeden bir veya `register` daha fazla veya değeri `registerGroup` kaldırır.

## <a name="remarks"></a>Açıklamalar
yerine `r` diğer ad `Debug.ListRegisters` kullanılabilir.

## <a name="example"></a>Örnek
Bu örnek, `Debug.ListRegisters` kayıt grubunun değerlerini görüntülemek için diğer adını `r` `Flags` kullanır.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Hata Ayıklama Temelleri: Yazmaçlar Penceresi](../../debugger/debugging-basics-registers-window.md)
- [Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../../debugger/how-to-use-the-registers-window.md)
