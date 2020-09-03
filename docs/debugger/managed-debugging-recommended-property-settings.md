---
title: C#, VB için önerilen hata ayıklayıcı özellik ayarları | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 07c63a70de9d633ccd73d1d0d3bd23196d421543
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72731381"
---
# <a name="managed-debugging-recommended-property-settings"></a>Yönetilen Hata Ayıklama: Önerilen Özellik Ayarları
Tüm yönetilen hata ayıklama senaryoları için bazı özellikler aynı şekilde ayarlanmalıdır.

 Aşağıdaki tablolarda önerilen özellik ayarları görüntülenir.

 Burada listelenmeyen ayarlar, farklı yönetilen proje türleri arasında farklılık gösterebilir. Örneğin, **başlatma eylemi** bir proje Windows Forms bir projede farklı şekilde ayarlanır [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Build (C#) veya Compile (Visual Basic) sekmesindeki yapılandırma özellikleri

|**Özellik adı**|**Ayar**|
|-----------------------|-----------------|
|**Hata ayıklama sabiti tanımla**|C# ve F #: onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanızın hata ayıklama sınıfını kullanmasını sağlar.|
|**Izleme sabitini tanımlama**|C# ve F #: onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanızın Trace sınıfını kullanmasını sağlar.|
|**Kodu iyileştirme**|C#, F # ve Visual Basic: false olarak ayarlanır. Üretilen yönergeler doğrudan kaynak kodunuza karşılık gelmediğinden, iyileştirilmiş kodun hata ayıklama işlemi daha zordur. Programınızın yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata olduğunu fark ederseniz, bu ayarı açabilirsiniz, ancak **ayrıştırma** penceresinde gösterilen kodun, kod düzenleyicisinde görerle eşleşmeyen en iyileştirilmiş kaynaktan oluşturulduğunu unutmayın. İyileştirilmiş kodda hata ayıklamak için Yalnızca kendi kodum kapatmanız gerekir. (Bkz. [yalnızca kendi kodum adımlamayı kısıtla](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Daha fazla bilgi için bkz. [bir Visual Basic hata ayıklama yapılandırması Için](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) [C# hata ayıklama yapılandırmaları veya proje ayarları için proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md) .|
|**Çıkış yolu**|Bin\Debug olarak ayarlayın \\ .|
|**Gelişmiş derleme seçenekleri**|Yalnızca Visual Basic. Aşağıdaki tabloda açıklanan Gelişmiş özellikleri ayarlamak için **Gelişmiş** ' e tıklayın.|

### <a name="advanced-compiler-settings-dialog-box"></a>Gelişmiş Derleyici Ayarları iletişim kutusu

|**Özellik adı**|**Ayar**|
|-----------------------|-----------------|
|**İyileştirmeleri etkinleştir**|Önceki tablodaki **kodu en iyileştirme** seçeneğinde belirtilen nedenler için false olarak ayarlayın.|
|**Hata ayıklama bilgileri oluştur**|Derleme sırasında/DEBUG bayrağının ayarlanmış olmasını sağlamak için bu onay kutusunu işaretleyin ve bu, hata ayıklamayı kolaylaştırmak için gereken bilgileri oluşturur.|
|**Hata ayıklama sabiti tanımla**|`DEBUG`Uygulamanızın sınıfını kullanmasını sağlayan sabiti tanımlamak için bu onay kutusunu seçin <xref:System.Diagnostics.Debug> .|
|**Izleme sabitini tanımlama**|`TRACE`Uygulamanızın sınıfını kullanmasını sağlayan sabiti tanımlamak için bu onay kutusunu seçin <xref:System.Diagnostics.Trace> .|

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)