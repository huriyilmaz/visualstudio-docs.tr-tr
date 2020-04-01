---
title: EditorConfig için .NET dil kuralları
ms.date: 03/31/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0c06d6c16082a8300092e36b9bbed126c66f8af4
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80528026"
---
# <a name="language-conventions"></a>Dil kuralları

Visual Studio'da EditorConfig için dil kuralları iki kategoriye ayrılır: Visual Basic ve C#'a uygulananlar ve C#'a özgü olanlar. Dil kuralları, bir programlama dilinin çeşitli yönlerinin (örneğin, değiştiriciler ve parantezler) nasıl kullanıldığını etkiler.

> [!TIP]
> - Tercih ettiğiniz programlama dilindeki kod örneklerini görmek için tarayıcı penceresinin sağ üst köşesindeki dil seçiciyi kullanarak seçin.
>
>   ![Kod dili seçici denetimi](media/code-language-picker.png)
>
> - Sayfanın farklı bölümlerine atlamak için **bu makalede** bağlantıları kullanın.

## <a name="rule-format"></a>Kural biçimi

Dil kuralları için kurallar aşağıdaki genel biçime sahiptir:

`option_name = value:severity`

Her dil kuralı için, stilin ne zaman veya ne zaman tercih edilip edilecek veya ne zaman tercih edilecek olduğunu tanımlayan bir değer belirtirsiniz. Birçok kural bir `true` değer kabul (bu `false` stili tercih) veya (bu stili tercih etmeyin). Diğer kurallar gibi `when_on_single_line` değerleri `never`kabul veya . Kuralın ikinci bölümü [şiddetini](#severity-levels)belirtir.

::: moniker range=">=vs-2019"

> [!NOTE]
> Dil kuralları çözümleyiciler tarafından zorlandığı için, çözümleyiciler için varsayılan yapılandırma sözdizimini kullanarak önem derecelerini de ayarlayabilirsiniz. Sözdizimi, örneğin, formu `dotnet_diagnostic.<rule ID>.severity = <severity>` `dotnet_diagnostic.IDE0040.severity = silent`alır. Daha fazla bilgi için [bkz.](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)

::: moniker-end

## <a name="severity-levels"></a>Önem düzeyleri

Bir dil kuralı önem derecesi, bu stilin uygulanacağı düzeyi belirtir. Aşağıdaki tabloda olası önem değerleri ve etkileri listelenebilmektedir:

Severity | Etki
:------- | ------
`error` | Bu stil kuralı ihlal edildiğinde, derleyici hatası gösterin.
`warning` | Bu stil kuralı ihlal edildiğinde, derleyici uyarısı gösterin.
`suggestion` | Bu stil kuralı ihlal edildiğinde, bunu bir öneri olarak kullanıcıya gösterin. Öneriler ilk iki karakterin altında üç gri nokta olarak görünür.
`silent` | Bu kural ihlal edildiğinde kullanıcıya hiçbir şey göstermeyin. Ancak kod oluşturma özellikleri bu stilde kod oluşturur. Önem `silent` derecesine sahip kurallar temizlemeye katılır ve **Hızlı Eylemler ve Refactorings** menüsünde görünür.
`none` | Bu kural ihlal edildiğinde kullanıcıya hiçbir şey göstermeyin. Ancak kod oluşturma özellikleri bu stilde kod oluşturur. Önem `none` derecesine sahip **kurallar, Hızlı Eylemler ve Refactorings** menüsünde hiçbir zaman görünmez. Çoğu durumda, bu "devre dışı" veya "yoksayıldı" olarak kabul edilir.

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>Kod stillerini otomatik olarak yapılandırma

Visual Studio 2019 sürüm 16.3'ten başlayarak, stil ihlali gerçekleştikten sonra [Quick Actions](quick-actions.md) ampul menüsünden kod stili kurallarını yapılandırabilirsiniz.

Kod stili kuralını değiştirmek için:

1. Editördeki dalgalı nın üzerine çıkın ve ardından görünen ampul menüsünü açın. **Yapılaşı veya Baskısorunlarını** > **Seçin \<Kural Kimliği> kod stilini yapılandırın.**

   ![Visual Studio'da ampul menüsünden kod stilini yapılandır](media/vs-2019/configure-code-style.png)

2. Buradan, kod stili seçeneklerinden birini seçin.

   ![Kod stili ayarını yapılandırma](media/vs-2019/configure-code-style-setting.png)

   Visual Studio, önizleme kutusunda gösterildiği gibi EditorConfig dosyasındaki yapılandırma ayarını ekler veya değiştirir.

Kod stili ihlalinin önem derecesini değiştirmek için, aynı adımları izleyin, ancak ** \<kural kimliği> kod stilini yapılandırmak**yerine ** \<kural kimliğini> önem derecesini yapılandır'ı** seçin. Daha fazla bilgi için [bkz.](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity)

::: moniker-end

## <a name="net-code-style-settings"></a>.NET kod stili ayarları

Bu bölümdeki stil kuralları hem C# hem de Visual Basic için geçerlidir.

- ["Bu." ve "Ben." elemeleri](#this-and-me)
  - dotnet\_\_tarzı\_yeterlilik for_field
  - dotnet\_\_tarzı\_nitelik for_property
  - dotnet\_\_tarzı\_yeterlilik for_method
  - dotnet\_\_tarzı\_yeterlilik for_event
- [Tür başvuruları için çerçeve türü adları yerine dil anahtar kelimeleri](#language-keywords)
  - yerel halk\_\_\_için\_\_dotnet stili önceden tanımlanmış tip\_parameters_members
  - member_access için\_\_\_dotnet stili önceden tanımlanmış\_tip\_
- [Değiştirici tercihleri](#normalize-modifiers)
  - dotnet\_\_tarzı\_accessibility_modifiers gerektirir
  - görsel\_\_temel\_tercih modifier_order
  - dotnet\_\_tarzı\_readonly alan
- [Tercihleri parantez e-ş](#parentheses-preferences)
  - \_aritmetik\_\_ikili\_\_işleçlerde\_dotnet tarzı parantezler
  - diğer\_\_\_\_ikili\_işleçlerde dotnet tarzı parantez\_
  - diğer\_\_\_işleçlerde\_dotnet tarzı parantez\_
  - ilişkisel\_\_\_\_\_ikili\_işleçlerde dotnet stili parantez
- [İfade düzeyi tercihleri](#expression-level-preferences)
  - dotnet\_\_tarzı object_initializer
  - dotnet\_\_tarzı collection_initializer
  - dotnet\_\_tarzı\_açık tuple_names
  - dotnet\_\_tarzı\_ertelenmiş\_tuple_names tercih
  - dotnet\_\_tarzı\_member_names\_inferred anonim\_türü\_tercih
  - dotnet\_\_stili\_\_otomatik özellikleri tercih
  - dotnet\_\_tarzı\_\_tercih\_\_referans\_\_eşitlik\_yöntemi üzerinde null kontrol
  - noktanet\_stili\_\_atama\_yerine\_\_koşullu ifadeyi tercih
  - dotnet\_\_stili\_dönüş\_\_yerine\_koşullu ifadeyi tercih
  - dotnet\_\_stili\_\_bileşik atama tercih
- ["Null" kontrol tercihleri](#null-checking-preferences)
  - dotnet\_\_tarzı coalesce_expression
  - dotnet\_\_tarzı null_propagation
  - dotnet\_\_tarzı\_\_tercih\_\_referans\_\_eşitlik\_yöntemi üzerinde null kontrol

### <a name="this-and-me-qualifiers"></a><a name="this-and-me"></a>"Bu." ve "Ben." Elemeleri

Bu stil kuralı alanlara, özelliklere, yöntemlere veya olaylara uygulanabilir. **Doğru** anlamın değeri, C# veya `this.` `Me.` Visual Basic'te öngörülebilmek için kod simgesini tercih edin. **False** değeri, kod öğesinin önceden _anlaşılmamasını_ `this.` tercih `Me.`etmek anlamına gelir veya .

Bu kurallar bir *.editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_\_tarzı\_yeterlilik for_field

|||
|-|-|
| **Kural adı** | dotnet_style_qualification_for_field |
| **Kural Kimliği** | IDE0003 ve IDE0009 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- C# veya `this.` `Me.` Visual Basic'te öngörülebilmek için alanları tercih edin<br /><br />`false`- Önyargıya uygun _olmayan_ `this.` alanları tercih etmek veya`Me.` |
| **Visual Studio varsayılan** | `false:silent` |

Kod örnekleri:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_\_tarzı\_nitelik for_property

|||
|-|-|
| **Kural adı** | dotnet_style_qualification_for_property |
| **Kural Kimliği** | IDE0003 ve IDE0009 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- C# veya `this.` `Me.` Visual Basic'te öngörülebilmek için özellikleri tercih edin<br /><br />`false`- Önceden _anlaşılmayan_ veya `this.` tercih edilmemek üzere özellikleri tercih etme`Me.` |
| **Visual Studio varsayılan** | `false:silent` |

Kod örnekleri:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_\_tarzı\_yeterlilik for_method

|||
|-|-|
| **Kural adı** | dotnet_style_qualification_for_method |
| **Kural Kimliği** | IDE0003 ve IDE0009 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- C# veya `this.` `Me.` Visual Basic'te önyargıda önyargılama yöntemlerini tercih edin.<br /><br />`false`- Önceden _anlaşılmaması_ gereken `this.` yöntemleri `Me.`tercih etmek veya . |
| **Visual Studio varsayılan** | `false:silent` |

Kod örnekleri:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_\_tarzı\_yeterlilik for_event

|||
|-|-|
| **Kural adı** | dotnet_style_qualification_for_event |
| **Kural Kimliği** | IDE0003 ve IDE0009 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- C# veya `this.` `Me.` Visual Basic'te öngörülebilmek için olayları tercih edin.<br /><br />`false`- Önceden _anlaşılmayan_ olayları `this.` tercih `Me.`etmek ya da . |
| **Visual Studio varsayılan** | `false:silent` |

Kod örnekleri:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

### <a name="language-keywords-instead-of-framework-type-names-for-type-references"></a><a name="language-keywords"></a>Tür başvuruları için çerçeve türü adları yerine dil anahtar kelimeleri

Bu stil kuralı yerel değişkenlere, yöntem parametrelerine ve sınıf üyelerine veya üye erişim ifadelerini yazmak için ayrı bir kural olarak uygulanabilir. **Doğru** anlamın değeri, `int` `Integer`onları temsil edecek bir anahtar kelimesi olan türler için `Int32`tür adı (örneğin,) yerine dil anahtar sözcük (örneğin) tercih eder. **Yanlış** değeri, dil anahtar sözcüğü yerine tür adını tercih etmek anlamına gelir.

Bu kurallar bir *.editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>yerel halk\_\_\_için\_\_dotnet stili önceden tanımlanmış tip\_parameters_members

|||
|-|-|
| **Kural adı** | dotnet_style_predefined_type_for_locals_parameters_members |
| **Kural Kimliği** | IDE0012 ve IDE0014 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Yerel değişkenler, yöntem parametreleri ve sınıf üyeleri için dil anahtar sözcüklerini, tür adı yerine, onları temsil edecek bir anahtar kelimeolan türler için tercih edin<br /><br />`false`- Dil anahtar sözcüğü yerine yerel değişkenler, yöntem parametreleri ve sınıf üyeleri için tür adını tercih edin |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

#### <a name="dotnet_style_predefined_type_for_member_access"></a>member_access için\_\_\_dotnet stili önceden tanımlanmış\_tip\_

|||
|-|-|
| **Kural adı** | dotnet_style_predefined_type_for_member_access |
| **Kural Kimliği** | IDE0013 ve IDE0015 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Tür adı yerine üye erişim ifadeleri için dil anahtar sözcüklerini, onları temsil edecek bir anahtar kelimesi olan türler için tercih edin<br /><br />`false`- Dil anahtar sözcüğü yerine üye erişim ifadelerinin tür adını tercih edin |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

### <a name="modifier-preferences"></a><a name="normalize-modifiers"></a>Değiştirici tercihleri

Bu bölümdeki stil kuralları, erişilebilirlik değiştiriciler gerektiren, istenen değiştirici sıralama sırasını belirtme ve salt okunur değiştirici gerektiren de dahil olmak üzere değiştirici tercihleri ile ilgilidir.

Bu kurallar bir *.editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_\_tarzı\_accessibility_modifiers gerektirir

|||
|-|-|
| **Kural adı** | dotnet_style_require_accessibility_modifiers |
| **Kural Kimliği** | IDE0040 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `always`- Belirtilecek erişilebilirlik değiştiricilertercih edin.<br /><br />`for_non_interface_members`- Genel arayüz üyeleri dışında bildirilecek erişilebilirlik değiştiricilertercih. (Bu **her zaman** olduğu gibi aynıdır ve C# varsayılan arabirim yöntemleri eklerse gelecek geçirmezlik için eklenmiştir.)<br /><br />`never`- Erişilebilirlik değiştiriciler belirtilecek tercih etmeyin.<br /><br />`omit_if_default`- Varsayılan değiştirici olmadıkları sürece belirtilen erişilebilirlik değiştiricilerini tercih edin. |
| **Visual Studio varsayılan** | `for_non_interface_members:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.5 |

Kod örnekleri:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

#### <a name="csharp_preferred_modifier_order"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Kural adı** | csharp_preferred_modifier_order |
| **Kural Kimliği** | IDE0036 |
| **Geçerli diller** | C# |
| **Değer** | Bir veya daha fazla C# `public`değiştiricisi, örneğin , `private`, ve`protected` |
| **Visual Studio varsayılan** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.5 |

- Bu kural değiştiriciler listesine ayarlandığında, belirtilen sıralamayı tercih edin.
- Bu kural dosyadan atlandığında, değiştirici bir sipariş tercih etmeyin.

Kod örnekleri:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Kural adı** | visual_basic_preferred_modifier_order |
| **Kural Kimliği** | IDE0036 |
| **Geçerli diller** | Visual Basic |
| **Değer** | Bir veya daha fazla Visual Basic `Partial` `Private`değiştiriciler, örneğin , , ve`Public` |
| **Visual Studio varsayılan** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.5 |

- Bu kural değiştiriciler listesine ayarlandığında, belirtilen sıralamayı tercih edin.
- Bu kural dosyadan atlandığında, değiştirici bir sipariş tercih etmeyin.

Kod örnekleri:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="visual_basic_style_unused_value_expression_statement_preference"></a>visual_basic_style_unused_value_expression_statement_preference

|||
|-|-|
| **Kural adı** | visual_basic_style_unused_value_expression_statement_preference |
| **Kural Kimliği** | IDE0058 |
| **Geçerli diller** | Visual Basic |
| **Değer** | `unused_local_variable:silent` |
| **Visual Studio varsayılan** | `unused_local_variable:silent` |

Kod örnekleri:

```vb
' visual_basic_style_unused_value_expression_statement_preference = unused_local_variable:silent

Dim unused = Computation()
```

#### <a name="visual_basic_style_unused_value_assignment_preference"></a>visual_basic_style_unused_value_assignment_preference

|||
|-|-|
| **Kural adı** | visual_basic_style_unused_value_assignment_preference |
| **Kural Kimliği** | IDE0059 |
| **Geçerli diller** | Visual Basic |
| **Değer** | `unused_local_variable:silent` |
| **Visual Studio varsayılan** | `unused_local_variable:silent` |

Kod örnekleri:

```vb
' visual_basic_style_unused_value_assignment_preference = unused_local_variable:suggestion

Dim unused = Computation()
Dim x = 1;
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Kural adı** | dotnet_style_readonly_field |
| **Kural Kimliği** | IDE0044 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Yalnızca satır içi `readonly` veya bir oluşturucunun içine atanmışsa, alanların (C#) veya `ReadOnly` (Visual Basic) ile işaretlenebilmelidir<br /><br />`false`- Alanların (C#) veya `readonly` `ReadOnly` (Visual Basic) ile işaretlenip işaretlenmeyeceği konusunda hiçbir tercih belirtme |
| **Visual Studio varsayılan** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |

Kod örnekleri:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

### <a name="parentheses-preferences"></a>Tercihleri parantez e-ş

Bu bölümdeki stil kuralları, aritmetik, ilişkisel ve diğer ikili işleçler için parantez kullanımı da dahil olmak üzere parantez tercihlerini ilgilendirir.

Bu kurallar bir *.editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>\_aritmetik\_binary_operators\_dotnet\_tarzı\_parantez

|||
|-|-|
| **Kural adı** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **Kural Kimliği** | IDE0047 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `always_for_clarity`- Aritmetik`*`işleç ( , `/`, `%` `+` `-` `<<` `>>`, , `&`, `^` `|`, , , , , , ) önceliğini açıklığa kavuşturmak için parantez tercih<br /><br />`never_if_unnecessary`- Aritmetik`*`işleç ( , , `/` `%` `+` `-` `<<`, , `>>`, `&`, `^` `|`, , , , , , , ) önceliği belirgin olduğunda parantez olmamasını tercih |
| **Visual Studio varsayılan** | `always_for_clarity:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürümü 15.8 |

Kod örnekleri:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>\_ilişkisel\_\_binary_operators\_dotnet tarzı parantez\_

|||
|-|-|
| **Kural adı** | dotnet_style_parentheses_in_relational_binary_operators |
| **Kural Kimliği** | IDE0047 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `always_for_clarity`- İlişkisel işleç`>`( , `<`, `<=` `>=`, `is` `as`, `==` `!=`, , , , , ) önceliğini netleştirmek için paranteztercih<br /><br />`never_if_unnecessary`- İlişkisel`>`işleç ( , , `<` `<=` `>=` `is`, `as`, , `==` `!=`, , , , ) önceliği belirgin olduğunda parantez olmamasını tercih |
| **Visual Studio varsayılan** | `always_for_clarity:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürümü 15.8 |

Kod örnekleri:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>\_diğer\_binary_operators\_\_dotnet\_tarzı parantez

|||
|-|-|
| **Kural adı** | dotnet_style_parentheses_in_other_binary_operators |
| **Kural Kimliği** | IDE0047 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `always_for_clarity`- Diğer ikili işleç (`&&`, `||` `??`, ) önceliğini açıklığa kavuşturmak için parantez tercih<br /><br />`never_if_unnecessary`- Diğer ikili işleç (`&&`, , `||` `??`) önceliği belirgin olduğunda parantez olmamasını tercih |
| **Visual Studio varsayılan** | `always_for_clarity:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürümü 15.8 |

Kod örnekleri:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

#### <a name="dotnet_style_parentheses_in_other_operators"></a>other_operators dotnet\_tarzı\_parantez\_\_

|||
|-|-|
| **Kural adı** | dotnet_style_parentheses_in_other_operators |
| **Kural Kimliği** | IDE0047 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `always_for_clarity`- Operatör önceliğini netleştirmek için parantez tercih edin<br /><br />`never_if_unnecessary`- Operatör önceliği belirginolduğunda parantez olmamasını tercih edin |
| **Visual Studio varsayılan** | `never_if_unnecessary:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürümü 15.8 |

Kod örnekleri:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

### <a name="expression-level-preferences"></a>İfade düzeyi tercihleri

Bu bölümdeki stil kuralları, nesne baş harflerini, koleksiyon baş harflerini, açık veya çıkarılan tuple adlarını ve çıkarılan anonim türleri kullanmada ifade düzeyi tercihlerini ilgilendirir.

Bu kurallar bir *.editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
dotnet_style_prefer_compound_assignment = true:suggestion
```

#### <a name="dotnet_style_object_initializer"></a>dotnet\_\_tarzı object_initializer

|||
|-|-|
| **Kural adı** | dotnet_style_object_initializer |
| **Kural Kimliği** | IDE0017 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Mümkün olduğunda nesne başharflerini kullanarak başharfe bünyesine kalınması nı tercih edin<br /><br />`false`- Nesne başharflerini kullanarak başharfe bilmeyecek nesneleri tercih edin *not* |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

#### <a name="dotnet_style_collection_initializer"></a>dotnet\_\_tarzı collection_initializer

|||
|-|-|
| **Kural adı** | dotnet_style_collection_initializer |
| **Kural Kimliği** | IDE0028 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Koleksiyon başlatmalayıcıları kullanılarak mümkün olduğunca başharfe bilmelidir<br /><br />`false`- Koleksiyon başlatmalayıcıları kullanılarak başharfe *başharfe bıyıltılmamak* için koleksiyonları tercih edin |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

#### <a name="dotnet_style_explicit_tuple_names"></a>dotnet\_\_tarzı\_açık tuple_names

|||
|-|-|
| **Kural adı** | dotnet_style_explicit_tuple_names |
| **Kural Kimliği** | IDE0033 |
| **Geçerli diller** | C# 7.0+ ve Visual Basic 15+ |
| **Değer** | `true`- Tuple adlarını ItemX özelliklerine tercih etme<br /><br />`false`- ItemX özelliklerini tuple adlarına tercih etme |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>dotnet\_\_tarzı\_ertelenmiş\_tuple_names tercih

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_inferred_tuple_names |
| **Kural Kimliği** | IDE0037 |
| **Geçerli diller** | C# 7.1+ ve Visual Basic 15+ |
| **Değer** | `true`- Çıkarılan tuple öğe adlarını tercih edin<br /><br />`false`- Açık tuple öğesi adlarını tercih etme |
| **Visual Studio varsayılan** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.6 |

Kod örnekleri:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>dotnet\_\_tarzı\_member_names\_inferred anonim\_türü\_tercih

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **Kural Kimliği** | IDE0037 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Çıkarılan anonim tip üye adlarını tercih edin<br /><br />`false`- Açık anonim tür üye adlarını tercih edin |
| **Visual Studio varsayılan** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.6 |

Kod örnekleri:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

#### <a name="dotnet_style_prefer_auto_properties"></a>dotnet\_\_stili\_\_otomatik özellikleri tercih

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_auto_properties |
| **Kural Kimliği** | IDE0032 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Özel destek alanlarına sahip özelliklere göre otomatik özellikleri tercih edin<br /><br />`false`- Otomatik özelliklere göre özel destek alanlarına sahip özellikleri tercih edin |
| **Visual Studio varsayılan** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |

Kod örnekleri:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_\_tarzı\_\_tercih\_\_referans\_\_eşitlik\_yöntemi üzerinde null kontrol

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Kural Kimliği** | IDE0041 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Üzerinde desen eşleştirme ile null çek kullanmayı tercih edin`object.ReferenceEquals`<br /><br />`false`- `object.ReferenceEquals` Desen eşleştirmeli null çek yerine tercih edin |
| **Visual Studio varsayılan** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |

Kod örnekleri:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_\_stili\_tercih\_\_koşullu ifade over_assignment

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_conditional_expression_over_assignment |
| **Kural Kimliği** | IDE0045 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- If-else deyimi yerine üçüncül koşullu atamaları tercih edin<br /><br />`false`- Bir üçüncü koşullu üzerinde if-else deyimi ile atamaları tercih |
| **Visual Studio varsayılan** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürümü 15.8 |

Kod örnekleri:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_\_stili\_tercih\_\_koşullu ifade over_return

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_conditional_expression_over_return |
| **Kural Kimliği** | IDE0046 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- İade deyimlerini if-else deyimi yerine üçüncül koşullu bir ifade kullanmayı tercih edin<br /><br />`false`- Tersiyer koşullu bir üzerinde if-else deyimi kullanmak için iade deyimleri tercih |
| **Visual Studio varsayılan** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürümü 15.8 |

Kod örnekleri:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

#### <a name="dotnet_style_prefer_compound_assignment"></a>dotnet\_\_stili\_\_bileşik atama tercih

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_compound_assignment |
| **Kural Kimliği** | IDE0054 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Bileşik atama ifadelerini tercih [edin](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false`- Bileşik atama ifadelerini tercih etmeyin |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// dotnet_style_prefer_compound_assignment = true
x += 1;

// dotnet_style_prefer_compound_assignment = false
x = x + 1;
```

```vb
' dotnet_style_prefer_compound_assignment = true
x += 1

' dotnet_style_prefer_compound_assignment = false
x = x + 1
```

### <a name="null-checking-preferences"></a>Tercihleri geçersiz kontrol etme

Bu bölümdeki stil kuralları, geçersiz kontrol tercihleri ile ilgilidir.

Bu kurallar bir *.editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
```

#### <a name="dotnet_style_coalesce_expression"></a>dotnet\_\_tarzı coalesce_expression

|||
|-|-|
| **Kural adı** | dotnet_style_coalesce_expression |
| **Kural Kimliği** | IDE0029 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `true`- Null coalescing ifadelerini üçüncül operatör denetimine tercih edin<br /><br />`false`- Null coalescing ifadeleri için üçüncül operatör kontrol tercih |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

#### <a name="dotnet_style_null_propagation"></a>dotnet\_\_tarzı null_propagation

|||
|-|-|
| **Kural adı** | dotnet_style_null_propagation |
| **Kural Kimliği** | IDE0031 |
| **Geçerli diller** | C# 6.0+ ve Visual Basic 14+ |
| **Değer** | `true`- Mümkün olduğunda null-koşullu operatör kullanmayı tercih<br /><br />`false`- Mümkün olduğunca üçüncül null kontrol kullanmayı tercih |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_\_tarzı\_\_tercih\_\_referans\_\_eşitlik\_yöntemi üzerinde null kontrol

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Kural Kimliği** | IDE0041 |
| **Geçerli diller** | C# 6.0+ ve Visual Basic 14+ |
| **Değer** | `true`- Tercih referans eşitlik yöntemi üzerinde null kontrol<br /><br />`false`- Tercih referans eşitlik yöntemi üzerinde null kontrol |
| **Visual Studio varsayılan** | `true:silent` |

## <a name="net-code-quality-settings"></a>.NET kod kalite ayarları

Bu bölümdeki kalite kuralları hem C# hem de Visual Basic kodu için geçerlidir. Visual Studio tümleşik geliştirme ortamında (IDE) yerleşik kod çözümleyicilerini yapılandırmak için kullanılırlar. Bir EditorConfig dosyası ile FxCop analizörleri yapılandırma hakkında bilgi için, [Bkz.](../code-quality/configure-fxcop-analyzers.md)

- [Parametre tercihleri](#parameter-preferences)
  - dotnet\_\_kod\_kalitesi\_kullanılmayan parametreler

### <a name="parameter-preferences"></a>Parametre tercihleri

Bu bölümdeki kalite kuralları yöntem parametrelerini ilgilendirir.

Bu kurallar bir *.editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>dotnet\_\_kod\_kalitesi\_kullanılmayan parametreler

|||
|-|-|
| **Kural adı** | dotnet_code_quality_unused_parameters |
| **Kural Kimliği** | IDE0060 |
| **Geçerli diller** | C# ve Visual Basic |
| **Değer** | `all`- Kullanılmayan parametreler içeren herhangi bir erişilebilirlik ile bayrak yöntemleri<br /><br />`non_public`- Yalnızca kullanılmayan parametreleriçeren genel olmayan yöntemleri bayrakla işaretleme |
| **Visual Studio varsayılan** | `all:suggestion` |

Kod örnekleri:

```csharp
// dotnet_code_quality_unused_parameters = all:suggestion
public int GetNum() { return 1; }

// dotnet_code_quality_unused_parameters = non_public:suggestion
public int GetNum(int arg1) { return 1; }
```

```vb
' dotnet_code_quality_unused_parameters = all:suggestion
Public Function GetNum()
    Return 1
End Function

' dotnet_code_quality_unused_parameters = non_public:suggestion
Public Function GetNum(arg1 As Integer)
    Return 1
End Function
```

## <a name="c-code-style-settings"></a>C# kod stili ayarları

Bu bölümdeki stil kuralları yalnızca C# için geçerlidir.

- [Örtük ve açık türleri](#implicit-and-explicit-types)
  - \_inşa\_in_types\_\_için\_csharp tarzı var
  - csharp\_\_stili\_\_var\_zaman türü is_apparent
  - csharp\_\_tarzı var_elsewhere
- [İfade gövdeli üyeler](#expression-bodied-members)
  - csharp\_\_stili\_ifade bodied_methods
  - csharp\_\_stili\_ifade bodied_constructors
  - csharp\_\_tarzı\_ifade bodied_operators
  - csharp\_\_stili\_ifade bodied_properties
  - csharp\_\_tarzı\_ifade bodied_indexers
  - csharp\_\_stili\_ifade bodied_accessors
  - csharp\_\_stili\_ifade bodied_lambdas
  - csharp\_\_tarzı\_ifade\_gövdeli local_functions
- [Desen eşleştirme](#pattern-matching)
  - csharp\_\_stili\_\_deseni\_\_üzerinde\_eşleşen cast_check ile
  - csharp\_\_stili\_\_deseni null_check\_ile\_\_eşleşen
- [Sıralı değişken bildirimleri](#inlined-variable-declarations)
  - csharp\_\_tarzı\_inlined variable_declaration
- [İfade düzeyi tercihleri](#c-expression-level-preferences)
  - csharp\_\_basit\_default_expression tercih
- ["Null" kontrol tercihleri](#c-null-checking-preferences)
  - csharp\_\_tarzı throw_expression
  - csharp\_\_tarzı\_koşullu delegate_call
- [Değiştirici tercihleri](#normalize-modifiers) -csharp\_tercih modifier_order\_
- [Kod bloğu tercihleri](#code-block-preferences)
  - csharp\_prefer_braces
- [Kullanılmayan değer tercihleri](#unused-value-preferences)
  - csharp\_\_stili\_kullanılmayan\_\_değer ifadesi statement_preference
  - csharp\_\_tarzı\_kullanılmayan\_değer assignment_preference
- [Dizin ve aralık tercihleri](#index-and-range-preferences)
  - csharp\_\_tarzı\_tercih index_operator
  - csharp\_\_tarzı\_range_operator tercih
- [Çeşitli tercihler](#miscellaneous-preferences)
  - csharp\_\_tarzı\_deconstructed variable_declaration
  - csharp\_\_stili\_\_desen\_anonymous_function üzerinde yerel
  - csharp\_\_yönerge\_yerleşimini kullanarak
  - csharp\_\_statik\_local_function tercih
  - csharp\_\_basit\_using_statement tercih
  - csharp\_\_tarzı\_switch_expression tercih

### <a name="implicit-and-explicit-types"></a>Örtük ve açık türleri

Bu bölümdeki stil kuralları, değişken bildiriminde açık bir türe karşılık [var](/dotnet/csharp/language-reference/keywords/var) anahtar kelimesinin kullanımıyla ilgilidir. Bu kural, tür belirgin olduğunda ve başka bir yerde yerleşik türlere ayrı olarak uygulanabilir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>\_inşa\_in_types\_\_için\_csharp tarzı var

|||
|-|-|
| **Kural adı** | csharp_style_var_for_built_in_types |
| **Kural Kimliği** | IDE0007 ve IDE0008 |
| **Geçerli diller** | C#  |
| **Değer** | `true`- `var` Tercih gibi yerleşik sistem türleri ile değişkenleri bildirmek için kullanılır`int`<br /><br />`false`- Dahili `var` sistem türleri gibi değişkenleri bildirmek için açık türü tercih edin`int` |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_\_stili\_\_var\_zaman türü is_apparent

|||
|-|-|
| **Kural adı** | csharp_style_var_when_type_is_apparent |
| **Kural Kimliği** | IDE0007 ve IDE0008 |
| **Geçerli diller** | C#  |
| **Değer** | `true`- `var` Bir bildirim ifadesinin sağ tarafında tür zaten belirtildiği zaman tercih<br /><br />`false`- Bir bildirim `var` ifadesinin sağ tarafında zaten belirtilmiş olan tür yerine açık türü tercih edin |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>csharp\_\_tarzı var_elsewhere

|||
|-|-|
| **Kural adı** | csharp_style_var_elsewhere |
| **Kural Kimliği** | IDE0007 ve IDE0008 |
| **Geçerli diller** | C#  |
| **Değer** | `true`- `var` Başka bir kod stili kuralı tarafından geçersiz kılınmadığı sürece, her durumda açık türü tercih edin<br /><br />`false`- Başka bir `var` kod stili kuralı tarafından geçersiz kılınmadığı sürece, her durumda açık türü tercih edin |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>İfade gövdeli üyeler

Bu bölümdeki stil kuralları, mantık tek bir ifadeden oluştuğunda [ifade gövdeli üyelerin](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) kullanımıyla ilgilidir. Bu kural yöntemlere, oluşturuculara, işleçlere, özelliklere, dizin oluşturuculara ve erişimcilere uygulanabilir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
```

#### <a name="csharp_style_expression_bodied_methods"></a>csharp\_\_stili\_ifade bodied_methods

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_methods |
| **Kural Kimliği** | IDE0022 |
| **Geçerli diller** | C# 6.0+  |
| **Değer** | `true`- Yöntemler için ifade gövdelerini tercih edin<br /><br />`when_on_single_line`- Tek bir satır olacak yöntemler için ifade gövdelerini tercih edin<br /><br />`false`- Yöntemler için blok gövdelerini tercih edin |
| **Visual Studio varsayılan** | `false:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>csharp\_\_stili\_ifade bodied_constructors

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_constructors |
| **Kural Kimliği** | IDE0021 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Yapıcılar için ifade gövdelerini tercih edin<br /><br />`when_on_single_line`- Tek bir satır olacak zaman yapıcılar için ifade gövdeleri tercih<br /><br />`false`- Yapıcılar için blok gövdelerini tercih edin |
| **Visual Studio varsayılan** | `false:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>csharp\_\_tarzı\_ifade bodied_operators

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_operators |
| **Kural Kimliği** | IDE0023 ve IDE0024 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Operatörler için ifade gövdelerini tercih edin<br /><br />`when_on_single_line`- Tek bir satır olacak operatörler için ifade gövdeleri tercih<br /><br />`false`- Operatörler için blok gövdelerini tercih edin |
| **Visual Studio varsayılan** | `false:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>csharp\_\_stili\_ifade bodied_properties

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_properties |
| **Kural Kimliği** | IDE0025 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Özellikler için ifade gövdelerini tercih edin<br /><br />`when_on_single_line`- Tek bir satır olacak özellikler için ifade gövdelerini tercih edin<br /><br />`false`- Özellikler için blok gövdelerini tercih edin |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>csharp\_\_tarzı\_ifade bodied_indexers

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_indexers |
| **Kural Kimliği** | IDE0026 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Dizinleyiciler için ifade gövdelerini tercih edin<br /><br />`when_on_single_line`- Tek bir satır olacak dizinleyiciler için ifade gövdelerini tercih edin<br /><br />`false`- Dizinleyiciler için blok gövdelerini tercih edin |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_\_stili\_ifade bodied_accessors

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_accessors |
| **Kural Kimliği** | IDE0027 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Erişimedenler için ifade gövdelerini tercih edin<br /><br />`when_on_single_line`- Tek bir satır olacak zaman erişimciler için ifade gövdeleri tercih<br /><br />`false`- Erişime erişim için blok gövdelerini tercih edin |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>csharp\_\_stili\_ifade bodied_lambdas

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_lambdas |
| **Kural Kimliği** | IDE0053 |
| **Değer** | `true`- Lambdas için ifade gövdelerini tercih edin<br /><br />`when_on_single_line`- Lambdas için ifade gövdelerini tek bir satır olacaksa tercih edin<br /><br />`false`- Lambdas için blok organları tercih edin |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>csharp\_\_tarzı\_ifade\_gövdeli local_functions

C# 7.0 ile başlayarak, C# [yerel işlevleri](/dotnet/csharp/programming-guide/classes-and-structs/local-functions)destekler. Yerel işlevler, başka bir üyede iç içe olan bir türdeki özel yöntemlerdir.

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_local_functions |
| **Kural Kimliği** | IDE0061 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Yerel işlevler için ifade gövdelerini tercih edin<br /><br />`when_on_single_line`- Tek bir satır olacak yerel işlevler için ifade gövdelerini tercih edin<br /><br />`false`- Yerel işlevler için blok gövdelerini tercih edin |
| **Visual Studio varsayılan** | `false:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_local_functions = true
void M()
{
    Hello();
    void Hello() => Console.WriteLine("Hello");
}

// csharp_style_expression_bodied_local_functions = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

### <a name="pattern-matching"></a>Desen eşleştirme

Bu bölümdeki stil kuralları C#'da [desen eşleştirmesinin](/dotnet/csharp/pattern-matching) kullanımıyla ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>csharp\_\_stili\_\_deseni\_\_üzerinde\_eşleşen cast_check ile

|||
|-|-|
| **Kural adı** | csharp_style_pattern_matching_over_is_with_cast_check |
| **Kural Kimliği** | IDE0020 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Tür dökümleri `is` olan ifadeler yerine desen eşleştirmesini tercih edin<br /><br />`false`- `is` Desen eşleştirme yerine tür dökümleri olan ifadeleri tercih edin |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>csharp\_\_stili\_\_deseni null_check\_ile\_\_eşleşen

|||
|-|-|
| **Kural adı** | csharp_style_pattern_matching_over_as_with_null_check |
| **Kural Kimliği** | IDE0019 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Bir şeyin `as` belirli bir türde olup olmadığını belirlemek için null denetimli ifadeler yerine desen eşleştirmesini tercih edin<br /><br />`false`- `as` Bir şeyin belirli bir türde olup olmadığını belirlemek için desen eşleştirmesi yerine null denetimli ifadeleri tercih etme |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Sıralı değişken bildirimleri

Bu stil kuralı, değişkenlerin satır içinde bildirilip bildirilemediğiyle `out` ilgilidir. C# 7'den başlayarak, ayrı bir değişken bildirimi yerine [bir yöntem çağrısının bağımsız değişken listesinde bir çıkış değişkeni bildirebilirsiniz.](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument)

#### <a name="csharp_style_inlined_variable_declaration"></a>csharp\_\_tarzı\_inlined variable_declaration

|||
|-|-|
| **Kural adı** | csharp_style_inlined_variable_declaration |
| **Kural Kimliği** | IDE0018 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- `out` Mümkün olduğunda bir yöntem çağrısının bağımsız değişken listesinde satır içi olarak bildirilecek değişkenleri tercih edin<br /><br />`false`- `out` Yöntem çağrısından önce bildirilecek değişkenleri tercih edin |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>C# ifade düzeyi tercihleri

Bu bölümdeki stil kuralları ifade düzeyi tercihlerini ilgilendirir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_\_basit\_default_expression tercih

Bu stil kuralı, derleyici ifade türünü çıkarabildiği zaman [ `default` varsayılan değer ifadeleri için literal'ı](/dotnet/csharp/language-reference/operators/default#default-literal) kullanmayla ilgilidir.

|||
|-|-|
| **Kural adı** | csharp_prefer_simple_default_expression |
| **Kural Kimliği** | IDE0034 |
| **Geçerli diller** | C# 7.1+  |
| **Değer** | `true`- `default` Tercih fazla`default(T)`<br /><br />`false`- `default(T)` Tercih fazla`default` |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>C# null-check tercihleri

Bu stil kuralları, ifadeler `null` `throw` veya `throw` deyimler kullanarak da dahil olmak üzere, denetim etrafında sözdizimi ile ilgilidir`?.`ve bir [lambda ifadesini](/dotnet/csharp/lambda-expressions)çağırırken geçersiz bir denetim yapmak veya koşullu birleştirme işleci kullanmak mı ?

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_\_tarzı throw_expression

|||
|-|-|
| **Kural adı** | csharp_style_throw_expression |
| **Kural Kimliği** | IDE0016 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- `throw` İfadeler `throw` yerine ifadeleri kullanmayı tercih etme<br /><br />`false`- `throw` İfadeler `throw` yerine deyimleri kullanmayı tercih etme |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>csharp\_\_tarzı\_koşullu delegate_call

|||
|-|-|
| **Kural adı** | csharp_style_conditional_delegate_call |
| **Kural Kimliği** | IDE0041 |
| **Geçerli diller** | C# 6.0+  |
| **Değer** | `true`- null çek yerine lambda ifadesini`?.`kullanırken koşullu birleştirme operatörü () kullanmak için bakın<br /><br />`false`- Koşullu birleştirme operatörünün kullanılması yerine lambda ifadesini kullanmadan önce null check`?.`yapmayı tercih edin ( ) |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Kod bloğu tercihleri

Bu stil kuralı, kod bloklarını `{ }` çevreleyen kıvırcık ayraçların kullanımıyla ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>csharp\_\_parantez tercih

|||
|-|-|
| **Kural adı** | csharp_prefer_braces |
| **Kural Kimliği** | IDE0011 |
| **Geçerli diller** | C# |
| **Değer** | `true`- Bir kod satırı için bile kıvırcık ayraçları tercih edin<br /><br />`false`- İzin verilirse kıvırcık ayraç lar tercih edeyim<br /><br />`when_multiline`- Birden fazla satırda kıvırcık ayraçları tercih edin |
| **Visual Studio varsayılan** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Kullanılmayan değer tercihleri

Bu stil kuralları kullanılmayan ifadeleri ve değer atamaları ile ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|||
|-|-|
| **Kural adı** | csharp_style_unused_value_expression_statement_preference |
| **Kural Kimliği** | IDE0058 |
| **Geçerli diller** | C# |
| **Değer** | `discard_variable`- Kullanılmayan bir ifadeyi bir [atmaya](/dotnet/csharp/discards) atamayı tercih etme <br /><br />`unused_local_variable`- Kullanılmayan bir ifadeyi yerel bir değişkene atamayı tercih etme |
| **Visual Studio varsayılan** | `discard_variable:silent` |

Kod örnekleri:

```csharp
// Original code:
System.Convert.ToInt32("35");

// After code fix for IDE0058:

// csharp_style_unused_value_expression_statement_preference = discard_variable
_ = System.Convert.ToInt32("35");

// csharp_style_unused_value_expression_statement_preference = unused_local_variable
var unused = Convert.ToInt32("35");
```

#### <a name="csharp_style_unused_value_assignment_preference"></a>csharp_style_unused_value_assignment_preference

|||
|-|-|
| **Kural adı** | csharp_style_unused_value_assignment_preference |
| **Kural Kimliği** | IDE0059 |
| **Geçerli diller** | C# |
| **Değer** | `discard_variable`- Kullanılmayan bir değer atarken [atma](/dotnet/csharp/discards) yı tercih etme<br /><br />`unused_local_variable`- Kullanılmayan bir değer atarken yerel bir değişken kullanmayı tercih etme |
| **Visual Studio varsayılan** | `discard_variable:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_unused_value_assignment_preference = discard_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    _ = wordCount.TryGetValue(searchWord, out var count);
    return count;
}

// csharp_style_unused_value_assignment_preference = unused_local_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    var unused = wordCount.TryGetValue(searchWord, out var count);
    return count;
}
```

### <a name="index-and-range-preferences"></a>Dizin ve aralık tercihleri

Bu stil kuralları, C# 8.0 ve sonraki yıllarda bulunan dizin ve aralık işleçlerinin kullanımıyla ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>csharp\_\_tarzı\_tercih index_operator

|||
|-|-|
| **Kural adı** | csharp_style_prefer_index_operator |
| **Kural Kimliği** | IDE0056 |
| **Geçerli diller** | C# 8.0+ |
| **Değer** | `true`- Koleksiyonun `^` sonundan bir dizin hesaplarken operatörü kullanmayı tercih edin<br /><br />`false`- Koleksiyonun sonundan `^` bir dizin hesaplarken operatörü kullanmayı tercih etmeyin |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>csharp\_\_tarzı\_range_operator tercih

|||
|-|-|
| **Kural adı** | csharp_style_prefer_range_operator |
| **Kural Kimliği** | IDE0057 |
| **Geçerli diller** | C# 8.0+ |
| **Değer** | `true`- Bir koleksiyonun `..` "dilimini" çıkarırken aralık işlecikullanmayı tercih edin<br /><br />`false`- Bir koleksiyonun "dilimini" çıkarırken aralık işlecikullanmayı `..` tercih etmeyin |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_prefer_range_operator = true
string sentence = "the quick brown fox";
var sub = sentence[0..^4];

// csharp_style_prefer_range_operator = false
string sentence = "the quick brown fox";
var sub = sentence.Substring(0, sentence.Length - 4);
```

### <a name="miscellaneous-preferences"></a>Çeşitli tercihler

Bu bölümde çeşitli stil kuralları içerir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_using_directive_placement = outside_namespace:silent
csharp_prefer_static_local_function = true:suggestion
csharp_prefer_simple_using_statement = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion
```

#### <a name="csharp_style_deconstructed_variable_declaration"></a>csharp\_\_tarzı\_deconstructed variable_declaration

|||
|-|-|
| **Kural adı** | csharp_style_deconstructed_variable_declaration |
| **Kural Kimliği** | IDE0042 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Deconstructed değişken bildirimini tercih edin<br /><br />`false`- Değişken beyannamelerde yapısızlaştırmayı tercih etmeyin |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>csharp\_\_stili\_\_desen\_anonymous_function üzerinde yerel

C# 7.0 ile başlayarak, C# [yerel işlevleri](/dotnet/csharp/programming-guide/classes-and-structs/local-functions)destekler. Yerel işlevler, başka bir üyede iç içe olan bir türdeki özel yöntemlerdir.

|||
|-|-|
| **Kural adı** | csharp_style_pattern_local_over_anonymous_function |
| **Kural Kimliği** | IDE0039 |
| **Geçerli diller** | C# 7.0+ |
| **Değer** | `true`- Anonim işlevlere göre yerel işlevleri tercih edin<br /><br />`false`- Anonim işlevleri yerel işlevlere tercih edin |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

#### <a name="csharp_using_directive_placement"></a>csharp\_\_kullanarak directive_placement

|||
|-|-|
| **Kural adı** | csharp_using_directive_placement |
| **Kural Kimliği** | IDE0065 |
| **Geçerli diller** | C# |
| **Değer** | `outside_namespace`- `using` Ad alanının dışına yerleştirilecek yönergeleri tercih etme<br /><br />`inside_namespace`- `using` Ad alanı nın içine yerleştirilecek yönergeleri tercih etme |
| **Visual Studio varsayılan** | `outside_namespace:silent` |

Kod örnekleri:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{
    ...
}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
    ...
}
```

#### <a name="csharp_prefer_static_local_function"></a>csharp\_\_statik\_local_function tercih

|||
|-|-|
| **Kural adı** | csharp_prefer_static_local_function |
| **Kural Kimliği** | IDE0062 |
| **Geçerli diller** | C# 8.0+ |
| **Değer** | `true`- İşaretlenecek yerel işlevleri tercih edin`static`<br /><br />`false`- Yerel işlevlerin işaretlemeyi tercih etme`static` |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_prefer_static_local_function = true
void M()
{
    Hello();
    static void Hello()
    {
        Console.WriteLine("Hello");
    }
}

// csharp_prefer_static_local_function = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

#### <a name="csharp_prefer_simple_using_statement"></a>csharp\_\_basit\_using_statement tercih

|||
|-|-|
| **Kural adı** | csharp_prefer_simple_using_statement |
| **Kural Kimliği** | IDE0063 |
| **Geçerli diller** | C# 8.0+ |
| **Değer** | `true`- *Basit* `using` bir ifade kullanmayı tercih edin<br /><br />`false`- *Basit* `using` bir ifade kullanmayı tercih etmeyin |
| **Visual Studio varsayılan** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>csharp\_\_tarzı\_switch_expression tercih

|||
|-|-|
| **Kural adı** | csharp_style_prefer_switch_expression |
| **Kural Kimliği** | IDE0066 |
| **Geçerli diller** | C# 8.0+ |
| **Değer** | `true`- Bir `switch` ifade kullanmayı tercih edin (C# 8.0 ile tanıtıldı)<br /><br />`false`- Anahtar bildirimi kullanmayı tercih [edin](/dotnet/csharp/language-reference/keywords/switch) |
| **Visual Studio varsayılan** | `true:suggestion` |
| **Tanıtılan sürüm** |  Visual Studio 2019 sürüm 16.2  |

Kod örnekleri:

```csharp
// csharp_style_prefer_switch_expression = true
return x switch
{
    1 => 1 * 1,
    2 => 2 * 2,
    _ => 0,
};

// csharp_style_prefer_switch_expression = false
switch (x)
{
    case 1:
        return 1 * 1;
    case 2:
        return 2 * 2;
    default:
        return 0;
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme kuralları](editorconfig-formatting-conventions.md)
- [Adlandırma kuralları](editorconfig-naming-conventions.md)
- [EditorConfig için .NET kodlama kuralı ayarları](editorconfig-code-style-settings-reference.md)
