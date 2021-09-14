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
ms.openlocfilehash: d118ac31d86fcf2935b6c7864ee7cdf2a8d5ad2a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627123"
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
