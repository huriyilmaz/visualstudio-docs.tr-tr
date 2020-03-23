---
title: Sayı Tabanını Ayarla Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f920311301b722c11bea4a9f4eb90e9aa7663d80
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747728"
---
# <a name="set-radix-command"></a>Sayı Tabanını Ayarla Komutu
İntesayı değerlerini görüntülemek için kullanılan sayısal tabanı ayarlar veya döndürür.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`10`veya `16` `hex` veya`dec`

İsteğe bağlı. Ondalık (10 veya aralık) veya hexadecimal (16 veya hex) gösterir. Bir bağımsız değişken atlanırsa, geçerli radix değeri döndürülür.

## <a name="example"></a>Örnek
Bu örnek, tamsayı değerlerini hexadecimal biçimde görüntülemek için ortamı ayarlar.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)