---
title: Başlat Komutu
description: Başlat komutunu ve başlangıç projesinde hata ayıklamanın nasıl başladığını öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f5eb9036b12d066e03eb6e4de346d99f78b04c79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048706"
---
# <a name="start-command"></a>Başlat Komutu
Başlangıç projesinde hata ayıklamaya başlar.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Bağımsız değişkenler
`address`

İsteğe bağlı. Programın, kaynak kodda kesme noktası gibi yürütmeyi askıya alma adresi. Bu bağımsız değişken yalnızca hata ayıklama modunda geçerlidir.

## <a name="remarks"></a>Açıklamalar
**Yürütülürken** Başlat komutu, belirtilen adrese bir RunToCursor işlemi gerçekleştirir.

## <a name="example"></a>Örnek
Bu örnek hata ayıklayıcıyı başlatır ve oluşan özel durumları yoksayar.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
