---
title: -ResetSettings (devenv.exe)
description: Varsayılan ayarları geri yüklemek ve IDE'yi otomatik olarak başlatmak için ResetSettings devenv komut satırı Visual Studio kullanmayı Visual Studio öğrenin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: cbc3b329b4a525a525823169d63ebbda2770727e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062153"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Varsayılan Visual Studio geri yüklenir ve IDE'nin Visual Studio başlatılır. Bu anahtar isteğe bağlı olarak ayarları belirtilen bir ayarlar dosyasına () `*.vssettings` sıfırlar.

Varsayılan ayarlar, Visual Studio ilk kez Visual Studio profilden gelir.

> [!TIP]
> Tümleşik geliştirme ortamını (IDE) kullanarak ayarları sıfırlamayı öğrenmek için [bkz. Ayarları sıfırlama.](../environment-settings.md#reset-settings)

## <a name="syntax"></a>Söz dizimi

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SettingsFile*

  İsteğe bağlı. Dosyanın geçerli olduğu `.vssettings` dosyanın tam yolu ve Visual Studio.

- *DefaultCollectionSpecifier*

  İsteğe bağlı. Geri yüklemek için varsayılan bir ayar koleksiyonunu temsil eden bir belirleyici. Tabloda listelenen varsayılan koleksiyon belirleyicilerinden birini seçin.

  | Varsayılan koleksiyon adı | Koleksiyon belirleyicisi |
  | --- | --- |
  | **Genel** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C #** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Web Geliştirme** | `Web` |
  | **Web Geliştirme (Yalnızca Kod)** | `WebCode` |

## <a name="remarks"></a>Açıklamalar

*AyarDosyası* belirtilmezse, IDE mevcut ayarları kullanarak açılır. 


## <a name="example"></a>Örnek

İlk örnek dosyasında depolanan ayarları `MySettings.vssettings` uygular.

İkinci örnek, Visual C# varsayılan profilini geri yükledi.

Üçüncü örnek, ayarları Visual Studio sonra da kapatacak. Ekini ekleme. `/Command "File.Exit"`

```shell
devenv /ResetSettings "%USERPROFILE%\MySettings.vssettings"

devenv /ResetSettings CSharp

devenv /NoSplash /ResetSettings General /Command Exit 
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../environment-settings.md)
- [IDE'Visual Studio kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
