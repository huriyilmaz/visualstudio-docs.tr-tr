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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a5ad6c57ed25d251ff7ce0e51093f5b542ed54
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610497"
---
# <a name="list-registers-command"></a>Yazmaçları Listele Komutu
Seçili yazmaçların değerini görüntüler ve gösterilecek kayıt listesini değiştirmenize izin verir.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Anahtarlar
/Display [{`register`&#124; `registerGroup`}...]

Belirtilen `register` veya `registerGroup` değerlerini görüntüler. @No__t_0 veya `registerGroup` belirtilmemişse, varsayılan kayıt listesi görüntülenir. Anahtar belirtilmemişse, davranış aynıdır. Örneğin:

`Debug.ListRegisters /Display eax`

eşdeğerdir

`Debug.ListRegisters eax`

/List

Listedeki tüm kayıt gruplarını görüntüler.

/Watch [{`register`&#124; `registerGroup`}...]

Listeye bir veya daha fazla `register` veya `registerGroup` değeri ekler.

/Unwatch [{`register`&#124; `registerGroup`}...]

Listeden bir veya daha fazla `register` veya `registerGroup` değeri kaldırır.

## <a name="remarks"></a>Açıklamalar
Diğer ad `r` `Debug.ListRegisters` yerine kullanılabilir.

## <a name="example"></a>Örnek
Bu örnek, kayıt grubu `Flags` değerlerini göstermek için `r` `Debug.ListRegisters` diğer adını kullanır.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Hata Ayıklama Temelleri: Yazmaçlar Penceresi](../../debugger/debugging-basics-registers-window.md)
- [Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../../debugger/how-to-use-the-registers-window.md)