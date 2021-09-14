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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f693391cea9ccb17a5e5427d7508424c05c3d457
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627105"
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

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)