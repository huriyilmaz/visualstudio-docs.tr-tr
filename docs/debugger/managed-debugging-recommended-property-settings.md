---
title: C#, VB için önerilen hata ayıklayıcısı özellik ayarları | Microsoft Docs
description: Tüm yönetilen hata ayıklama için aynı olması gereken derleme ve derleme özelliği ayarlarına bakın. Diğer ayarlar proje türüne göre değişiklik gösterebilir.
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
ms.workload:
- dotnet
ms.openlocfilehash: c2262194dbb6a8f4b0a47b4fcfc7f9f696c60167
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390404"
---
# <a name="managed-debugging-recommended-property-settings"></a>Yönetilen Hata Ayıklama: Önerilen Özellik Ayarları
Belirli özellikler tüm yönetilen hata ayıklama senaryolarında aynı şekilde ayarlayıcıdır.

 Aşağıdaki tablolarda önerilen özellik ayarları görüntülenir.

 Burada listelenmiyor ayarlar farklı yönetilen proje türleri arasında değişiklik gösterebilir. Örneğin, **Başlangıç Eylemi** bir proje içinde bir Windows Forms projeden farklı şekilde [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ayarlanır.

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Derleme (C#) veya Derleme (Visual Basic) sekmesindeki Yapılandırma Özellikleri

|**Özellik Adı**|**Ayar**|
|-----------------------|-----------------|
|**DEBUG sabiti tanımlama**|C# ve F#: Onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanın Hata Ayıklama sınıfını kullanmalarını sağlar.|
|**TRACE sabiti tanımlama**|C# ve F#: Onay kutusunu işaretli olarak ayarlayın. Bu, uygulamanın Trace sınıfını kullanmalarını sağlar.|
|**Kodu iyileştirme**|C#, F# ve Visual Basic: False olarak ayarlayın. İyileştirilmiş kodun hata ayıklaması zordur çünkü oluşturulan yönergeler doğrudan kaynak kodunuzla ilgili değildir. Programda yalnızca iyileştirilmiş kodda görünen bir hata olduğunu bulursanız, bu ayarı açabilirsiniz, ancak **Disassembly** penceresinde gösterilen kodun Kod Düzenleyicisi'nde gördüğünüzle eşleşmeyabilecek iyileştirilmiş kaynaktan oluşturulmuş olduğunu unutmayın. İyileştirilmiş kodda hata ayıklamak için, Yalnızca kendi kodum. [(Bkz. Adımlama ile Yalnızca kendi kodum).](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)<br /><br /> Daha fazla bilgi için [bkz. C#](../debugger/project-settings-for-csharp-debug-configurations.md) Hata Ayıklama Yapılandırmaları için Proje Ayarları veya Hata [Ayıklama Yapılandırması Visual Basic Proje Ayarları.](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)|
|**Çıkış yolu**|bin\Debug olarak \\ ayarlayın.|
|**Gelişmiş Derleme Seçenekleri**|Visual Basic'e göre. Aşağıdaki **tabloda** açıklanan gelişmiş özellikleri ayarlamak için Gelişmiş'e tıklayın.|

### <a name="advanced-compiler-settings-dialog-box"></a>Gelişmiş Derleyici Ayarları iletişim kutusu

|**Özellik Adı**|**Ayar**|
|-----------------------|-----------------|
|**İyileştirmeleri etkinleştirme**|Yukarıdaki tabloda yer alan Kodu en iyi duruma **getirme seçeneğinde belirtilen** nedenlerle false olarak ayarlayın.|
|**Hata ayıklama bilgileri oluşturma**|Derleme sırasında /DEBUG bayrağının ayarlanmasına neden olmak için bu onay kutusunu seçin. Bu, hata ayıklamayı kolaylaştırmak için gereken bilgileri üretir.|
|**DEBUG sabiti tanımlama**|Sabiti tanımlamak için bu onay `DEBUG` kutusunu seçin. Bu, uygulamanın sınıfını kullanmalarını <xref:System.Diagnostics.Debug> sağlar.|
|**TRACE sabiti tanımlama**|Sabiti tanımlamak için bu onay `TRACE` kutusunu seçin. Bu, uygulamanın sınıfını kullanmalarını <xref:System.Diagnostics.Trace> sağlar.|

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)