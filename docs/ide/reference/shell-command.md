---
title: Kabuk Komutu
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf13c7624d6c9d8e64b79f653eb83a0c5f3b3f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565883"
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
> Yol dizesini değişmez tırnak işaretleri ("" ") içine aldıysanız, Windows yalnızca ilk alana kadar olan dizenin kısmını kullanır. Örneğin, yukarıdaki yol dizesi düzgün şekilde alıntılanmışsa Windows, C:\ dizininde bulunan "program" adlı bir dosya arar. kök dizin. C:\Program.exe yürütülebilir bir dosyanın gerçekten kullanılabilir olması durumunda bile, Windows bu programı istenen "c:\Program Files\SomeFile.exe" programının yerine yürütmeye çalışır.

## <a name="example"></a>Örnek
Aşağıdaki komut, dosyayı klasörüne kopyalamak için xcopy.exe kullanır `MyText.txt` `Text` . xcopy.exe çıkışı hem **komut penceresinde** hem de **Çıkış** penceresinde görüntülenir.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Çıkış Penceresi](../../ide/reference/output-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
