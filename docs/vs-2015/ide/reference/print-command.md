---
title: Komutu Yazdır | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662151"
---
# <a name="print-command"></a>Yazdır Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir ifadeyi değerlendirir veya belirtilen metni görüntüler.

## <a name="syntax"></a>Söz dizimi

```
Debug.Print text
```

## <a name="arguments"></a>Bağımsız değişkenler
 `text` Gerekli. Değerlendirilecek ifade veya görüntülenecek metin.

## <a name="remarks"></a>Açıklamalar
 Bu komut için bir diğer ad olarak soru işareti (?) kullanabilirsiniz. Bu nedenle, örneğin, komut

```
>Debug.Print expA
```

 Ayrıca yazılabilir

```
>? expA
```

 Bu komutun her iki sürümü de ifadenin geçerli değerini döndürür `expA` .

## <a name="example"></a>Örnek

```
>Debug.Print varA
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Ifadeyi değerlendir komutu](../../ide/reference/evaluate-statement-command.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
