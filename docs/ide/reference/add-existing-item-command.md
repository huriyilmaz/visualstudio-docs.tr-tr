---
title: Varolan Öğeyi Ekle Komutu
description: Var Olan Öğeyi Ekle komutunu ve mevcut bir çözüme mevcut bir dosyayı nasıl ekleyen ve açtığı hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ff4f6cb0e5c7dd45618615246c4c652e8611bf4a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041301"
---
# <a name="add-existing-item-command"></a>Varolan Öğeyi Ekle Komutu
Mevcut bir dosyayı geçerli çözüme ekler ve açar.

## <a name="syntax"></a>Söz dizimi

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler
`filename`\
Gereklidir. Geçerli çözüme eklemek istediğiniz öğenin uzantısıyla birlikte tam yol ve dosya adı. Dosya yolu veya dosya adı boşluk içeriyorsa, yolun tamamını tırnak işaretleri içine alın.

## <a name="switches"></a>Anahtarlar
/e: `editorname`\
İsteğe bağlı. Dosyanın açılamıyor olduğu düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadı ise, **Birlikte Aç** iletişim kutusu görüntülenir.

/e: bağımsız değişken söz dizimi, düzenleyici adlarını tırnak içine alınmış, Birlikte `editorname` **Aç İletişim** Kutusunda görünen şekilde kullanır. Örneğin, kaynak kod düzenleyicisinde bir stil sayfası açmak için /e: bağımsız değişkeni için aşağıdakini `editorname` girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar
Otomatik tamamlama, siz yazarak doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
Bu örnek Form1.frm dosyasını geçerli çözüme ekler.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
