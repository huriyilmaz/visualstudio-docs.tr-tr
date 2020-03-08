---
title: EditorConfig için .NET dil kuralları
ms.date: 09/23/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 471932f6a097879da194dc6bb4f18807f2323397
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408503"
---
# <a name="language-conventions"></a>Dil kuralları

Visual Studio 'da EditorConfig için dil kuralları iki kategoriye ayrılır: Visual Basic ve C#ve C# özel olanlar için geçerlidir. Dil kuralları, bir programlama dilinin çeşitli yönlerinin nasıl kullanıldığını, örneğin değiştiriciler ve ayraçları etkiler.

> [!TIP]
> - Kod örneklerini tercih ettiğiniz programlama dilinde görmek için, tarayıcı penceresinin sağ üst köşesindeki dil seçicisini kullanarak bunu seçin.
>
>   ![Kod dili seçici denetimi](media/code-language-picker.png)
>
> - **Bu makalede** , sayfanın farklı bölümlerine gitmek için bağlantıları kullanın.

## <a name="rule-format"></a>Kural biçimi

Dil kuralları kuralları aşağıdaki genel biçimdedir:

`option_name = value:severity`

Her dil kuralı için, stilin ne zaman tercih edilmesi gerektiğini tanımlayan bir değer belirtirsiniz. Birçok kural `true` değerini kabul eder (Bu stili tercih et) veya `false` (Bu stili tercih etmez). Diğer kurallar `when_on_single_line` veya `never`gibi değerleri kabul eder. Kuralın ikinci bölümü [önem derecesini](#severity-levels)belirtir.

::: moniker range=">=vs-2019"

> [!NOTE]
> Dil kuralları çözümleyiciler tarafından zorlandığından, çözümleyiciler için varsayılan yapılandırma söz dizimini kullanarak önem derecesini de ayarlayabilirsiniz. Sözdizimi, örneğin `dotnet_diagnostic.IDE0040.severity = silent`gibi `dotnet_diagnostic.<rule ID>.severity = <severity>`alır. Daha fazla bilgi için bkz. [bir EditorConfig dosyasında kural önem derecesini ayarlama](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file).

::: moniker-end

## <a name="severity-levels"></a>Önem düzeyleri

Dil kuralı önem derecesi, bu stilin zorlanmasını sağlayan düzeyi belirtir. Aşağıdaki tabloda olası önem düzeyi değerleri ve bunların etkileri listelenmektedir:

Önem Derecesi | Efekt
:------- | ------
`error` | Bu stil kuralı ihlal edildiğinde, bir derleyici hatası gösterir.
`warning` | Bu stil kuralı ihlal edildiğinde, bir derleyici uyarısı gösterin.
`suggestion` | Bu stil kuralı ihlal edildiğinde kullanıcıya öneri olarak gösterin. Öneriler, ilk iki karakterin altında üç gri nokta olarak görünür.
`silent` | Bu kural ihlal edildiğinde kullanıcıya herhangi bir şey gösterme. Kod oluşturma özellikleri bu stilde kod üretir. `silent` önem derecesine sahip kurallar temizleme işlemine katılır ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünde görüntülenir.
`none` | Bu kural ihlal edildiğinde kullanıcıya herhangi bir şey gösterme. Kod oluşturma özellikleri bu stilde kod üretir. `none` önem derecesine sahip kurallar hiçbir şekilde **Hızlı Eylemler ve yeniden düzenlemeler** menüsünde görünmez. Çoğu durumda bu, "devre dışı" veya "yoksayıldı" olarak değerlendirilir.

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>Kod stillerini otomatik yapılandır

Visual Studio 2019 sürüm 16,3 ' den başlayarak, bir stil ihlali oluştuktan sonra [hızlı eylemler](quick-actions.md) ampul menüsünden kod stili kurallarını yapılandırabilirsiniz.

Kod stili kuralını değiştirmek için:

1. Düzenleyicide dalgalı çizgi üzerine gelin ve görüntülenen ampul menüsünü açın. **\<kural kimliği > kod stilini yapılandırmak** > **sorunları Yapılandır veya gizle** ' yi seçin.

   ![Visual Studio 'da ampul menüsünden kod stili yapılandırma](media/vs-2019/configure-code-style.png)

2. Buradan, kod stili seçeneklerinden birini seçin.

   ![Kod stili ayarını Yapılandır](media/vs-2019/configure-code-style-setting.png)

   Visual Studio, önizleme kutusunda gösterildiği gibi EditorConfig dosyasındaki yapılandırma ayarını ekler veya değiştirir.

Kod stili ihlalinin önem derecesini değiştirmek için, aynı adımları izleyin, ancak **\<kural kimliği > kod stilini yapılandırmak**yerine **\<kural kimliği > önem derecesi** ' ni seçin. Daha fazla bilgi için bkz. [kural önem derecesini otomatik olarak yapılandırma](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity).

::: moniker-end

## <a name="net-code-style-settings"></a>.NET kod stili ayarları

Bu bölümdeki stil kuralları hem hem de C# Visual Basic için geçerlidir.

- ["This." ve "Me." niteleyicileri](#this-and-me)
  - DotNet\_Style\_niteleme\_for_field
  - DotNet\_Style\_niteleme\_for_property
  - DotNet\_Style\_niteleme\_for_method
  - DotNet\_Style\_niteleme\_for_event
- [Tür başvuruları için çerçeve türü adları yerine dil anahtar sözcükleri](#language-keywords)
  - \_\_\_\_\_Yereller\_için öntanımlı tür stili parameters_members
  - DotNet\_Style\_önceden tanımlanmış\_tür\_\_için member_access
- [Değiştirici tercihleri](#normalize-modifiers)
  - DotNet\_Style\_\_gerektiriyor accessibility_modifiers
  - CSharp\_tercih edilen\_modifier_order
  - Visual\_temel\_tercih edilen\_modifier_order
  - DotNet\_Style\_ReadOnly\_alanı
- [Parantez tercihleri](#parentheses-preferences)
  - DotNet\_Style\_parantez\_\_aritmetik\_ikili\_işleçleri
  - \_diğer\_ikili\_işleçleri içindeki DotNet\_Style\_parantezleri\_
  - DotNet\_Style\_parantez\_\_diğer\_işleçlerinde
  - DotNet\_Style\_parantez\_\_ilişkisel\_ikili\_işleçleri
- [İfade düzeyi tercihleri](#expression-level-preferences)
  - DotNet\_stil\_object_initializer
  - DotNet\_stil\_collection_initializer
  - DotNet\_stil\_açık\_tuple_names
  - DotNet\_Style\_\_gösterilen\_tercih eder tuple_names
  - DotNet\_Style\_\_\_anonim\_tür\_çıkarmayı tercih eder member_names
  - DotNet\_Style\_\_otomatik\_özellikleri tercih et
  - DotNet\_Style\_\_tercih\_null\_\_\_\_\_
  - DotNet\_Style\_\_atama üzerinde\_koşullu\_ifade\_tercih eder
  - DotNet\_Style\_\_Return\_koşullu\_ifade\_tercih eder
  - DotNet\_Style\_bileşik\_atamasını\_tercih eder
- ["Null" Denetim tercihleri](#null-checking-preferences)
  - DotNet\_stil\_coalesce_expression
  - DotNet\_stil\_null_propagation

### <a name="this-and-me"></a>"This." ve "Me." ilerini

Bu stil kuralı alanlara, özelliklere, yöntemlere veya olaylara uygulanabilir. **True** değeri, kod sembolünün Visual Basic içinde C# veya `Me.` `this.` ile önceden çıkacak şekilde tercih edilmesinin tercih ettiği anlamına gelir. **False** değeri, kod öğesinin `this.` veya `Me.`önceden başında yer _almamayı_ tercih eder anlamına gelir.

Bu kurallar bir *. editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>DotNet\_Style\_niteleme\_for_field

|||
|-|-|
| **Kural adı** | dotnet_style_qualification_for_field |
| **Kural KIMLIĞI** | IDE0003 ve IDE0009 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-Visual Basic içinde `this.` C# veya `Me.` ile önceden kullanıma hazır olmak Için alanları tercih et<br /><br />`false`-`this.` veya `Me.` kullanıma hazır _olmayan_ alanları tercih et |
| **Visual Studio varsayılanı** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_property"></a>DotNet\_Style\_niteleme\_for_property

|||
|-|-|
| **Kural adı** | dotnet_style_qualification_for_property |
| **Kural KIMLIĞI** | IDE0003 ve IDE0009 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-Visual Basic içinde `this.` C# veya `Me.` ile önceden çıkacak özellikleri tercih et<br /><br />`false`-`this.` veya `Me.` kullanıma hazır _olmayan_ özellikleri tercih et |
| **Visual Studio varsayılanı** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_method"></a>DotNet\_Style\_niteleme\_for_method

|||
|-|-|
| **Kural adı** | dotnet_style_qualification_for_method |
| **Kural KIMLIĞI** | IDE0003 ve IDE0009 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-Visual Basic içinde `this.` C# veya `Me.` ile önceden kullanıma hazır olmak Için Yöntemler tercih edilir.<br /><br />`false`-`this.` veya `Me.`birlikte kullanıma hazır _olmayan_ Yöntemler tercih edilir. |
| **Visual Studio varsayılanı** | `false:silent` |

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

#### <a name="dotnet_style_qualification_for_event"></a>DotNet\_Style\_niteleme\_for_event

|||
|-|-|
| **Kural adı** | dotnet_style_qualification_for_event |
| **Kural KIMLIĞI** | IDE0003 ve IDE0009 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-Visual Basic ' de `this.` C# veya `Me.` ile önceden çıkacak olayları tercih edin.<br /><br />`false`-`this.` veya `Me.`birlikte kullanıma hazır _olmayan_ olayları tercih et. |
| **Visual Studio varsayılanı** | `false:silent` |

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

### <a name="language-keywords"></a>Tür başvuruları için çerçeve türü adları yerine dil anahtar sözcükleri

Bu stil kuralı yerel değişkenlere, yöntem parametrelerine ve sınıf üyelerine veya üye erişim ifadeleri yazmak için ayrı bir kural olarak uygulanabilir. **True** değeri, dil anahtar sözcüğünü `Integer``int` (örneğin, `Int32`) değil, bunları temsil etmek için anahtar sözcüğü olan türler için tercih eder. **False** değeri, Language anahtar sözcüğü yerine tür adını tercih eder anlamına gelir.

Bu kurallar bir *. editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>\_\_\_\_\_Yereller\_için öntanımlı tür stili parameters_members

|||
|-|-|
| **Kural adı** | dotnet_style_predefined_type_for_locals_parameters_members |
| **Kural KIMLIĞI** | IDE0012 ve IDE0014 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-yerel değişkenler, yöntem parametreleri ve sınıf üyeleri için tür adı yerine, bunları temsil eden bir anahtar sözcük içeren türler için dil anahtar sözcüğünü tercih et<br /><br />`false`-dil anahtar sözcüğü yerine yerel değişkenler, yöntem parametreleri ve sınıf üyeleri için tür adını tercih edin |
| **Visual Studio varsayılanı** | `true:silent` |

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

#### <a name="dotnet_style_predefined_type_for_member_access"></a>DotNet\_Style\_önceden tanımlanmış\_tür\_\_için member_access

|||
|-|-|
| **Kural adı** | dotnet_style_predefined_type_for_member_access |
| **Kural KIMLIĞI** | IDE0013 ve IDE0015 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-temsil etmek için anahtar sözcük içeren türler için tür adı yerine üye erişim ifadeleri için dil anahtar sözcüğünü tercih edin<br /><br />`false`-dil anahtar sözcüğü yerine üye erişim ifadeleri için tür adını tercih edin |
| **Visual Studio varsayılanı** | `true:silent` |

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

### <a name="normalize-modifiers"></a>Değiştirici tercihleri

Bu bölümdeki stil kuralları, erişilebilirlik değiştiricileri gerektirme, istenen değiştirici sıralama düzenini belirtme ve salt okunurdur değiştirici gerektirme dahil olmak üzere değiştirici tercihlerine devam ediyor.

Bu kurallar bir *. editorconfig* dosyasında aşağıdaki gibi görünebilir:

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

#### <a name="dotnet_style_require_accessibility_modifiers"></a>DotNet\_Style\_\_gerektiriyor accessibility_modifiers

|||
|-|-|
| **Kural adı** | dotnet_style_require_accessibility_modifiers |
| **Kural KIMLIĞI** | IDE0040 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `always`-erişilebilirlik değiştiricilerini belirtilmesini tercih edin.<br /><br />`for_non_interface_members`-genel arabirim üyeleri hariç olmak üzere erişilebilirlik değiştiricilerini tercih edin. (Bu **her zaman** ile aynıdır ve varsayılan arabirim yöntemleri C# eklerse ileride prova için eklenmiştir.)<br /><br />`never`-erişilebilirlik değiştiricilerini belirtilen şekilde tercih etmez.<br /><br />`omit_if_default`-varsayılan değiştirici olup olmadıkları sürece, erişilebilirlik değiştiricilerini belirtilmesini tercih edin. |
| **Visual Studio varsayılanı** | `for_non_interface_members:silent` |
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
| **Kural KIMLIĞI** | IDE0036 |
| **Uygun diller** | C# |
| **Değerler** | `public`, `private`C# ve `protected` gibi bir veya daha fazla değiştirici |
| **Visual Studio varsayılanı** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.5 |

- Bu kural bir değiştiriciler listesine ayarlandığında, belirtilen sıralamayı tercih edin.
- Bu kural dosyadan atlandığında, bir değiştirici sırası tercih etmez.

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
| **Kural KIMLIĞI** | IDE0036 |
| **Uygun diller** | Visual Basic |
| **Değerler** | `Partial`, `Private`ve `Public` gibi bir veya daha fazla Visual Basic değiştiricisi |
| **Visual Studio varsayılanı** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.5 |

- Bu kural bir değiştiriciler listesine ayarlandığında, belirtilen sıralamayı tercih edin.
- Bu kural dosyadan atlandığında, bir değiştirici sırası tercih etmez.

Kod örnekleri:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Kural adı** | dotnet_style_readonly_field |
| **Kural KIMLIĞI** | IDE0044 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-yalnızca satır içi olarak veya bir oluşturucunun içinde varsaC#, `readonly` () veya `ReadOnly` (Visual Basic) ile Işaretlenmesinin tercih edilmesi gerekir<br /><br />`false`-alanların `readonly` (C#) veya `ReadOnly` (Visual Basic) ile işaretlenmesi gerekip gerekmediğini belirlemek için tercih yok |
| **Visual Studio varsayılanı** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,7 |

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

### <a name="parentheses-preferences"></a>Parantez tercihleri

Bu bölümdeki stil kuralları, aritmetik, ilişkisel ve diğer ikili işleçler için parantez kullanımı dahil olmak üzere parantezler tercihlerine yöneliktir.

Bu kurallar bir *. editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>DotNet\_Style\_parantez\_\_aritmetik\_binary_operators

|||
|-|-|
| **Kural adı** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **Kural KIMLIĞI** | IDE0047 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `always_for_clarity`-aritmetik işleci (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) önceliğini netleştirmek için parantezleri tercih et<br /><br />`never_if_unnecessary`-aritmetik işleç (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) önceliği belirgin olduğunda parantez içermemelidir |
| **Visual Studio varsayılanı** | `always_for_clarity:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,8 |

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

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>DotNet\_Style\_parantez\_\_ilişkisel\_binary_operators

|||
|-|-|
| **Kural adı** | dotnet_style_parentheses_in_relational_binary_operators |
| **Kural KIMLIĞI** | IDE0047 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `always_for_clarity`-ilişkisel işleci (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) önceliğini netleştirmek için parantezleri tercih et<br /><br />`never_if_unnecessary`-ilişkisel operatör (`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) önceliği belirgin olduğunda parantez içermemelidir |
| **Visual Studio varsayılanı** | `always_for_clarity:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,8 |

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

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>DotNet\_Style\_parantez\_diğer\_\_binary_operators

|||
|-|-|
| **Kural adı** | dotnet_style_parentheses_in_other_binary_operators |
| **Kural KIMLIĞI** | IDE0047 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `always_for_clarity`-diğer ikili işleci (`&&`, `||`, `??`) önceliğini netleştirmek için parantezleri tercih et<br /><br />`never_if_unnecessary`-diğer ikili işleç (`&&`, `||`, `??`) önceliği açık olduğunda parantez içermemelidir |
| **Visual Studio varsayılanı** | `always_for_clarity:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,8 |

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

#### <a name="dotnet_style_parentheses_in_other_operators"></a>\_other_operators\_DotNet\_Style\_parantez

|||
|-|-|
| **Kural adı** | dotnet_style_parentheses_in_other_operators |
| **Kural KIMLIĞI** | IDE0047 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `always_for_clarity`-işleç önceliğini netleştirmek için parantezleri tercih et<br /><br />`never_if_unnecessary`-işleç önceliği belirgin olduğunda parantez içermemelidir |
| **Visual Studio varsayılanı** | `never_if_unnecessary:silent` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,8 |

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

Bu bölümdeki stil kuralları, nesne başlatıcıları, koleksiyon başlatıcıları, açık veya Çıkarsanan ad alanları ve çıkartılan anonim türler kullanımı dahil olmak üzere, ifade düzeyi tercihlere yönelik olarak sorun.

Bu kurallar bir *. editorconfig* dosyasında aşağıdaki gibi görünebilir:

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

#### <a name="dotnet_style_object_initializer"></a>DotNet\_stil\_object_initializer

|||
|-|-|
| **Kural adı** | dotnet_style_object_initializer |
| **Kural KIMLIĞI** | IDE0017 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-mümkün olduğunda nesne başlatıcıları kullanılarak başlatılacak nesneleri tercih et<br /><br />`false`-nesne başlatıcıları kullanarak *başlatılmayan* nesneleri tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

#### <a name="dotnet_style_collection_initializer"></a>DotNet\_stil\_collection_initializer

|||
|-|-|
| **Kural adı** | dotnet_style_collection_initializer |
| **Kural KIMLIĞI** | IDE0028 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-koleksiyonları mümkün olduğunda koleksiyon başlatıcıları kullanılarak başlatılacak şekilde tercih et<br /><br />`false`-koleksiyonların koleksiyon başlatıcıları kullanılarak *başlatılmamaları* tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

#### <a name="dotnet_style_explicit_tuple_names"></a>DotNet\_stil\_açık\_tuple_names

|||
|-|-|
| **Kural adı** | dotnet_style_explicit_tuple_names |
| **Kural KIMLIĞI** | IDE0033 |
| **Uygun diller** | C#7.0 + ve Visual Basic 15 + |
| **Değerler** | `true`-demet adlarını IMX özelliklerine tercih et<br /><br />`false`-tür tanımlama alanları için IMX özellikleri tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>DotNet\_Style\_\_gösterilen\_tercih eder tuple_names

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_inferred_tuple_names |
| **Kural KIMLIĞI** | IDE0037 |
| **Uygun diller** | C#7.1 + ve Visual Basic 15 + |
| **Değerler** | `true`-gösterilen demet öğesi adlarını tercih et<br /><br />`false`-açık demet öğesi adlarını tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |
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

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>DotNet\_Style\_\_\_anonim\_tür\_çıkarmayı tercih eder member_names

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **Kural KIMLIĞI** | IDE0037 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-gösterilen anonim türdeki üye adlarını tercih et<br /><br />`false`-açık anonim tür üye adlarını tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |
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

#### <a name="dotnet_style_prefer_auto_properties"></a>DotNet\_Style\_\_otomatik\_özellikleri tercih et

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_auto_properties |
| **Kural KIMLIĞI** | IDE0032 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-özel yedekleme alanları olan özellikler üzerinde oto özellikleri tercih et<br /><br />`false`-gizli özellikler üzerinde özel yedekleme alanları ile özellikleri tercih edin |
| **Visual Studio varsayılanı** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,7 |

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

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>DotNet\_Style\_\_tercih\_null\_\_\_\_\_

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Kural KIMLIĞI** | IDE0041 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-`object.ReferenceEquals` üzerinde kalıp eşleme ile null bir denetim kullanmayı tercih edin<br /><br />`false`-`object.ReferenceEquals` bir null denetimi üzerinde desenler ile eşleştirme |
| **Visual Studio varsayılanı** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,7 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>DotNet\_Style\_koşullu\_ifade\_\_tercih eder over_assignment

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_conditional_expression_over_assignment |
| **Kural KIMLIĞI** | IDE0045 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-Else bildiriminde Üçlü koşullu olarak atamaları tercih edin<br /><br />`false`-Üçlü koşullu bir if-else ifadesiyle atamaları tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,8 |

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

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>DotNet\_Style\_koşullu\_ifade\_\_tercih eder over_return

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_conditional_expression_over_return |
| **Kural KIMLIĞI** | IDE0046 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-if-else deyimi üzerinde Üçlü koşullu koşul kullanmak için return deyimlerini tercih et<br /><br />`false`-Return deyimlerini, Üçlü koşullu koşullu bir if-else deyimi kullanacak şekilde tercih eder |
| **Visual Studio varsayılanı** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,8 |

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

#### <a name="dotnet_style_prefer_compound_assignment"></a>DotNet\_Style\_bileşik\_atamasını\_tercih eder

|||
|-|-|
| **Kural adı** | dotnet_style_prefer_compound_assignment |
| **Kural KIMLIĞI** | IDE0054 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`- [bileşik atama](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment) Ifadelerini tercih et<br /><br />`false`-bileşik atama ifadelerini tercih etmeyin |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

### <a name="null-checking-preferences"></a>Null denetleme tercihleri

Bu bölümdeki stil kuralları null denetleme tercihleri ile ilgilendirin.

Bu kurallar bir *. editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
```

#### <a name="dotnet_style_coalesce_expression"></a>DotNet\_stil\_coalesce_expression

|||
|-|-|
| **Kural adı** | dotnet_style_coalesce_expression |
| **Kural KIMLIĞI** | IDE0029 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | `true`-Üçlü operatör denetimi için null birleşim ifadelerini tercih et<br /><br />`false`-Üçlü işleç denetimini null birleştirme ifadelerine kadar tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

#### <a name="dotnet_style_null_propagation"></a>DotNet\_stil\_null_propagation

|||
|-|-|
| **Kural adı** | dotnet_style_null_propagation |
| **Kural KIMLIĞI** | IDE0031 |
| **Uygun diller** | C#6.0 + ve Visual Basic 14 + |
| **Değerler** | `true`-mümkün olduğunda null koşullu işleç kullanmayı tercih et<br /><br />`false`-mümkün olduğunda Üçlü null denetimi kullanmayı tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

## <a name="net-code-quality-settings"></a>.NET kod kalitesi ayarları

Bu bölümdeki kalite kuralları hem hem de C# Visual Basic koduna uygulanır. Visual Studio tümleşik geliştirme ortamında (IDE) yerleşik olarak bulunan kod Çözümleyicileri yapılandırmak için kullanılırlar. Bir EditorConfig dosyası ile FxCop çözümleyicileri yapılandırma hakkında bilgi için bkz. [FxCop çözümleyicileri yapılandırma](../code-quality/configure-fxcop-analyzers.md).

- [Parametre tercihleri](#parameter-preferences)
  - DotNet\_kod\_kalitesi\_kullanılmayan\_parametreleri

### <a name="parameter-preferences"></a>Parametre tercihleri

Bu bölümdeki kalite kuralları Yöntem parametrelerine önem vermez.

Bu kurallar bir *. editorconfig* dosyasında aşağıdaki gibi görünebilir:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>DotNet\_kod\_kalitesi\_kullanılmayan\_parametreleri

|||
|-|-|
| **Kural adı** | dotnet_code_quality_unused_parameters |
| **Kural KIMLIĞI** | IDE0060 |
| **Uygun diller** | C# ve Visual Basic |
| **Değerler** | Kullanılmayan parametreleri içeren herhangi bir erişilebilirliği içeren `all` bayrak yöntemleri<br /><br />`non_public`-yalnızca kullanılmayan parametreleri içeren genel olmayan metotları Işaretle |
| **Visual Studio varsayılanı** | `all:suggestion` |

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

## <a name="c-code-style-settings"></a>C#kod stili ayarları

Bu bölümdeki stil kuralları yalnızca için C# geçerlidir.

- [Örtük ve açık türler](#implicit-and-explicit-types)
  - CSharp\_Style\_var\_\_oluşturulan\_için in_types
  - CSharp\_Style\_var\_\_tür\_is_apparent
  - CSharp\_Style\_var_elsewhere
- [İfade gövdeli üyeler](#expression-bodied-members)
  - CSharp\_Style\_ifade\_bodied_methods
  - CSharp\_Style\_ifade\_bodied_constructors
  - CSharp\_Style\_ifade\_bodied_operators
  - CSharp\_Style\_ifade\_bodied_properties
  - CSharp\_Style\_ifade\_bodied_indexers
  - CSharp\_Style\_ifade\_bodied_accessors
  - CSharp\_Style\_ifade\_bodied_lambdas
  - CSharp\_Style\_ifade\_gövdeli\_local_functions
- [Desen eşleştirme](#pattern-matching)
  - CSharp\_Style\_deseninin\_\_üzerinde eşleşen\_\_\_cast_check
  - CSharp\_Style\_deseninin\_üzerindeki\_\_\_\_ile eşleştirme null_check
- [Satır içi değişken bildirimleri](#inlined-variable-declarations)
  - CSharp\_stili\_satır içine alınmış\_variable_declaration
- [İfade düzeyi tercihleri](#c-expression-level-preferences)
  - CSharp\_\_basit\_tercih eder default_expression
- ["Null" Denetim tercihleri](#c-null-checking-preferences)
  - CSharp\_Style\_throw_expression
  - CSharp\_Style\_koşullu\_delegate_call
- [Kod bloğu tercihleri](#code-block-preferences)
  - CSharp\_prefer_braces
- [Kullanılmayan değer tercihleri](#unused-value-preferences)
  - CSharp\_Style\_kullanılmayan\_değer\_ifade\_statement_preference
  - CSharp\_Style\_kullanılmayan\_değeri\_assignment_preference
- [Dizin ve Aralık tercihleri](#index-and-range-preferences)
  - CSharp\_Style\_\_tercih eder index_operator
  - CSharp\_Style\_\_tercih eder range_operator
- [Çeşitli tercihler](#miscellaneous-preferences)
  - CSharp\_Style\_ayrıştırılmış\_variable_declaration
  - CSharp\_Style\_deseninin\_yerel\_\_
  - \_yönergesini\_yerleştirme kullanarak CSharp\_
  - CSharp\_\_statik\_tercih eder local_function
  - CSharp\_\_basit\_tercih eder using_statement
  - CSharp\_Style\_\_tercih eder switch_expression

### <a name="implicit-and-explicit-types"></a>Örtük ve açık türler

Bu bölümdeki stil kuralları, [var](/dotnet/csharp/language-reference/keywords/var) olan anahtar sözcüğünün kullanımını ve değişken bildiriminde açık bir tür ile ilgilendirin. Bu kural, türü görünür olduğunda ve başka bir yerde yerleşik türlere ayrı olarak uygulanabilir.

Örnek *. editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>CSharp\_Style\_var\_\_oluşturulan\_için in_types

|||
|-|-|
| **Kural adı** | csharp_style_var_for_built_in_types |
| **Kural KIMLIĞI** | IDE0007 ve IDE0008 |
| **Uygun diller** | C#  |
| **Değerler** | `true`-`var`, `int` gibi yerleşik sistem türleriyle değişkenleri bildirmek için kullanılmasını tercih eder<br /><br />`false`-`int` gibi yerleşik sistem türleriyle değişkenleri bildirmek için `var` üzerinde açık tür kullanmayı tercih edin |
| **Visual Studio varsayılanı** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>CSharp\_Style\_var\_\_tür\_is_apparent

|||
|-|-|
| **Kural adı** | csharp_style_var_when_type_is_apparent |
| **Kural KIMLIĞI** | IDE0007 ve IDE0008 |
| **Uygun diller** | C#  |
| **Değerler** | `true`-tür bir bildirim ifadesinin sağ tarafında zaten bahsedildiğinde `var` tercih eder<br /><br />`false`-tür bir bildirim ifadesinin sağ tarafında zaten bahsedildiğinde `var` açık türü tercih et |
| **Visual Studio varsayılanı** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>CSharp\_Style\_var_elsewhere

|||
|-|-|
| **Kural adı** | csharp_style_var_elsewhere |
| **Kural KIMLIĞI** | IDE0007 ve IDE0008 |
| **Uygun diller** | C#  |
| **Değerler** | `true`-başka bir kod stili kural tarafından geçersiz kılınmadığı müddetçe, her durumda açık tür üzerinde `var` tercih edin<br /><br />`false`-başka bir kod stili kuralı tarafından geçersiz kılınmadığı müddetçe, her durumda `var` açık türü tercih et |
| **Visual Studio varsayılanı** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>İfade gövdeli üyeler

Bu bölümdeki stil kuralları, mantık tek bir ifadeden oluşur [ifadesi Bodied üyelerin](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) kullanımına neden olabilir. Bu kural metotlar, oluşturucular, işleçler, özellikler, Dizin oluşturucular ve erişimciler için uygulanabilir.

Örnek *. editorconfig* dosyası:

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

#### <a name="csharp_style_expression_bodied_methods"></a>CSharp\_Style\_ifade\_bodied_methods

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_methods |
| **Kural KIMLIĞI** | IDE0022 |
| **Uygun diller** | C#6.0 +  |
| **Değerler** | `true`-yöntemler için ifade gövdeleri tercih et<br /><br />`when_on_single_line`-tek satırlık olmaları durumunda yöntemler için ifade gövdeleri tercih eder<br /><br />`false`-yöntemler için blok gövdeleri tercih et |
| **Visual Studio varsayılanı** | `false:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>CSharp\_Style\_ifade\_bodied_constructors

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_constructors |
| **Kural KIMLIĞI** | IDE0021 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-oluşturucular için ifade gövdeleri tercih et<br /><br />`when_on_single_line`-tek satır olabilecekleri oluşturucular için ifade gövdeleri tercih et<br /><br />`false`-oluşturucular için blok gövdeleri tercih et |
| **Visual Studio varsayılanı** | `false:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>CSharp\_Style\_ifade\_bodied_operators

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_operators |
| **Kural KIMLIĞI** | IDE0023 ve IDE0024 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-işleçler için ifade gövdeleri tercih et<br /><br />`when_on_single_line`-tek satırlarsa işleçler için ifade gövdeleri tercih eder<br /><br />`false`-operatörler için blok gövdeleri tercih et |
| **Visual Studio varsayılanı** | `false:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>CSharp\_Style\_ifade\_bodied_properties

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_properties |
| **Kural KIMLIĞI** | IDE0025 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-özellikler için ifade gövdelerini tercih et<br /><br />`when_on_single_line`-tek satırlarsa özellikler için ifade gövdeleri tercih eder<br /><br />`false`-özellikler için blok gövdeleri tercih et |
| **Visual Studio varsayılanı** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>CSharp\_Style\_ifade\_bodied_indexers

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_indexers |
| **Kural KIMLIĞI** | IDE0026 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-Dizin oluşturucular için ifade gövdeleri tercih et<br /><br />`when_on_single_line`-tek satır olması durumunda Dizin oluşturucular için ifade gövdeleri tercih eder<br /><br />`false`-Dizin oluşturucular için blok gövdeleri tercih et |
| **Visual Studio varsayılanı** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>CSharp\_Style\_ifade\_bodied_accessors

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_accessors |
| **Kural KIMLIĞI** | IDE0027 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-erişimciler için ifade gövdeleri tercih et<br /><br />`when_on_single_line`-tek satır olması durumunda erişimciler için ifade gövdeleri tercih eder<br /><br />`false`-erişimciler için blok gövdeleri tercih et |
| **Visual Studio varsayılanı** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>CSharp\_Style\_ifade\_bodied_lambdas

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_lambdas |
| **Kural KIMLIĞI** | IDE0053 |
| **Değerler** | `true`-Lambdalar için ifade gövdelerinin tercih edilmesi<br /><br />`when_on_single_line`-tek satırlarsa Lambdalar için ifade gövdeleri tercih eder<br /><br />`false`-Lambdalar için blok gövdeleri tercih et |
| **Visual Studio varsayılanı** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>CSharp\_Style\_ifade\_gövdeli\_local_functions

7,0 ile C# başlayarak C# [Yerel işlevleri](/dotnet/csharp/programming-guide/classes-and-structs/local-functions)destekler. Yerel işlevler, başka bir üyede iç içe yerleştirilmiş bir türün özel yöntemleridir.

|||
|-|-|
| **Kural adı** | csharp_style_expression_bodied_local_functions |
| **Kural KIMLIĞI** | IDE0061 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-yerel işlevler için ifade gövdeleri tercih et<br /><br />`when_on_single_line`-tek satır olacak şekilde yerel işlevler için ifade gövdeleri tercih edin<br /><br />`false`-yerel işlevler için blok gövdeleri tercih et |
| **Visual Studio varsayılanı** | `false:silent` |

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

Bu bölümdeki stil kuralları ' de C# [model eşleme](/dotnet/csharp/pattern-matching) kullanımını sorun.

Örnek *. editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>CSharp\_Style\_deseninin\_\_üzerinde eşleşen\_\_\_cast_check

|||
|-|-|
| **Kural adı** | csharp_style_pattern_matching_over_is_with_cast_check |
| **Kural KIMLIĞI** | IDE0020 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-tür atamaları olan `is` ifadeler yerine kalıp eşleştirmeyi tercih et<br /><br />`false`-tür atamaları olan `is` ifadeleri desenler eşleme yerine tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>CSharp\_Style\_deseninin\_üzerindeki\_\_\_\_ile eşleştirme null_check

|||
|-|-|
| **Kural adı** | csharp_style_pattern_matching_over_as_with_null_check |
| **Kural KIMLIĞI** | IDE0019 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-belirli bir türün bir şeyin olup olmadığını anlamak üzere null denetimleri olan `as` ifadeler yerine kalıp eşleştirmeyi tercih et<br /><br />`false`-belirli bir türün bir şeyin olup olmadığını anlamak için kalıp eşleme yerine null denetimleri ile `as` ifadelerini tercih edin |
| **Visual Studio varsayılanı** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Satır içi değişken bildirimleri

Bu stil kuralı `out` değişkenlerinin satır içi olarak verilip verilmeyeceğini belirtir. C# 7 ' den başlayarak, ayrı bir değişken bildiriminde değil, [yöntem çağrısının bağımsız değişken listesinde bir out değişkeni bildirebilirsiniz](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument).

#### <a name="csharp_style_inlined_variable_declaration"></a>CSharp\_stili\_satır içine alınmış\_variable_declaration

|||
|-|-|
| **Kural adı** | csharp_style_inlined_variable_declaration |
| **Kural KIMLIĞI** | IDE0018 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-mümkün olduğunda bir yöntem çağrısının bağımsız değişken listesinde `out` değişkenlerin satır içi olarak bildirilmesini tercih et<br /><br />`false`-yöntem çağrısından önce `out` değişkenlerin bildirilmesini tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Örnek *. editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>C#ifade düzeyi tercihleri

Bu bölümdeki stil kuralları, ifade düzeyi tercihlerine önem vermez.

Örnek *. editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>CSharp\_\_basit\_tercih eder default_expression

Bu stil kuralı, derleyicinin ifadenin türünü çıkardığı zaman [varsayılan değer ifadeleri için`default` değişmez](/dotnet/csharp/language-reference/operators/default#default-literal) değeri kullanılarak ilgilidir.

|||
|-|-|
| **Kural adı** | csharp_prefer_simple_default_expression |
| **Kural KIMLIĞI** | IDE0034 |
| **Uygun diller** | C#7.1 +  |
| **Değerler** | `true`-`default(T)` üzerinde `default` tercih et<br /><br />`false`-`default` üzerinde `default(T)` tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>C#null denetleme tercihleri

Bu stil kuralları, `throw` ifadeleri veya `throw` deyimlerini kullanma ve null denetim yapılıp yapılmayacağını ya da bir [lambda ifadesi](/dotnet/csharp/lambda-expressions)çağrılırken koşullu birleştirme işlecini (`?.`) kullanmak gibi `null` denetimi etrafında sözdizimini sorun.

Örnek *. editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>CSharp\_Style\_throw_expression

|||
|-|-|
| **Kural adı** | csharp_style_throw_expression |
| **Kural KIMLIĞI** | IDE0016 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-`throw` deyimler yerine `throw` ifadeleri kullanmayı tercih et<br /><br />`false`-`throw` ifadeleri yerine `throw` deyimlerini kullanmayı tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>CSharp\_Style\_koşullu\_delegate_call

|||
|-|-|
| **Kural adı** | csharp_style_conditional_delegate_call |
| **Kural KIMLIĞI** | IDE0041 |
| **Uygun diller** | C#6.0 +  |
| **Değerler** | `true`-bir lambda ifadesi çağrılırken, null denetimi yapmak yerine koşullu birleştirme işlecini (`?.`) kullanma konusuna bakın<br /><br />`false`-koşullu birleştirme işlecini (`?.`) kullanmak yerine bir lambda ifadesini çağırmadan önce null denetimi gerçekleştirmeyi tercih eder |
| **Visual Studio varsayılanı** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Kod bloğu tercihleri

Bu stil kuralı, kod bloklarını çevrelemek için `{ }` küme ayraçları kullanımı ile ilgilidir.

Örnek *. editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>CSharp\_\_ayraçları tercih et

|||
|-|-|
| **Kural adı** | csharp_prefer_braces |
| **Kural KIMLIĞI** | IDE0011 |
| **Uygun diller** | C# |
| **Değerler** | `true`-tek bir kod satırı bile küme ayraçları tercih et<br /><br />`false`-izin verildiğinde küme ayracı olmadan tercih et<br /><br />`when_multiline`-birden çok satırda küme ayraçları tercih etme |
| **Visual Studio varsayılanı** | `true:silent` |

Kod örnekleri:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Kullanılmayan değer tercihleri

Bu stil kuralları kullanılmayan ifadelere ve değer atamalarına sorun.

Örnek *. editorconfig* dosyası:

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
| **Kural KIMLIĞI** | IDE0058 |
| **Uygun diller** | C# |
| **Değerler** | `discard_variable`-bir [atma](/dotnet/csharp/discards) için kullanılmamış bir Ifade atamayı tercih et <br /><br />`unused_local_variable`-bir yerel değişkene kullanılmamış bir ifade atamayı tercih et |
| **Visual Studio varsayılanı** | `discard_variable:silent` |

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
| **Kural KIMLIĞI** | IDE0059 |
| **Uygun diller** | C# |
| **Değerler** | `discard_variable`-kullanılmayan bir değer atarken [atmayı](/dotnet/csharp/discards) kullanmayı tercih et<br /><br />`unused_local_variable`-kullanılmayan bir değer atarken yerel bir değişken kullanmayı tercih et |
| **Visual Studio varsayılanı** | `discard_variable:suggestion` |

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

### <a name="index-and-range-preferences"></a>Dizin ve Aralık tercihleri

Bu stil kuralları, C# 8,0 ve üzeri sürümlerde kullanılabilen dizin ve Aralık işleçleri kullanımını sorun.

Örnek *. editorconfig* dosyası:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>CSharp\_Style\_\_tercih eder index_operator

|||
|-|-|
| **Kural adı** | csharp_style_prefer_index_operator |
| **Kural KIMLIĞI** | IDE0056 |
| **Uygun diller** | C#8.0 + |
| **Değerler** | `true`-bir koleksiyonun sonundan bir dizin hesaplarken `^` işlecini kullanmayı tercih eder<br /><br />`false`-bir koleksiyonun sonundan Dizin hesaplarken `^` işlecini kullanmayı tercih etmeyin |
| **Visual Studio varsayılanı** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>CSharp\_Style\_\_tercih eder range_operator

|||
|-|-|
| **Kural adı** | csharp_style_prefer_range_operator |
| **Kural KIMLIĞI** | IDE0057 |
| **Uygun diller** | C#8.0 + |
| **Değerler** | `true`-bir koleksiyonun "dilimini" ayıkladığınızda Aralık işleci `..` kullanmayı tercih eder<br /><br />`false`-bir koleksiyonun "dilimini" ayıkladığınızda Aralık işleci `..` kullanmayı tercih etmeyin |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

Bu bölüm çeşitli stil kurallarını içerir.

Örnek *. editorconfig* dosyası:

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

#### <a name="csharp_style_deconstructed_variable_declaration"></a>CSharp\_Style\_ayrıştırılmış\_variable_declaration

|||
|-|-|
| **Kural adı** | csharp_style_deconstructed_variable_declaration |
| **Kural KIMLIĞI** | IDE0042 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-oluşturulmuş değişken bildirimini tercih et<br /><br />`false`-değişken bildirimlerinde oluşturmayı tercih etme |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>CSharp\_Style\_deseninin\_yerel\_\_

7,0 ile C# başlayarak C# [Yerel işlevleri](/dotnet/csharp/programming-guide/classes-and-structs/local-functions)destekler. Yerel işlevler, başka bir üyede iç içe yerleştirilmiş bir türün özel yöntemleridir.

|||
|-|-|
| **Kural adı** | csharp_style_pattern_local_over_anonymous_function |
| **Kural KIMLIĞI** | IDE0039 |
| **Uygun diller** | C#7.0 + |
| **Değerler** | `true`-anonim işlevler üzerinde yerel işlevleri tercih et<br /><br />`false`-yerel işlevler üzerinde anonim işlevleri tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

#### <a name="csharp_using_directive_placement"></a>\_directive_placement kullanarak CSharp\_

|||
|-|-|
| **Kural adı** | csharp_using_directive_placement |
| **Kural KIMLIĞI** | IDE0065 |
| **Uygun diller** | C# |
| **Değerler** | `outside_namespace`-`using` yönergelerinin ad alanı dışına yerleştirilmesini tercih et<br /><br />`inside_namespace`-ad alanı içine yerleştirilecek `using` yönergeleri tercih et |
| **Visual Studio varsayılanı** | `outside_namespace:silent` |

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

#### <a name="csharp_prefer_static_local_function"></a>CSharp\_\_statik\_tercih eder local_function

|||
|-|-|
| **Kural adı** | csharp_prefer_static_local_function |
| **Kural KIMLIĞI** | IDE0062 |
| **Uygun diller** | C#8.0 + |
| **Değerler** | `true`-yerel işlevlerin işaretlenmesini tercih et `static`<br /><br />`false`-yerel işlevlerin işaretlenmesini tercih etmeyin `static` |
| **Visual Studio varsayılanı** | `true:suggestion` |

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

#### <a name="csharp_prefer_simple_using_statement"></a>CSharp\_\_basit\_tercih eder using_statement

|||
|-|-|
| **Kural adı** | csharp_prefer_simple_using_statement |
| **Kural KIMLIĞI** | IDE0063 |
| **Uygun diller** | C#8.0 + |
| **Değerler** | `true`- *basit* bir `using` Ifadesini kullanmayı tercih et<br /><br />`false`- *basit* bir `using` ifadesini kullanmayı tercih etmeyin |
| **Visual Studio varsayılanı** | `true:suggestion` |

Kod örnekleri:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>CSharp\_Style\_\_tercih eder switch_expression

|||
|-|-|
| **Kural adı** | csharp_style_prefer_switch_expression |
| **Kural KIMLIĞI** | IDE0066 |
| **Uygun diller** | C#8.0 + |
| **Değerler** | `true`-`switch` ifadesi (8,0 ile C# tanıtılan) kullanmayı tercih et<br /><br />`false`- [switch ifadesinin](/dotnet/csharp/language-reference/keywords/switch) kullanılmasını tercih et |
| **Visual Studio varsayılanı** | `true:suggestion` |
| **Tanıtılan sürüm** | Visual Studio 2019 sürüm 16,2 |

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
