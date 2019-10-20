---
title: EditorConfig dosyaları Için .NET adlandırma kuralları
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ff6c9885bd01a94cc36046faf71067e1fe9c17b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650910"
---
# <a name="net-naming-conventions-for-editorconfig"></a>EditorConfig için .NET adlandırma kuralları

Adlandırma kuralları sınıflar, Özellikler ve yöntemler gibi kod öğelerinin adlandırılmasına yardımcı olabilir. Örneğin, ortak üyelerin büyük harfle veya zaman uyumsuz yöntemlerin "Async" ile bitmesi gerektiğini belirtebilirsiniz. Bu kuralları bir [. editorconfig dosyasında](../ide/create-portable-custom-editor-options.md)belirterek uygulayabilirsiniz. Kural için seçtiğiniz önem derecesine bağlı olarak, adlandırma kuralı ihlalleri **hata listesi** veya ad altında bir öneri olarak görüntülenir. İhlalleri görmek için projeyi derlemek gerekmez.

Her adlandırma kuralı için, aşağıda açıklanan özellikleri kullanarak, uygulanan sembolleri, bir adlandırma stilini ve kuralı zorlamaya yönelik önem derecesini belirtmeniz gerekir. Özelliklerin sırası önemli değildir.

Başlamak için, kural için gereken her bir özelliklerde kullanacağınız adlandırma kuralınız için bir başlık seçin. Örneğin, `public_members_must_be_capitalized` bir adlandırma kuralı için iyi, açıklayıcı bir addır. Bu sayfa, aşağıdaki bölümlerde **< Namingrutatitle \>** olarak seçtiğiniz başlığa başvurur.

## <a name="symbols"></a>Simgeleri

İlk olarak, adlandırma kuralını uygulamak için bir sembol grubu belirler. Bu özellik aşağıdaki biçimdedir:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

**< symboltitle \>** değerini açıklayıcı bir başlıkla değiştirerek sembol grubuna bir ad verin, örneğin `public_symbols`. Kuralın hangi sembolleri uygulanacağını (sembol, erişilebilirlik düzeyi ve değiştirici türleri) açıklayan üç özellik adında **< symbolTitle \>** değerini kullanacaksınız.

### <a name="kinds-of-symbols"></a>Sembol türleri

Adlandırma kuralının uygulanacağı simge türünü belirlemek için, aşağıdaki biçimde bir özellik belirtin:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

Aşağıdaki liste, izin verilen değerleri gösterir ve birden fazla değeri virgülle ayırarak belirtebilirsiniz.

- \* (tüm sembolleri belirtmek için bu değeri kullanın)
- ad alanı
- sınıf
- struct
- arabirim
- enum
- özellik
- yöntemi
- alan
- olay
- temsilci
- parametre
- type_parameter
- yerel
- local_function

### <a name="accessibility-levels-of-symbols"></a>Simgelerin erişilebilirlik düzeyleri

Adlandırma kuralının uygulanmasını istediğiniz sembollerin erişilebilirlik düzeylerini belirlemek için, aşağıdaki biçimde bir özellik adı belirtin:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

Aşağıdaki liste, izin verilen değerleri gösterir ve birden fazla değeri virgülle ayırarak belirtebilirsiniz.

- \* (tüm erişilebilirlik düzeylerini belirtmek için bu değeri kullanın)
- public
- iç veya arkadaş
- private
- protected
- korumalı \_internal veya protected_friend
- Özel \_protected
- yerel

   @No__t_0 erişilebilirlik düzeyi bir yöntem içinde tanımlanan semboller için geçerlidir. Erişilebilirlik, kodda belirtime gibi semboller için adlandırma kuralları tanımlamak için faydalıdır. Örneğin, sabitler (`required_modifiers = const`) için bir adlandırma kuralında `applicable_accessibilities = local` belirtirseniz, kural yalnızca bir yöntemde tanımlanan ve bir tür içinde tanımlananlar için geçerlidir.

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

### <a name="symbol-modifiers-optional"></a>Sembol değiştiricileri (isteğe bağlı)

Adlandırma kuralının uygulanmasını istediğiniz sembollerin değiştiricilerini anlatmak için aşağıdaki biçimde bir özellik adı belirtin:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

Aşağıdaki liste, izin verilen değerleri gösterir (birden çok değeri virgülle ayırın):

- `abstract` veya `must_inherit`
- `async`
- `const`
- `readonly`
- `static` veya `shared`

   > [!NOTE]
   > @No__t_0 veya `shared` sembolleri için bir adlandırma kuralınız varsa, örtülü olarak statik olduklarından `const` sembollerine de uygulanır. @No__t_0 adlandırma kuralının `const` simgelere uygulanmasını istemiyorsanız `const` sembolleri için ayrı bir adlandırma kuralı oluşturun.

Adlandırma kuralı, `required_modifiers` ' de belirtilen *Tüm* değiştiricilere sahip imzalarla eşleşir. Bu özelliği atlarsanız, boş bir listenin varsayılan değeri kullanılır, diğer bir deyişle, eşleşme için belirli bir değiştirici gerekmez. Bu, sembolün değiştiricilerin bu kuralın uygulanıp uygulanmadığı üzerinde hiçbir etkisi olmayacağı anlamına gelir.

> [!TIP]
> @No__t_1 için `*` değeri belirtmeyin. Bunun yerine, `required_modifiers` özelliğini tamamen atlayın ve adlandırma kuralınız her türlü değiştirici için geçerlidir.

## <a name="style"></a>Stil

Adlandırma kuralını uygulamak için sembol grubunu tanımladığınıza göre, adlandırma stilini tanımlayabilirsiniz. Bir stil, adın belirli bir ön eke veya belirli bir sonekine sahip olması ya da ad içindeki tek sözcüklerin belirli bir karakterle ayrılması olabilir. Büyük/küçük harf stili de belirtebilirsiniz. Style özelliği aşağıdaki biçimdedir:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

**< styletitle \>** değerini açıklayıcı bir başlıkla değiştirerek stile bir ad verin, örneğin `first_word_upper_case_style`. Adlandırma stilini (ön ek, sonek, sözcük ayırıcı karakteri ve büyük/küçük harf) tanımlayan özellik adlarında **< styleTitle \>** değerini kullanacaksınız. Stilinizi anlatmak için bu özelliklerden birini veya daha fazlasını kullanın.

### <a name="require-a-prefix"></a>Ön ek gerektir

Sembol adlarının belirli karakterlerle başlaması gerektiğini belirtmek için şu özelliği kullanın:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Sonek gerektir

Sembol adlarının belirli karakterlerle bitmesi gerektiğini belirtmek için şu özelliği kullanın:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Belirli bir sözcük ayırıcısı iste

Sembol adlarındaki tek sözcüklerin belirli bir karakterle ayrılması gerektiğini belirtmek için şu özelliği kullanın:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Büyük harfe çevirme stili gerektir

Sembol adları için belirli bir büyük harfle bir stil belirtmek için şu özelliği kullanın:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Bu özellik için izin verilen değerler şunlardır:

- pascal_case
- camel_case
- ilk \_word_upper
- Tüm \_upper
- all_lower

> [!NOTE]
> Adlandırma stiliniz kapsamında bir büyük harf stili belirtmeniz gerekir, aksi takdirde adlandırma stiliniz yok sayılabilir.

## <a name="severity"></a>Önem Derecesi

Adlandırma kuralınızın ihlalinin önem derecesini belirlemek için, aşağıdaki biçimde bir özellik belirtin:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

Aşağıdaki tabloda izin verilen önem derecesi değerleri ve anlamları gösterilmektedir:

Önem Derecesi | Efekt
------------ | -------------
yok | Kural tamamen bastırılır.
yeniden düzenleme veya sessiz | Bu stil izlenmediğinden, kullanıcıya hiçbir şey göstermeyin; Ancak otomatik olarak oluşturulan kod bu stili izler.
bulunmak | Bu stil izlenmediğinden, ilk iki karakter üzerinde altta yatan noktalar olarak kullanıcıya öneri olarak gösterin. Derleme zamanında hiçbir etkisi yoktur.
warning | Bu stil izlenmediğinden **hata listesi**bir derleyici uyarısı gösterin.
error | Bu stil izlenmediğinden **hata listesi**bir derleyici hatası gösterir.

> [!NOTE]
> Adlandırma kuralı ihlallerini görmek için projenizi oluşturmak zorunda değilsiniz. **Hata listesi** veya bir öneri olarak kod düzenlendiğinde görünürler.

## <a name="rule-order"></a>Kural sırası

::: moniker range="vs-2017"

Adlandırma kuralları, EditorConfig dosyasında en çok özgü olan en büyük öğesine göre sıralanmalıdır. Uygulanabilecek ilk kural, uygulanan tek kuraldır. Ancak, aynı ada sahip birden fazla kural *özelliği* varsa, bu adı taşıyan en son bulunan özellik öncelik kazanır. Daha fazla bilgi için bkz. [Dosya hiyerarşisi ve önceliği](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 2019 sürüm 16,2 ' den başlayarak, adlandırma kurallarının bir EditorConfig dosyasında tanımlandığı sıra bu şekilde değildir. Bunun yerine, Visual Studio, adlandırma kurallarını kuralların tanımına göre otomatik olarak sıralar. [Editorconfig dil hizmeti uzantısı](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) , bir editorconfig dosyasını çözümleyebilir ve dosyadaki kural sıralaması derleyicinin çalışma zamanında kullandıklarıyla farklı olduğunda rapor durumlarını rapor edebilir.

Visual Studio 'nun önceki bir sürümünü kullanıyorsanız, adlandırma kuralları, EditorConfig dosyasında en çok belirli olan en az özel olarak sıralanmalıdır. Uygulanabilecek ilk kural, uygulanan tek kuraldır. Ancak, aynı ada sahip birden fazla kural *özelliği* varsa, bu adı taşıyan en son bulunan özellik öncelik kazanır. Daha fazla bilgi için bkz. [Dosya hiyerarşisi ve önceliği](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Varsayılan adlandırma stilleri

Herhangi bir özel adlandırma kuralı belirtmezseniz, Visual Studio aşağıdaki varsayılan stilleri kullanır:

- @No__t_0, `private`, `internal`, `protected` veya `protected_internal` erişilebilirliği olan sınıflar, yapılar, numaralandırmalar, Özellikler ve olaylar için, varsayılan adlandırma stili Pascal durumdur.

- @No__t_0, `private`, `internal`, `protected` veya `protected_internal` erişilebilirliği olan arabirimler için, varsayılan adlandırma stili, gerekli bir **I**ön eki olan Pascal durumdur.

## <a name="example"></a>Örnek

Aşağıdaki *. editorconfig* dosyası, ortak özellikler, Yöntemler, alanlar, olaylar ve temsilcilerin büyük harfli olması gerektiğini belirten bir adlandırma kuralı içerir. Bu adlandırma kuralının, bir değeri ayırmak için bir virgül kullanarak kuralın uygulanacağı birden çok sembol türünü belirttiğinden emin olun.

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

Aşağıdaki ekran görüntüsünde, bu adlandırma kuralının düzenleyicide etkisi gösterilmektedir. İlk harfin büyük harfle yazılmaksızın iki ortak değişken adlandırılmıştı. Biri `const`, diğeri ise `readonly`. Adlandırma kuralı yalnızca `readonly` sembolleri için geçerli olduğundan, yalnızca `readonly` değişkeni bir adlandırma kuralı önerisi gösterir.

![Adlandırma kuralı önerisi](media/editorconfig-naming-rule-suggestion.png)

Şimdi ihlalin önem derecesini `warning` olarak değiştirelim:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Kod dosyanızı kapatıp yeniden açarsanız, ad ihlalinin altındaki öneriyi görmek yerine Hata Listesi yeşil bir dalgalı çizgi ve uyarı görürsünüz:

![Adlandırma kuralı uyarısı](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Dil kuralları](editorconfig-language-conventions.md)
- [Biçimlendirme kuralları](editorconfig-formatting-conventions.md)
- [Roslyn adlandırma kuralları](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Taşınabilir özel düzenleyici seçenekleri oluştur](../ide/create-portable-custom-editor-options.md)
- [EditorConfig için .NET kodlama kuralı ayarları](editorconfig-code-style-settings-reference.md)
