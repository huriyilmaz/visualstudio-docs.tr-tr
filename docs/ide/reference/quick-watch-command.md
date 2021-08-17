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
ms.openlocfilehash: 3b47b34fafce8acf2eebaf01257e76df5b195c14
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056166"
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

`text`Atlanırsa, imleçte seçili olan metin veya sözcük izleme penceresi.

## <a name="example"></a>Örnek

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki Watch ve QuickWatch Windows Kullanarak Değişkenler üzerinde İzleme Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
