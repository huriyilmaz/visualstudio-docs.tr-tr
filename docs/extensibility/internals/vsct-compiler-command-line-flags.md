---
title: VSCT Derleyici Komut Satırı Bayrakları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703963"
---
# <a name="vsct-compiler-command-line-flags"></a>VSCT Derleyici Komut Satırı Bayrakları
Visual Studio Komut Tablosu (VSCT) derleyicisi .vsct dosyalarının başarılı bir şekilde derlemesini sağlamak için komut satırı anahtarları sağlar.

## <a name="command-line-parameters"></a>Komut Satırı Parametreleri
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Komut** penceresinden temel VSCT yardımını görüntülemek için *Visual Studio SDK yükleme yoluna*\VisualStudioIntegration\Tools\Bin\ klasörüne gidin ve yazın:

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
> - (tire) ve / (ileri eğik çizgi) karakterleri komut satırı parametrelerini belirtmek için kabul edilen gösterimdir.

 Kabul edilebilir bayraklar ve ne anlama geldiğini aşağıdaki gibidir.

|Anahtar|Açıklama|
|------------|-----------------|
|-D|Tanımlanmış ek semboller belirtin.|
|-I|Dosya başvurularını çözerken kullanılması gereken ek dahil yolları belirtin.|
|-L|<xref:System.Globalization.CultureInfo> Kültür adını belirtin, örneğin "en-US".|
|-E|Komut öğeleri için belirtilen ad alanına C# nesneleri yonu, ardından [C&#124;H&#124;N]:*dosya adı*nerede C = C#, H = C++ üstbilgi, N = namespace. C# için ad alanı gereklidir.|
|-v|Verbose çıkışı.|

 -L anahtarı derleyiciye, verilen <xref:System.Globalization.CultureInfo> kültür adına karşılık gelen ikili .cto dosyasını oluşturmak için bir dize grubu seçmesini bildirir. Belirtilen kültür adı,.vsct dosyasındaki bir veya daha fazla [Strings Öğesinin](../../extensibility/strings-element.md) Dil özniteliğiyle eşleşmelidir. Bir Strings öğesi nin Dil özniteliği yoksa, içeren [CommandTable Öğesi'nden](../../extensibility/commandtable-element.md)devralır.

 Bir .vsct dosyasında birden çok String öğesi olabilir ve her birinin farklı bir Dil özniteliği olabilir. Küreselleşme, VSCT derleyicisinin birden çok kez çalıştırılması ve her kültür adı için -L anahtarının değiştirilmesiyle sağlanır.

 -L anahtarı tarafından verilen kültür adı, herhangi bir Strings öğesinin Dil özniteliğiyle eşleşmiyorsa, derleyici bölgeyle değil, dile eşleşmeye çalışır. Örneğin, "en-US" bulunamıyorsa, derleyici bunun yerine "en" dener. Aksi takdirde, işletim sisteminin geçerli kültürünü deneyecektir. Aksi takdirde, bulduğu ilk Strings öğesini derler.

 -E anahtarı, komut tablosu tarafından kullanılan sembolleri içeren C stili bir üstbilgi dosyası yaçmak veya komut sembolleri için nesneler içeren bir C# dosyası yontmak için kullanılabilir.

 -D ve-I anahtarları, aynı ada sahip Cl.exe C önişlemci bayraklarının sözdizimine sahiptir. -X=Y biçimine sahip D tanımları, XML tabanlı \<Tanımlı>'nin özniteliklerinin genişletilmesinde `Condition` kullanılır. -Ben>, \< \<Extern> ve \<Bitmap> dosya başvuruları dahil çözmek için kullanılan yolları içerir. Daha fazla bilgi için [VSCT XML Şema Başvurusu'na](../../extensibility/vsct-xml-schema-reference.md)bakın.

 VSCT derleyicisi, önceden oluşturulmuş bir ikili dosyayı da derleyebilir. Bunu yapmak için, dosya \<> için ikili bir dosya kaynağı.   İkili dosya VSCT derleyicisi tarafından üretilmiştirsa, sembolleri zaten gömülü olacak ve \<çıktının Semboller> bölümünde sembolik adlarla çıktı üretecektir. İkili CTC derleyicisi tarafından üretildiyse, çıktı gerçek GUID'leri ve dislerini içerir. Ctc.exe'nin geçerli sürümleri tarafından üretilen *.ctsym dosyası ikili giriş dosyasıyla aynı klasördeyse, semboller bu dosyadan yüklenir ve çıktı için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
