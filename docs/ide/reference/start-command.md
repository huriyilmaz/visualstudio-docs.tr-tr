---
title: Başlat Komutu
description: Başlangıç komutu ve başlangıç projesinde hata ayıklamaya başlama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0cae9d4630a854bc24c952380a1e27cbab42d261
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938661"
---
# <a name="start-command"></a>Başlat Komutu
Başlangıç projesinde hata ayıklamaya başlar.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Bağımsız değişkenler
`address`

İsteğe bağlı. Kaynak kodundaki bir kesme noktasına benzer şekilde programın yürütmeyi askıya aldığı adres. Bu bağımsız değişken yalnızca hata ayıklama modunda geçerlidir.

## <a name="remarks"></a>Açıklamalar
Çalıştırıldığında **Başlat** komutu, belirtilen adrese bir RunToCursor işlemi gerçekleştirir.

## <a name="example"></a>Örnek
Bu örnek, hata ayıklayıcıyı başlatır ve oluşan tüm özel durumları yoksayar.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
