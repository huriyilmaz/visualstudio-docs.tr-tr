---
title: İzle Komutu
description: İzleme komutu hakkında bilgi edinmek ve bir uygulamanın belirtilen örneğini nasıl oluşturduğu ve izleme penceresi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2258c704e8a91b2b00942a8dcae5ca5215da028d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724888"
---
# <a name="watch-command"></a>İzle Komutu
İzleme penceresinin belirtilen bir örneğini oluşturur **ve** açar. Değişkenlerin, **ifadelerin** ve kayıtların değerlerini hesaplamak, bu değerleri düzenlemek ve sonuçları kaydetmek için bir İzleme penceresi kullanabilirsiniz.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Bağımsız değişkenler

`index`\
Gereklidir. İzleme penceresinin örnek numarası.

## <a name="remarks"></a>Açıklamalar

bir `index` tamsayı olmalıdır. Geçerli değerler 1, 2, 3 veya 4'tir.

## <a name="example"></a>Örnek

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatikler ve Yereller Pencereleri](../../debugger/autos-and-locals-windows.md)
- [Visual Studio'daki Watch ve QuickWatch Windows kullanarak Değişkenler üzerinde watch Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
