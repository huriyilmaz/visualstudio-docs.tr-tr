---
title: Geçerli Işlemi ayarla | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c362d3f5dda5015e91ac88dd8f0abd60a185ba72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665475"
---
# <a name="set-current-process"></a>Geçerli Süreci Ayarla
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen işlemi hata ayıklayıcıda etkin işlem olarak ayarlar.

## <a name="syntax"></a>Söz dizimi

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Bağımsız değişkenler
 `index` Gerekli. İşlemin dizini.

## <a name="remarks"></a>Açıklamalar
 Hata ayıklarken birden çok işleme iliştirebilirsiniz, ancak belirli bir zamanda Dubber içinde yalnızca bir işlem etkin olur. `SetCurrentProcess`Etkin işlemi ayarlamak için komutunu kullanabilirsiniz.

## <a name="example"></a>Örnek

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
