---
title: Kabuk Komutu
description: Kabuk komutu ve Visual Studio içinden yürütülebilir programları nasıl Başlatan hakkında bilgi edinin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117117"
---
# <a name="shell-command"></a>Kabuk Komutu
İçinden çalıştırılabilir programları başlatır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="syntax"></a>Söz dizimi

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Bağımsız değişkenler
`path`

Gereklidir. Yürütülecek dosyanın yolu ve dosya adı ya da açılacak belge. Belirtilen dosya yol ortam değişkeninde dizinlerden birinde değilse tam yol gereklidir.

`args`

İsteğe bağlı. Çağrılan programa geçirilecek herhangi bir bağımsız değişken.

## <a name="switches"></a>Anahtarlar
/CommandWindow [veya]/Command [veya]/c [veya]/cmd

İsteğe bağlı. Yürütülebilir dosyanın çıktısının **komut** penceresinde görüntülendiğini belirtir.

/dir: `folder` [veya]/d: `folder`

İsteğe bağlı. Program çalıştırıldığında ayarlanacak çalışma dizinini belirtir.

/OutputWindow [veya]/output [veya]/Out [veya]/o

İsteğe bağlı. Yürütülebilir dosyanın çıktısının **Çıkış** penceresinde görüntülendiğini belirtir.

## <a name="remarks"></a>Açıklamalar
/Dir/o/c anahtarlarının hemen sonra belirtilmesi gerekir `Tools.Shell` . Yürütülebilir dosyanın adından sonra belirtilen her şey, komut satırı bağımsız değişkenleri olarak kendisine geçirilir.

Önceden tanımlanmış diğer ad, yerine `Shell` kullanılabilir `Tools.Shell` .

> [!CAUTION]
> `path`Bağımsız değişken dizin yolunu ve dosya adını sağlarsa, aşağıdaki gibi tüm yol adını sabit tırnak ("" ") içine almalısınız:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Her üç çift tırnak ("" ") kümesi, `Shell` işlemci tarafından tek bir çift tırnak karakteri olarak yorumlanır. Bu nedenle, önceki örnek şu yol dizesini `Shell` komutuna geçirir:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> yol dizesini değişmez tırnak işaretleri ("" ") içine aldıysanız Windows, yalnızca ilk alana kadar olan dizenin kısmını kullanacaktır. örneğin, yukarıdaki yol dizesi düzgün şekilde tırnak içine alınmazdı, Windows c:\ dizininde bulunan "Program" adlı bir dosya arayacaktır. kök dizin. C:\Program.exe çalıştırılabilir bir dosya gerçekten kullanılabilir durumda olsa da, "c:\Program Files\SomeFile.exe" programının yerine bu programı yürütmeyi dener Windows.

## <a name="example"></a>Örnek
Aşağıdaki komut, dosyayı klasörüne kopyalamak için xcopy.exe kullanır `MyText.txt` `Text` . xcopy.exe çıkışı hem **komut penceresinde** hem de **Çıkış** penceresinde görüntülenir.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Çıkış Penceresi](../../ide/reference/output-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
