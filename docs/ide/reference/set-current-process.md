---
title: Geçerli Süreci Ayarla
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3440c66d79fef3eac3744681870c9ce1ed0e97b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593557"
---
# <a name="set-current-process"></a>Geçerli Süreci Ayarla
Belirtilen işlemi hata ayıklamadaki etkin işlem olarak ayarlar.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Bağımsız Değişkenler
`index`

Gereklidir. Sürecin dizini.

## <a name="remarks"></a>Açıklamalar
Hata ayıklama sırasında birden çok işleme ekleyebilirsiniz, ancak herhangi bir zamanda dublajda yalnızca bir işlem etkindir. Etkin işlemi `SetCurrentProcess` ayarlamak için komutu kullanabilirsiniz.

## <a name="example"></a>Örnek

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
