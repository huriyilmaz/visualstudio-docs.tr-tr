---
title: Gelişmiş Derleme Ayarları İletişim Kutusu (C#)
description: projenin gelişmiş derleme yapılandırma özelliklerini belirtmek için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/05/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 81ad77639a5ffb957c0de12069732e51103e8651f775469de2d1b8c5c5d6cde7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372796"
---
# <a name="advanced-build-settings-dialog-box-c"></a>gelişmiş derleme Ayarlar iletişim kutusu (C#)

projenin gelişmiş derleme yapılandırma özelliklerini belirtmek için **Project tasarımcısının** **gelişmiş derleme Ayarlar** iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca C# projeleri için geçerlidir.

## <a name="general"></a>Genel

Aşağıdaki seçenekler genel Gelişmiş ayarları ayarlamanıza olanak sağlar.

**Dil sürümü**

::: moniker range=">=vs-2019"

Bir projenin hedef çerçevesine göre varsayılan dil sürümünün nasıl seçildiği hakkında bilgi sağlayan [/langversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)bağlantıları.

::: moniker-end

::: moniker range="vs-2017"

Kullanılacak dilin sürümünü belirtir. Özellik kümesi her sürümde farklıdır, bu nedenle derleyicinin uygulanan özelliklerin yalnızca bir alt kümesine izin vermeye zorlamak veya yalnızca var olan bir standartta uyumlu özellikleri etkinleştirmek için bu seçenek kullanılabilir.

Varsayılan değer C# 7,0 ' dir.

::: moniker-end

**İç derleyici hata bildirimi**

Derleyici hatalarının Microsoft 'a raporlanıp raporlanmayacağını belirtir. **İstem** olarak ayarlandıysa (varsayılan), iç derleyici hatası oluşursa, Microsoft 'a elektronik bir hata raporu gönderme seçeneği sunarak bir istem alırsınız. **Send** olarak ayarlandıysa, otomatik olarak bir hata raporu gönderilir. **Sıraya** ayarlandıysa, hata raporları sıraya alınır. **None** olarak ayarlanırsa, hata yalnızca derleyicinin metin çıkışında bildirilir. Daha fazla bilgi için bkz. [/errorreport (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Aritmetik taşma/yetersiz kalması için denetle**

[Checked](/dotnet/csharp/language-reference/keywords/checked) veya [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) anahtar kelimelerinde bulunmayan ve veri türü aralığının dışında bir değer elde eden bir tamsayı aritmetik ifadesinin çalışma zamanı özel durumuna neden olup olmayacağını belirtir. Daha fazla bilgi için bkz. [/checked (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Başvuruya mscorlib.dll**

mscorlib.dll, tüm ad alanını tanımlayarak, programınıza içeri aktarılmayacağını belirtir <xref:System> . Kendi ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu kutuyu işaretleyin <xref:System> . Daha fazla bilgi için bkz. [/nostdlib (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Çıktı

Aşağıdaki seçenekler gelişmiş çıkış seçeneklerini belirtmenizi sağlar.

**Hata ayıklama bilgileri**

Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz. [bir görüntüyü hata ayıklamayı kolaylaştırın](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). Bu ayar aşağıdaki seçeneklere sahiptir:

- **yok**

   Hata ayıklama bilgilerinin üretilmeyecek olduğunu belirtir.

- **tümünü**

   Çalışan programa hata ayıklayıcı iliştirmesini sağlar.

- **pdbonly**

   Program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamasına izin verir, ancak çalışan program hata ayıklayıcıya eklendiğinde yalnızca assembler görüntülenir.

- **ın**

   Bir oluşturur. PDB dosyası, başka araçlar, özellikle hata ayıklayıcılar, ana yürütülebilir dosyada bulunan ve nasıl üretildiği hakkında bilgi sağlayan, platforma özgü olmayan taşınabilir bir sembol dosyası. Daha fazla bilgi için bkz. [TAŞINABILIR pdb](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) .

- **eklenen**

   Taşınabilir sembol bilgilerini derlemeye gömer. Dış değil. PDB dosyası üretildi.

Daha fazla bilgi için bkz. [/Debug (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Dosya hizalaması**

Çıkış dosyasındaki bölümlerin boyutunu belirtir. Geçerli değerler **512**, **1024**, **2048**, **4096** ve **8192**. Bu değerler bayt cinsinden ölçülür. Her bölüm, çıkış dosyasının boyutunu etkileyen bu değerin birden çok katı olan bir sınıra göre hizalanacaktır. Daha fazla bilgi için bkz. [/filealign (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Kitaplık temel adresi**

DLL 'nin yükleneceği tercih edilen temel adresi belirtir. bir DLL için varsayılan temel adres .NET Framework ortak dil çalışma zamanı tarafından ayarlanır. Daha fazla bilgi için bkz. [/BaseAddress (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](/dotnet/csharp/language-reference/compiler-options/index)
- [yapı sayfası, Project tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md)
