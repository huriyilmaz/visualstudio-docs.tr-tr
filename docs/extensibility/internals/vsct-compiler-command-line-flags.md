---
title: VSCT derleyicisi Command-Line bayrakları | Microsoft Docs
description: Visual Studio komut tablosu derleyicisi,. vsct dosyalarının başarıyla derlemesini sağlamak için komut satırı seçenekleri sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 53e50e408166eb2d2e1545549cdd6c72018c9553
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938791"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT Derleyici Komut Satırı Bayrakları
Visual Studio komut tablosu (VSCT) derleyicisi,. vsct dosyalarının başarıyla derlemesini sağlamak için komut satırı anahtarları sağlar.

## <a name="command-line-parameters"></a>Komut satırı parametreleri
 Temel VSCT yardımını bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **komut** penceresinden görüntülemek IÇIN *Visual Studio SDK yükleme yolu*\VisualStudioIntegration\Tools\Bin\ klasörüne gidin ve şunu yazın:

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
> -(Dash) ve/(eğik çizgi) karakterleri, komut satırı parametrelerini belirten kabul edilen simgedir.

 Kabul edilebilir bayraklar ve anlamları aşağıda verilmiştir.

|Anahtar|Description|
|------------|-----------------|
|-D|Ek tanımlanmış sembolleri belirtin.|
|-I|Dosya başvurularını çözümlerken kullanılması gereken ek ekleme yollarını belirtin.|
|-L|<xref:System.Globalization.CultureInfo>Kültür adını (örneğin, "en-US") belirtin.|
|-E|C# nesnelerini, komut öğeleri için belirtilen ad alanında, izleyen [C&#124;H&#124;N]:*filename* WHERE C = C#, H = C++ üstbilgisi, N = Namespace. C# için ad alanı gereklidir.|
|-v|Ayrıntılı çıkış.|

 -L anahtarı derleyiciye, belirtilen kültür adına karşılık gelen binary. CTO dosyasını oluşturmak için bir dize grubu seçmesini söyler <xref:System.Globalization.CultureInfo> . Belirtilen kültür adı,. vsct dosyasındaki bir veya daha fazla [dize öğesinin](../../extensibility/strings-element.md) dil özniteliğiyle eşleşmelidir. Bir dizeler öğesinin Language özniteliği yoksa, kapsayan [CommandTable öğesinden](../../extensibility/commandtable-element.md)devralınır.

 Bir. vsct dosyası birden çok dizeler öğesine sahip olabilir ve her birinin farklı bir Language özniteliği olabilir. Genelleştirme, VSCT derleyicisini birden çok kez çalıştırıp her kültür adı için-L anahtarını değiştirerek elde edilir.

 -L anahtarı tarafından verilen kültür adı herhangi bir dizeler öğesinin dil özniteliğiyle eşleşmiyorsa, derleyici, bölgeyi değil, dili eşleştirmeye çalışır. Örneğin, "en-US" bulunamazsa, derleyici bunun yerine "en" i dener. Bu, işletim sisteminin geçerli kültürünü deneyiyor. Bu, bulduğu ilk dizeler öğesini derler.

 -E anahtarı, komut tablosu tarafından kullanılan sembolleri içeren C stili bir üst bilgi dosyasını veya komut sembolleri için nesneleri içeren bir C# dosyası yayarak kullanılabilir.

 -D ve-I anahtarları aynı ada sahip Cl.exe C Önişlemci bayraklarının sözdizimine sahiptir. X = Y biçiminde olan-D tanımları, özniteliklerdeki XML tabanlı testlerin genişletilmesi için kullanılır \<Defined> `Condition` . -İ içerme yolları \<Include> , çözümlemek \<Extern> ve \<Bitmap> Dosya başvuruları için kullanılır. Daha fazla bilgi için bkz. [VSCT XML Schema başvurusu](../../extensibility/vsct-xml-schema-reference.md).

 VSCT derleyicisi daha önce oluşturulmuş bir ikili dosyayı da derlemeyi bozabilir. Bunu yapmak için, için bir ikili dosya sağlayın \<infile> .   İkili dosya VSCT derleyicisi tarafından üretildiyse, sembolleri zaten katıştırılır ve çıktının bir bölümünde sembolik adlarla çıktı üretir \<Symbols> . İkili dosya CTC derleyicisi tarafından üretildiyse, çıktı gerçek GUID 'Leri ve kimlikleri içerir. Geçerli Ctc.exe sürümleri tarafından üretilen *. ctsyd dosyası ikili giriş dosyasıyla aynı klasörsluysa, semboller bu dosyadan yüklenir ve çıkış için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
