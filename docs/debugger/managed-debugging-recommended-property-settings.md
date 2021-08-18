---
title: C#, VB için önerilen hata ayıklayıcı özellik ayarları | Microsoft Docs
description: Tüm yönetilen hata ayıklama için aynı olması gereken derleme ve derleme özellik ayarlarına bakın. Diğer ayarlar proje türüne göre değişiklik gösterebilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 780838f02ea605329d3ff90a6d4f8ded6e7ce326
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030769"
---
# <a name="managed-debugging-recommended-property-settings"></a>Yönetilen Hata Ayıklama: Önerilen Özellik Ayarları
Tüm yönetilen hata ayıklama senaryoları için bazı özellikler aynı şekilde ayarlanmalıdır.

 Aşağıdaki tablolarda önerilen özellik ayarları görüntülenir.

 burada listelenmeyen Ayarlar, farklı yönetilen proje türleri arasında farklılık gösterebilir. örneğin, **başlatma eylemi** bir proje Windows Forms bir projede farklı şekilde ayarlanır [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Build (C#) veya Compile (Visual Basic) sekmesindeki yapılandırma özellikleri

|**Özellik Adı**|**Ayar**|
|-----------------------|-----------------|
|**Hata ayıklama sabiti tanımla**|C# ve F #: onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanızın hata ayıklama sınıfını kullanmasını sağlar.|
|**Izleme sabitini tanımlama**|C# ve F #: onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanızın Trace sınıfını kullanmasını sağlar.|
|**Kodu iyileştirme**|C#, F # ve Visual Basic: false olarak ayarlanır. Üretilen yönergeler doğrudan kaynak kodunuza karşılık gelmediğinden, iyileştirilmiş kodun hata ayıklama işlemi daha zordur. Programınızın yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata olduğunu fark ederseniz, bu ayarı açabilirsiniz, ancak **ayrıştırma** penceresinde gösterilen kodun, kod düzenleyicisinde görerle eşleşmeyen en iyileştirilmiş kaynaktan oluşturulduğunu unutmayın. İyileştirilmiş kodda hata ayıklamak için Yalnızca kendi kodum kapatmanız gerekir. (Bkz. [yalnızca kendi kodum adımlamayı kısıtla](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> daha fazla bilgi için bkz. [C# hata ayıklama yapılandırmaları için Project Ayarlar](../debugger/project-settings-for-csharp-debug-configurations.md) veya [Visual Basic hata ayıklama yapılandırması için Project Ayarlar](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|
|**Çıkış yolu**|Bin\Debug olarak ayarlayın \\ .|
|**Gelişmiş derleme seçenekleri**|Visual Basic Yalnızca. Aşağıdaki tabloda açıklanan Gelişmiş özellikleri ayarlamak için **Gelişmiş** ' e tıklayın.|

### <a name="advanced-compiler-settings-dialog-box"></a>Gelişmiş Derleyici Ayarları iletişim kutusu

|**Özellik Adı**|**Ayar**|
|-----------------------|-----------------|
|**İyileştirmeleri etkinleştir**|Önceki tablodaki **kodu en iyileştirme** seçeneğinde belirtilen nedenler için false olarak ayarlayın.|
|**Hata ayıklama bilgileri oluştur**|Derleme sırasında/DEBUG bayrağının ayarlanmış olmasını sağlamak için bu onay kutusunu işaretleyin ve bu, hata ayıklamayı kolaylaştırmak için gereken bilgileri oluşturur.|
|**Hata ayıklama sabiti tanımla**|`DEBUG`Uygulamanızın sınıfını kullanmasını sağlayan sabiti tanımlamak için bu onay kutusunu seçin <xref:System.Diagnostics.Debug> .|
|**Izleme sabitini tanımlama**|`TRACE`Uygulamanızın sınıfını kullanmasını sağlayan sabiti tanımlamak için bu onay kutusunu seçin <xref:System.Diagnostics.Trace> .|

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)