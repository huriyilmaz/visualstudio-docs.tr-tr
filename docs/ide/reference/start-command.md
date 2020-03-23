---
title: Başlat Komutu
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6138c4cff33f0b2a4211439a01a058da59da811
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590286"
---
# <a name="start-command"></a>Başlat Komutu
Başlangıç projesihatasını ayıklama başlar.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`address`

İsteğe bağlı. Programın yürütmeyi askıya aldığı adres, kaynak kodundaki bir kesme noktasına benzer. Bu bağımsız değişken yalnızca hata ayıklama modunda geçerlidir.

## <a name="remarks"></a>Açıklamalar
**Başlat** komutu yürütüldüğünde, belirtilen adrese bir RunToCursor işlemi gerçekleştirir.

## <a name="example"></a>Örnek
Bu örnek hata ayıklama yı başlatır ve oluşan tüm özel durumları yoksa.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
