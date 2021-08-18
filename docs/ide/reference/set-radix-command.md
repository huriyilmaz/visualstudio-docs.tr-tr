---
title: Sayı Tabanını Ayarla Komutu
description: Set Radix komutunu ve tamsayı değerlerini görüntülemek için kullanılan sayısal tabanı ayarlama veya döndürür.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: cccc39371ce07d0b3ee93ec422d29ee4381602e27e17ba690167a18d7bb9cb3a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121356978"
---
# <a name="set-radix-command"></a>Sayı Tabanını Ayarla Komutu
Tamsayı değerlerini görüntülemek için kullanılan sayısal tabanı ayarlar veya döndürür.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Bağımsız değişkenler
`10`veya `16` veya `hex``dec`

İsteğe bağlı. Ondalık (10 veya ara) veya onaltılık (16 veya onaltılık) gösterir. Bir bağımsız değişken atlanırsa geçerli radyax değeri döndürülür.

## <a name="example"></a>Örnek
Bu örnek, ortamı tamsayı değerlerini onaltılık biçimde görüntülemektedir.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)