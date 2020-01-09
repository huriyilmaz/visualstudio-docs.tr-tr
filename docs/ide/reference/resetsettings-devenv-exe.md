---
title: -ResetSettings (devenv.exe)
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
ms.openlocfilehash: eebcf2c6796723e51c3aefdb12575aa89779429f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593869"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Visual Studio varsayılan ayarlarını geri yükler ve Visual Studio IDE 'yi otomatik olarak başlatır. Bu anahtar isteğe bağlı olarak ayarları belirtilen ayarlar dosyasına sıfırlar.

Varsayılan ayarlar, Visual Studio ilk kez başlatıldığında seçili olan profilden gelir.

> [!TIP]
> Tümleşik geliştirme ortamı (IDE) kullanarak ayarları sıfırlama hakkında bilgi edinmek için bkz. [ayarları sıfırlama](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Sözdizimi

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Arguments

- *SettingsFile*

  İsteğe bağlı. Visual Studio 'ya uygulanacak ayarlar dosyasının tam yolu ve adı.

- *Defaultcollectionbelirleyicisi*

  İsteğe bağlı. Geri yüklenecek varsayılan ayar koleksiyonunu temsil eden bir tanımlayıcı. Tabloda listelenen varsayılan koleksiyon belirticilerden birini seçin.

  | Varsayılan koleksiyon adı | Koleksiyon Belirleyicisi |
  | --- | --- |
  | **Genel** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Web geliştirme** | `Web` |
  | **Web geliştirme (yalnızca kod)** | `WebCode` |

## <a name="remarks"></a>Açıklamalar

*SettingsFile* BELIRTILMEMIŞSE, IDE var olan ayarları kullanarak açılır.

## <a name="example"></a>Örnek

İlk örnek, `MySettings.vssettings`dosya içinde depolanan ayarları uygular.

İkinci örnek, görsel C# varsayılan profilini geri yükler.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../environment-settings.md)
- [Visual Studio IDE'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
