---
title: Radix komutunu ayarla | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 050cbe6e639f4177694d9af3ecbc0b768065b7d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665417"
---
# <a name="set-radix-command"></a>Sayı Tabanını Ayarla Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tamsayı değerlerini göstermek için kullanılan sayısal temeli ayarlar veya döndürür.

## <a name="syntax"></a>Söz dizimi

```
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `10` ya da ya da `16` `hex` `dec` isteğe bağlı. Ondalık (10 veya Dec) ya da onaltılı (16 veya onaltılı) anlamına gelir. Bir bağımsız değişken atlanırsa, geçerli taban değeri döndürülür.

## <a name="example"></a>Örnek
 Bu örnek, ortamı tamsayı değerlerini onaltılık biçimde görüntüleyecek şekilde ayarlar.

```
>Debug.SetRadix hex
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
