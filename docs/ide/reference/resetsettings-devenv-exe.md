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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593869"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Visual Studio varsayılan ayarlarını geri yükler ve Visual Studio IDE'yi otomatik olarak başlatın. Bu anahtar, ayarları isteğe bağlı olarak belirli bir ayarlar dosyasına sıfırlar.

Varsayılan ayarlar Visual Studio ilk başlatıldığında seçilen profilden gelir.

> [!TIP]
> Tümleşik geliştirme ortamını (IDE) kullanarak ayarları sıfırlamayı öğrenmek [için, ayarları sıfırla'ya](../environment-settings.md#reset-settings)bakın.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *SettingsFile*

  İsteğe bağlı. Visual Studio'ya uygulanacak ayarlar dosyasının tam yolu ve adı.

- *VarsayılanKoleksiyonSpecifier*

  İsteğe bağlı. Geri yüklenir varsayılan bir ayar koleksiyonunu temsil eden bir belirtim. Tabloda listelenen varsayılan koleksiyon belirtecilerbirini seçin.

  | Varsayılan koleksiyon adı | Koleksiyon belirtimi |
  | --- | --- |
  | **Genel** | `General` |
  | **Javascript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Görsel C #** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Web Geliştirme** | `Web` |
  | **Web Geliştirme (Yalnızca Kod)** | `WebCode` |

## <a name="remarks"></a>Açıklamalar

*SettingsFile* belirtilmemişse, IDE varolan ayarları kullanarak açılır.

## <a name="example"></a>Örnek

İlk örnek, dosyada `MySettings.vssettings`depolanan ayarları uygular.

İkinci örnek, Visual C# varsayılan profilini geri yükler.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../environment-settings.md)
- [Visual Studio IDE'yi kişiselleştirin](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
