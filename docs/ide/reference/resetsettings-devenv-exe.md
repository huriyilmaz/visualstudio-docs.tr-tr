---
title: -ResetSettings (devenv.exe)
description: varsayılan Visual Studio ayarlarını geri yüklemek ve Visual Studio ıde 'yi otomatik olarak başlatmak için resetsettings devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: b3329f4a5f42094a1ad87dd8b69ec99255d4e21cdf64575a91bf68494d7c7d30
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121317806"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

varsayılan Visual Studio ayarlarını geri yükler ve Visual Studio ıde 'yi otomatik olarak başlatır. Bu anahtar isteğe bağlı olarak ayarları belirtilen ayarlar dosyasına () sıfırlar `*.vssettings` .

varsayılan ayarlar, Visual Studio ilk kez başlatıldığında seçili olan profilden gelir.

> [!TIP]
> Tümleşik geliştirme ortamı (IDE) kullanarak ayarları sıfırlama hakkında bilgi edinmek için bkz. [ayarları sıfırlama](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Söz dizimi

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SettingsFile*

  İsteğe bağlı. Visual Studio uygulanacak dosyanın tam yolu ve adı `.vssettings` .

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

üçüncü örnek, ayarları uyguladıktan sonra Visual Studio de kapatır. Ekleme yapabilirsiniz `/Command "File.Exit"` .

```shell
devenv /ResetSettings "%USERPROFILE%\MySettings.vssettings"

devenv /ResetSettings CSharp

devenv /NoSplash /ResetSettings General /Command Exit 
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../environment-settings.md)
- [Visual Studio ıde 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
