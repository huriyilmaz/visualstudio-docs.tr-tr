---
title: EditorConfig için .NET biçimlendirme kuralları
ms.date: 07/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 42f1ab99a82f402ef6eced09ad5e47cf54122b86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652799"
---
# <a name="formatting-conventions"></a>Biçimlendirme kuralları

Visual Studio için EditorConfig 'in biçimlendirme kuralları şu kategorilere ayrılır:

- [.NET biçimlendirme ayarları](#net-formatting-settings)

- [C#biçimlendirme ayarları](#c-formatting-settings)

## <a name="rule-format"></a>Kural biçimi

Biçimlendirme kuralları için kurallar aşağıdaki biçimdedir:

`rule_name = value`

Birçok kural için, `value` için `true` (Bu stili tercih et) ya da `false` (Bu stili tercih et) belirtirsiniz. Diğer kurallar için, kuralın ne zaman ve nereye uygulanacağını betimleyen `flush_left` veya `before_and_after` gibi bir değer belirtirsiniz. Önem derecesi belirtmezsiniz.

## <a name="net-formatting-settings"></a>.NET biçimlendirme ayarları

Bu bölümdeki biçimlendirme kuralları için C# geçerlidir ve kodu Visual Basic.

- [Using deyimlerini Düzenle](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Yönergeleri kullanarak düzenleme

Bu biçimlendirme kuralları `using` yönergelerinin ve `Imports` deyimlerinin sıralanmasını ve görüntülenmesini sorun.

Örnek *. editorconfig* dosyası:

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>DotNet \_sort \_system \_directives_first

|||
|-|-|
| **Kural adı** | dotnet_sort_system_directives_first |
| **Uygun diller** | C# ve Visual Basic |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-System. * `using` yönergelerini alfabetik olarak sıralayın ve diğer using yönergelerinden önce yerleştirin.<br /><br />`false`-diğer `using` yönergelerinden önce System. * `using` yönergeleri yerleştirmeyin. |
| **Visual Studio varsayılanı** | `true` |

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

#### <a name="dotnet_separate_import_directive_groups"></a>DotNet \_separate \_import \_directive \_groups

|||
|-|-|
| **Kural adı** | dotnet_separate_import_directive_groups |
| **Uygun diller** | C# ve Visual Basic |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,5 |
| **Değerler** | `true` `using` yönerge grupları arasına boş bir satır koyun.<br /><br />`false`-`using` yönerge grupları arasına boş bir satır yerleştirmeyin. |
| **Visual Studio varsayılanı** | `false` |

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

## <a name="c-formatting-settings"></a>C#biçimlendirme ayarları

Bu bölümdeki biçimlendirme kuralları yalnızca kod için C# geçerlidir.

- [Yeni satır seçenekleri](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Girintileme seçenekleri](#indentation-options)
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
- [Sarlama seçenekleri](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>Yeni satır seçenekleri

Bu biçimlendirme kuralları kodu biçimlendirmek için yeni satırların kullanılmasını sağlar.

Örnek *. editorconfig* dosyası:

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

#### <a name="csharp_new_line_before_open_brace"></a>CSharp \_new \_line \_before \_open_brace

Bu kural, bir açık ayraç `{` önceki kodla aynı satıra veya yeni bir satıra yerleştirilmelidir. Bu kural için, bu kuralın ne zaman uygulanacağını tanımlamak üzere **Yöntemler** veya **Özellikler**gibi **All**, **none**veya bir ya da daha fazla kod öğesi belirtirsiniz. Birden çok kod öğesi belirtmek için bunları virgülle (,) ayırın.

|||
|-|-|
| **Kural adı** | csharp_new_line_before_open_brace |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `all`-küme ayracın tüm ifadeler için yeni bir satırda olması gerekir ("Allman" stili).<br /><br />`none`-ayraç, tüm ifadeler için aynı satırda olması gerekir ("K & R").<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, 0, 1-küme ayraçlarının belirtilen kod öğesi ("Allman" Style) için yeni bir satırda olması gerekir. |
| **Visual Studio varsayılanı** | `all` |

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

#### <a name="csharp_new_line_before_else"></a>CSharp \_new \_line \_before_else

|||
|-|-|
| **Kural adı** | csharp_new_line_before_else |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true` `else` deyimlerini yeni bir satıra yerleştirin.<br /><br />`false` `else` deyimlerini aynı satıra yerleştirin. |
| **Visual Studio varsayılanı** | `true` |

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

#### <a name="csharp_new_line_before_catch"></a>CSharp \_new \_line \_before_catch

|||
|-|-|
| **Kural adı** | csharp_new_line_before_catch |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true` `catch` deyimlerini yeni bir satıra yerleştirin.<br /><br />`false` `catch` deyimlerini aynı satıra yerleştirin. |
| **Visual Studio varsayılanı** | `true` |

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

#### <a name="csharp_new_line_before_finally"></a>CSharp \_new \_line \_before_finally

|||
|-|-|
| **Kural adı** | csharp_new_line_before_finally |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-`finally` deyimlerinin, kapanış ayracından sonra yeni bir satırda olmasını gerektir.<br /><br />`false`-`finally` deyimlerinin kapanış ayracı ile aynı satırda olmasını gerektir. |
| **Visual Studio varsayılanı** | `true` |

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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>CSharp \_new \_line \_before \_members \_in \_object_initializers

|||
|-|-|
| **Kural adı** | csharp_new_line_before_members_in_object_initializers |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-nesne başlatıcılarının üyelerinin ayrı satırlarda olmasını gerektir<br /><br />`false`-nesne başlatıcılarının üyelerinin aynı satırda olması gerekir |
| **Visual Studio varsayılanı** | `true` |

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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>CSharp \_new \_line \_before \_members \_in \_anonymous_types

|||
|-|-|
| **Kural adı** | csharp_new_line_before_members_in_anonymous_types |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-anonim türlerin üyelerinin ayrı satırlarda olmasını gerektir<br /><br />`false`-anonim türlerin üyelerinin aynı satırda olmasını gerektir |
| **Visual Studio varsayılanı** | `true` |

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-sorgu ifadesi yan tümcelerinin öğelerinin ayrı satırlarda olmasını gerektir<br /><br />`false`-sorgu ifadesi yan tümcelerinin öğelerin aynı satırda olmasını gerektir |
| **Visual Studio varsayılanı** | `true` |

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

### <a name="indentation-options"></a>Girintileme seçenekleri

Bu biçimlendirme kuralları kodu biçimlendirmek için girintileme kullanımını sağlar.

Örnek *. editorconfig* dosyası:

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

#### <a name="csharp_indent_case_contents"></a>CSharp \_indent \_case_contents

|||
|-|-|
| **Kural adı** | csharp_indent_case_contents |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-`switch` Case içeriğini Girintile<br /><br />`false`-`switch` Case içeriğini girintileme |
| **Visual Studio varsayılanı** | `true` |

- Bu kural **true**olarak ayarlandığında, ı.
- Bu kural **false**, d olarak ayarlandığında.

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

#### <a name="csharp_indent_switch_labels"></a>CSharp \_indent \_switch_labels

|||
|-|-|
| **Kural adı** | csharp_indent_switch_labels |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-`switch` etiketleri Girintile<br /><br />`false`-`switch` etiketleri girintileme |
| **Visual Studio varsayılanı** | `true` |

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

#### <a name="csharp_indent_labels"></a>CSharp \_indent_labels

|||
|-|-|
| **Kural adı** | csharp_indent_labels |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `flush_left` Etiketler en soldaki sütuna yerleştirilir<br /><br />`one_less_than_current` Etiketler geçerli bağlama göre daha az bir girintide yerleştirilir<br /><br />`no_change` Etiketler, geçerli bağlamla aynı girintide yer alır |
| **Visual Studio varsayılanı** | `no_change` |

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
| **Uygun diller** | C# |
| **Değerler** | `true` - <br /><br />`false` -  |
| **Visual Studio varsayılanı** | `true` |

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
| **Uygun diller** | C# |
| **Değerler** | `true` - <br /><br />`false` -  |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `true` - <br /><br />`false` -  |
| **Visual Studio varsayılanı** | `true` |

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

Bu biçimlendirme kuralları kodu biçimlendirmek için boşluk karakterlerinin kullanılmasını sağlar.

Örnek *. editorconfig* dosyası:

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

#### <a name="csharp_space_after_cast"></a>CSharp \_space \_after_cast

|||
|-|-|
| **Kural adı** | csharp_space_after_cast |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`, bir atama ve değer arasında bir boşluk karakteri yerleştir<br /><br />`false`-atama ve değer arasındaki boşluğu kaldırma |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true` bir denetim akışı deyimindeki anahtar sözcükten sonra `for` döngüsü gibi bir boşluk karakteri yerleştirme<br /><br />`false`-`for` döngüsü gibi bir denetim akışı deyimindeki anahtar sözcükten sonra boşluk kaldır |
| **Visual Studio varsayılanı** | `true` |

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `control_flow_statements`-denetim akışı deyimlerinin ayraçları arasına boşluk yerleştir<br /><br />`expressions` ifadelerin parantezleri arasına boşluk yerleştir<br /><br />`type_casts`-tür yayınlarına parantez arasına boşluk yerleştir |
| **Visual Studio varsayılanı** | `false` |

Bu kuralı atlarsanız veya `control_flow_statements`, `expressions` veya `type_casts` dışında bir değer kullanırsanız, ayar uygulanmaz.

Kod örnekleri:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>CSharp \_space \_before \_colon \_in \_inheritance_clause

|||
|-|-|
| **Kural adı** | csharp_space_before_colon_in_inheritance_clause |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,7 |
| **Değerler** | `true` bir tür bildirimindeki tabanların veya arabirimlerin üst üsteden önce bir boşluk karakteri yerleştir<br /><br />`false`-bir tür bildiriminde temeller veya arabirimler için iki noktadan önce boşluğu kaldır |
| **Visual Studio varsayılanı** | `true` |

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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>CSharp \_space \_after \_colon \_in \_inheritance_clause

|||
|-|-|
| **Kural adı** | csharp_space_after_colon_in_inheritance_clause |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,7 |
| **Değerler** | `true` bir tür bildirimindeki tabanların veya arabirimlerin iki noktadan sonra bir boşluk karakteri yerleştir<br /><br />`false`-bir tür bildirimindeki tabanların veya arabirimlerin iki noktadan sonra boşluğu kaldır |
| **Visual Studio varsayılanı** | `true` |

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

#### <a name="csharp_space_around_binary_operators"></a>CSharp \_space \_around \_binary_operators

|||
|-|-|
| **Kural adı** | csharp_space_around_binary_operators |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,7 |
| **Değerler** | `before_and_after`-ikili işleçten önce ve sonra boşluk Ekle<br /><br />`none`-ikili işleçten önce ve sonra boşlukları kaldır<br /><br />`ignore`-ikili operatörlerin çevresindeki boşlukları yoksay |
| **Visual Studio varsayılanı** | `before_and_after` |

Bu kuralı atlarsanız veya `before_and_after`, `none` veya `ignore` dışında bir değer kullanırsanız, ayar uygulanmaz.

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-açma parantezinden sonra ve bir yöntem bildirimi parametre listesinin kapatma parantezinden önce bir boşluk karakteri yerleştirin<br /><br />`false`-boşluk karakterlerini açma parantezinden sonra ve bir yöntem bildirimi parametre listesinin kapatma parantezinden önce kaldırın |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,7 |
| **Değerler** | `true`-yöntem bildirimi için boş parametre listesi ayraçları içine boşluk Ekle<br /><br />`false`-bir yöntem bildirimi için boş parametre listesi ayraçları içindeki alanı kaldır |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `true` yöntem bildiriminde Yöntem adı ve açma ayracı arasına bir boşluk karakteri yerleştirin<br /><br />`false`-yöntem bildiriminde Yöntem adı ve açma ayracı arasındaki boşluk karakterlerini kaldırın |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-açma parantezinden sonra ve bir yöntem çağrısının kapatma parantezinden önce bir boşluk karakteri yerleştirin<br /><br />`false`-boşluk karakterlerini açma parantezinden sonra ve bir yöntem çağrısının kapatma parantezinden önce kaldırın |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,7 |
| **Değerler** | `true`-boş bağımsız değişken listesi ayraçları içine boşluk Ekle<br /><br />`false`-boş bağımsız değişken listesi ayraçları içindeki alanı kaldır |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,7 |
| **Değerler** | `true`-Yöntem çağrısı adı ve açma ayracı arasına boşluk Ekle<br /><br />`false`-Yöntem çağrısı adı ve açma ayracı arasındaki boşluğu kaldır |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `true`-virgülden sonra boşluk Ekle<br /><br />`false`-virgülden sonra boşluk kaldır |
| **Visual Studio varsayılanı** | `true` |

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
| **Uygun diller** | C# |
| **Değerler** | `true`-virgülden önce boşluk Ekle<br /><br />`false`-bir virgülden önce boşluğu kaldır |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `true`-noktadan sonra boşluk Ekle<br /><br />`false`-noktadan sonra boşluk kaldır |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `true`-noktadan önce boşluk Ekle <br /><br />`false`-noktadan önce boşluğu kaldır |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `true`-`for` deyiminde her noktalı virgülden sonra boşluk Ekle<br /><br />`false`-`for` deyiminde her noktalı virgülden sonra boşluk kaldır |
| **Visual Studio varsayılanı** | `true` |

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
| **Uygun diller** | C# |
| **Değerler** | `true`-`for` deyiminde her noktalı virgülden önce boşluk Ekle <br /><br />`false`-`for` deyiminde her noktalı virgülden önce boşluk kaldır |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `ignore`-bildirim deyimlerine fazladan boşluk karakterleri kaldırmayın<br /><br />`false`-bildirim deyimlerine ek boşluk karakterlerini kaldır |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `true`-köşeli parantezleri açmadan önce boşluk Ekle `[` <br /><br />`false`-köşeli ayraçları açmadan önce alanı kaldırın `[` |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `true`-boş köşeli ayraçlar arasında boşluk Ekle `[ ]` <br /><br />`false`-boş köşeli ayraçlar arasındaki boşluğu kaldır `[]` |
| **Visual Studio varsayılanı** | `false` |

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
| **Uygun diller** | C# |
| **Değerler** | `true`-boş olmayan köşeli ayraçlar içine boşluk karakterleri ekleyin `[ 0 ]` <br /><br />`false`-boş olmayan köşeli ayraçdaki boşluk karakterlerini kaldırın `[0]` |
| **Visual Studio varsayılanı** | `false` |

Kod örnekleri:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Sarlama seçenekleri

Bu biçimlendirme kuralları, deyimler ve kod blokları için ayrı satırlara karşı tek satırların kullanımını önemli olarak kullanır.

Örnek *. editorconfig* dosyası:

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-deyimleri ve üye bildirimlerini aynı satırda bırak<br /><br />`false`-deyimleri ve üye bildirimlerini farklı satırlarda bırak |
| **Visual Studio varsayılanı** | `true` |

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
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15,3 |
| **Değerler** | `true`-kod bloğunu tek satırda bırak<br /><br />`false`-kod bloğunu ayrı satırlarda bırak |
| **Visual Studio varsayılanı** | `true` |

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

## <a name="see-also"></a>Ayrıca bkz.

- [Dil kuralları](editorconfig-language-conventions.md)
- [Adlandırma kuralları](editorconfig-naming-conventions.md)
- [EditorConfig için .NET kodlama kuralı ayarları](editorconfig-code-style-settings-reference.md)
