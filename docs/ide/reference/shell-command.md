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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565883"
---
# <a name="shell-command"></a>Kabuk Komutu
Yürütülebilir programları içinden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]başlatın.

## <a name="syntax"></a>Sözdizimi

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`path`

Gereklidir. Yürütülecek dosyanın yolu ve dosya adı veya açılacak belge. Belirtilen dosya PATH ortamı değişkenindeki dizinlerden birinde değilse tam bir yol gereklidir.

`args`

İsteğe bağlı. Çağrılan programa geçirilen bağımsız değişkenler.

## <a name="switches"></a>Anahtarlar
/commandwindow [veya] /command [veya] /c [veya] /cmd

İsteğe bağlı. Yürütülebilir çıktının **Komut** penceresinde görüntüleneceğini belirtir.

/dir:`folder` [veya] /d:`folder`

İsteğe bağlı. Program çalıştırıldığında ayarlanacak çalışma dizinini belirtir.

/outputwindow [veya] /output [veya] /out [veya] /o

İsteğe bağlı. Çalıştırılabilen çıktının **Çıktı** penceresinde görüntüleneceğini belirtir.

## <a name="remarks"></a>Açıklamalar
/dir /o /c anahtarları hemen sonra `Tools.Shell`belirtilmelidir. Yürütülebilir addan sonra belirtilen her şey komut satırı bağımsız değişkenleri olarak ona aktarılır.

Önceden tanımlanmış takma `Shell` ad yerine `Tools.Shell`kullanılabilir.

> [!CAUTION]
> `path` Bağımsız değişken, dosya adının yanı sıra dizin yolunu da sağlıyorsa, tüm yol adının tamamını aşağıdaki gibi gerçek tırnak (""""""""" olarak) içine almanız gerekir:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Üç çift tırnak (""""" her küme) `Shell` işlemci tarafından tek bir çift tırnak karakteri olarak yorumlanır. Böylece, önceki örnek aslında `Shell` komuta aşağıdaki yol dizegeçer:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Yol dizesini gerçek tırnak içinde ("""""" olarak) içine koymazsanız, Windows dizenin yalnızca ilk boşluğa kadar olan kısmını kullanır. Örneğin, yukarıdaki yol dizesi düzgün bir şekilde alıntı yapılmazsa, Windows C:\ kök dizini. C:\Program.exe yürütülebilir dosya aslında mevcutsa, hatta yasadışı kurcalama tarafından yüklenen bir dosya olsaydı, Windows bu programı istenen "c:\Program Files\SomeFile.exe" programı yerine yürütmeyi dener.

## <a name="example"></a>Örnek
Aşağıdaki komut, dosyayı `MyText.txt` `Text` klasöre kopyalamak için xcopy.exe kullanır. xcopy.exe'den çıkan çıktı hem **Komut Penceresinde** hem de **Çıktı** penceresinde görüntülenir.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Çıkış Penceresi](../../ide/reference/output-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
