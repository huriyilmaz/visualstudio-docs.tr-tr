---
title: Hızlı Bakış Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1de6841f25bcc6f6c45bde93fdd4cf2cb49481ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747812"
---
# <a name="quick-watch-command"></a>Hızlı Bakış Komutu
[QuickWatch](../../debugger/watch-and-quickwatch-windows.md) penceresinin Expression alanında seçili veya belirtilen metni görüntüler. Bu iletişim kutusunu, hata ayıklayıcı tarafından tanınan bir değişkenin veya ifadenin geçerli değerini ya da bir kaydın içeriğini hesaplamak için kullanabilirsiniz. Ayrıca, herhangi bir const olmayan değişkenin veya herhangi bir kaydın içeriğinin değerini değiştirebilirsiniz.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Arguments

`text`\
İsteğe bağlı. **QuickWatch** iletişim kutusuna eklenecek metin.

## <a name="remarks"></a>Açıklamalar

@No__t_0 atlanırsa, imlecin Şu anda seçili olan metni veya sözcüğü izleme penceresi eklenir.

## <a name="example"></a>Örnek

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da gözcü ve hızlı gözcü pencerelerini kullanarak değişkenlerde bir Izleme ayarlayın](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)