---
title: VSCT derleyici komut satırı bayrakları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71634a007019dd39e843ccc63af1c3188f778ea9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722024"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT Derleyici Komut Satırı Bayrakları
Visual Studio komut tablosu (VSCT) derleyicisi,. vsct dosyalarının başarıyla derlemesini sağlamak için komut satırı anahtarları sağlar.

## <a name="command-line-parameters"></a>Komut satırı parametreleri
 Temel VSCT yardımını bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **komut** penceresinden görüntülemek Için *Visual Studio SDK yükleme yolu*\VisualStudioIntegration\Tools\Bin\ klasörüne gidin ve şunu yazın:

```
vsct /?
```

 Bu değer şunu döndürür:

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

|Anahtar|Açıklama|
|------------|-----------------|
|-D|Ek tanımlanmış sembolleri belirtin.|
|-I|Dosya başvurularını çözümlerken kullanılması gereken ek ekleme yollarını belirtin.|
|-L|@No__t_0 kültür adını (örneğin, "en-US") belirtin.|
|-E|Belirtilen C# ad alanındaki nesneleri komut öğeleri için yay, ardından [c&#124;H&#124;N]: burada c= C#, H = C++ Header, N = Namespace. İçin C#ad alanı gereklidir.|
|-v|Ayrıntılı çıkış.|

 -L anahtarı, derleyiciye, verilen <xref:System.Globalization.CultureInfo> kültür adına karşılık gelen binary. CTO dosyasını oluşturmak için bir dize grubu seçmesini söyler. Belirtilen kültür adı,. vsct dosyasındaki bir veya daha fazla [dize öğesinin](../../extensibility/strings-element.md) dil özniteliğiyle eşleşmelidir. Bir dizeler öğesinin Language özniteliği yoksa, kapsayan [CommandTable öğesinden](../../extensibility/commandtable-element.md)devralınır.

 Bir. vsct dosyası birden çok dizeler öğesine sahip olabilir ve her birinin farklı bir Language özniteliği olabilir. Genelleştirme, VSCT derleyicisini birden çok kez çalıştırıp her kültür adı için-L anahtarını değiştirerek elde edilir.

 -L anahtarı tarafından verilen kültür adı herhangi bir dizeler öğesinin dil özniteliğiyle eşleşmiyorsa, derleyici, bölgeyi değil, dili eşleştirmeye çalışır. Örneğin, "en-US" bulunamazsa, derleyici bunun yerine "en" i dener. Bu, işletim sisteminin geçerli kültürünü deneyiyor. Bu, bulduğu ilk dizeler öğesini derler.

 -E anahtarı, komut tablosu tarafından kullanılan sembolleri içeren bir C stili üstbilgi dosyası oluşturmak veya komut sembolleri için nesneler içeren bir C# dosya oluşturmak için kullanılabilir.

 -D ve-I anahtarları, aynı ada sahip CL. exe C Önişlemci bayraklarının sözdizimine sahiptir. X = Y biçiminde olan-D tanımları, `Condition` özniteliklerde XML tabanlı \<Defined > testlerin genişletilmesi için kullanılır. -I içerme yolları \<Include >, \<Extern > ve \<Bitmap > dosya başvurularını çözümlemek için kullanılır. Daha fazla bilgi için bkz. [VSCT XML Schema başvurusu](../../extensibility/vsct-xml-schema-reference.md).

 VSCT derleyicisi daha önce oluşturulmuş bir ikili dosyayı da derlemeyi bozabilir. Bunu yapmak için, \<infile > için bir ikili dosya sağlayın.   İkili dosya VSCT derleyicisi tarafından üretildiyse, sembolleri zaten katıştırılır ve çıktının \<Symbols > bölümünde sembolik adlarla çıktı üretir. İkili dosya CTC derleyicisi tarafından üretildiyse, çıktı gerçek GUID 'Leri ve kimlikleri içerir. CTC. exe ' nin geçerli sürümleri tarafından üretilen *. ctsym dosyası ikili giriş dosyası ile aynı klasörsluysa, semboller bu dosyadan yüklenir ve çıkış için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)