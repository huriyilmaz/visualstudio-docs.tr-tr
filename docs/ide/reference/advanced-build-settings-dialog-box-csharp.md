---
title: Gelişmiş Derleme Ayarları İletişim Kutusu (C#)
ms.date: 08/05/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f25f9d96cd8de8dcb140c79c7dfb3a7a5981986c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595858"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Gelişmiş Yapı Ayarları iletişim kutusu (C#)

Projenin **gelişmiş yapı** yapılandırma özelliklerini belirtmek için **Project Designer'ın** Gelişmiş Yapı Ayarları iletişim kutusunu kullanın. Bu iletişim kutusu yalnızca C# projeleri için geçerlidir.

## <a name="general"></a>Genel

Aşağıdaki seçenekler, genel gelişmiş ayarları ayarlamanızı sağlar.

**Dil Sürümü**

::: moniker range=">=vs-2019"

Varsayılan dil sürümünün projenin hedef çerçevesine göre nasıl seçildiği hakkında bilgi sağlayan [/langversion (C# derleyici seçenekleri)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)bağlantıları.

::: moniker-end

::: moniker range="vs-2017"

Kullanılacak dilin sürümünü belirtir. Özellik kümesi her sürümde farklıdır, bu nedenle bu seçenek derleyiciyi uygulanan özelliklerin yalnızca bir alt kümesine izin vermeye zorlamak veya yalnızca varolan bir standartla uyumlu özellikleri etkinleştirmek için kullanılabilir.

Varsayılan değer C# 7.0'dır.

::: moniker-end

**İç Derleyici Hata Raporlama**

Derleyici hatalarını Microsoft'a bildirip bildirmeyin ilerler. **İstem (varsayılan)** olarak ayarlanmışsa, bir iç derleyici hatası oluşursa, microsoft'a elektronik olarak hata raporu gönderme seçeneği verir. **Göndermeye**ayarlanırsa, otomatik olarak bir hata raporu gönderilir. **Sıraya ayarlanırsa,** hata raporları sıraya alınır. **Hiçbiri**olarak ayarlanırsa, hata yalnızca derleyicinin metin çıktısında bildirilir. Daha fazla bilgi için bkz: [/errorreport (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Aritmetik taşma/taşma olup yok**

[Denetlenen](/dotnet/csharp/language-reference/keywords/checked) veya [işaretlenmemiş](/dotnet/csharp/language-reference/keywords/unchecked) anahtar kelimelerin kapsamında olmayan bir tamsayı aritmetik deyiminin veri türü aralığının dışında bir değerle sonuçlanıp sonuçlanmayacağını belirtir. Daha fazla bilgi için bkz/ [kontrol (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**mscorlib.dll referans etmeyin**

mscorlib.dll'nin programınıza alınıp alınmayacağını belirterek <xref:System> tüm ad alanını tanımlar. Kendi <xref:System> ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu kutuyu işaretleyin. Daha fazla bilgi için bkz: [/nostdlib (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Çıktı

Aşağıdaki seçenekler gelişmiş çıktı seçenekleri belirtmenizi sağlar.

**Hata Ayıklama Bilgileri**

Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. Bir uygulamanın hata ayıklama performansını yapılandırma hakkında bilgi için [bkz.](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug) Bu ayarın aşağıdaki seçenekleri vardır:

- **yok**

   Hata ayıklama bilgisi oluşturulmaması gerektiğini belirtir.

- **Tam**

   Çalışan programa hata ayıklama eklemeyi sağlar.

- **pdbonly**

   Program hata ayıklayıcıda başlatıldığında kaynak kodunun hata ayıklanmasına izin verir, ancak yalnızca çalışan program hata ayıklayıcıya eklendiğinde assembler görüntülenir.

- **Taşınabilir**

   Bir . PDB dosyası, diğer araçlar, özellikle hata ayıklayıcılar, ana yürütülebilir dosyada ne olduğu ve nasıl üretildiği hakkında bilgi sağlayan platforma özgü olmayan taşınabilir bir sembol dosyasıdır. Daha fazla bilgi için [Taşınabilir PDB'ye](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) bakın.

- **Katıştırılmış**

   Taşınabilir sembol bilgilerini derlemeye yerle bir eder. Harici yok. PDB dosyası üretilir.

Daha fazla bilgi için bkz: [/hata ayıklama (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Dosya Hizalama**

Çıktı dosyasındaki bölümlerin boyutunu belirtir. Geçerli değerler **512**, **1024**, **2048**, **4096**, ve **8192**. Bu değerler bayt cinsinden ölçülür. Her bölüm, çıktı dosyasının boyutunu etkileyen, bu değerin bir katı olan bir sınırüzerinde hizalanır. Daha fazla bilgi için bkz: [/filealign (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Kütüphane Taban Adresi**

DLL yüklemek için tercih edilen temel adresi belirtir. Bir DLL için varsayılan temel adres .NET Framework ortak dil çalışma süresi tarafından ayarlanır. Daha fazla bilgi için bkz: [/baseaddress (C# Derleyici Seçenekleri)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](/dotnet/csharp/language-reference/compiler-options/index)
- [Yapı sayfası, Proje Tasarımcısı (C#)](../../ide/reference/build-page-project-designer-csharp.md)
