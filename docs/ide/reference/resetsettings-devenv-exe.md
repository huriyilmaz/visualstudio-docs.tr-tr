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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e523738ff23b40c80b5df21d90b582d94c59087f
ms.sourcegitcommit: a8031c1387d2090129ed33e063744f9f31653dcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2021
ms.locfileid: "110724544"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Visual Studio varsayılan ayarlarını geri yükler ve Visual Studio IDE 'yi otomatik olarak başlatır. Bu anahtar isteğe bağlı olarak ayarları belirtilen ayarlar dosyasına () sıfırlar `*.vssettings` .

Varsayılan ayarlar, Visual Studio ilk kez başlatıldığında seçili olan profilden gelir.

> [!TIP]
> Tümleşik geliştirme ortamı (IDE) kullanarak ayarları sıfırlama hakkında bilgi edinmek için bkz. [ayarları sıfırlama](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Söz dizimi

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SettingsFile*

  İsteğe bağlı. `.vssettings`Visual Studio 'ya uygulanacak dosyanın tam yolu ve adı.

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

Üçüncü örnek, ayarları uyguladıktan sonra Visual Studio 'Yu da kapatacak. Ekleme yapabilirsiniz `/Command "File.Exit"` .

```shell
devenv /ResetSettings "%USERPROFILE%\MySettings.vssettings"

devenv /ResetSettings CSharp

devenv /NoSplash /ResetSettings General /Command Exit 
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../environment-settings.md)
- [Visual Studio IDE 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
