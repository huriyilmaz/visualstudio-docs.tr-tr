---
title: Varolan Projeyi Ekle Komutu
description: Mevcut proje Ekle komutu ve mevcut bir projeyi geçerli bir çözüme nasıl ekleyen hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c12106621599d428e9a701de9ba5e468b5e312a
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871008"
---
# <a name="add-existing-project-command"></a>Varolan Projeyi Ekle Komutu
Geçerli çözüme mevcut bir projeyi ekler.

## <a name="syntax"></a>Söz dizimi

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Bağımsız değişkenler
`filename`\
İsteğe bağlı. Çözüme eklenecek projenin Uzantısı ile tam yol ve proje adı.

`filename`Bağımsız değişken boşluk içeriyorsa, tırnak işaretleri içine alınmalıdır.

Dosya adı belirtilmemişse, komut, kullanıcının bir proje seçmesini sağlamak için dosya iletişim kutusunu açar.

## <a name="remarks"></a>Açıklamalar
Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
Bu örnek, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] TestProject1 projesini geçerli çözüme ekler.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
