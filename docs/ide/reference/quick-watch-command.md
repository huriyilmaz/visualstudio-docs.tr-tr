---
title: Hızlı Bakış Komutu
description: Hızlı İzleme komutu ve QuickWatch penceresinin İfade alanında seçili veya belirtilen metni görüntüleme hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ae0717b8c4f4ffe6f3d469b21d26b794ee855dc6b25a965f2642e322892b76f4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387076"
---
# <a name="quick-watch-command"></a>Hızlı Bakış Komutu
[QuickWatch](../../debugger/watch-and-quickwatch-windows.md) penceresinin İfade alanında seçili veya belirtilen metni görüntüler. Hata ayıklayıcısı tarafından tanınan bir değişkenin veya ifadenin geçerli değerini veya yazmacın içeriğini hesaplamak için bu iletişim kutusunu kullanabilirsiniz. Ayrıca, sabit olmayan herhangi bir değişkenin değerini veya herhangi bir yazmaç içeriğini değiştirebilirsiniz.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Bağımsız değişkenler

`text`\
İsteğe bağlı. **QuickWatch** iletişim kutusuna eklemek istediğiniz metin.

## <a name="remarks"></a>Açıklamalar

`text`Atlanırsa, o anda imleçte seçili olan metin veya sözcük izleme penceresi.

## <a name="example"></a>Örnek

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki Watch ve QuickWatch Windows kullanarak Değişkenler üzerinde watch Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
