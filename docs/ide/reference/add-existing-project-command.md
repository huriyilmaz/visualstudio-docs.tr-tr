---
title: Varolan Projeyi Ekle Komutu
description: Mevcut Proje Ekle komutunu Project mevcut bir çözümü nasıl ekley olduğunu öğrenin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 1bb60929279b79e8fb9b3f77ca98f5346f96851ddc894054895b113fd340ef6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412367"
---
# <a name="add-existing-project-command"></a>Varolan Projeyi Ekle Komutu
Mevcut bir projeyi geçerli çözüme ekler.

## <a name="syntax"></a>Söz dizimi

```cmd
File.AddExistingProject filename
```

## <a name="arguments"></a>Bağımsız değişkenler
`filename`\
İsteğe bağlı. Çözüme eklemek istediğiniz projenin uzantısıyla birlikte tam yol ve proje adı.

Bağımsız `filename` değişken boşluk içeriyorsa tırnak içine alınmalıdır.

Hiçbir dosya adı belirtilmezse, komut kullanıcının bir proje seçene kadar dosya iletişim kutusunu açar.

## <a name="remarks"></a>Açıklamalar
Otomatik tamamlama, siz yazarak doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
Bu örnek [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] TestProject1 projesini geçerli çözüme ekler.

```cmd
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
