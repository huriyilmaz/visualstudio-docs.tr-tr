---
title: Ayarları İçeri ve Dışarı Aktar komutu
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0be61d8690c0605f6e7773efe02f5db351110f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658772"
---
# <a name="import-and-export-settings-command"></a>Ayarları İçeri ve Dışarı Aktar komutu

Visual Studio ayarlarını içeri aktarır, dışarı aktarır veya sıfırlar.

## <a name="syntax"></a>Sözdizimi

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Anahtarlar

/Export: `filename`

İsteğe bağlı. Geçerli ayarları belirtilen dosyaya dışa aktarır.

/import: `filename`

İsteğe bağlı. Belirtilen dosyadaki ayarları içeri aktarır.

/Reset süpürmeden

İsteğe bağlı. Geçerli ayarları sıfırlar.

## <a name="remarks"></a>Açıklamalar

Bu komutu hiçbir anahtar olmadan çalıştırmak, **Ayarları içeri ve dışarı aktarma** Sihirbazı 'nı açar. Daha fazla bilgi için bkz. ayarlarınızı ve [ortam ayarlarınızı](../environment-settings.md) [eşitler](../synchronized-settings-in-visual-studio.md) .

## <a name="example"></a>Örnek

Aşağıdaki komut, geçerli ayarları dosyaya `MyFile.vssettings` dışa aktarır:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../../ide/environment-settings.md)
- [Ayarlarınızı eşitler](../../ide/synchronized-settings-in-visual-studio.md)
- [Visual Studio IDE 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)