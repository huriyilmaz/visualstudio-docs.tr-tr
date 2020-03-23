---
title: Yazmaçları Listele Komutu
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e87b10a7827b5365b507abb2c72a21506e59c19e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568691"
---
# <a name="list-registers-command"></a>Yazmaçları Listele Komutu
Seçili kayıtların değerini görüntüler ve göstermek için kayıt listesini değiştirmenize olanak tanır.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Anahtarlar
/Görüntüle`register` [{&#124;`registerGroup`}...]

Belirtilen `register` veya `registerGroup`. değerlerini görüntüler Hayır `register` veya `registerGroup` belirtilmişse, varsayılan kayıt listesi görüntülenir. Anahtar belirtilmemişse, davranış aynıdır. Örnek:

`Debug.ListRegisters /Display eax`

eşdeğerdir

`Debug.ListRegisters eax`

/Liste

Listedeki tüm kayıt gruplarını görüntüler.

/İzle`register` [{ `registerGroup`&#124;}...]

Listeye bir `register` veya `registerGroup` daha fazla değer veya değer ekler.

/İzlemeiz`register` [{ `registerGroup`&#124;}...]

Bir veya daha `register` `registerGroup` fazla değeri veya değerleri listeden kaldırır.

## <a name="remarks"></a>Açıklamalar
Takma ad, `r` '' `Debug.ListRegisters`yerine kullanılabilir.

## <a name="example"></a>Örnek
Bu örnek, `Debug.ListRegisters` kayıt `r` grubunun `Flags`değerlerini görüntülemek için takma ad kullanır.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Hata Ayıklama Temelleri: Yazmaçlar Penceresi](../../debugger/debugging-basics-registers-window.md)
- [Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../../debugger/how-to-use-the-registers-window.md)
