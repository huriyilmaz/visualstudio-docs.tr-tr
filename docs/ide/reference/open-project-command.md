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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4298c840094f7f1f75e58be1b25213cdf66a6674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881977"
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
