---
title: Sayı Tabanını Ayarla Komutu
description: Radix Ayarla komutu ve tam sayı değerlerini göstermek için kullanılan sayısal temeli nasıl ayarlayan veya döndüren hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: 50d0097debbd7e91906202b85e8e9e6dab36a27d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957692"
---
# <a name="set-radix-command"></a>Sayı Tabanını Ayarla Komutu
Tamsayı değerlerini göstermek için kullanılan sayısal temeli ayarlar veya döndürür.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Bağımsız değişkenler
`10` veya `16` veya `hex` veya `dec`

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