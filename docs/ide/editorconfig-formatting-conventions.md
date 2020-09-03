---
title: EditorConfig için .NET biçimlendirme kuralları
ms.date: 04/02/2020
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
ms.openlocfilehash: 0490912683fd683398c89e8e69b62dd3824ee04b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533477"
---
# <a name="formatting-conventions"></a>Biçimlendirme kuralları

Visual Studio için EditorConfig 'in biçimlendirme kuralları şu kategorilere ayrılır:

- [.NET biçimlendirme ayarları](#net-formatting-settings)

- [C# biçimlendirme ayarları](#c-formatting-settings)

## <a name="rule-format"></a>Kural biçimi

Biçimlendirme kuralları için kurallar aşağıdaki biçimdedir:

`rule_name = value`

Birçok kural için `true` (Bu stili tercih et) veya `false` (Bu stili tercih etme) için bir tane belirtin `value` . Diğer kurallar için, `flush_left` ya da `before_and_after` kuralın ne zaman ve nereye uygulanacağını betimleyen bir değer belirtirsiniz. Önem derecesi belirtmezsiniz.

## <a name="net-formatting-settings"></a>.NET biçimlendirme ayarları

Bu bölümdeki biçimlendirme kuralları C# ve Visual Basic kodu için geçerlidir.

- [Using deyimlerini Düzenle](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Yönergeleri kullanarak düzenleme

Bu biçimlendirme kuralları yönergeleri ve deyimleri sıralamayı ve görüntülemeyi sorun `using` `Imports` .

Örnek *. editorconfig* dosyası:

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>DotNet \_ sıralama \_ sistem \_ directives_first

|Özellik|Değer|
|-|-|
| **Kural adı** | dotnet_sort_system_directives_first |
| **Uygun diller** | C# ve Visual Basic |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` -System. * `using` yönergelerini alfabetik olarak sıralayın ve diğer using yönergelerinden önce yerleştirin.<br /><br />`false` -System. * `using` yönergelerini diğer yönergelerden önce yerleştirmeyin `using` . |

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

#### <a name="dotnet_separate_import_directive_groups"></a>DotNet \_ ayrı \_ içeri aktarma \_ yönergesi \_ grupları

|Özellik|Değer|
|-|-|
| **Kural adı** | dotnet_separate_import_directive_groups |
| **Uygun diller** | C# ve Visual Basic |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.5 |
| **Değerler** | `true` -Yönerge grupları arasına boş bir satır koyun `using` .<br /><br />`false` -Yönerge grupları arasına boş bir satır yerleştirmeyin `using` . |

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

Bu bölümdeki biçimlendirme kuralları yalnızca C# kodu için geçerlidir.

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
- [Yönerge seçeneklerini kullanma](#using-directive-options) 
  - csharp_using_directive_placement

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

#### <a name="csharp_new_line_before_open_brace"></a>\_ \_ \_ open_brace önce CSharp yeni \_ satırı

Bu kural, bir açık küme ayracın `{` önceki kodla aynı satıra mi yoksa yeni bir satıra mı yerleştirileceğini ele alır. Bu kural için, bu kuralın ne zaman uygulanacağını tanımlamak üzere **Yöntemler** veya **Özellikler**gibi **All**, **none**veya bir ya da daha fazla kod öğesi belirtirsiniz. Birden çok kod öğesi belirtmek için bunları virgülle (,) ayırın.

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_new_line_before_open_brace |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `all` -Küme ayracın tüm ifadeler için yeni bir satırda olması gerekir ("Allman" stili).<br /><br />`none` -Küme ayracın tüm ifadeler için aynı satırda olması gerekir ("K&R").<br /><br />`accessors`, `anonymous_methods` , `anonymous_types` , `control_blocks` , `events` , `indexers` , `lambdas` , `local_functions` , `methods` , `object_collection_array_initializers` , `properties` , `types` -Küme ayracı belirtilen kod öğesi ("Allman" stili) için yeni bir satırda olması gerekir. |

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

#### <a name="csharp_new_line_before_else"></a>CSharp \_ Yeni \_ satır \_ before_else

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_new_line_before_else |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` - `else` Deyimlerini yeni bir satıra yerleştir.<br /><br />`false` - `else` Deyimleri aynı satıra yerleştir. |

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

#### <a name="csharp_new_line_before_catch"></a>CSharp \_ Yeni \_ satır \_ before_catch

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_new_line_before_catch |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` - `catch` Deyimlerini yeni bir satıra yerleştir.<br /><br />`false` - `catch` Deyimleri aynı satıra yerleştir. |

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

#### <a name="csharp_new_line_before_finally"></a>CSharp \_ Yeni \_ satır \_ before_finally

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_new_line_before_finally |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` - `finally` Deyimlerin, kapanış ayracından sonra yeni bir satırda olmasını gerektir.<br /><br />`false` - `finally` Deyimlerinin kapanış ayracı ile aynı satırda olmasını gerektir. |

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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>\_ \_ \_ \_ object_initializers üyelerinizden önce \_ CSharp yeni \_ satır

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_new_line_before_members_in_object_initializers |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` -Nesne başlatıcılarının üyelerinin ayrı satırlarda olmasını gerektir<br /><br />`false` -Nesne başlatıcılarının üyelerinin aynı satırda olmasını gerektir |

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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>\_ \_ \_ \_ anonymous_types üyelerinizden önce \_ CSharp yeni \_ satır

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_new_line_before_members_in_anonymous_types |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` -Anonim türlerin üyelerinin ayrı satırlarda olmasını gerektir<br /><br />`false` -Anonim türlerin üyelerinin aynı satırda olmasını gerektir |

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

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_new_line_between_query_expression_clauses |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` -Sorgu ifadesi yan tümcelerinin öğelerinin ayrı satırlarda olmasını gerektir<br /><br />`false` -Sorgu ifadesi yan tümcelerinin öğelerin aynı satırda olmasını gerektir |

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

#### <a name="csharp_indent_case_contents"></a>CSharp \_ girintileme \_ case_contents

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_indent_case_contents |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` - `switch` Case içeriğini Girintile<br /><br />`false` - `switch` Servis talebi içeriklerini girintileme |

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

#### <a name="csharp_indent_switch_labels"></a>CSharp \_ girintileme \_ switch_labels

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_indent_switch_labels |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` - `switch` Etiketleri Girintile<br /><br />`false` - `switch` Etiketleri girintileme |

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

#### <a name="csharp_indent_labels"></a>CSharp \_ indent_labels

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_indent_labels |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `flush_left` -Etiketler en soldaki sütuna yerleştirilir<br /><br />`one_less_than_current` -Etiketler geçerli bağlama göre daha az bir girintide yerleştirilir<br /><br />`no_change` -Etiketler, geçerli bağlamla aynı girintide yer alır |

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

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_indent_block_contents |
| **Uygun diller** | C# |
| **Değerler** | `true` - <br /><br />`false` -  |

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

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_indent_braces |
| **Uygun diller** | C# |
| **Değerler** | `true` - <br /><br />`false` -  |

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

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_indent_case_contents_when_block |
| **Uygun diller** | C# |
| **Değerler** | `true` - <br /><br />`false` -  |

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

#### <a name="csharp_space_after_cast"></a>CSharp \_ space \_ after_cast

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_after_cast |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` -Bir atama ve değer arasına bir boşluk karakteri koyun<br /><br />`false` -Cast ve değer arasındaki boşluğu kaldır |

Kod örnekleri:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_after_keywords_in_control_flow_statements |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true`-Döngü gibi bir denetim akışı deyimindeki anahtar sözcükten sonra bir boşluk karakteri yerleştir `for`<br /><br />`false`-Döngü gibi bir denetim akışı deyimindeki anahtar sözcükten sonra boşluk Kaldır `for` |

Kod örnekleri:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_between_parentheses |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `control_flow_statements` -Denetim akışı deyimlerinin parantezleri arasına boşluk yerleştir<br /><br />`expressions` -İfadelerin parantezleri arasına boşluk yerleştir<br /><br />`type_casts` -Tür atamalerdeki parantezler arasında boşluk yerleştir |

Bu kuralı atlarsanız veya,, veya dışında bir değer kullanırsanız `control_flow_statements` , `expressions` `type_casts` ayar uygulanmaz.

Kod örnekleri:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>\_ \_ \_ inheritance_clause iki noktadan önce \_ CSharp \_ Space

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_before_colon_in_inheritance_clause |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değerler** | `true` -Bir tür bildiriminde temeller veya arabirimler için iki noktadan önce bir boşluk karakteri yerleştirin<br /><br />`false` -Tür bildiriminde temeller veya arabirimler için iki noktadan önce boşluğu kaldır |

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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>\_ \_ \_ inheritance_clause iki noktadan sonra \_ CSharp \_ Space

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_after_colon_in_inheritance_clause |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değerler** | `true` -Bir tür bildiriminde tabanların veya arabirimlerin iki noktadan sonra bir boşluk karakteri yerleştir<br /><br />`false` -Bir tür bildiriminde temeller veya arabirimler için iki noktadan sonra boşluk kaldır |

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

#### <a name="csharp_space_around_binary_operators"></a>\_ \_ binary_operators etrafında CSharp \_ alanı

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_around_binary_operators |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değerler** | `before_and_after` -İkili işleçten önce ve sonra boşluk Ekle<br /><br />`none` -İkili işleçten önce ve sonra boşlukları kaldır<br /><br />`ignore` -İkili operatörlerin çevresindeki boşlukları yoksay |

Bu kuralı atlarsanız veya,, veya dışında bir değer kullanırsanız, `before_and_after` `none` `ignore` ayar uygulanmaz.

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

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` -Açma parantezinden sonra ve bir yöntem bildirimi parametre listesinin kapatma parantezinden önce bir boşluk karakteri yerleştirin<br /><br />`false` -Boşluk karakterlerini açma parantezinden sonra ve bir yöntem bildirimi parametre listesinin kapatma parantezinden önce kaldırın |

Kod örnekleri:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değerler** | `true` -Yöntem bildirimi için boş parametre listesi ayraçları içine boşluk Ekle<br /><br />`false` -Yöntem bildirimi için boş parametre listesi ayraçları içindeki alanı kaldır |

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

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Uygun diller** | C# |
| **Değerler** | `true` -Yöntem bildiriminde Yöntem adı ve açma ayracı arasına bir boşluk karakteri koyun<br /><br />`false` -Yöntem bildiriminde Yöntem adı ve açma ayracı arasındaki boşluk karakterlerini kaldırın |

Kod örnekleri:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_between_method_call_parameter_list_parentheses |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` -Açma parantezinden sonra ve bir yöntem çağrısının kapatma parantezinden önce bir boşluk karakteri yerleştirin<br /><br />`false` -Açma parantezinden sonra ve bir yöntem çağrısının kapanış parantezinden önce boşluk karakterlerini kaldırın |

Kod örnekleri:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değerler** | `true` -Boş bağımsız değişken listesi ayraçları içine boşluk Ekle<br /><br />`false` -Boş bağımsız değişken listesi ayraçları içindeki alanı kaldır |

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

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| **Değerler** | `true` -Yöntem çağrısı adı ve açma ayracı arasına boşluk Ekle<br /><br />`false` -Yöntem çağrı adı ve açılış ayracı arasındaki boşluğu kaldır |

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

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_after_comma |
| **Uygun diller** | C# |
| **Değerler** | `true` -Virgülden sonra boşluk Ekle<br /><br />`false` -Virgülden sonra boşluk kaldır |

Kod örnekleri:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_before_comma |
| **Uygun diller** | C# |
| **Değerler** | `true` -Virgülden önce boşluk Ekle<br /><br />`false` -Bir virgülden önce boşluğu kaldır |

Kod örnekleri:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_after_dot |
| **Uygun diller** | C# |
| **Değerler** | `true` -Noktadan sonra boşluk Ekle<br /><br />`false` -Noktadan sonra boşluk kaldır |

Kod örnekleri:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_before_dot |
| **Uygun diller** | C# |
| **Değerler** | `true` -Noktadan önce boşluk Ekle <br /><br />`false` -Noktadan önce boşluğu kaldır |

Kod örnekleri:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_after_semicolon_in_for_statement |
| **Uygun diller** | C# |
| **Değerler** | `true`-Bir ifadede her noktalı virgülden sonra boşluk Ekle `for`<br /><br />`false`-Bir bildirimde her noktalı virgülden sonra boşluk Kaldır `for` |

Kod örnekleri:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_before_semicolon_in_for_statement |
| **Uygun diller** | C# |
| **Değerler** | `true`-Bir bildirimde her noktalı virgülden önce boşluk Ekle `for` <br /><br />`false`-Bir bildirimde her noktalı virgülden önce boşluk Kaldır `for` |

Kod örnekleri:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_around_declaration_statements |
| **Uygun diller** | C# |
| **Değerler** | `ignore` -Bildirim deyimlerine fazladan boşluk karakterleri kaldırmayın<br /><br />`false` -Bildirim deyimlerine ek boşluk karakterlerini kaldır |

Kod örnekleri:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_before_open_square_brackets |
| **Uygun diller** | C# |
| **Değerler** | `true` -Açılış köşeli ayracından önce boşluk Ekle `[` <br /><br />`false` -Köşeli ayraçları açmadan önce boşluğu kaldır `[` |

Kod örnekleri:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_between_empty_square_brackets |
| **Uygun diller** | C# |
| **Değerler** | `true` -Boş köşeli ayraç arasına boşluk Ekle `[ ]` <br /><br />`false` -Boş köşeli ayraçlar arasındaki boşluğu kaldır `[]` |

Kod örnekleri:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_space_between_square_brackets |
| **Uygun diller** | C# |
| **Değerler** | `true` -Boş olmayan köşeli Parantezde boşluk karakterleri Ekle `[ 0 ]` <br /><br />`false` -Boş olmayan köşeli ayraçdaki boşluk karakterlerini kaldır `[0]` |

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

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_preserve_single_line_statements |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` -Deyimleri ve üye bildirimlerini aynı satırda bırak<br /><br />`false` -Deyimleri ve üye bildirimlerini farklı satırlarda bırak |

Kod örnekleri:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_preserve_single_line_blocks |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** | Visual Studio 2017 sürüm 15.3 |
| **Değerler** | `true` -Kod bloğunu tek satırda bırak<br /><br />`false` -Kod bloğunu ayrı satırlarda bırak |

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

### <a name="using-directive-options"></a>Yönerge seçeneklerini kullanma

Bu biçimlendirme kuralı, bir ad alanı dışında, içine yerleştirilmiş yönergelerin kullanımı ile ilgilidir.

Örnek *. editorconfig* dosyası:

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a>csharp_using_directive_placement

|Özellik|Değer|
|-|-|
| **Kural adı** | csharp_using_directive_placement |
| **Uygun diller** | C# |
| **Tanıtılan sürüm** |  Visual Studio 2019 sürüm 16.1 |
| **Değerler** | `outside_namespace` -Ad alanı dışındaki yönergeleri kullanmayı bırak<br /><br />`inside_namespace` -Ad alanı içinde yönergeleri kullanmayı bırak |

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
