---
title: Geçerli Süreci Ayarla
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d8c313eebc8623156dd7a575060397ee6e16a9d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748645"
---
# <a name="set-current-process"></a>Geçerli Süreci Ayarla
Belirtilen işlemi hata ayıklayıcıda etkin işlem olarak ayarlar.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Arguments
`index`

Gerekli. İşlemin dizini.

## <a name="remarks"></a>Açıklamalar
Hata ayıklarken birden çok işleme iliştirebilirsiniz, ancak belirli bir zamanda Dubber içinde yalnızca bir işlem etkin olur. Etkin işlemi ayarlamak için `SetCurrentProcess` komutunu kullanabilirsiniz.

## <a name="example"></a>Örnek

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)