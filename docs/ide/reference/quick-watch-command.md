---
title: Hızlı Bakış Komutu
description: Hızlı Izleme komutu ve seçilen veya belirtilen metnin hızlı Izleme penceresinin Ifade alanında nasıl görüntüleneceğini öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6185418364e8b22e1f473308b2db9899c8778d13
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304171"
---
# <a name="quick-watch-command"></a>Hızlı Bakış Komutu
[QuickWatch](../../debugger/watch-and-quickwatch-windows.md) penceresinin Expression alanında seçili veya belirtilen metni görüntüler. Bu iletişim kutusunu, hata ayıklayıcı tarafından tanınan bir değişkenin veya ifadenin geçerli değerini ya da bir kaydın içeriğini hesaplamak için kullanabilirsiniz. Ayrıca, herhangi bir const olmayan değişkenin veya herhangi bir kaydın içeriğinin değerini değiştirebilirsiniz.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Bağımsız değişkenler

`text`\
İsteğe bağlı. **QuickWatch** iletişim kutusuna eklenecek metin.

## <a name="remarks"></a>Açıklamalar

`text`Atlanırsa, imlecin üzerinde şu anda seçili olan metin veya sözcük izleme penceresi eklenir.

## <a name="example"></a>Örnek

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da gözcü ve hızlı gözcü pencerelerini kullanarak değişkenlerde bir Izleme ayarlayın](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
