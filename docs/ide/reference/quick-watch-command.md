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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f6382a79884bf8c3891a3a191b594bf183efb62
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565636"
---
# <a name="quick-watch-command"></a>Hızlı Bakış Komutu
Seçilen veya belirtilen metni [QuickWatch](../../debugger/watch-and-quickwatch-windows.md) penceresinin İfade alanında görüntüler. Hata ayıklayıcı veya bir kaydın içeriğini tanıyan bir değişkenin veya ifadenin geçerli değerini hesaplamak için bu iletişim kutusunu kullanabilirsiniz. Buna ek olarak, const olmayan değişkenin veya herhangi bir kaydın içeriğini değiştirebilirsiniz.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Bağımsız Değişkenler

`text`\
İsteğe bağlı. **QuickWatch** iletişim kutusuna eklenecek metin.

## <a name="remarks"></a>Açıklamalar

`text` Atlanırsa, imleçte şu anda seçili metin veya sözcük İzle penceresine eklenir.

## <a name="example"></a>Örnek

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Watch ve QuickWatch Windows'u kullanarak Değişkenlere Göz Kırtın](../../debugger/watch-and-quickwatch-windows.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
