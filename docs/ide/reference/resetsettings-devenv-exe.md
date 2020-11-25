---
title: -ResetSettings (devenv.exe)
description: Visual Studio varsayılan ayarlarını geri yüklemek ve Visual Studio IDE 'yi otomatik olarak başlatmak için ResetSettings Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22b3308b3bd1fed6ff1bc3d1f3a5622eb6f8284f
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040036"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Visual Studio varsayılan ayarlarını geri yükler ve Visual Studio IDE 'yi otomatik olarak başlatır. Bu anahtar isteğe bağlı olarak ayarları belirtilen ayarlar dosyasına sıfırlar.

Varsayılan ayarlar, Visual Studio ilk kez başlatıldığında seçili olan profilden gelir.

> [!TIP]
> Tümleşik geliştirme ortamı (IDE) kullanarak ayarları sıfırlama hakkında bilgi edinmek için bkz. [ayarları sıfırlama](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Söz dizimi

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SettingsFile*

  İsteğe bağlı. Visual Studio 'ya uygulanacak ayarlar dosyasının tam yolu ve adı.

- *Defaultcollectionbelirleyicisi*

  İsteğe bağlı. Geri yüklenecek varsayılan ayar koleksiyonunu temsil eden bir tanımlayıcı. Tabloda listelenen varsayılan koleksiyon belirticilerden birini seçin.

  | Varsayılan koleksiyon adı | Koleksiyon Belirleyicisi |
  | --- | --- |
  | **Genel** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C #** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Web Geliştirme** | `Web` |
  | **Web geliştirme (yalnızca kod)** | `WebCode` |

## <a name="remarks"></a>Açıklamalar

*SettingsFile* BELIRTILMEMIŞSE, IDE var olan ayarları kullanarak açılır.

## <a name="example"></a>Örnek

İlk örnek dosyada depolanan ayarları uygular `MySettings.vssettings` .

İkinci örnek, Visual C# varsayılan profilini geri yükler.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../environment-settings.md)
- [Visual Studio IDE 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
