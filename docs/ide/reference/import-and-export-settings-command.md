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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: eb9c82d02a708d8aec49a620b836da6761594733c67b52cb04c1e4d7adfe62ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372471"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Ayarlar komutu (. vssettings dosyası) içeri ve dışarı aktarma

Visual Studio ayarları dosyasını içeri aktarır, dışarı aktarır veya sıfırlar `.vssettings` .

Dosyanın şeması açık. En yaygın olarak, şema her kategorinin bir etiket olduğu bir XML yapısına uyar ve bu, kendisini alt kategori etiketleri içerebilir. Bu alt kategori etiketleri, özellik değeri etiketleri içerebilir. çoğu paket ortak yapıyı kullandığından, Visual Studio her bir paket, seçtiği şemayı içeren bir dosyaya rastgele XML katkıda bulunabilir.

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

bu komutu hiçbir anahtar olmadan çalıştırmak, **Ayarlar içeri ve dışarı aktarma** sihirbazı 'nı açar. Daha fazla bilgi için bkz. ayarlarınızı ve [ortam ayarlarınızı](../environment-settings.md) [eşitler](../synchronized-settings-in-visual-studio.md) .

## <a name="example"></a>Örnek

Aşağıdaki komut geçerli ayarları dosyaya dışa aktarır `MyFile.vssettings` :

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```



## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../../ide/environment-settings.md)
- [Ayarlarınızı eşitler](../../ide/synchronized-settings-in-visual-studio.md)
- [Visual Studio ıde 'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
