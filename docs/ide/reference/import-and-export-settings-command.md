---
description: Visual Studio ayarlarını içeri aktarır, dışarı aktarır veya sıfırlar. vssettings dosya uzantısı
title: Ayarları İçeri ve Dışarı Aktar komutu
ms.date: 05/28/2021
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dba50cf598c3c74f6c9407fbef5d55f938941a11
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687642"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Ayarları içeri ve dışarı aktar komutu (. vssettings dosyası)

Visual Studio ayarlar dosyasını içeri aktarır, dışarı aktarır veya sıfırlar `.vssettings` .

Dosyanın şeması açık. En yaygın olarak, şema her kategorinin bir etiket olduğu bir XML yapısına uyar ve bu, kendisini alt kategori etiketleri içerebilir. Bu alt kategori etiketleri, özellik değeri etiketleri içerebilir. Çoğu paket ortak yapıyı kullandığından, Visual Studio 'daki herhangi bir paket, tarafından seçtiği şemayı kullanarak rastgele XML 'yi dosyaya katkıda bulunabilir.

## <a name="syntax"></a>Syntax

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Anahtarlar

/Export`filename`

İsteğe bağlı. Geçerli ayarları belirtilen dosyaya dışa aktarır.

/import`filename`

İsteğe bağlı. Belirtilen dosyadaki ayarları içeri aktarır.

/Reset süpürmeden

İsteğe bağlı. Geçerli ayarları sıfırlar.

## <a name="remarks"></a>Açıklamalar

Bu komutu hiçbir anahtar olmadan çalıştırmak, **Ayarları içeri ve dışarı aktarma** Sihirbazı 'nı açar. Daha fazla bilgi için bkz. ayarlarınızı ve [ortam ayarlarınızı](../environment-settings.md) [eşitler](../synchronized-settings-in-visual-studio.md) .

## <a name="example"></a>Örnek

Aşağıdaki komut geçerli ayarları dosyaya dışa aktarır `MyFile.vssettings` :

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```



## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../../ide/environment-settings.md)
- [Ayarlarınızı eşitler](../../ide/synchronized-settings-in-visual-studio.md)
- [Visual Studio IDE 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
