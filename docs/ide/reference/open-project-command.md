---
title: Proje Aç komutu
description: Açık proje komutu ve mevcut bir projeyi veya çözümü nasıl açtığı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce00713cbfe862c5788a0131c99ba4c5750bb600
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304140"
---
# <a name="open-project-command"></a>Proje Aç komutu

Mevcut bir projeyi veya çözümü açar.

## <a name="syntax"></a>Söz dizimi

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Bağımsız değişkenler

`filename`

Gereklidir. Açılacak proje veya çözümün tam yolu ve dosya adı.

> [!NOTE]
> Bağımsız değişkeninin sözdizimi, `filename` boşluk içeren yolların tırnak işaretleri kullanmasını gerektirir.

## <a name="remarks"></a>Açıklamalar

Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

Hata ayıklanırken bu komut kullanılamaz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Basic projesi **test1** açar:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
