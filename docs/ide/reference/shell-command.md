---
title: Kabuk Komutu
description: Kabuk komutu ve dosyanın içindeki yürütülebilir programları nasıl Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 070d58d8fc4561c37dfce66fd89c2e6905184daa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725718"
---
# <a name="shell-command"></a>Kabuk Komutu
içinde yürütülebilir programları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] başlatıyor.

## <a name="syntax"></a>Söz dizimi

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Bağımsız değişkenler
`path`

Gereklidir. Yürütülecek dosyanın yolu ve dosya adı veya açılacak belge. Belirtilen dosya PATH ortam değişkenli dizinlerden biri içinde yoksa tam yol gereklidir.

`args`

İsteğe bağlı. Çağrılan programa geçilen tüm bağımsız değişkenler.

## <a name="switches"></a>Anahtarlar
/commandwindow [or] /command [or] /c [or] /cmd

İsteğe bağlı. Yürütülebilir dosyanın çıktının Komut penceresinde **görüntülendiğinden belirtir.**

/dir: `folder` [or] /d: `folder`

İsteğe bağlı. Program çalıştır çalışırken ayar için çalışma dizinini belirtir.

/outputwindow [veya] /output [or] /out [or] /o

İsteğe bağlı. Yürütülebilir dosyanın çıktının Çıkış penceresinde **görüntülendiğinden belirtir.**

## <a name="remarks"></a>Açıklamalar
/dir /o /c anahtarları hemen sonra `Tools.Shell` belirtilmelidir. Yürütülebilir dosyanın adına göre belirtilen her şey komut satırı bağımsız değişkenleri olarak geçirilebilir.

Önceden tanımlanmış diğer `Shell` ad yerine `Tools.Shell` kullanılabilir.

> [!CAUTION]
> Bağımsız değişken dizin yolunu ve dosya adını sağlarsa, pathname'in tamamını aşağıda olduğu gibi değişmez tırnak `path` içine (""") yazmanız gerekir:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Her üç çift tırnak (""") kümesi, işlemci tarafından tek bir `Shell` çift tırnak karakteri olarak yorumlanır. Bu nedenle, önceki örnek aslında aşağıdaki yol dizesini komutuna `Shell` iletir:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Yol dizesini değişmez tırnak içine ("""), Windows dizenin yalnızca ilk alana kadar olan kısmını kullanır. Örneğin, yukarıdaki yol dizesi düzgün bir şekilde tırnak içine Windows C:\ konumunda bulunan "Program" adlı bir dosyayı aramanız gerekir. kök dizini. Bir C:\Program.exe yürütülebilir dosya gerçekten varsa, hatta bir tane kötü amaçlı kurcalama tarafından yüklenmişse, Windows istenen "c:\Program Files\SomeFile.exe" programı yerine bu programı yürütmeyi denebilir.

## <a name="example"></a>Örnek
Aşağıdaki komut, xcopy.exe klasörüne kopyalamak `MyText.txt` için aşağıdaki komutu `Text` kullanır. Komut xcopy.exe hem de Çıkış **penceresinde** **görüntülenir.**

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Çıkış Penceresi](../../ide/reference/output-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
