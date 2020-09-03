---
title: Hızlı Izle komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da9ba9572e121a9eba74cd8d624789032f1bb4a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665665"
---
# <a name="quick-watch-command"></a>Hızlı Bakış Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[QuickWatch Iletişim kutusunun](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)ifade alanında seçili veya belirtilen metni görüntüler. Bu iletişim kutusunu, hata ayıklayıcı tarafından tanınan bir değişkenin veya ifadenin geçerli değerini ya da bir kaydın içeriğini hesaplamak için kullanabilirsiniz. Ayrıca, herhangi bir const olmayan değişkenin veya herhangi bir kaydın içeriğinin değerini değiştirebilirsiniz.

## <a name="syntax"></a>Söz dizimi

```
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `text` Seçim. **QuickWatch** iletişim kutusuna eklenecek metin.

## <a name="remarks"></a>Açıklamalar
 `text`Atlanırsa, imlecin üzerinde şu anda seçili olan metin veya sözcük izleme penceresi eklenir.

## <a name="example"></a>Örnek

```
>Debug.QuickWatch
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: QuickWatch Iletişim kutusunu kullanma](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
