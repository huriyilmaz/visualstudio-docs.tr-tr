---
title: Proje Aç komutu
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c84a2dcd99ef7cff9b5f37a1c69f235582a7973
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666422"
---
# <a name="open-project-command"></a>Proje Aç komutu

Mevcut bir projeyi veya çözümü açar.

## <a name="syntax"></a>Sözdizimi

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>Arguments

`filename`

Gerekli. Açılacak proje veya çözümün tam yolu ve dosya adı.

> [!NOTE]
> @No__t_0 bağımsız değişkeninin sözdizimi, boşluk içeren yolların tırnak işaretleri kullanmasını gerektirir.

## <a name="remarks"></a>Açıklamalar

Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

Hata ayıklanırken bu komut kullanılamaz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Basic projesi **test1**açar:

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)