---
title: Geçerli Süreci Ayarla
description: Geçerli Işlem ayarla komutunu ve belirtilen işlemi hata ayıklayıcıda etkin işlem olarak nasıl ayarlacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4b6a5c2f010b60546fe1ece16f66bf437d2dc633
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616595"
---
# <a name="set-current-process"></a>Geçerli Süreci Ayarla
Belirtilen işlemi hata ayıklayıcıda etkin işlem olarak ayarlar.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Bağımsız değişkenler
`index`

Gereklidir. İşlemin dizini.

## <a name="remarks"></a>Açıklamalar
Hata ayıklarken birden çok işleme iliştirebilirsiniz, ancak belirli bir zamanda Dubber içinde yalnızca bir işlem etkin olur. `SetCurrentProcess`Etkin işlemi ayarlamak için komutunu kullanabilirsiniz.

## <a name="example"></a>Örnek

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
