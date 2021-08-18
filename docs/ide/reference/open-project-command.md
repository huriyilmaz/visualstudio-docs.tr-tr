---
title: Proje Aç komutu
description: açık Project komutu ve bunun mevcut bir projeyi veya çözümü nasıl açtığı hakkında bilgi edinin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b7e74880ec1dd038dd5bd50416bc97652cf1818c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041220"
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

aşağıdaki örnek, Visual Basic projesi **Test1** açar:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
