---
title: .NET Adlandırma Kuralları EditorConfig dosyaları için
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5c4115f4d63456e105fb4a6770fd1650938770d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588609"
---
# <a name="net-naming-conventions-for-editorconfig"></a>.NET, EditorConfig için adlandırma kuralları

Adlandırma kuralları, sınıflar, özellikler ve yöntemler gibi kod öğelerinin adlandırmasını içerir. Örneğin, ortak üyelerin büyük harfle karşılanabilmesi veya özel `_`alanların '. Bu kuralları bir [.editorconfig dosyasında](../ide/create-portable-custom-editor-options.md)belirterek uygulayabilirsiniz. Adlandırma kuralı ihlalleri, kuralınız için seçtiğiniz öneme bağlı olarak **Hata Listesi'nde** veya ad altında bir öneri olarak görünür. İhlalleri görmek için projeyi oluşturmaya gerek yoktur.

Her adlandırma kuralı için, aşağıda açıklanan özellikleri kullanarak, geçerli olduğu sembolleri, bir adlandırma stilini ve kuralı uygulamak için önem derecesini belirtmeniz gerekir. Özelliklerin sırası önemli değildir.

Başlamak için, kuralı tam olarak açıklamak için gereken özelliklerin her birinde kullanacağınız adlandırma kuralınız için bir başlık seçin. Örneğin, `public_members_must_be_capitalized` bir adlandırma kuralı için iyi, açıklayıcı bir addır. Bu sayfada, aşağıdaki bölümlerde **<namingRuleTitle\> ** olarak seçtiğiniz başlık belirtecektir.

## <a name="symbols"></a>Simgeleri

İlk olarak, adlandırma kuralını uygulamak için bir sembol grubu tanımlayın. Bu özellik aşağıdaki biçime sahiptir:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

`public_symbols` **<sembolÜndeki\> ** değeri açıklayıcı bir başlıkla değiştirerek sembol grubuna bir ad verin. Kuralın uygulandığı sembolleri (sembol türleri, erişilebilirlik düzeyleri ve değiştiriciler) açıklayan üç özellik adlarında **<sembolBaşlık\> ** değerini kullanırsınız.

### <a name="kinds-of-symbols"></a>Sembol türleri

Adlandırma kuralını uygulayacak sembollerin türünü açıklamak için aşağıdaki biçimde bir özellik belirtin:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

Aşağıdaki liste izin verilebilen değerleri gösterir ve bunları virgülle ayırarak birden çok değer belirtebilirsiniz.

- \*(tüm sembolleri belirtmek için bu değeri kullanın)
- ad alanı
- sınıf
- struct 
- arabirim
- enum
- özellik
- method
- alan
- event
- temsilci
- parametre
- type_parameter
- yerel
- local_function

### <a name="accessibility-levels-of-symbols"></a>Sembollerin erişilebilirlik düzeyleri

Adlandırma kuralının uygulanmasını istediğiniz sembollerin erişilebilirlik düzeylerini açıklamak için aşağıdaki biçimde bir özellik adı belirtin:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

Aşağıdaki liste izin verilebilen değerleri gösterir ve bunları virgülle ayırarak birden çok değer belirtebilirsiniz.

- \*(tüm erişilebilirlik düzeylerini belirtmek için bu değeri kullanın)
- public
- dahili veya arkadaş
- private
- protected
- korunan\_iç veya protected_friend
- özel\_korumalı
- yerel

   Erişilebilirlik `local` düzeyi, bir yöntem içinde tanımlanan simgeler için geçerlidir. Erişilebilirliği kodda belirtilemeyen semboller için adlandırma kuralları tanımlamak için yararlıdır. Örneğin, sabitler `applicable_accessibilities = local` için bir adlandırma kuralı`required_modifiers = const`(), kural yalnızca bir yöntem içinde tanımlanan sabitler için geçerlidir, bir türde tanımlananlar için değil.

   ```csharp
   class TypeName
   {
     // Constant defined in a type.
     const int X = 3;

     void Method()
     {
       // Constant defined in a method with "local" accessibility.
       const int Y = 4;
     }
   }
   ```

### <a name="symbol-modifiers-optional"></a>Sembol değiştiriciler (isteğe bağlı)

Adlandırma kuralının uygulanmasını istediğiniz sembollerin değiştiricilerini açıklamak için aşağıdaki biçimde bir özellik adı belirtin:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

Aşağıdaki liste izin verilebilen değerleri (virgülle ayrı birden çok değer) gösterir:

- `abstract` veya `must_inherit`
- `async`
- `const`
- `readonly`
- `static` veya `shared`

   > [!NOTE]
   > Bir `static` adlandırma kuralınız veya `shared` sembolleriniz varsa, `const` dolaylı olarak statik oldukları ndan sembollere de uygulanır. Adlandırma kuralının `static` sembollere `const` uygulanmasını istemiyorsanız, semboller için `const` ayrı bir adlandırma kuralı oluşturun.

Adlandırma kuralı, `required_modifiers` *''de* belirtilen tüm değiştiricilere sahip imzalarla eşleşir. Bu özelliği atlarsanız, boş bir listenin varsayılan değeri kullanılır, yani bir eşleşme için belirli bir değiştirici gerekmez. Bu, bir sembolün değiştiricilerinin bu kuralın uygulanıp uygulanmadığı üzerinde hiçbir etkisi olmadığı anlamına gelir.

> [!TIP]
> for `required_modifiers`için bir `*` değer belirtmeyin. Bunun yerine, `required_modifiers` sadece tamamen özelliği atlayın ve adlandırma kuralı değiştirici her türlü geçerli olacaktır.

## <a name="style"></a>Stil

Artık adlandırma kuralını uygulamak için semboller grubunu tanımladığınıza göre, adlandırma stilini tanımlayabilirsiniz. Bir stil, adın belirli bir önek veya belirli bir sonek olması veya addaki tek tek sözcüklerin belirli bir karakterle ayrılması olabilir. Büyük harf stili de belirtebilirsiniz. Stil özelliği aşağıdaki biçime sahiptir:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

`first_word_upper_case_style` **örneğin,<\> styleTitle** değerini açıklayıcı bir başlıkla değiştirerek stile bir ad verin. Adverme stilini açıklayan özellik adlarında **<styleTitle\> ** değerini kullanırsınız (önek, sonek, sözcük ayırıcı karakter ve büyük harf). Stilinizi açıklamak için bu özelliklerden birini veya birkaçını kullanın.

### <a name="require-a-prefix"></a>Önek gerektir

Sembol adlarının belirli karakterlerle başlaması gerektiğini belirtmek için şu özelliği kullanın:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Sonek gerektir

Sembol adlarının belirli karakterlerle sona ermesi gerektiğini belirtmek için şu özelliği kullanın:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Belirli bir sözcük ayırıcısı gerektirir

Sembol adlarında tek tek sözcüklerin belirli bir karakterle ayrılması gerektiğini belirtmek için şu özelliği kullanın:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Büyük harf stili gerektirme

Sembol adları için belirli bir büyük harf stili belirtmek için şu özelliği kullanın:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Bu özellik için izin verilebilen değerler şunlardır:

- pascal_case
- camel_case
- ilk\_word_upper
- tüm\_üst
- all_lower

> [!NOTE]
> Adlandırma stilinizin bir parçası olarak büyük harf stili belirtmeniz gerekir, aksi takdirde adlandırma stiliniz yoksayılabilir.

## <a name="severity"></a>Severity

Adlandırma kuralınızın ihlalinin önem derecesini açıklamak için aşağıdaki biçimde bir özellik belirtin:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

Aşağıdaki tablo, izin verilebilen önem değerlerini ve bunların ne anlama geldiğini gösterir:

Severity | Etki
------------ | -------------
yok | Kural tamamen bastırıldı.
refactoring veya sessiz | Bu stil izlenmiyorsa, kullanıcıya hiçbir şey göstermeyin; ancak, otomatik oluşturulan kod bu stili izler.
Öneri | Bu stil izlenmiyorsa, ilk iki karakterde temel nokta olarak kullanıcıya bir öneri olarak gösterin. Derleme zamanında hiçbir etkisi yoktur.
warning | Bu stil izlenmiyorsa, **Hata Listesinde**derleyici uyarısı gösterin.
error | Bu stil izlenmiyorsa, **Hata Listesinde**bir derleyici hatası gösterin.

> [!NOTE]
> Adlandırma kuralı ihlallerini görmek için projenizi oluşturmanız gerekmez. **Hata Listesi'nde** veya öneri olarak kod düzenlenirken görünürler.

## <a name="rule-order"></a>Kural sırası

::: moniker range="vs-2017"

Adlandırma kuralları, EditorConfig dosyasında en çok özelden en az özele doğru sıralanmalıdır. Uygulanabilecek ilk kural, uygulanan tek kuraldır. Ancak, aynı ada sahip birden çok kural *özelliği* varsa, bu ada sahip en son bulunan özellik önceliklidir. Daha fazla bilgi için [Dosya hiyerarşisi ve önceliği'ne](create-portable-custom-editor-options.md#file-hierarchy-and-precedence)bakın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 2019 sürüm 16.2'den başlayarak, bir EditorConfig dosyasında adlandırma kurallarının tanımlanma sırası önemli değildir. Bunun yerine, Visual Studio kuralların tanımına göre adlandırma kurallarını otomatik olarak emreder. [EditorConfig Dil Hizmeti uzantısı,](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) bir EditorConfig dosyasını analiz edebilir ve dosyadaki kural sıralayıcının çalışan zamanda derleyicinin kullanacağından farklı olduğu durumları bildirebilir.

Visual Studio'nun önceki bir sürümünü kullanıyorsanız, adlandırma kuralları EditorConfig dosyasında en özelden en az özele kadar sıralanmalıdır. Uygulanabilecek ilk kural, uygulanan tek kuraldır. Ancak, aynı ada sahip birden çok kural *özelliği* varsa, bu ada sahip en son bulunan özellik önceliklidir. Daha fazla bilgi için [Dosya hiyerarşisi ve önceliği'ne](create-portable-custom-editor-options.md#file-hierarchy-and-precedence)bakın.

::: moniker-end

## <a name="default-naming-styles"></a>Varsayılan adlandırma stilleri

Özel adlandırma kuralları belirtmezseniz, Visual Studio aşağıdaki varsayılan stilleri kullanır:

- Sınıflar, structs, sayısallaştırmalar, özellikleri ve `public`olaylar `private` `internal`için `protected`, `protected_internal` , , veya erişilebilirlik, varsayılan adlandırma stili Pascal durumda.

- , `public`, `private`, `internal` `protected`veya `protected_internal` erişilebilirlik ile arabirimler için, varsayılan adlandırma stili **I**gerekli bir öneki ile Pascal durumda .

## <a name="example"></a>Örnek

Aşağıdaki *.editorconfig* dosyası, ortak özelliklerin, yöntemlerin, alanların, olayların ve temsilcilerin büyük harfle yazılması gerektiğini belirten bir adlandırma kuralı içerir. Bu adlandırma kuralı, değerleri ayırmak için virgül kullanarak kural uygulamak için birden çok sembol türü belirtir dikkat edin.

```ini
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

Aşağıdaki ekran görüntüsü, bu adlandırma kuralının düzenleyicideki etkisini gösterir. İlk harfin büyük harfle yazılması olmadan iki ortak değişken adlandırılmıştır. Biri, `const`diğeri `readonly`. Adlandırma kuralı yalnızca semboller `readonly` için geçerli `readonly` olduğundan, yalnızca değişken bir adlandırma kuralı önerisi gösterir.

![Adlandırma kuralı önerisi](media/editorconfig-naming-rule-suggestion.png)

Şimdi ihlalin şiddetini şu `warning`şekilde değiştirelim:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Kod dosyanızı kapatıp yeniden açarsanız, öneriyi ad ihlali altında görmek yerine, Hata Listesinde yeşil bir dalgalı lık ve bir uyarı görürsünüz:

![Adlandırma kuralı uyarısı](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil kuralları](editorconfig-language-conventions.md)
- [Biçimlendirme kuralları](editorconfig-formatting-conventions.md)
- [Roslyn adlandırma kuralları](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Taşınabilir özel düzenleyici seçenekleri oluşturma](../ide/create-portable-custom-editor-options.md)
- [EditorConfig için .NET kodlama kuralı ayarları](editorconfig-code-style-settings-reference.md)
