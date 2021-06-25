---
title: VSCT Derleyicisi Command-Line Flags | Microsoft Docs
description: Komut Visual Studio derleyicisi, .vsct dosyalarının başarıyla derlenmesi için komut satırı seçenekleri sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ce83df56e1bcfad50fe71da31291b5c43b26c47a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898905"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT Derleyici Komut Satırı Bayrakları
Visual Studio Tablosu (VSCT) derleyicisi, .vsct dosyalarının başarıyla derlenmesi için komut satırı anahtarları sağlar.

## <a name="command-line-parameters"></a>Komut Satırı Parametreleri
 Komut penceresinden temel VSCT yardımını görüntülemek için Visual Studio SDK yükleme yolu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  \VisualStudioIntegration\Tools\Bin\ klasörüne gidin ve şunları yazın: 

```
vsct /?
```

 Şunu döndürür:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> Komut satırı parametrelerinin belirtimleri için ( tire) ve / (eğik çizgi) karakterlerinin her ikisi de kabul edilir.

 Kabul edilebilir bayraklar ve bunların anlamı aşağıdaki gibidir.

|Anahtar|Açıklama|
|------------|-----------------|
|-D|Tanımlanmış ek sembolleri belirtin.|
|-I|Dosya başvurularını çözümlerken kullanılacak ek dahil yolları belirtir.|
|-L|Kültür <xref:System.Globalization.CultureInfo> adını belirtin, örneğin "en-US".|
|-E|Komut öğeleri için belirtilen ad alanı içinde C# nesnelerini yayma ve ardından [C&#124;H&#124;N]:*dosya adı;* burada C = C#, H = C++ üst bilgisi, N = ad alanı. Ad alanı C# için gereklidir.|
|-v|Ayrıntılı çıktı.|

 -L anahtarı, derleyiciye verilen kültür adına karşılık gelen ikili .cto dosyasını üretmek için bir dize grubu <xref:System.Globalization.CultureInfo> seçmesi talimatı sağlar. Belirtilen kültür adı, .vsct dosyasındaki bir veya daha fazla [Dize Öğesinin Language](../../extensibility/strings-element.md) özniteliğiyle eşleşmeli. Bir Strings öğesinin Language özniteliği yoksa, içeren CommandTable Öğesinden [devralınmıştır.](../../extensibility/commandtable-element.md)

 Bir .vsct dosyasında birden çok Dize öğe olabilir ve her biri farklı bir Dil özniteliğine sahip olabilir. Genelleştirme, VSCT derleyicisini birden çok kez çalıştırarak ve her kültür adı için -L anahtarını değiştirerek elde edilir.

 -L anahtarı tarafından verilen kültür adı herhangi bir Dize öğesinin Language özniteliğiyle eşlen yoksa, derleyici bölgeyle değil dille eşleşmeyi dener. Örneğin, "en-US" bulunamazsa, derleyici bunun yerine "en" dener. Başarısız olursa, işletim sisteminin geçerli kültürünü dener. Bu başarısız oluyorsa bulduğu ilk Dizeler öğesini derler.

 -E anahtarı, komut tablosu tarafından kullanılan sembolleri içeren bir C stili üst bilgi dosyası ya da komut sembolleri için nesneleri içeren bir C# dosyası yayan için kullanılabilir.

 -D ve -I anahtarları, aynı adı Cl.exe C önişlemci bayraklarının söz dizimlerini içerir. Özniteliklerde XML tabanlı testlerin genişletilmesi için X=Y biçimine sahip -D \<Defined> `Condition` tanımları kullanılır. -I include yolları , ve dosya \<Include> \<Extern> başvurularını \<Bitmap> çözümlemek için kullanılır. Daha fazla bilgi için bkz. [VSCT XML Şema Başvurusu.](../../extensibility/vsct-xml-schema-reference.md)

 VSCT derleyicisi, daha önce derlenmiş bir ikili dosyayı da koda dönüştürür. Bunu yapmak için, için bir ikili dosya \<infile> sağlar.   İkili dosya VSCT derleyicisi tarafından üretilmişse, simgeleri zaten eklenmiş olur ve çıkışın bir bölümünde sembolik adlarla \<Symbols> çıkış üretir. İkili CTC derleyicisi tarafından üretilmişse, çıkış gerçek GUID'leri ve kimlikleri içerir. Ctc.exe'nin geçerli sürümleri tarafından üretilen *.ctsym dosyası ikili giriş dosyasıyla aynı klasörde yer aldı ise semboller bu dosyadan yüklenir ve çıkış için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
