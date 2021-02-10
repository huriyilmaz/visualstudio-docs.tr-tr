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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 30e2daae72dfd3b5d5a08847ddf87b93d1810a37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956678"
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
