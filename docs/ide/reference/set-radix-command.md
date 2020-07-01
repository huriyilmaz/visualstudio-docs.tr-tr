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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e88dc1318e29ddf35073b78218eb113fe8952aac
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769653"
---
# <a name="set-radix-command"></a>Sayı Tabanını Ayarla Komutu
Tamsayı değerlerini göstermek için kullanılan sayısal temeli ayarlar veya döndürür.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Bağımsız değişkenler
`10`veya `16` veya `hex` veya`dec`

İsteğe bağlı. Ondalık (10 veya Dec) ya da onaltılı (16 veya onaltılı) anlamına gelir. Bir bağımsız değişken atlanırsa, geçerli taban değeri döndürülür.

## <a name="example"></a>Örnek
Bu örnek, ortamı tamsayı değerlerini onaltılık biçimde görüntüleyecek şekilde ayarlar.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)