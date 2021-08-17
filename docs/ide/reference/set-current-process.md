---
title: Geçerli Süreci Ayarla
description: Geçerli Süreci Ayarla komutunu ve belirtilen işlemi hata ayıklayıcıda etkin işlem olarak nasıl ayarlaycı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c5f4aed5c44d8e3fe18ebbfdfaf2e4459bb14888608df91a9fcccd0c813ec67c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372029"
---
# <a name="set-current-process"></a>Geçerli Süreci Ayarla
Belirtilen işlemi hata ayıklayıcıda etkin işlem olarak ayarlar.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Bağımsız değişkenler
`index`

Gereklidir. Sürecin dizini.

## <a name="remarks"></a>Açıklamalar
Hata ayıklama sırasında birden çok işleme iliştirin, ancak herhangi bir zamanda tek bir işlem dosyada etkindir. Etkin işlemi ayarlamak `SetCurrentProcess` için komutunu kullanabilirsiniz.

## <a name="example"></a>Örnek

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
