---
title: .NET EditorConfig için biçimlendirme kuralları
ms.date: 03/31/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f10d4c710c0686b22e29883cabc21550ffd32f8c
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80527963"
---
# <a name="formatting-conventions"></a>Biçimlendirme kuralları

Visual Studio için EditorConfig için biçimlendirme kuralları şu kategorilere girer:

- [.NET biçimlendirme ayarları](#net-formatting-settings)

- [C# biçimlendirme ayarları](#c-formatting-settings)

## <a name="rule-format"></a>Kural biçimi

Kuralları biçimlendirme kuralları aşağıdaki biçime sahiptir:

`rule_name = value`

Birçok kural için, `true` 'yi belirtiniz `false` (bu stili tercih edin) veya (bu stili tercih etmeyin) için. `value` Diğer kurallar için, kuralın `flush_left` ne `before_and_after` zaman ve nerede uygulanacağınız gibi bir değer belirtirsiniz. Bir önem belirtmedin.

## <a name="net-formatting-settings"></a>.NET biçimlendirme ayarları

Bu bölümdeki biçimlendirme kuralları C# ve Visual Basic koduna uygulanır.

- [Kullanımı düzenleme](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Yönergeleri kullanarak düzenleme

Bu biçimlendirme kuralları yönergelerin ve `using` deyimlerin `Imports` sıralanması ve görüntülenmesiyle ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>dotnet\_\_sıralama\_sistemi directives_first

|||
|-|-|
| **Kural adı** | dotnet_sort_system_directives_first |
| **Geçerli diller** | C# ve Visual Basic |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Sistem.* `using` yönergelerini alfabetik olarak sıralayın ve bunları diğer yönergelerden önce yerleştirin.<br /><br />`false`- Sistem.* `using` direktiflerini diğer `using` direktiflerden önce yerleştirmeyin. |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a>dotnet\_\_ayrı\_\_ithalat direktifi grupları

|||
|-|-|
| **Kural adı** | dotnet_separate_import_directive_groups |
| **Geçerli diller** | C# ve Visual Basic |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.5 |
| **Değer** | `true`- Yönerge grupları `using` arasına boş bir satır yerleştirin.<br /><br />`false`- Yönerge grupları arasına `using` boş bir satır yerleştirmeyin. |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-settings"></a>C# biçimlendirme ayarları

Bu bölümdeki biçimlendirme kuralları yalnızca C# koduna uygulanır.

- [Yeni hat seçenekleri](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Girintisi seçenekleri](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Aralık seçenekleri](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [Kaydırma seçenekleri](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks
- [Yönerge seçeneklerini kullanma](#using-directive-options) 
  - csharp_using_directive_placement

### <a name="new-line-options"></a>Yeni hat seçenekleri

Bu biçimlendirme kuralları, kodu biçimlendirmek için yeni satırların kullanılmasıyla ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a>csharp\_\_yeni\_\_satır önce open_brace

Bu kural, açık `{` bir ayraç önceki kodla aynı satıra mı yoksa yeni bir satıra mı yerleştirilmesi gerektiğiyle ilgilidir. Bu kural için, bu kuralın ne zaman uygulanması gerektiğini tanımlamak için **tüm**, **yok**veya **yöntemler** veya **özellikler**gibi bir veya daha fazla kod öğesi belirtirsiniz. Birden çok kod öğesi belirtmek için, bunları virgülle (,) ayırın.

|||
|-|-|
| **Kural adı** | csharp_new_line_before_open_brace |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `all`- Tüm ifadeler ("Allman" stili) için parantezin yeni bir satırda olmasını gerektirir.<br /><br />`none`- Tüm ifadeler için ayraçların aynı satırda olmasını gerektirir ("K&R").<br /><br />`accessors`, `anonymous_methods` `anonymous_types`, `control_blocks` `events`, `indexers` `local_functions` `methods` `object_collection_array_initializers` `properties`, , , `types` , , , , , , , - Parantezin belirtilen kod öğesi ("Allman" stili) için yeni bir satırda olmasını `lambdas`gerektirir. |
| **Visual Studio varsayılan** | `all` |

Kod örnekleri:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a>csharp\_\_yeni\_hat before_else

|||
|-|-|
| **Kural adı** | csharp_new_line_before_else |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- `else` İfadeleri yeni bir satıra yerleştirin.<br /><br />`false`- `else` İfadeleri aynı satıra yerleştirin. |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a>csharp\_\_yeni\_hat before_catch

|||
|-|-|
| **Kural adı** | csharp_new_line_before_catch |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- `catch` İfadeleri yeni bir satıra yerleştirin.<br /><br />`false`- `catch` İfadeleri aynı satıra yerleştirin. |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a>csharp\_\_yeni\_hat before_finally

|||
|-|-|
| **Kural adı** | csharp_new_line_before_finally |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- `finally` Kapanış ayracından sonra ifadelerin yeni bir satırda olmasını zorunlu kınlayın.<br /><br />`false`- `finally` İfadelerin kapanış ayracıyla aynı çizgide olmasını gerektirir. |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>\_\_\_\_csharp yeni satır\_object_initializers üyeleri önce\_

|||
|-|-|
| **Kural adı** | csharp_new_line_before_members_in_object_initializers |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Nesne başharflerinin üyelerinin ayrı satırlarda olmasını zorunlu<br /><br />`false`- Nesne başharflerinin üyelerinin aynı hatta olmasını zorunlu |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>\_\_\_\_csharp yeni hat\_anonymous_types üyeleri önce\_

|||
|-|-|
| **Kural adı** | csharp_new_line_before_members_in_anonymous_types |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Anonim türlerin üyelerinin ayrı hatlarda olmasını zorunlu<br /><br />`false`- Anonim türlerin üyelerinin aynı hatta olmasını zorunlu |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Kural adı** | csharp_new_line_between_query_expression_clauses |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Sorgu ifade yan tümcelerinin öğelerinin ayrı satırlarda olmasını gerektirme<br /><br />`false`- Sorgu ifade yan tümcelerinin öğelerinin aynı satırda olmasını gerektirir |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a>Girintisi seçenekleri

Bu biçimlendirme kuralları, girintinin kodu biçimlendirmek için kullanılmasıyla ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a>csharp\_girinti\_case_contents

|||
|-|-|
| **Kural adı** | csharp_indent_case_contents |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Girintisi `switch` servis talebi içeriği<br /><br />`false`- `switch` Kasa içeriğini girintisi yapmayın |
| **Visual Studio varsayılan** | `true` |

- Bu kural **doğru**ayarlandığında , i.
- Bu kural **yanlış**olarak ayarlandığında , d.

Kod örnekleri:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a>csharp\_girinti\_switch_labels

|||
|-|-|
| **Kural adı** | csharp_indent_switch_labels |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Girintinetiketler `switch`<br /><br />`false`- Etiketleri girintisi yapmayın `switch` |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a>csharp\_indent_labels

|||
|-|-|
| **Kural adı** | csharp_indent_labels |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `flush_left`- Etiketler en soldaki sütuna yerleştirilir<br /><br />`one_less_than_current`- Etiketler, geçerli içeriğe göre bir girintin daha az<br /><br />`no_change`- Etiketler geçerli bağlamla aynı girintilere yerleştirilir |
| **Visual Studio varsayılan** | `no_change` |

Kod örnekleri:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a>csharp_indent_block_contents

|||
|-|-|
| **Kural adı** | csharp_indent_block_contents |
| **Geçerli diller** | C# |
| **Değer** | `true` - <br /><br />`false` -  |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a>csharp_indent_braces

|||
|-|-|
| **Kural adı** | csharp_indent_braces |
| **Geçerli diller** | C# |
| **Değer** | `true` - <br /><br />`false` -  |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a>csharp_indent_case_contents_when_block

|||
|-|-|
| **Kural adı** | csharp_indent_case_contents_when_block |
| **Geçerli diller** | C# |
| **Değer** | `true` - <br /><br />`false` -  |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a>Aralık seçenekleri

Bu biçimlendirme kuralları, kodu biçimlendirmek için alan karakterlerinin kullanımıyla ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a>csharp\_\_uzay after_cast

|||
|-|-|
| **Kural adı** | csharp_space_after_cast |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Bir boşluk karakterini döküm ve değer arasına yerleştirin<br /><br />`false`- Döküm ve değer arasındaki boşluğu kaldırın |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Kural adı** | csharp_space_after_keywords_in_control_flow_statements |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Döngü gibi `for` bir denetim akışı deyiminde bir anahtar kelimeden sonra boşluk karakterini yerleştirin<br /><br />`false`- `for` Döngü gibi bir kontrol akışı deyimindeki bir anahtar kelimeden sonra alanı kaldırma |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Kural adı** | csharp_space_between_parentheses |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `control_flow_statements`- Kontrol akış tablolarının parantezleri arasında boşluk<br /><br />`expressions`- İfadelerin parantezleri arasına boşluk yerleştirme<br /><br />`type_casts`- Tip dökümlerinde parantezler arasında boşluk yerleştirin |
| **Visual Studio varsayılan** | `false` |

Bu kuralı atlar veya `control_flow_statements`", " `expressions`veya `type_casts`, , , ayarı dışında bir değer kullanırsanız uygulanmaz.

Kod örnekleri:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>inheritance_clause\_kolon\_\_\_\_önce csharp uzay

|||
|-|-|
| **Kural adı** | csharp_space_before_colon_in_inheritance_clause |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değer** | `true`- Bir tür bildiriminde üsler veya arabirimler için üst üste bir boşluk karakteri yerleştirin<br /><br />`false`- Bir tür bildiriminde bazlar veya arabirimler için üst üste önce boşluk kaldırma |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>inheritance_clause\_kolon\_\_\_\_sonra csharp boşluk

|||
|-|-|
| **Kural adı** | csharp_space_after_colon_in_inheritance_clause |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değer** | `true`- Bir tür bildiriminde bazlar veya arabirimler için üst üste sonra bir boşluk karakteri yerleştirin<br /><br />`false`- Bir tür bildiriminde bazlar veya arabirimler için iki nokta üst üste alan kaldırma |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a>binary_operators\_etrafında\_\_csharp boşluk

|||
|-|-|
| **Kural adı** | csharp_space_around_binary_operators |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değer** | `before_and_after`- İkili işleçten önce ve sonra boşluk yerleştirin<br /><br />`none`- İkili işleçten önceki ve sonraki boşlukları kaldırın<br /><br />`ignore`- İkili işleçler etrafında boşluk yoksay |
| **Visual Studio varsayılan** | `before_and_after` |

Bu kuralı atlarsanız veya `before_and_after`, veya `none` `ignore`, , , dışında bir değer kullanırsanız, ayar uygulanmaz.

Kod örnekleri:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Kural adı** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Bir boşluk karakterini açılış parantezinden sonra ve yöntem bildirimi parametre listesinin kapanış parantezinden önce yerleştirin<br /><br />`false`- Açılış parantezinden sonra ve yöntem bildirimi parametre listesinin kapanış parantezinden önce boşluk karakterlerini kaldırma |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Kural adı** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değer** | `true`- Bir yöntem bildirimi için boş parametre listesi paranteziçinde boşluk ekleme<br /><br />`false`- Bir yöntem bildirimi için boş parametre listesi paranteziçinde boşluk kaldırma |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|||
|-|-|
| **Kural adı** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Geçerli diller** | C# |
| **Değer** | `true`- Yöntem bildiriminde yöntem adı ile açılış parantezi arasına bir boşluk karakteri yerleştirin<br /><br />`false`- Yöntem bildiriminde yöntem adı ve açılış parantezi arasındaki boşluk karakterlerini kaldırma |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Kural adı** | csharp_space_between_method_call_parameter_list_parentheses |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Açılış parantezinden sonra ve bir yöntem çağrısının kapanış parantezinden önce bir boşluk karakteri yerleştirin<br /><br />`false`- Açılış parantezinden sonra ve bir yöntemin kapanış parantezinden önce boşluk karakterlerini çıkarın |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Kural adı** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değer** | `true`- Boş bağımsız değişken listesi paranteziçinde boşluk ekleme<br /><br />`false`- Boş bağımsız değişken listesi paranteziçinde boşluk kaldırma |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Kural adı** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değer** | `true`- Yöntem çağrı adı ile açılış parantezi arasında boşluk ekleme<br /><br />`false`- Yöntem çağrı adı ve açılış parantezi arasındaki boşluğu kaldırın |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a>csharp_space_after_comma

|||
|-|-|
| **Kural adı** | csharp_space_after_comma |
| **Geçerli diller** | C# |
| **Değer** | `true`- Virgülden sonra boşluk ekleme<br /><br />`false`- Virgülden sonra alanı kaldırma |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|||
|-|-|
| **Kural adı** | csharp_space_before_comma |
| **Geçerli diller** | C# |
| **Değer** | `true`- Virgülden önce boşluk ekleme<br /><br />`false`- Virgülden önce alanı kaldırma |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|||
|-|-|
| **Kural adı** | csharp_space_after_dot |
| **Geçerli diller** | C# |
| **Değer** | `true`- Nokta dan sonra boşluk ekleme<br /><br />`false`- Bir nokta sonra boşluk kaldırma |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|||
|-|-|
| **Kural adı** | csharp_space_before_dot |
| **Geçerli diller** | C# |
| **Değer** | `true`- Noktadan önce boşluk ekleme <br /><br />`false`- Noktadan önce alanı kaldırma |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|||
|-|-|
| **Kural adı** | csharp_space_after_semicolon_in_for_statement |
| **Geçerli diller** | C# |
| **Değer** | `true`- Bir `for` deyimde her yarım kolon dan sonra boşluk yerleştirin<br /><br />`false`- Bir `for` deyimde her yarım kolon sonra boşluk kaldırın |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|||
|-|-|
| **Kural adı** | csharp_space_before_semicolon_in_for_statement |
| **Geçerli diller** | C# |
| **Değer** | `true`- Bir `for` deyimde her yarım kolon önce boşluk eklemek <br /><br />`false`- Bir `for` deyimde her yarım kolon önce boşluk kaldırın |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|||
|-|-|
| **Kural adı** | csharp_space_around_declaration_statements |
| **Geçerli diller** | C# |
| **Değer** | `ignore`- Bildirim beyanlarında fazladan boşluk karakterlerini kaldırma<br /><br />`false`- Bildirim beyanlarında fazladan boşluk karakterlerini kaldırma |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|||
|-|-|
| **Kural adı** | csharp_space_before_open_square_brackets |
| **Geçerli diller** | C# |
| **Değer** | `true`- Kare ayraçları açmadan önce boşluk ekle`[` <br /><br />`false`- Kare ayraçları açmadan önce alanı kaldırın`[` |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|||
|-|-|
| **Kural adı** | csharp_space_between_empty_square_brackets |
| **Geçerli diller** | C# |
| **Değer** | `true`- Boş kare köşeli ayraçlar arasına boşluk ekleme`[ ]` <br /><br />`false`- Boş kare köşeli ayraçlar arasındaki boşluğu kaldırın`[]` |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|||
|-|-|
| **Kural adı** | csharp_space_between_square_brackets |
| **Geçerli diller** | C# |
| **Değer** | `true`- Boş olmayan kare ayraçlara boşluk karakterleri ekleme`[ 0 ]` <br /><br />`false`- Boş olmayan kare ayraçlarda boşluk karakterlerini kaldırma`[0]` |
| **Visual Studio varsayılan** | `false` |

Kod örnekleri:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Kaydırma seçenekleri

Bu biçimlendirme kuralları, deyimler ve kod blokları için ayrı satırlara karşılık tek satırkullanımıyla ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Kural adı** | csharp_preserve_single_line_statements |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Beyannameleri ve üye beyannamelerini aynı satırda bırakın<br /><br />`false`- Beyannameleri ve üye beyannamelerini farklı satırlarda bırakın |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Kural adı** | csharp_preserve_single_line_blocks |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değer** | `true`- Kod bloğunu tek satırda bırakın<br /><br />`false`- Ayrı satırlarda kod bloğu bırakın |
| **Visual Studio varsayılan** | `true` |

Kod örnekleri:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

- [Yönerge seçeneklerini kullanma](#using-directive-options) 
  - csharp_using_directive_placement
  
### <a name="using-directive-options"></a>Yönerge seçeneklerini kullanma

Bu biçimlendirme kuralı, bir ad alanı dışında karşı içine yerleştirilen yönergeleri kullanarak kullanımı ile ilgilidir.

Örnek *.editorconfig* dosyası:

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a>csharp_using_directive_placement

|||
|-|-|
| **Kural adı** | csharp_using_directive_placement |
| **Geçerli diller** | C# |
| **Tanıtılan sürüm** |  Visual Studio 2019 sürüm 16.1 |
| **Değer** | `outside_namespace`- Ad alanı dışındaki yönergeleri kullanarak bırakın<br /><br />`inside_namespace`- Ad alanı içinde yönergeleri kullanarak bırakın |
| **Visual Studio varsayılan** | `outside_namespace` |

Kod örnekleri:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Dil kuralları](editorconfig-language-conventions.md)
- [Adlandırma kuralları](editorconfig-naming-conventions.md)
- [EditorConfig için .NET kodlama kuralı ayarları](editorconfig-code-style-settings-reference.md)
